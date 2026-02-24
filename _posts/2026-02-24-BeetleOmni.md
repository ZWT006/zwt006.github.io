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
arxiv_url:   "https://arxiv.org/abs/..."
video_url:   "https://youtu.be/..."
# summary_url: "https://youtu.be/..."    # short summary video
code_url:    "https://github.com/ZWT006"

# ── Button accent color (hex, optional) ──────────────
btn_color: "#1a3a5c"

# ── Teaser: use teaser_image OR youtube_url, not both ─
teaser_image: /images/omnirl/highlights.png
teaser_caption: >
  Our RL policy enables agile and robust full 6-DoF flight across diverse real-world scenarios:
  (a) waypoints hovering, (b) trajectory tracking, (c) external force recovery, (d) wind disturbance rejection, and (e) payload variation.

# ── BibTeX ───────────────────────────────────────────
bibtex: |
  @article{zhang2026omnirl,
    title   = {Learning Agile and Robust Omnidirectional Aerial Motion
               on Overactuated Tiltable-Quadrotors},
    author  = {Zhang, Wentao and Ma, Zhaoqi and Li, Jinjie and Wang, Huayi
               and Liu, Haokun and Sugihara, Junichiro and Chen, Chen
               and Chen, Yicheng, Moju Zhao},
    journal = {arXiv preprint},
    year    = {2026}
  }

# ── Post settings ────────────────────────────────────
math: true
categories: [research, aerial robotics]
tags: [reinforcement learning, tilt-rotor]
---

## Abstract

Tilt-rotor aerial robots enable omnidirectional maneuvering through thrust vectoring, but introduce significant control challenges due to **strong coupling between joint and rotor dynamics**.
While model-based controllers achieve high accuracy under nominal conditions, their robustness degrades in the presence of disturbances and modeling uncertainties. 
We present a **reinforcement learning (RL) framework** for agile and robust omnidirectional aerial motion control on an overactuated tiltable quadrotor. 
A single learned policy outputs coordinated joint position commands and rotor thrust commands to reach arbitrary target poses in the **SE(3)space**. 
To achieve reliable sim-to-real transfer while preserving accuracy, we integrate **system identification** with minimal, physically consistent domain randomization.
Compared with a state-of-the-art NMPC controller, the proposed method achieves comparable 6-DoF pose tracking accuracy while demonstrating **superior robustness, agility, and 30× faster inference** across diverse tasks, enabling zero-shot deployment on real hardware.

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
| System latency | Communication + estimation delays (3–5 ms) | Timing measurements |

Rather than relying on heavy domain randomization, we randomize only **body mass, inertia,
and joint offsets**, preserving model fidelity while improving robustness.

---

## Experiments

All policies are deployed **zero-shot** on the real hardware without any fine-tuning.
Comparisons are made against an NMPC controller implemented following [Li et al., 2024].

### Waypoints Hovering

The robot sequentially reaches 5 predefined 6-DoF target poses (repeated 3 times). The RL policy achieves **comparable position accuracy** and **better orientation accuracy**.
State trajectories show RL reaches higher peak velocities (> 2 m/s linear, ~5 rad/s angular),
confirming more **agile transient behavior**.

<!-- | Controller | Mean Position Error | Mean Orientation Error |
|---|---|---|
| **RL (Ours)** | 0.077 m | **4.26°** |
| NMPC | **0.042 m** | 4.35° | -->

<!-- ![Waypoints state trajectories](/images/beetleomni/waypoints.png) -->

### Disturbance Rejection

The robot hovers stably while subjected to (1) continuous wind from a fan and
(2) impulsive stick pushes.

- **Wind:** RL shows lower orientation fluctuation (std 0.63° vs 1.32°) with tighter velocity response.
- **Stick push:** RL recovers to target pose faster with sharper, shorter velocity peaks.

<!-- ![Disturbance rejection results](/images/beetleomni/disturbance.png) -->

### Payload Adaptation

The robot maintains stable hovering under additional payloads up to **0.25 kg × 4** without
re-tuning. Increasing payload primarily increases vertical ($z$-axis) position offset while
orientation accuracy remains stable — consistent for both RL and NMPC.

### Trajectory Tracking

Although trained **only for pose reaching**, the RL policy generalizes to tracking a 3D
lemniscate trajectory with simultaneous roll, pitch, and yaw modulation — zero additional training required.

<!-- ![Trajectory tracking (3D lemniscate)](/images/beetleomni/tracking.png) -->



<!-- ![Payload experiments](/images/beetleomni/payload.png) -->

---

<!-- ## Comparison Summary

| Capability | RL (Ours) | NMPC |
|---|---|---|
| Position accuracy | Comparable | ✓ Slightly better |
| Orientation accuracy | ✓ Better | — |
| Agility (convergence speed) | ✓ More agile | — |
| Disturbance rejection | ✓ Better (moderate) | — |
| Inference time | ✓ **~0.3 ms** | ~10 ms |
| Zero-shot deployment | ✓ | ✓ |
| Payload adaptation | ✓ 0.5 kg × 2 | Limited | -->
