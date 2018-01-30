---
title: Other Types
permalink: /docs/other_types
layout: docs
categories: documentation
---

### Location
In order to give the points coordinates, the `loc` keyword must be used.
This takes three parameters, the name of the `point` to give the coordinates to, the value of the `x` coordinate (between -1.0 and 1.0), and the value of the `y` coordinate (between -1.0 and 1.0).
An example of this is as follows:
```
[loc A -0.25 0.5]
```
This will create a `point A` (if it does not yet exist), and give it the coordinates `(-0.25, 0.5)`.
If `point A` already existed, then the coordinates would be assigned to the preexisting `point`.
<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Decision</h3>
                </div>
                <div class="panel-body">
                    For a discussion of this keyword, see the discussion in the <span markdown="1">["Displaying Objects" section of the Syntax Basic page](/jekyll-doc-theme/docs/basics/)</span>
                </div>
            </div>
        </div>
    </div>
</div>

### Center
The `center` keyword is used to give a `center` to a `circle`.
Unlike other objects, the `center` assumes that the `circle` exists prior to being created.
Creating a `center` object requires two arguments, a positional argument representing the name to give to the center `point`, and a keyword argument (`circle=`) to assign the center to.
This object exists to allow for the word `center` to be replaced in Euclid's *Elements*, instead of the word `point` by our parser.
This object may disappear once we allow custom text to replace words.
To create a `center`, use the following syntax:
```
We must assume that a [circle ABC] exists first.
[center D circle=ABC]
```

### Step
The `step` keyword can be used to provide a natural grouping of elements to appear on the screen at a time.
Elements between `step` commands will be grouped together.
Each group will be overlayed on top of the previous layer.
You should not include a `step` command at the top of the file, however, you should include one at the end to delimit the end of the last step.
The reader can use the `left` and `right` arrow keys to toggle through the steps.
Below is an example usage of the command:
```
These three objects, [line AB], [circle ABC], and [circle DFG] are grouped together. [step]
Once the user presses the right arrow key, [line CD] will appear on the screen. [step]
```

<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Decision</h3>
                </div>
                <div class="panel-body">
                    The original design motivation for supporting the <span markdown="1">`[step]`</span> command was to provide a way to walk through steps in Euclid's <span markdown="1">*Elements*</span>.
                    When trying to follow a construction for a proposition, we thought that it would be useful for the reader to see what happens at each individual step, so that there could be a clear visual correspondence.
                    If doing a construction by hand, you would be able to follow the text as you created each object, which could help to provide a better understanding of what is going on.
                    If you just saw a static image, this would be lost.
                    As such, we decided that we would allow the write to specify steps in the construction that provide natural breakpoints, as the benefit may extend to more than just the <span markdown="1">*Elements*</span>.
                </div>
            </div>
        </div>
    </div>
</div>

### Clear
The `clear` keyword can be used to remove old objects from being displayed.
Any object from the current step, or from previous steps, will not be displayed on the screen, until it is referenced again.
Below is an example usage of this command:
```
[line AB] [line BC] [point D] [step]
[clear]
[line AB]
```
After the reader goes through the first step, `line AB`, `line BC` and `point D` will no longer be displayed on the screen, and then `line AB` will be redrawn.
<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Decision</h3>
                </div>
                <div class="panel-body">
                    While the <span markdown="1">`[step]`</span> command allows for elements to be displayed in groups over each other, there was no way to remove old groups.
                    As such, we implemented the <span markdown="1">`[clear]`</span> command to allow for the writer to clear the screen if there was a need to prevent old objects from being displayed.
                    We use this in our examples to display the final part of Euclid's construction, so that the reacher can see the final result.
                </div>
            </div>
        </div>
    </div>
</div>
