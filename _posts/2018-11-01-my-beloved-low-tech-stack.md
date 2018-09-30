---
layout: post
author: David Boureau
minread: 11
title: "My beloved, low-tech stack"
date: 2018-11-01
categories: work
permalink: /blog/:title/
description: "My beloved, low-tech stack"
---


Writing a web-application (clara) for the French unemployed people, I have longly considered each options that would achieve :
 - the highest possible quality
 - at the lowest possible price
 - with a maximized speed of delivery
 

## Plain old vanillaJS (JavaScript, but ES5)

Not using ES6 nowadays is probably not something you're allowed to claim publicly. 

Sorry then. I appreciate to work with ES6 when I have to, but I more happy when working with ES5.

ES6 is fine. You have a trap-free, shorter syntax, and modules, and probably other good things.

The most obvious drawback of ES6 is instrumentation. You need a transpiler that integrates properly with your build tool. Once it's start to be buggy, you spent time on a technical stuff, instead of the business stuff you are paid for.

The other bad part is langage itself. You have many ways to declare functions, sometimes the "return" keyword is allowed to be implicit. That makes debugging and reading code pretty hard. 

ES6 went after ES5, so even an ES6 coder have to know ES5.

ES6 went after ES5, so ES5 is much more universally known than ES6.

"The bad parts" of plain old JavaScript are extremely easy to prevent with a good linter.

The use of separate modules with ES6 is really nice, but I didn't feel the need for it at any point of the project. Polluting the global scope will actually only pollute *one* tab of *one* browser of *one* client, so I can only laugh about that weakpoint, in comparison of time NOT spent over-instrumenting my project.

Now the important point is : **there is nothing you can do with ES6 that you can't with ES5.** (Please, see next paragraph if you wanted to tell me "but the API is much more important!")

Even babel-compatible, oriented-object programming can be nicely achieved with ES5. https://github.com/WebReflection/classtrophobic-es5

ES6 is nice, but I loose stability of the build and universality by using it, without any significant gain anywhere.

So I'm back to a low-tech JavaScript technology.


## Lodash

Please stop to say Lodash is no more needed because of future version of JavaScript. The high number of primitives available will never be reached in the core language, so instead of loosing time reinventing the wheel, I reuse work of others.

I know Lodash "as-is" doesn't mean "pure" functional programming, but I really don't care. I never had an algorithm that required such a level of so-called "purity". Properly chaining primitives are often more than enough to get things done. Here is one of the most complicated function I've ever written : https://github.com/1024pix/pix/blob/v2.2.0/mon-pix/app/utils/value-as-array-of-boolean.js. Nothing fancy, isn't it ?


LoDash can be extended, so most of the time, even if the core team decided not to include a feature, someone else wrote an extension that is publicly available on GitHub. The "count" function for example is missing but easy to retrieve and extend : https://github.com/lodash/lodash/issues/702

Is LoDash a technology of the past ? I don't know, and I don't really care, because I can achieve much more with it that I would without.




## jQuery

j-j-jQuery ? Aren't you kidding ? I think I just lost 91.2 % of my readers here:)

jQuery is the most popular JavaScript library, 5 years ago, when I learnt JavaScript seriously, jQuery was more known by students than JavaScript itself ! 

A good explanation could be the ease of use of the library. 

Today, it is still a lot more used (at least 10 times) than React, who leads the trend of popularity of JS Frameworks.

Which means, when you need a special plugin, there a great chances it already exists in jQuery. 

For my current project I needed an accessible (a11y) address picker.

Well, great news, I didn't had to code it, someone made it already... in jQuery.

At that time it didn't exists (yet) in Angular or React. 

Worse, if a nice Angular component, you can't use it in React. Each has its own lifecycle that completly differs from the one of the browser, and of course also differs from others. This is insane.

Which means for my a11y-datepicker, if I had an Angular project, and I nice component existed in React, I couldn't use it for my projet. Duh ??

Every new fancy JavaScript framework launched since BackBone in 2011 failed to become "the new web component standard library". Even the official, w3c based, web component is not much used.

