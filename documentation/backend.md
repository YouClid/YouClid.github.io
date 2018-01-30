---
title: Backend Architecture
permalink: /docs/backend
categories: documentation
layout: docs
---
In terms of a backend technology stack, we have been writing a parser in python3 to parse our markup and generate HTML.
We chose python3 due to our familiarity with it as well as the flexibility that it provides.
The choice of python3 over python2.7 stems from the fact that python3 is the future, and python2.7 will be EOL in 2020.
I have taken lead on the backend team and have been trying to develop the code in such a way that it is flexible to work with.
Since we anticipated our syntax changing frequently, we did not want to build the parser such that it was hard to modify.
The core of our parser is a dictionary mapping keywords (strings) to corresponding parser functions.
For example, we started out by only supporting parsing lines, points, and circles. As such, the structure of our code looked as follows:
```
parser_mappings = {
                   'line': parse_line,
                   'point': parse_point,
                   'circle': parse_circle
                  }
def parse_line(args):
    # Code to parse a line
def parse_point(args):
    # Code to parse a point
def parse_circle(args):
    # Code to parse a circle
```
When our parser encounters a piece of our markup, for example `[line AB]`, it first determines the object it is creating (a line).
Then, it does a lookup in the dictionary to find the appropriate function to call, and then passes the rest of the data for that markup (in this case the name, `AB`), as the `args` parameter.
This means that if we wanted to support other objects, all we would need to do is create a function to parse that object, add the add the mapping to the dictionary.
Unfortunately, we ended up doing a bit too much work in each of the individual parser functions, and ended up duplicating some code.
As such, we are in the process of making the individual parser functions more specific to their particular object and moving common code out of these.
However, the structure that we have in place makes such changes quite easy to work with.

When it comes time to generate the HTML, we simply take a template HTML file that defines a lot of the layout and includes the javascript written by the frontend team, and plug in the JSON that we have created to represent the objects.
Eventually, we anticipate creating a javascript version of the parser as well.
This will allow us to have the entirety of out project in one language, and means that we can host all of this code on something like github pages where anyone can interact with it.

One of the biggest architecture decisions that we had to make was was the flow of our backend process would look like.
Clearly, we wanted the writer to write code, give it to our parser, and they would get an HTML output.
However, what was not necessarily clear, was exactly how the user would use our parser to create this output.
Was our parser a compiler that the user needs to invoke manually?
Is it a javascript library that the user includes in an HTML file and then pastes the markup into?
Is it a sharelatex kind of site where the user uploads code and we compile it, providing them with the output?
For our first pass, we decided that taking a compiler like approach would be the easiest.
This means that we would be able to work in python, a language that we were all comfortable with, and could utilize aspects of the python standard library (for example regular expressions) to create a minimum viable product quickly.
However, we did not discount the other two possibilities.
In fact, our current implementation has its roots in the second thought (including a javascript library).
This is how the JSON that we generate is turned into a front end visualization.
The last idea, a sharelatex kind of site, is something that we want to be able to support in the future.
It would be really cool if we could host a site that would translate the markup to visualization live as the user types it.
We want to be able to use the technology that we have available to us, and Euclid did not, to take his work and create a more modern representation of it.
