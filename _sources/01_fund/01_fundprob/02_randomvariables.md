(sec:rv)=
# Random Variables

Imagine that we perform multiple independent random experiments by rolling repeatedly ($n$-times) a fair dice. The corresponding sample space is given by

$$\Omega = \{ \omega = (\omega_1, \omega_2, \dots, \omega_n)~|~\omega_i \in \{1, 2, 3, 4, 5, 6\} \ \text{for } i=1, \dots,n \}.$$

Since the experiments are independent and we consider a fair dice, it is reasonable to define

$$ p(\omega) = \frac{1}{6^n} \quad \text{for each } \omega \in \Omega$$

which results in a discrete probability space $(\Omega, \mathcal{P}(\Omega), P)$. Eventually, we are not interested in events with respect to $\Omega$, but for example in the average outcome of the experiments or the number of times of rolling a six. Instead of modelling these experiments directly by redefining $\Omega$ and $p$, it is very useful to apply the concept of random variables:

```{admonition} Definition
:class: tip
:name: def:rv
Let $(\Omega, \mathcal{F}, P)$ be a probabiliy space. A map $X: \Omega \rightarrow \mathbb{R}^d$, $d \ge 1$, is called a real-valued **random variable**, if 

$$ X^{-1}(A) := \{ \omega \in \Omega~|~X(\omega) \in A \} \in \mathcal{F}$$

for each $A \in \mathcal{B}(\mathbb{R}^d)$ and the probability measure $P_X: \mathcal{B}(\Omega) \rightarrow [0, 1]$ given by

$$P_X(A) := P(X^{-1}(A)) \quad \text{for } A \in \mathcal{B}(\Omega)$$

is called the **distribution of** $X$ **under** $P$. We also write $X \sim P_X$ which is useful if $P_X$ is well-known (refer to {ref}```sec:impprobdistr```). If $P_X$ admits a {ref}`probability density <def:contdistr>`, then we denote the density by $f_X$. Furthermore, the cumulative distribution function of $P_X$ is denoted by $F_X$.
```

In order to model a fair dice as a random variable simply set $\Omega= \{1, 2, 3, 4, 5, 6\}$ as well as $p(\omega) = \frac{1}{6}$ for $\omega \in \Omega$ to obtain the discrete probability space $(\Omega, P)$ and define $X$ by

$$X(\omega) = \omega \quad \text{for } \omega \in \Omega.$$

Observe that $X$ does only take values in $\{1, 2, 3, 4, 5, 6\}$. Hence, $X$ maps to $\mathbb{R}$, but $P_X(\mathbb{R} \backslash \{1, 2, 3, 4, 5, 6\}) = 0$. $\{1, 2, 3, 4, 5, 6\}$ is called the **support** of $P_X$.   

- If $d > 1$, $X: \Omega \rightarrow \mathbb{R}^d$ is also called a multivariate random variable or random vector. In this case, $X$ is a random variable if and only if each component $X_i: \Omega \rightarrow \mathbb{R}$ is a scalar random variable. The special case $d=2$ is known as bivariate random variable. For $d=1$, the term univariate is used.
- If $(\Omega, \mathcal{F}, P)$ is a {ref}`discrete probability space <def:discrdistr>`, **each** map $X: \Omega \rightarrow \mathbb{R}^d$ is a random variable, since $\mathcal{F} = \mathcal{P}(\Omega)$ contains all subsets of $\Omega$. Moreover, note that we can identify $P_X$ with a discrete probability distribution (as seen in the example of a dice), since $X$ can take at most countably many distinct values in $\mathbb{R}^d$. In this case, we denote the corresponding elementary probabilities by $p_X$.
- If $(\Omega, \mathcal{F}, P)$ is a {ref}`continuous probability space <def:contdistr>`, it can be shown that at least each **continuous** map $X: \Omega \rightarrow \mathbb{R}^d$ is a random variable.

A very important concept is the expectation of random variables:

