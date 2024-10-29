---
layout: post
title: "Multi-Modal Training"
date: 2024-10-28
categories: [perspective]
tags: [thoughts, multi-modal]
---

There are ongoing discussions about the architecture of future multi-modal models that may impact the framework.

The trend towards unified model architecture seems promising for the future. However, current high-performing multimodal models don't adopt this approach, likely due to difficulties in achieving good performance.

The direction I'm advocating is multimodal collaborative pre-training combined with structural unification (without specially designed modal components). The former is more urgent and feasible in the short term. The key challenge lies in achieving good results by training multiple tasks' data together. Unifying the model structure will come later, potentially starting with modal Mixture of Experts (MoE), where different modalities or tasks use different Experts. This might involve prior knowledge in Expert selection or learning a Router. Eventually, this could evolve into a completely modality-agnostic, unified large model.

Our previous plan primarily focused on collaborative pre-training of multimodal task data, without yet investing in a unified multimodal structure. However, both approaches currently face a significant challenge: the dynamic nature of data. This issue can be addressed now and will prove valuable in the future.

We concluded that the priority is currently on training multiple tasks together, such as simultaneously training generation and comprehension tasks, rather than focusing on the model structure itself.

