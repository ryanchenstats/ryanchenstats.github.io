---
layout: default
title: Ito Process
parent: Stochastic Calculus
grand_parent: All Things Statistics
nav_order: 2
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

# Ito Process

The Ito-Doeblin theorem from the previous section was specifically for intergrating with respect to a Brownian motion $W(t)$. Now we extend this to a more general case, **Ito processes**.

An Ito process is defined as the following:

$$
X(T) = X(0) + \int_0^T \Delta(u)d W_u + \int_0^T \Theta(u) du
$$

and in differential form:

$$\partial X(t) = \Delta(t) \partial W(t) + \Theta(t)\partial t$$

Here, $W_u$ is a Brownian motion, and $\Delta(u)$ and $\Theta(u)$ are adapted processes. Also $\delta(u)^2$ is integrable and $\Theta(u)$ is absolutely integrable.

The Ito process is defined as a sum of an Ito integral and a Lebesgue intergal. We denote the Ito portion as $I(T) = \int_0^T \Delta(u)dW(u)$ and the Lebesgue portion as $L(T) = \int_0^T \Theta(u)du$. The quadratic variation of such an Ito process is $QV_X(T) = \int_0^T \Delta(u)^2 du$ as demonstrated below.

## Quadratic Variation for Ito Process

For a given partition, denote $$\vert \cv{T}_n \vert$$ as the length of the largest partition. For a given $n$, let the partition be $0 < t_1 < ... < T$. Then the quadratic variation without the limit is:

$$
\sum_{j=0}^{n-1}(X(t_{j+1}) - X(t_j))^2 = \sum_{j=0}^{n-1}(I(t_{j+1}) - I({t_j}))^2 + \sum_{j=0}^{n-1}(L(t_{j+1}) - L({t_j}))^2 + 2\sum_{j=0}^{n-1}(I(t_{j+1}) - I({t_j}))(L(t_{j+1}) - L({t_j}))
$$

We shall see that several terms go to 0 in the limit as required by the definition of QV, and the only term remaining will be $\int_0^T \Delta(t)^2dt$.

In the limit, the $\sum_{j=0}^{n-1}(I(t_{j+1}) - I({t_j}))^2$ term becomes $QV_{I}(T) = \int_0^T \Delta^2(u)du$.

We bound the second term by:
$$
\begin{align*}
    \sum_{j=0}^{n-1}(L(t_{j+1}) - L({t_j}))^2 &\leq \max_{(t_j, t_{j+1})\in\cv{T}_n}\{R(t_{j+1})-R({t_j})\}\sum_{j=0}^{n-1}\vert R(t_{j+1})-R({t_j})\vert \\
    &= \max_{(t_j, t_{j+1})\in\cv{T}_n}\{R(t_{j+1})-R({t_j})\}\left\lvert \int_0^T \Theta(u)du \right\rvert \\
    &\leq \max_{(t_j, t_{j+1})\in\cv{T}_n}\{R(t_{j+1})-R({t_j})\} \int_0^T \vert \Theta(u) \vert du \\
    &\to 0
\end{align*}
$$

We bound the third term with 

$$
\begin{align*}
2\sum_{j=0}^{n-1}(I(t_{j+1}) - I({t_j}))(L(t_{j+1}) - L({t_j})) &\leq 2\max_{(t_j, t_{j+1})\in\cv{T}_n}\{(I(t_{j+1}) - I({t_j}))\}\sum_{j=0}^{n-1}\vert L(t_{j+1}) - L({t_j})\vert \\
&= 2\max_{(t_j, t_{j+1})\in\cv{T}_n}\{(I(t_{j+1}) - I({t_j}))\}\left\lvert \int_0^T \Theta(u)du \right\rvert \\
&\leq 2\max_{(t_j, t_{j+1})\in\cv{T}_n}\{(I(t_{j+1}) - I({t_j}))\} \int_0^T \vert \Theta(u) \vert du \\
&\to 0
\end{align*}
$$

So all that remains in the limit is $QV_I(T) = \int_0^T \Delta^2(u)du$. 






