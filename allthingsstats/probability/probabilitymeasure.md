---
layout: default
title: Probability as a Measure
parent: Probability Theory
grand_parent: All Things Statistics
has_toc: false
has_children: true
usemathjax: true
---

# Probability as a Measure
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

$\newcommand{\reals}{\mathbb{R}}$ $\newcommand{\pr}{\mathbb{P}}$ $\newcommand{\cv}[1]{\mathcal{#1}}$ $\newcommand{\nul}{\varnothing}$

# Laws of Probability

There are three main axioms in probability determined by A. N. Kolmogorov and hence called Kolmogorov's axioms. Given a **probability measure space** $(\Omega, \cv{F}, \pr)$:

1. $\pr(\Omega) = 1$
2. $\pr(A) \geq 0$ for all $A \in \cv{F}$
3. For disjoint sequence $A\_1,...,A\_n,...\in\cv{F}$, $\pr(\cup A\_i) = \sum \pr(A_i)$ (countable additivity)

We can derive some critical results on continuity and sub-additivity of the probability measure function $\pr: \cv{F}\to [0,1]$ from these axioms.

## Continuity

Continuity of probability refers to the idea that $\lim \pr(A\_n) = \pr(\lim A\_n)$ provided a limit exists. It turns out we can do this if $A\_n$ is a nested decreasing or increasing sequence. If a) $A_1\subseteq...\subseteq A_n \subseteq ...$, or if b) $$A_1\supseteq...\supseteq A_n \supseteq ...$$ then:

$$\lim_{n\to\infty} \pr(A_n) = \pr\left(\lim_{n\to\infty} A_n\right)$$ 

_Proof_ : The sets $A\_n$ are increasing so for any $A\_n \cap A\_{n+1} = A\_n$. Thus define $B\_{n} = A\_{n}\setminus A\_{n-1}$ where we let $A\_0 = \nul$. Here $B\_n$ becomes a sequence of disjoint sets with $\cup\_{n=1}^N B\_n = \cup\_{n=1}^N A\_n = A\_N$ for all $N$. Therefore,

$$\pr\left(\bigcup_{n \geq 1} A_n \right) = \pr\left(\cup_{n\geq 1} B_n \right) = \lim_{N\to\infty} \sum_{n=1}^N \pr(B_n) = \lim_{N\to\infty} \pr(A_N)$$ 

Note here we treat $\lim A\_n = \cup A\_n$ since $A\_n \subseteq A\_{n+1}$. 

The case for when $A\_n \supseteq A\_{n+1}$ works in the same way, and it is critical that we assume $\pr(\Omega) = 1$ to maintain that $\pr(\cdot)$ is a finite measure.

## Sub-Additivity

Sub-additivity refers to the idea that if $A\_1,...,A\_n,...$ is a countable sequence of events that need not be disjoint, then

$$\pr\left(\bigcup_{i\geq 1}A_i\right) \leq \sum_{i\geq1} \pr(A_i)$$

_Proof_ : Let $B\_1 = A\_1$, and $B_n = A\_n\setminus \cup\_{k < n} A\_k$. Then the sequence of sets $B\_n$ are mutually disjoint. This gives:

$$\bigcup_{n\geq 1} A_n = \bigcup_{n\geq 1} B_n$$

and we know $\pr(\cup\_{n\geq 1} A_n) = \pr(\cup\_{n\geq 1} B_n) = \sum \pr(B\_n)$ by Kolmogorov's axioms. Now:

$$\pr(B_n) = \pr(A_n\setminus \cup_{k < n} A_k) \leq \pr(A_n)$$

So putting it all together $\pr(\cup\_{n\geq 1} A_n) = \pr(\cup\_{n\geq 1} B_n) = \sum \pr(B\_n) \leq \sum \pr(A\_n)$. Thus proves the sub-additivity of the probability measure. $\tag*{∎}$

**Exercise** (Finite additivity): Prove that the probability measure is finitely additive, i.e. for $(\Omega, \cv{F}, \pr)$, if $A\_1,...,A\_N \in \cv{F}$ disjoint then $\pr(\cup\_{i=1}^N A\_i) = \sum\_{i=1}^N \pr(A\_i)$

**Exercise**: Suppose that we did not know about countable additivity, but we knew about finite additivity and countable sub-additivity. Prove that countable additivity still holds.

**Exercise**: Consider a sequence of events $A\_1,...,A\_n,... \in \cv{F}$ in probability space $(\Omega, \cv{F}, \pr)$. If for any pair of events $\pr(A\_k \cap A\_j) = 0$ then show $\pr(\cup A\_n) = \sum\_{n=1}^\infty \pr(A\_n)$. Be careful, $\pr(A\_k \cap A\_j) = 0$ does not necessarily imply $A\_k \cap A\_j = \nul$. (Hint: consider the finite case of $n$ events, then send $n$ to $\infty$.)

