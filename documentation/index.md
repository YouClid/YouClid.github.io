---
title: Getting Started
permalink: /docs/home
layout: docs
categories: documentation
---

### Goal
The goal of our project is to create a modern, interactive, visualization of Euclid’s Elements.
In order to accomplish this, we were tasked with creating both a markup language, and a way to turn this markup language into the corresponding visualization.
As a team, we defined a generic “minimum viable product” in which a user could utilize their favorite text editor to mark up a section of Euclid’s Elements, then run a parser which would turn this markup into a static file that they could then open.
With this being said, we believe that our product will be able to accomplish much more than this.
We quickly realized that the end user could use our markup to create a visualization of something other than just Euclid’s Elements.
The user should be able to create arbitrary geometric figures, potentially even figures in three dimensions, using our markup and generate a representation that they could include in things like websites, academic papers, or documentation, just to name a few.
As such, we have tried to make design decisions that allow for our codebase to be flexible and easily modifiable as we anticipate the code changing quite dramatically during the development process.

### I Just Want To Get Started
```bash
git clone https://github.com/YouClid/youclid.git
cd youclid
echo "[line AB][loc A 0 0][loc B 0.5 0.5]" > example.yc
python3 backend/main_parser example.yc --output example.html
# Now open example.html in your web browser; you should see a line across the screen
```

### Where Does the Name Come From?
We want everyone to be able to quickly pick up on our markup language and start using with as little overhead as possible, yes, even *you*!
As such, the name "youclid" was born, stemming from the Greek mathematician, Euclid, and this desire.
