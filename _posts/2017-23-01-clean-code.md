---
layout: post
author: David Boureau
minread: 12
title:  "An exceedingly clean code"
date:   2017-01-23
categories: work
permalink: /blog/:title/
description: "How to write a readable code"
---

<p>&nbsp;</p>
**Update 9 Deb 2017** : _Today, it is by far my most read article, and also the most hated. I didn’t intend to publish the holy grails of clean code, there is already a whole book for it. As the title implies, the quality is pushed a little too far, and achieve it on every function is probably not so realistic. I tried to explore new ways to document code and augment robustness, you don’t have to agree with / like it, just do whatever you want to increase both quality and speed of delivery._
<p>&nbsp;</p>
The article is written with ES6 for examples, but the article could be applied to other programming languages.
<p>&nbsp;</p>


<style type="text/css">div.gist-meta{display: none;} div.gist .gist-file{border: none;} div.gist .gist-data{border: none;}</style>

<script src="https://gist.github.com/bdavidxyz/74bb653ee49fa849edc8e4037f1b8654.js"></script>


- F*** what does this function try to...
- stop, the dev who made it left last week
- well, since _.zip is used, proposals and checkboxes are probably arrays.
- good ... arrays of what? Didn’t know _.zip, I discovered lodash with this project.
- and what’s the point of line 4 condition ?
- I dunno.
- ...

A small, very small JS function of 11 lines turns into a maintenance nightmare. The slightest bug, the slightest recovery, the slightest refactoring costs a lot of time and energy.

Knowing that any software is counted easily in thousands of lines of code ...

## Version 0 : do not change anything

And write automated tests. No need to be unit tests written the TDD way. Integration tests written afterwards are just as good enough to begin with. Or acceptance tests. 

Without any test, it’s impossible to improve anything.

Voluntarily I do not show the unit tests of this function, the purpose of the article is to give an example of documentation by the code.

## Version 1 : Check preconditions

In order to help the reader, while improving the robustness of the code, and to avoid the edge effects, let’s be sure of the input parameters before going further.

<script src="https://gist.github.com/bdavidxyz/59289f3cd5c817b03e8c31f1c8eb265a.js"></script>

We understand what the input parameters are, but that's hard. Have you noticed the "!" Exclamation mark ?? No ? So why not write some utility functions that makes it great:

<script src="https://gist.github.com/bdavidxyz/fcf0c85fcf3df127a0eefd4f8b60c757.js"></script>

And even better, we use an IDE plugin to get a nice alignment

<script src="https://gist.github.com/bdavidxyz/0e4a37b6d0164f40221febba014d6c2f.js"></script>



There you go ! No need to comment at this stage, it's clear as water.

We use Ruby-like code, where each word is placed in the right order to be sure we will able to read the code as in natural language. For example, here one can read in the 2nd line, excluding everything that is not strictly textual:

> if proposals is not array of string return []

There you go ! Again, no need to comment until then.

**Note 1** : An effective way of fighting the anxiety of "but-what-if-this-happens" (and against the debugging hours!) is to guard against any unexpected parameters by returning an empty value corresponding to expected type. This is the behavior chosen in a majority of cases for lodash / underscore. (For example, returning an empty string if the function returns a String, an empty array if the array must return an Array, etc.).

**Note 2** : Even a strongly-typed language wouldn't have solved all problems. The checks on the difference of the array sizes / on the non-empty array would still have taken place.




## Version 2 : Comment by example 

Comment the signature of the function. But-that-serves-nothing-if-the-function-is-well-named.

Not exactly.


<script src="https://gist.github.com/bdavidxyz/b7488c92e7275216b5bfcef426820158.js"></script>



- The general idea is: document by example. 
  - These parameters are relocated in the overall context of the project (for example, it is understood that proposals are proposals or questions posed to the user)   
  - By the way the type of parameters of the function are now evident.
- Any odd / counterintuitive thing can be reported here. With the help of the word WARNING or XXX in the comments. It's a bit like Github: do not be afraid to abuse it. There will ALWAYS be issues, always odd thinks in your code, even if you do not like it.






## Version 3 : Verticalize your code

