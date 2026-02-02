# Awesome Medical World Models

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Last Update](https://img.shields.io/badge/last%20update-January%202025-blue)]()

> A curated list of **World Models for Healthcare**: prediction, simulation, counterfactual reasoning, and clinical decision support.

---


## Table of Contents

- [What is Medical World Model?](#what-is-medical-world-model)
- [Capability Levels (L1-L4)](#capability-levels-l1-l4)
- [Survey \& Review](#survey--review)
- [Papers by Method](Papers-by-Method)
- [Papers by Application](#papers-by-application)
- [Capability Matrix](#capability-matrix)
- [Datasets \& Benchmarks](#datasets--benchmarks)
- [Open-Source Projects](#open-source-projects)

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
| **Machine Learning in Modeling Disease Trajectory and Treatment Outcomes: An Emerging Enabler for Model-Informed Precision Medicine** | Clinical Pharmacology & Therapeutics | 2024 | [[PDF](https://ascpt.onlinelibrary.wiley.com/doi/10.1002/cpt.3153)] [[PubMed](https://pubmed.ncbi.nlm.nih.gov/38105646/)] |

---

## Papers by Method

### 🧩Latent World Model
**Enhancing End-to-End Autonomous Driving with Latent World Model** [Jun 2024]<br>
*Yingyan Li, Lue Fan, Jiawei He, Yuqi Wang, Yuntao Chen, Zhaoxiang Zhang, Tieniu Tan*<br>
[[PDF](https://arxiv.org/abs/2406.08481)]

**DREAM TO CONTROL: LEARNING BEHAVIORS BY LATENT IMAGINATION** [Mar 2020]<br>
*Danijar Hafner, Timothy Lillicrap, Jimmy Ba, Mohammad Norouzi*<br>
[[PDF](https://arxiv.org/pdf/1912.01603v3)]

### 🧩Open-source Implementations                                                                    
**LingBot-World: Advancing Open-source World Models** [Jan 2026]<br>
*Robbyant Team (Zelin Gao, Qiuyu Wang, Yanhong Zeng, et al.)*<br>     
Open-source Diffusion Real-time Long-horizon MoE
[https://arxiv.org/abs/2601.20540]
[https://github.com/Robbyant/lingbot-world]

> Fully open-source world model with three-stage training (pre-train → knowledge injection → interaction readiness). Supports 10-minute video generation with sub-second latency, emergent spatial memory, and multi-modal control. Achieves SOTA on VBench. 

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
[[PDF](https://arxiv.org/abs/2504.13065)] [[Github](https://github.com/LeapLabTHU/EchoWorld)]

> Motion-aware cardiac ultrasound world model that encodes anatomical structures and probe motion effects, reducing plane guidance error.

**Cardiac Copilot: Automatic Probe Guidance for Echocardiography with World Model.** [MICCAI 2024]<br>
*Haojun Jiang, Zhenguo Sun, Ning Jia, et al.*<br>
`L2` `Ultrasound` `Cardiac` `Navigation` `Real-time`<br>
[[PDF](https://arxiv.org/abs/2406.13165)]

> Introduces "Cardiac Dreamer" world model where latent space features provide navigation maps for real-time probe guidance.

**Structure-aware World Model for Probe Guidance via Large-scale Self-supervised Pre-train.** [MICCAI 2024]<br>
*Haojun Jiang, Meng Li, Zhenguo Sun, et al.*<br>
`L2` `Ultrasound` `Cardiac` `Self-supervised` `Large-scale`<br>
[[PDF](https://arxiv.org/abs/2406.19756)]

> Large-scale self-supervised pre-training to acquire cardiac structure-aware world model using 1.36M echocardiograms.

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

**SurgWorld: Learning Surgical Robot Policies from Videos via World Modeling.** [Dec 2025]<br>
*Yufan He, Pengfei Guo, Mengya Xu, et al.*<br>
`L4` `Surgical Robot` `VLA` `Cosmos 2.5` `Policy Learning`<br>
[[PDF](https://arxiv.org/abs/2512.23162)]

> Builds surgical world model using Cosmos 2.5, infers pseudo-kinematics via inverse dynamics for training surgical VLA policies.

**Towards Suturing World Models: Learning Predictive Models for Robotic Surgical Tasks.** [Mar 2025]<br>
*Mehmet Kerem Turkcan, Mattia Ballo, Filippo Filicori, Zoran Kostic.*<br>
`L3` `Surgical` `Suturing` `Diffusion` `Video Prediction`<br>
[[PDF](https://arxiv.org/abs/2503.12531)] [[Project](https://mkturkcan.github.io/suturingmodels/)]

> Diffusion-based world models for surgical suturing, fine-tuned LTX-Video and HunyuanVideo for high-fidelity action sequences.

**World Model for AI Autonomous Navigation in Mechanical Thrombectomy.** [MICCAI 2025]<br>
*H. Robertshaw, HR. Wu, A. Granados, T.C. Booth.*<br>
`L4` `Catheter Navigation` `Thrombectomy` `TD-MPC2` `Reinforcement Learning`<br>
[[PDF](https://arxiv.org/abs/2509.25518)]

> TD-MPC2 world model for autonomous endovascular navigation, achieves 65% success rate vs SAC's 37%.

---

### Treatment Planning

**CLARITY** (see MRI & Tumor Modeling section above)<br>
`L4` `Treatment Planning` `Inverse Survival Evaluation`

**MeWM** (see MRI & Tumor Modeling section above)<br>
`L3` `Protocol Selection` `Action-Conditioned`

---

## Capability Matrix

| Paper | L1 | L2 | L3 | L4 | Domain | Architecture |
|-------|:--:|:--:|:--:|:--:|--------|--------------|
| CheXWorld | ✅ | | | | Radiology | JEPA |
| X-WIN | ✅ | ✅ | | | Radiology | JEPA |
| Xray2Xray | ✅ | | | | Radiology | Transformer |
| EchoWorld | | ✅ | | | Ultrasound | World Model |
| Cardiac Copilot | | ✅ | | | Ultrasound | WM + Nav |
| Structure-aware WM | | ✅ | | | Ultrasound | Self-supervised |
| MeWM | | ✅ | ✅ | | Tumor/CT | Diffusion |
| CLARITY | | ✅ | ✅ | ✅ | MRI/Treatment | Latent Dynamics |
| Surgical Vision WM | | ✅ | ✅ | | Surgery | VQ-VAE + Transformer |
| WM-Grasp | | | | ✅ | Surgical Robotics | Dreamer-style |
| SurgWorld | | | | ✅ | Surgical Robot | Cosmos 2.5 |
| Suturing WM | | | ✅ | | Surgical | Diffusion |
| Thrombectomy WM | | | | ✅ | Catheter Nav | TD-MPC2 |

---

## Datasets & Benchmarks

### Chest X-ray / CT Datasets

| Dataset | Size | Used By | Availability | Link |
|---------|------|---------|--------------|------|
| MIMIC-CXR | 377K images | X-WIN | 🔐 Credentialed | [PhysioNet](https://physionet.org/content/mimic-cxr/2.0.0/) |
| NLST | 32K CT scans | X-WIN, Xray2Xray | 🔐 Application | [CDAS](https://cdas.cancer.gov/nlst/) |
| NIH ChestX-ray14 | 112K images | CheXWorld, X-WIN | 🔓 Public | [NIH Box](https://nihcc.app.box.com/v/ChestXray-NIHCC) |
| CheXpert | 224K images | X-WIN, Xray2Xray | 🔓 Public | [Stanford AIMI](https://aimi.stanford.edu/datasets/chexpert-chest-x-rays) |
| VinDr-CXR | 18K images | CheXWorld, X-WIN | 🔓 Public | [PhysioNet](https://physionet.org/content/vindr-cxr/1.0.0/) |
| ShenZhen-CXR | 662 images | CheXWorld | 🔓 Public | [LHNCBC](https://data.lhncbc.nlm.nih.gov/public/Tuberculosis-Chest-X-ray-Datasets/Shenzhen-Hospital-CXR-Set/) |
| RSNA Pneumothorax | 12K images | CheXWorld | 🔓 Public | [Kaggle](https://www.kaggle.com/c/siim-acr-pneumothorax-segmentation) |
| RSNA Pneumonia | 30K images | X-WIN | 🔓 Public | [Kaggle](https://www.kaggle.com/c/rsna-pneumonia-detection-challenge) |
| JSRT | 247 images | X-WIN | 🔓 Public | [Kaggle](https://www.kaggle.com/datasets/raddar/nodules-in-chest-xrays-jsrt) |
| COVIDx | 30K+ images | X-WIN | 🔓 Public | [GitHub](https://github.com/lindawangg/COVID-Net) |

### Brain MRI / Tumor Datasets

| Dataset | Size | Used By | Availability | Link |
|---------|------|---------|--------------|------|
| MU-Glioma-Post | 203 patients, 654 MRIs | CLARITY | 🔓 Public | [TCIA](https://www.cancerimagingarchive.net/collection/mu-glioma-post/) |
| UCSF-ALPTDG | 298 patients, 596 MRIs | CLARITY | 🔓 Public | [UCSF Datasets](https://imagingdatasets.ucsf.edu/dataset/2) |
| I-SPY2 | Multi-center trial | CLARITY | 🔐 Application | [Quantum Leap Healthcare](https://www.quantumleaphealth.org/) |
| HCC-TACE-SEG | 105 patients | MeWM | 🔓 Public | [TCIA](https://www.cancerimagingarchive.net/collection/hcc-tace-seg/) |

### Surgical Video Datasets

| Dataset | Size | Used By | Availability | Link |
|---------|------|---------|--------------|------|
| SurgToolLoc-2022 | 24,695 clips | Surgical Vision WM | 🔓 Public | [Grand Challenge](https://surgtoolloc.grand-challenge.org/) |
| SAR-RARP50 | 50 videos | SurgWorld | 🔓 Public | [Synapse](https://www.synapse.org/#!Synapse:syn27618412) |
| AutoLaparo | 21 videos | SurgWorld | 🔓 Public | [GitHub](https://github.com/ziyiwangx/AutoLaparo) |
| GraSP | Surgical scenes | SurgWorld | 🔓 Public | [arXiv](https://arxiv.org/abs/2401.11174) |
| HeiCo | Colorectal surgery | SurgWorld | 🔓 Public | [Synapse](https://www.synapse.org/Synapse:syn21903917) |
| Multiypass140 | 140 videos | SurgWorld | 🔐 Request | [CAMMA](https://camma.unistra.fr/) |
| SurgicalActions160 | 160 videos | SurgWorld | 🔐 Request | [Publication](https://doi.org/10.1007/s11042-017-5252-2) |

### Simulation & Tools

| Resource | Description | Used By | Link |
|----------|-------------|---------|------|
| stEVE | Endovascular simulation framework | Thrombectomy WM | [GitHub](https://github.com/lkarstensen/stEVE) |
| SOFA | Physics simulation framework | Thrombectomy WM | [SOFA](https://www.sofa-framework.org/) |

### Datasets by Paper

<details>
<summary><b>X-WIN</b> - Click to expand</summary>

- **Training**: MIMIC-CXR (371K CXRs), NLST (32K CT scans)
- **Evaluation**: VinDr-CXR, CheXpert, NIH-CXR, RSNA, JSRT, COVIDx
</details>

<details>
<summary><b>CheXWorld</b> - Click to expand</summary>

- **Pre-training & Fine-tuning**: NIH ChestX-ray14
- **Fine-tuning**: VinDr-CXR, ShenZhen-CXR, RSNA Pneumothorax
</details>

<details>
<summary><b>Xray2Xray</b> - Click to expand</summary>

- **Training**: NLST (1,000 CT volumes)
- **Evaluation**: CheXpert
</details>

<details>
<summary><b>CLARITY</b> - Click to expand</summary>

- **Primary**: MU-Glioma-Post (203 patients, 654 MRI follow-ups)
- **External Validation**: UCSF-ALPTDG (298 patients)
- **Cross-disease**: I-SPY2 (breast cancer trial)
</details>

<details>
<summary><b>MeWM</b> - Click to expand</summary>

- **Training & Evaluation**: HCC-TACE-SEG (105 HCC patients, pre/post-TACE CT)
</details>

<details>
<summary><b>EchoWorld</b> - Click to expand</summary>

- **Training**: Proprietary (1M+ echocardiograms from 200+ scans)
</details>

<details>
<summary><b>Cardiac Copilot</b> - Click to expand</summary>

- **Training**: Proprietary (110 clinical scans, 151K sample pairs)
</details>

<details>
<summary><b>Structure-aware WM</b> - Click to expand</summary>

- **Training**: Proprietary (1.36M echocardiograms, 10 standard views)
</details>

<details>
<summary><b>Surgical Vision WM</b> - Click to expand</summary>

- **Training & Evaluation**: SurgToolLoc-2022
</details>

<details>
<summary><b>WM-Grasp</b> - Click to expand</summary>

- **Training**: Simulation environment
- **Evaluation**: Real robot with 5 types of surgical objects
</details>

<details>
<summary><b>SurgWorld</b> - Click to expand</summary>

- **SATA Dataset** (created by authors): 2,447 clips, 300K+ frames, 8 procedures
- **Source datasets**: GraSP, SAR-RARP50, Multiypass140, SurgicalActions160, AutoLaparo, HeiCo, YouTube surgical channels
</details>

<details>
<summary><b>Suturing WM</b> - Click to expand</summary>

- **Training**: 102 simulation training videos (~2K annotated clips)
</details>

<details>
<summary><b>Thrombectomy WM</b> - Click to expand</summary>

- **Simulation**: stEVE framework
- **Patient Data**: 10 CTA scans (UK REC 24/LO/0057)
</details>

---

## Open-Source Projects

| Project | Description | Code |
|---------|-------------|------|
| EchoWorld | Echocardiography probe guidance world model | [GitHub](https://github.com/LeapLabTHU/EchoWorld) |
| CheXWorld | X-ray representation learning | [GitHub](https://github.com/LeapLabTHU/CheXWorld) |
| Surgical Vision World Model | Action-controllable surgical video generation | [GitHub](https://github.com/bhattarailab/Surgical-Vision-World-Model) |
| MeWM | Medical world model for tumor evolution | [GitHub](https://github.com/scott-yjyang/MeWM) |
| stEVE | Endovascular simulation framework | [GitHub](https://github.com/lkarstensen/stEVE) |
| TD-MPC2 | Model-based RL for world models | [GitHub](https://github.com/nicklashansen/tdmpc2) |
| Suturing World Model | Predictive models for surgical suturing | [Project Page](https://mkturkcan.github.io/suturingmodels/) |
| CLARITY | Treatment decision world model | [Project Page](https://dingtianxingjian.github.io/clarity-project-page/) |
| LingBot-World | Open-source world model with real-time interaction   | [GitHub](https://github.com/Robbyant/lingbot-world) |
