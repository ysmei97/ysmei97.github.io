---
layout: archive
permalink: /projects/
title: "Projects"
author_profile: true
---

This page includes my projects over the years, covering stochastic optimization, reinforcement learning, image segmentation, network security, etc.

<details>
<summary><b>Table of Contents</b></summary>

- [Determining the region of interest in discrete point data](#determining-roi-in-discrete-point-data)
- [Unveiling sub-optimal solution in an unknown function](#unveiling-sub-optimal-solutions-in-an-unknown-function)
- [Segment the precise brain tumor with attention to correlated information](#segment-the-precise-brain-tumor-with-attention-to-correlated-information)
- [Prioritized sampling for multi-agent RL](#prioritized-sampling-for-multi-agent-rl)
- [The multi-agent RL can be even trained faster](#the-multi-agent-rl-can-be-even-trained-faster)
- [Remixing monotonic projection with theoretical explanation](#remixing-monotonic-projection-with-theoretical-explanation)
- [With protocol dialects, a windtalker](#with-protocol-dialects-a-windtalker)

</details>


<a name="determining-roi-in-discrete-point-data"></a>
## Determining regions of interest in discrete point data

To determine an optimal solution in the expensive unknown function, General Bayesian optimization methods sequentially sample the space by maximizing an acquisition function defined over the posterior of the [Gaussian process](https://en.wikipedia.org/wiki/Gaussian_process) model and according to past samples and evaluations. This requires the continuality of the search space so the GP model can indicate the correlation among input samples. Nevertheless, if our observations are point events (e.g., following a [Poisson point process](https://en.wikipedia.org/wiki/Poisson_point_process)), GP cannot perform the modeling over those discrete samples.

Therefore, we choose a doubly stochastic point process, the Gaussian [Cox process](https://en.wikipedia.org/wiki/Cox_process) (GCP) with a non-negative smooth [link function](https://en.wikipedia.org/wiki/Generalized_linear_model#Link_function) connecting the Poisson process with an underlying GP, as the surrogate model for the point data Bayesian optimization (PDBO). We formulate a Maximum *a posteriori* inference of the functional posterior and solve its latent intensity mean and covariance via the Laplace approximation and kernel transformation. On top of that, we consider a wide range of special acquisition functions, such as detecting peak intensity, idle time, change point, and cumulative arrivals, through the underlying GCP model to efficiently discover regions of interest (ROIs) in a large discrete point dataset.


<a name="unveiling-sub-optimal-solutions-in-an-unknown-function"></a>
## Unveiling sub-optimal solutions in an unknown function 

Giving up the optimal solution while turning to a sub-optimal one is painful. However, even if finding all or most global optima is desired in many real-world problems that can be seen as multimodal optimization, implementing the optimal solutions is sometimes infeasible due to various practical restrictions, such as resource limitations, physical constraints, etc.

We developed a multimodal [Bayesian optimization](https://en.wikipedia.org/wiki/Bayesian_optimization) (MBO) framework to locate a set of local/global solutions of a given unknown expensive function. We derive the joint distribution of the objective function and its first-order gradients (that are not considered in standard BO frameworks) and introduce new acquisition functions backed by this joint distribution to decide local optima sequentially during optimization.


<a name="segment-the-precise-brain-tumor-with-attention-to-correlated-information"></a>
## Segment the precise brain tumor with attention to correlated information

<a name="prioritized-sampling-for-multi-agent-rl"></a>
## Prioritized sampling for multi-agent RL

<a name="the-multi-agent-rl-can-be-even-trained-faster"></a>
## The multi-agent RL can be even trained faster

<a name="remixing-monotonic-projection-with-theoretical-explanation"></a>
## Remixing monotonic projection with theoretical explanation

<a name="with-protocol-dialects-a-windtalker"></a>
## With protocol dialects, a windtalker
