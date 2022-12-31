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

## Example of where Riemann Breaks, and a Proposed Solution

At this point, integration ought to be defined. In the Riemann sense, integration is not entirely well defined as we see pitfalls when Riemann integrating some pathological functions. This is particularly troublesome because it means Riemann integration is not a general enough technique. For example, let $f(\omega) = \ind_{\omega \in \mathbb{Q}}$. where $\omega \in (0,1)$. It is easy to show the lower and upper Riemann sums do not agree, thus the Riemann integral is not defined. 

**Exercise**: Show that the function above is not Riemann integrable. (Hint: Riemann integration requires the lower and upper sum to agree, in order for it to exist.)

The integral of the non-Riemann integrable function given above is one formulation of asking the question "what is the probability of picking a rational number from all real numbers in the interval [0,1]?" Since the rational numbers are countable, the probability should be 0. Yet, breaking a function up into interval partitions and observing how its upper and lower sum converges in the Riemann sense will not provide an adequate answer (the function is not Riemann integrable). So the Riemann integral is sufficient for a subset of "nice" functions, but there are functions in which the Riemann integral is not adequate. Thus we need another approach to integration - one even more general to handle more than just the "nice" functions. As Riemann integration relied on forming peicewise functions that approximate the original function from above and below based on interval partions, we would need to estiblish another paradigm of approximating a function. Hopefully this new paradigm will help form a "better" definition of an integral.

### Simple Functions

We introduce the idea of a simple function. A simple function is a function that can be expressed as a finite linear combination of indicator functions on disjoint sets. That is:

$$f(\omega) := \sum_{i=1}^N a_i \ind_{A_i}(\omega)$$

where $a\_i$ is a sequence of constants and $A\_i$ is a sequence of disjoint sets indexed by $i$. While this may look like we are approximating the function in a Riemann sense where we take $\inf f(x) \Delta x$ or $\sup f(x) \Delta x$, however the difference is that $A\_i$ does not need to be an interval; it could be a union of seperate intervals. It could even be a single point. The sole requirement is that $A\_i$ must be measurable.  

### Lebesgue Integral

The Riemann integral attempts to partition the region of integration into infinitessimal intervals. The Lebesgue integral aims to look at the possible values of $f: \Omega \to \reals$ and then look at the subsets of $\Omega$ where $k\_{n-1} \leq f(\omega) \leq k\_n$ for some partition of the codomain $\\{k\_n\\}\_{n\geq 1}$. That is, the integral is defined as $\sum\_n k\_n \lambda(\\{\omega : k\_{n-1} \leq f(\omega) \leq k\_n\\})$ for all $k$ in the image of $f$. The integral of $f$ will be the weighted sum, as $\\{k\_n\\}$ becomes a finer partition. Some pictures will help make this more understandable.  

![The Integral](lebesgue-integral.svg)

The above image is the case when $n=3$, where we divide the codomain of the function $f$ into 3 equally spaced intervals $f = a\_1$, $f=a\_2$, and $f=a\_3$. Then we examine the measure of $\\{\omega : f(\omega) = a\_1 \\}$ and multiply it by $a\_1$ and we do the same for $a\_2$ and $a\_3$. Essentially, we are representing the function as a sequence of stepwise functions.




_Proof_ : Let $f$ be a function of interest. Then for each $n$, we define the following stepwise

$$f_n(x) = \begin{cases}\end{cases}$$



