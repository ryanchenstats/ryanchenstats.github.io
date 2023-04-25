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

For a given partition, denote $$\vert \cv{T}_n \vert$$ as the length of the largest partition. For a given $n$, let the partition be $0 < t_1 < ... < T$. Then the quadratic variation without the limit (via expanding squares) is:

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

So all that remains after taking limits, is $QV_I(T) = \int_0^T \Delta^2(u)du$. 

## Ito-Doeblin Theorem for Ito Processes

The Ito-Doeblin theorem for an Ito process is analogous to that in the Brownian motion only case. It states that:

$$
f(T, X(T)) = f(0, X(0)) + \int_0^T f_t(t,X(t))dt + \int_0^T f_x(t,X(t))dX(t) + \frac{1}{2}\int_0^T f_{xx}(t,X(t))dX(t)dX(t) 
$$

Note the final $dX(t)dX(t)$ is a product of the quadratic variation on $X(t)$ which is $\int_0^T \Delta^2(u)du$ as opposed to the quadratic variation on $W(t)$ which is $T$.

The proof is as follows, with Taylor expansion:

$$
\begin{align*}
f(T,X(T)) - f(0,X(0)) &= \sum_{j=0}^{n-1}f_t(t_j, X(t_j))(t_{j+1}-t_j) + \sum_{j=0}^{n-1}f_x(t_j, X(t_j))(X(t_{j+1})-X(t_j)) + \\
&\qquad \qquad \frac{1}{2}\sum_{j=0}^{n-1}f_{xx}(t_j, X(t_j))(X(t_{j+1})-X(t_j))^2 + \frac{1}{2}\sum_{j=0}^{n-1}f_{tt}(t_j, X(t_j))(t_{j+1}-t_j)^2 + \\
&\qquad \qquad \sum_{j=0}^{n-1}f_{tx}(t_j, X(t_j))(t_{j+1}-t_j)(X(t_{j+1})-X(t_j)) + R
\end{align*}
$$




