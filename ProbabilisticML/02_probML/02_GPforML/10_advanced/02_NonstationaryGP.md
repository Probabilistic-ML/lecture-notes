# Non-stationary Gaussian Processes

Length scale and other kernel parameters have a large influence on the resulting $\mathcal{GP}$ model. For example, if the lengthscale is too large, the resulting model may underfit the data, smoothing out important characteristics. Similarly, a too small lengthscale will lead to overfitting data points, generating peaks around them. MLE or MAP approaches seek to find a good trade-off between under- and overfitting. 

However, a global treatment of the length scale and other kernel parameters may be too limiting. Some functions may depict locally different structures, where the optimal length scale in one region is not equal to the optimal length scale in another. If we use MLE in this case, we would get a weighted average of these optimal values, where the weights depend on the number of data points in the corresponding subregion.

Non-stationary $\mathcal{GP}$ were proposed to tackle this problem, where $q\in\mathbb{N}$ kernel parameters $\theta \in \mathbb{R}^q$ are replaced with continous functions $\theta_{x}: \mathbb{R}^n \rightarrow \mathbb{R}^q$ which depend on the input coordinates $x \in \mathbb{R}^n$ of the $\mathcal{GP}$ prediction. In the following, we only consider isotropic $\mathcal{GP}$ for ease of notation but the results can be trivially extended to anisotropic $\mathcal{GP}$.

Point estimates of local smoothness were used in {cite}```Plagemann2008```, where a further $\mathcal{GP}_l$ is deployed to predict the log-length scales $l_i \in \mathbb{R}$, such that $l_i =\mathrm{exp}(f_\theta(x_i))$ to impose positivity, where $f_\theta$ is the mean prediction of $\mathcal{GP}_l$ at point $x_i$. In addition, the authors proposed to use a modified version of the squared exponential kernel for the first level $\mathcal{GP}$

$$ k(x_i, x_j) = \sigma^2 \sqrt{l_i l_j} \cdot \sqrt{\frac{2}{l_i^2 + l_j^2}} \cdot \mathrm{exp}\left(-2 \frac{\left(x_i - x_j\right)^2}{l_i^2 + l_j^2}\right) $$

which results from averaging two local covariance matrices $\Sigma_i$ and $\Sigma_j$ of the correspoding $\mathcal{GP}$ with length scales $l_i$ and $l_j$. Authors propose to use the posterior likelihood  for training 

$$ \mathrm{log} \, p(l | y, X, \theta) = \mathrm{log} \, p(y|X, exp(l), \theta_y) + \mathrm{log} \, p(l|X,l_l, X_l, \theta_l) + const. $$

where $X \in \mathbb{R}^{m, n}, y \in \mathbb{R}^m$ represent the $m$ training samples, $\theta_y$ are the further parameters of $\mathcal{GP}$, $X_l$, $l_l$ and $\theta_l$ represent the support points, the length scale and further parameters of $\mathcal{GP}_l$ respectively. Other kernel parameters $\theta_y, \theta_l$ such as the variances $\sigma, \sigma_l$ of the kernels as well as the noise variance $\sigma_n$ are obtained in an outer optimization loop, where the length scale parameters $l, l_l$ were fixed.

Deep Gaussian covariance networks, a more general non-stationary $\mathcal{GP}$ is proposed in {cite}```Cremanns2021```. In this work, the authors propose to use a deep neural network (DNN) to approximate the length scales. Moreover, they also propose to learn a non-stationary noise variance $\sigma_{\mathrm{noise}}^2$ using a DNN to handle data sets, where the amount of noise varies in different regions (i.e. heteroscedastic instead of homoscedastic noise). Moreover, instead of restricting to a squared exponential kernel, they propose to reparametrize the existing kernels using two length scales $l_i, l_j$. For squared exponential kernel, this would look like

$$ k(x_i, x_j) = \sigma^2 \mathrm{exp} \left( -\frac{1}{2} \left(\frac{x_i}{l_i} - \frac{x_j}{l_j}\right)^2 \right) $$

For the training, the weights of the DNN have to be obtained. Authors use the [MLE of the stationary $\mathcal{GP}$](https://probabilistic-ml.github.io/lecture-notes/02_probML/02_GPforML/06_hyperparamselect.html#sec-selectofhyperp) as the loss function. Using backpropagation, the gradients of the weights wrt. the MLE are computed and the optimal weights are obtained through optimization.


```{bibliography}
:filter: docname in docnames
:style: plain
```
