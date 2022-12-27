---
layout: default
title: Probability Theory
parent: All Things Statistics
nav_order: 3
has_toc: true
has_children: true
usemathjax: true
permalink: probability/probability
---

Probability theory was not formalized until [A.N. Kolmogorov](https://en.wikipedia.org/wiki/Andrey_Kolmogorov), a Soviet mathematician, set out to view probability as a measure - and this viewpoint drew upon the work of [Henri Lebesgue](https://en.wikipedia.org/wiki/Henri_Lebesgue) who generalized the field of measure theory via integration. From calculus-based probability, we saw that a probability was either a sum or an integral over the density or mass function, and at the time of studying it, we did not necessarily need to connect the ideas of "measure" and "integration" together, but in order to better understand properties of probability, it is crucial to visit measure theory and to view probability as a measure. 

Before delving into probability, you might ask, "Why are we only focusing on integration as opposed to summations when dealing with mass functions?" It turns out that an integral will generalize a sum. The connection to measure theory is that instead of integrating with respect to the Lebesgue measure, we integrate a step function with respect to a counting measure to represent a sum. Of course, none of this will make sense to you if you have not studied integration as a measure theoretic concept - and hopefully after reading these pages, it will become more clear to you.

One of the core motivations for studying measure theoretic probability is to understand the concept of limits and infinities - which is where analysis comes into play. An outcome space with a finite number of outcomes is easy to analyze, and we are able to enumerate each event with a probability. However in the case of infinite outcome spaces, this is no longer so simple. Throughout the study of measure theoretic probability, it is critical to understand the notion of what it truly means when considering the "limit."

To this end, this lecture will follow closely to Durrett's ["Probability: Theory and Examples"](https://www.amazon.com/Probability-Cambridge-Statistical-Probabilistic-Mathematics/dp/0521765390)