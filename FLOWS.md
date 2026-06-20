# 🔁 Technical Debt Hunter — Agent Flows

## Purpose

This document defines the **end-to-end execution workflows** of the Technical Debt Hunter Agent.

Each flow describes:
- triggers
- Orbit usage
- skill execution order
- decision-making logic
- GitLab outputs

---

# FLOW 1: Merge Request Risk Analysis (CORE FLOW)

## Trigger
- Merge Request opened OR updated

---

## Goal
Evaluate the risk of the MR using GitLab Orbit + skills, then:
- comment on MR OR
- create technical debt issues

---

## Execution Steps

### 1. Load MR Context
Use GitLab tool:
- `build_review_merge_request_context`

Extract:
- changed files
- diff summary
- affected modules

---

### 2. Orbit Graph Extraction (MANDATORY FIRST STEP)

Query GitLab Orbit for:

- dependency graph of changed files
- upstream/downstream dependencies
- module relationships

👉 Output: MR Impact Graph

---

### 3.  Run Skills

Execute skills in parallel:

#### Skill A: Dependency Blast Radius Analyzer
- determine how many systems are affected

#### Skill B: Circular Dependency Detector
- detect cycles involving changed files

#### Skill C: Change Hotspot Detector
- check if modified files are unstable

---

### 4. Risk Scoring Engine

Compute final MR risk score:

Inputs:
- blast radius
- cycle involvement
- hotspot status
- file centrality (Orbit)

Output:

| Score | Level |
|------|------|
| 80–100 | 🔴 Critical |
| 50–79  | 🟠 High |
| 20–49  | 🟡 Medium |
| 0–19   | 🟢 Low |

---

### 5. Decision Logic

#### If Critical:
- Post MR comment
- Create GitLab issue(s)
- Suggest blocking merge

#### If High:
- Post warning comment
- Create issue (optional)

#### If Medium:
- Comment only

#### If Low:
- No action OR minimal comment

---

### 6. Output Actions

- MR comment:
  > “This MR affects 6 downstream services via Orbit dependency graph.”

- GitLab issues:
  - refactoring tasks
  - dependency cleanup tasks

---

# FLOW 2: Repository Technical Debt Sweep

## Trigger
- Scheduled run OR manual invocation

---

## Goal
Scan entire repository for structural technical debt using Orbit.

---

## Execution Steps

### 1. Orbit Full Graph Load
- full repository dependency graph
- file relationships
- unreferenced nodes

---

### 2. Run Skills

Execute:

- Circular Dependency Detector
- Orphan Code Detector
- Dependency Blast Radius Analyzer
- Change Hotspot Detector

---

### 3. Aggregate Findings

Group findings into:

- Architectural debt
- Maintenance debt
- Stability risks

---

### 4. Prioritize Findings

Sort by:
- dependency centrality
- system impact
- risk score

---

### 5. GitLab Actions

For top findings:

- Create GitLab Issues:
  - “Refactor high-centrality module”
  - “Remove orphaned utilities”
  - “Break dependency cycle”

---

# FLOW 3: Hotspot Monitoring Flow

## Trigger
- Frequent changes detected in Orbit

---

## Goal
Detect unstable modules early.

---

## Execution Steps

### 1. Orbit Hotspot Query
- fetch change frequency signals

---

### 2. Run Skill
- Change Hotspot Detector

---

### 3. Risk Evaluation

If:
- high change frequency + high dependency centrality

→ classify as critical instability zone

---

### 4. Action

- Create “Stability Risk” issue
- Suggest refactoring into smaller modules

---

# DESIGN PRINCIPLES

## 1. Orbit First
No flow starts without Orbit context.

---

## 2. Skill Composition
Flows are NOT logic-heavy.
They orchestrate skills only.

---

## 3. Deterministic Execution
Same input → same outputs.

---

## 4. Action-Oriented Output
No flow ends with “analysis only”.

Every flow produces:
- MR comments OR
- GitLab issues OR
- both

---
# 🏁 End Goal

Transform GitLab into a system that continuously:

> detects architectural risk, prioritizes it using graph intelligence, and converts it into engineering work automatically.