---
layout: distill
title: Adversarial Robustness Theory and Algorithms
description: CSCI-GA.2566 Foundations of Machine Learning Course Project
img: assets/img/2024-FoML-CourseProject.png
importance: 300
category: Data Science

bibliography: references.bib
comments: true
hidden: false

authors:
  - name: Kehan (Genghis) Luo
    url: "https://Genghis-L.github.io/"
    email: kl4747@nyu.edu
    affiliations:
      name: NYU Shanghai
  - name: Jiajun (Jackie) Chen
    email: jc11815@nyu.edu
    affiliations:
      name: NYU Shanghai
  - name: Haolin (Daniel) Jin
    email: hj2528@nyu.edu
    affiliations:
      name: NYU

shortcuts:
  - name: Slides
    link: /assets/pdf/projects/Adversarial_Robustness_Theory_Slides.pdf
    description: "Slides"
  - name: Report
    link: /assets/pdf/projects/Adversarial_Robustness_Theory_Report.pdf
    description: "Report"


toc:
  beginning: true

---

## Overview

By looking through recent works in adversarial robustness (e.g. Goodfellow et al. (2015); Ma (2018); Zhang et al. (2019); Awasthi et al. (2023)), we start by defining the question of what adversarial robustness is and why it is important. We then consider frameworks for training robust models, and survey theoretical results that provide insights into the fundamental trade-offs between accuracy and robustness. Specifically, Zhang et al. (2019) introduces TRADES, a theory-based algorithm for balancing this trade-off, and Awasthi et al. (2023) introduces a thorough theoretical framework for adversarial robustness theory. Overall, we examine recent advances that improve training by leveraging conditions such as classification-calibrated surrogate losses and the concept of $H$-consistency, thereby guiding the design of robust models that maintain strong theoretical guarantees.

Keywords: Adversarial Robustness, Robust Optimization, TRADES, $H$-Consistency, ClassificationCalibrated Surrogate Loss


## Introduction

Deep neural networks have achieved remarkable success in recent years, yet their vulnerability to adversarial perturbations remains a significant concern. Goodfellow et al. (2015) demonstrated that even small, imperceptible changes to input data can deceive state-of-the-art models with high confidence. This phenomenon challenges the reliability of neural networks in safety-critical applications. Further research by Ma (2018) showed that existing defenses, despite their apparent success, often fail against stronger, adaptive adversaries. These findings suggest that current methods lack the theoretical guarantees necessary for practical robustness.

A key issue in addressing adversarial robustness is the fundamental trade-off between robustness and accuracy. This trade-off was formalized by Zhang et al. (2019), who introduced TRADES, a theoretically principled framework for balancing robustness and accuracy. In parallel, work by Awasthi et al. (2023) and others provided rigorous theoretical foundations, illustrating that certain adversarial robustness guarantees can only be achieved at the expense of reduced natural accuracy.

At the same time, the concept of $H$-consistency has emerged as a critical property for surrogate loss functions, ensuring alignment between the surrogate loss and the true classification loss under adversarial settings. This concept guides the choice of training objectives, ensuring that improvements in surrogate loss directly translate into improved adversarial robustness.

The goal of this work is to revisit and connect key theories and results from foundational research on adversarial robustness. By analyzing these contributions, we aim to develop a deeper understanding of both the theoretical and practical aspects of adversarial defenses, ultimately bridging the gap between accuracy and robustness.


## Methodology

As shown in Ma (2018), the robust optimization objective can be formalized as:

$$
\min _\theta \rho(\theta), \quad \text { where } \rho(\theta)=\mathbb{E}_{(x, y) \sim \mathcal{D}}\left[\max _{\delta \in \mathcal{S}} \mathcal{L}(\theta, x+\delta, y)\right]
$$

where $\mathcal{S} \subseteq \mathbb{R}^d$ represents the set of allowable perturbations. Minimizing $\rho(\theta)$ ensures that the loss remains small for all allowed adversarial perturbations. Thus, the search for robust models reduces to solving a well-defined optimization problem.

Standard optimization techniques, such as Stochastic Gradient Descent (SGD), cannot be directly applied to this saddle-point formulation because the adversarial loss involves solving the inner maximization problem at each iteration. The paper applies Danskin's Theorem to address this issue. Specifically, for a differentiable function $g(\theta, \delta)$, where $\delta \in S$, the max-function $\phi(\theta)=\max _{\delta \in S} g(\theta, \delta)$ has a well-defined gradient, given by:

$$
\phi^{\prime}(\theta, h)=\sup _{\delta \in \delta^*(\theta)} h^T \nabla_\theta g(\theta, \delta)
$$
