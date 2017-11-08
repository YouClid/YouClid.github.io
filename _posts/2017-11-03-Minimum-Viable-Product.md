---
layout: post
title:  "Minimum Viable Product"
date:   2017-11-03 00:10:00-0400
categories: jekyll update
---
#### Soumya Kundu, Drew Monroe, Sailesh Simhadri

### Updates
The goal for the end of the week was to accomplish the tasks we defined for a minimum viable product. These tasks were

1. Use brackets
2. Allow for object creation
3. Parse down up
4. Update animation structure
5. Syntax highlighting

We have completed all of these tasks which will be detailed below.

### A New Syntax
Our syntax has again changed. We now define our keywords between brackets, `[` and `]`. We decided that our initial use of backticks would lead to problems. Specifically, having unique delimeters for open and close will mitigate the impact of ill formed files by the user. For example, if a user forgets to add a backtick to close a keyword, the parser will still attempt to parse the text without notifying the user of an error. Therefore, we have decided that it is important to have specific open and close delimeters.

We initially considered a wide range of delimeters. Our considerations included `<` and `>`, `{` and `}`, and even `,` and `.` to name a few. However, we still wanted the text to be easily readable and markable. Therefore, one of the biggest drawbacks for many of our choices was the need to use a shift key. Keywords are something that will be used very frequently and having to press the shift key frequently would be very cumbersome and annoying to use. However, we still wanted the text to be readable, so using random delimeters would also be a bad choice. As a result, we came to the final decision of using brackets.

### Object Creation
Initially, we intended the user to mark up as little text as possible and have our product work. We initially intended our product to be used to markup Euclid's Elements with as little changes as possible.  However, we ultimately decided that this would lead to limitations, and possibly issues, as we expand our product. Even though our product could be used to markup the text, it should not be limited to that. We need a method to clearly define an object as well as our shorthand syntax. Therefore, we decided that it would be best allow for explicit object creation instead of just limiting to our short hand syntax. However, we still want to maintain our goal of the markup being human readable. Therefore, we deemed it good practice, but not an actual requirement, to have all object creations in the bottom of the text. Then, within the text, the user has to just reference the object. For example, if the user wants to create a circle named `circle A` with a radius of `6` and a center of `point A`, the user would first put `[Circle cirlceA radius=6 center="point A"]` at the bottom of the file. Then, if the user needs to reference the cirlce in the text, the user would use `[Circle circleA]`.

### Parse Down Up
With the allowance of creating explicit objects at the bottom of the file, we have restructured the parser to parse bottom up. As a result, we have defined a section called `[definitions]` at the bottom of the file where all object creation code should, and is highly recommended to, go. Although this is just a recommendation, we deem it highly important to follow this suggestion to maintain our initial goals when defining our product. If the definitions do not go here, the objects must be explicitly created before being referenced in the text.

### Update Animation Structure
Initially, we defined animations as incremental steps where the current step builds off the previous step. We thought that this goes in parallel with the incremental building of proofs in Euclid's Elements. However, this too would lead to limitations. For example, in the first proposition, Euclid incrementally builds a equilateral triangle using circles and lines. By only allowing incremental steps, we don't allow a viewer to see the end result itself, the equilateral triangle without the circles and lines used for the construction. Therefore, we have decided to move away from this incremental approach. Instead, we structured the parser to make each step independent of any other step. Therefore, if the user wanted to, a completely different picture can be displayed in the next step. To allow for this, we have added a new keyword `[clear]` that clears the screen at the current step. Therefore, the user can add elements to the current step without worrying about left over elements in the previous step. However, with this came the need for hidden keywords. The user should be allowed to add elements to the animation without having it show up in the text. Therefore, we decided that we needed to allow for hidden keywords. As an initial decision, we will use the `*` symbol to define hidden keywords. For example, if a circle called `ABC` needs to be added in the current animation step without being added to the text itself, then the user needs to add `[*circle ABC]`.

### Syntax Highlighting
We have also created syntax highlighting files for vim and atom. Emacs is in the pipeline.

### Next Steps
For next week, when we will release Demo 0.2, we will be working on allowing for case insensitivity in addition to cleaning up a large part of the parser code.


