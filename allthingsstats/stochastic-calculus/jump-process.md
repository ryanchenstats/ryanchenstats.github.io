---
layout: default
title: Jump Processes
parent: Stochastic Calculus
grand_parent: All Things Statistics
nav_order: 3
has_toc: false
has_children: true
usemathjax: true
---

# Ito Process
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

$\renewcommand{\reals}{\mathbb{R}}$ $\newcommand{\nats}{\mathbb{N}}$ $\newcommand{\ind}{\mathbb{1}}$  $\newcommand{\pr}{\mathbb{P}}$ $\newcommand{\cv}[1]{\mathcal{#1}}$ $\newcommand{\nul}{\varnothing}$ $\newcommand{\eps}{\varepsilon}$ $\newcommand{\E}{\mathbb{E}}$ $\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}$

# Jump Processes

Brownian motion only processes are called diffusion processes. Here we introduce *jump diffusion* processes which are paths that follow the Brownian motion diffusion process but also exhibit finitely many jumps in finite time intervals. There are processes that have infinitely many jumps in a finite time interval however there are some conditions on the size of the jumps. 

The most fundamental *pure* jump process is the Poisson process, which is flat almost everywhere, except for what the process makes a jump which is of size 1. Poisson processes are covered under the stochastic processes sections.

## Extensions of the Poisson process

Let $N(t)$ be a Poisson process. In order to make it a martingale, the monotonic increasing $N(t)$ should be demeaned. Of course at a given $N(t)$, $\E(N(t)) = \lambda t$ so one should expect $N(t)-\lambda t$ to be a martingale wrt the canonical filtration. This is the **compensated Poisson process** which looks like 

![Compensated Poisson](compensated_poisson.png)

The reader should check that this is indeed a martingale.

Another form of a Poisson process is a **compound Poisson process**. It is a process in which the jumps are of random height, defined by the following.

$$
Q(t) = \sum_{i=1}^{N(t)}Y_i
$$

Here $N(t)$ is a Poisson process and $Y_i$'s are iid random variables with mean $\beta$ independent of $N(t)$. $Y_i$ is not restricted to positive values, so jumps can be negative. Its expectation is:

$$
\E(Q(t)) = \E\left(\E\left(\sum_{i=1}^{N(t)} Y_i \vert N(t)\right)\right) = \E(N(t)\E(Y_i|N(t))) = \E(N(t)\E(Y_i)) = \E(N(t))\E(Y_i) = \lambda \beta t 
$$

Therefore, $Q(t) - \beta\lambda t$ should be expected to be a martingale. (Reader should check that this is true).

The compound Poisson process $Q(t)$ has independent increments, and stationary increments like the regular Poisson process, as the reader should check.

### Decomposition of the Compound Poisson Process

Suppose we have $y_1,..,y_m$ non-zero numbers such that $\sum_{i=1}^m p(y_i) = 1$. Suppose we also have the Poisson processes $N_1(t),...,N_m(t)$ each with mean $\lambda p(y_i)$. We define the following:

$$
Q(t) = \sum_{i=1}^M y_i N_i(t)
$$

Here $Q(t)$ is a compound Poisson process. To see this:

1. Note that the superposition of $N_1,...,N_m$ poisson processes yield another Poisson process with rate $\lambda$.
2. $Q(t)$ in the above, can be written as a sum $\sum_{i=1}^{N(t)} y_i$

And as a corrolary, for a given compound Poisson process $Q(t) = \sum_{i=1}^{N(t)} Y_i$, and jumps of size $y_k$ for $k=1,...,m$, we can let $N_k(t)$ be the number of jumps of size $y_k$. Then we can rewrite $Q(t)$ as:

$$
Q(t) = \sum_{i=1}^m y_i N_i(t)
$$

which uses Poisson thinning to reduce $N(t) = \sum_{i=1}^m N_i(t)$.

# Jump Processes



