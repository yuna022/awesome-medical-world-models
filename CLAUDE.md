# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

Personal "awesome list" curating research papers on **Medical World Models** - AI systems that learn environment dynamics for healthcare applications. This is a documentation-only repository (README.md is the main content).

## L1-L4 Capability Framework

Based on [Qazi et al., 2025](https://arxiv.org/abs/2511.16333):

| Level | Name | Criteria |
|-------|------|----------|
| **L1** | Temporal Prediction | Predicts future states without action conditioning |
| **L2** | Action-Conditioned | Predictions depend on input actions/treatments |
| **L3** | Counterfactual Rollouts | Supports "what-if" analysis |
| **L4** | Planning & Control | Autonomous planning or real-time control |

## Adding a New Paper

Format in README.md under appropriate section:

```markdown
**Paper Title.** [Month Year] [Venue, Year]<br>
*Author1, Author2, et al.*<br>
`L{1-4}` `Domain` `Architecture`<br>
[[PDF](link)] [[Github](link)]

> One sentence description (optional)
```

Also update the Capability Matrix table and add any new datasets to Datasets & Benchmarks section.

## Inclusion Criteria

✅ Papers that **explicitly claim to be "World Models"** in their text

❌ Papers not explicitly claiming to be world models (even if technically similar)

## README Structure

- Papers organized by application domain (Radiology, MRI/Tumor, Ultrasound, Surgical)
- Capability Matrix shows L1-L4 levels for each paper
- Datasets section organized by modality with expandable per-paper details
- Open-Source Projects lists available code/project pages
