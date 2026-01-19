---
layout: home
title: "Visualization"
---
TF-VLA: A Framework for Force-Aware Bimanual Manipulation without Tactile Feedback

Abstract

Deploying robotic systems in unstructured logistic environments is hindered by the challenge of manipulating heterogeneous objects under physical uncertainty. 
While dual-arm platforms offer the kinematic capacity to handle diverse geometries, existing control paradigms face significant hurdles. 
Reinforcement Learning (RL) policies often suffer from prohibitive sim-to-real gaps, while state-of-the-art Vision-Language-Action (VLA) models struggle with "tactile blindness" in force-aware, non-prehensile tasks due to a lack of force-annotated datasets. 
To bridge this gap, we propose Tactile-Free Vision-Language-Action (TF-VLA), a framework designed to learn force-sensitive manipulation without physical tactile feedback. 
Our approach introduces a novel data synthesis strategy that utilizes Virtual Penetration Depth as a geometric proxy for contact force, converting low-cost, position-controlled trajectories into force-aware primitives. 
Furthermore, we incorporate subtask grounding to enable the model to semantically reason about manipulation progress and modulate effort through iterative attempts. 
Extensive real-world experiments demonstrate that TF-VLA achieves robust zero-shot generalization, outperforming state-of-the-art baselines by 65\% on objects with unseen weights and 17\% on unseen geometries.

Overview
<figure>
  <img src="{{ '/images/fig-2.png' | relative_url }}" alt="Scenic view of mountains" loading="lazy">
  <figcaption>Figure 1 ¡ª A scenic mountain view.</figcaption>
</figure>
