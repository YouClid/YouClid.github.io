---
title: Basics
permalink: /docs/basics
layout: docs
categories: documentation
---

### Delimiting the Markup
In order to delimit text as being a part of our markup, it must be enclosed in hard brackets (`[` and `]`).
Text that is not enclosed in brackets will not be interpreted by the parser.
If you want to write a literal hard bracket, such that it is not interpreted by our parser, simply escape it (`\[` or `\]`).


<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Discussion</h3>
                </div>
                <div class="panel-body">
                    The character that delimits our syntax has undergone several iterations.
					The first type of markup that we decided to use was a LaTeX like syntax.
					This would allow for clear delineation of our markup (we would use a command like <span markdown="1">`\point{A}`</span> to generate a point named A), and would also allow us to do inline markup.
					We thought that this syntax was more clear than HTML or XML tags, as we felt that those introduced a lot of overhead.
					One of the nice things about this kind of markup was that it was quite easy to tell what was marked up text and what was not.
					However, as we started working with this syntax, we quickly realized that it failed to meet some of the goals that we had set out for the writer, namely, that our syntax should be easy to write.
					While we were not doing anything particularly complicated in terms of our syntax, it was annoying to use.
					As silly as it sounds, the <span markdown="1">`\`</span>, <span markdown="1">`{`</span>, and <span markdown="1">`}`</span> characters were a hassle to type, and would break the natural flow that someone writing a piece of text would usually have.
					As such, we switched to using the <span markdown="1">``` ` ```</span> character to delimit our markup.
					This meant that one would create a point A as follows: <span markdown="1">``` `point A` ```</span>.
					This kind of markup had the nice feature that it was very unintrusive to the eye.
					It made the markup for Euclid's Elements look quite like actual text, in that there was little overhead, which was something that we liked a lot.
					While the backtick character was still somewhat annoying to use, at least the writer only had to press two keys when they wanted to start using our markup, as opposed to three.
					We felt that these two features created a better flow than the previous style that we were using.
					However, this style had an unintended drawback: while it was hard to notice the markup, which was nice when reading the text, it was also hard to notice the markup, which was bad when trying to figure out where one misplaced a backtick.
					We quickly realized that our parser would have to way to determine if someone missed a backtick, or if they added in an extra.
					This would not be possible if the delimiter for starting and ending the syntax was the same.
					As such, we switched our delimiters once again.
					This time, we decided that we would use the hard brackets, <span markdown="1">`[`</span> and <span markdown="1">`]`</span>, to delimit our markup.
					While this style is much closer to the LaTeX style, it is slightly more simple (and at least somewhat less of a hassle to type as at least the user does not need to press shift).
					It also has the added benefit over the backticks in that the starting and ending delimiter are different from each other, making it easier to raise errors in the parser.
                </div>
            </div>
        </div>
    </div>
</div>

### Syntax Structure
When creating objects, the basic syntax structure is as follows:
```
[object_type object_name key=value otherkey=othervalue]
```
Each argument inside of the brackets is space separated.
There is currently no support for keys or values that have spaces in them, although this feature is planned to a future release.
There are a few types that do not follow this structure (see below).
We plan to add support for objects that do not have names, however, they cannot be referenced again if they are not given a name.
If provided, the positional `object_name` argument will be treated as a list of single letter points that make up the object.
For example, the following creates a line with endpoints named `A` and `B`.
```
[line AB]
```
It is important to note that even if points `A` and `B` have not yet been created, they are implicitly created when creating this line.
We do not currently support the ability to give objects a name that is not just made up of the points.

<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Discussion</h3>
                </div>
                <div class="panel-body">
                    The use of keyword arguments came about as a way to prevent users from needing to remember what order arguments needed to be provided in.
                    Furthermore, they allow the user flexibility to only speicfy the arguments that they care about.
                    For example, if the user wanted to create a circle centered at a point with a given radius, they could simply do the following:
                    <span markdown="1">
                    ```
                    [circle ABC center=D radius=0.5]
                    ```
                    </span>
                    This syntax is also more readable than alternatives that we considered, such as
                    <span markdown="1">
                    ```
                    [circle ABC D 0.5]
                    ```
                    Here, it is not clear what <span markdown="1">`D`</span> is, nor is it clear what <span markdown="1">`0.5`</span> represents.
                    Keyword arguments are also easier to implement in the parser, since to add support for another argument, we simply need to add the code inside of the parser function for the particular object, and the syntax itself does not need to change at all.
                    At first, it may seem counterintuitive that we have an optional positional argument (the name) at all.
                    If keyword arguments are more clear, why allow a positional argument?
                    In this case, we felt that a positional argument was easier to write than the keyword argument, and did not lose any readability.
                    Creating a line from two points should be easy.
                    As such, a syntax like
                    <span markdown="1">
                    `[line name=AB]`
                    </span>
                    added too much unnecessary overhead.
                    If all the user wants to do is create an object from points, there should be no need to type out the full keyword.
                </div>
            </div>
        </div>
    </div>
</div>

### Displaying Objects
In order for objects to be displayed, you must give them explicit coordinates.
In order to do so, we provide the `[loc]` command, which takes two arguments (an `x` and a `y` coordinate).
In order for a point to be displayed on the screen (an consequently any objects that use that point), it must be given coordinates.
The `[loc]` command can occur at any point in the markup (as long as it isn't inside of another object).
This means that you gave give the coordinates for a point before or after you declare it elsewhere in the markup.
We suggest placing all of these coordinates the bottom of your markup, so that they don't clutter the rest of the document.

<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Discussion</h3>
                </div>
                <div class="panel-body">
                We force the user to provide explicit coordinates out of convenience for the backend parser, and this requirement will be removed as soon as possible.
                Ideally, the user would not need to specify any coordinates (or a minimal subset of the coordinates needed), and the backend would dynamically generate coordinates for any other points such that the geometric constraints are preserved.
                We have had several design dicussions about the best way to do this.
                Our initial plan was to assign points random coordinates until we could calculate the rest of the coordinates, however, sometimes the placement of a point is dependent upon the placement of other points.
                This would require a method to represent dependencies between objects.
                We also considered taking a constraint-based approach, where we define constraints between objects and allow the computer to solve the system of equations.
                We also considered doing a rough calculation of the coordinate of the points and then projecting the points onto their appropriate object to give them coordinates.
                However, each approach takes time, and prevented us from creating our minimum viable product.
                As such, we have tabled the dynamic coordinate generation until we are satisfied with the basics of our program and will revisit the issue then.
                </div>
            </div>
        </div>
    </div>
</div>
#### Supported Primitives
Below is a list of the primitives that we currently support.
For a more complete description of these primitives, see the [Primitives documentation page](/jekyll-doc-theme/docs/primitives/).
- point
- line
- circle
- polygon

#### Other Supported Objects
Below is a list of the other objects/keywords that we support.
For a more complete description of these, see the [Other Supported Objects documentation page](/jekyll-doc-theme/docs/other_types/).
- loc
- center
- step
- clear

#### Supported Keyword Arguments
Currently, there is only one supported keyword arguments.
For `center` objects, the `circle` keyword argument can be used to provide the center for a circle.
The value for the `circle` keyword must exist prior to creating the `center` object.
The next keyword argument that we plan to support is the `name` keyword argument to allow for names to be provided to objects other than via the positional argument.
