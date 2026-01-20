---
layout: home
title: "Visualization"
---

<style>
/* Grid that shows three columns on wide screens, then 2, then 1 */
.video-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  align-items: start;
  margin: 0;
}

/* Individual video item */
.video-item {
  margin: 0;
  text-align: center;
}

/* Make the video fill its grid cell while preserving aspect ratio */
.video-item video {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 6px;
  background: #000;
  aspect-ratio: 16 / 9;
  object-fit: contain;
}

/* Caption style */
.video-item figcaption {
  margin-top: 0.5rem;
  font-size: 0.9rem;
  color: #444;
}

/* Responsive breakpoints */
@media (max-width: 900px) {
  .video-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 520px) {
  .video-grid { grid-template-columns: 1fr; }
}
</style>

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
  <figcaption>Figure 1 A scenic mountain view.</figcaption>
</figure>
Data Collection
Grasp Task
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/grasp_small.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/Data_Collectgrasp_small.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Grasp small-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/grasp_mid.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/Data_Collectgrasp_mid.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Grasp medium-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/grasp_trials_mid.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/Data_Collectgrasp_trial_mid.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Grasp medium-sized box with trials</figcaption>
  </figure>
</div>
Reorient Task
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/small.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/Data_Collect_small.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Reorient small-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/mid.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/Data_Collect_mid.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Reorient medium-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/mid_trial_2.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/Data_Collect_box_mid_trial_2.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>Reorient medium-sized box with trial</figcaption>
  </figure>
</div>
Experiment Result
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/7.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/Reorient_1kg.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>(1) Reorient the box with increasing effort(1 kg)</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/8.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/Consecutive_grasp.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>(2) Consecutive Task</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/9.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/Cross_Embodiment.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>(3) Reorient medium-sized box with trial</figcaption>
  </figure>
</div>

(1)The model correctly identifies the failure of initial attempts and dynamically ramps up the virtual penetration until stable contact is verified, effectively "probing" for the necessary force.

(2)Leveraging subtask-grounding, the model generalizes from a single training roll to execute repetitive rolls. It continues until the label faces up, stopping precisely upon task completion.

(3)By carefully selecting kinematic anchor points to avoid finger interference, the humanoid successfully reorients the box using the retargeted trajectory.

Failure Cases
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/10.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/F_Insufficient_Effort.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>(1) Insufficient Force</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/11.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/F_Cant_Stop.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>(2) Termination Failure</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/12.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/F_Too_Much_Effort.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption>(3) False Negative & Excessive Force</figcaption>
  </figure>
</div>
(1) Insufficient Force: "The most common baseline failure mode is the generation of insufficient force, resulting in an inability to displace the box."

(2) Termination Failure: "Lacking awareness of task progress, the model learns the manipulation policy but fails to recognize the termination condition, causing it to continue acting after success."

(3) False Negative & Excessive Force: "Our policy occasionally exerts excessive force in unseen scenarios. For example, if a successful grasp is not detected by the vision system (false negative), the policy incorrectly initiates a retrial with increased effort, resulting in object damage."