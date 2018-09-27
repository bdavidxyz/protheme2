---
layout: post
author: David Boureau
minread: 11
title: "My beloved, low-tech stack"
date: 2018-10-01
categories: work
permalink: /blog/:title/
description: "My beloved, low-tech stack"
---


Writing a web-application (clara) for the French unemployed people, I have longly considered each options that would achieve :
 - the highest possible quality
 - at the lowest possible price
 - with a maximized speed of delivery

Most of the time, 

## Plain old vanillaJS (JavaScript, but ES5)

Not using ES6 nowadays is probably not something you're allowed to claim publicly. 

Sorry then. I appreciate to work with ES6 when I have to, but I more happy when working with ES5.

ES6 is fine. You have a trap-free, shorter syntax, and modules, and probably other good things.

The most obvious drawback of ES6 is instrumentation. You need a transpiler that integrates properly with your build tool. Once it's start to be buggy, you spent time on a technical stuff, instead of the business stuff you are paid for.

The other bad part is langage itself. You have many ways to declare functions, sometimes the "return" keyword is allowed to be implicit. That makes debugging and reading code pretty hard. 

ES6 went after ES5, so even an ES6 coder have to know ES5.

ES6 went after ES5, so ES5 is much more universal than ES6.

"The bad parts" of plain old JavaScript are extremely easy to prevent with a good linter.

The use of separate modules with ES6 is really nice, but I didn't feel the need for it at any point of the project. Polluting the global scope will actually only pollute *one* tab of *one* browser of *one* client, so I can only laugh about that weakpoint, given the time I win by NOT over-instrumenting my project.

Now the worst part : there is nothing you can do with ES6 that you can't with ES5. (Please, see next paragraph if you wanted to tell me "but the API is much more important!")

ES6 is nice, but I loose robustness and universality by using it, without any gain anywhere. 

So I'm back to a low-tech.

## Lodash

Please stop to say LoDash is no more needed because of future version of JavaScript. The high number of primitives available will never be reached in the core language, so instead of loosing time reinventing the wheel, I reuse 

LoDash can be extended, so most of the time, even if the core team decided not to include a feature, someone else wrote an extension that is publicly available on GitHub.

Is LoDash a technology of the past ? I don't know, and I don't really care, because I can achieve much more with it that I would without.

## jQuery

jQuery ? Aren't you kidding ? I think I just lost 91.2 % of my readers here:)

jQuery is the most popular JavaScript library, 5 years ago, when I learnt JavaScript seriously, jQuery was more known by students than JavaScript itself ! 

A good explanation could be the ease of use of the library. 

Today, it is still a lot more used (at least 10 times) than React, who leads the trend of popularity of JS Frameworks.

Which means, when you need a special plugin, there a great chances it already exists in jQuery. 

For my current project I needed an accessible address picker.

Well, great news, I didn't had to code it, someone made it already... in jQuery.

Maybe it doesn't exists (yet) in Angular or React, and worse, if a nice Angular component, you can't use it in React. Each has its own lifecycle that completly differs from the one of the browser.

Every new fancy JavaScript framework launched since BackBone in 2011 failed to become "the new web component library".

jQuery, despite never explicitly being fancy, has always been the de-facto web component library. 

Moreover, jQuery do not try to have a lifecycle on top of the lifecycle of the browser.

You have tons reusable webcomponents, unbugued.

The only case where jQuery can turn into spaghetti code, is when you try to have a lot of custom interactivity on one web page. In this scenario

## Redux

This is the only exception of this list. Redux is a quite recent technology, mostly used in combination with React. This is a mistake. Use it in conjunction with jQuery, and you'll save quite a few days per month.

I have worked with React, Ember, Angular, Backbone, Vue. VueJS is probably the most awesome of them, but after a decent try, I dropped it from the main part of the project. Why would I ? 

