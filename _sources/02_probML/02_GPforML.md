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

(sec:GPforML)=
# Gaussian Processes for Machine Learning

Roughly speaking, Gaussian processes are a collection of random variables with Gaussian distributions. They are mainly characterized by their **kernel** or **kernel function**. In particular, they provide the foundation for probabilistic machine learning models belonging to the class of kernel-based methods. These methods use the kernel function to enable the use of a high-dimensional feature space. The purpose is to generate a more flexible machine learning model. This approach is particularly useful to generalize linear learning methods to non-linear settings and is also referred to as **kernel trick**. In this chapter, we focus on Gaussian processes, since they are most useful for our applications and fit into our probabilistic framework. First, let us discuss the intuition behind the kernels.
