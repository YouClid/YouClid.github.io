---
title: Formal Definitions
permalink: /docs/formal_definitions
layout: docs
categories: documentation
---

Below contains a formal description of what is and is not allowed in terms of our syntax.
This file can be found in [yc-format.txt](https://raw.githubusercontent.com/YouClid/youclid/feature/documentation/yc-format.txt) in the `documentation` branch on our github.
We aim to merge this into the `master` branch soon, once the rest of the team has had time to review it.
It shall serve as the formal definitions of how someone is supposed to write our syntax.
The document should be completely self-sufficient; anyone should be able to read it and understand how to write our syntax perfectly.
```
                        .yc File Format Specifications

Drew Monroe, Sailesh Simhadri, Joseph Sweeney, Soumya Kundu, Ian Dechene
University of Connecticut

Introduction

    This document outlines the specifications for writing files in the .yc file
    format. Currently, this file format can be parsed by our python parser to
    generate HTML pages.

Status of this Document

    This document is currently a draft and is subject to change without notice.

Definitions

1.  The terms "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
    "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to
    be interpreted as described in RFC 2119.
2.  The "[" and "]" characters will be referred to in this document as the
    BRACKET characters. The "[" character will be referred to as the
    OPEN BRACKET character, and the "]" character will be referred to as the
    CLOSED BRACKET character. When talking about both characters, the term
    BRACKETS will be used.
3.  The "\" character will be referred to in this document as the BACKSLASH
    character.

Specifications

1.  All text that is desired to be parsed MUST be enclosed by BRACKETS. The
    first character MUST be the OPEN BRACKET character, and the last character
    MUST be the CLOSED BRACKET character. All keywords MUST be enclosed by the 
    BRACKETS to be interpreted by the parser
2.  Text that is not enclosed by the BRACKETS will be treated as normal text.
3.  In the event that a BRACKET is to be interpreted literally in the text,
    it MUST be escaped by a BACKSLASH character.
4.  Words inside BRACKETS MUST be separated by a single space.
5.  The first word inside BRACKETS MUST represent the type of the object 
    and MUST be one of the following:
        - line
        - circle
        - center
        - point
        - polygon
        - loc
        - step
        - clear
        - definitions
6.  In order to be referenced, an object MUST have a name parameter assigned.
7.  The second word inside BRACKETS MAY represent the name of the object and
    SHALL be the name of the points that define that object, each represented 
    by a single character.
8.  If an name is defined through a keyword, the name SHALL NOT be parsed into 
    points.
9.  All arguments to an object MUST be keyword arguments, excluding the name 
    and type.
10. For the “center” keyword, the third word inside the BRACKETS MUST be 
    “circle=ABC” where ABC MUST be the name of the circle object.
11. For the “loc” keyword, the third word inside BRACKETS MUST be a floating 
    point number that represents the x coordinate of the point between -1.0 
    and 1.0 inclusive.
12. For the “loc” keyword, the fourth word inside BRACKETS MUST be a floating 
    point number that represents the y coordinate of the point between -1.0 
    and 1.0 inclusive.
13. For each point specified, either explicitly by the “point” keyword, or 
    implicitly by using a “line”, “circle”, “center”, or “polygon” keyword, 
    there MUST be a corresponding “loc” keyword to provide coordinates for 
    that point.
14. It is RECOMMENDED that text be marked up and is RECOMMENDED that the 
    object not be added to the text. For example, if the text was “Let line 
    AB a given finite straight line”, the markup should be “Let [line AB] be a 
    given finite straight line” and not “Let line [line AB] be a give finite 
    straight line”, as the latter will result in the word “line” being 
    displayed twice.
15. The user MAY specify steps in the markup which will represent groups of 
    elements to be displayed together in the frontend. This allows the user 
    to create animated steps in the frontend construction. All elements 
    created between two [step] commands will be displayed together, and in 
    every subsequent [step] command.
16. The user MAY use the “clear” keyword as a way to remove all visualization 
    from the screen.
```
