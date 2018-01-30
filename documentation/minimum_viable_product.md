---
title: Minimum Viable Product
permalink: /docs/minimum_viable_product
layout: docs
categories: documentation
---

### Reader Minimum Viable Product
The minimum viable product story for the reader is as follows:
The user opens a web page that has the text and the visualization side by side.
The user can now step through the animations of the visual as specified by the authors.
The user can hover over text and see the corresponding geometric elements, and the user can hover over the geometric elements and see the corresponding text.

We believe that this accomplishes our three high level goals for the reader
1. Be able to easily see both the text and the visualization
2. Be able to easily tell which object in the text corresponds to the object on the screen
3. Be able to see the construction of the visualization.

### Writer Minimum Viable Product
The minimum viable product story for the writer is as follows:
The writer should markup some text in their favorite text editor.
They can then compile this into a static HTML file, which can be send to anyone and can be opened in a browser.

We aim to use this to drive the decision to accomplish the five high level goals for the writer
1. Easily be able to learn the syntax
2. Easily be able to write the syntax
3. Easily be able to read the syntax
4. Feel that the natural to write
5. Specify steps in which the visualization should be drawn in.

### Implementation
We are close to having a complete minimum viable product.
We have created the entire basic reader experience, as well as the writer experience.
However, there are a few bugs that we need to work out before we feel comfortable declaring the minimum viable product completed.
Furthermore, the backend and frontend code could use a rework/cleanup.
The frontend team has been working on removing dependencies from the code to create a self-sufficient codebase, and the backend team is working on restructuring the code to make it significantly easier to support other syntax elements in the future.
We will then be able to move on to some of the more advanced features that we want to implement, as well as add easily support for other geometric elements referenced by Euclid.
