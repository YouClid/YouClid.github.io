---
layout: post
title:  "Front End Update"
date:   2017-11-10 00:11:00-0400
categories: jekyll update
---
#### Joseph Sweeney, Ian Dechene

### Status

Currently, the front end shows a side by side of the text, with the visual that is created. You are able to jump between different stages or steps in the construction by using the left and right arrow keys. You are also now able to highlight over parts of the text and see the corresponding object in the visual also highlighted. This also works when hovering over objects in the visual.

### Data Structure Changes

So we've changed the structure of the `JSON` that the backend generates to enable the steps. We used to have two fields, `geometry`, which held all the necessary data to construct the scene, and `text`, which held the original markup text. We've introduced the `steps` field, which contains an array, of arrays of object ids. Each element of the outer array corresponds to a step in the contruction of the visual, and each element of the stage is an id that can be used to get the correct geometric object from the `geometry` field. 

We take this `steps` array and use it to construct multiple scenes, which we can then switch between to show the construction.

The plan is to expand this implementation to actually add animations between the steps, such as connecting two points with a line, or drawing a circle. The best way to do this is currently being evaluated.

### Refactoring

The way the frontend is currently structured is with a few functions, and a bunch of global variable, which is definitely less than optimal. This structure makes adding new functionality and interactivity very difficult because all the code to construct geometric objects is separated from the interactivity code and all of these functions modify the global state of the visual. 

This method enabled us to quickly iterate and add new functionality, but as we get closer to the functionality that we actually want, we need to think about a better way to structure the code.

We've recently stumbled across an API style called "Immediate Mode Graphical User Interfaces" or IMGUI. This is in contrast to most modern GUI API's, which we refer to as "Retain Mode Graphical User Interface" or RMGUI. The idea here is that with normal RMGUI API's, if you want to draw an object, like a rectangle, onto the screen, you would first instantiate a `Rectangle` object, add it to the scene, then call `scene.draw()` or `scene.render()`. 

With an IMGUI API, to draw a rectangle, all you do is call `drawRectangle()`. So instead of keeping a data structure with all the objects that you draw, then rendering that 60 times a second, you just individually draw each object with no overhead.

This enables you to write code like the following:

```js
if(drawRectangle(0, 0, 10, 100)) {
	// The rectangle was clicked
	// so do some action
}
```

So all the interaction code directly follows the code that draws your object. By creating the visual in an imperative manner, it makes it much easier to understand how the object behaves.

You might be thinking that this would be unweildy for more complex objects, but it actually makes it easier, to make more complex components.

```js
function drawComplexObject(args) {
	drawRectangle(...)
	drawCircle(...)
	
	if(drawButton()) {
		// Do more things
	}
	
	// Add anything else, and any more interaction that you may want
}
```

So if you want a more complex object, all you have to do is create another function that encapsulates the behavior of your new function. 


So the plan is to implement a simple test library that allows us to simplify the front end with an IMGUI like API. Then we'll update with a post on whether the test implementation was better than our functions and global variable everywhere.
