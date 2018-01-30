---
title: Color Schemes
permalink: /docs/color_schemes
layout: docs
categories: documentation
---
We currently have colorscheme support for vim and atom.
These color schemes can be [found on our Github page](https://github.com/YouClid/youclid/colors), and installation instructions are [documented in the README](https://github.com/YouClid/youclid/blob/master/README.md).
I will walk through the process of creating a colorscheme for atom with the thought that this process can be applied to other editors.

##### Grammar

The first thing that must be done is to define a grammar which defines the language.
In atom, this is done via a `.cson` file.
The file contains some metadata about the file type that it is applied to, and then a pattern (regular expression) that defines how to match text.
This regular expression should have extraction groups.
This will allow colors to different parts of the syntax.
We define 4 objects that we want to stylize.
The first is the leading bracket.
We ensure that we match a `[` character that is not escaped and create an extraction group for this bracket.
We also do the same for the closing bracket, `]`.
These brackets are give a name `keyword.youclid.bracket`.
We then match a word up until a space (the type of the object).
After that is the name of the object.
Finally, various arguments that can be passed to the object.
Each of these is extracted and given its own name.
Now, we can apply a style to each of these names.

##### Styles

Now that we have extracted various objects, we can apply a style to each object.
The name of the object represents a unique identifier for the style of object.
We create a `.less` file that maps the name of the object to a particular color.
Atom allows the user to specify RGB colors for each object.
What is nice about segmenting syntax highlighting in this way is that anyone can plug in another style file and change the colors of the highlighting, however, the core structure of what is highlighted (defined in the grammar file) will remain the same.
