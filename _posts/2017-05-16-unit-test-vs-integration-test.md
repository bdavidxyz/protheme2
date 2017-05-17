---
layout: post
author: David Boureau
minread: 8
title:  "Unit tests vs. Integration tests"
date:   2017-05-16
categories: work
permalink: /blog/:title/
description: "How unit and integration test compares, and when to write them"
---


## How's there ? 

A unit test happens when you test the smallest part of your application is under test, which means : a function.

If the function under test calls another function, it is an integration test. 



## Clichés

**Unit tests** are the holy grail of automated testing. You should cover everything with unit test, or you’re not what can be called a “developer”.

**Integration tests** are slow, only beginners write such crappy tests, because they are more intuitive to write at first place.


<h2><s>Clichés</s></h2>

Despite unit-test activists occupy the place on Stackoverflow, numbers of articles show that **[all](https://chriskottom.com/blog/2017/04/full-stack-testing-with-rails-system-tests/)** is **[not](http://rbcs-us.com/documents/Why-Most-Unit-Testing-is-Waste.pdf)** that **[simple](https://henrikwarne.com/2014/09/04/a-response-to-why-most-unit-testing-is-waste/)**. Without googling, simply ask developers around you if they covers everything with unit test, you might be surprised.

<h2>Coding monopoly "player turn" function</h2>

This how the call stack of how the “player_turns” function of Monopoly game could look like.


![Monopoly player turn](http://res.cloudinary.com/bdavidxyz-com/image/upload/v1494419163/catan2_d3u4aj.png)

### roll_dice

The first day of your project, you have an automated test that covers the "player_turn" function. "roll_dice" is such a classic requirement, that is has already made and tested by another library. Good ! No need of any test right now.

### move_pawn

Then you write the "move_pawn" function. It's actually just reflecting the output of the "roll_dice" function, which is 12 possibilities (two 6-sided dices). Keep an integration test that covers both roll_dice + move pawn is ok.

_Boring._

### pay_stuff

But one day the boss come to the office and say "Hey Alfred, the player may buy something after the pawn has been moved."

**Uh-oh.** You realize that 98 different items could be bought, which makes 98 * 12 cases to cover.

You can either

 - Write 12 * 98 = 1176 integration tests.
 - Or write 12 + 98 unit tests, and keep 1 integration test just to ensure every function can talk with each other = 111 automated tests.

Write unit test **often** (but not always) means **write less code with higher confidence.**

## Conclusions

 - Always start to write higher-level integration, they are far easier to write, closer to actual business rules.

 - Make every test go as fast as possible, no matter what kind of test it is. It may require subtle work to get it work for integration test.

 - If the underlying call stack of the function under test suddenly have a combinatory explosion, transfer your integration test to unit test.

 - If this happen, always keep at least one integration test to ensure the whole stack can properly.

 - The kind of test is not _that_ important, as long as the description stick to business rule, understandable by a non coder.

 - Be pragmatic about the actual value of your test, don't be shy to delete/move/update an existing test.

