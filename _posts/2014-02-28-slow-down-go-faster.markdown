---
layout: post
title:  "Slow down, go faster"
meta-title:  "Slow down, go faster"
subtitle: "How slowing down and taking a breath will actually make you deliver faster"
date:   2014-02-28 17:00:00
---

We always want to move faster; faster requirements capture, faster and more efficient coding, faster to production. That’s all well and good, but if we try to go too fast, to soon, things can go really bad.

Let’s take a step back, take a breath and slow down.

The fastest way to get from requirements to production is to do it right the first time. If our software sails through the QA process, and we build what the customer actually wants first time, doing it once must be quicker than doing it twice, or three times, right?

The second fastest way is to do it well the first time. No project survives the user unscathed. You will have to come back to your code and make changes. Writing clear, maintainable code now will save you time hacking around it later on.

Let’s worry about doing it right first, doing it well second, and then we can make all the other stuff quicker later.


#Good requirements

I’ll just clarify before everybody runs for their browser’s back button, by requirements I do not necessarily mean a 2 foot tall stack of A4 paper which nobody will read. We do, however, need something to work from.

Most people are probably doing waterfall with user stories under the guise of being Agile. That’s fine, it’s a perfectly valid solution and it works well. Those user stories are requirements; the stakeholder can read them, you can develop against them, test against them and clearly define when those requirements are complete.

Five different versions of designs and three pages of emails going back and forth with a customer are not requirements. You cannot show that requirement to a stakeholder, you cannot be sure what exactly you are supposed to be testing against, and, if you have to spend an hour working our whether that change document from Wednesday is more or less recent than version 2.1.a of the design PSD, you cannot develop efficiently against them.

Take time at the start of the process to define the requirements properly. Get all of the various emails and documents into one place, and write a clear set of requirements.


#Write some tests

Unit testing adds very little time to a project, so let’s get that out of the way now. It might take you 5 minutes longer to type the thing, but we all know by now that the bulk of the time spent on something is in the thinking, not in how long it types to press the keys to put the letters on the screen.

Unit testing ensures that the feature actually works. It saves you the time and embarrassment of finding out from QA (or worse, the user) that your code is broken.

We don’t need to keep discussing this. It’s 2014, just write some tests already.


#Collaborate

Before you start a particularly complex user story, spend five minutes with another developer discussing it.

Often, we can just go headlong into code with only a half-baked idea of how to do it. It’s only when we get a day into the code that we realise it was probably the wrong way to approach it. Spending five minutes at the start discussing it with somebody else could save you from that.

The worst case scenario is that you both have the same approach and you have spent five minutes agreeing with each other.


#Pair

Good luck selling this to non-developers, but pair programming is actually quite efficient. Working together on a difficult problem often means it is solved quicker. It is also more likely to produce cleaner, more maintainable code, as it provides the benefit of real-time code review.

Over time, pairing will increase the overall momentum of the team. This is because it prevents knowledge silos, where certain developers have the super-secret-hidden-way of doing something that nobody else knows how to do. If that person is off work, or busy, the project stops. Pairing is a great way to avoid that.

I’m not suggesting that we all pair 100% of the time, but it should be a regular practice and accepted (even encouraged) by the organisation.


#Daily stand ups

Stand ups are ten minutes well spent.

They force everybody to think about their day up front. This is where they raise any issues they might have during the day which may block them, which means they need to think early about what issues they might face. Removing a developer’s blockers now means that they can work uninterrupted for the rest of the day. There is nothing that slows down development more than breaking a programmer’s concentration.

Stand ups also help to avoid you solving a problem somebody else has already solved months ago in a different context. By discussing what you plan to do, it allows other developers to chip in now with knowledge and experience that could shave hours off of your development time.

*N.B. Any in-depth conversations should be parked and discussed outside of the stand up to avoid breaking the momentum of the group.*
