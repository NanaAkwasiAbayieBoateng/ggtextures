
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ggtextures

Written by Claus O. Wilke

This package provides functions to draw textured rectangles and bars
with the grid graphics system and with ggplot2.

## Installation

Please install from github via:

``` r
devtools::install_github("clauswilke/ggtextures")
```

## Example

Basic example of a textured rectangle drawn with grid:

``` r
library(ggtextures)
library(grid)

img <- magick::image_read("https://jeroen.github.io/images/Rlogo.png")

grid.newpage()
tg1 <- texture_grob(
  img,
  x = unit(.2, "npc"), y = unit(.05, "npc"),
  width = unit(.1, "npc"), height = unit(.9, "npc"),
  img_width = unit(.5, "in"), ncol = 1
)
tg2 <- texture_grob(
  img,
  x = unit(.5, "npc"), y = unit(.05, "npc"),
  width = unit(.3, "npc"), height = unit(.6, "npc"),
  img_width = unit(.5, "in"), ncol = 1
)

grid.draw(tg1)
grid.draw(tg2)
```

<img src="man/figures/README-texture-grob-1.png" width="100%" />

Basic example of textured rectangles in ggplot2:

``` r
library(ggplot2)
library(tibble)

data <- tibble(
  xmin = c(1, 2.5), ymin = c(1, 1), xmax = c(2, 4), ymax = c(4, 3),
  image = list("https://jeroen.github.io/images/Rlogo.png",
               "https://jeroen.github.io/images/tiger.svg")
)

ggplot(data, aes(xmin = xmin, xmax = xmax, ymin = ymin, ymax = ymax, image = image)) +
  geom_textured_rect()
```

<img src="man/figures/README-geom-textured-rect-1.png" width="100%" />
