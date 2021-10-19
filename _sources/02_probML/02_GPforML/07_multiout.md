---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.10.3
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

(sec:multiout)=
# Extension to Multiple Outputs

In {ref}```sec:gpr```, we considered the single output case and the data $\mathcal{D}$ of observations was of the form

$$\mathcal{D} = \{ (x_i, y_i)~|~x_i \in \mathbb{R}^d, y_i \in \mathbb{R} \quad \text{for } i=1,\dots,n \}$$

In the present section, we consider the multi-output case, i.e., $\mathcal{D}$ is given by

$$\mathcal{D} = \{ (x_i, y_i)~|~x_i \in \mathbb{R}^d, y_i \in \mathbb{R}^k \quad \text{for } i=1,\dots,n \}$$

with some $k \ge 2$ and the functional relation between inputs $x_i$ and outputs $y_i$ reads

$$y_i = f(x_i) + \varepsilon_i,$$

where $f: \mathbb{R}^d \rightarrow \mathbb{R}^k$ which is identified with (a sample path of) a suitable Gaussian process $f$ and $\varepsilon_i$, $i=1,\dots,n$, are $\mathbb{R}^k$-valued centered independent multivariate Gaussian random variables.

In order to construct a Gaussian process regression model, some simple strategies exist:

- Under the assumption that the components of the output are independent, a single output model as stated in {ref}```sec:gpr``` can be fitted 
    - separately for each component or
    - jointly by maximizing the sum of log marginal likelihoods (shared hyperparameters)
- Otherwise, i.e., if the compontents of the output are correlated, a possibility is to assume that there exists some function $g: \mathbb{R}^d \rightarrow \mathbb{R}^m$ and a matrix $W \in \mathbb{R}^{k \times m}$ such that 

 $$f(x) = Wg(x)$$
 
 and the compontents of $g$ are independent. This means that $f$ is at least the linear transformation of independent compontents. Then, a Gaussian process regression model can be fitted for $g$ and the transformation $W$ can be applied additionally. A popular method to construct $W$ is the use of [principal component analysis](https://en.wikipedia.org/wiki/Principal_component_analysis) of the labels $y$ (also called singular value decomposition (SVD) or proper orthogonal decomposition (POD)). The idea can also be generalized to non-linear transformation such as [autoencoders](https://en.wikipedia.org/wiki/Autoencoder).
 
References to further approaches can be found in Section 9.1 of {cite}```Rasmussen2006```.

```{bibliography}
:filter: docname in docnames
:style: plain
```
