---
layout: home
title: "Project Overview"
---

<style>
/* 1. SECTION TITLE FONT SIZE */
h3 {
  font-size: 2.0rem !important; /* Adjust size as needed */
  margin-top: 2.5rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

/* 2. MERGED GREY PANEL CONTAINER */
.video-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  align-items: start;
  margin: 2rem 0;
  
  /* The grey background now lives here, creating one large panel */
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}

/* Individual video item (removed background from here) */
.video-item {
  margin: 0;
  text-align: center;
  /* No background here anymore */
}

/* Make the video fill its grid cell while preserving aspect ratio */
.video-item video {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 4px;
  background: #000;
  aspect-ratio: 16 / 9;
  object-fit: contain;
}

/* Caption style */
.video-item figcaption {
  margin-top: 0.8rem;
  font-size: 0.9rem;
  color: #333;
  font-weight: 500;
}

/* Responsive breakpoints */
@media (max-width: 900px) {
  .video-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 520px) {
  .video-grid { grid-template-columns: 1fr; }
}
</style>

# Virtual Penetration as a Force Proxy: Generating Synergistic Force-Aware Trajectories for Dual-Arm Manipulation

### Abstract

Deploying robotic systems in unstructured logistic environments is hindered by the challenge of manipulating heterogeneous objects under physical uncertainty. 
While dual-arm platforms offer the kinematic capacity to handle diverse geometries, existing control paradigms encounter substantial challenges. 
Reinforcement Learning (RL) policies often suffer from prohibitive sim-to-real gaps, while state-of-the-art Vision-Language-Action (VLA) models struggle with "tactile blindness" in force-aware, dual-arm manipulation tasks due to a lack of force-annotated datasets. 
To bridge this gap, we propose Virtual Force Grounded Vision-Language-Action model (VFG-VLA), a framework designed to learn force-sensitive manipulation without physical tactile feedback. 
Our approach introduces a novel data synthesis strategy that utilizes virtual penetration depth as a geometric proxy for contact force, converting low-cost, position-controlled trajectories into force-aware counterparts. 
Furthermore, we incorporate subtask grounding to enable the model to semantically reason about manipulation progress and modulate compressive force through iterative attempts. 
Extensive real-world experiments demonstrate that VFG-VLA achieves robust zero-shot generalization, outperforming state-of-the-art baselines by 65% on objects with unseen weights and 17% on unseen geometries.

---

### Overview
<figure>
  <img src="{{ '/images/fig-2.png' | relative_url }}" alt="TF-VLA Framework Overview" loading="lazy">
  <figcaption></figcaption>
</figure>

---

### Data Collection: Grasp Task
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/grasp_small.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/Data_Collectgrasp_small.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>Grasp small-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/grasp_mid.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/Data_Collectgrasp_mid.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>Grasp medium-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/grasp_trials_mid.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/Data_Collectgrasp_trial_mid.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>Grasp medium-sized box with trials</figcaption>
  </figure>
</div>

### Data Collection: Reorient Task
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/small.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/Data_Collect_small.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>Reorient small-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/mid.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/Data_Collect_mid.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>Reorient medium-sized box</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/mid_trial_2.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/Data_Collect_box_mid_trial_2.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>Reorient medium-sized box with trial</figcaption>
  </figure>
</div>

---

### Experiment Result
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/7.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/Reorient_1kg.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>(1) Reorient the box with increasing effort (1 kg)</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/8.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/Consecutive_grasp.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>(2) Consecutive Task</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/9.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/Cross_Embodiment.mp4' | relative_url }}" type="video/mp4"> 
    </video>
    <figcaption>(3) Cross Embodiment (Humanoid)</figcaption>
  </figure>
</div>

1. **Adaptive Force Probing:** The model correctly identifies the failure of initial attempts and dynamically ramps up the virtual penetration until stable contact is verified, effectively "probing" for the necessary force.
2. **Subtask Grounding:** Leveraging subtask-grounding, the model generalizes from a single training roll to execute repetitive rolls. It continues until the label faces up, stopping precisely upon task completion.
3. **Kinematic Retargeting:** By carefully selecting kinematic anchor points to avoid finger interference, the humanoid successfully reorients the box using the retargeted trajectory.

---

### Failure Cases
<div class="video-grid" role="list">
  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/10.png' | relative_url }}" aria-label="Demo video one">
      <source src="{{ '/videos/F_Insufficient_Effort.mp4' | relative_url }}" type="video/mp4"> 
    </video>
    <figcaption>(1) Insufficient Force</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/11.png' | relative_url }}" aria-label="Demo video two">
      <source src="{{ '/videos/F_Cant_Stop.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>(2) Termination Failure</figcaption>
  </figure>

  <figure class="video-item" role="listitem">
    <video controls preload="metadata" poster="{{ '/images/12.png' | relative_url }}" aria-label="Demo video three">
      <source src="{{ '/videos/F_Too_Much_Effort.mp4' | relative_url }}" type="video/mp4">
    </video>
    <figcaption>(3) False Negative & Excessive Force</figcaption>
  </figure>
</div>

1. **Insufficient Force:** The most common baseline failure mode is the generation of insufficient force, resulting in an inability to displace the box.
2. **Termination Failure:** Lacking awareness of task progress, the model learns the manipulation policy but fails to recognize the termination condition, causing it to continue acting after success.
3. **False Negative & Excessive Force:** Our policy occasionally exerts excessive force in unseen scenarios. For example, if a successful grasp is not detected by the vision system (false negative), the policy incorrectly initiates a retrial with increased effort, resulting in object damage.