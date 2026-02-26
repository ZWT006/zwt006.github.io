---
title: "Learning Agile and Robust Omnidirectional Aerial Motion on Overactuated Tiltable-Quadrotors"
date: 2026-02-24
layout: academic

# ── Hero metadata ────────────────────────────────────
authors: "<a href='https://zwt006.github.io' target='_blank'>Wentao Zhang</a><sup>1</sup>, Zhaoqi Ma<sup>1</sup>, <a href='https://jinjie.li/' target='_blank'>Jinjie Li</a><sup>1</sup>, <a href='https://why618188.github.io' target='_blank'>Huayi Wang</a><sup>2</sup>, Haokun Liu<sup>1</sup>, Junichiro Sugihara<sup>1</sup>, Chen Chen<sup>1</sup>, <a href='https://yichengchen.com/' target='_blank'>Yicheng Chen</a><sup>1</sup>, <a href='http://www.dragon.t.u-tokyo.ac.jp/author/moju-zhao/' target='_blank'>Moju Zhao</a><sup>1†</sup>"
affiliations: "<sup>1</sup>The University of Tokyo &nbsp;·&nbsp; <sup>2</sup>Shanghai Jiao Tong University &nbsp;&nbsp; <sup>†</sup>Corresponding Author"
venue: "Under Review 2026"

# ── Link buttons ─────────────────────────────────────
# paper_url:   "https://doi.org/..."
arxiv_url:   "https://arxiv.org/abs/2602.21583"
video_url:   "https://youtu.be/7oc55aLMC4U?si=wM8UVOdweMaUoPCf"
# summary_url: "https://youtu.be/..."    # short summary video
code_url:    "https://github.com/ut-dragon-lab/aerial_lab"

# ── Button accent color (hex, optional) ──────────────
btn_color: "#1a3a5c"

# ── Teaser: use teaser_image OR youtube_url, not both ─
# teaser_image: /images/omnirl/highlights.png
youtube_url: "https://www.youtube.com/embed/7oc55aLMC4U?si=4l4MFXZdMX6_6lID"
teaser_caption: >
  Our RL policy enables agile and robust full 6-DoF flight across diverse real-world scenarios: (a) waypoints hovering, (b) trajectory tracking, (c) external force recovery, (d) wind disturbance rejection, and (e) payload variation.

