---
layout: post
title:  "Working Parser"
date:   2017-09-27 07:08:00-0400
categories: jekyll update
---
#### Drew Monroe, Soumya Kundu, Sailesh Simhadri

### Updates
We have made lots of progress since last week.
We have created a (basic) parser that, while it certainly has flaws, is at least capable of parsing the first postulate.
We made several design decisions this week, and while there are quite a few decisions to be made still, we are hoping to have a full end-to-end demonstration by Friday.

### Design Decisions
The first decision we needed to make was how we were going to store objects.
We wanted to store them in a dictionary so that we would know if we had already created the particular object before.
For example, if we created `Point(A)` and stored it in the dictionary, we would be able to determine if we already have created `Point(A)` previously by performing a lookup in the dictionary.
However, we realized that we would need a key into this dictionary.
Hashing the object itself did not feel right, since we would then need to have the object (hence creating a new object, or already having the object) to check if it was already in the dictionary.
We decided that we would, for simplicity's sake, use the name of the object as the key, and assume that the user would specify the name of the object only by the points that define the object.
For example, `line(AB)` would contain the two points `A` and `B`.
However, this raised another problem: how do we know if we are accessing two objects that are the same, even though their names are not technically the same?
For example, `line AB` and `line BA` represent the same line, however, the string representations of their name (`AB` and `BA`) are not the same.
To solve this problem, we decided that we would sort the points lexicographically before we checked if the object was in the dictionary.
While this might create some problems in the future (for example, if the ordering of points matters), at least for now, it gives us a solution to do an end-to-end test.
Furthermore, this does not address cases such as the following: points `A`, `B`, `C`, and `D` all exist on the same line.
Hence, `Line CD` would be the same as `Line AB`.
In the future, we hope to solve this issue by storing the equation that defines the line (or object) with the object itself.
There also arose the issue of potentially creating an object that required points that did not yet exist yet.
For example, the first postulate begins with:

>Let AB be the given finite straight line.

Points `A` and `B` do not exist yet, however, they are needed to define the line.
We decided that, if given an object that required points that did not yet exist, we would create the points during the creation of the object itself and add the points to our object dictionary.

After talking with the frontend team, we decided to use JSON as an intermediate representation for now.
While we had suspected that this would be the case last week, we have since hammered out exactly what the frontend team should need in order to create a visualization.
We will be sending marked up text (which will hopefully give the frontend team the ability to markup the text in the browser), as well as a list of JSON objects to be plotted.
In order to give them all the data that they will need to plot their points, we generate random coordinates when we create a point.
These values can be updated, and although not yet supported by our parser, we aim to allow the user to specify `x` and `y` coordinates if needed.

### Plans for Next Week
By this time next week we aim to have successfully demonstrated that we can mark up a postulate, run it through our script, and generate a visualization.
We also will need to mark up more postulates so that we can determine what other kinds of syntax we need to support in our markup language.
As mentioned above, there are several janky things that we needed to do in order to get a working parser, and some of our design decisions are not yet final.
Hopefully we will be able to come up with a better way to solve some of the problems that we encountered.
