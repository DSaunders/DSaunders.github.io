---
layout: post
title:  "It's not Agile's fault"
meta-title:  "It's not Agile's fault"
subtitle: "A bad team doing agile doesn't make agile bad for the team"
date:   2014-06-10 18:00:00
---


Recently, [Mike Hadlow](https://twitter.com/mikehadlow) wrote a great article entitled ['Heisenberg Developers'](http://mikehadlow.blogspot.co.uk/2014/06/heisenberg-developers.html).

The article is essentially a story about how management brought in what I'll call an 'agile-ish' process.

The article is a great cautionary tale about how not to alienate your development team. I  would like to contrast Mike's story with my experience of working in agile teams. I'm worried that there are other people in the same situation as Mike, who will turn against 'Agile' because of similar experiences.

It doesn't have to be this way..

# Micro-management of features

Mike describes how a process was put in place that required developers to split larger requirements into smaller tasks, until everything was less than a day long.

He talks about  how the developers that stayed with the organisation during this change (or came in afterwards) were a different type of developer; less passionate programmers who were happy to work on one small task at a time and not think about the bigger picture.

 >As one explained to me, “you take the next item off the list, do the work, check it in, and you don’t have to worry about it.”

This is definitely a danger; I've met the developers who are happy to work on their task in isolation, with no interest in the overall design.

The solution is this.. don't hire these people. I do think that some agile processes can make it easy to hide this kind of behaviour for a while, but no agile evangelist worth their salt will advocate that a developer isolates themselves and just churns out features with no awareness of the overall picture.

Once a developer works on a user story, that story belongs to them. They are responsible for seeing it all the way through to production. If it doesn't play nice with others, it's their responsibility. If it doesn't fit into the way the guy across the office is architecting his solution, it's their responsibility. That way, the team is forced to work together and develop an architecture that works for everybody.

Breaking larger features into smaller tasks has other benefits too. It forces the stakeholder to be more specific about their requirements. It would love to be able to spend a few weeks working on a feature totally uninterrupted. The chances are though, that what I develop would have little relation to what the stakeholder wanted. Small user-stories force this out into the open before we write a single line of code.

# Sprint planning

> As soon as you ask a developer to tell you exactly what he’s going to do over the next 8 days (or worse weeks or months), you kill much of the creativity and serendipity.

I totally agree, but I think there's a difference between forcing a developer to predict every hour of the next sprint, and just prioritising tasks.

Sprint planning should be about deciding what is going to add most value to the business over the next couple of weeks, and deciding how much of it can reasonably be done.

Developers should not be tied strictly to these estimates; sometimes we get it right, often we get it wildly wrong. It happens (and the business should be able to deal with it), but it's reasonable to expect us to provide at least an indication of how long something will take.

I dislike estimates as much as the next guy, but if I was paying the bills, I'd like to have at least a rough idea what functionality I was going to be getting for the next 2 weeks of my development budget.


# Lack of refactoring

Mike talks about how they could not refactor their code when they needed to.

> Whenever there was any debate about refactoring the code, or backing out of a problematic feature, the new guys would argue against it, saying it was ‘ivory tower’, and not delivering features. The PM would veto the work and side with the new guys.

I have to say that refactoring is not automatically out of the question in an agile team. I have worked in a team where I would be quite confident to approach the PM and tell them that I would have to take a little longer over the current user-story because I needed to refactor a related part of the code.

A user-story is not 'done' until the developer is happy with the code. If a developer finds something they can improve along the way, it is their professional responsibility to fix it. Not doing so will ultimately slow the project down in the long run (as Mike describes in his article) as the technical debt mounts up.


# Being measured

The crux of the article is that by measuring a developer, you slow them down. Whilst I think this is true in the case of Mike's team, with Mike's management, I don't think it's always true.

I'm a data geek, and I actually love having metrics around the development process. I want to know how many story points are left in the sprint; how many stories are queued up for the next live release; how much technical debt we are carrying. Knowing this stuff makes the team better and tells us where the process works and where it doesn't.

The danger of this is that we measure *developers* instead of the *team*. The metrics are designed to make the team more efficient, if we start to hold individual developers accountable then it becomes every man for himself and all is lost.


# Conclusion

I agree with almost everything Mike says in his article. I would have the same feelings had I been in that team. To be clear, Mike never once says that the entire 'agile' process is wrong.

I think it's important however, to explicitly disassociate teams like that with the overall goal of 'doing agile'.

Whatever names people dream up for the agile process to put on their certificates, the whole point of it is to be able to adapt to improve the overall team.

In Mike's instance, the process wasn't working. The *truly agile* thing for management to do in that organisation would be to rethink the process.

If you read Mark's article and you are in the same boat, please don't let it put you off any of the concepts the management were *trying* (badly) to introduce.

Some organisations are dysfunctional and just happen to be trying out agile processes..

These places would be dysfunctional regardless, **it's not Agile's fault**.
