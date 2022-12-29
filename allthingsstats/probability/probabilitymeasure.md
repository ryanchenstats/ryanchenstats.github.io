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

$\newcommand{\reals}{\mathbb{R}}$ $\newcommand{\pr}{\mathbb{P}}$ $\newcommand{\cv}[1]{\mathcal{#1}}$

# Laws of Probability

There are three main axioms in probability determined by A. N. Kolmogorov and hence called Kolmogorov's axioms. Given a **probability measure space** $(\Omega, \cv{F}, \pr)$:

1. $\pr(\Omega) = 1$
2. $\pr(A) \geq 0$ for all $A \in \cv{F}$
3. For disjoint sequence $A\_1,...,A\_n,...\in\cv{F}$, $\pr(\cup A\_i) = \sum \pr(A_i)$ 

We can derive some critical results on continuity and sub-additivity of the probability measure function $\pr: \cv{F}\to [0,1]$ from these axioms.

## Sub-Additivity

Sub-additivity refers to the idea that if $A\_1,...,A\_n,...$ is a countable sequence of events that need not be disjoint, then

$$\pr\left(\bigcup_{i\geq 1}A_i\right) \leq \sum_{i\geq1} \pr(A_i)$$

_Proof_: Let $B\_1 = A\_1$, and $B_n = A\_n\setminus \cup\_{k < n} A\_\k$. Then the sequence of sets $B\_n$ are disjoint. This gives:

$$\bigcup_{n\geq 1} A_n = \bigcup_{n\geq 1} B_n$$

and we know $\pr(\cup\_{n\geq 1} A_n) = \pr(\cup\_{n\geq 1} B_n) = \sum \pr(B\_n)$ by Kolmogorov's axioms. Now:

$$\pr(B_n) = \pr(A_n\setminus \cup_{k < n} A_k) \leq \pr(A_n)$$

So putting it all together $\pr(\cup\_{n\geq 1} A_n) = \pr(\cup\_{n\geq 1} B_n) = \sum \pr(B\_n) \leq \sum \pr(A\_n)$. Thus proves the sub-additivity of the probability measure. $\tag*{∎}$

