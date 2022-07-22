---
layout: post
author: David Boureau
minread: 4
title: "Rails : a concern about separation of concern"
date: 2020-10-27
categories: work
permalink: /blog/:title/
description: "Rails is shipped with a very low separation of concerns. This might be a concern :)"
---


## Intro

I work with my Ruby-on-Rails friend for more than 5 years now. I'm a Rails zealot since first day, and still today.

There is still one thing that annoys me : separation of concern  - abbreviated SOC from now on :)

So what is SOC ? Well, it basically means that each class, each function, each piece of code does one thing, and only one thing. A Model represents data and that's all. A test will (ahem) test one thing and nothing else. A controller will respond to a request and nothing else. A view will display something to the user and nothing else. And so on.

## Problem

Rails new app doesn't  enforce you (or not much) to separate cleanly each piece of code. Action Mailbox and ActionText are very nice-to-have options (and incredible work given to the community for free), but stands very far behind the need of SOC.

I do not understand why Rails is shipped with such a low SOC by default. 

IMHO, this is why a lot of devs (unfortunately) dislike this stack, and why Rails (great) adoption didn't break the roof as NodeJS did.  

If you use Rails official examples and default scaffolders, you end up with :

- models in the view (!!)
- business rules that happens inside the controller (or model),
- UI error messages hold by the model, 
- validations that happens where response to the request is supposed to happen (inside the respond_to block).

In theory, official  ["Rails Concerns"](https://api.rubyonrails.org/classes/ActiveSupport/Concern.html) could help, but they only partially solve the problem, and pretty much disliked by the community.

Unhappy experienced Rails developers come with their own solution to the problem : Concerns (official waynot liked much), Form objects, Validators, Interactors, Service Objects, and so on.

Which is kind of ironic once you noticed that, aside from SOC, the incredible abstraction power of Rails saves you tons of work hours and energy.

I have my own way to tackle the lack of SOC, but this will be for another article.

## Bottom line

I'm kind of annoy to give any advice since I use Rails a lot without contribute to it. 

But the point is : the Rails team should work on a default clean SOC. Very like Webpacker : you can use any JS framework you want (or skip web pack entirely if you don't like it). These are all valid options, depending on your experience with ES6.

The same should apply with SOC. Rails should be shipped with valid SOC options by default. "Valid" means widely enough adopted practices. 

I can't see any experienced Rails dev to like and adopt the practice of a model inside a view...

The next big thing in Rails 7 should be : SOC.

What are your thought ? My preferred way to talk in on reddit so do no hesitate to comment this article.

Cheers ! stay safe.

And a big thank you to the Rails community 
😍😍😍

David.


