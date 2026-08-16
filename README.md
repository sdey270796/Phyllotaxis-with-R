# Phyllotaxis with R: Mathematics, Nature & Creative Visualization

> **A playful R/ggplot2 project demonstrating how mathematics and data
> visualization can recreate plant-inspired patterns such as spirals,
> dandelions, sunflowers, and imaginary flowers.**

## 🌱 Project Overview

This notebook is a small **creative coding and visualization experiment
in R**, developed primarily to showcase the versatility of R beyond
conventional statistical analysis.

The central idea is **phyllotaxis**---the natural arrangement of leaves,
flowers, or seeds around a plant stem. Many such arrangements exhibit
spiral patterns associated with the **Golden Angle**, approximately
137.5°.

Rather than treating `ggplot2` only as a tool for conventional charts,
this project uses it as a medium for mathematical and artistic
exploration.

The notebook starts with something as simple as **50 points on a
circle** and progressively transforms them into:

``` text
Circle
  ↓
Spiral
  ↓
Minimalist plant-like pattern
  ↓
Dandelion
  ↓
Sunflower
  ↓
Alternative patterns
  ↓
Imaginary flowers
```

The result is intentionally more **playful and visual than analytical**.

------------------------------------------------------------------------

# 🎯 Purpose

This project was created as a **fun classroom activity with students**,
while simultaneously demonstrating a useful point:

> **R is not limited to statistics, machine learning, and serious
> analytical work---it can also be used creatively to explore
> mathematics, nature, aesthetics, and visual design.**

The notebook uses a simple mathematical construction to introduce
students to several practical `ggplot2` concepts in an engaging way.

It is therefore best viewed as a **creative teaching demonstration**,
rather than as a production data-science project.

------------------------------------------------------------------------

# 🌻 What is Phyllotaxis?

Phyllotaxis refers to the arrangement of leaves, flowers, or seeds on
the stem of a plant.

Many natural arrangements exhibit spiral structures. The notebook
introduces the **Golden Angle**, approximately:

``` text
137.5°
```

and connects it with the Golden Ratio and patterns found in nature.

Examples discussed in the notebook include:

-   Sunflower seeds
-   Pine cones
-   Flower petals
-   Plant leaves
-   Daisies
-   Shells
-   Spiral galaxies
-   Hurricanes

The project uses this mathematical idea as the foundation for generating
its visual patterns.

------------------------------------------------------------------------

# 🧮 The Mathematics

The notebook begins with points on a unit circle.

For an angle `t`:

``` text
x = sin(t)
y = cos(t)
```

which satisfies:

``` text
x² + y² = 1
```

because of the Pythagorean trigonometric identity:

``` text
sin²(t) + cos²(t) = 1
```

This provides the simplest possible starting point for the
visualization.

------------------------------------------------------------------------

# 🔄 From Circle to Spiral

Initially, all points have the same distance from the origin.

To transform the circle into a spiral, the notebook progressively
increases the radial distance.

Conceptually:

``` text
x = sin(t)
y = cos(t)

       ↓

X = x × t
Y = y × t
```

The angle is then advanced by the Golden Angle:

``` text
Golden Angle = π(3 − √5)
```

and the number of points is initially set to:

``` text
500
```

This simple combination creates a recognizable spiral structure.

------------------------------------------------------------------------

# 📊 Learning `ggplot2` Through Art

The project uses `ggplot2` throughout the notebook.

Rather than presenting a conventional dataset, the generated coordinates
themselves become the data to visualize.

The notebook therefore provides a natural introduction to:

-   `ggplot()`
-   `aes()`
-   `geom_point()`
-   Point size
-   Point transparency (`alpha`)
-   Point shape
-   Point color
-   Plot themes
-   Removing unnecessary visual elements
-   Hiding legends
-   Controlling plot dimensions

This makes the project particularly suitable for students who are
learning visualization concepts.

------------------------------------------------------------------------

# 🧪 Project Progression

The notebook is structured as a gradual visual experiment.

## 1. Patterns in Nature

The project introduces the idea that mathematical structures can
describe visually striking natural phenomena.

The notebook emphasizes the connection between:

``` text
Nature
  +
Mathematics
  +
Visualization
```

------------------------------------------------------------------------

## 2. Warming Up: Drawing Points on a Circle

The first computational step generates:

``` text
50 points
```

on a unit circle.

The R code is essentially:

``` r
t <- seq(0, 2*pi, length.out = 50)
x <- sin(t)
y <- cos(t)

df <- data.frame(t, x, y)
```

The points are then plotted using:

``` r
ggplot(df, aes(x, y)) +
    geom_point()
```

This establishes the basic relationship between numerical coordinates
and a `ggplot2` visualization.

------------------------------------------------------------------------

# 🌀 3. The Golden-Angle Spiral

The next stage introduces the Golden Angle:

``` r
angle <- pi * (3 - sqrt(5))
```

with:

``` r
points <- 500
```

The angular position of each point is generated by:

``` r
t <- (1:points) * angle
```

and the spiral is created by scaling the coordinates according to `t`.

