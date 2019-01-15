---
title: "Introduction to Shiny"
---

{{% notice info %}}

This site is no longer updated, and elements of it may no longer work. The workshop was converted to a half-day workshop, which is offered by Research IT  at the University of Manchester.  The workshop materials can be found at https://uomresearchit.github.io/r-shiny-course/  

Details of Research IT's training courses can be found at [here](https://www.staffnet.manchester.ac.uk/staff-learning-and-development/academicandresearch/practical-skills-and-knowledge/it-skills/research-computing/research-courses/)


{{% /notice %}}

This is the "Data Visualization Using Shiny" workshop for the 2018 [Research Software Engineers' Conference](http://rse.ac.uk/conf2018/)



# Introduction

Shiny lets us build interactive web apps, using R.   This means we can use (pretty much) all of R's extensive (and extensible) data analysis and visualisation features in our app.  Essentially, we can take almost any analysis we've done in R, and then make it interactive.   We can run our apps locally, within R Studio (this is what we'll do most of today), make them standalone, either by deploying them to a [Shiny Server](https://www.rstudio.com/products/shiny/shiny-server/), or to a hosting service, such as https://shinyapps.io (we'll do this today), or even including them in a Markdown document.

R studio provide a gallery of other Shiny apps: https://shiny.rstudio.com/gallery/

Shiny works well with many widely used R packages, such as [ggplot2](https://ggplot2.tidyverse.org/), and [Leaflet for R](https://rstudio.github.io/leaflet/).  

In this workshop, we're going to use data from the [Gapminder project](https://www.gapminder.org) to visualise how GDP per capita and life expectancy have changed over time.   This takes one of Hans Rosling's 
innovative visualisations and puts it into Shiny. 
{{< youtube id="jbkSRLYSojo" start="90" >}}

We'll replicate this in Shiny (albeit without the smooth animation between years):
<!--. A deployed version of the app is at https://mawds.shinyapps.io/worked_example/ -->

<iframe src="https://shinyapp.mawds.co.uk/app/worked_example/" style="border:none; width:100%;  height:700px"></iframe> 

{{% notice info %}}
I've tried to minimise the amount of non-Shiny material in this workshop, but we will need to do some manipulation of the data. I've adopted a [tidyverse](https://www.tidyverse.org/) based approach to doing this, using pipes and filters.  If you're more comfortable using base R you're very welcome to use that approach.   If you need a quick refresher on using the tidyverse to manipulate tabular data, [this episode](https://uomresearchit.github.io/r-tidyverse-intro/04-dplyr/) of the [Data Analysis using R course](https://uomresearchit.github.io/r-tidyverse-intro/), which we teach at the University of Manchester may be useful.
 
To minimise the amount of formatting of graphs etc, I've provided functions that will generate the graphs we'll be using, given an appropriate data set.  Where these functions are used you could use your own call to `ggplot()`, `plot()` etc.
{{% /notice %}}


## How the workshop materials work

The material we'll use for this workshop are in the `~/mawdsley` directory.  This contains the gapminder data we'll be plotting (`gapminder.rds`), the Shiny app we're going to be making  (in `worked_example/`) and some example code showing how to produce (static) graphs of the gapminder data (in `codeExample.R`).  The example code uses the functions in `plottingFunctions.R` to produce the graphs; this is to reduce the time we spend dealing with the intricacies of ggplot2.

The directory is a git repository.  Each commit is tagged, and represents the solution to an exercise, or a "checkpoint" in the workshop.   The workshop VM is configured so that the initial commit, [git:00_workshopdata](https://github.com/UoMResearchIT/RSE18-shiny-workshop-materials/commit/c24d957e61c1fcc90bee9cad7204a89a1cab882b), is checked out.  This contains the data and functions we'll be using.   Within this website, links to the commits are clickable, and will show you the diff of that commit on github.  

You should try the exercises in your own directory (outside of `~/mawdsley`). If you get stuck, or your code gets horribly broken you can checkout the appropriate commit in `~/mawdsley` by changing to that directory and using:

```bash
git checkout tagname
```

(For example, `git checkout 09_richcountry` will take you to the finished app.)

You can then copy the working code to your directory and carry on from there.


