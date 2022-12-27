---
layout: default
title: Sigma Algebras and Measurability
parent: Probability Theory
grand_parent: All Things Statistics
has_toc: true
has_children: true
usemathjax: true
---

# Motivation for Sigma-Algebras

In probability, one fundamental object of interest is the **outcome space** denoted by $\Omega$. This is the set of all possible observable outcomes. Any subset of $\Omega$ is called an **event** For example, in flipping a coin twice, the outcome space is

$$\Omega := \{HH,HT,TH,TT\}$$

This is a countable set of events, and in their entirity, forms the outcome space $\Omega$. Here $\Omega$ has a cardinality of 4, and it is a finite outcome space. Things are easy to calculate here. For example $\mathbb{P}(\text{at least one head}) = \frac{\|\{HH,HT,TH\}\|}{\|\Omega\|} = 3/4$.

In the example above, the outcome space is finite, and all possible subsets of the outcome space is enumerable and we can assign probabilities to each event in $2^\Omega$. However in an infinite outcome space, it is no longer possible to enumerate all the events with probabilities. Instead, we focus our attention to subsets of "interest." In this context, a set is interesting if these sets a probability assigned to it and we wish to evaluate the probability. In any outcome space we would be interested in events as enumerated below:

1. The empty set, which has probability of 0
2. For a given event, the complement of the event should also be of interest
3. For any given set of events, their unions should be also of interest

These three qualities completely define all sets that are of interest to us. Of course, you might wonder, what about set intersections, using the coin flipping example, we might be interested in the quantity $\{HH,HT,TH\} \cap \{HT, HT, TT\}$. Namely, this is the intersection of the event where we get at least one head, and the event where we get at least one tail. The intersection of these two events is $\{HT, TH\}$, which is clearly a set of interest, and it has probability $1/2$. Surprisingly, this set intersection example is already covered by the 3 qualities of "interesting" events.

These three charactersitics of "interesting events" forms a logical structure called the $\sigma$-algebra. A $\sigma$-algebra of events in $\Omega$ is simply the power set $2^\Omega$ which has 16 elements in it. Now if we consider the outcome space of rolling a six-sided die, the $\sigma$-algebra of events is again the power set of $2^\Omega$ where this time $\Omega$ is the set of numbers from 1 to 6. Now lets make the game more complicated, and suppose the computer rolls the dice for us, and it will not tell us the result of the roll. Instead, it will check if the number is 1 or 2 in which it will tell us 'A'. If the roll was a 3 or 4, the computer will tell us 'B'. And finally if the roll was a 5 or 6, the computer will tell us 'C'. So we never observe any numbers, and we only observe the resulting 'A', 'B', or 'C'. Our $\sigma$-algebra will look like: 

$$\Omega := \{\emptyset, \{1,2\}, \{3,4\}, \{5,6\}, \{1,2,3,4\}, \{3,4,5,6\}, \{1,2,5,6\}, \{1,2,3,4,5,6\} \}$$

It is not productive to try to imagine what a $\sigma$-algebra should look like. 

**Exercise**: Show that 