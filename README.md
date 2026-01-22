# Awesome Medical World Models

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Last Update](https://img.shields.io/badge/last%20update-January%202025-blue)]()

> A curated list of **World Models for Healthcare**: prediction, simulation, counterfactual reasoning, and clinical decision support.


---

## Table of Contents

- [What is Medical World Model?](#what-is-medical-world-model)
- [Capability Levels (L1-L4)](#capability-levels-l1-l4)
- [Survey \& Review](#survey--review)
- [Papers by Application](#papers-by-application)
  - [Medical Imaging \& Diagnostics](#medical-imaging--diagnostics)
  - [Surgical Vision \& Robotics](#surgical-vision--robotics)
  - [Treatment Planning](#treatment-planning)
- [Capability Matrix](#capability-matrix)
- [Foundation World Models](#foundation-world-models)
- [Datasets \& Benchmarks](#datasets--benchmarks)
- [Open-Source Projects](#open-source-projects)
- [Reading Roadmap](#reading-roadmap)
- [Citation](#citation)

---

## What is Medical World Model?

A **World Model** is an internal simulator that learns environment dynamics. The core is learning the state transition function:

```
p(s_{t+1} | s_t, a_t)
```

Given current state `s_t` and action `a_t`, predict the next state `s_{t+1}`.

### Why Healthcare Needs World Models?

| Traditional AI | World Model |
|----------------|-------------|
| Static prediction: "This is a tumor" | Dynamic simulation: "How will the tumor evolve after treatment" |
| Single output | Multi-step rollout, visualize trajectory |
| Cannot answer what-if | Supports counterfactual reasoning |
| Black-box decision | Interpretable planning process |

### World Model vs Generative Model

```
Generative Model (e.g., Diffusion):
  Input: Noise → Output: Realistic image
  Goal: Visual fidelity

World Model:
  Input: State + Action → Output: Next state
  Goal: Dynamic consistency + Causal correctness
```

---

## Capability Levels (L1-L4)

Based on the capability framework proposed in [Qazi et al., 2025](https://arxiv.org/abs/2511.16333):

| Level | Name | Capability | Example |
|-------|------|------------|---------|
| **L1** | Temporal Prediction | Predict future states | Predict future medical images |
| **L2** | Action-Conditioned | Prediction conditioned on actions | Predict based on treatment/probe movement |
| **L3** | Counterfactual Rollouts | Counterfactual reasoning, decision support | "What if we use drug A instead of B?" |
| **L4** | Planning & Control | Closed-loop planning, real-time control | Autonomous surgical planning |

```
L1 ──────► L2 ──────► L3 ──────► L4
Temporal   Action     Counterfactual  Planning
Prediction Conditioned Rollouts       & Control
```

---

## Survey & Review

| Title | Venue | Year | Links |
|-------|-------|------|-------|
| **Beyond Generative AI: World Models for Clinical Prediction, Counterfactuals, and Planning** | NeurIPS Workshop | 2025 | [[PDF](https://arxiv.org/abs/2511.16333)] |

---

## Papers by Application

### Medical Imaging & Diagnostics

#### Radiology (X-ray / CT)

**X-WIN: Building Chest Radiograph World Model via Predictive Sensing.** [Nov 2025]<br>
*Zefan Yang, Ge Wang, James Hendler, Mannudeep K. Kalra, Pingkun Yan.*<br>
`L1-L2` `X-ray` `CT` `JEPA-style` `3D Knowledge Distillation`<br>
[[PDF](https://arxiv.org/abs/2511.14918)]

> Distills 3D knowledge from CT to 2D X-ray world model by predicting projections from different angles to learn 3D anatomical structures.

**CheXWorld: Exploring Image World Modeling for Radiograph Representation Learning.** [CVPR 2025]<br>
*Yang Yue, Yulin Wang, Chenxin Tao, Pan Liu, Shiji Song, Gao Huang.*<br>
`L1` `X-ray` `JEPA-style` `Representation Learning`<br>
[[PDF](https://arxiv.org/abs/2504.13820)]

> Uses JEPA-style predictive learning objectives to learn local anatomy, global layout, and domain variation representations from chest X-rays.

**Xray2Xray: World Model from Chest X-rays with Volumetric Context.** [Jun 2025]<br>
*Zefan Yang, Xinrui Song, Xuanang Xu, et al.*<br>
`L1` `X-ray` `Volumetric` `Projection Transition`<br>
[[PDF](https://arxiv.org/abs/2506.19055)]

> Learns 3D volumetric context by modeling projection transition dynamics.

---

#### MRI & Tumor Modeling

**CLARITY: Medical World Model for Guiding Treatment Decisions by Modeling Context-Aware Disease Trajectories in Latent Space.** [Dec 2025]<br>
*Tianxingjian Ding, Yuanhao Zou, Chen Chen, Mubarak Shah, Yu Tian.*<br>
`L4` `MRI` `Glioma` `Latent-space` `Treatment Planning` `Survival Analysis`<br>
[[PDF](https://arxiv.org/abs/2512.08029)] [[Project](https://dingtianxingjian.github.io/clarity-project-page/)]

> Models disease evolution trajectories in latent space, integrates temporal and clinical context, achieves prediction-to-decision closed-loop through inverse survival evaluation.

**MeWM: Medical World Model for Tumor Evolution Simulation.** [Jun 2025]<br>
*Yijun Yang, Zhao-Yang Wang, Qiuping Liu, et al.*<br>
`L3` `CT` `Tumor` `Diffusion-based` `Treatment Simulation`<br>
[[PDF](https://arxiv.org/abs/2506.02327)]

> Action-conditioned 3D generator that simulates post-treatment tumor states for protocol selection.

---

#### Ultrasound

**EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance.** [CVPR 2025]<br>
*Yang Yue, Yulin Wang, Haojun Jiang, Pan Liu, Shiji Song, Gao Huang.*<br>
`L2` `Ultrasound` `Cardiac` `Probe Guidance` `Motion-Aware`<br>
[[PDF](https://arxiv.org/abs/2504.xxxxx)]

> Motion-aware cardiac ultrasound world model that encodes anatomical structures and probe motion effects, reducing plane guidance error.

**Cardiac Copilot: Automatic Probe Guidance for Echocardiography with World Model.** [MICCAI 2024]<br>
*Haojun Jiang, Zhenguo Sun, Ning Jia, et al.*<br>
`L2` `Ultrasound` `Cardiac` `Navigation` `Real-time`<br>
[[PDF](https://arxiv.org/abs/2406.xxxxx)]

> Introduces "Cardiac Dreamer" world model where latent space features provide navigation maps for real-time probe guidance.

---

### Surgical Vision & Robotics

**Surgical Vision World Model.** [Sep 2025]<br>
*Saurabh Koju, Saurav Bastola, Prashant Shrestha, Sanskar Amgain, Yash Raj Shrestha, Rudra P.K. Poudel, Binod Bhattarai.*<br>
`L2-L3` `Surgical Video` `Latent Action` `da Vinci` `Unlabeled Data`<br>
[[PDF](https://arxiv.org/abs/2503.02904)] [[Github](https://github.com/bhattarailab/Surgical-Vision-World-Model)]

> First surgical vision world model that learns latent actions from unlabeled surgical videos, enabling action-controllable surgical data generation.

**World Models for General Surgical Grasping.** [May 2024]<br>
*Guangyao Lin, Xinyue Yan, Yuzhou Hu, et al.*<br>
`L4` `Surgical Robotics` `Grasping` `Reinforcement Learning` `Sim-to-Real`<br>
[[PDF](https://arxiv.org/abs/2405.17940)]

> World model-based reinforcement learning controller for general surgical grasping, robust to object variations and perturbations.

---

### Treatment Planning

**CLARITY** (see MRI & Tumor Modeling section above)<br>
`L4` `Treatment Planning` `Inverse Survival Evaluation`

**MeWM** (see MRI & Tumor Modeling section above)<br>
`L3` `Protocol Selection` `Action-Conditioned`

---

## Capability Matrix

A quick comparison of capability levels across papers:

| Paper | L1 | L2 | L3 | L4 | Domain | Architecture |
|-------|:--:|:--:|:--:|:--:|--------|--------------|
| CheXWorld | ✅ | | | | Radiology | JEPA |
| X-WIN | ✅ | ✅ | | | Radiology | JEPA |
| Xray2Xray | ✅ | | | | Radiology | Transformer |
| EchoWorld | | ✅ | | | Ultrasound | World Model |
| Cardiac Copilot | | ✅ | | | Ultrasound | WM + Nav |
| MeWM | | ✅ | ✅ | | Tumor/CT | Diffusion |
| CLARITY | | ✅ | ✅ | ✅ | MRI/Treatment | Latent Dynamics |
| Surgical Vision WM | | ✅ | ✅ | | Surgery | VQ-VAE + Transformer |
| WM-Grasp | | | | ✅ | Surgical Robotics | Dreamer-style |

---

## Foundation World Models

Foundational world model works from the general domain, essential for understanding medical applications:

| Paper | Year | Venue | Key Contribution |
|-------|------|-------|------------------|
| [World Models](https://arxiv.org/abs/1803.10122) | 2018 | NeurIPS | VAE + RNN architecture prototype |
| [Dreamer](https://arxiv.org/abs/1912.01603) | 2019 | ICLR | Latent imagination for RL |
| [DreamerV2](https://arxiv.org/abs/2010.02193) | 2020 | ICLR | Discrete latents |
| [MuZero](https://www.nature.com/articles/s41586-020-03051-4) | 2020 | Nature | Planning without environment model |
| [DreamerV3](https://arxiv.org/abs/2301.04104) | 2023 | ICLR | Mastering diverse domains |
| [A Path Towards AMI (JEPA)](https://openreview.net/pdf?id=BZ5a1r-kVsf) | 2022 | OpenReview | Predict latent, not pixels |
| [V-JEPA](https://arxiv.org/abs/2404.08471) | 2024 | arXiv | Video understanding via JEPA |
| [Genie](https://arxiv.org/abs/2402.15391) | 2024 | ICML | Generative interactive environments |

---

## Datasets & Benchmarks

| Dataset | Modality | Size | Task | Availability |
|---------|----------|------|------|--------------|
| [SurgToolLoc-2022](https://surgtoolloc.grand-challenge.org/) | Surgical Video | 24,695 clips | Tool Localization | 🔓 Public |
| [MIMIC-CXR](https://physionet.org/content/mimic-cxr/2.0.0/) | Chest X-ray | 377K images | Diagnosis | 🔐 Credentialed |
| [NLST](https://cdas.cancer.gov/nlst/) | Chest CT | 32K scans | Lung Screening | 🔐 Application |
| [MU-Glioma-Post](https://www.cancerimagingarchive.net/) | Brain MRI | 203 patients | Tumor Progression | 🔓 Public |
| [UCSF-ALPTDG](https://www.cancerimagingarchive.net/) | Brain MRI | 298 patients | Glioma Follow-up | 🔓 Public |
| [I-SPY2](https://www.ispytrials.org/) | Breast MRI + Clinical | Multi-center | Treatment Response | 🔐 Application |

---

## Open-Source Projects

| Project | Description | Code | Stars |
|---------|-------------|------|-------|
| Surgical Vision World Model | Action-controllable surgical video generation | [Github](https://github.com/bhattarailab/Surgical-Vision-World-Model) | ![](https://img.shields.io/github/stars/bhattarailab/Surgical-Vision-World-Model?style=social) |
| CLARITY | Treatment decision world model | 🔜 Coming Soon | - |
| CheXWorld | X-ray representation learning | 🔜 Coming Soon | - |

---

## Reading Roadmap

### For Beginners

```
Step 1: Understand World Model fundamentals
        ├── Ha & Schmidhuber, "World Models" (2018) ⭐ Must read
        └── LeCun, "A Path Towards Autonomous Machine Intelligence" (2022)

Step 2: Learn about medical applications
        └── Qazi et al., "Beyond Generative AI" (2025) ⭐ Must read

Step 3: Dive into specific areas based on interest
        ├── Medical Imaging → CheXWorld, X-WIN
        ├── Surgical Robotics → Surgical Vision WM, WM-Grasp
        └── Tumor Treatment → CLARITY, MeWM
```

### For Reproduction

| Paper | Code Availability | Difficulty | Framework |
|-------|-------------------|------------|-----------|
| Surgical Vision WM | ✅ Full | ⭐⭐ Medium | PyTorch |
| CheXWorld | ✅ Available | ⭐⭐ Medium | PyTorch |
| CLARITY | 🔜 Coming | ⭐⭐⭐ Hard | PyTorch |
| MeWM | ❓ Unknown | - | - |

---

## Citation

If this list is helpful for your research, please consider citing:

```bibtex
@misc{awesome-medical-world-models,
  author = {yuna022},
  title = {Awesome Medical World Models},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/yuna022/awesome-medical-world-models}
}
```

---

## Acknowledgments

Thanks to all paper authors for their contributions, and [awesome-medical-vision-language-models](https://github.com/yangzhou12/awesome-medical-vision-language-models) for format reference.

---

<div align="center">
  <b>Made with ❤️ for the Medical AI Community</b>
  <br><br>
  <a href="#awesome-medical-world-models">⬆️ Back to Top</a>
</div>