# ── BibTeX ───────────────────────────────────────────
bibtex: |
  @article{zhang2026omnirl,
    title   = {Learning Agile and Robust Omnidirectional Aerial Motion
               on Overactuated Tiltable-Quadrotors},
    author  = {Wentao Zhang and Zhaoqi Ma and Jinjie Li and Huayi Wang and Haokun Liu and Junichiro Sugihara and Chen Chen and Yicheng Chen and Moju Zhao},
    year={2026},
    eprint={2602.21583},
    archivePrefix={arXiv},
    primaryClass={cs.RO},
    url={https://arxiv.org/abs/2602.21583},
  }

# ── Post settings ────────────────────────────────────
math: true
categories: [research, aerial robotics]
tags: [reinforcement learning, tilt-rotor]
---

## Abstract

Tilt-rotor aerial robots enable omnidirectional maneuvering through thrust vectoring, but introduce significant control challenges due to the strong coupling between joint and rotor dynamics. While model-based controllers can achieve high motion accuracy under nominal conditions, their robustness and responsiveness often degrade in the presence of disturbances and modeling uncertainties. This work investigates **reinforcement learning** for omnidirectional aerial motion control on over-actuated tiltable quadrotors that prioritizes robustness and agility. We present a learning-based control framework that enables efficient acquisition of coordinated rotor-joint behaviors for reaching target poses in the $SE(3)$ space. To achieve reliable sim-to-real transfer while preserving motion accuracy, we integrate system identification with minimal and physically consistent domain randomization. Compared with a state-of-the-art NMPC controller, the proposed method achieves comparable six-degree-of-freedom pose tracking accuracy, while demonstrating superior robustness and generalization across diverse tasks, enabling zero-shot deployment on real hardware.

---

## Robot Platform

The **Beetle** tiltable quadrotor is equipped with four single-DOF tilt joints
(DYNAMIXEL XC330 servomotors) and four T-Motor AT2814 brushless rotors.
By actively rotating the joint angles, the thrust direction of each rotor can be independently
redirected, enabling full 6-DoF actuation in 3D space.

<!-- ![Robot platform hardware](/images/beetleomni/hardware.png) -->

---

## Method

### Reinforcement Learning Framework

We formulate the control problem as a **Partially Observable MDP (POMDP)** and train an
actor-critic policy using PPO (Proximal Policy Optimization) in Isaac Sim / Isaac Lab.

- **Action space (8-dim):** joint position targets $\boldsymbol{q}^{\ast}\_j \in \mathbb{R}^4$ + rotor thrust targets $\boldsymbol{f}^{\ast}\_r \in \mathbb{R}^4$
- **Observation (33-dim):** body velocities, relative target pose, current orientation,
  joint positions, previous actions
- **Asymmetric actor-critic:** the critic receives privileged rotor thrust and torque
  signals during training only

![RL framework overview](/images/omnirl/overframework.png)

### System Identification for Sim-to-Real

A key contribution is **physically consistent simulation** via system identification:

| Module | Model | Identified From |
|---|---|---|
| Rotor thrust & torque | Polynomial map: $(f, \tau) = g(\text{cmd}, V)$ | 6-axis F/T sensor measurements |
| Joint motor | 2nd-order transfer function $\frac{\omega\_n^2}{s^2+2\zeta\omega\_n s+\omega\_n^2}$ | Sin Wave-response experiments |
| System latency | Communication + estimation delays (3–5 $\mathrm{d}t$) | Timing measurements |

Rather than relying on heavy domain randomization, we randomize only **body mass, inertia,
and joint offsets**, preserving model fidelity while improving robustness.

<!-- ---

## Highlights

| | RL (Ours) | NMPC |
|---|---|---|
| Inference Time | **~0.3 ms** (30× faster) | ~10 ms |
| Mean Position Error | 0.077 m | **0.042 m** |
| Mean Orientation Error | **4.26°** | 4.35° |
| Wind disturbance (Position std) | **0.005m** | 0.028 |
| Wind disturbance (orientation std) | **0.63°** | 1.32° |
| Max payload (stable) | **1.0 kg** | 0.5 kg |
| Zero-shot deployment | ✓ | ✓ |
| Trajectory tracking (no extra training) | ✓ | — | -->

---

## Experiments

All policies are deployed **zero-shot** on real hardware against a state-of-the-art NMPC baseline.
The RL policy runs at **~0.3 ms** per inference step — over **30× faster** than NMPC (~10 ms).

### Waypoints Hovering

The robot sequentially reaches 5 predefined 6-DoF poses (3 repetitions).

| Target $\boldsymbol{p}^*$ [m] / $\boldsymbol{\theta}^*$ [°] | RL Pos (m) | RL Ori (°) | NMPC Pos (m) | NMPC Ori (°) |
|---|---|---|---|---|
| [0,0,0.8] / [0,0,0] | 0.114 | **2.59** | **0.026** | 2.64 |
| [1,0,1] / [45,0,0] | **0.060** | **4.35** | 0.074 | 4.37 |
| [0,1,1] / [0,−25,0] | **0.046** | **4.21** | 0.054 | 8.23 |
| [−1,0,1] / [−25,0,0] | 0.074 | 5.56 | **0.028** | **4.74** |
| [0,0,0.8] / [0,0,90] | 0.091 | 4.59 | **0.028** | **1.77** |
| **Mean** | 0.077 | **4.26** | **0.042** | 4.35 |

RL achieves **comparable position accuracy** and **better overall orientation accuracy**.
State trajectories reveal more **agile** behavior: RL peaks at **> 2 m/s** linear and **≈ 5 rad/s** angular velocity during transitions, with faster error convergence.

<!-- Waypoints clip: replace START/END with actual seconds, e.g. start=10&end=55 -->
<div class="video-wrapper" style="text-align: center">
  <iframe src="https://www.youtube.com/embed/7oc55aLMC4U?si=4l4MFXZdMX6_6lID&start=22&end=77&loop=1&playlist=7oc55aLMC4U&autoplay=1&mute=1"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen></iframe>
</div>

<div style="display:flex; gap:1rem; flex-wrap:wrap; align-items:flex-start;">
  <figure style="flex:1; margin:0; text-align:center;">
    <img src="/images/omnirl/waypointsPos.svg" alt="Position">
    <figcaption>Position</figcaption>
  </figure>
  <figure style="flex:1; margin:0; text-align:center;">
    <img src="/images/omnirl/waypointsAng.svg" alt="Orientation">
    <figcaption>Orientation</figcaption>
  </figure>
  <figure style="flex:1; margin:0; text-align:center;">
    <img src="/images/omnirl/waypointsVel.svg" alt="Velocity">
    <figcaption>Velocity</figcaption>
  </figure>
</div>

### Disturbance Rejection

The robot holds a fixed hover pose under two external disturbances:

- **Continuous wind (fan):** RL orientation fluctuation std **0.63°** vs NMPC **1.32°** — 2× more stable; position std **0.005 m** vs **0.028 m**.
- **Impulsive stick push:** RL recovers faster, with sharper but shorter velocity peaks and lower average velocity (0.025 vs 0.033 m/s linear; 0.081 vs 0.092 rad/s angular).

<!-- Disturbance clip: replace START/END with actual seconds -->
<div class="video-wrapper" style="text-align: center">
  <iframe src="https://www.youtube.com/embed/7oc55aLMC4U?si=4l4MFXZdMX6_6lID&start=79&end=108&loop=1&playlist=7oc55aLMC4U&autoplay=1&mute=1"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen></iframe>
</div>

<div style="display:flex; gap:1rem;flex-wrap:wrap; align-items:flex-start;">
  <figure style="flex:1; margin:0; text-align:center;">
    <img src="/images/omnirl/DisturbancePoseErr.svg" alt="Position Error">
    <figcaption>Position Error</figcaption>
  </figure>
  <figure style="flex:1; margin:0; text-align:center;">
    <img src="/images/omnirl/DisturbanceVel.svg" alt="Velocity">
    <figcaption>Velocity</figcaption>
  </figure>
</div>

<!-- ### Payload Adaptation -->

Stable hovering under additional payloads up to **1.0 kg** (RL) without re-tuning.
Increased payload shifts the vertical ($z$-axis) position offset while orientation accuracy remains stable for both controllers.

<!-- Payload clip: replace START/END with actual seconds -->
<div class="video-wrapper" style="text-align: center">
  <iframe src="https://www.youtube.com/embed/7oc55aLMC4U?si=4l4MFXZdMX6_6lID&start=109&end=112&loop=1&playlist=7oc55aLMC4U&autoplay=1&mute=1"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen></iframe>
</div>

### Trajectory Tracking *(Zero-Shot Generalization)*

Although trained **only for point-to-point pose reaching**, the policy generalizes to tracking a **3D lemniscate** with synchronized roll, pitch, and yaw modulation — zero additional training.

- Mean position error: 0.16 m (RL) vs 0.05 m (NMPC)
- Mean orientation error: 8.06° (RL) vs 5.19° (NMPC)
- **Comparable tracking stability:** position error std 0.04 vs 0.02 m; orientation error std **2.45° vs 2.46°**

> The RL policy behaves as a low-level feedback motion controller, enabling robust and stable tracking of dynamic trajectories well beyond its original training scope.

<!-- Tracking clip: replace START/END with actual seconds -->
<div class="video-wrapper" style="text-align: center">
  <iframe src="https://www.youtube.com/embed/7oc55aLMC4U?si=4l4MFXZdMX6_6lID&start=150&end=185&loop=1&playlist=7oc55aLMC4U&autoplay=1&mute=1"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen></iframe>
</div>

![trajectoryTrackingPose](/images/omnirl/trackingPose.svg)
![trajectoryTrackingPos](/images/omnirl/trackingPos.svg)
<div style="display:flex; gap:1rem;flex-wrap:wrap; align-items:flex-start;">
  <figure style="flex:1; margin:0; text-align:center;">
    <img src="/images/omnirl/trackingPoseErr.svg" alt="Position Error">
    <figcaption>Position Error</figcaption>
  </figure>
  <figure style="flex:1; margin:0; text-align:center;">
    <img src="/images/omnirl/trackingVel.svg" alt="Velocity">
    <figcaption>Velocity</figcaption>
  </figure>
</div>
