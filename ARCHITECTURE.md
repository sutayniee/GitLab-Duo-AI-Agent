#  Technical Debt Hunter — System Architecture

##  Overview

The Technical Debt Hunter is an AI agent system built on the GitLab Duo Agent Platform that uses **GitLab Orbit as its structural reasoning layer** to detect, prioritize, and convert technical debt into actionable GitLab issues.

The system is designed as a **multi-layer agent architecture**:

> Orbit (structure) → Skills (analysis) → Actions (GitLab outputs)

---

##  High-Level Architecture

```plaintext id="arch_flow_001"
                ┌────────────────────────────┐
                │   GitLab Repository        │
                └────────────┬───────────────┘
                             │
                             ▼
                ┌────────────────────────────┐
                │     GitLab Orbit           │
                │ (Graph + Structure Layer)  │
                └────────────┬───────────────┘
                             │
                structural context (graph)
                             ▼
        ┌────────────────────────────────────┐
        │     Agent Core (AGENTS.md)         │
        │  - decision engine                │
        │  - prioritization logic           │
        └────────────┬───────────────────────┘
                     │
         invokes skills / workflows
                     ▼
        ┌────────────────────────────────────┐
        │        SKILLS Layer                │
        │  - debt detection                  │
        │  - hotspot analysis               │
        │  - dependency evaluation          │
        └────────────┬───────────────────────┘
                     │
                     ▼
        ┌────────────────────────────────────┐
        │   GitLab Duo Tools Layer          │
        │  - create issues                  │
        │  - MR analysis                   │
        │  - CI validation                 │
        └────────────┬───────────────────────┘
                     │
                     ▼
        ┌────────────────────────────────────┐
        │     GitLab Outputs                │
        │  - Issues                         │
        │  - MR comments                   │
        │  - Risk reports                  │
        └────────────────────────────────────┘