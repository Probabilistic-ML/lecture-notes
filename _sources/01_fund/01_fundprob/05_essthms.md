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

In many cases, the distribution of a sum of random variables is not known explicitly. Luckily, independent normally distributed random variables behave nicely in this regard:

```{admonition} Lemma
:class: important
:name: lem:sumnormaldistr
Let $X_1 \sim \mathcal{N}(\mu_1, \Sigma_1)$ and $X_2 \sim \mathcal{N}(\mu_2, \Sigma_2)$ be $\mathbb{R}^{d}$-valued independent normal distributed random variables. Then, the sum $X_1 + X_2$ is also normally distributed with

$$X_1 + X_2 \sim \mathcal{N}(\mu_1 + \mu_2, \Sigma_1 + \Sigma_2).$$
```

If $X \sim \mathcal{N}(\mu, \Sigma)$ is a multivariate normally distributed random vector, the marginal distribution of some subvector is again a normal distribution and can simply be obtained by restriction of the mean and covariance to the relevant components. For example, for a $3$-dimensional random vector

$$ X = \begin{pmatrix} X_1 \\
X_2 \\
X_3 \end{pmatrix}$$

with

$$ \mu = \begin{pmatrix} \mu_1 \\
\mu_2 \\
\mu_3 \end{pmatrix} \quad \text{ and } \quad
\Sigma = \begin{pmatrix} \Sigma_{11} & \Sigma_{12} & \Sigma_{13} \\
\Sigma_{21} & \Sigma_{22} & \Sigma_{23} \\
\Sigma_{31} & \Sigma_{32} & \Sigma_{33} \end{pmatrix}$$

the subvector

$$X^{\prime} = \begin{pmatrix} X_1 \\
X_3 \end{pmatrix}$$

is again normally distributed with mean and covariance given by

$$ \mu = \begin{pmatrix} \mu_1 \\
\mu_3 \end{pmatrix} \quad \text{ and } \quad
\Sigma = \begin{pmatrix} \Sigma_{11} & \Sigma_{13} \\
\Sigma_{31} & \Sigma_{33} \end{pmatrix}$$

Due to the definition of the pdf of a multivariate normal distribtion and the properties of the exponential function, we get the following lemma. We restrict to the bivariate case, but in view of the preceding considerations the according result holds also true for pairwise independence of general multivariate normal distributions.

```{admonition} Lemma
:class: important
:name: lem:uncorrindep
Let $X = (X_1, X_2) \sim \mathcal{N}(\mu, \Sigma)$ be a random vector such that $X_1$ and $X_2$ are uncorrelated (i.e., $\Sigma$ is a diagonal matrix). Then, $X_1$ and $X_2$ are independent random variables. 
```

In {ref}```sec:indep``` we mentioned that uncorrelated random variables are not necessarily independent, but the preceding lemma shows that this is different for normally distributed random variables provided that **the joint distribution is also Gaussian**. If $X_1$ and $X_2$ are normally distributed, but $X$ is not, the statement does not hold true!

In view of the subsequent applications to Gaussian process regression, the following result will be very useful:

```{admonition} Lemma
:class: important
:name: lem:condnormaldistr
Let $X \sim \mathcal{N}(\mu, \Sigma)$ be $d$-dimensional and consider a partition of $X$ into two subvectors

$$X = \begin{pmatrix} X_1 \\
X_2 \end{pmatrix}$$
where $X_1$ is $d_1$-valued and $X_2$ is $d_2$-valued such that $d_1 + d_2 = d$. Accordingly, the mean and covariance are partitioned as follows

$$ \mu = \begin{pmatrix} \mu_1 \\
\mu_2 \end{pmatrix} \quad \text{ with  } \mu_1 \in \mathbb{R}^{d_1},~\mu_2 \in \mathbb{R}^{d_2}$$

and 

$$\Sigma = \begin{pmatrix} \Sigma_{11} & \Sigma_{12} \\
\Sigma_{21} & \Sigma_{22} \end{pmatrix} \quad \text{ with  } \Sigma_{11} \in \mathbb{R}^{d_1 \times d_1},~\Sigma_{12} \in \mathbb{R}^{d_1 \times d_2},~\Sigma_{21} \in \mathbb{R}^{d_2 \times d_1}, ~\Sigma_{22} \in \mathbb{R}^{d_2 \times d_2}.$$

Then, the {ref}```conditional distribution density<def:conddistr>``` of $X_1$ given $X_2=x_2$ is the density of a normal distribution with mean and covariance given by

$$\overline{\mu} = \mu_1 + \Sigma_{12} \Sigma_{22}^{-1}\big(x_2 - \mu_2\big)$$

and 

$$\overline{\Sigma} = \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21}.$$
```

