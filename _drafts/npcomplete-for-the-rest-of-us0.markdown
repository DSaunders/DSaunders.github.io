---
layout: post
title:  "NP-Complete for the rest of us"
subtitle: "An explanation of P, NP, NP-Hard and NP-Complete that you don't need a CS degree for"
date:   2013-04-01 18:00:00
---


We often hear problems in computer-science classified as NP, P, NP-Complete, or NP-Hard, but what do they actually mean?

The definitions on Wikipedia are good, but hardly easy reading. This post aims to explain what these terms mean in a way that doesn't require you to have a CS degree.

It does use slightly simplified definitions of the terms, so please expand on this by reading more about the concepts later.

*Disclaimer: I'm assuming that P != NP for the purpose of this post*

Lets get going...

#Definitions

We need to go through the definitions of these terms first. These will become clearer with the examples that follow later, so just skim read this bit and refer to it later.


**P**

The formal definition of problems in *P*, is that a solution can be found using a Deterministic Turing machine in polynomial time.

This essentially means that you can solve this problem algorithmically in a realistic time. This would also mean that you could verify that a solution to this problem was correct with relative ease.

These are the simplest problems to solve.

**NP**

The original definition of *NP* is that a problem can be solved in polynomial time using a non-deterministic Turing Machine.

A simpler way of understanding *NP* is this:
If I gave you a solution, you could *easily* verify that my solution is correct.

Note that this does not mean that you can *solve* the problem easily, only that the *solution* is easy to verify once found.


**NP-Hard**

A problem is NP-Hard if it is at-least as hard as the *hardest* NP problem.

In other words, if I can find a way to solve this problem, I can solve *every other* NP problem.

This is done by *reduction*; proving that this problem is essentially the same as another problem that is already known to be NP-Hard. Somebody already decided what the first [NP-Hard problem](http://en.wikipedia.org/wiki/Boolean_satisfiability_problem ) was, so all we have to do is prove that ours is like that one, and it then becomes *NP-Hard*.

It is generally accepted that we cannot solve *NP-Hard* problems yet (at least until quantum computing becomes a thing). If we could though, we could solve *all* NP problems.


**NP-Complete**

This is where it gets a little confusing until we look at the examples later, so bear with me for now.

A problem that is *NP-Hard* does not have to be in *NP*.

Consider an extreme example; a problem that is *impossible* to solve and where a
solution would be *impossible* to verify even if it were found.

This problem is *at least as hard as the hardest NP problem*,
in fact it's harder (it's impossible!), so it's definitaly *NP-Hard*.  


This problem can't be in *NP* though, since if I gave you a solution it would be impossible to verify.

If a problem *is* NP-Hard *and* in NP however, we can say it is *NP-Complete*.


This all makes much more sense with examples, so let's take a look at some now...


#Example 1 - Even number test

<span class="left-image">
![Even Number Problem](/img/np-hard/even-number-problem.png)
</span>

What if I asked you; 'tell me all the even numbers between 1 and 10'.

If I told you the answer to this problem, you could *very easily* check my answer, so we can say that this problem is in *NP*.

We can also *easily* solve this problem in a realistic time, just iterate through the number and check whether they are divisible by two. That means this problem is also in *P*.

This problem is actually quite easy though, so it would be unfair to claim that if we solve *this* problem, we can solve *every other* NP problem. So the problem is *not* NP-Hard, which means it cannot be NP-Complete either.

#Example 2 - Sudoku

<span class="right-image">
![Sudoku Problem](/img/np-hard/sudoku-problem.png)
</span>

Let's try something harder.

You couldn't solve a Sudoku possible using a computer in a realistic time period. There are so many possibilities for each square that as the size of the Sudoku puzzle grows, it gets exponentially harder to solve the puzzle. Because of this, we *cannot* say the puzzle is in *P*.

If, however, I was to give you a solution to a Sudoku puzzle; you could quite easily write an algorithm to check that my solution was correct. Just check that each column, row and 3x3 grid contained the numbers 1-9. That means the problem *is* in *NP*.

It also turns out that this problem is *at least as hard as the hardest NP problem*. If you simplify the Sudoku problem, is starts to look a lot like the NP-Hard problems that we already know about. That makes this problem *NP-Hard* also.

Because Sudoku is in *NP* and *NP-Hard*, we can say that it is *NP-Complete*.


#Example 3 - Travelling Salesman (Decision version)

<span class="left-image">
![Travelling Salesman (Decision version)](/img/np-hard/sudoku-problem.png)
</span>

Question: Given the locations of 50 cities, can I travel between them in *less that 3000 miles*?

You cannot find a solution to this problem in a realistic time. You would have to try every combination until you found one that was under 3000 miles, or you ran out of combinations. What if I gave you 500 cities, or 5000? This problem is definitely *not* easily solvable and thus definitely *not* in *P*.

If I told you I had somehow found a solution though, all you would need to do is check the distance of the route I gave you. If it was less that 3000 miles then my solution is correct. Because you can verify my answer easily, this problem *is* in *NP*.

If you think about this problem, it's actually quite similar to Sudoku. We know that Sudoku is *NP-Hard*, which means that this is *also* NP-Hard. We have the set of both *NP* and *NP-Hard*, so the decision version of the travelling salesman is *NP-Complete*.

#Example 4 - Travelling Salesman (The harder version!)

<span class="right-image">
![Travelling Salesman (Hardversion)](/img/np-hard/travelling-salesman.png)
<span>

Consider a variation of the example above:
Given the locations of 50 cities, what is the *shortest* route I can take and still visit all of them.

This is a very tough problem. You cannot solve it in a realistic time, so let's forget about *P* straight away.

It's fair to say that if we can solve this problem, we could *definitely* solve all *NP* problems like Sudoku. That makes this *NP-Hard*.

What if I claimed to have a solution to this problem though. The only way you could verify my solution is to check *every* possible route to make sure mine was the shortest. We already decided that this was impossible. Because the solution cannot be easily verified, this problem is not in *NP*.

This version of Travelling Salesman problem is an example of a problem that is in *NP-Hard* but is not in *NP* (and thus also not *NP-Complete*).
