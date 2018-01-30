---
title: User Experience
permalink: /docs/user_experience
layout: docs
categories: documentation
---

We defined two possible types of users for our application, a “reader” and a “writer”.
The reader is the person that is viewing the output of our program, the visualization, while the writer is the person that is using the markup to create a visualization.

### Reader
The basic goal of the reader should be able to see both the original text, as well as the visualization defined by our markup.
In addition, the reader should be able to easily determine which object in the original text corresponds to which object in the visualization.
For example, if the text contained a reference to a `point A`, it should be easy to determine where `point A` is in the visualization.
Finally, we believe that the reader should be able to determine how the visualization was constructed by animating through the various steps in the construction.
This is particularly important in regards to Euclid’s *Elements*.
The purpose of the *Elements* is to present a way to do basic geometric constructions.
As we are creating a modern representation of this text, we should be able to do things that Euclid could not have done when he wrote the text thousands of years ago.
One such way this can be done is by animating the construction.
This will allow the user to clearly see what steps are being taken, what it means to take each step, and how each step contributes to the final construction.
The idea of being able to do things that Euclid could not have done himself leads itself to other possible interactions for the reader.
Perhaps the reader should be able to customize the colors of the visualization to highlight various parts.
Perhaps the reader should be able to interact with the visualization, moving points and shapes around to alter the construction.
These represent design goals that we would like to incorporate into our finished product.


### Writer
We defined several goals that we believe all writers would like to see implemented.
The first is that our syntax is as easy to write as possible.
This utility should be usable by someone who does not necessarily have a computer science background, so creating a complicated programming language was out of the question.
By defining a syntax that is easy to use, we believe that we will be able to reach a larger audience.
Along a similar vein, our markup should be nice to use.
This means that there should be as little “boilerplate” as possible; the writer should only need to write the minimum to create a visualization, with the ability to add more complex syntax if desired.
As such, we adopted the design philosophy of making it easy to learn the base features that our markup supports and making the advanced features intuitive.
As a whole, using our markup should feel natural, and there should not be questions about why something was implemented the way it was.
If there are such questions, there should be explanations that show why that particular design decision was the one that makes the most sense.
Along the lines of feeling natural to write, our markup should feel natural to read.
We want to be as unintrusive as possible with our syntax, and ideally, the writer should be able to mark up Euclid’s *Elements* with no changes to the core text itself.
Part of the motivation behind being easy to read is that it will feel more natural to type, and people will enjoy working with our syntax.
Furthermore, once the writer has marked up their text, it should be easy to generate a output.
This means no complicated build processes; there should be one command to run, or one button to press on a GUI that will create the output.
Finally, we want to allow flexibility in writing.
The user should be able to use whatever text editor they are comfortable with to create their markup.
However, we also want the user to be comfortable using their text editor.
One of the nice features about text editors is that they will highlight the code for you, make it easy to distinguish between different elements in the code.
As such, we want to provide color schemes for common text editors (vim, atom, emacs, sublime, etc.) to make the user “feel at home” while writing in this markup language.
I have already created a few of these color schemes (vim and atom), and anticipate being able to create several more.
One of the nice things about these color schemes is that they are usually defined by some sort of regular expression.
By writing these schemes, it helps to determine if the structure that we have for our syntax is consistent, or if there are weird edge cases that we may want to rework.
This helps us to reach our goal of our syntax feeling natural and easy to write.
If there is vastly different syntax for various different parts of our markup, it will be more difficult for the writer to use.
This will allow us the ability to look at things through the eyes of someone who has not worked with our syntax before and see what could be changed to improve the experience.
