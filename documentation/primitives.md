---
title: Primitives
permalink: /docs/primitives
layout: docs
categories: documentation
---

### Point
The most basic of primitives is the `point`.
The point supports two coordinates, an `x` and a `y` coordinate, representing the location of the point in the Cartesian plane centered at `(0, 0)`.
While we only currently support two dimensional points, we plan to support three dimensional points as well.
In order to create a point, the writer must do the following:
```
[point A]
```
This will create a point named `A`.
In order to give the point coordinates, the `[loc]` keyword must be used; [see the Other Types page](/jekyll-doc-theme/docs/other_types/).
Currently, only single letter named points are allowed, however, we plan to allow points with longer names in the near future, once we solidify support for keyword arguments for all objects.

### Line
A `line` (technically a line segment in our code) is made up of two points representing the end points of the line.
Much like a `point` can only currently be given a single letter name, a `line` can currently only be given a two letter name, which each letter representing the single letter for a `point`.
In order to create a line, simply do the following:
```
[line AB]
```
This will create a line with one endpoint as `point A` and the other as `point B`.
If the endpoints exist already, the code will use the existing endpoint, otherwise, it will create one.
For example, if `point A` already exists, `[line AB]` will not make a new `point A` but will instead use the already created one.
This means that the follow produce identical results
```
[point A]
[point B]
[line AB]
```
and
```
[line AB]
```
<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Decision</h3>
                </div>
                <div class="panel-body">
                    Having the <span markdown="1">line</span> object automatically create the points if they do not exist felt natural to us, and we were all in agreement that this should be the default behavior.
                    If the user wanted to create a line between two points, they should not need to create the points first, they should be created automatically if they do not exist.
                    This makes it easier to create objects and requires less typing from the user.
                    We also felt that this behavior would almost be expected.
                    As such, we extended this idea to all of the objects that we support.
                </div>
            </div>
        </div>
    </div>
</div>

### Circle
A circle is defined by three points on the circumference of the circle.
Like the other primitives, these points can currently only have single letter names.
As such, a circle can only have a three letter name, with each letter representing a `point`.
To create a circle, simply provide these three points as an argument to the `circle` type, as follows:
```
[circle ABC]
```
Much like a `line`, this will create the points if they do not already exist, and will use existing points if they do.

<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Decision</h3>
                </div>
                <div class="panel-body">
                    Geometrically, there are two ways to define a circle

                    <ol>
                        <li>A center and a radius</li>
                        <li>Three unique points</li>
                    </ol>

                    As we are using Eulcids <span markdown="1">*Elements*</span> as the basis for our testing and examples, and his first proposition defines a circle by way of three points, that was the syntax that we decided to support first.
                    However, we are in the process of implementing a circle that can be defined via a center and a radius using keyword arguments.
                    This will gives users the flexibility to use either notation, depending on their needs.
                </div>
            </div>
        </div>
    </div>
</div>

### Polygon
Much like the other primitives, a `polygon` is defined by a series of `points`.
Unlike a `circle` or a `line` however, the ordering of the points for a `polygon` matters.
We connect each consecutive `point` with a `line` to create the `polygon`.
This means that `polygon ABCD` will be different from `polygon ACDB`, even though they are comprised of the same points.
You create a `polygon` as follows:
```
[polygon ABCD]
```
This will implicitly create all a `line` between each consecutive `point`, and as such, will implicitly create each `point` if it does not already exist.
As such, the above declaration is equivalent to the following (however the above is obviously much more compact):
```
[point A]
[point B]
[point C]
[point D]
[line AB]
[line BC]
[line CD]
[line DA]
[polygon ABCD]
```

<div class="row">
    <div class="col-lg-12">
        <div class="bs-component">
            <div class="panel panel-primary">
                <div class="panel-heading">
                    <h3 class="panel-title">Design Decision</h3>
                </div>
                <div class="panel-body">
                    Originally, we had a <span markdown="1">`triangle`</span> datatype.
                    However, we quickly realized that if we wanted to support polygons with arbitrary sides, having a type for each possible polygon would not only be unfesible from a design end, but it would also be very annoying for the end user.
                    As such, we switched to a generic <span markdown="1">`polygon`</span> object.
                    The type of the polygon will be based upon the number of points that are provided to the polygon.
                </div>
            </div>
        </div>
    </div>
</div>
