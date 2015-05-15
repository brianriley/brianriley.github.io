---
title: "What I read this week"
---

I read a lot of blog posts throughout the week. This is the first in hopefully a series of posts on what I've been reading. It's intended to be a record for myself, but might also serve to give others context for where I'm coming from.

###### [Hybrid sweet spot: Native navigation, web content](https://signalvnoise.com/posts/3743-hybrid-sweet-spot-native-navigation-web-content)

I may not agree with [everything](http://david.heinemeierhansson.com/2014/test-induced-design-damage.html) [DHH says](http://david.heinemeierhansson.com/2014/tdd-is-dead-long-live-testing.html), but I do respect his thinking. And I like a lot of what he says about web application architecture. This article is an interesting defense of web views for mobile applications.

###### [The Single Responsibility Principle](http://blog.8thlight.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html)

Uncle Bob has a great way of describing SRP, specifically with regards to the idea that modules of code should have only one reason to change. He says to think about "_who_ must the design of the program _respond_ to".

###### [Speeding Up ActiveRecord Tests](http://articles.coreyhaines.com/posts/active-record-spec-helper/)

Corey Haines loves fast tests. Who doesn't!? Most speaking and writing about fast tests focus on how to decouple your business logic from the libraries and frameworks we love to use. This isn't one of those posts. Corey shows how to test ActiveRecord models that connect to a DB faster than the default Rails way.

###### [Beyond Mock Objects](http://blog.thecodewhisperer.com/2013/11/23/beyond-mock-objects/)

This is one of those posts I think I'm going to want to read several times. I want this kind of thinking to become second nature. J.B. Rainsberger shows how dependency injection can be a crutch for actual design thinking. I read this article on Friday, and it was a great read in the context of the earlier DHH articles (J.B. shows how thinking about testability with no regard for design _can_ harm the design and what do do about it without giving up on TDD and testability all together) and the Uncle Bob article (the end result is code split up along SRP lines). Read those first.

###### [A Rocket To Nowhere](http://idlewords.com/2005/08/a_rocket_to_nowhere.htm)

Old but new to me. A longish read on the failures of the manned space program.
