---
title: Euclid's Elements
permalink: /docs/euclids_elements
layout: docs
categories: documentation
---
### Book 1 Proposition 1
The markup of the proposition is below:
```
Let [line AB] be the given finite straight line.
It is required to construct an equilateral triangle on the straight [line AB]. [step]
Describe the [circle BCD] with [center A circle=BCD] and radius [line AB]. [step]
Again describe the [circle ACE] with [center B circle=ACE] and radius [line BA]. [step]
Join the straight lines [line CA] and [line CB] from the [point C] at which the circles cut one another to the points [point A] and [point B]. [step]
Now, since the [point A] is the center of the [circle CDB], therefore [line AC] equals [line AB].
Again, since the [point B] is the center of the [circle CAE], therefore [line BC] equals [line BA].
But [line AC] was proved equal to [line AB], therefore each of the straight lines [line AC] and [line BC] equals [line AB].
And things which equal the same thing also equal one another, therefore [line AC] also equals [line BC].
Therefore the three straight lines [line AC], [line AB], and [line BC] equal one another.
Therefore the [polygon ABC] is equilateral, and it has been constructed on the given finite straight [line AB]. [step]
[clear] [polygon ABC] [step]

[definitions]

[loc A -0.25 0]
[loc B 0.25 0]
[loc C 0 0.433]
[loc D -0.75 0]
[loc E 0.75 0]
```

This file is saved as `postulate1.yc`.
It is then run through the parser as follows:
```bash
python main_parser.py postulate1.yc --output postulate1.html
```
The `postulate1.html` file can be open in a browser to create an interactive page that looks as follows:

<img src="/jekyll-doc-theme/assets/postulate1.png" alt="postulate1">

Hovering over text on the left will highlight the corresponding geometric shapes on the right.
Hovering over a geometric shape on the right will highlight the corresponding text on the left.
Using the left and right arrow keys will toggle through the steps of the construction.
