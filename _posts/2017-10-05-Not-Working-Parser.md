---
layout: post
title:  "Not Working Parser"
date:   2017-10-05 18:20:00-0400
categories: jekyll update
---
#### Soumya Kundu, Sailesh Simhadri, Drew Monroe

### Updates
We have found numerous issues with our main parser function. While these issues can be fixed to handle Proposition 1, we have also realized that our approach to designing the parser needs rethinking, as we need a better system to delineate the relationships between the different objects that we wish to generate; as the complexity of the propositions increases, without a more general framework for specifying object relationships, we will be forced to encode each of these relationships individually, which will be both inefficient and inelegant. A greater degree of abstraction is needed for the parser. Also, we have developed a flask application that establishes a pipeline between the backend and the frontend to streamline the process of converting marked-up text to interactive geometric figures.

### Design Decisions
We have decided that we will be designing a new parser function that can better handle the relationships between different objects.

### Plans for Next Week
We will be reading the first few propositions of Euclid's Elements to gain a better understanding of the nature of the relationships that our parser function will need to handle, and then, we will design a new approach to construct the parser. One way to do this would be to reduce the text to only the essential keywords necessary to convert the text into displayable figures without losing any essential details, identify the attributes and relationships conveyed by those keywords, and then design a method to encode that information using a parser. A robust and versatile design for a parser framework now will ensure that our parser remains scalable as we approach the more complex parts of Euclid's Elements.
