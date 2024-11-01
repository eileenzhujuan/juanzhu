---
layout: posts
title: "Parallelized Planner"
date: 2024-11-01
categories: [advanced]
tags: [robot-planner, acceleration]
---

Probabilistic Roadmap (PRM) Planners assume multiple planning queries will be executed within the same static environment.

Dynamic Roadmaps (DRMs) adapt the classical PRM by generating a preprocessed roadmap for use in changing environments. To enable real-time planning, DRMs swiftly identify which parts of the roadmap are blocked by obstacles through online adaptation.

DRMs are typically used with fixed-pose robots. In dynamic scenarios, they demand substantial computational resources and memory to store and update samples. However, with GPUs, we may be able to overcome these challenges.

For instance, H. Schumann-Olsen et al. [1] propose accelerating DRM implementation through parallel redesign. The illustration below is from their paper.

![image1.png]({{ '/assets/PDRM.png' | relative_url }})

Similarly, S. Murray et al. [2] suggest that collision detection in general PRM can be naturally parallelized, as shown in the following illustration from their original paper.

![image2.png]({{ '/assets/parallelPRM.png' | relative_url }})

Additionally, Nvidia has released [NVIDIA Robotics](https://developer.nvidia.com/isaac), a full-stack solution to help developers accelerate cloud-to-edge systems and optimize AI models for robotic systems.

Among these tools, CuRobo [3] is a CUDA-accelerated library that tackles robot motion planning problems at scale. It runs multiple trajectory optimizations simultaneously to yield the best solution, demonstrating excellent performance through parallel trajectory optimization.

![image3.png]({{ '/assets/cuRobo.png' | relative_url }})

## Reference

1. H. Schumann-Olsen, M. Bakken, Ø. H. Holhjem, and P. Risholm,
“Parallel Dynamic Roadmaps for Real-Time Motion Planning in
Complex Dynamic Scenes,” 3rd Workshop on Robots in Clutter, IEEE,
2014.
2. S. Murray, W. Floyd-Jones, Y. Qi, D. Sorin, and G. Konidaris, “Robot
Motion Planning on a Chip,” in RSS, 2016
3. https://curobo.org/reports/curobo_report.pdf