This [StackOverflow answer](http://stackoverflow.com/a/37770048/2595513) is a good example of verticalization.

In our case, the use of [applicative programming](http://bekk.github.io/functional-js/workshop/02-1-applicative) make  code greater.

Even on a very small function, think about what happens when the flow of instruction looks like this
<div style="text-align: center;">
<svg width="260px" height="285px" viewBox="0 0 260 285" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><rect id="path-1" x="0" y="0" width="80" height="60"></rect><mask id="mask-2" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="80" height="60" fill="white"><use xlink:href="#path-1"></use></mask><rect id="path-3" x="0" y="0" width="80" height="60"></rect><mask id="mask-4" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="80" height="60" fill="white"><use xlink:href="#path-3"></use></mask><rect id="path-5" x="0" y="0" width="80" height="60"></rect><mask id="mask-6" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="80" height="60" fill="white"><use xlink:href="#path-5"></use></mask><rect id="path-7" x="6" y="6" width="26" height="26"></rect><mask id="mask-8" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="26" height="26" fill="white"><use xlink:href="#path-7"></use></mask><rect id="path-9" x="6" y="6" width="26" height="26"></rect><mask id="mask-10" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="26" height="26" fill="white"><use xlink:href="#path-9"></use></mask></defs><g id="A-visual-vocabulary--" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd"><g id="Artboard" transform="translate(-141.000000, -23.000000)"><g id="Making-choices" transform="translate(141.000000, 23.000000)"><g id="decision-point"><g id="basic/page-text" transform="translate(100.000000, 0.000000)"><use id="page" stroke="#7F8C8D" mask="url(#mask-2)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" xlink:href="#path-1"></use><text id="login" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="14.3476562" y="32.9296875">do this</tspan></text></g><g id="basic/page-text" transform="translate(20.000000, 150.000000)"><use id="page" stroke="#7F8C8D" mask="url(#mask-4)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" xlink:href="#path-3"></use><text id="login" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="13.6767578" y="32.9296875">do that</tspan></text></g><g id="basic/page-text-2" transform="translate(180.000000, 150.000000)"><use id="page" stroke="#7F8C8D" mask="url(#mask-6)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" xlink:href="#path-5"></use><text id="product" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="11.5" y="28">launch this</tspan></text></g><g id="arrow/connection" transform="translate(129.000000, 172.500000) rotate(-270.000000) translate(-129.000000, -172.500000) translate(16.500000, 77.500000)" fill="#7F8C8D"><path d="M84.3252772,4.74242424 C83.859262,5.91273569 82.8636364,7.28787879 82.8636364,7.28787879 L90.5,3.89393939 L82.8636364,0.5 C82.8636364,0.5 83.9708907,1.92335529 84.3965901,3.04545455 L64.5,3.04545455 L64.5,4.74242424 L84.3252772,4.74242424 Z M84.5,4.21126578 C84.5387505,4.05322147 84.5606061,3.9051318 84.5606061,3.77213542 C84.5606061,3.64835443 84.5387505,3.51052598 84.5,3.36343266 L84.5,4.21126578 Z" id="Triangle-1"></path><path d="M169.325277,4.74242424 C168.859262,5.91273569 167.863636,7.28787879 167.863636,7.28787879 L175.5,3.89393939 L167.863636,0.5 C167.863636,0.5 168.970891,1.92335529 169.39659,3.04545455 L149.5,3.04545455 L149.5,4.74242424 L169.325277,4.74242424 Z M169.5,4.21126578 C169.538751,4.05322147 169.560606,3.9051318 169.560606,3.77213542 C169.560606,3.64835443 169.538751,3.51052598 169.5,3.36343266 L169.5,4.21126578 Z" id="Triangle-1" transform="translate(162.500000, 3.893939) scale(-1, 1) translate(-162.500000, -3.893939) "></path><path d="M84.3252772,164.742424 C83.859262,165.912736 82.8636364,167.287879 82.8636364,167.287879 L90.5,163.893939 L82.8636364,160.5 C82.8636364,160.5 83.9708907,161.923355 84.3965901,163.045455 L64.5,163.045455 L64.5,164.742424 L84.3252772,164.742424 Z M84.5,164.211266 C84.5387505,164.053221 84.5606061,163.905132 84.5606061,163.772135 C84.5606061,163.648354 84.5387505,163.510526 84.5,163.363433 L84.5,164.211266 Z" id="Triangle-1"></path><path d="M228.325277,177.742424 C227.859262,178.912736 226.863636,180.287879 226.863636,180.287879 L234.5,176.893939 L226.863636,173.5 C226.863636,173.5 227.970891,174.923355 228.39659,176.045455 L208.5,176.045455 L208.5,177.742424 L228.325277,177.742424 Z M228.5,177.211266 C228.538751,177.053221 228.560606,176.905132 228.560606,176.772135 C228.560606,176.648354 228.538751,176.510526 228.5,176.363433 L228.5,177.211266 Z" id="Triangle-1" transform="translate(221.500000, 176.893939) rotate(90.000000) translate(-221.500000, -176.893939) "></path><rect id="Triangle-1" x="0" y="83" width="66" height="2"></rect><rect id="Triangle-1" x="156" y="163" width="66" height="2"></rect><rect id="Triangle-1" transform="translate(65.500000, 83.993827) rotate(-270.000000) translate(-65.500000, -83.993827) " x="-15" y="83" width="161" height="1.98765432"></rect><rect id="Triangle-1" transform="translate(221.500000, 83.993827) rotate(-270.000000) translate(-221.500000, -83.993827) " x="141" y="83" width="161" height="1.98765432"></rect></g><g id="action/decision" transform="translate(121.000000, 74.000000)"><text id="decision-point" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="43" y="24">decision point</tspan></text><use id="Rectangle-121" stroke="#7F8C8D" mask="url(#mask-8)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" transform="translate(19.000000, 19.000000) rotate(-315.000000) translate(-19.000000, -19.000000) " xlink:href="#path-7"></use></g><g id="Line-+-Triangle-1" transform="translate(0.000000, 26.000000)"><path d="M1,153.519608 L1,4.22899284 M1,154.013072 L19,154.013072" id="Line" stroke="#7F8C8D" stroke-width="2" stroke-linecap="square"></path><path d="M1,254.519608 L1,105.228993 M1,255.013072 L19,255.013072" id="Line" stroke="#7F8C8D" stroke-width="2" stroke-linecap="square"></path><path d="M93.7226482,5 C93.1734159,6.37929564 92,8 92,8 L98.75,5 L100,5 L100,4.44444444 L101,4 L100,3.55555556 L100,3 L98.75,3 L92,0 C92,0 93.3049783,1.67752588 93.8066955,3 L2,3 L2,5 L93.7226482,5 Z" id="Triangle-1" fill="#7F8C8D"></path><path d="M151.722648,256 C151.173416,257.379296 150,259 150,259 L156.75,256 L158,256 L158,255.444444 L159,255 L158,254.555556 L158,254 L156.75,254 L150,251 C150,251 151.304978,252.677526 151.806695,254 L60,254 L60,256 L151.722648,256 Z" id="Triangle-1" fill="#7F8C8D"></path></g></g></g><g id="connection/completion/arrow--mini" transform="translate(201.000000, 245.000000) rotate(-270.000000) translate(-201.000000, -245.000000) translate(188.000000, 241.000000)" fill="#7F8C8D"><path d="M18.7226482,5 C18.1734159,6.37929564 17,8 17,8 L26,4 L17,0 C17,0 18.3049783,1.67752588 18.8066955,3 L0,3 L0,5 L18.7226482,5 Z" id="Triangle-1"></path></g><path d="M180.5,304 L148,304" id="Line" stroke="#979797" stroke-width="2" stroke-linecap="square"></path><g id="action/decision" transform="translate(182.000000, 254.000000)"><text id="decision-point" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="43" y="24">decision point</tspan></text><use id="Rectangle-121" stroke="#7F8C8D" mask="url(#mask-10)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" transform="translate(19.000000, 19.000000) rotate(-315.000000) translate(-19.000000, -19.000000) " xlink:href="#path-9"></use></g><path d="M361,256.5 L361,304.5" id="Line" stroke="#979797" stroke-width="2" stroke-linecap="square"></path></g></g></svg>
</div>

<p> </p>
**This is particularly painful, isn’t it?**
 
<p> </p>


On the other hand, a vertical instruction flow make things much simpler.


<div style="text-align: center;">
<svg width="80px" height="232px" viewBox="0 0 80 232" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><polygon id="path-1" points="-5.68434189e-14 50.2998047 -5.68434189e-14 10.3369141 10.3095703 0 70 0 80 9.86816406 80 50.3212891 69.6318359 60 9.42285156 60"></polygon><mask id="mask-2" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="80" height="60" fill="white"><use xlink:href="#path-1"></use></mask><rect id="path-3" x="0" y="0" width="80" height="60"></rect><mask id="mask-4" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="80" height="60" fill="white"><use xlink:href="#path-3"></use></mask><rect id="path-5" x="0" y="0" width="80" height="60"></rect><mask id="mask-6" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="80" height="60" fill="white"><use xlink:href="#path-5"></use></mask></defs><g id="A-visual-vocabulary--" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd"><g id="Artboard" transform="translate(-620.000000, -26.000000)"><g id="useful-label" transform="translate(620.000000, 26.000000)"><g id="basic/reference" transform="translate(0.000000, 86.000000)"><use id="page" stroke="#7F8C8D" mask="url(#mask-2)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" xlink:href="#path-1"></use><text id="foo" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="23.5" y="35">do foo</tspan></text></g><g id="basic/page-text"><use id="page" stroke="#7F8C8D" mask="url(#mask-4)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" xlink:href="#path-3"></use><text id="login" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="20.0136719" y="32.9296875">do A</tspan></text></g><g id="connection/completion/arrow--mini" transform="translate(40.000000, 73.000000) rotate(-270.000000) translate(-40.000000, -73.000000) translate(27.000000, 69.000000)" fill="#7F8C8D"><path d="M18.7226482,5 C18.1734159,6.37929564 17,8 17,8 L26,4 L17,0 C17,0 18.3049783,1.67752588 18.8066955,3 L0,3 L0,5 L18.7226482,5 Z" id="Triangle-1"></path></g><g id="connection/completion/arrow--mini" transform="translate(40.000000, 159.000000) rotate(-270.000000) translate(-40.000000, -159.000000) translate(27.000000, 155.000000)" fill="#7F8C8D"><path d="M18.7226482,5 C18.1734159,6.37929564 17,8 17,8 L26,4 L17,0 C17,0 18.3049783,1.67752588 18.8066955,3 L0,3 L0,5 L18.7226482,5 Z" id="Triangle-1"></path></g><g id="basic/page-text" transform="translate(0.000000, 172.000000)"><use id="page" stroke="#7F8C8D" mask="url(#mask-6)" stroke-width="4" fill="#FFFFFF" fill-rule="evenodd" xlink:href="#path-5"></use><text id="login" font-family="ArialMT, Arial" font-size="12" font-weight="normal" line-spacing="13" fill="#7F8C8D"><tspan x="19.6826172" y="32.9296875">do B</tspan></text></g></g></g></g></svg>
</div>

<p> </p>

Applied to our example, we replace

<script src="https://gist.github.com/bdavidxyz/e32af14aa7bc58e522dc10652df291dd.js"></script>

By this:

<script src="https://gist.github.com/bdavidxyz/c4e64d7ab5e4bd1c48a9472d7afdad3c.js"></script>

We take a breathe! No decision tree, no “unambiguous” variable (item), functions that make a unitary job ...

We comments again by example, line by line:

<script src="https://gist.github.com/bdavidxyz/529d960b711ccd8d059fc61abe9294fc.js"></script>

## Final Code

<script src="https://gist.github.com/bdavidxyz/ef29f2e44eafb0da0d304823cc3805e5.js"></script>


## Small synthesis



- The code must be covered by automated testing. It does not matter whether they are unitary, of integration, of acceptance. The absence of a safety net prevents the code from being improved.

- The input parameters must be checked. Although this point is particularly subject to debate in the case of a dynamic language, it will help you to debug your code faster, and also increasing the readability of the code.

- The functions must be as small as possible, with a maximum explicit naming.

- A readable code is not necessarily the shortest.

- Avoid any for loop, application programming simplifies reading.

- any (relevant!) comment is good, but the best remains the explanation of the nominal case.

- [Aligning characters](https://packagecontrol.io/packages/Alignment) helps to make the code readable.

- Any oddity, counter-intuitive or that makes you think for more than 2 seconds must be written in black and white using a statement previously made by the team members (XXX most often).

- To avoid overloading the article, naming variables has not been mentioned, whereas it is probably [the hardest thing](https://martinfowler.com/bliki/TwoHardThings.html) in computing. You've been warned :)

- It's never really over :
  - [a recent article](https://medium.com/making-internets/why-using-chain-is-a-mistake-9bc1f80d51ba#.5qwj6cycm) suggests not to use _.chain 
  - we should at least put a warning if an input parameter is not valid in our example.

