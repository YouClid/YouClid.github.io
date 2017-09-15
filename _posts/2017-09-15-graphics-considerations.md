---
layout: post
title:  "How do we draw our shapes?"
date:   2017-09-15 12:00:00-0400
categories: jekyll update
---
#### Joe Sweeney

### Front End

An essential component of this project is going to be drawing shapes onto the screen. 
So one of our first choices is going to be how do we do this? What technologies do we
use? What are the actual requirements going to be and how do we meet them?

First let's look at what we actually need to be able to do.

### Requirements

We want to choose a method that will work for any of these cases.

* Draw simple shapes (i.e. points, lines, circles, quadrilaterals, polygons)
* Easily viewable and usable
  * No extra installation required 
* Create animations
* Draw more complex geometries (three dimensional visualizations)
* Move these shapes around interactively
  
### Decision

Given these requirements, our first implementation is going to be web based. This
allows us to easily share the visualizations and support any system that a user may
have. Specifically, we are going to be using the WebGL API with the `canvas` element
because these are now supported across most modern browsers. It also supports any 
use case that we may have, because it's a general purpose graphics API. 

The plan is to start using [three.js](https://threejs.org), a nice wrapper around the 
WebGL API because none of us have experience with graphics programming so using the WebGL 
API directly may cause more problems for us than it solves. In addition, three.js
is highly regarded in its accessibility and usability which will allow us to get started
quickly, with a technology that will be able to accommodate any situation that comes up.
As we become more familiar with graphics programming, we have the option to move to the WebGL
API without a wrapper if we become constrained by three.js.