For the interested reader, we show the result for the bivariate case $d=2$ and $d_1=d_2=1$.

```{admonition} Proof.
:class: dropdown
Let the mean value be given by

$$\mu = \begin{pmatrix} \mu_1 \\
\mu_2 \end{pmatrix} \quad \text{ with  } \mu_1, \mu_2 \in \mathbb{R}$$

and 

$$\Sigma = \begin{pmatrix} \sigma_{1}^2 & \sigma_{12} \\
\sigma_{12} & \sigma_{2}^2 \end{pmatrix}$$

where $\sigma_1^2$ is the variance of $X_1$, $\sigma_2^2$ is the variance of $X_2$ and $\sigma_{12}$ is the covariance of $X_1$ and $X_2$. 

Note that $\sigma_{12} = \rho \sigma_1 \sigma_2$, where $\rho$ is the correlation of $X_1$ and $X_2$ (refer to the section {ref}```sec:rv```). Hence, the aim is to show that the conditional distribution is normally distributed with mean

$$\overline{\mu} = \mu_1 + \frac{\sigma_{12}}{\sigma_2^2}\big(x_2 - \mu_2\big) =  \mu_1 + \rho \frac{\sigma_1}{\sigma_2}\big(x_2 - \mu_2\big)$$

and variance

$$\overline{\sigma}^2 = \sigma_1^2 - \frac{\sigma_{12}^2}{\sigma_2^2} = (1 - \rho^2) \sigma_1^2.$$

According to the {ref}```definition<def:conddistr>```, the conditional distribution of $X_1$ given $X_2 = x_2$ is given by

$$f_{X_1~|~X_2=x_2}(x_1) := \frac{f_{X}(x_1, x_2)}{f_{X_2}(x_2)}.$$

Note that $X_2 \sim \mathcal{N}(\mu_2, \sigma_2^2)$ and thus, 

$$f_{X_2}(x_2) = \frac{1}{\sqrt{2\pi \sigma_2^2}} ~\exp\big(-\frac{1}{2}~\frac{(x_2- \mu_2)^2}{\sigma_2^2}\big).$$

Moreover, it holds by assumption

$$f_{X}(x) = \frac{1}{\sqrt{(2\pi)^2 |\Sigma|}} ~\exp\Big(-\frac{1}{2}~(x - \mu)^T \Sigma^{-1}(x -\mu)\Big)$$

With $|\Sigma| = \sigma_1^2 \sigma_2^2 - \sigma_{12}^2 = (1 - \rho^2) \sigma_1^2 \sigma_2^2$ and 

$$\Sigma^{-1} = \frac{1}{|\Sigma|}~\begin{pmatrix} \sigma_{2}^2 & -\sigma_{12} \\
-\sigma_{12} & \sigma_{1}^2 \end{pmatrix}$$

it follows that 

$$Q(x_1, x_2) &:= (x - \mu)^T \Sigma^{-1}(x -\mu) \\
              &= \frac{1}{\sigma_1^2 \sigma_2^2 - \sigma_{12}^2}~\big((x_1 - \mu_1)^2 \sigma_2^2 - 2(x_1 - \mu_1)(x_2 - \mu_2)\sigma_{12} + (x_2 - \mu_2)^2\sigma_1^2 \big) \\
&= \frac{1}{(1 - \rho^2) \sigma_1^2 \sigma_2^2}~\big((x_1 - \mu_1)^2 \sigma_2^2 - 2(x_1 - \mu_1)(x_2 - \mu_2) \rho \sigma_1 \sigma_2 + (x_2 - \mu_2)^2\sigma_1^2 \big) \\
&= \frac{1}{1 - \rho^2}~\Big(\Big(\frac{x_1 - \mu_1}{\sigma_1}\Big)^2 - 2 \rho \Big(\frac{x_1 - \mu_1}{\sigma_1}\Big)\Big(\frac{x_2 - \mu_2}{\sigma_2}\Big) + \Big(\frac{x_2 - \mu_2}{\sigma_2}\Big)^2 \Big)$$

Consequently, it holds

$$f_{X_1~|~X_2=x_2}(x_1) &= \frac{f_{X}(x_1, x_2)}{f_{X_2}(x_2)} \\
&= \frac{\sqrt{2\pi \sigma_2^2}}{\sqrt{(2\pi)^2 (1 - \rho^2) \sigma_1^2 \sigma_2^2}}~\exp\Big(-\frac{1}{2} Q(x_1, x_2)\Big)~\exp\Big(\frac{1}{2}~\Big(\frac{x_2- \mu_2}{\sigma_2}\Big)^2\Big) \\
&= \frac{1}{\sqrt{2\pi (1 - \rho^2) \sigma_1^2}}~\exp\Big(-\frac{1}{2} \Big(Q(x_1, x_2) - \Big(\frac{x_2- \mu_2}{\sigma_2}\Big)^2 \Big)\Big) \\
&= \frac{1}{\sqrt{2\pi (1 - \rho^2) \sigma_1^2}}~\exp\Big(-\frac{1}{2} \frac{\Big(\frac{x_1 - \mu_1}{\sigma_1}\Big)^2 - 2 \rho \Big(\frac{x_1 - \mu_1}{\sigma_1}\Big)\Big(\frac{x_2 - \mu_2}{\sigma_2}\Big) + \rho^2 \Big(\frac{x_2 - \mu_2}{\sigma_2}\Big)^2}{1 - \rho^2} \Big) \\
&= \frac{1}{\sqrt{2\pi (1 - \rho^2) \sigma_1^2}}~\exp\Big(-\frac{1}{2} \frac{\Big(\frac{x_1 - \mu_1}{\sigma_1} - \rho \frac{x_2 - \mu_2}{\sigma_2} \Big)^2}{1 - \rho^2} \Big) \\
&= \frac{1}{\sqrt{2\pi (1 - \rho^2) \sigma_1^2}}~\exp\Big(-\frac{1}{2} \frac{\Big( x_1 - \big(\mu_1 + \rho \frac{\sigma_1}{\sigma_2} \big(x_2 - \mu_2 \big) \big) \Big)^2}{(1 - \rho^2) \sigma_1^2} \Big), $$

i.e. the conditional distribution is a normal distribution with mean $\mu_1 + \rho \frac{\sigma_1}{\sigma_2} \big(x_2 - \mu_2 \big)$ and variance $(1 - \rho^2) \sigma_1^2$.
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

The central limit theorem makes the normal distribution particularly important, since it can be considered as the limit of the average of "nice" i.i.d. random variables. Similarly to the law of large numbers, the theorem exists in several versions. In this section, we state the Lindeberg-L&eacute;vy central limit theorem: 

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

$$P(A~|~B) = \frac{P(B~|~A)~ P(A)}{P(B)}$$
```

