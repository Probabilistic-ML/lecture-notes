# Gaussian Processes on latent representations

Although the representative power of a Gaussian process is quite high due to the use of kernels, a single kernel measure may not be sufficient to represent very complicated relationships. Although kernel engineering, i.e. combining multiple kernels, may provide some improvement of the representative power, this may still be insufficient. The kernel evaluation is bound to the original $d$-dimensional space $\mathbb{R}^d$. However, the Euclidean distance as used in stationary kernels may not be the best way of measuring similarity between the samples $x_i \in \mathbb{R}^d$, on which the kernel approximation relies. Thus, a transformation $f_t: \mathbb{R}^d \rightarrow \mathbb{R}^q$ to a latent space $\mathbb{R}^q$ can be deployed to improve the effectivenes of the Eulidean distance on the new latent samples $u_i = f_t(x_i)$.

Both {cite}```Damianou2013``` and {cite}```Salimbeni2017``` propose to use deep $\mathcal{GP}$, where multiple $\mathcal{GP}$ are stacked and the outputs of the previous layer $\mathcal{GP}_{i-1}$ are used as the inputs of the current layer $\mathcal{GP}_{i}$. In other words, $l$ number of $\mathcal{GP}$s are stacked, where the first layers $\mathcal{GP}_{1, \dots, l-1}$ correspond to the transformation function $f_t(\cdot)$ and the posterior of the last layer $\mathcal{GP}$ corresponds to the predicted posterior. Both publications differ in the way the training and posterior prediction are formulated. In {cite}```Damianou2013```, a variational posterior is used. This assumes an independence of the outputs of each layer. In {cite}```Salimbeni2017```, a doubly stochastic variational inference is performed instead, where the assumption of independence is dropped.

Besides stacking $\mathcal{GP}$s, various neural network architectures are also proposed for the transformation $f_t$. Most importantly, exact {cite}```Wilson2015``` and approximate {cite}```Wilson2016``` deep kernel learning were proposed, where a deep neural network (DNN) with reducing number of neurons were used as $f_t(\dot)$ to reduce the dimensionality. This approach is especially useful, if the original representation contains redundant features such as in images. 

Moreover, using variational autoencoders with exact {cite}```Casale2018``` and sparse {cite}```Jazbec2021``` $\mathcal{GP}$ were also proposed. Since variational autoencoder seek to learn independent Gaussians as latent variables {cite}```Kingma2014```, using them in a $\mathcal{GP}$ context becomes more straightforward while providing the advantages of probabilistic treatment.  Finally, {cite}```Lee2018``` derive an exact equivalence between $\mathcal{GP}$ and DNN, followed by a proposal to use $\mathcal{GP}$ prior on DNN, yielding neural network Gaussian Processes. As such, $f_t(\cdot)$ consists of all latent layers of the DNN before the output layer.

```{bibliography}
:filter: docname in docnames
:style: plain
```


