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

Let $N(t)$ be a Poisson process. In order to make it a martingale, the monotonic increasing $N(t)$ should be demeaned. Of course at a given $N(t)$, $\E(N(t)) = \lambda t$ so one should expect $N(t)-\lambda t$ to be a martingale wrt the canonical filtration $$\cv{F}_t$$.







