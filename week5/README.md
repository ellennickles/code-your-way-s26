# Week 5

## References

- [Class Slides](https://docs.google.com/presentation/d/1xHHQjLG4BQKmyB7eRheWoB0fK_tK5doksTyXGHfffnY/edit?slide=id.g1ceca21a636_0_0#slide=id.g1ceca21a636_0_0)
- Version Control Part 3 - Git Branches:
  - [Git
    Intro](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/git.md)
  - [Tips and
    Tricks](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/tips-and-tricks.md)
  - [All Version Control
    Guides](https://github.com/ellennickles/code-your-way-s26/tree/main/version-control-guides)

## Assignment

### Creative Exercises Path • Parametric Geometries

<details>

<summary>Assignment details</summary>

Don't worry if you haven't worked with algebra and trigonometry in a long time!
Just tinker and have fun with the equations in the code examples. This week is
also about practicing Git branches using the command line interface.

#### Part 1: Explore and Experiment

Modify each sketch to make it your own: play with the numbers (make some huge,
some tiny), change the shapes, make multiples of an animation, integrate some
random functions (`random()` and `noise()`), "layer up sine and cosine
functions" as suggested in Miller's video (linked below), make a grid, make it
interactive, and/or combine it with a previous sketch.

- [Example 1](https://editor.p5js.org/enickles/sketches/XFLDhFgk6)
- [Example 2](https://editor.p5js.org/enickles/sketches/291nqvFwo)
- [Example 3](https://editor.p5js.org/enickles/sketches/DIQO7W7ep)
- [Example 4](https://editor.p5js.org/enickles/sketches/I3fbOML-3)
- [Example 5](https://editor.p5js.org/enickles/sketches/ARUWgs58A)

##### Resources

- Highly recommend! [Recreating Vintage Computer Art with
  Processing](https://www.youtube.com/watch?v=LaarVR1AOvs), inspired by John
  Whitney's work (linked below), is an excellent introduction to creative coding
  with parametric equations with sine and cosine functions. (What's the
  [`return`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return)
  keyword?)
- [Khan Academy's lesson on Parametric
  equations](https://www.khanacademy.org/math/algebra-home/alg-trig-functions/alg-parametric/v/parametric-equations-1)
- [Graphs of Sine, Cosine and
  Tangent](https://www.mathsisfun.com/algebra/trig-sin-cos-tan-graphs.html)
- [Amplitude, Period, Phase Shift and
  Frequency](https://www.mathsisfun.com/algebra/amplitude-period-frequency-phase-shift.html)
- Description and use of the `sin()` function in [Creative Computing: Changes
  over time](https://creative-coding.decontextualize.com/changes-over-time) by
  Allison Parrish
- Coding Train videos
  - [3.4 Polar
    Coordinates](https://thecodingtrain.com/tracks/the-nature-of-code-2/noc/3-angles/4-polar-coordinates)
    (don't worry about vectors)
  - [3.5 Harmonic
    Motion](https://thecodingtrain.com/tracks/the-nature-of-code-2/noc/3-angles/5-harmonic-motion)
    demonstrating how to use the `sin()` function to simulate simple harmonic motion
  - [3.6 Graphing Sine
    Wave](https://thecodingtrain.com/tracks/the-nature-of-code-2/noc/3-angles/6-graphing-sine-wave)
    on how to graph and animate a sine wave varying the period and
    phase
  - [Coding Challenge #116 — Lissajous Curve
    Table](https://thecodingtrain.com/challenges/116-lissajous-curve-table) (and
    [challenge continued](https://www.youtube.com/watch?v=glDU8Nsyidg))

#### Part 2: Re/Code + Git Branches Practice

1. Develop a local p5 project on your computer in VS Code, and program your own
  full screen screensaver. Further extend one of your modified examples above or
  combine some.
2. As you develop your sketch, commit your changes regularly (aim for at least
  3 commits). Remember: saving in VS Code and saving to Git are two separate
  steps.
3. When you're ready to try a more experimental direction **create a branch** rather than editing
  your stable version directly:
    1. Create and switch to a new branch: `git checkout -b nameofnewbranch`
    2. Make your changes, then stage and commit as usual.
    3. Switch back to your main branch when you want to return to your stable
      version: `git checkout main`
    4. If you like what you made on the branch, merge it in:
      `git merge nameofnewbranch`
    5. If Oh My Zsh isn't installed yet, check the [Tips and
      Tricks](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/tips-and-tricks.md)
      guide. It makes your current branch visible in the command prompt, which
      helps a lot.
4. Review possible inspiration
   - Featured artists in the [Class
     Slides](https://docs.google.com/presentation/d/1xHHQjLG4BQKmyB7eRheWoB0fK_tK5doksTyXGHfffnY/edit?slide=id.g1dd282650f5_1_161#slide=id.g1dd282650f5_1_161)
   - Classic Windows screensavers that do not use parametric equations but are
    adjacent to this week's creative
    theme: [Mystify](https://www.youtube.com/watch?v=FPfMkEgi2qI),
    [Bézier](https://www.youtube.com/watch?v=3SEBEh_t5K8), and also
    [Screensaver_XP](https://openprocessing.org/sketch/215642) by kuba
   - John Whitney's [Catalog](https://www.youtube.com/watch?v=TbV7loKp69s) (1961)
    and [Matrix III](https://www.youtube.com/watch?v=ZrKgyY5aDvA) (1972), as
    well as [An Afternoon with John
    Whitney](https://www.youtube.com/watch?v=cP5Mj6ZvZJc)
   - [Franke's
    Oscilloscope](https://www.drbillkolomyjec.com/artworks/generative-art-vending-machine/franke-s-oscilloscope)
    Be sure to click _Generate_ for new examples! See description for how to
    start with a pair of parametric equations.
   - [Coding Train Coding Challenge #12 — The Lorenz
    Attractor](https://thecodingtrain.com/challenges/12-lorenz-attractor) in
    Processing
   - [Peter de Jong Attractors](http://paulbourke.net/fractals/peterdejong/)
    (1989) written by Paul Bourke (images updated 2014)
   - [Visualize:
    SUPERFORMULA](http://formandcode.com/code-examples/visualize-superformula)
    in _Form+Code in Design, Art, and Architecture_
   - The [PATHS](https://exchange.art/semuspace/nfts) series by @semuspace, "an
    art project inspired by the image produced by a
    [Harmonograph](https://en.wikipedia.org/wiki/Harmonograph), a mechanical
    device that employs a pendulum to generate images"

> **Remember:** Branches are a low-stakes way to try something new, and your `main`
> branch stays safe while you experiment. Think of it as a "what if?" lane.

#### Part 3: Document

- Document your work. Copy and paste any code from VS Code into the p5 web
  editor, so you can link to your sketches in your documentation. I know, I know
  this is getting super redundant, but it's still the easiest way to share.
- Reflect on the discoveries and challenges you encountered with the code
  exercises **and also with your Git branches workflow**. And also:
  - What graphic or animation effects are most pleasing to you?
  - Where did you get stuck, and what steps did you take to troubleshoot?
  - Did you use a branch this week? What did you put on it, and did you end up
    merging it or leaving it separate? How did it feel to have a "safe" space to
    experiment?
  - What would you like to explore and practice more?
- [Submit here](https://forms.gle/HaUJ7Mg74TJHxrJe8)

</details>

### Self-Guided Study Path • Independent Learning

<details>

<summary>Assignment details</summary>

#### Part 1: Keep Going

You're a third of the way through the semester. The foundation you've been
laying week by week is starting to mean something, keep building on it.

One thing to keep on your radar: in **Week 8**, everyone will share their
project proposals with the class for feedback. We'll talk through ideas together
before then, but it's worth keeping in mind as you work through your resources. What are you building toward?

Keep working through your resources and building on last week's progress. This week, aim to:

- Complete the next section or module of your chosen tutorial, course, or
  resource.
- Apply what you're learning through a small exercise, experiment, or
  mini-project.
- If you're finding that your resources aren't quite right—too basic, too
  advanced, or not what you expected—that's useful information! Make a note of
  it and reach out to me so we can find alternatives together.

#### Part 2: Git Branches (Optional but Encouraged)

This week in class we practiced **Git branches** — a way to develop experimental
changes without affecting your stable `main` version.

**If you've already been making commits**, this is a great next step. Try
creating a branch before making a bigger change or trying a new direction in
your project:

1. Create and switch to a new branch: `git checkout -b nameofnewbranch`
2. Make your changes, stage, and commit as usual.
3. Switch back to `main` when you want to return to your stable version:
  `git checkout main`
4. If you like what you made, merge it in: `git merge nameofnewbranch`

The [Tips and Tricks](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/tips-and-tricks.md)
guide covers this workflow and also has instructions for installing Oh My Zsh,
which makes your current branch visible in the command prompt. Even one branch
attempt is great practice.

**If you're not yet managing local files** — for example, if you're primarily
working through browser-based tutorials or building foundational knowledge — no
worries. These resources will be here when you need them.

#### Part 3: Document

Continue documenting your weekly progress and reflections:

- What did you work on this week? (topics, exercises, mini-projects, etc.)
- What clicked? (concepts or techniques that made sense or felt useful)
- What was challenging? (any points of confusion, how you approached them, and
  whether you found a solution or decided to revisit them later)
- What's next? (next steps and any lingering questions to explore)
- If you tried Git branches this week: what did you put on a branch, and how
  did it go? What was confusing or surprising?
- [Submit here](https://forms.gle/HaUJ7Mg74TJHxrJe8)

</details>
