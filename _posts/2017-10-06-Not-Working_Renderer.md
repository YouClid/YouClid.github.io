---
layout: post
title:  "Not Working Front End"
date:   2017-10-06 10:35:00-0400
categories: jekyll update
---
#### Joe Sweeney, Ian Dechene

### Updates
We've had better success than the backend team but we still have a lot of work to go.
So far we've:

1. Wrote the code to use the JSON that the parser generates and draws the shapes.
2. Added simple interaction so points and shapes can be moved around.

Both of these have two major catches. 

Number 1 works, except there's an unknown bug when converting from normalized device coordinates, which is what the parser outputs, to world coordinates. What we see is that a certain aspect of the geometry doesn't hold when converting. For example, if we have circle `ACE` with center `B`, we can either draw the circle where the center lies on `B` but some of the points don't lie on the circle, or all points `A, C, E` lie on the circle, but we're no longer centered around `B`. The cause of this is unknown.

Number 2 also works, except the constraints between shapes aren't respected when moving one of them. For example, if we have line `AB` and then we move point `A`, only the point moves, but not the line. In order to solve this, we need some way to represent these constraints so that changes can easily be propogated to the rest of the geometry.

### Plans for Next Week
Our plan for the next week is to work on these two bugs. 

After both of these problems are solved, we'll begin to refactor all the Javascript we've written so far because it's a jumbled mess.
