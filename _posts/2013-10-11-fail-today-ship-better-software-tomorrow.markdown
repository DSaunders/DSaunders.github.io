---
layout: post
title:  "Fail today .."
meta-title:  "Fail today .."
subtitle: ".. and ship better software tomorrow."
date:   2013-10-11 17:00:00
---

I am privileged to work with people who are very interested in the Agile work flow and Continuous Integration.  As I learn more about these things myself, I realise there is a common theme across everything we are trying to achieve:

*Fail as quickly as possible.*

As long as humans are writing code, bugs will happen and mistakes will be made; that’s entirely normal and is to be expected when creating something new.  The processes we put in place are designed to catch these failures at the earliest stage we can.

If the customer sees the bug, we didn’t catch it early enough.  If we find it before it goes live, we can deal with it swiftly and move on.

If we have the ability to do that, we allow people to fail without fear; which means we can try new things and push our software forward, rather than play it safe.



#User Stories

User stories are one of the earliest stages of building a feature, where we sit down and describe how the user will interact with our product.

A colleague of mine suggested that this time is not just for writing cards for the Kanban board; it is also the time to address any queries and narrow down on the specifics of the requirement.

Are we building something the user actually wants?  Are we implementing it correctly?

This is generally when we should consider time estimates too:

Is it realistic to fit this feature in to the next sprint?  Are we underestimating how long it will take?

It’s better to find this out now than two weeks down the line when we are under huge pressure to ship it.  Something that can seem simple when written down can actually be incredibly difficult to implement in code.  This is probably the time to have that discussion.



#Unit Tests

Isn’t it cool that we can have an automated process that will catch bugs before we even commit our code to source control?  If we have good unit tests around a feature, we have much more confidence that it will behave the way we intended.

Testing whether a feature works is easy.  Testing the ‘edge-cases’, the unique occurrences that we don’t usually find until we’ve shipped, is hard.  That’s why unit testing is so great.  We can list all of the bad inputs or potential issues our code could have and know at build time whether we have coded a robust solution around those things.

Unit testing also allows us to work on the code later without fear of breaking it.  We can re-factor, fix bugs and add something new; all the time knowing that the original functionality is not affected as long as the tests are passing.

This all relies on us writing good tests of course.  I am still trying to learn the best practices around unit testing, but there are loads of resources out there to help.



#Staging/Test Servers

Even if we are reasonably happy that the feature is as intended and the code is robust, it might be a good idea to stage it somewhere before letting it loose.  In an ideal world, we would do all of our development in an environment identical to that in which the final product will run.  In practice that is actually quite hard to achieve.

By deploying our code to a staging area (this is an exact replica of the live environment), we can reproduce the customer experience before releasing it into the wild.  This is the time when we can catch the ‘it works on my machine’ issues that every project has.  Any integration tests will also be run here.

This is also a good place for the feature to be reviewed by any stakeholders.  What they are seeing should be exactly what the customer will see.  If any changes are needed, it’s not too late to make them before the code finally leaves the building.



These are just some of the ways to trap problems early before they get as far as production. Did I miss any?
