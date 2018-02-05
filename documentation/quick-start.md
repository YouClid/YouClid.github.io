---
title: Quick Start
permalink: /docs/quick_start
layout: docs
categories: documentation
---

### Obtaining the code
```bash
git clone https://github.com/YouClid/youclid.git
cd youclid
pip install -e .
```

### Basic Syntax
We support the following primitives
- point
- line
- circle
- polygon

Any text that you wish to be parsed by our parser must be enclosed in `[]` (see below for examples).

### Drawing Points
In order to draw points, simply use the following syntax:
```
[point A]
```
This will create a point named `A`, however, the point will not be placed anywhere on the screen.
In order to place the point, you must explicitly give it coordinates, as follows:
```
[loc A x=0 y=0]
```
This will take a point, named `A`, and place it at `(0, 0)`.
The coordinates must be between `[-1, 1]` for both the `x` and the `y` coordinates.

### Drawing Lines
In order to draw lines, simply use the following syntax:
```
[line AB]
```
This will create a line from `A` to `B`, and will create points `A` and `B` if they do not exist yet.
Like you have to do with points, you must also give coordinates to the points `A` and `B` to get them to appear on the screen.
```
[loc A x=0 y=0]
[loc B x=0.5 y=0.5
```

### Drawing Circles
#### Creating a Circle From Three Points
In order to create a circle, simply use the following syntax:
```
[circle ABC]
```
This will create a circle, with points `A`, `B`, and `C` on the circumference of the circle.
Of course, you must explicitly give the points coordinates in order for them to appear.
Unfortunately, this syntax only supports single letter point names as of the time of writing this document.

#### Creating a Circle From a Center and a Radius
Another, more natural way to create a circle is from a center and a radius.
The syntax for doing so is as follows:
```
[circle myCircle center=A radius=0.5]
```
This will create a circle centered at point `A` with a radius of 0.5.

### Drawing Polygons
In order to draw a polygon, specify the letters of the points that you wish to be a part of the polygon.
The syntax for doing so is as follows:
```
[polygon ABCD]
```
Unfortunately, this syntax only supports single letter point names as of the time of writing this document.

### Text replacement
Our primary use case for this application has been marking up Euclid's *Elements*.
As such, we are creating side-by-side text with the geometric representation.
To specify particular text that the geometric object replaces, simply use the `text` keyword argument.
For example,
```
This is a [circle ABC text="circle named ABC"]
```
will generate the following text:
```
This is a circle named ABC
```

### Putting it all together
The following will create a square with a circumscribed circle, and a line representing the radius.
```
This is a circle named [circle c name=mycircle center=A radius=0.5 text=C]
This is a square named [polygon BCDE text=BCDE]
This is the [line AB text=radius]

[loc A x=0 y=0]
[loc B x=-0.353553391 y=0.353553391]
[loc C x=-0.353553391 y=-0.353553391]
[loc D x=0.353553391 y=-0.353553391]
[loc E x=0.353553391 y=0.353553391]
```

Now, compile the `.yc` file to create HTML.
From inside the `youclidbackend` directly, run the following command:
```bash
python3 main_parser.py /path/to/your/file.yc --output=../frontend/output.html
```
Now you can open up `output.html` in your browser to see the results.
