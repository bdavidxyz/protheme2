---
layout: post
author: David Boureau
minread: 9
title:  "Feedback about an Ember-Node app"
date:   2017-03-18
categories: work
permalink: /blog/:title/
description: "Experience feedback"
---

<p>&nbsp;</p>

[Pix](https://pix.beta.gouv.fr) is an [open-source project](https://github.com/sgmap/pix) initiated by the French Ministry of education.

I just spent 6 month on this very new project, here is a feedback as a Javascript developer.

**EmberJS, the good parts.** 1) Ember is strongly integrated and opinionated : it makes tons of valueless, technicals decisions for you, this feature alone makes a huge difference compared to other SPA frameworks competitors. 2) Ember is very intuitive if you already did some Backbone or Angular before, so assumption that Ember has a high learning curve is simply not true. 3) Ember team is available on Slack, this help is pure gold.

**EmberJS, the other parts.**  1) I felt qUnit is deprecated compared to mocha.  2) ember-data is counter-intuitive, unlike the rest of the framework. 3) Sometimes, Ember fails silently instead of raising an exception 4) testing is not as easy and intuitive as it should, examples available on docs are too gentle. Ember misses a few “showcase” big open-source project with tons of examples that could help on that point.

**[Airtable](https://airtable.com/) is awesome.** Sorry to talk about a commercial software here, but it saved us so I find quite fair to talk about it. It is a SASS product, comparable to an advanced Google Spreadsheet. It allow the business dudes to administrate the backend by themselves. You add/remove strongly typed columns on-the-fly without technical skills. It saved the project when the needs of the Product Owner were not well defined, and were moving very fast.
When a project starts, it’s definetly far better and agile than hand-made or scaffolded admin backend.

**NodeJS in the backend is not _that_ awesome.** I don’t really understand “the hype” around Node. It has a very low time-to-market, has no deep integration nor opinions like Ember or Rails. It took us monthes before to have a really productive stack, and even so, classic requirement like building an authentication system is quite a big challenge. For persistence, we chose not-so-well-known knexJS and bookshelfJS. Figuring out how to make our first "make an update in a SQL database" was a difficult, technical story. It's hard to forgive in 2017. Coding everything in an asynchronous way is unsurprisingly harder than the synchronous way, even with “Promises”. 

Questions...

Can you do achieve every requirement you want with NodeJS ? Yes. 

Is it fast, "enterprise-ready”, testable, scalable ? 

Yes, yes, yes, and yes.

But it’s not “sweet”.

If this point matters to you, I suggest you [this article](https://medium.com/the-node-js-collection/why-the-hell-would-you-use-node-js-4b053b94ab8e#.3je1csdwx).

**ES6 is easy.** Not a big deal if you wrote vanillaJS. It makes code shorter and more robust. 

**Relationship to Product Owner is the “human" key to success.** I have the feeling that would the project be written in PHP or assembler, it would still have been a great success. Once you have a strong mutual confidence, mutual understanding, and benevolent behaviour with your PO and team, the project will succeed.

**Product Owner is unable to create exhaustive acceptance criteria.** We dreamed about acceptance criteria that could be automagically mapped to automated tests. This is impossible. We had once a single acceptance criteria (written by PO) that was actually converted into more than 100+ automated test.  You simply can’t ask your PO to write and think about every rules, especially implied rules. It’s your job as developer to convert requirements into realistic business rules. Just rely on the trustful relationship described above with your PO.

**The control of your test suite is the "technical" key to success.** Ok, there are plenty of technical aspects other than testing, but I had the feeling that this one is the most important for any project, this one makes no exception. Once you start to feel that every piece of code fall right were it should, and is tested by the right test the right way, both productivity and quality break through the roof. 

For the Single Page App, the development mode is served by a fake server (Ember Mirage), with stubs that only covers the nominal scenario. This mode allow us to write higher-level test, that covers mostly routing and component communication. We also have classic unit test that covers function in isolation, integration tests that covers components in isolation. This rocks.

For the backend, it’s a classic approach : integration test are our highest-level, with internet connections cutted by NockJS, everything else falls in the unit test area, with help of mocha / SinonJS.

UI/UX must be defined before to write any code.  The SketchApp/Photoshop/static HMTL prototypes must be completely defined and validated before to write any line of code. If not, you can’t finish a user story or task. Before we hired a designer, we had to rewrite every piece of functionalities twice or more. Everybody understood the “what", but each member had a different opinion on “how”. I hope I won’t do that mistake in my next projects :)

**Avoid bootstrap if you enroll a designer.** Not using Bootstrap is a mistake if you have no designer. It saves times and energy like no other CSS framework. But once you hired one, drop Bootstrap. We started to fight against the framework to meet designer requirements, which was bad. So now we tend to drop Bootstrap dependency, one component at a time. If you start a fresh new project with a designer in the team, you can pick a lightweight CSS framework like ConciseCSS or KNACSS.

**Retrospective is the only mandatory process.** It doesn’t matter much if you are certified Scrum Master or the top-notch Kanban dude of the universe. But retrospective is a mandatory meeting, IMHO. Where you can debate of the utility of other processes. With it, you can continuously improve atmosphere, productivity, tools, everything you need to.
 
**Be paid for an open source project Once in your career.** This rocks. This demonstrate your abilities more than any resume.
