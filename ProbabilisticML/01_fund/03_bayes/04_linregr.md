# Linear Regression

In this section, we illustrate the preceding concepts for the case of a linear regression model. The probabilistic concepts are applied to the linear setting and the connection to classical (deterministic) methods are shown. 

We assume the following setting:
- Some data of the form
  
  $$\mathcal{D} = \{ (x_i, y_i)~|~x_i, y_i \in \mathbb{R} \quad \text{for } i = 1,\dots, n\}$$
  
  is given
- The data $\mathcal{D}$ is collected from observation with the relation
  
  $$y_i = a~x_i + \varepsilon_i,$$
  
  where $a \in \mathbb{R}$ and $\varepsilon_i \sim \mathcal{N}(0, \sigma^2)$, $i=1, \dots, n$ are independent normally distributed random variables.
  
$\varepsilon_i$ represents some error term (e.g. measurement errors). The **unknown** coefficient $a$ is called slope. Please note that the outputs $y_i$, $i=1,\dots,n$, are also independent normally distributed random variables with distribution $\mathcal{N}(a~x_i, \sigma^2)$.

Our goal is to use the information in $\mathcal{D}$ to estimate $a$ in an appropiate way. In use of these estimates, it is possible to make predictions for new inputs $x$. Similarly, the probabilistic concepts are applied later on to more advanced models.

## Ordinary Least Squares

The most common approach is to choose an estimate $\hat{a}$ for $a$ such that the **sum of squared resiudals** (SSR) (or residual sum of squares (RSS)) between observations and predictions is minimized, i.e.,

$$\hat{a} = \underset{a}{\text{argmin}}~\sum_{i=1}^n \big(y_i - a~x_i\big)^2$$

The solution is given by 

$$\hat{a} = \frac{\sum_{i=1}^n x_i ~ y_i }{\sum_{i=1}^n x_i^2},$$

where $\overline{x}$ and $\overline{y}$ are the sample means of $x_1, \dots, x_n$ and $y_1,\dots, y_n$, respectively.

In our probabilistic setting, the same result is obtained by the **MLE estimate with Gaussian prior**. Since the observations $y_i$, $i=1,\dots,n$, are independent and $\mathcal{N}(a~x_i, \sigma^2)$-distributed, the joint probability density function reads

$$p(\mathcal{D}~|~a) = \prod_{i=1}^d \frac{1}{\sqrt{2\pi \sigma^2}} ~\exp\Big(-\frac{1}{2}~\frac{(y_i - a~x_i)^2}{\sigma^2}\Big)$$

Thus, the MLE yields

$$
\begin{aligned}
\hat{a} &= \underset{a}{\text{argmax}} ~\prod_{i=1}^n \frac{1}{\sqrt{2\pi \sigma^2}} ~\exp\Big(-\frac{1}{2}~\frac{(y_i - a~x_i)^2}{\sigma^2}\Big) \\
&= \underset{a}{\text{argmax}}~ \prod_{i=1}^n~\exp\Big(-\frac{1}{2}~\frac{(y_i - a~x_i)^2}{\sigma^2}\Big)
\end{aligned}$$

Since $\ln$ is a monotonically increasing function, we can apply it to the righthand side without changing the $\text{argmax}$. Consequently, it holds

$$
\begin{aligned}
\hat{a} &= \underset{a}{\text{argmax}}~ - \frac{1}{2~\sigma^2}~\sum_{i=1}^n~(y_i - a~x_i)^2\big) \\
        &= \underset{a}{\text{argmin}}~\sum_{i=1}^n~\big(y_i - a~x_i\big)^2
\end{aligned}
$$

i.e., the MLE estimate minimizes the SSR.

## Ridge Regression

Instead of minimizing the sum of squared resiudals, it is in some cases useful to introduce an additional **regularization** term. The use of a so-called $L^2$-regularization leads to ridge regression. In this case, the approach is to choose $\hat{a}$ such that 

$$\hat{a} = \underset{a}{\text{argmin}}~\Big(\sum_{i=1}^n \big(y_i - a~x_i\big)^2 + \lambda ~a^2 \Big)$$

The regularization term penalizes large values of the slope $a$. This means that a steep regression line is not desired. The parameter $\lambda > 0$ is called **complexity parameter** and controls how much influence the regularization has.

Again, the solution can be calculated explicitly and is given by 

$$\hat{a} = \frac{\sum_{i=1}^n x_i ~ y_i }{\sum_{i=1}^n x_i^2 + \lambda}$$

## LASSO

## Bayesian Linear Regression

```python

```