jQuery, despite never explicitly being fancy, has always been the de-facto web component library.

Moreover, jQuery do not try to have a lifecycle on top of the lifecycle of the browser.

With jQuery you have gigatons of free, customizable, reusable web components.

The only case where jQuery can turn into bloated, paghetti code, is when you try to have a lot of custom interactivity on one web page.

In this case, see paragraph below :)


## Redux

This is the only exception of this list. Redux is a quite recent technology, mostly used in combination with React. This is a mistake.  Use it in conjunction with jQuery, and you'll save quite a few weeks per month.

On the most interactive page of my current project, I gave a decent try to jQuery (alone), VueJS, KnockoutJS, and gave StimulusJS a chance.

On previous project, I have worked with React, Ember, Angular, Backbone.

I ended up with Redux + jQuery. Why ?

Speed and stability.

For SEO and performance purposes, I needed the HTML to be rendered by the server. This eliminates the nice **EmberJS**.

**StimulusJS** was too new to try, moreover, it forces you to use ES6 where I don't want to.

**KnockoutJS**, when used in conjunction with Knockout-pre-rendered, has the same philosophy as StimulusJS : a JavaScript for the HTML you already have.  Knockout was really nice and quick to write, but really harder to read and debug. Moreover, there is no centralization of the state, which makes really hard to reason about state and transition, and state restoration was really painful. I dropped Knockout from the project.

**VueJS** has an awesome ubiquitous property. However SSR is still immature. And it doesn't work well with pre-rendered HTML.

Moreover, if you have read paragraph above about jQuery, you know I don't want anything that build components with it's own lifecycle. 

This eliminates VuesJS and ReactJS. 

However, I had the option of giving **ReactJS** (with SSR) a chance, but at that point, I encountered my last obstacle : Too much quality. Too much details. Too much files.

Let's say your wardrobe is an ugly, complete mess. You want to store each item properly. You start to add shelfs and drawers. Now it is good-looking. You continue to add shelfs and drawers, until there is one drawer for each sock, one drawer for each shirt, etc. Now the situation is almost as ugly as it was : a complete mess.

This what I wanted to pointed out. Too much decomposition of components like React/Vue does leads into a tons of independant HTML/CSS/JS widgets, that are hard to navigate between when coding, and maintain altogether.

