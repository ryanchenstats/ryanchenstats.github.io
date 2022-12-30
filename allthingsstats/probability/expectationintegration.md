---
layout: default
title: Expectation and Integration
parent: Probability Theory
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

# Integration

Thus far, we have defined a random variable as a function. We have also developed a mechanism to help understand how to evaluate probability measures of limiting events and its relationship to continuity. Another important property of a random variable is its expectation or moment, and we can examine higher order moments for random variables which will provide more information about the behavior of the random variable. Moments also help us control certain aspects of the random variable, which allows us to make generalizations of sequences of random variables ad infinitum. Expectation is expressed as an integration. For random variable $X$, we define the expectation as

$$\E(X) = \int_\Omega X(\omega) d\pr = \int_\Omega X(\omega) \pr(d\omega)$$

## Revisiting Induced Measure

Suppose we have a random variable $X(\omega) : (\Omega, \cv{F}, \pr) \to (\reals, \cv{B})$ defined on a probability space $(\Omega, \cv{F}, \pr)$. To say $\pr(X \in A)$ for some set $A \in \cv{B}$, we are really taking the probability measure of $\\{\omega : X(\omega) = A\\}$ events. This can be written as $\\{X^{-1}(A)\\}$ so $\pr(X \in A) = \pr(X^{-1}(A))$. Note that this is simply a composition of functions, $(X^{-1}\circ \pr)(A)$. $X^{-1} \circ \pr$ (we can write it as $\lambda$) is also a measure since we arrived at this measure from $\pr(X^{-1}(A))$. We call this an **induced measure** by $X$ and now the image of the random variable has an induced measure space $(\reals, \cv{B}, \lambda)$. So using an induced measure, we can rewrite the expectation defintion as:

$$\E(X) = \int_\Omega X(\omega) \pr(d\omega) = \int_\reals x \lambda(dx)$$