```{admonition} Definition
:class: tip
:name: def:exp
Let $X: \Omega \rightarrow \mathbb{R}^d$, $d \ge 1$, be a random variable on some probability space $(\Omega, \mathcal{F}, P)$. The **expectation**, **expected value** or **mean** of X is defined by

$$ \mathbb{E}(X) := \sum_{x \in X(\Omega)} x ~ p_X(x) $$

for discrete probability spaces, if the sum if well-defined, as well as by

$$ \mathbb{E}(X) := \int_{\mathbb{R}^d} x ~ f_X(x)~dx $$

if $P_X$ admits a probability density and the integral is well-defined. Sometimes $\mathbb{E}(X)$ is denoted by $\mu$ or $\mu_X$.
```

The expectation of rolling a fair dice is given by

$$\sum_{i=1}^6 i ~ p(i) = \sum_{i=1}^6 i ~ \frac{1}{6} = \frac{21}{6} = 3.5$$

In many cases, we need to compute the mean of a transformed random variable. For this purpose, the following results will be useful:

```{admonition} Theorem
:class: important
:name: thm:trans
Let $X: \Omega \rightarrow \mathbb{R}^d$, $d \ge 1$, be a random variable and $g: \mathbb{R}^d \rightarrow \mathbb{R}^k$ a function. Then

$$ \mathbb{E}(g(X)) = \sum_{x \in X(\Omega)} g(x) ~ p_X(x) $$

for discrete probability spaces and

$$ \mathbb{E}(g(X)) := \int_{\mathbb{R}^d} g(x) ~ f_X(x)~dx $$

if $P_X$ admits a probability density.
```

At this point, we are somewhat imprecise. Indeed, the transformation $g$ needs to be sufficiently nice, but at this point we neglect additional assumptions. 

The remaining part of this section is a little bit **more involved and not necessarily required**. Nevertheless, we state these results in view of a better understanding of {ref}```multivariate normal distributions <def:multnormal>```. 

In use of the above theorem, we are able to define the covariance matrix of multivariate random variables:

```{admonition} Definition
:class: tip
:name: def:cov
Let $X: \Omega \rightarrow \mathbb{R}^d$ and $Y: \Omega \rightarrow \mathbb{R}^k$ be random variables. The **covariance matrix** between X and Y is defined by

$$\text{Cov}(X, Y) := \mathbb{E}\big((X - \mathbb{E}(X))(Y - \mathbb{E}(Y))^T \big)$$

If $Y = X$ the definition yields the **covariance matrix of** X, i.e., 

$$ \text{Cov}(X) := \text{Cov}(X, X).$$
```

- From two random variables $X$ with values in $\mathbb{R}^d$ and $Y$ with values in $\mathbb{R}^k$, we can define a new single random variable $Z = (X, Y)$ with values in $\mathbb{R}^{d + k}$ by stacking the two vectors. Note that we need to consider $P_Z$ in order to apply the {ref}```transformation theorem <thm:trans>``` and to compute $\text{Cov}(X, Y)$. The distribution of $Z$ is called the **joint distribution** of $X$ and $Y$.
- Note that in general $\text{Cov}(X, Y)$ is indeed a matrix of size $d \times k$. This matrix contains the pairwise covariances of all components of $X$ and $Y$, i.e., 
\begin{align*}
\text{Cov}(X, Y) = \begin{pmatrix} \text{Cov}(X_1, Y_1) & \text{Cov}(X_1, Y_2) & \cdots & \text{Cov}(X_1, Y_k) \\
\text{Cov}(X_2, Y_1) & \text{Cov}(X_2, Y_2) & \cdots & \text{Cov}(X_2, Y_k) \\
\vdots & \vdots & \ddots & \vdots \\
\text{Cov}(X_d, Y_1) & \text{Cov}(X_d, Y_2) & \cdots & \text{Cov}(X_d, Y_k)
\end{pmatrix}
\end{align*}
- In the case $d=1$, $\text{Cov}(X) \in \mathbb{R}$ is simply called the **variance of** $X$ which is also denoted by $\sigma^2$ or $\sigma_X^2$. Furthermore, $\sigma := \sigma_X := \sqrt{\sigma_X^2}$ is called the **standard deviation** of $X$. It holds 

