---
title: 'Stochastic Convergence and Convergence Speed'
date: 2024-07-15T15:55:56-05:00
draft: false
tags: ["econometrics", "statistics"]
---

# Motivating Example

Consider a simpel example of estimating the population mean with sample average. 
Let $ \{X_i\}^n_{i=1} $ denote a collection of i.i.d. random variables with distribution $P_0$. 
The population mean is denoted as $\mu:=\mathrm{E}_{P_0}(X_i)$ and the population variance is $\sigma^2$. 
A natural estimator for it is the sample average: 
$$
\bar{X}_n = n^{-1}\sum_{i=1}^n X_i
$$

Now that we have an estimator for the parameter of interest, we want to know how good it is. 
Evaluating the quality of an estimator typically boils down to answering the following questions: 
(1) Is $\bar{X}$ consistent and unbiased? 
(2) What is the asymptotic distribution of $\bar{X}$? 
(3) How fast does $\bar{X}$ converge to its asymptotic distribution? 

# Different Types of Convergence

**Definition (Converge Almost Surely)** A sequence of random variables $X_n$ are said to converge almost surely if to $X$ if 
$$
\Pr(\lim_{n\rightarrow \infty} \|X_n - X\| = 0) = 1
$$
We denote such convergence as $X_n \xrightarrow{a.s.} X$. 

**Definition (Converge in Probability)** A sequence of random variables $X_n$ are said to converge in probability to $X$ if for alll $\epsilon > 0$:
$$
\lim_{n\rightarrow \infty}\Pr(|X_n - X| \geq \epsilon) =0
$$
We denote such convergence as $X_n \xrightarrow{P} X$. 

**Definition (Converge in Distribution)** A sequence of random variables $X_n$ is said to converge in distribution to a random variable $X$ if the CDFs $F_n$ satisfies
$$
\lim_{n\rightarrow \infty} F_n(x) = F(x),\;\forall x
$$
We denote such convergence as $X_n \rightsquigarrow X$ or $X_n \xrightarrow{d} X$. 

**Definition (Uniformly tight, or bounded in probability)** A set of random variables $\{X_n\}$ is called unifomly tight if for every $\epsilon > 0$, there exists a constant $M$ such that:
$$
\sup_{n} \Pr(\|X_n\| \geq M) \leq \epsilon
$$

## Relations between Different Convergence

**Theorem (Prohorov's Theorem)**
* If $X_n$ converges in distribution, then $X_n$ is bounded in probability
* If $X_n$ is bounded in probability, there there exists a subsequence of $X_n$ that converges in distribution. 

# $o_P$ and $O_P$ Notation

We denote a sequence of random variable $X_n$ converging in probability to zero as $X_n = o_P(1)$. 
Similarly, we denote a sequence of random variables $X_n$ bounded in probability as $X_n = O_P(1)$. 



# Convergence Speed
Convergence speed refers to how fast the uncertainty of an estimator shrinks with sample size. 
More specifically, consider an estimator $X_n = O_P(a_n)$. 
From definition, we have that for all $n$, 
$$
\begin{aligned}
& \Pr(\|a_n^{-1}X_n\| \geq M) \leq \epsilon\\
\iff & \Pr(- a_n M \leq X_n \leq a_n M) \geq 1 - \epsilon
\end{aligned}
$$
That is, the high-confidence region of $X_n$ is $[-a_n M, a_n M]$. 
The smaller the high-confidence region, the more precise $X_n$ is. 
Thus, $a_n$ essentially quantifies the range of the high-confidence region of a given estimator. 
The smaller $a_n$ is, the more precise the estimator $X_n$ is. 

Consider the following example. 
There are two estimators, $X_n = O_P(n^{-1/4})$ and $Y_n = O_P(n^{-1/2})$. 
When we have $1000$ observations, with confidence $1 - \epsilon$, we can state that the bias of $X_n$ is within $[-0.1778M, 0.1778M]$, and the one of $Y_n$ is $[-0.0316M, 0.0316M]$. 
Obviously, $Y_n$ is more precise. 
That is, $Y_n$ converges faster than $X_n$. 


# Convergence $\bar{X}$
For ease of demonstration, we assume without loss of generality that the population mean $\mu=0$. 

First, from the weak law of large numbers, we know that
$$
\bar{X}_n = o_P(1)
$$

From the central limit theorem, we know that 
$$
\sqrt{n} \sigma^{-1} \bar{X}_n \rightsquigarrow \mathcal{N}(0, 1)
$$
CLT tells us that $\bar{X}_n$ is uniformly tight and the convergence speed is:
$$
\bar{X}_n = O_p(n^{-1/2})
$$