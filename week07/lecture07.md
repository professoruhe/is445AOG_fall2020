---
title: Lecture 7
layout: lecture
visible_lec: true
visible_n: true
---

<!-- .slide: class="titleslide" -->

# Data Visualization
<div style="height: 6.0em;"></div>

## Jill P. Naiman
## Fall 2020
## Lecture 7

---

## Announcement #1: Office Hours Nov 3

In accordance with the UIUC/Illinois holiday, office hours Tuesday, Nov 3 will be by appointment only (so, email me if you want to chat!).  

There will be additional office hours on Thursday, Nov 5, 5-6pm.

---

## Announcement #2: Office Hours Nov 3

Short *anonymous* feedback survey.

---

## Where we are: Last week

<img src="images/dataviz_map_lastweek_take2.png">

notes: last week  we started playing with dashboarding using some randomly generated data in bqplot

we also started working with the Grammer of Graphics and used bqplot declaritively to start "painting" scales and axis on our canvas

we also talked about different viz engines and you got to look at this in the HW

---

## Where we are: Today

<img src="images/dataviz_map_thisweek.png">

notes: Today we'll continue building up dashboards

if we have time we'll also start talking about map projections this week (but we might only get to it next week)

---

## Today's Main Topics

 1. Interactivity and linked views
 1. More dashboarding
 1. Dashboards with maps
 1. Map projections (if we have time)

---

<br>
<br>
<br>

# TOPIC 1: Interactivity


---

## Interactivity

This week, we'll talk about some more basics principles of interactivity in
visualization.

What do you think of when you think of interactive visualizations?

---

## Interactivity: Parameters

<!-- .slide: data-background-image="images/brushlink_01.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

 * Point characteristics
 * Axis limits/bounds
 * Transform/scale

note: we'll think a little about different ways to manipulate each of these types of plot characteristics

---

## Interactivity: Parameters

<!-- .slide: data-background-image="images/brushlink_01.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

 * Point characteristics - Click-and-drag
 * Axis limits/bounds - Rectangle zoom
 * Transform/scale - Adjustment

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_02.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

`data(variable1, variable2, variable3, variable4)`

note: here we are plotting a set of data that is a function of 4 variables.

For example, this could be the amount you are late to class as a function of (1) how much sleep you got, (2) how excited you are about the topic that day (3) how nervous you are about the topic that day and (4) how much of your homework the dog ate.

here we are plotting 2 2d plots of this dataset - were we know intuatively each point is represented both as a dot on the first graph *and* as a dot on the 2nd graph

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_02.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

`data(variable1, variable2, variable3, variable4)`

`filter( variable2 > variable1 )`

note: now we are going to think about applying a simple filter, based around the first plot

we'll only show data where variable2 > variable1

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_03.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

`data(variable1, variable2, variable3, variable4)`

`filter( variable2 > variable1 )`

note: lets draw a line where the demarkation of our filter would be

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_04.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

`data(variable1, variable2, variable3, variable4)`

`filter( variable2 > variable1 )`

note: ... and lets take out all the data of both plots that has variable2 <= variable1

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_05.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

note: we can also select regions in our linked view

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_06.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

note: here are how these points are linked in the plot of variable3 vs variable4

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_07.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

note: so when we select with our brush in the first plot we can show what is selected in the second plot

---

## Interactivity: Linking & Brushing with UFO data

![](images/durationAllPoints.png)

note: as a "practical" example, we can for example make cuts in things like the
duration of UFO sitings for all years

---

## Interactivity: Linking & Brushing with UFO data

![](images/durationAllPoints_p2.png)

note: we can select only the longest sitings

---

## Interactivity: Linking & Brushing with UFO data

![](images/durationLongPoints.png)

note: this is how this plot would now look

---

## Interactivity: Linking & Brushing with UFO data

![](images/mapAllPoints.png)

note: and then we can see how the map changes

this is our original

---

## Interactivity: Linking & Brushing with UFO data

![](images/mapLongPoints.png)

note: this is how this dataset looks now w/o the shortest duration ufo sitings

---

<iframe width="1024" height="576"
src="https://www.youtube.com/embed/B7XoW2qiFUA?rel=0" frameborder="0"
allow="autoplay; encrypted-media" allowfullscreen></iframe>
[Link to video](https://www.youtube.com/embed/B7XoW2qiFUA)

note: here is one of the first examples of a "linked view" visualization machine.  We won't watch this whole video, but
if you are interested, they talk about how they can "interact" with different views

this was developed by SLAC (stanford linear accelerator)

prim9 = picturing, rotation, isolation & masking in up to 9 dimensions - for looking at multidimensional datasets
this was developed for particle data (so, like x,y,z and vx,vy,vz might be of interest)

---

## Implementing This

Two main approaches to the selection process:

 * Concurrent filtering ("masks")
 * Index-based selection (i, j - based)

What are the pros and cons of each?

What are methods of showing "linked" and "brushed" data if you have:

 * Scatter plot
 * Histogram
 * Field / image plot

---

<br>
<br>
<br>

# TOPIC 2: Dashboarding

---

## Recall: HW 6 this week

Build a dashboard for the buildings data.
 * Left component:
    * Grid heat map
    * Rows are congressional district
    * Columns are the governmental department (Agency Name)
    * Values are sum of total square footage for that set of criteria
 * Right component:
    * line plot
    * x is the year
    * y is total square footage acquired that year
 * These two should be linked so that you can select cells and that will update the square footage plot.
 * Things to think about:
    * Can you keep the x and y ranges static on the line plot?
    * Can you change the style?

---

## Today's Python Programming:

Starting with these ideas, we'll progressively enhance.

 * Create heat maps of the sightings in the UFO dataset
 * Select based on states (do not use map marks yet)
 * Manually create "bins" for aggregation
 * Use different scales for dates, times, locations

We'll use these to build up a _dashboard_ for our data.

---

## Dashboards: Tableau
![](images/Tableau-Sample-Training-Dashboard-Original.png)

notes: so here is an example of a dashboard, I *think* from Tableau.  Here we see a linked view which
displays data in several different ways to give the user the ability to visualize what their data
means spatially (with the map & region bargraph) and temporally (with the calendar/bar view at the bottom)

---

## Dashboards: Glueviz
![](images/histogram.png)

note: aside, there are opensource dashboarding type software, this is an example of glueviz that is
used a lot in astronomy and built on python

This is an example of binning light (dark or bright pixels) in an image of a star forming region (I think),
and linking this with a histogram which responds to a selection tool (in red) in the image.

---

## Dashboards: Building our own in Python

Why bother?

notes: so, given that there is dashboarding software out there, why would be bother going through the difficulty of doing it ourselves?

---

## Dashboards: Building our own in Python

Why bother?
 * Understand choices about data formatting/missing data

notes: the first reason is that we can learn a bit about what choices we make for "messy" data

---

## Dashboards: Building our own in Python

Why bother?
 * Understand choices about data formatting/missing data
 * Understand necessary data transformations

notes: next, we can learn a bit about how data is transformed to make it dash-boardable

---

## Dashboards: Building our own in Python

Why bother?
 * Understand choices about data formatting/missing data
 * Understand necessary data transformations
 * Understand data links

notes: also we want to understand the ways we can actually link parts of our data together -- what choices do we make to link data like this?

if we use dashboarding software, it can often obfuscate a lot of of these aspects

---

## Dashboards: Building our own in Python

# TOPIC 3: To Python for an intro to map dashboards!

notes: today we will get more experience building up these sorts of interfaces ourselves!
