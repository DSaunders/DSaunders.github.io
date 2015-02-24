---
layout: post
title:  "Bug now, pay later"
meta-title:  "The 5-to-5 test"
subtitle: "You always have to pay back your technical debt.. eventually"
date:   2013-09-27 17:00:00
---

I was recently fortunate enough to go to the .NET Rocks! UK tour.  In it, Richard Campbell talked briefly about ‘technical debt’.  I thought it would be interesting to explore that metaphor further in a blog post.

Technical debt is when we write code we know will cause us problems later.  That could be because it’s the easy way out, or perhaps because we just don’t know how to tackle the problem any better right now.

I like the term technical debt because it implies a decision on the part of the developer.  Calling it bad code implies poor development skills, technical debt implies the developer made a conscious decision to borrow against the project now and pay it off later.



#Borrowing against a project

Governments and banks are run on borrowing.  Take the money now and pay it off later, with interest. Software projects are the same.

When we accrue technical debt, there is an always an interest rate.  This is analogous to the extra effort required to ‘fix’ the code when it comes to paying off the debt.  The longer we leave it before paying off a financial loan, the more expensive it is as the interest compounds.  The longer we leave it before fixing our technical debt, the more the code is baked in and the harder it is to fix.

Creating technical debt might not always be a bad thing; we just have to ask ourselves this question first:

Is it better to borrow now and have the instant reward (finishing a feature on time, fixing a bug quicker), knowing we will have to pay it off later with interest?



#Paying off the debt

Waiting until your code comes back to bite you is the equivalent of waiting for the debt collectors to come knocking.  At this point all we can do is pay them as much as we can afford at the time and defer them for a while.  If we are going to accrue technical debt we have to have a strategy for paying it back.

I’ve been unfortunate enough to work on a project that had so much technical debt mounted up that we had to declare it ‘bankrupt’. The only option was to wipe the slate clean and start again at great cost.  This is the inevitable consequence of not making the repayments.

In the .NET Rocks! talk, Richard talked about a company that had regular ‘bug fix days’ where all of their developers would spend the day fixing bugs instead of writing any new code.  I heard another story about a developer who used his 20% time to fix all the compiler warnings in a project, in doing so he uncovered several critical bugs that had so far gone unnoticed.  These are both examples of paying off the technical debt before it becomes unmanageable.



It’s impossible to go through a project without carrying some technical debt along with you. Doing so is surely futile, there is never enough time to finish a feature the way you would like and it’s impossible to get everything right first time.  As developers, we just have to be mindful of the debt we are building up and plan a repayment strategy for it before the debt collectors come knocking.

How do you manage technical debt?
