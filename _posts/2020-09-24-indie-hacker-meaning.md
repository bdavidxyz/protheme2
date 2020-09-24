---
layout: post
author: David Boureau
minread: 13
title: "Indie hacker meaning"
date: 2020-09-24
categories: work
permalink: /blog/:title/
description: "Indie hacker meaning"
---


## 1. Definition

On his [excellent website](https://www.indiehackers.com/about){:target="_blank"} dedicated to indie hackers, Courtland Allen give us a great definition :

> You're an indie hacker if you've set out to make money independently. That means you're generating revenue directly from your customers, not indirectly through an employer. 

> Indie hackers are often solo founders, software engineers, and bootstrapped, but it's totally okay if you have co founders, can't code, and have raised money.

In short : technically speaking, you are *alone* to build a ❤️lovely❤️ product.

## 2. Constraint

So now you are the one-(wo)man-band. 

You're *alone* to achieve :

- Deployment
- Test suite
- Maintainable CSS
- Maintainable algorithms
- Database(s)
- Async Jobs
- Security
- Logging
- Accessibility
- Performance
- And probably a lot more...

Your business co-founder has one problem : 💰 market.

You have one problem : ⌛ **time** ⌛


## 3. How to avoid exhaustion

In a personal perspective, if you don't deliver value at a fast pace, you could quickly dive and endanger your motivation, finance, health, relationships, etc.

In a business perspective, 

> Faster shipping means a faster feedback cycle. Faster feedback cycle means you can make a lot of small bets, rather than investing a lot of time in one big bet. Statistically, a lot of small bets have a better chance of paying off for you.

So how to stay on the safe side of entrepreneurship ? 

### a. Experience

Without experience, outside the fact it will be longer to build the product, you will probably fail to prioritize tasks correctly. 

Which bug is important to correct right now, and which nasty hack can stay here for decades requires intuition, which can only be acquired by experience.

It could take months or years depending on your acquaintance with coding.

Try as many tools as possible, then pick the ones where you feel the most comfortable.

### b. Boring business, boring stack

Choose the most boring possible business. To the contrary, you should avoid 

<small>(list inspired from another dev)</small>

- Anything that requires a lot of users to achieve success.
- Anything that involves ML/AI, crypto, hard algorithm problems.
- Anything that involves scraping.
- Anything that is hot right now and you want to jump on the bandwagon.
- Anything that involves tons of complicated, nested, real-time UI screens.

I mean by "boring" : nothing shiny at first glance, but it solves a simple, perfectly identified problem by someone who already works in the targeted industry.

Be reassured, a vast majority of regular, everyday business problems can be solved with plain, [fullstack, server-rendered, boring](https://hackernoon.com/the-boring-stack-the-best-way-to-build-interesting-things-9f54420f683e){:target="_blank"} web framework.

### c. Trustful relationships

With your co-founder or users, build one-to-one, trustful, warm and friendly relationships  . 🥰 

Yeah I know, it may sound obvious, so I won't develop further.

## 3. A possible stack

### a. Deeply integrated, fullstack framework

I can see only 3 candidates here : Django, Laravel, Rails.

Why there are no such tools in the Java or JavaScript field remains a mystery (well, they actually exist, but are not widely enough adopted).

Without this "deep integration philosophy", you will spend time on hard, difficult, valueless, technical-only choices (like file & directory structure) instead of focusing on the business.

### b. Avoid JS as much as possible

It sounds completely to the opposite trend of these last years, but trust me, server-rendered pages are more than enough for 95% of your UI Screen.

Moreover, it will avoid you a heavy mental headache about how the data is supposed to flow before to be rendered.

Can you render this UI component directly from the server, with some sprinkled CSS ? well, no JS is needed.

You found a way to avoid this modal ? Avoid it.

Oh wait, this jQuery plugin does the job ? Avoid the no-jQuery trap and drop the plugin to your app.

I'm not an anti-JS. I learned & used multiple JS (ES6) frameworks.

But I use them on the very few cases they are needed : screens with reactive, nested UI components. In my last project it was needed only once (for *~100* differents screens)


### b. Bootstrap

In the industry I tend to avoid Bootstrap. It comes with design opinions in mind that does not match the ones of your UI designer.

However, these opinions save you tons of time for a solo project. Vertical rhythm, typography, helpers, a11y, bunch of utilities, components, and so on.

Do not choose another framework here, (except maybe Tailwind), because large adoption means tons of examples and help available at every corner case.

Do not overthink UI design. You can improve appearance and experience later on.

### c. Heroku

It saves you tons of devops & sysadmin problems, so go ahead even if everything is not perfect.

### d. Few tests

Keep a few high-level, integration tests, just the few that will maximize your confidence. In the industry it is a better practice to unit test everything, but for a solo project, chances are you will never have enough time to do so.

However each function you write must be very small, expressive, focused, easy to read, without side-effects, or maintenance will very soon be a nightmare. 

Like in your everyday job :)

## 4. Conclusion

I started with a definition of what an "Indie Hacker" is, with a simple consequence : time is not your friend. 

Being full-time or part-time on your solo project is the wrong debate : you must be efficient at all levels to deliver value at a fast pace, in order to avoid motivation fall.

This is why I listed all tools that are - not perfect, but who is ? - "good enough" to match this definition.

Something like 99% of startups will fail anyway, so this article was about how to lower that risk to only 95%. 😂

Good luck to all, happy coding !

😍😍😍

David.


