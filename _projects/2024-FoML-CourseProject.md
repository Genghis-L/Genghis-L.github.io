---
layout: distill
title: Adversarial Robustness Theory and Algorithms
description: CSCI-GA.2566 Foundations of Machine Learning Course Project
img: assets/img/2024-FoML-CourseProject.png
importance: 300
category: Mathematics, Data Science

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
  - name: Overview

---

## Overview

By looking through recent works in adversarial robustness (e.g. Goodfellow et al. (2015); Ma (2018); Zhang et al. (2019); Awasthi et al. (2023)), we start by defining the question of what adversarial robustness is and why it is important. We then consider frameworks for training robust models, and survey theoretical results that provide insights into the fundamental trade-offs between accuracy and robustness. Specifically, Zhang et al. (2019) introduces TRADES, a theory-based algorithm for balancing this trade-off, and Awasthi et al. (2023) introduces a thorough theoretical framework for adversarial robustness theory. Overall, we examine recent advances that improve training by leveraging conditions such as classification-calibrated surrogate losses and the concept of $H$-consistency, thereby guiding the design of robust models that maintain strong theoretical guarantees.

Keywords: Adversarial Robustness, Robust Optimization, TRADES, $H$-Consistency, ClassificationCalibrated Surrogate Loss



