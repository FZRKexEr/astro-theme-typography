---
title: "Random Processes"
pubDate: 2024-12-02
categories: ["概率"]
description: "一些随机过程"
---

# Random Processes

Random Processes:

1. Geometric random variable
2. Exponential random variable
3. Stochastic process
4. Poisson process
5. Discrete time Markov chain
6. Chapman-Kolmogorov equation(for DTMC)
7. Continuous time Markov chain
8. Chapman-Kolmogorov equation(for CTMC)
9. Kolmogorov differential equation
10. Birth-death process

## 1. Geometric random variable

$$
\begin{equation*}
P(X=k)=(1-p)^{k-1} p, \quad k=1,2,3, \cdots \tag{1}
\end{equation*}
$$

Mean of $X=E(X)=\frac{1}{p}$

Memoryless Property (or Markovian property)

$$
\begin{equation*}
P(X=m+n \mid X>m)=P(X=n), \quad m, n \geq 1 \tag{2}
\end{equation*}
$$

## 2. Exponential Random Variable

The cumulative distribution function (cds)

$$
F_{X}(x)=P(X \leq x)= \begin{cases}1-e^{-\lambda x}, & 0 \leq x<\infty  \tag{3}\\ 0, & x<0\end{cases}
$$

$$
P(X>x)=1-P(X \leq x)=e^{-\lambda x}, \quad x \geq 0 .
$$

The probability density function (pdf)

$$
f_{X}(x)= \begin{cases}\lambda e^{-\lambda x}, & x>0  \tag{4}\\ 0, & x \leq 0\end{cases}
$$

Mean of $X=E(X)=\frac{1}{\lambda}$

## 3. Stochastic Processes

A stochastic process is a collection of random variables $\{X(t): t \in T\}$. Note that $X(t)$ is a r.v. for each $t \in T$.
$T$ is called the index set of the process, a $t \in T$ is called an index. Very often, the index $t$ is interpreted as time.

If $T$ is a countable set, then the stochastic process is called a discrete time process.

If $T$ is an interval of $\mathbb{R}$, then the stochastic process is called a continuous time process.

The set of all values that $X(t)$ may assume is called the state space, denoted by $S$.
$S$ can be a discrete state space (countable). In this case, the stochastic process is called a chain. Eg, a machine has only 2 states, working or failed.
$S$ can be a continuous state space. Eg, $X(t)$ represents the distance covered by a robot arm in time $t$.

There are 4 different types of stochastic processes:

1. discrete time, discrete state space processes (discrete time chain)
2. discrete time, continuous state space processes
3. continuous time, discrete state space processes (continuous time chain)
4. continuous time, continuous state space processes

## 4. Poisson Process

Poisson random variable

$$
\begin{equation*}
P(X(t)=k)=\frac{e^{-\lambda t}(\lambda t)^{k}}{k!}, \quad k=0,1,2, \cdots \tag{5}
\end{equation*}
$$

A collection of Poisson random variables $\{X(t)$ : $t \geq 0\}$ is a Poisson process. $\lambda$ is a parameter and is called the rate of the Poisson process.

Superposition of Poisson Processes

$\lambda = \Sigma_{i=1}^{n} \lambda_{i}$

