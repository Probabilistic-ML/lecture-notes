(sec:probessthm)=
# Essential Theorems

## Properties of the Normal Distribution

```{admonition} Lemma
:class: important
:name: lem:lintransnormaldistr
Let $X \sim \mathcal{N}(\mu_1, \Sigma_1)$ be a $\mathbb{R}^{d_1}$-valued random variable as well as $\mu_2 \in \mathbb{R}^{d_2}$ and $A \in \mathbb{R}^{d_2 \times d_1}$ be a matrix with full rank. Then,

$$\mu_2 + AX \sim \mathcal{N}(\mu_2 + A\mu_1, A\Sigma A^T)$$

In particular, $\mu_2 + AX \sim \mathcal{N}(\mu_2, AA^T)$ if $X$ is standard normally distributed.
```

As a consequence, each normally distributed random variable $X \sim \mathcal{N}(\mu, \Sigma)$ can be written as the linear transformation of a standard normally distributed random variable $Z$:

$$ X = \mu + A Z,$$

where $A$ is the matrix root of $\Sigma$, i.e., $\Sigma = AA^T$.

```{admonition} Lemma
:class: important
:name: lem:sumnormaldistr
Let $X_1 \sim \mathcal{N}(\mu_1, \Sigma_1)$ and $X_2 \sim \mathcal{N}(\mu_2, \Sigma_2)$ be $\mathbb{R}^{d}$-valued independent normal distributed random variables. Then, the sum $X_1 + X_2$ is also normally distributed with

$$X_1 + X_2 \sim \mathcal{N}(\mu_1 + \mu_2, \Sigma_1 + \Sigma_2).$$
```

## Law of Large Numbers

The law of large numbers has multiple (strong and weak) versions and is of particular importance in statistics, since it justifies for example the estimation of the expectation of random variables in terms of sample means. In this section, we state one version of the strong law of large numbers:

```{admonition} Theorem
:class: important
:name: thm:lln
Let $X_1, X_2, \dots$ be a sequence of independent identical distributed random variables with expectation $\mu$. Then, it exists an event $N$ of probability zero such that

$$ \lim_{n \rightarrow \infty} \frac{1}{n} ~\sum_{i=1}^n X_i(\omega) = \mu \quad \text{for all } \omega \in \Omega \backslash N$$

or equivalently

$$P\big(\lim_{n \rightarrow \infty} \frac{1}{n} ~\sum_{i=1}^n X_i = \mu \big) = 1,$$

i.e., the average converges almost surely to the expectation.
```

## Central Limit Theorem

The central limit theorem makes the normal distribution particularly important, since it can be considered as the limit of the average of "nice" i.i.d. random variables. Similarly to the law of large numbers, the theorem exists in several versions. In this section, we state the Lindeberg-L{\'e}vy central limit theorem: 

```{admonition} Theorem
:class: important
:name: thm:clt
Let $X_1, X_2, \dots$ be a sequence of independent identical distributed random variables with expectation $\mu$ and $0 < \sigma^2 < \infty$. Set 

$$Z_n := \frac{\frac{1}{n} ~\sum_{i=1}^n X_i - \mu}{\sigma/\sqrt{n}} = \frac{\sum_{i=1}^n X_i - n\mu}{\sigma \sqrt{n}}.$$

Then, it holds

$$\lim_{n \rightarrow \infty} P(Z_n \le z) = \Phi(z) \quad \text{for each } z \in \mathbb{R},$$

where $\Phi$ denotes the cumulative distribution function of the standard normal distribution.
```

Briefly speaking, the cumulative distribution function of standardized average $Z_n$ converges pointwisely to the cumulative distribution function of the standard normal distribution $\mathcal{N}(0, 1)$. By definition, this means that $Z_n$ **converges in distribution** to the standard normal distribution. The definition of $Z_n$ might seem confusing, but it simply scales the average $\frac{1}{n} ~\sum_{i=1}^n X_i$ such that its mean is $0$ and its variance is $1$ (in accordance with $\mathcal{N}(0, 1)$). 

This result is really notable, since it is independent from the underlying distribution of the random variables $X_i$, $i \in \mathbb{N}$, which could be totally different from a normal distribution and possibly be a discrete distribution.  

The arithmetic average fulfills

$$P\big(\frac{1}{n} ~\sum_{i=1}^n X_i \le z\big) = P\big(Z_n \le \frac{z - \mu}{\sigma/\sqrt{n}}\big) \approx \underbrace{\Phi\big(\frac{z - \mu}{\sigma/\sqrt{n}}\big)}_{\text{cdf of } \mathcal{N}(\mu, \frac{\sigma^2}{n})}.$$

Thus, the average can be approximated by $\mathcal{N}(\mu, \frac{\sigma^2}{n})$ for sufficiently large $n$. If the distribution of the variables $X_1, X_2, \dots$ is $\mathcal{N}(\mu, \sigma^2)$, it holds indeed that $\frac{1}{n} ~\sum_{i=1}^n X_i \sim \mathcal{N}(\mu, \frac{\sigma^2}{n})$.  

## Bayes' Theorem

From a mathematical standpoint, Bayes' theorem is a rather simple, since the statement is follows directly from the definition of conditional probabilities. Nevertheless, it has a very important interpretation which is the foundation of Bayesian inference.

```{admonition} Theorem
:class: important
:name: thm:bt
Let $(\Omega, \mathcal{F}, P)$ be a probability space and $A, B \in \mathcal{F}$ with $P(B) > 0$. Then

$$P(A~|~B) = \frac{P(B~|~A) P(A)}{P(B)}$$
```

Note that $P(B~|~A)$ is not well-defined if $P(A) = 0$, but in this case it holds $P(A~|~B) = 0$ and the righthand side can also be regarded as $0$, since $P(A) = 0$ and the (ill-defined) $P(B~|~A)$ should be between $0$ and $1$.
