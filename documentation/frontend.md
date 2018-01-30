---
title: Frontend Architecture
permalink: /docs/frontend
layout: docs
categories: documentation
---

For our first frontend, we have decided to use HTML and `three.js`.
The `three.js` library has abstractions to make displaying of geometric objects easier.
This will also make it easier to transition away from `three.js` and use pure WebGL instead.
Using WebGL instead of `three.js` will mean that our frontened will not have any outside dependencies.
This will make it easier to have others use our code, and we hope that it will help give our codebase longer longevity
The choice of HTML means that it is easy for the end user to view the output that we create, all they have to do is open a web browser!
It also means that we do not have to deal with running and administering a server since the content is all displayed locally.
