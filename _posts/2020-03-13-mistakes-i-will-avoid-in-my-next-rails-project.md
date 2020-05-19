---
layout: post
author: David Boureau
minread: 11
title: "Mistakes I will avoid in my next Ruby-on-Rails project"
date: 2020-05-19
categories: work
permalink: /blog/:title/
description: "Mistakes I will avoid in my next Ruby-on-Rails project"
---

My current, beloved, monolithic Rails app is 3 years old now. 

What if I had to start a new project today ?

This is the classic situation where you could wonder : "Which stack I should use in 2020 ?"

After years of trying various tech stacks, I finally found the best way to produce high added value within a short amount of time, without depreciation and without compromising quality over the long term : Ruby-on-Rails.

So the next famous stack to use in 2020 after the Ruby-on-Rails hype is "Ruby-on-Rails, done right".

Of course these are thoughts base on my own experience, they are very subjective and very possibly criticized.

Here are mistakes I will avoid in my next Ruby-on-Rails project :


## 1. Not using "end-to-end testing" as a priority

The testing part is an endless debate, even with myself.

There are weeks where I'm completly sure about "unit test first".

Then a week where I'm sure about "unit test last".

Then some more weeks with "Uh no, end-to-end first".

Now I think all are importants, but end-to-end testing is more important than other kind of tests.

It requires less mental effort to setup context and write test.

You can write a lot LESS test, with a very good businness coverage, and decent technical coverage.

Finally, it documents how and why the application works, far better than any other test.

Of course I have also some decent unit coverage, but for my next project, I will not start without a Cypress suite correctly setted up, both locally and in CI.


## 2. Not using Cypress

Cypress is a *de-facto* tool for end-to-end testing. I tried Capybara, but it works well mostly for server-rendered-only pages. 

If there is any Javascript, the problems start to grow.

Compared to Selenium, Cypress doesn't care about the underlying stack, have faster commands, less random errors, easier selectors, easier IDE.

Cypress rocks.


## 2. Not using ES6

In my last article, I was writing how easier it was to work with ES5, but now I must acknowledge that ES6 is the new standard, and it's not going to go away anytime.


## 3. Sprockets

I will keep Sprockets, but I won't use it for my custom code. Why ? Locally, Webpack(er) does already everything what Sprockets is supposed to do.

But must-go external gems may not use it (administrate for example).


## 4. Not using turbolinks

I disabled turbolinks on my current project because of the "too many headaches" problem, but now that I have seen the huge performance gap it involves, I will do everything to keep Turbolinks alive as much as possible.


## 5. Not using an "action view library"

React or Vue may be optionnal, but the need may arise quickly from the UI/UX part without a warning. So in my mind it is better to be prepared.

I won't use StimulusJS, because without centralized state, reasonning about what is going on in the frontend is a true nightmare.


## 6. Fall into the "Technology lock-in trapp"

I made this mistakes twice : with the Teaspoon JS test runner, and KnockoutJS.

These are very decent technologies, robust, but not anymore actively maintained.

Over the long run, it involves a lot of lacking features, that may be very frustrating compared to newer equivalent projects.


## 7. Over engineered deployment solution

I used mina for deployment, but I feel now that the bunch of configuration needed is another example of "Technology lock-in"



## 8. Not starting with Docker

Using marketing words, Docker is a huge "pain-killer". 

**Any newbies** can install the app from scratch, run specs, deploy to production or staging, with a very small README and very small technical knowledge.

**Any services** (like redis or) can be added with 4 or 5 lines of configuration.

**Any version upgrade** of any service is completly effortless.

It requires some efforts to keep the Docker stack simple, but, like Turbolinks, once mastered, the advantages quickly outweigh the negative effects. 


## 9. RSpec

This is more controversial, but after having trying both RSpec and Minitest, I will go for Minitest.

Minitest is a lot more simple.

Of course, this simplicity comes with a cost : duplication.

But RSpec push the "cleaning" part of each test too far, making hard to reason about a single test.

It is easier to reason with minitest, and not *that* difficult to propagate a modification through all duplications.




## 10. Stay away from the Rails way

If you try to do something against the framework, you start to loose time and energy very quickly, which is precisely what Rails is fighting against.

I once started to put all the controller logic inside *service classes* to increase testability of what the controller is supposed to do.

That was a very bad idea, actually. It adds a layer without increasing any value of the unit tests suite.

Now I keep the controller logic inside controller logic, and this logic is tested through end-to-end tests.



## 11. Add a few layer if necessary, that's very ok

It seems a contradiction of the previous paragraph, but it's not.

I badly miss a view layer in some cases, the I added an app/view folder and then I was done.


## 12. InuitCSS

There's not much to say in CSS. I will still follow BEM-IT convention, OO structure, naming classes as close as possible from their target, and that's enough to get a long-term, maintainable project.

I hope that webpacker and postCSS will increase some performances. But as for writing CSS, stick to the few principles above and you're done.

I appreciate inuitCSS a lot, and I will probably use it again.

But I find the spacing utilities very verbose, and I hope I can switch to another framework like KNACSS the next time.


## 13. I won't avoid : rails-administrate

Well this is probably where Rails outperform its competitors. You have a free, intuitive, secured, customizable administration part for free.

As far as I know, there are no framework with such an advanced admin panel.

So in my next project, I will avoid **not** to use it :)



## 14. I won't avoid : guys of Thoughtbot and Gorails

Well, I don't know how to thanks them enough. Their guides are invaluable and helped me to get things done.

There are others of course, but I can't remember of each so I just want to thanks the community a lot

😍😍😍

David.


