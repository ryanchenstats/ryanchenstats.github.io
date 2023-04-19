---
layout: default
title: Markov Processes
parent: Stochastic Processes
grand_parent: All Things Statistics
nav_order: 3
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

$\newcommand{\reals}{\mathbb{R}}$ $\newcommand{\nats}{\mathbb{N}}$ $\newcommand{\ind}{\mathbb{1}}$  $\newcommand{\pr}{\mathbb{P}}$ $\newcommand{\cv}[1]{\mathcal{#1}}$ $\newcommand{\nul}{\varnothing}$ $\newcommand{\eps}{\varepsilon}$ $\newcommand{\E}{\mathbb{E}}$ 

# Introduction to Stochastic Processes

From probability theory, especially towards the law of large numbers and central limit theorems, the discussion began to revolve around properties of a sequence of random variables, and their convergence properties. Another instance in probability theory that dealt with a sequence of random variables is in the convergence theorems of integration on a sequence of random variables, i.e. MCT, DCT, and Fatou's lemma. The behavior of these sequences are also useful to study.

A **stochastic process** is a a collection of random variables indexed by some indexing $\cv{T}$ which can be countable or uncountable. The most basic form of a stochastic process is a **Markov Process** which is a sequence of random variables that exhibit the Markov property. 

## Markov Property

A sequence of random variables exhibit the Markov property when

$$\pr(X_{t+1} = x_{t+1} | X_{t} = x_t, \hdots, X_1 = x_1) = \pr(X_{t+1} = x_{t+1} | X_{t} = x_t) $$

In otherwords, the probability of the future only deends on the present, and does not depend on the past. Speaking in terms of conditional probability, we say that the past and future are conditionally independent, conditioned on the present. A few examples can immediately come to mind.

#### Example

Suppose $X_1, X_2,\hdots$ are a countable collection of random variables. Let $S_n = \sum_{i=1}^n X_n$. Then $S_n$ is a sequence of random variables indexed by $n$ and exhibits the Markov property. (Why?)

Using the same collection as previously defined, Suppose $P_n = \prod_{i=1}^n X_n$ and $X_n > 0$ for all $n$. $P_n$ is Markov. However, if $X_n \geq 0$, $P_n$ need not be Markov. (Why?)

Markov structure is useful in the sense that calculating probabilities is simplified. Given some initial condition $X_0 = x_0$, we are able to calculate the joint probability of $(X_0,\hdots,X_t)$ in a simple manner, provided that $X_t$ is a Markov process. This is shown through Bayes rule and induction. The base case is trivial: $\pr(X_{1}=x_1, X_0 = x_0) = \pr(X_{1}=x_1 | X_0 = x_0)\pr(X_0 = x_0)$. Now let the inductive hypothesis be: $\pr(X_t = x_t,\hdots,X_0=x_0) = \pr(X_{t}=x_t|X_{t-1}=x_{t-1})\cdots \pr(X_{1}=x_1 | X_0 = x_0)\pr(X_0 = x_0)$. Then:

$$\pr(X_{t+1}=x_{t+1},\hdots,X_0=x_0) = \pr(X_{t+1}=x_{t+1}|X_{t}=x_t,\hdots,X_0=x_0)\pr(X_{t}=x_t,\hdots,X_0=x_0)$$