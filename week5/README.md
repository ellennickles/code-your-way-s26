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

### Creative Exercises Path • Parametric Geometries - UPDATE GIT PART

<details>

<summary>Assignment details</summary>

Don't worry if you haven't worked with algebra and trigonometry in a long time!
Just tinker and have fun with the equations in the code examples. This week is
more about continued practice of version control with Git using the
command line interface.

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
  Whitney’s work (linked below), is an excellent introduction to creative coding
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

#### Part 2: Re/Code

1. Develop a local p5 project on your computer in VS Code, and program your own
  full screen screensaver. (Hmmm... coming full circle to Week 1's preloaders?)
  Further extend one of your modified examples above or combine some.
2. Using the command line, navigate into the p5 project directory and
    initialize it as a Git repository. (I generally recommend creating one folder per p5 project to initialize as a repo.)
3. Use our [Git Intro](https://github.com/ellennickles/code-your-way-s25/blob/main/version-control-guides/git.md)
    as references and try committing your changes as you develop your sketch.
    - NOTE: Saving changes in VS Code does not automatically save them to your
      Git repository. To save changes in Git, you need to (1) stage (add) your
      modified files and then (2) commit them to the repository.
4. Review possible inspiration
   - Featured artists in the [Class
     Slides](https://docs.google.com/presentation/d/1xHHQjLG4BQKmyB7eRheWoB0fK_tK5doksTyXGHfffnY/edit?slide=id.g1dd282650f5_1_161#slide=id.g1dd282650f5_1_161)
   - Classic Windows screensavers that do not use parametric equations but are
    adjacent to this week's creative
    theme: [Mystify](https://www.youtube.com/watch?v=FPfMkEgi2qI),
    [Bézier](https://www.youtube.com/watch?v=3SEBEh_t5K8), and also
    [Screensaver_XP](https://openprocessing.org/sketch/215642) by kuba
   - John Whitney’s [Catalog](https://www.youtube.com/watch?v=TbV7loKp69s) (1961)
    and [Matrix III](https://www.youtube.com/watch?v=ZrKgyY5aDvA) (1972), as
    well as [An Afternoon with John
    Whitney](https://www.youtube.com/watch?v=cP5Mj6ZvZJc)
   - [Franke’s
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

#### Part 3: Document

- Document your work. Copy and paste any code from VS Code into the p5 web
  editor, so you can link to your sketches in your documentation. I know, I know
  this is getting super redundant, but it's still the easiest way to share.
- Reflect on the discoveries and challenges you encountered with the code
  exercises **and also with your new workflow using the command line interface
  with Git for version control**. And also: what graphic or animation effects are most pleasing to you? Where did you get stuck, and what steps did you take to troubleshoot? If you debugged or extended your code with GitHub Copilot, reflect on your discoveries and challenges, noting where AI was helpful or limiting. Are there any code-related techniques that would you like to explore and practice more?
  What would you like to explore and practice more?
- [Submit here](https://forms.gle/HaUJ7Mg74TJHxrJe8)

#### Part 4: Prepare for next week's class

- You should have this from Week 2 but if you don’t already have one,
  create a [GitHub account](https://github.com/).
- Sign up for the [GitHub Student Developer
  Pack](https://education.github.com/pack) to get free benefits.

</details>

### Self-Guided Study Path • Independent Learning - UPDATE FROM LAST WEEK - POINT OUT THAT THERE ARE THREE WEEKS (not including spring break) until project proposals, which everyone will do

<details>

<summary>Assignment details</summary>

#### Part 1: Keep Going

Showing up each week and doing the work *is* the work. Learning anything new
independently can genuinely be hard, and the fact that you're here, building a
practice week by week, matters more than any single breakthrough. Progress isn't
always visible right away, but it accumulates. Trust the process.

Keep working through your resources and building on last week's progress. This week, aim to:

- Complete the next section or module of your chosen tutorial, course, or
  resource.
- Apply what you're learning through a small exercise, experiment, or
  mini-project.
- If you're finding that your resources aren't quite right—too basic, too
  advanced, or not what you expected—that's useful information! Make a note of
  it and reach out to me so we can find alternatives together.

#### Part 2: Git Practice (Optional but Encouraged)

This week in class we introduced Git for version control. Whether or not it's
relevant to your current learning plan right now depends on where you are.

**If you're already iterating on code week to week** (writing, testing, and
revising files on your own computer), then this is a good time to start practicing Git
alongside the class. Use these guides to get started:

- [Git Intro](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/git.md)
- [Tips and Tricks](https://github.com/ellennickles/code-your-way-s26/blob/main/version-control-guides/tips-and-tricks.md)
- [All Version Control Guides](https://github.com/ellennickles/code-your-way-s26/tree/main/version-control-guides)

Try initializing a Git repository for your current project and making a few
commits as you work this week. Even if it feels awkward at first, the muscle
memory builds quickly.

**If you're not yet at a stage where you're managing local files**—for example,
if you're primarily working through browser-based tutorials or building
foundational knowledge—no worries. These resources will be here when you're
ready.

#### Part 3: Document

Continue documenting your weekly progress and reflections:

- What did you work on this week? (topics, exercises, mini-projects, etc.)
- What clicked? (concepts or techniques that made sense or felt useful)
- What was challenging? (any points of confusion, how you approached them, and
  whether you found a solution or decided to revisit them later)
- What's next? (next steps and any lingering questions to explore)
- If you tried Git this week: how did it go? What was confusing or surprising?
- [Submit here](https://forms.gle/HaUJ7Mg74TJHxrJe8)

</details>