This transforms the circular arrangement into a plant-like spiral.

------------------------------------------------------------------------

# 🎨 4. Removing Everything Unnecessary

The notebook then demonstrates how much visual appearance can change
simply by removing standard chart components.

It removes:

-   Grid lines
-   Axis ticks
-   Axis titles
-   Axis labels
-   Default visual clutter

For example:

``` r
theme(
    panel.background = element_rect(fill="white"),
    panel.grid = element_blank(),
    axis.ticks = element_blank(),
    axis.title = element_blank(),
    axis.text = element_blank()
)
```

This illustrates an important visualization principle:

> A plot does not always need to look like a conventional chart.

The same graphical system can be used to create visual art.

------------------------------------------------------------------------

# 🌿 5. A Bit of Makeup

The project then modifies:

``` text
Size
Color
Transparency
```

For example:

``` r
geom_point(
    size = 8,
    alpha = 0.5,
    color = "darkgreen"
)
```

The resulting pattern begins to resemble a plant.

This stage demonstrates how aesthetic parameters can transform the
interpretation and visual character of the same underlying data.

------------------------------------------------------------------------

# 🌼 6. The Dandelion

The notebook next makes point size depend on the variable `t`:

``` r
geom_point(
    aes(size = t),
    alpha = 0.5,
    shape = 8
)
```

Instead of assigning every point the same size, the size now varies
throughout the spiral.

This demonstrates a key `ggplot2` concept:

``` text
Variable
   ↓
Aesthetic mapping
   ↓
Visual property
```

In this case:

``` text
t
 ↓
point size
```

The resulting structure resembles a delicate dandelion.

------------------------------------------------------------------------

# 🌻 7. The Sunflower

The notebook combines the techniques introduced earlier to create a
sunflower-inspired pattern.

The final plot uses:

``` r
geom_point(
    aes(size = t),
    alpha = 0.5,
    shape = 17,
    color = "yellow"
)
```

along with a dark background.

This section connects the visualization back to the natural occurrence
of spiral arrangements in sunflower seed heads.

------------------------------------------------------------------------

# 🔬 8. What Happens if the Angle Changes?

One of the most interesting demonstrations in the notebook is the effect
of changing the angular increment.

The Golden Angle produces one particular structure, but even a
relatively small change in the angle can produce a dramatically
different pattern.

The notebook changes the angle to:

``` r
angle <- 2
```

and increases the number of points to:

``` r
points <- 1000
```

The resulting visualization looks very different.

This provides an intuitive demonstration of **sensitivity to
mathematical parameters**.

A small numerical change can produce a large visual change.

------------------------------------------------------------------------

# 🌸 9. Imaginary Flowers

The final section emphasizes the creative potential of the approach.

The notebook changes the parameters to:

``` r
angle <- 13*pi/180
points <- 2000
```

and then modifies:

``` text
Point size
Transparency
Shape
Color
Background
```

to produce a magenta flower-like pattern.

The notebook concludes that the same techniques can generate an
essentially unlimited variety of nature-inspired patterns.

------------------------------------------------------------------------

# 🧰 Technology Stack

  Component              Technology
  ---------------------- ------------------------------------------------------
  Programming language   R
  Visualization          ggplot2
  Environment            Jupyter Notebook / R-compatible notebook environment
  Primary geometry       `geom_point()`
  Mathematical basis     Trigonometry + Golden Angle
  Output                 Generative mathematical visualizations

------------------------------------------------------------------------

# 📦 Required Package

The project requires:

``` r
library(ggplot2)
```

No external dataset is required.

The coordinates are generated mathematically inside the notebook.

------------------------------------------------------------------------

# 🚀 Running the Notebook

Open:

``` text
Phyllotaxis_with_R.ipynb
```

in a notebook environment capable of executing R code.

Then run the cells sequentially.

The notebook progressively builds the visualization, so running the
sections in order is recommended.

------------------------------------------------------------------------

# 📁 Repository Structure

A minimal repository can contain:

``` text
.
├── README.md
└── Phyllotaxis_with_R.ipynb
```

No external dataset is necessary because the project generates all
coordinates algorithmically.

------------------------------------------------------------------------

# 🎓 Classroom Value

Although this project is deliberately simple, it has several useful
teaching applications.

## 1. Making R Less Intimidating

Students often associate R exclusively with:

``` text
Statistics
Dataframes
Regression
Machine Learning
```

This project presents a different side of the language.

R can also be used to:

``` text
Explore mathematics
Create art
Generate patterns
Experiment visually
```

------------------------------------------------------------------------

## 2. Teaching `ggplot2` Without a Conventional Dataset

Students can learn:

``` r
ggplot()
aes()
geom_point()
theme()
```

without first having to deal with a complicated real-world dataset.

The generated mathematical coordinates act as a very simple dataset.

------------------------------------------------------------------------

## 3. Connecting Mathematics and Programming

The project creates a direct bridge between:

``` text
Mathematical Formula
        ↓
R Code
        ↓
Numerical Coordinates
        ↓
Visualization
```

Students can therefore see how an abstract mathematical idea becomes a
computational object.