# Limit Inferior and Limit Superior of Events

The basic laws of probability have been built. There is nothing particularly interesting regarding basic probability laws, but we have now defined it as a measure and showed some basic properties. In the end, we hope to learn something about limiting behavior of these probability measures. Limits not not always defined, but from analysis, we know that $\limsup$ and $\liminf$ are always defined and when they are equivalent, then the limit exists and is defined.

From analysis, we know that $\limsup a\_n$ is essentially the largest completion value attainable occuring infinitely many times with respect to $n$, and $\limsup a\_n$ is the lowest completion value attainable. So if we have $a\_n := \sin \pi n$, then $\liminf a\_n = -1$ and $\limsup a\_n = 1$. The $\inf$ and $\sup$ portions are only meaningful since a partial ordering is defined on the real numbers. Likewise in sets, the partial ordering is $\subseteq$. We are ready to define $\liminf$ and $\limsup$ for sets now. Given a sequence of sets $A\_n$:

$$\liminf_{n\to\infty} A_n = \bigcup_{N\geq 1} \bigcap_{n > N} A_n$$

$$\limsup_{n\to\infty} A_n = \bigcap_{N\geq 1} \bigcup_{n > N} A_n$$ 

It is important to digest what exactly this means, especially if this is the first time seeing this type of set notation. 

## Limit Inferior

An event $\omega$ is in $\liminf A\_n$ if and only if it is in $\cup\_{N\geq 1} \cap\_{n > N} A\_n$. This means, there exists some $N$, such that we can find $\omega$ in _all_ $A\_n$ for any $n$ larger than $N$. This means $\omega$ is in $A\_n$ eventually, and that there are only finitely many $A_n$'s that do not contain $\omega$. To contexualize, I can pick an $N$ such that if this chosen $N$ is large enough, I can guarantee that $\omega$ is in $A\_n$ for all indices $n$ greater than the picked $N$.

## Limit Superior

An event $\omega$ is in $\limsup A\_n$ if and only if it is in $\cap\_{N\geq 1} \cup\_{n > N} A\_n$. This means, for all $N$, we can find $\omega$ in some $A\_n$ for any $n$ larger than $N$. To contexualize, if you give me any number $N$, I can still find at least one $A\_n$ that contains $\omega$ where the index $n$ is larger than the provided $N$. This concept is known as _infinitely often_ and is typically abbreviated as i.o. 

**Exercise**: Consider a sequence of numbers $a\_n$ where $a\_n := -1$  when $n$ is even and $a\_n := 1$ when $n$ is odd. Is $a_n$ odd eventually, or is it odd infinitely often? Is $a_n$ even eventually or odd infinitely often?

**Exercise**: Let $A\_n := [0, 1/n]$ be a set of numbers indexed by $n$. Describe what is in the set $\cup\_{N\geq 1} \cap\_{n> N} A\_n$ and what is in $\cap\_{N\geq 1} \cup\_{n> N} A\_n$?

**Exercise**: Let $A\_n := [0,1/3)$, for $n$ mod $3 = 0$, $A\_n := [1/3, 2/3)$ for $n$ mod $3 = 1$ and $A\_n := [2/3, 1)$ for $n$ mod $3 = 2$. What is in $\liminf A\_n$ and what is in $\limsup A\_n$?

**Exercise**: Prove $\liminf A\_n \subseteq \limsup A\_n$. 

