# Independence

Independence of random variables can be defined in multiple, but equivalent, ways. For this purpose, the cumulative distribution function is useful: 

```{admonition} Definition
:class: tip
:name: def:cdf
Let $X: \Omega \rightarrow \mathbb{R}^d$, $d \ge 1$, be a random variable on some probability space $(\Omega, \mathcal{F}, P)$. The function $F_X: \mathbb{R}^d \rightarrow [0, 1]$ defined by

$$ F_X(x) := P_X((-\infty, x_1] \times \cdots \times (-\infty, x_d]) \quad \text{for } x=(x_1, \dots, x_d) \in \mathbb{R}^d$$

is called the **cumulative distribution function** (CDF) of $X$ or $P_X$.
```

Now, we are able to define independence of events and random variables:

```{admonition} Definition
:class: tip
:name: def:indep
Let $(\Omega, \mathcal{F}, P)$ be a probability space. Then two events $A, B \in \mathcal{F}$ are called **independent**, if 

$$ P(A \cap B) = P(A) P(B).$$

Let $X: \Omega \rightarrow \mathbb{R}$ and $Y: \Omega \rightarrow \mathbb{R}$ be two random variables. Then $X$ and $Y$ are called **independent random variables**, if the events $X^{-1}(A)$ and $Y^{-1}(B)$ are independent for all $A, B \in \mathcal{B}(\mathbb{R})$. This is equivalent to the property

$$F_{(X, Y)}(x, y) = F_X(x) F_Y(y) \quad \text{for all } x,y \in \mathbb{R}$$

and if the corresponding densities exist to

$$f_{(X, Y)}(x, y) = f_X(x) f_Y(y) \quad \text{for all } x,y \in \mathbb{R}.$$
```

Independence basically means that the occurrence of event A has no impact on the occurrence of event B or in terms of random variables, the outcomes of random variables should not impact each other. The definition of independent random variables generalizes easily to $d > 1$. 

Note that two events $A$ and $B$ are independent if and only if $P(A~|~B) = P(A)$ (i.e., the probability of $A$ does not change given $B$).  

```{admonition} Lemma
:class: important
:name: lem:indep
Let $X$ and $Y$ be two independent random variables. Then
1. $\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y)$
2. $\text{Cov}(X, Y) = 0$
3. $\text{Cov}(X + Y) = \text{Cov}(X) + \text{Cov}(Y)$
```

If $\text{Cov}(X, Y) = 0$, $X$ and $Y$ are called **uncorrelated**. Note that independent random variables are always uncorrelated, but uncorrelated random variables are not necessarily independent (see e.g. Bemerkung C 5.21 in {cite}```Cramer2017```).  

In many cases, we are able to observe outcomes of independent random variables with the same distribution (so-called **independent identical distributed** (i.i.d.) random variables), but do not know the underlying distribution exactly. Thus, we would like to make conclusions about the distribution based on our observations. In this way, our probabilistic definitions are linked to statistics and estimators. For example, think of rolling a dice multiple times and initially we do not know if the dice is fair or not. We have shown that a fair dice has an expectation of $3.5$. Thus, it is reasonable to verify this expectation in use of the given observations. If the sample mean (see below) of many independent experiments is not sufficiently close to $3.5$, we may reject the hypothesis that the dice is fair. This procedure is called **hypothesis testing** in statistics.

Assume that $X$ and $Y$ are two random variables and that $x_1, \dots, x_n$ and $y_1, \dots, y_n$ are samples of i.i.d. experiments with respect to $P_X$ and $P_Y$, respectively. Then, the preceding definitions of expectation, covariance, variance, standard deviation and correlation have the following statistical counterparts: 
- expectation:

$$\overline{x} := \frac{1}{n}~\sum_{i=1}^n x_i \quad \textbf{(sample mean)}$$

- covariance:

$$s_{xy} := \frac{1}{n-1}~\sum_{i=1}^n (x_i - \overline{x})(y_i - \overline{y}) \quad \textbf{(sample covariance)}$$

- variance:

$$s^2_x := s_{xx} = \frac{1}{n-1}~\sum_{i=1}^n (x_i - \overline{x})^2 \quad \textbf{(sample variance)}$$

- standard deviation:

$$s_x := \sqrt{s^2_x} \quad \textbf{(sample standard deviation)}$$

- correlation:

$$r_{xy} := \frac{s_{xy}}{s_x s_y} = \frac{\sum_{i=1}^n (x_i - \overline{x})(y_i - \overline{y})}{\sqrt{\sum_{i=1}^n (x_i - \overline{x})^2} \sqrt{\sum_{i=1}^n (y_i - \overline{y})^2}} \quad \textbf{(Pearson correlation coefficient)}$$
