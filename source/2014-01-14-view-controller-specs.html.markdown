---
title:  "On view and controller specs"
---

> We don't write \[view\|controller\] specs because that code is exercised by the request specs.

I recently converted all views on a project from ERB to HAML. There were no view specs, and I wasn't entirely confident in my understanding of the project to be sure that I wasn't going to break anything in the transition. So I went through the tedious process of adding view specs for all views. When I got to a set of partials that had only text content (terms of service, etc.), I was tired and thought that my spec for the layout views that include these partials should tell me if I broke anything.

Well I did break something. And though the layout view specs told me that I had broken something, they weren't entirely clear which partial was causing the error. I had two choices: comb through all the partials looking for some syntax error or write view specs for the partials and smoke out the error there. I chose the latter, writing stupidly simple specs that basically confirm that the views render, and in the process, I quickly found my error.

I think for a lot of developers (even TDDers), testing is a balancing game: we want the most coverage for the least amount of testing. We rely on request specs or cucumber features--both integration tests--or other existing specs that exercise what will be the production code we're about to write. Views and controllers shouldn't be doing much anyways, so light coverage is all we need. Or so we think.

When we stop writing focussed unit tests, we take big steps. Often we're confident that we're not going to break anything with these steps; we've done it a million times before. But maybe we make a typo or introduce some other regression. As was the case for me, our steps are just big enough that it takes longer to track down a regression than it would have if we had been taking smaller steps. And let's not forget that our tests are no longer driving our development or design.

Integration tests are great. They confirm that the system as a whole is wired up correctly. But they should never be relied on to get fine-grained feedback on individual objects. View and controller specs give you immediate feedback on how you're doing and guide you through your development.
