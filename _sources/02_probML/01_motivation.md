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

# Motivation of Probabilistic Models

In {ref}```sec:linregr```, we have discussed a simple linear model in use of different approaches:

- MLE / ordinary least squares
- MAP with Gaussian prior / ridge regression
- MAP with Laplace prior / LASSO
- Bayesian ridge regression

The first three methods yield **point estimates** for the slope $\beta$. It is possible to include some prior belief by using a MAP estimate, but the result is still an ordinary linear function which can be used to make predictions on unseen inputs. This way it is very hard to quantify the uncertainty of the prediction. *Is it reasonable to assume that the prediction is close to the outcome of a real experiment or is it possible only a rough guess?* This is a huge disadvantage in decision making. However, the Bayesian ridge regression yields additional information. The model does not only make a prediction. Instead of a fixed value for $\beta$, it uses a probability distribution and returns even a distribution of possible outcomes (refer to posterior distribution and posterior predictive distribution in {ref}```sec:bayesianinference```). Additionally, Bayesian ridge regression includes regularization.

Hence, a main advantage of Bayesian / probabilistic models is the possibility to include uncertainty into decision making. It is even possible to consider different types of uncertainty. In the example in {ref}```sec:linregr```, we already mentioned the terms **epistemic** and **aleatoric** uncertainty:

- epistemic uncertainty: 
    - uncertainty due to the lack of knowledge of the real world
    - can be reduced by more data
- aleatoric uncertainty:
    - inherent uncertainty of the data
    - represents the randomness (noise) in experiments, i.e., it causes different outcomes when repeating the same experiment over and over again
    - can not be reduced

In the simple linear regression, it was assumed that the noise term (the  aleatoric uncertainty) is normally distributed with zero mean and **known** variance $\sigma_{\text{noise}}^2$. A more general setting could also include $\sigma^2$ as a unknown parameter. In this case, the aim is to perform Bayesian inference on $\beta$ (with Gaussian prior) and $\sigma_{\text{noise}}^2$ (with inverse gamma distributed prior) simultaneously. Consequently, the resulting Bayesian model contains both types of uncertainty. Additional to the mean prediction, the posterior predictive distribution contains information on the epistemic uncertainty and estimates the aleaetoric uncertainty as well. The frequentist approach to linear regression can also make some statements about uncertainty in terms of confidence and prediction intervals, but we have already seen in the {ref}```coin toss example<sec:cointoss>``` that the interpretation is more difficult and less intuitive. Please note that the interpretation of uncertainty in frequentists statistics and  Bayesian inference is much discussed. Hence, the present explanations reflect only a specific, but hopefully reasonable, point of view.

A drawback of the use of probabilistic models is the **increased computational effort**. In the simple example, we needed first to apply some more mathematics and in addition to the mean of the posterior distribution it is necessary to calculate the variance. This is an acceptable effort, but one should keep in mind that the posterior (predictive) distribution can not be computed analytically in most applications. Therefore, approximations such as MCMC and variational inference are used which include expensive computations for high dimensional and complex problems. For this reason, these types of models have just become more and more popular in recent years due to the rapid progress in computational power.

Overall, a **major advantage of Bayesian models is the quantification of uncertainty** and in particular, of the epistemic uncertainty. This property is highly relevant in more complex problems. After the discussion of more advanced models in the following sections, we will review some important applications.
