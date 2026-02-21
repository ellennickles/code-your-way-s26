# Git Introduction

>_This guide was adapted with permission from
[Joey Lee](https://github.com/joeyklee) and [Cassie
Tarakajian's](https://github.com/catarak) [Git
Guide](https://github.com/itp-dwd/2020-spring/blob/master/guides/git.md)._

## Contents

- [1. About Git](#1-about-git)
- [2. Install Git](#2-install-git)
  - [2.1 Check if Git is installed](#21-check-if-git-is-installed)
  - [2.2 Install Git](#22-install-git)
- [3. Configure Git](#3-configure-git)
  - [3.1 Set username](#31-set-username)
  - [3.2 Set email](#32-set-email)
  - [3.3 Set default text editor](#33-set-default-text-editor)
  - [3.4 Set default branch name](#34-set-default-branch-name)
  - [3.5 Check all settings](#35-check-all-settings)
- [4. Create a Git repository](#4-create-a-git-repository)
  - [4.1 About repositories](#41-about-repositories)
  - [4.2 Initialize a repository in a local p5 project directory](#42-initialize-a-repository-in-a-local-p5-project-directory)
- [5. Add and commit changes](#5-add-and-commit-changes)
  - [5.1 Check the status of your files](#51-check-the-status-of-your-files)
  - [5.2 Stage and commit changes](#52-stage-and-commit-changes)
    - [5.2a Add and commit ALL changes](#52a-add-and-commit-all-changes)
    - [5.2b Add a single file and commit](#52b-add-a-single-file-and-commit)
    - [5.2c Add multiple files and commit](#52c-add-multiple-files-and-commit)
  - [5.3 Show commit history](#53-show-commit-history)
  - [5.4 Ignore files from Git tracking](#54-ignore-files-from-git-tracking)
- [6. Undo changes](#6-undo-changes)
  - [6.1 The differences at a glance](#61-the-differences-at-a-glance)
  - [6.2 Recommended: git reset --hard](#62-recommended-git-reset---hard)
  - [6.3 Other options worth knowing](#63-other-options-worth-knowing)
- [7. Branching and merging](#7-branching-and-merging)
  - [7.1 Create a branch](#71-create-a-branch)
  - [7.2 Switch branches](#72-switch-branches)
  - [7.3 Create and switch in one command](#73-create-and-switch-in-one-command)
  - [7.4 View all branches](#74-view-all-branches)
  - [7.5 Merge a branch](#75-merge-a-branch)
- [8. Resources](#8-resources)

---

## 1. About Git

**Git** is a tool that tracks changes to your project files over time. This is called **version control** — instead of saving over your work, Git lets you take snapshots of your project as it evolves, so you can always see what changed and go back to an earlier state if something breaks.

You can think of Git as a system that lets you drop "breadcrumbs" as you work, so you can:

1. **Track how your project develops** — when you add new files, make changes, or add new features
2. **Go back in time** — if you break something, want to try a different direction, or just want to recover an earlier version of a file

This is what we mean when we say Git is like a time machine ✨

A few key terms you'll see throughout this guide:

- **Repository (repo):** The folder for your project, once Git is tracking it. It contains all your files plus Git's record of every change you've made.
- **Commit:** A saved snapshot of your project at a specific moment in time. Think of it as a milestone you can always return to.
- **Staging:** The step where you tell Git *which* files to include in your next commit. More on this in [Section 5](#5-add-and-commit-changes).
- **Branch:** A parallel version of your project. You can experiment on a branch without affecting your main work. More on this in [Section 7](#7-branching-and-merging).

Git provides many benefits which are outlined in the [About section of the Git documentation](https://www.git-scm.com/about).

---

## 2. Install Git

### 2.1 Check if Git is installed

Open [Terminal (Mac)](https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac) or [PowerShell (Windows)](https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7.5) and type:

```sh
git --version
```

> 💡 **About the `$` symbol:** In this guide, code examples sometimes start with `$`. This represents your terminal's command prompt — the line where you type. **Do not type the `$`** — only type the command that comes after it. Your terminal will already show a prompt symbol of its own.

If Git is installed, the output will look something like this:

```sh
git version 2.53.0
```

If you see a version number, you're good — skip ahead to [Section 3: Configure
Git](#3-configure-git).

If Git is not installed, you will likely see a message like this:

![Screenshot of message indicating the git command is not recognized](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/assets/no-git-installed.png)

### 2.2 Install Git

If Git is not installed, follow the steps for your operating system:

**Mac:**

1. Go to [git-scm.com/download/mac](https://git-scm.com/download/mac)
2. There are several installation options — any will work
3. After installation completes, verify it worked:
   ```sh
   git --version
   ```
4. Keep the installer package and README.txt in case you need to troubleshoot later

**Windows:**

1. Go to [git-scm.com/download/win](https://git-scm.com/download/win)
2. Click the first download link — "Click here to download"
3. Run the installer and follow the prompts, accepting the default options
4. After installation completes, verify it worked:
   ```sh
   git --version
   ```

---

## 3. Configure Git

Before you start using Git, you need to tell it a few things about yourself. **You only need to do this once** — these settings are saved globally on your computer and will apply to all of your Git projects.

### 3.1 Set username

This is the name that will appear in your commit history. It doesn't need to match your GitHub username, but keeping them consistent is helpful.

1. Set your username:
   ```sh
   git config --global user.name "Awesome Person"
   ```

2. Verify it was set correctly:
   ```sh
   git config user.name
   ```

3. The output should match what you entered:
   ```sh
   Awesome Person
   ```

### 3.2 Set email

This is the email that will be associated with your commits. Use any address you'd like.

1. Set your email:
   ```sh
   git config --global user.email awesomeperson@example.com
   ```

2. Verify it was set correctly:
   ```sh
   git config user.email
   ```

3. The output should match what you entered:
   ```sh
   awesomeperson@example.com
   ```

### 3.3 Set default text editor

Sometimes Git needs you to type a message — for example, when reverting a commit. Rather than dropping you into Vim (Git's default, which can be disorienting for beginners), we'll set a friendlier editor upfront.

**Mac: set nano**

Nano is a simple text editor that's already installed on every Mac. It opens right inside your terminal window — no new app or window to deal with.

1. Set nano as your editor:
   ```sh
   git config --global core.editor "nano"
   ```

2. When Git opens nano for a message, type your text, then press **Control + X** to exit, **Y** to confirm saving, and **Enter** to accept the filename.

3. Verify it was set correctly:
   ```sh
   git config core.editor
   ```

4. The output should be:
   ```sh
   nano
   ```

**Windows: set Notepad**

Notepad is pre-installed on every Windows machine and works well for Git messages.

1. Set Notepad as your editor:
   ```sh
   git config --global core.editor "notepad"
   ```

2. When Git opens Notepad, type your message, save the file (**Ctrl + S**), and close the window. Git will continue once the window is closed.

3. Verify it was set correctly:
   ```sh
   git config core.editor
   ```

4. The output should be:
   ```sh
   notepad
   ```

---

**Optional: set VS Code as your editor**

If you're already comfortable in VS Code, you can set it as your Git editor instead. Any time Git needs a message, a new VS Code tab will open for you to type in.

1. Set VS Code as your editor:
   ```sh
   git config --global core.editor "code --wait"
   ```

> ⚠️ **A note of caution:** The `--wait` flag is important — it tells Git to pause and wait for you to close the VS Code tab before continuing. Without it, Git won't receive your message. This setup can also trigger VS Code's merge editor in some situations, which looks more complex than it needs to be at this stage. For now, nano (Mac) or Notepad (Windows) will keep things simpler and more predictable. You can always switch to VS Code later once you're more comfortable with Git's overall flow.

---

### 3.4 Set default branch name

The default branch name for a new Git repository is **master**. [Let's change this](https://www.wired.com/story/tech-confronts-use-labels-master-slave/) to **main**.

A **branch** is a parallel version of your project. You're always working on some branch — by default, that's `main`. With branching, say goodbye to file-naming gymnastics like "myProject-final-1", "myProject-final-final", "myProject-version-with-rainbows". Git handles all of that for you. We'll cover branching in detail in [Section 7](#7-branching-and-merging).

1. Set the default branch name:
   ```sh
   git config --global init.defaultBranch main
   ```

2. Verify it was set correctly:
   ```sh
   git config init.defaultBranch
   ```

3. The output should be:
   ```sh
   main
   ```

### 3.5 Check all settings

Once you've completed steps 3.1–3.4, you can review all four settings together in one go:

```sh
git config user.name
git config user.email
git config core.editor
git config init.defaultBranch
```

---

## 4. Create a Git repository

### 4.1 About repositories

A **Git repository** (or "repo") is your project folder once Git is tracking it. You can think of it as a folder with a memory — Git stores a complete record of every change you've committed, so you can always see how your project evolved and return to any earlier state.

Repositories can live locally on your computer or remotely on a hosting platform like GitHub, GitLab, or Bitbucket. To start, we'll work locally.

### 4.2 Initialize a repository in a local p5 project directory

1. **Create a new local p5 project in VS Code:**
   - If you haven't already, install the **p5.vscode** extension
   - Open the **Command Palette** (Mac: `command-shift-p` / Windows: `ctrl-shift-p`)
   - Type and select **Create p5.js Project**
   - Choose the **Desktop** as your save location
   - Create a new folder and give it a name, for example `myproject`
   - Click Open

2. **Navigate into the project folder from the command line:**
   ```sh
   cd Desktop/myproject
   ```

3. **Initialize the folder as a Git repository:**
   ```sh
   git init
   ```

4. **Check the status of your new repository:**
   ```sh
   git status
   ```

   The output will look something like this:

   ```sh
   On branch main

   No commits yet

   Untracked files:
     (use "git add <file>..." to include in what will be committed)
       index.html
       jsconfig.json
       libraries/
       sketch.js
       style.css

   nothing added to commit but untracked files present (use "git add" to track)
   ```

   Here's what this output is telling you:
   - **On branch main** — you're on the `main` branch (the default)
   - **No commits yet** — Git hasn't saved any snapshots yet
   - **Untracked files** — Git can see these files exist, but isn't recording changes to them yet
   - **nothing added to commit** — nothing is staged (queued up) for your first snapshot

5. **Stage all the files to start tracking them:**
   ```sh
   git add .
   ```
   The `.` means "everything in this folder." This queues up all your files to be included in the next commit.

6. **Check the status again** to see what changed:
   ```sh
   git status
   ```
   Your files should now appear under "Changes to be committed" — they're staged and ready.

7. **Commit the files** to save your first snapshot:
   ```sh
   git commit -m "Initial commit"
   ```

8. **Check the status one more time** to confirm everything is clean:
   ```sh
   git status
   ```
   You should see: `nothing to commit, working tree clean` — Git is up to date with your latest changes.

---

## 5. Add and commit changes

Most of the time, this is what you'll be doing day to day. The following commands will become part of your muscle memory.

### 5.1 Check the status of your files

At any time, you can check which files have been modified and what's been staged:

```sh
git status
```

> **Run `git status` all the time** — before and after every command. It's the best way to build a mental model of what's happening in your repository at any given moment, and it will often tell you exactly what to do next.

### 5.2 Stage and commit changes

Saving a snapshot to Git is a **two-step process**:

1. **Stage** your files with `git add` — this is like choosing which photos to include in an album. You're telling Git: "these are the changes I want to save."
2. **Commit** them with `git commit` — this takes the snapshot and stores it permanently in your project's history.

> 💡 **Important:** Saving a file in VS Code (`Cmd/Ctrl + S`) is *not* the same as committing it to Git. VS Code saves the file to your computer — Git commits save it to your version history. You need to do both.

- **Stage** with `git add` — even files that are already tracked need to be staged again after you make changes to them.
- **Commit** with `git commit -m "your message"` — the `-m` flag lets you write a short description of what changed, right in the command.

#### 5.2a Add and commit ALL changes

Use this when you want to stage and commit everything that's new or modified:

```sh
git add .
git commit -m "describe what changed"
```

> _How can you make your commit message more specific and descriptive for your project?_

#### 5.2b Add a single file and commit

Use this when you only want to commit changes to one specific file:

```sh
git add sketch.js
git commit -m "refactor with class to create many ball objects"
```

#### 5.2c Add multiple files and commit

Use this when you want to stage a specific group of files together:

```sh
git add index.html ball.js
git commit -m "updates index with reference to new ball.js"
```

### 5.3 Show commit history

The `git log` command shows your past commits in reverse chronological order (most recent first). Use it when you want to review what you've done, or find a commit ID to return to.

1. View the full log:
   ```sh
   git log
   ```

   The output will look something like this:

   ```sh
   commit 45d57112e59d0d5c31976a205de4688a19e4a436 (HEAD -> main)
   Author: yourGithubHandle
   Date:   Mon Feb 27 13:38:05 2023 -0500

       adds blue circle

   commit b5fb295283083775c550980bc4da8ec3050b8761
   Author: yourGithubHandle
   Date:   Mon Feb 27 13:37:38 2023 -0500

       adds red circle

   commit ff1aae083c35a6bea9ffed83e3a269593a9ded77
   Author: yourGithubHandle
   Date:   Mon Feb 27 13:36:15 2023 -0500

       Initial commit
   ```

   > 💡 **What does `HEAD -> main` mean?** `HEAD` is Git's way of saying "where you are right now." `HEAD -> main` means you're currently at the latest commit on the `main` branch. As you move back in time or switch branches, `HEAD` moves with you.

2. The log opens in a scrollable viewer inside your terminal:
   - Press **spacebar** to scroll down through older commits if the list is long
   - Press **q** to exit and return to your command line prompt
   
   > 💡 If your terminal seems frozen or unresponsive after running `git log`, you're probably still inside the log viewer — press **q** to get out.

3. For a more compact view that's easier to scan — especially when you need to grab a commit ID — use the `--oneline` flag:
   ```sh
   git log --oneline
   ```

   The output will look something like this:

   ```sh
   45d5711 (HEAD -> main) adds blue circle
   b5fb295 adds red circle
   ff1aae0 Initial commit
   ```

### 5.4 Ignore files from Git tracking

Some files don't belong in your Git history — system files, secret keys, or large assets you don't want tracked. You can tell Git to ignore them by adding a file named `.gitignore` to your project folder.

1. Create the `.gitignore` file. Make sure you're inside your project folder first (`cd Desktop/myproject`), then:

   On a Mac:
   ```sh
   touch .gitignore
   ```

   On Windows:
   ```sh
   new-item .gitignore
   ```

2. Open the `.gitignore` file and add the names of any files or folders you want Git to skip. You can open it in whichever editor you're comfortable with:

   - **Mac (nano):** `nano .gitignore`
   - **Windows (Notepad):** `notepad .gitignore`
   - **Either (VS Code):** `code .gitignore`

   Common entries to add include:

   ```txt
   # the macOS Finder metadata file, usually hidden from users
   .DS_Store

   # secret files or folders (e.g. API keys)
   .env
   private/*

   # large files you don't want tracked
   my200mbImageFile.tiff
   ```

3. Save the file, then stage and commit it like any other file:
   ```sh
   git add .gitignore
   git commit -m "adds gitignore"
   ```

---

## 6. Undo changes

One of the most powerful things about Git is the ability to move back to a previous state of your project. The approach you choose depends on whether you want to **rewrite history** or **preserve it**.

### 6.1 The differences at a glance

| Command | What it does | Rewrites history? | Best for |
|---|---|---|---|
| `git reset --hard` | Moves your project back to a previous commit | ✅ Yes | Solo projects, local work |
| `git revert` | Creates a new commit that undoes a previous one | ❌ No | Shared/collaborative repos |
| `git checkout -- <file>` | Restores a single file to its last committed state | ❌ No | Recovering one file only |

### 6.2 Recommended as you get started: `git reset --hard`

> ⚠️ **Read this before you run the command:** `git reset --hard` permanently discards any uncommitted changes in your working directory, as well as all commits after the one you reset to. Make sure you've committed everything you want to keep before running this.

For a solo p5 project where you're the only person working on the repo, `git reset --hard` is the most direct way to go back in time. It moves your project back to a previous commit — think of it as actually turning back the clock. Everything after that commit is gone from the history.

1. **View your commit history** to find the ID of the commit you want to return to:
   ```sh
   git log --oneline
   ```

   Your output will look something like this:
   ```sh
   3a9f1c2 (HEAD -> main) adds blue circle
   88e4d10 adds yellow circle
   b5fb295 adds red circle
   ff1aae0 Initial commit
   ```

2. **Copy the 7-character commit ID** of the commit you want to return to. In the example above, if you want to go back to "adds red circle," you'd copy `b5fb295`.

3. **Reset to that commit:**
   ```sh
   git reset --hard <commit id>
   ```

   Example:
   ```sh
   git reset --hard b5fb295
   ```

4. **Confirm you're there:**
   ```sh
   git log --oneline
   ```

   Your log will now end at the commit you reset to — the commits after it are gone.

### 6.3 Other options worth knowing

#### `git revert` — the "polite" undo

`git revert` doesn't erase history. Instead, it creates a *new* commit that undoes the effect of a previous one — like adding a correction at the end of a document rather than crossing something out in the middle. This is the preferred approach when working collaboratively, because it keeps the full history intact and doesn't disrupt other people's copies of the repo.

1. Revert a specific commit:
   ```sh
   git revert <commit id>
   ```

2. Git will open your default text editor asking you to write a message for the new "undo" commit. Save and close to proceed. To skip the editor entirely, use the `--no-edit` flag:
   ```sh
   git revert <commit id> --no-edit
   ```

> **Note:** Reverting a commit that isn't the most recent one can sometimes cause conflicts, because later changes may have built on top of it. If that happens, Git will let you know and ask you to resolve them.

#### `git checkout -- <filename>` — restore a single file

If you only want to recover one file to its last committed state — without touching anything else in your project — you can do so like this:

1. Restore the file:
   ```sh
   git checkout -- sketch.js
   ```

This is useful when you've been experimenting with one section and want to start fresh from the last commit, without reverting your whole project.

---

## 7. Branching and merging

Along with tracking file changes, Git also lets you work on different versions of your project at the same time — this is called **branching**.

A branch is a parallel version of your project. Your default branch is called `main`, and it always contains your stable, working code. When you want to try something experimental — a new feature, a refactor, a completely different visual direction — you create a new branch. Any changes you make there won't touch `main` at all. If you like what you built, you can **merge** the branch back in. If you don't, you can simply delete it and nothing is lost.

> 💡 **Heads up — branch notation in this section:** In the examples below, you'll sometimes see `(main):` or `(new-feature):` before a command. This is just to show you which branch you're on at that moment. **Do not type the `(branchname):` part** — only type the `git ...` command that follows it.

### 7.1 Create a branch

1. First, confirm you're on `main`:
   ```sh
   git status
   ```
   You should see `On branch main` near the top of the output.

2. Create a new branch:
   ```sh
   git branch new-feature
   ```
   This creates the branch but doesn't switch you to it yet — you're still on `main`.

### 7.2 Switch branches

1. Switch to your new branch:
   ```sh
   (main): git checkout new-feature
   ```

2. Verify which branch you're now on:
   ```sh
   git status
   ```
   You should see `On branch new-feature` near the top of the output.

### 7.3 Create and switch in one command

You can combine creating and switching into a single step using the `-b` flag — this is the most common way to do it:

1. Create and switch to a new branch at the same time:
   ```sh
   (main): git checkout -b new-feature
   ```

2. Verify:
   ```sh
   git status
   ```

### 7.4 View all branches

1. List all branches in your repository:
   ```sh
   git branch
   ```

2. Your current branch will be marked with an asterisk (`*`).

3. Type the letter **q** to exit and return to the command line prompt.

### 7.5 Merge a branch

When you're happy with what you've built on a branch and want to bring it into `main`:

1. Switch back to the `main` branch:
   ```sh
   git checkout main
   ```

2. Merge your feature branch into `main`:
   ```sh
   git merge new-feature
   ```

3. Once merged, delete the branch to keep things tidy:
   ```sh
   git branch -d new-feature
   ```

4. Verify the branch is gone:
   ```sh
   git branch
   ```

---

## 8. Resources

- At the command line, type `git help` for a list of all Git commands
- [Git Cheat Sheet (pdf)](https://education.github.com/git-cheat-sheet-education.pdf)
- [Git Documentation](https://git-scm.com/doc)
- [Introduction to version control with Git — Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/intro-to-git/)
- [Oh Shit, Git!?!](https://ohshitgit.com/) — plain-language fixes for common
  Git mistakes
