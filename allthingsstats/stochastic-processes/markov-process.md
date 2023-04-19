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

Stochastic processes are usually defined on a state space $S$. That is, $X_t \in S$ for all $t$. In a coin flipping game, the state space is $\{H,T\}$, and this can be thought of as the same as the outcome space $\Omega$ in probability. For now, we consider finite state spaces.

## Markov Property

A sequence of random variables exhibit the Markov property when

$$\pr(X_{t+1} = x_{t+1} | X_{t} = x_t, ..., X_1 = x_1) = \pr(X_{t+1} = x_{t+1} | X_{t} = x_t) $$

In otherwords, the probability of the future only deends on the present, and does not depend on the past. Speaking in terms of conditional probability, we say that the past and future are conditionally independent, conditioned on the present. A few examples can immediately come to mind.

#### Example

Suppose $X_1, X_2,...$ are a countable collection of random variables. Let $S_n = \sum_{i=1}^n X_n$. Then $S_n$ is a sequence of random variables indexed by $n$ and exhibits the Markov property. (Why?)

Using the same collection as previously defined, Suppose $P_n = \prod_{i=1}^n X_n$ and $X_n > 0$ for all $n$. $P_n$ is Markov. However, if $X_n \geq 0$, $P_n$ need not be Markov. (Why?)

Markov structure is useful in the sense that calculating probabilities is simplified. Given some initial condition $X_0 = x_0$, we are able to calculate the joint probability of $(X_0,...,X_t)$ in a simple manner, provided that $X_t$ is a Markov process. This is shown through Bayes rule and induction. The base case is trivial: $\pr(X_{1}=x_1, X_0 = x_0) = \pr(X_{1}=x_1 \vert X_0 = x_0)\pr(X_0 = x_0)$. Now let the inductive hypothesis be: $\pr(X_t = x_t,...,X_0=x_0) = \pr(X_{t}=x_t\vert X_{t-1}=x_{t-1})\cdots \pr(X_{1}=x_1 \vert X_0 = x_0)\pr(X_0 = x_0)$. Then:

$$\pr(X_{t+1}=x_{t+1},...,X_0=x_0) = \pr(X_{t+1}=x_{t+1}\vert X_{t}=x_t,...,X_0=x_0)\pr(X_{t}=x_t,...,X_0=x_0)$$

By the inductive hypothesis, replace $\pr(X_{t}=x_t,...,X_0=x_0)$ with $\pr(X_{t}=x_t\vert X_{t-1}=x_{t-1})\cdots \pr(X_{1}=x_1 \vert X_0 = x_0)\pr(X_0 = x_0)$ and by the Markov property, replace $\pr(X_{t+1}=x_{t+1}\vert X_{t}=x_t,...,X_0=x_0) = \pr(X_{t+1}=x_{t+1}\vert X_{t} = x_t)$. 

Therefore:

$$\pr(X_{t+1}=x_{t+1},...,X_0=x_0) = \pr(X_{t+1}=x_{t+1}\vert X_{t}=x_t)... \pr(X_{1} = x_1\vert X_0=x_0)\pr(X_0=x_0)$$

Thus when $t=0$, and at $t=k$, the probability of a particular path denoted as $(X_0=x_0,...,X_k = x_k)$, has probability $\pr(X_0 = x_0)\prod_{i=1}^k \pr(X_{i}=x_i \vert X_{i-1}=x_{i-1})$.

Furthermore, suppose we are interested in $\pr(X_t = x_t \vert X_0 = x_0)$. This is the probability that the chain hits state $x_t$ at time $t$ given that the chain started at $X_0 = x_0$. This is simply the probability of all sample paths starting at $x_0$ and hitting $x_t$ at time $t$. For simplicity, consider $\pr(X_2=x_2 \vert X_0 = x_0)$. Provided $X_0 = x_0$, the probability that $X_2 = x_2$ is the probability of all sample paths between $t=0$ and $t=2$ that start with $x_0$ and ends in $x_2$. This is:
$$\pr(X_2= x_2\vert X_0=x_0)=\sum_{k\in S} \pr(X_2=x_2|X_1=k)\pr(X_1 = k |X_0=x_0)$$


