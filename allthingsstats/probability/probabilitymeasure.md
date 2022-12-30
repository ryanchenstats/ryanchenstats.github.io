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

_Proof_: The sets $A\_n$ are increasing so for any $A\_n \cap A\_{n+1} = A\_n$. Thus define $B\_{n} = A\_{n}\setminus A\_{n-1}$ where we let $A\_0 = \nul$. Here $B\_n$ becomes a sequence of disjoint sets with $\cup\_{n=1}^N B\_n = \cup\_{n=1}^N A\_n = A\_N$ for all $N$. Therefore,

$$\pr\left(\bigcup_{n \geq 1} A_n \right) = \pr\left(\cup_{n\geq 1} B_n \right) = \lim_{N\to\infty} \sum_{n=1}^N \pr(B_n) = \lim_{N\to\infty} \pr(A_N)$$ 

Note here we treat $\lim A\_n = \cup A\_n$ since $A\_n \subseteq A\_{n+1}$. 

The case for when $A\_n \supseteq A\_{n+1}$ works in the same way, and it is critical that we assume $\pr(\Omega) = 1$ to maintain that $\pr(\cdot)$ is a finite measure.

## Sub-Additivity

Sub-additivity refers to the idea that if $A\_1,...,A\_n,...$ is a countable sequence of events that need not be disjoint, then

$$\pr\left(\bigcup_{i\geq 1}A_i\right) \leq \sum_{i\geq1} \pr(A_i)$$

_Proof_: Let $B\_1 = A\_1$, and $B_n = A\_n\setminus \cup\_{k < n} A\_k$. Then the sequence of sets $B\_n$ are mutually disjoint. This gives:

$$\bigcup_{n\geq 1} A_n = \bigcup_{n\geq 1} B_n$$

and we know $\pr(\cup\_{n\geq 1} A_n) = \pr(\cup\_{n\geq 1} B_n) = \sum \pr(B\_n)$ by Kolmogorov's axioms. Now:

$$\pr(B_n) = \pr(A_n\setminus \cup_{k < n} A_k) \leq \pr(A_n)$$

So putting it all together $\pr(\cup\_{n\geq 1} A_n) = \pr(\cup\_{n\geq 1} B_n) = \sum \pr(B\_n) \leq \sum \pr(A\_n)$. Thus proves the sub-additivity of the probability measure. $\tag*{∎}$

**Exercise** (Finite additivity): Prove that the probability measure is finitely additive, i.e. for $(\Omega, \cv{F}, \pr)$, if $A\_1,...,A\_N \in \cv{F}$ disjoint then $\pr(\cup\_{i=1}^N A\_i) = \sum\_{i=1}^N \pr(A\_i)$
**Exercise**: Assume we did not assume countable additivity, but we assumed finite additivity and sub-additivity. Prove that countable additivity still holds.