**Exercise**: Prove $(\limsup A\_n)^C = (\liminf A\_n)$. (Hint: Use De Morgan's laws.)

Note: the last two exercises are important properties of $\liminf$ and $\limsup$ of sets. Make sure you understand them.

## Baby "Fatou"

For those exposed to some measure theory, [Fatou's lemma](https://en.wikipedia.org/wiki/Fatou%27s_lemma) may look familiar. Here, we present a relation similar to Fatou's lemma which we coin as Baby "Fatou."

$$\pr\left(\liminf_{n\to\infty} A_n\right) \leq \liminf_{n\to\infty} \pr(A_n) \leq \limsup_{n\to\infty} \pr(A_n) \leq \pr\left(\limsup_{n\to\infty} A_n\right)$$ 


We prove the first $\leq$. The second $\leq$ follows by definition from analysis.

_Proof_ : Using the definition of $\liminf$:

$$\pr\left(\liminf_{n\to\infty} A_n\right) = \pr\left(\bigcup_{N \geq 1} \bigcap_{n > N} A_n\right)$$

Note that $\cap\_{n>N} A\_n$ is an increasing sequence of sets as $N$ gets larger (less intersections make resulting sets less restrictive). Thus by continuity of probability,

$$\pr\left(\bigcup_{N \geq 1} \bigcap_{n > N} A_n\right) = \lim_{N\to\infty} \pr\left(\bigcap_{n > N} A_n\right)$$

Since $\cap\_{n > N} A\_n \subseteq A_{N+1}$ then $\pr(\cap\_{n>N} A\_n) \leq \pr(A\_{N+1})$. Therefore,

$$\liminf_{n\to\infty} \pr(\cap_{n>N} A_n) \leq \liminf_{N\to\infty} \pr(A\_{N+1})$$

Putting the above two equations together:

$$\pr\left(\bigcup_{N \geq 1} \bigcap_{n > N} A_n\right) \leq \liminf_{N\to\infty} \pr(A_{N+1})$$

which can be rewritten as:

$$\pr\left(\liminf_{n\to\infty} A_n\right) \leq \liminf_{n\to\infty} \pr(A_n)$$ 

This demonstrates the leftmost inequality and the second inequality follows from basic analysis. $\tag*{∎}$ 

**Exercise**: Prove the $\limsup$ relation, (right-most inequality)

# Borel-Cantelli Lemmas

Now that we have discussed the $\limsup$ and $\liminf$ procedures on events, we can now talk about how to measure these limiting events. Later on, we will see that limiting procedures in general, will always have probability 0 or 1 provided some technical details. For now, we focus on some conditions regarding the measure of these limiting procedures. The rules governing the probability of these limiting procedures are called the Borel-Cantelli lemmas. 

## First Borel-Cantelli Lemma:

> Let $A\_1,...,A\_n,...$ is a sequence of events indexed by $n$. 

$$\sum_{i=1}^\infty \pr(A_n) < \infty \implies \pr\left(\limsup_{n\to\infty} A_n\right) = 0$$

This tells use that if the sum of the probabilities over $n$ converges quick enough to 0, then $A_n$ happens infinitely often (w.r.t. n) almost never (almost never means with measure 0, or with probability 0).

_Proof_ : Let $A\_1,...,A\_n,...$ be a sequence of events such that the sum of the probability is convergent. Then,

$$\pr\left(\bigcap_{N \geq 1} \bigcup_{n\geq N} A_n\right) = \lim_{N\to\infty}\sum_{N=1}^\infty \pr\left(\bigcup_{n \geq N} A_n\right) \leq \lim_{N\to\infty} \sum_{n=N}^\infty \pr\left(A_N\right) = 0$$ 

The last equality is by the Cauchy criteria of tail sums of convergent sequences from analysis. Since $\pr(\limsup A\_n) \leq 0$ then it must be 0 by non-negativity of probability. $\tag*{∎}$ 

For the next lemma, we need to define **independence** of events. Two sets are independent if $\pr(A\_j \cap A\_k) = \pr(A\_j)\pr(A\_k)$. We will discuss more about independence later but this definition is sufficient to understand the second Borel-Cantelli lemma.

## Second Borel-Cantelli Lemma:

> Let $A\_1,...,A\_n,...$ is a sequence of jointly independent events indexed by $n$. 

$$\sum_{i=1}^\infty \pr(A_n) = \infty \implies \pr\left(\limsup_{n\to\infty} A_n\right) = 1$$

_Proof_ : Let $A\_1,...,A\_n,...$ be a sequence of independent events such that the sum of the probability is infinite. Then,

$$\pr\left(\bigcap_{N \geq 1} \bigcup_{n\geq N} A_n\right) = 1 - \pr\left(\bigcup_{N \geq 1} \bigcap_{n\geq N} A_n^C\right) = 1 - \lim_{N\to\infty} \pr\left(\bigcap_{n\geq N} A_n^C\right)$$

The above is by the continuity of probability. Then by independence,

$$1-\lim_{N\to\infty} \pr\left(\bigcap_{n\geq N} A_n^C\right) = 1-\lim_{N\to\infty} \prod_{n=N}^\infty \pr\left(A_n^C\right) = 1-\lim_{N\to\infty} \prod_{n=N}^\infty (1-\pr\left(A_n\right))$$

Using the relationship between $e^{-x} \geq 1 - x$, we have:

$$1-\lim_{N\to\infty} \prod_{n=N}^\infty (1-\pr\left(A_n\right)) \geq 1-\lim_{N\to\infty} e^{-\sum_{n=N}^\infty \pr\left(A_n\right)} \to 1$$

as $\sum \pr(A\_n) = \infty$. So $\pr(\limsup A\_n^C) \geq 1$ thus $\pr(\limsup A\_n) = 1$. $\tag*{∎}$ 

These Borel-Cantelli lemmas, abbreviated as BC lemma 1 (and 2) are critical in understanding convergence concepts in probability. BC lemma provides a relationship between the convergence rate of a sequence of measures $\pr(A\_n)$ and the limiting measure of the sequence. From a previous 