### Transition Probabilities 

Thus we have seen that any joint probability on a Markov process can be reduced into one step probabilities. We have also seen that the probability of sample paths can be calculated by considering one step probabilities. These one step probabilities are called transition probabilities. For ease of notation, we denote $p_{ij,t}$ as the probability of arriving at time state $j$ given we started at state $i$ - as evaluated at time $t$. Often times, the Markov process does not depend on $t$, meaning that $p_{ij}$ is constant over time. This is called a **time homogeneous** markov chain, which we restrict our attention to. 

We can specify the transition probabilities going from any two states in $S$. Thus we have $\vert S \vert^2$ probabilities to specify. We can furthermore arrange them into a matrix, called the **transition matrix** $P$. 

$$P = \begin{bmatrix} p_{0,0} & p_{0,1} & ... & p_{0,S} \\
p_{1,0} & p_{1,1} & ... & p_{1,S}  \\
\vdots & \vdots & \ddots & \vdots \\
p_{S, 0} & p_{S,1} & \vdots & p_{S,S}
\end{bmatrix}$$

The transition matrix $P$ fully categorizes the time-homogeneous Markov chain, when given $X_0$, the initial value of the Markov chain. We can evaluate the joint probabilities given the probabilities entirely contained in the matrix $P$.  

In the transition matrix, each row sums to 1. For example, take row $i$ and sum over the columns:
$$\sum_{j\in S} p_{i,j} = \sum_{j\in S} \pr(X_t=j|X_{t-1}=i) = 1$$

Note that the columns need not sum to 1. 

We can express the two-step probability from above with these transition probabilities:
$$\pr(X_2= x_2\vert X_0=x_0) = \sum_{k\in S} \pr(X_2=x_2|X_1=k)\pr(X_1 = k |X_0=x_0) = \sum_{k\in S} p_{x_0,k}p_{k,x_2}$$

We can further extend this to $k$ step probabilities, i.e. $\pr(X_{k}=x_{k}\vert X_0 = x_0)$. 

$$\pr(X_k= x_k\vert X_0=x_0) = \sum_{i\in S} \sum_{j \in S} ... \sum_{l\in S} p_{x_0,k}p_{k,i} p_{i,\cdot} ... p_{\cdot, l} p_{l,x_2}$$

While this equation looks extremely complicated, it reduces down to a matter of multiplying the matrix $P$. That is, we can consider the exponentiation, $P^k$ and look at row $x_0$ and column $x_k$ so $P_{x_0, x_k}^k$ gives $\pr(X_k= x_k\vert X_0=x_0)$. Thus $\pr(X_k = x_k\vert X_0 = x_0) = P_{x_0, x_k}^k$. Therefore, by associativity of matrix multiplication, if $k=m+n$:

$$P^{k} = P^{n+m} = P^{n}P^{m};\;\; P^{k}_{x_0, x_k} = \sum_{i\in S} P^n_{x_0, i} P^m_{i,x_k}$$
That is, when considering a $k$-step path from $x_0$ to $x_k$, we take the $n$-step transition probabilities from $x_0$ to all states, then take the $m$-step probability from all states to $x_k$. This is known as the **Chapman-Kolmogorov equation**.

**Exercise**: Consider the following transition probabilities on state space $\{1,2,3,4\}$:
$$P = \begin{bmatrix} 1/2 & 1/2 & 0 & 0 \\
1/3 & 1/2 & 1/12 & 1/12 \\
0 & 0 & 1/3 & 2/3 \\
0 & 0 & 2/3 & 1/3
\end{bmatrix}$$
What is the probability $\pr(X_2=1 | X_0 = 1)$? What is the probability that $\pr(X_5 = 3| X_0 = 2)$?

