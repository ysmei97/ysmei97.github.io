---
layout: archive
permalink: /projects/
title: "Projects"
author_profile: true
---

This page includes my projects since 2019.

<details>
<summary><b>Table of Contents</b></summary>

- [Stochastic process and Bayesian optimization](#stochastic-process-and-bo)
  - [Determining the region of interest in discrete point data](#determining-roi-in-discrete-point-data)
  - [Unveiling sub-optimal solution of an unknown function](#unveiling-sub-optimal-solutions-of-an-unknown-function)
- [Segmenting the precise tumor via attention to common information](#segment-the-precise-brain-tumor-via-attention-to-correlated-information)
- [Reinforcement learning](#rl)
  - [Prioritized sampling for multi-agent RL](#prioritized-sampling-for-multi-agent-rl)
  - [The multi-agent RL can be trained faster](#the-multi-agent-rl-can-be-even-trained-faster)
  - [Remixing monotonic projection with theoretical explanation](#remixing-monotonic-projection-with-theoretical-explanation)
- [Network security](#network-security)
  - [With protocol dialects, a windtalker](#with-protocol-dialects-a-windtalker)

</details>


<a name="stochastic-process-and-bo"></a>
# Stochastic process and Bayesian optimization
About [Bayesian optimization](https://en.wikipedia.org/wiki/Bayesian_optimization)

<a name="determining-roi-in-discrete-point-data"></a>
## Determining regions of interest in discrete point data

To determine an optimal solution in the expensive unknown function, general Bayesian optimization methods sequentially sample the space by maximizing an [acquisition function](https://botorch.org/docs/acquisition) defined over the posterior of the [Gaussian process](https://en.wikipedia.org/wiki/Gaussian_process) model and according to past samples and evaluations. This requires the continuality of the search space so that the GP model can indicate the correlation among input samples. Nevertheless, if our observations are point events (e.g., following a [Poisson process](https://en.wikipedia.org/wiki/Poisson_point_process)), GP cannot perform accurate modeling over those discrete samples.

Therefore, we choose a doubly stochastic point process, the Gaussian [Cox process](https://en.wikipedia.org/wiki/Cox_process) (GCP) with a non-negative smooth [link function](https://en.wikipedia.org/wiki/Generalized_linear_model#Link_function) (connecting the Poisson process with an underlying GP) as the surrogate model for point event intensity to achieve our **point data Bayesian optimization (PDBO)**. We formulate a [Maximum *a posteriori*](https://en.wikipedia.org/wiki/Maximum_a_posteriori_estimation) inference of the functional posterior of latent intensity and solve its mean and covariance via the [Laplace approximation](https://en.wikipedia.org/wiki/Laplace%27s_approximation) and kernel transformation in [reproducing kernel Hilbert space](https://en.wikipedia.org/wiki/Reproducing_kernel_Hilbert_space). On top of that, we consider a wide range of special acquisition functions, such as detecting peak intensity, idle time, [change point](https://en.wikipedia.org/wiki/Change_detection), and cumulative arrivals, through the underlying GCP model to efficiently discover regions of interest (ROIs) in a large discrete point dataset.


<a name="unveiling-sub-optimal-solutions-of-an-unknown-function"></a>
## Unveiling sub-optimal solutions of an unknown function 

Giving up the optimal solution while turning to a sub-optimal one is painful. However, even if finding all or most global optima is desired in many real-world problems that can be seen as [multimodal optimization](https://en.wikipedia.org/wiki/Evolutionary_multimodal_optimization), implementing the optimal solutions is sometimes infeasible due to various practical restrictions, such as resource limitations, physical constraints, etc.

We developed a **multimodal Bayesian optimization (MBO)** framework to locate a set of local/global solutions of a given unknown expensive function. We derive the joint distribution of the objective function and its first-order gradients (that are not considered in standard BO frameworks) and introduce new acquisition functions backed by this joint distribution to decide local optima sequentially during optimization.


<a name="segment-the-precise-brain-tumor-via-attention-to-correlated-information"></a>
# Segmenting the precise tumor via attention to common information

The multimodal data allows the identification of correlated information shared by different modalities, i.e., [common information](https://isl.stanford.edu/~abbas/presentations/lect00-viterbi.pdf), thus achieving better representations by the resulting neural networks. From the information theory perspective, the most informative structure between modalities represents the feature representation of one modality that carries the maximum amount of information toward another. To better measure the latent microstructure within the common information, we designed the **partial common information mask (PCI-mask)** to identify the latent partial common information shared by subsets of different modalities in finer granularity. The PCI-mask is optimized online in an unsupervised fashion during the learning.

Besides, we add a [self-attention](https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/#attention-and-self-attention) module that takes the PCI masks and concatenated feature representation of each modality as inputs to obtain the attention feature representation carrying precise partial common information. This module will discriminate different types and structures of partial common information by selectively assigning different attention weights. Thus, utilizing the PCI-mask and self-attention makes our segmentation algorithm more capable of avoiding treating different modalities as equal contributors during training or over-aggressively maximizing the total correlation (e.g., [Hirschfeld-Gebelein-Renyi](https://en.wikiversity.org/wiki/HGR) maximal correlation) of feature representations.

The proposed method optimizes the common information in feature representations of multimodal brain tumor data inputs, which allows precise segmentation with attention to microstructures. The framework is evaluated on the public brain tumor dataset: [Multimodal Brain Tumor Segmentation Challenge](https://www.med.upenn.edu/cbica/brats2020/data.html), where we achieved the [Dice](https://en.wikipedia.org/wiki/S%C3%B8rensen%E2%80%93Dice_coefficient) scores (median) of 0.920, 0.897, 0.837 for the whole tumor, tumor core, and enhancing tumor, respectively.


<a name="rl"></a>
# Reinforcement learning

<a name="prioritized-sampling-for-multi-agent-rl"></a>
## Prioritized sampling for multi-agent RL

We formulate a **multi-agent collective prioritization optimization (MAC-PO)** problem that defines the objective as the regret of the expected return and solves it to acquire the weight solution. Following the prioritized experience replay scheme, we extend the prioritized weight assignment to the multi-agent RL scenario, where the agents' individual action-value functions contribute to determining the weights. Specifically, we use several case studies to illustrate our findings.

<a name="the-multi-agent-rl-can-be-even-trained-faster"></a>
## The multi-agent RL can be trained faster

The sampling phase matters in off-policy RL, where a batch of transitions is uniformly sampled from the memory replay buffer in normal circumstances. We identified the bottleneck during this sampling stage, and to handle it, we can reuse a set of transitions we have already sampled from the replay buffer. We designed an acceleration framework in multi-agent off-policy RL. This data reuse strategy will **accelerate the multi-agent experience replay (AccMER)** guided by the priority weights.

<a name="remixing-monotonic-projection-with-theoretical-explanation"></a>
## Remixing monotonic projection with theoretical explanation


<a name="network-security"></a>
# Network security

<a name="with-protocol-dialects-a-windtalker"></a>
## With protocol dialects, a windtalker
