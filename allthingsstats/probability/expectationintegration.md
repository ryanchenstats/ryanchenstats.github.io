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

Recall the discussion on induced measures from the measure theory and $\sigma$-algebra discussion. We can rewrite the integral by changing the variable of integration justified through induced measures by the random variable. $X : (\Omega, \cv{F}, \pr) \to (\reals, \cv{B})$ where $\lambda$ is the induced measure on $(\reals, \cv{B})$:

$$\E(X) = \int_\Omega X(\omega) \pr(d\omega) = \int_\reals x \lambda(dx)$$

## Defining Integration

At this point, integration ought to be defined. In the Riemann sense, integration is not entirely well defined. We see pitfalls of Riemann integration when integrating some pathological functions. This is particularly troublesome because it means Riemann integration is not a general enough technique. For example, let $f(\omega) = \ind_{\omega \in \mathbb{Q}}$. where $\omega \in (0,1)$. It is easy to show the lower and upper Riemann sums do not agree, thus the Riemann integral is not defined. 

**Exercise**: Show that Riemann integration is not defined for the function above.




