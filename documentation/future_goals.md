---
title: Future Goals
permalink: /docs/future_goals
layout: docs
categories: documentation
---
We have repeatedly try to think about what we could implement that would make this project “wildly successful”.
We think that we have a solid minimum viable product, however, want to add features that will set our project apart.

### Dynamic Visualization Generation

A big piece of this is interaction and dynamic visualization generation.
Currently, the writer needs to specify the location of the points on the screen to be drawn.
This approach works, but takes away from the spirit of the Elements, where someone should be able to follow a set of steps and come up with an output without needing to explicitly define where everything lies on the plane; the construction should force the points and geometric shapes to create the final product.
As such, we want to require the user to only specify as few constraints as possible to create the image, and our parser will dynamically determine where the points need to be placed to fix the geometric constraints.
We have experimented with a few ways of doing this so far.
We originally were trying to randomize some of the locations of the points and then use the geometric constraints to do the math for where the other points needed to go.
However, this approach was complicating the backend code significantly, and was starting to eat a lot of our time.
We decided to table this approach until we had a more solidified parser that we could possibly integrate this into.
We also dabbled with a python constraint based programming library, python-constraint, where we provide a set of variables and geometric equations as constraints, and the library will dynamically determine where the points need to be located.
There were a few problems with this approach however.
The first was that we were running into issues with floating point arithmetic.
Sometimes, the library would be unable to solve the equation due to floating point numbers not providing exact equality.
We tried to provide bounds for which solutions could be acceptable, however this sometimes would yield too many solutions and would take too long to compute.
We tabled this approach as well, however, we feel that it may be a viable way to proceed in the future.
We also have a library provided to us by our advisor, Don Sheehy, in which the points are giving initial starting locations and the code will project the points onto their constraints.
This approach may be the best way to proceed, and we will be playing around with this idea further.

### Frontend Interaction and Customization

We also want the user to be able interact with the visualization, trying to move the points around, and have the frontend keep the geometric constraints.
Another form of interaction is to allow the user to change the colors of the geometric shapes to suite their needs.
This could be done via CSS, allowing the writer to completely customize the way in which the page is drawn, or via some frontend interface, allowing the reader to completely customize their viewing experience.

We are also imaging a web site or application that renders the visualization in real-time as they type it.
This would allow the writer to easily see what they are typing to ensure that the visualization is what they intend.
One of the problems with this is that we might be taking the writer out of their preferred developing environment and forcing them into a less feature-filled editor that we would be providing.
As such, it would be nice to provide this as a plugin for the text editor that the writer prefers.
While this may not be possible for all text editors, it may be possible for something like atom.
Since atom is built on electron (which is just a javascript application), it may be possible to integrate our parser and visualization renderer as an atom plugin.
This would require a bit of work, we would need a version javascript version of our javascript parser, but would produce results that would make it very easy for the writer to verify what they are generating.

### The Next Dimension

A natural extension of our project is to allow it to support 3D.
Everything we have programmed so far has been to support creating visualizations in 2D, however, it is often three dimensional constructions that are the hardest to visualize without computer aid.
We think that our product will allow for ease of creating visualizations, and we think that since we have a solid framework already in place, it should be possible to extend our two dimensional procedures to three dimensional procedures.

### Advanced Syntax Features

Finally, we want to be able to provide “advanced” syntax features to turn our syntax into more of a programming language.
Thinking in terms of Euclid’s constructions, he often will refer to previous constructions, utilizing them to create a more advanced construction.
We want to be able to do a similar sort of thing, and provide a way to define algorithms or procedures that people can use to create even more complex visualizations.
I personally am very excited to try to tackle this sort of problem, and think that it would help our markup to become fully formed.
There will certainly be interesting design challenges to be made around implementing this, but I think that we as a group are up to the challenge!

### Creating the Entire Reader Experience

Finally, we want a way to create the entire reading experience.
For something like the *Elements*, which is a book, we would like a way to link to older propositions or definitions, and a way to go to the next.
Essentially, we would like a way for the writer to create a sort of eBook that the reader could use.
This would help to bring Euclid's *Elements* to more people, and would hopefully help to provide a mechanism for people to distribute contend in an interactive way.
This could be useful for people who write papers or blogs as well, having a way to reference previous posts or pages.