Note that $P(B~|~A)$ is not well-defined if $P(A) = 0$, but in this case it holds $P(A~|~B) = 0$ and the righthand side can also be regarded as $0$, since $P(A) = 0$ and the (ill-defined) $P(B~|~A)$ should be between $0$ and $1$.

The events $A$ and $B$ are often denoted by $H$ and $E$, respectively, where $H$ denotes the **hypothesis** and $E$ denotes the **evidence**. Hence, Bayes' theorem states a way to calculate the probability of some hypothesis $H$ given some data (the evidence) $E$. In use of the law of total probability stated in {ref}```sec:condprob``` Bayes' theorem reads

$$P(H~|~E) = \frac{P(E~|~H)~P(H)}{P(E)} = \frac{P(E~|~H)~P(H)}{P(E~|~H)~P(H) + P(E~|~H^c)~P(H^c)}.$$

The concept is demonstrated in the following video:

<div class="video-container">
<iframe src="https://www.youtube.com/embed/R13BD8qKeTg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
<br>

Bayes' theorem can also be formulated in terms of {ref}```conditional distributions<def:conddistr>```:

Let $X$ and $Y$ be two continuous random variables with joint density $f_{X, Y}$. Then, it holds

$$f_{X~|~Y=y}(x) = \frac{f_{Y~|~X=x}(y) f_X(x)}{f_Y(y)}.$$

More informally, this can be expressed as

$$p(x~|~y) = \frac{p(y~|~x) ~p(x)}{p(y)},$$

where $p$ is a shorthand notation for some probability density in analogy to the elementary probabilities in the case of discrete distributions.

```python

```
