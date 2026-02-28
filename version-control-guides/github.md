# GitHub Introduction

>_This guide picks up where the [Git Introduction](git.md) guide leaves off. Make sure you have Git installed and configured before continuing._

## Contents

- [1. About GitHub](#1-about-github)
- [2. Create a GitHub account](#2-create-a-github-account)
- [3. Set up SSH keys for authentication](#3-set-up-ssh-keys-for-authentication)
  - [3.1 Generate a new SSH key pair](#31-generate-a-new-ssh-key-pair)
  - [3.2 Add the SSH private key to the ssh-agent](#32-add-the-ssh-private-key-to-the-ssh-agent)
  - [3.3 Add the SSH public key to your GitHub account](#33-add-the-ssh-public-key-to-your-github-account)
  - [3.4 Test your SSH connection](#34-test-your-ssh-connection)
- [4. Connect a local repository to GitHub](#4-connect-a-local-repository-to-github)
  - [4.1 Add a local Git repository to GitHub](#41-add-a-local-git-repository-to-github)
  - [4.2 Push changes to a remote repository](#42-push-changes-to-a-remote-repository)
  - [4.3 Pull changes from a remote repository](#43-pull-changes-from-a-remote-repository)
  - [4.4 Clone a GitHub repository to your computer](#44-clone-a-github-repository-to-your-computer)
- [5. Resources](#5-resources)

---

## 1. About GitHub

**GitHub** is an online platform for hosting Git repositories. Once your project
is on GitHub, you can share it with others, access it from any computer, and
collaborate with teammates, all while keeping the full version history that Git
provides.

A few key terms you'll see throughout this guide:

- **Remote:** A version of your repository stored somewhere other than your local computer — in this case, on GitHub.
- **Push:** Sending commits from your local repository up to the remote on GitHub.
- **Pull:** Downloading changes from the remote repository to your local computer.
- **Clone:** Making a full local copy of a remote repository, including its entire history.

---

## 2. Create a GitHub account

If you don't already have one, create a free account at [github.com](https://github.com/signup).

> 💡 **Tip:** Your GitHub username will appear in your commit history and on your public profile.

---

## 3. Set up SSH keys for authentication

To connect your local repositories to GitHub, you need to set up **SSH keys**. SSH (Secure Shell Protocol) is a secure way to authenticate over a network without typing your password every time.

It works using a pair of keys:
- A **private key** that stays on your computer (never share this)
- A **public key** that you give to GitHub

When you push or pull, GitHub uses the public key to verify that you're you.

> 💡 **The setup process may look slightly different** depending on your operating system version. If you run into issues, refer to GitHub's official documentation linked in each step.

### 3.1 Generate a new SSH key pair

> _Reference: [Generating a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)_

1. Open [Terminal (Mac)](https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac) or [PowerShell (Windows)](https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7.5) and run the following command, substituting in **your GitHub email address**:

   ```sh
   ssh-keygen -t ed25519 -C "your_github_email@example.com"
   ```

   The output should look something like this:

   ```txt
   Generating public/private ed25519 key pair.
   ```

2. You'll be prompted to choose a location to save the key (where `YOU` is your computer username):

   ```txt
   Enter a file in which to save the key (/Users/YOU/.ssh/ed25519): [Press enter]
   ```

   **Don't type anything** — just press **Enter** to accept the default location.

3. You'll then be prompted to set a passphrase for extra security. For now, press **Enter twice** to leave it empty. You can always add one later.

4. Once the key is saved, the output will look something like this (where `YOU` is your computer username):

   ```txt
   Your identification has been saved in /Users/YOU/.ssh/id_ed25519.
   Your public key has been saved in /Users/YOU/.ssh/id_ed25519.pub.
   The fingerprint is: SHA256:...and a long string of characters your_github_email@example.com
   ```

### 3.2 Add the SSH private key to the ssh-agent

The **ssh-agent** is a program that runs in the background on your computer and manages your SSH keys so you don't have to re-enter them during every session.

> _Reference: [Adding your key to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)_

**Follow the instructions for your operating system:**

<details>
<summary><strong>Mac</strong></summary>

1. Start the ssh-agent in the background:

   ```sh
   eval "$(ssh-agent -s)"
   ```

   The output should look something like this:

   ```txt
   Agent pid 59566
   ```

   > 💡 Depending on your environment, you may need to use a slightly different command. Check the reference link above for alternatives.

2. If you're using macOS Sierra 10.12.2 or later, you'll need to configure your SSH settings so your key is loaded automatically each time you start a session.

   - Check whether the config file already exists:

     ```sh
     cat ~/.ssh/config
     ```

   - If the file doesn't exist, create it:

     ```sh
     touch ~/.ssh/config
     ```

   - Open the file in your text editor (note this assumes that you [set up a
     default text
     editor to nano](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/git.md#33-set-default-text-editor)):

     ```sh
     nano ~/.ssh/config
     ```

   - Add the following lines. Be careful not to include any extra spaces at the end:

     ```txt
     Host github.com
       AddKeysToAgent yes
       IdentityFile ~/.ssh/id_ed25519
     ```

   - Save and close the file, then verify the contents:

     ```sh
     cat ~/.ssh/config
     ```

3. Add your SSH private key to the ssh-agent:

   ```sh
   ssh-add ~/.ssh/id_ed25519
   ```

   The output should look something like this (where `YOU` represents your computer username):

   ```txt
   Identity added: /Users/YOU/.ssh/id_ed25519 (your_github_email@example.com)
   ```

</details>

<details>
<summary><strong>Windows</strong></summary>

1. Open a **new PowerShell window as Administrator**. To do this, search for "PowerShell" in the Start menu, right-click it, and select **"Run as administrator."** Click Yes when prompted.

   > 💡 You'll know you're in admin mode when the window title says "Administrator: Windows PowerShell."

2. Run these two commands **one at a time** to start the ssh-agent:

   ```powershell
   Get-Service -Name ssh-agent | Set-Service -StartupType Manual
   ```

   ```powershell
   Start-Service ssh-agent
   ```

   The first command configures the ssh-agent service to allow manual startup. The second command starts it. If you don't see any error messages, it worked.

3. **Switch back to a regular (non-admin) PowerShell window.** You don't need admin permissions for the next step.

4. Add your SSH private key to the ssh-agent:

   ```powershell
   ssh-add C:\Users\YOU\.ssh\id_ed25519
   ```

   Replace `YOU` with your Windows username. The output should look something like this:

   ```txt
   Identity added: C:\Users\YOU\.ssh\id_ed25519 (your_github_email@example.com)
   ```

   > ⚠️ **Make sure the filename matches the key you generated.** If you ran `ssh-keygen -t ed25519` in step 3.1, the file is `id_ed25519`. If you see "No such file or directory," run `ls ~/.ssh` to check what files are there.

</details>

### 3.3 Add the SSH public key to your GitHub account

> _Reference: [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)_

1. Copy your public key to your clipboard:

   **Mac:**
   ```sh
   pbcopy < ~/.ssh/id_ed25519.pub
   ```

   If `pbcopy` isn't working, print the key and copy it manually:
   ```sh
   cat ~/.ssh/id_ed25519.pub
   ```

   **Windows:**
   ```sh
   Get-Content ~/.ssh/id_ed25519.pub | Set-Clipboard
   ```

2. In your GitHub account, click your **profile photo** (upper right corner) > **Settings**

3. In the sidebar, click **SSH and GPG keys**

4. Click **New SSH key** or **Add SSH key**

5. Complete the form:
   - **Title:** A descriptive label for this key, e.g. `Personal laptop`
   - **Key type:** Authentication Key
   - **Key:** Paste in the public key you copied above

6. Click **Add SSH key**. If prompted, confirm access to your account.

### 3.4 Test your SSH connection

> _Reference: [Testing your SSH connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)_

1. In your terminal, run:

   ```sh
   ssh -T git@github.com
   ```

2. You may see a warning like this:

   ```txt
   The authenticity of host 'github.com (IP ADDRESS)' can't be established.
   RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
   Are you sure you want to continue connecting (yes/no)?
   ```

   Verify that the fingerprint matches [GitHub's published key fingerprints](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints). If it does, type `yes` and press **Enter**.

3. A successful connection will look like this:

   ```txt
   Hi YOURGITHUBUSERNAME! You've successfully authenticated, but GitHub does not provide shell access.
   ```

   This means it worked! (The "shell access" message is normal — GitHub uses SSH only for Git operations, not for remote login.)

   If you see a "permission denied" error instead, refer to GitHub's guide on [fixing permission denied errors](https://docs.github.com/en/authentication/troubleshooting-ssh/error-permission-denied-publickey).

---

## 4. Connect a local repository to GitHub

### 4.1 Add a local Git repository to GitHub

> _References: [Creating a new repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository) and [Adding a local repository to GitHub](https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git)_

You can **push** a local Git repository to GitHub to back it up, share it, or access it from another computer.

1. Make sure you have a local Git repository with at least one commit. If you need to create one, refer to [Section 4.2 of the Git Introduction guide](git.md#42-initialize-a-repository-in-a-local-p5-project-directory).

2. On GitHub.com, create a **new repository**. From the **+** menu in the upper right corner, select **New repository**.

3. Complete the form:
   - **Repository name:** Use the same name as your local folder for consistency. No spaces — for example: `myproject`
   - **Visibility:** For course projects you want to share, use **Public**
   - Skip the optional initialization steps (README, .gitignore, license) — you'll be pushing existing files
   - Click **Create repository**

4. On the next screen, copy the **SSH URL** — it looks like: `git@github.com:YOURUSERNAME/myproject.git`

   > 💡 Make sure you click the **SSH** button (not HTTPS) before copying the URL. If you don't see SSH and HTTPS options, look for the **Quick setup** section at the top of the page.

5. In your terminal, navigate into your local repository. Make sure all your recent changes are committed and that you're on the `main` branch:

   ```sh
   git checkout main
   ```

6. Link your local repository to the new remote and push your commits:

   ```sh
   git remote add origin git@github.com:YOURUSERNAME/myproject.git
   git push -u origin main
   ```

   > 💡 **What does `origin` mean?** It's the conventional name for your primary remote repository. The `-u` flag in the push command sets `origin main` as the default, so future pushes can be shortened to just `git push`.

7. Refresh your GitHub repository page — your files should now appear there.

   > ⚠️ **Commits don't sync automatically.** After this initial setup, local commits will _not_ appear on GitHub until you push them. See [Section 4.2](#42-push-changes-to-a-remote-repository) below.

### 4.2 Push changes to a remote repository

After your local and remote repositories are connected, use `git push` to send new commits to GitHub:

```sh
git push
```

Refresh your GitHub repository page to see the updated files and commit history.

> 💡 **Run `git status` first** to confirm you're on the `main` branch and that your changes are committed before pushing.

### 4.3 Pull changes from a remote repository

If changes are made directly on GitHub — like editing a file or adding a README in the browser — those changes won't appear on your local machine until you pull them down.

Let's try it by adding a README file on GitHub:

1. On your GitHub repository page, click **Add a README**

2. GitHub will generate a title from your repository name using [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax). Feel free to edit the title and add a project description.

3. Click **Preview** to see how it will render.

4. When you're ready, scroll to the bottom of the page and click **Commit changes**, keeping the default message (`Create README.md`).

5. In your terminal, pull the new file to your local repository:

   ```sh
   git pull
   ```

6. Look inside your project folder — `README.md` should now be there.

### 4.4 Clone a GitHub repository to your computer

**Cloning** creates a complete local copy of a remote repository, including all of its files and commit history. Use this when you want to:

- Work on a repository from a different computer
- Get a local copy of someone else's public repository
- Download a project from GitHub to work on locally

1. Navigate to the repository on GitHub.

2. Click the **<> Code** button > **Local** tab > **SSH** > copy the SSH URL.

3. In your terminal, navigate to the location where you want to place the folder, then run:

   ```sh
   git clone git@github.com:GITHUBUSERNAME/reponame.git
   ```

   This creates a new folder with the repository name and downloads everything into it.

---

## 5. Resources

- [About Git and how it works with
  GitHub](https://docs.github.com/en/get-started/using-git/about-git)
- [Hello World — a beginner exercise for
  GitHub](https://docs.github.com/en/get-started/quickstart/hello-world)
- [GitHub flow](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Pro Git book: Collaborating on
  GitHub](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project)
- [Markdown basic
  syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [Markdown Tutorial](https://www.markdowntutorial.com/)