![](https://cdn.mathpix.com/cropped/2024_10_25_9ccb2666f78a919041a9g-18.jpg?height=1017&width=1603&top_left_y=1165&top_left_x=218)

Decomposition of a Poisson Process

![](https://cdn.mathpix.com/cropped/2024_10_25_9ccb2666f78a919041a9g-19.jpg?height=852&width=1337&top_left_y=1387&top_left_x=248)

## 5. Discrete Time Markov Chain (DTMC)

Markov property

$P\left(X_{n}=j \mid X_{n-1}=i, X_{n-2}=i_{2}, X_{n-3}=i_{3}, \cdots, X_{0}=i_{n}\right)$

$$
\begin{equation*}
=P\left(X_{n}=j \mid X_{n-1}=i\right) \tag{6}
\end{equation*}
$$

One-Step Transition Probability

$$
\begin{equation*}
p_{i j} \equiv p_{i j}(1)=P\left(X_{n}=j \mid X_{n-1}=i\right), \quad n \geq 1 \tag{7}
\end{equation*}
$$

Transition Probability Matrix (TPM)

$$
\begin{align*}
P=\left[p_{i j}\right] & =\left[\begin{array}{cccc}
p_{00} & p_{01} & p_{02} & \cdots \\
p_{10} & p_{11} & p_{12} & \cdots \\
p_{20} & p_{21} & p_{22} & \cdots \\
\cdot & \cdot & \cdot & \cdots
\end{array}\right]  \tag{8}\\
0 \leq p_{i j} \leq 1, & i, j \in N \\
\sum_{j} p_{i j} & =1, \quad i \in N \tag{9}
\end{align*}
$$

Sojourn Time

Given a state $i$ of a DTMC $\left\{X_{n} \in S: n \in N\right\}$, the sojourn time $T_{i}$ of the state $i$ is the discrete r.v. that gives the no. of time steps for which the DTMC resides in state $i$ before transiting to a different state.

$$
\begin{aligned}
& P\left(T_{i}>n\right) \\
& =P\left(X_{n}=i \mid X_{n-1}=i\right) P\left(X_{n-1}=i \mid X_{n-2}=i\right) \cdots \\
& \quad \cdots P\left(X_{2}=i \mid X_{1}=i\right) P\left(X_{1}=i \mid X_{0}=i\right)
=p_{i i}^{n} 
\end{aligned}
$$

$$
\begin{aligned}
P\left(T_{i}=n\right) & =\sum_{k=n}^{\infty} P\left(T_{i}=k\right)-\sum_{k=n+1}^{\infty} P\left(T_{i}=k\right) \\
& =P\left(T_{i}>n-1\right)-P\left(T_{i}>n\right) \\
& =p_{i i}^{n-1}-p_{i i}^{n}=p_{i i}^{n-1}\left(1-p_{i i}\right) .
\end{aligned}
$$

Thus, $T_{i}$ is a geometric r.v. with success probability $\left(1-p_{i i}\right)$.

$E\left(T_{i}\right)=\frac{1}{1-p_{i i}}$

## 6. Chapman-Kolmogorov Equation (C-K eqn)

$$
p_{i j}(m+n)=\sum_{k \in S} p_{i k}(m) p_{k j}(n)
$$

$$
\Longrightarrow P(m+n)=P(m) P(n) .
$$

Let $P(n)=\left[p_{i j}(n)\right]$ be the matrix of $n$-step transition probabilities. Note that $P(0)=I$.

$$
\begin{equation*}
P(n)=P(n-1) \cdot P, \quad n \geq 1
\end{equation*}
$$

State Probabilities

$$
\begin{equation*}
p_{j}(n)=P\left(X_{n}=j\right), \quad n=0,1,2, \cdots, j=0,1,2, \cdots 
\end{equation*}
$$

$$
\begin{align*}
p_{j}(n) & =P\left(X_{n}=j\right) \\
& =\sum_{i \in S} P\left(X_{n}=j, \quad X_{0}=i\right) \\
& =\sum_{i \in S} P\left(X_{n}=j \mid X_{0}=i\right) P\left(X_{0}=i\right) \\
& =\sum_{i \in S} p_{i}(0) p_{i j}(n), \quad j=0,1,2, \cdots 
\end{align*}
$$

$$
\pi(n)=\left[\begin{array}{llll}
p_{0}(n) & p_{1}(n) & p_{2}(n) & \cdots 
\end{array}\right]
$$

$$
\begin{equation*}
\pi(n)=\pi(0) P(n)=\pi(0) P^{n}, \quad n=0,1,2, \cdots
\end{equation*}
$$

## 7. Continuous Time Markov Chain (CTMC)

Sojourn Times in States

$T_{i}$ is an exponential r.v., i.e., $T_{i}=\operatorname{EXP}\left(\lambda_{i}\right)$,

$$
P\left(T_{i}>x\right)=e^{-\lambda_{i} x}, \quad x \geq 0
$$

If $\lambda_{i}=0$, the state $i$ is an absorbing state.

If $\lambda_{i}=\infty$, the state $i$ is an instantaneous state.
If $\lambda_{i} \in(0, \infty)$, the state $i$ is a stable state.

## 8. Chapman-Kolmogorov Equation (C-K eqn)

$$
H(s, t)=\left[p_{i j}(s, t)\right]
$$

$$
\begin{equation*}
H(s, t)=H(s, u) H(u, t), \quad 0 \leq s \leq u \leq t 
\end{equation*}
$$

## 9. Kolmogorov Differential Equation

$$
\begin{equation*}
\frac{\partial H(s, t)}{\partial t}=H(s, t) Q(t), \quad 0 \leq s \leq t 
\end{equation*}
$$

$$
\begin{equation*}
\frac{\partial H(s, t)}{\partial s}=-Q(s) H(s, t), \quad 0 \leq s \leq t
\end{equation*}
$$

$$
\begin{equation*}
q_{i i}(t)=\lim _{h \rightarrow 0} \frac{p_{i i}(t, t+h)-1}{h}
\end{equation*}
$$

$$
\begin{equation*}
q_{i j}(t)=\lim _{h \rightarrow 0} \frac{p_{i j}(t, t+h)}{h}, \quad i \neq j .
\end{equation*}
$$

$$
\begin{equation*}
\sum_{j} q_{i j}(t)=0, \quad \text { for all } i
\end{equation*}
$$