I guess there are situation where one drawer per item is required (or React wouldn't reach that level of success), but for the everyday businness : use Redux.

With Redux :

 - Even if the server renders a ton of HTML, you can move only the parts that requires to move, instead of divising each HTML part into a component (React, or Vue component, or whatever).
 - The state is completly centralized into a single, plain JSON object.
 - The flow is **completly intuitive, easy to follow, easy to debug, easy to test.**
 - This is incredibly easy to write. The API is as simple as A-B-C. You can be a Redux expert within a day. Really. Who can pretend to be a Backbone or React expert in a few hours?
 - (Correlated) It's so easy that even the intern with little Knowledge of ES5 can help you to build the front-end part.
 - You can still use your favorite backend technology, no need to separate frontend and backend into 2 separate teams.
 - You can tackle **any** complexity on the front-end. It was still possible, but really harder with older tools like BackboneJS or KnockoutJS.

 I can see no real drawback.

 Maybe you end up with a JavaScript file (per page/url) that is maybe not as elegant as the one you can find in a React component, but you spare so much time and energy without sacrifing speed, stability. Top of the pop, **you don't use anything that breaks the brower's flow.** 


## Keyboard-based IDE

I won't name the IDE I'm using, because it's not the point.

I use an IDE that allow me to do **everything with the keyboard**. It's a huge relief for the mind when you don't have to point something with the mouse's cursor.

Apart from syntaxic coloration and linting, I avoid to give the IDE too much reponsibility. The more you "integrate" things inside the IDE ("I" is for "integrated"), the more unstable tool you have. Then you spend time on your problems, instead of helping your customers to solve their problems.

## Ruby

I code the backend with Ruby.

It's **not** a fantastic langage, but it's oriented-object enough, and functional oriented enough, to get things done quickly.

The bad parts are "functions not used as first-class citizens". Which means I have to create lambda, block and proc if I want to go for a walk with my tiny function. Ahem. Not good.

The syntax is easy... once you spent some weeks with it. I would have prefered a C-based syntax which is more world-wide known.

Fortunately, the API is wide, consistent, and developer-friendly -  which is, this time, a good point.

Lastly, Ruby is virtually unused outside the Ruby-on-Rails space. Which is a bad thing. I would have prefered a Python or PHP or Java "on Rails", which would have beed better in a Human Resource point of view.

## Ruby-on-Rails

A slow and old framework. Not kidding here, this is actually what I'm thinking about it.

But still unbeaten when it's time to get things done.

I'm still astonished to see every new framework (backend or frontend) delivered **without** console, pre-defined environment, migration, efficient default build and testing tool, efficient admin plugins, and, very importantly, an opinionated directory structure.

**If only one of these feature is missing, you add tons of pressure and unstability on the technical team**, who is then unable to focus on the quickly enough business part - or not at a reasonnable price.

It's probably a question for quora or meta-stackoverflow.

I'm not completly sure why "new" didn't mean "get things done more quickly than the stuff that was here before".

NodeJs brought use more universality by bringing JS to the backend, but failed to deliver a (sufficiently and widely backed by community) framework to get things done quickly.

Phoenix/Elixir brought us more rendering speed and functional programming, without being mature enough on the "get things done" part.

ReactJS focused on the "front-end" part, MeteorJS focused on the "real time" part, etc.

No one now focuses on "get thing done quickly" part, and I have no clear answer why history didn't go into this direction.


## Stackoverflow, and Slack-overflow

Stackoverflow has 10 years this month, and it didn't lost it's hype actually. Then, it's a bit weird to see him in this list, but it's an important part of my everyday stack. Sometimes I use a slack channel, but just learn to isolate a problem and ask clearly, unambiguously on Stackoverflow, and you'll be fine for a while :)

## Test last

Again, this is not something you are allowed to claim publicly.

I love to test something *after* the feature is released. The lacking test often ends up in the technical debt, which is paid off as soon as possible. **The business teams is educated and know about the tech debt.**

Thus, I'm ensured to test with the minimum possible effort.

I'm not saying I'm never testing anything. I have currently between 700 and 800 automated tests, frontend and backend alltogether. My code-to-test ratio is 1:2.1, which is https://stackoverflow.com/a/1205695/2595513 a good average. More importantly, I'm confident enough about the application.

I hugely rely on unit testing on the critical parts of the system, making them sometimes redundant if necessary.

Some non-critical part are left with an integration test that perfectly does the job.

Some parts are left to a manual testing, because automating it would cost too much. For example, the result of the "print this page" button is virtually untestable.

I use TDD sometimes, when  the *how* (the system under test) is known before to code it.

But, more often, I test the thing **after** I code the thing. I code the smallest possible stuff, I do the ugly manual check in the browser, then I commit/push it, until I release a **draft** version that I can widely discuss with my Product Owner (abbreviated PO). Once the discussion is over, I trash some part of the code, I keep some other parts of the code. I submit it again to the PO. Once he/she's satisfied with it, I have to consider if unit, or integration, or manual testing is the more appropriate thing **for the release that has been proven to be fine** to the PO's eyes.


## Unknown build tool

Do you know webpack ? It's probably a bad tool because the name "webpack" is known. Which means you probably spent time to tweak it.

I rely on the build tools of my framework, whose job is to compile assets properly, and build backend dependencies properly.

I copy/paste my frontend 3rd-party dependencies into my project, then I commit and push them into the project's GitHub repository.

Very Ugly™ right ?

No CDN. No bower, gulp, webpack, and so on. I removed a lot of complexity in the project by letting the framework do what it is already supposed to do.

## Conclusion

Doing things "the old way" often mean stability and productivity. Of course criticism should not be abandoned, and sometimes a new tool could mean something great for your project. But be aware that this is the exception, not the rule.