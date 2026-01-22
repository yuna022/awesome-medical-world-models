# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a personal "awesome list" curating research papers on **Medical World Models** - AI systems that learn environment dynamics for healthcare applications including prediction, simulation, counterfactual reasoning, and clinical decision support.

## Repository Structure

```
├── README.md                    # Main paper list and documentation
└── resources/
    ├── reading-roadmap.md       # Learning paths for different backgrounds
    └── datasets.md              # Dataset information for training/evaluation
```

## L1-L4 Capability Framework

Papers are classified by capability level (from Qazi et al., 2025):

| Level | Name | Criteria |
|-------|------|----------|
| **L1** | Temporal Prediction | Predicts future states without action conditioning |
| **L2** | Action-Conditioned | Predictions depend on input actions/treatments |
| **L3** | Counterfactual Rollouts | Supports "what-if" analysis, comparing scenarios |
| **L4** | Planning & Control | Autonomous planning or real-time control |

## Adding a New Paper

Use this format in README.md under the appropriate application section:

```markdown
**Paper Title.** [Month Year] [Venue, Year]<br>
*Author1, Author2, Author3, et al.*<br>
`L{1-4}` `Domain` `Architecture`<br>
[[PDF](link)] [[Github](link)]

> One sentence describing the contribution (optional)
```

**Application domains:** Medical Imaging, Surgical Vision & Robotics, Treatment Planning

**Architecture tags:** JEPA-style, Diffusion-based, Transformer, VAE/Latent Dynamics, GAN

## Inclusion Criteria

✅ Include: Papers that **explicitly claim to be "World Models"**, model state transition dynamics p(s_{t+1} | s_t, a_t), applied to medical/clinical scenarios

❌ Exclude: Papers not explicitly claiming to be world models, static diagnosis models, pure image generation without dynamics