$$\sigma^2 = \int (x - \mathbb{E}(X))^2 ~ f_X(x)~dx.$$
- For $d=k=1$, the **correlation** $\text{Corr}(X, Y)$ (also denoted $\rho$ or $\rho_{X, Y}$) is given by

$$ -1 \le \text{Corr}(X, Y) := \frac{\text{Cov}(X, Y)}{\sigma_X ~ \sigma_Y} \le 1$$

Note that the correlation is only defined if the variances of $X$ and $Y$ are non-zero. 

Expectation and covariance have some nice properties:

```{admonition} Lemma
:class: important
:name: lem:expprop
Let $X$, $Y$ and $Z$ be random variables and $a, b \in \mathbb{R}$. Then
1. $\mathbb{E}(a) = a$
2. $\mathbb{E}(aX) = a~\mathbb{E}(X)$
3. $\mathbb{E}(X + Y) = \mathbb{E}(X) + \mathbb{E}(Y)$
4. $\mathbb{E}(|X + Y|) \le \mathbb{E}(|X|) + \mathbb{E}(|Y|)$
5. If $X \le Y$ (i.e., $X(\omega) \le Y(\omega)$ for each $\omega \in \Omega$, then $\mathbb{E}(X) \le \mathbb{E}(Y)$
6. $\mathbb{E}(|X|) = 0 ~ \Leftrightarrow ~ P(X \ne 0) = 0$
7. $\text{Cov}(X) \ge 0$
8. $\text{Cov}(X, Y) = \text{Cov}(Y, X)$
9. $\text{Cov}(X, Y) = \mathbb{E}(XY^T) - \mathbb{E}(X) \mathbb{E}(Y)^T$
10. $\text{Cov}(X + Y, Z) = \text{Cov}(X, Z) + \text{Cov}(Y, Z)$
11. $\text{Cov}(X) = 0 ~ \Leftrightarrow ~ P(X \ne \mathbb{E}(X)) = 0$. In particular, $\text{Cov}(a) = 0$.
12. $\text{Cov}(a, b) = 0$
13. $\text{Cov}(aX, bY) = ab~\text{Cov}(X, Y)$
``` 

In analogy to conditional probabilities, it also possible to define conditional probability distributions for two random variables:

```{admonition} Definition
:class: tip
:name: def:conddistr
Let $X$ and $Y$ be two random variables. 

For discrete random variables, the conditional distribution of $X$ given $Y=y$ is defined by

$$P(X=x~|~Y=y) := \frac{P(X=x, Y=y)}{P(Y=y)} \quad \text{if } P(Y=y) > 0.$$

For continuous random variables with joint distribution density $f_{X, Y}$, the conditional distribution of $X$ given $Y=y$ is given by

$$f_{X~|~Y=y}(x) := \frac{f_{X, Y}(x, y)}{f_Y(y)},$$

where $f_Y$ is the pdf of $Y$ and it is assumed that $f_Y(y) > 0$.
```

The idea behind this definition is that the distribution of a random vector $(X, Y)$ is possibly known (i.e., the joint distribution of $X$ and $Y$). In this case, the distributions of $X$ and $Y$ are known (the so-called marginal distributions), but these distributions characterize $X$ and $Y$ independently. However, we would also like to **make conclusions about the values of** $X$ **in the case that the value for** $Y$ **is known** in use of the conditional distribution.

It is also possible to express the marginal distribution in terms of the conditional distribution:

$$f_X(x) = \int f_{X, Y}(x, y) ~dy = \int f_{X~|~Y=y}(x)~f_Y(y)~dy$$ 