------------------------------------------------------------------------

## 4. Demonstrating Parameters

The notebook provides an intuitive way to show how changing:

``` text
angle
points
size
alpha
shape
color
```

changes the final output.

This is a particularly accessible introduction to experimentation and
parameter sensitivity.

------------------------------------------------------------------------

## 5. Encouraging Computational Creativity

The final section invites students to modify the parameters and create
their own patterns.

Instead of asking:

> "What is the correct answer?"

the activity encourages:

> "What happens if I change this?"

That makes it well suited to an informal classroom activity.

------------------------------------------------------------------------

# 🧠 Key Concepts Demonstrated

### Mathematics

-   Trigonometric functions
-   Unit circle
-   Polar-like coordinate construction
-   Golden Ratio
-   Golden Angle
-   Spiral geometry
-   Parameter sensitivity

### R Programming

-   Sequence generation
-   Variables
-   Vectors
-   Data frames
-   Mathematical functions
-   Function arguments

### Data Visualization

-   `ggplot()`
-   `aes()`
-   `geom_point()`
-   Size mapping
-   Transparency
-   Shape
-   Color
-   Themes
-   Plot dimensions

### Computational Thinking

-   Start with a simple model
-   Modify one component at a time
-   Observe the effect
-   Combine techniques
-   Experiment with parameters

------------------------------------------------------------------------

# 🔬 The Core Idea in One Diagram

``` text
             Golden Angle
                  │
                  ▼
        Generate angular positions
                  │
                  ▼
           sin(t), cos(t)
                  │
                  ▼
       Increase radial distance
                  │
                  ▼
          Generate coordinates
                  │
                  ▼
             ggplot2
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
     Size       Shape       Color
       │          │          │
       └──────────┼──────────┘
                  ▼
          Nature-inspired art
```

------------------------------------------------------------------------

# 🎨 Why This Project Matters

The computational complexity of this project is intentionally low.

That is precisely the point.

A few mathematical expressions and a handful of `ggplot2` parameters are
sufficient to produce visually interesting structures.

It demonstrates that programming does not always have to be about
solving a difficult engineering problem.

Sometimes the value of code is simply that it allows us to:

-   See mathematics
-   Explore patterns
-   Appreciate nature
-   Experiment
-   Create something beautiful
-   Make learning enjoyable

------------------------------------------------------------------------

# 🔮 Ideas for Further Experimentation

Students can extend the notebook by changing:

``` r
angle
points
size
alpha
shape
color
```

and observing the resulting structures.

Possible experiments include:

### Experiment 1 --- Golden Angle

Try:

``` r
angle <- pi * (3 - sqrt(5))
```

### Experiment 2 --- Different Angles

Try values such as:

``` r
angle <- 1
angle <- 2
angle <- 2.5
angle <- 13*pi/180
```

### Experiment 3 --- More Points

Try:

``` r
points <- 500
points <- 1000
points <- 2000
points <- 5000
```

### Experiment 4 --- Different Point Shapes

Experiment with different `shape` values in `geom_point()`.

### Experiment 5 --- Different Aesthetics

Change:

``` text
size
alpha
color
background
```

to create completely different visual styles.

------------------------------------------------------------------------

# ⚠️ Scope

This repository should **not** be interpreted as a scientific model of
biological phyllotaxis.

The notebook uses a mathematical pattern inspired by phyllotaxis to
create visualizations.

It does not attempt to:

-   Model plant growth
-   Simulate biological development
-   Explain the physiological mechanism behind phyllotaxis
-   Perform botanical measurements
-   Validate a biological hypothesis

Its purpose is primarily **educational, exploratory, and creative**.

------------------------------------------------------------------------

# 🏁 Conclusion

**Phyllotaxis with R** is a small but deliberately playful demonstration
of the expressive capabilities of R and `ggplot2`.

Starting from the equation of a circle, the notebook progressively
introduces the Golden Angle, radial scaling, aesthetic mappings, and
parameter variation to produce increasingly elaborate nature-inspired
patterns.

The journey is:

``` text
50 points on a circle
        ↓
Golden-Angle spiral
        ↓
Minimalist plant pattern
        ↓
Dandelion
        ↓
Sunflower
        ↓
Alternative angle patterns
        ↓
Imaginary flower
```

The project was created as a **fun classroom activity with students**,
but it also carries a broader lesson:

> **Programming can be a medium for curiosity and creativity, not merely
> a tool for solving predefined problems.**

The same `ggplot2` skills used here for creating mathematical
flowers---mapping variables to aesthetics, controlling geometry,
adjusting transparency, manipulating themes, and experimenting with
parameters---are directly transferable to serious real-world data
visualization.

------------------------------------------------------------------------

# 👤 Author

**Subhadeep Dey**

Educational and exploratory projects spanning:

-   Physics
-   Mathematics
-   Data Science
-   Machine Learning
-   Artificial Intelligence
-   Scientific Visualization
-   Computational Creativity

------------------------------------------------------------------------

## 🌱 Final Thought

> **Start with a circle. Add mathematics. Let the code grow.**
