---
layout: post
title:  "Front End Plan"
date:   2017-09-22 11:00:00-0400
categories: jekyll update
---
#### Joe Sweeney and Ian Dechene

### Where We're At

So far, we've gotten THREE.js up and running in our browsers and are able to draw simple shapes with relative ease.
The last week or so has been reading the documentation for THREE and just becoming familiar with how it works.

### Plan

Immediately, there's a few things we need to do.

1. Write some intermediate code that takes the JSON that the parser team is outputting and render it.
2. Come up with our internal model of the geometries that we render to allow for flexibility in interactions and animations.
3. Add some simple interaction:
   * Move points around
   * Adjust scale on circles

We'll probably tackle 1 this week, and if we have time start refactoring our code for 2. 
The reason to go in this order is once we have the intermediate layer, we'll have a 
better understanding of how these geometries should be represented.

This is mainly a quick update, we should be in a much more impressive place this time next week.
