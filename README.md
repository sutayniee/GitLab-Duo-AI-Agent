# Technical Debt Hunter

### AI-Powered GitLab Agent using GitLab Orbit

---

## Overview

**Technical Debt Hunter** is an AI-powered GitLab Duo Agent that automatically detects technical debt in your repository and creates actionable GitLab issues instantly.

Instead of manually auditing codebases, developers can run a single command:

```
Analyze technical debt
```

and receive automatically generated issues highlighting the most critical problems.

---

## Problem

Developers often inherit or work in large, evolving codebases where:

* Risky modules are difficult to identify
* Large, complex files go unnoticed
* Missing tests are overlooked
* High coupling increases fragility

Manual analysis is:

* Time-consuming
* Inconsistent
* Easy to ignore

---

## Solution

Technical Debt Hunter uses **GitLab Orbit** to understand your repository structure and automatically:

* Identifies technical debt
* Prioritizes high-impact issues
* Generates clear, actionable GitLab issues
* Integrates directly into developer workflows

---

## How It Works

### 1. Trigger the Agent

```
Analyze technical debt
```

---

### 2. Query GitLab Orbit

The agent retrieves structured repository data such as:

* File sizes and line counts
* Dependency relationships
* Test coverage indicators

---

### 3. Analyze Technical Debt

The system detects:

* Large files greater than 500 lines
* Files without tests
* Highly coupled modules

---

### 4. Create GitLab Issues

For each finding, the agent automatically creates:

* Issue title
* Detailed description
* Labels such as `technical-debt` and `high`

---

## Example Output

Instead of:

> "Your code needs refactoring..."

You get:

* `Refactor UserService.ts (High Complexity)`
* `Add tests for PaymentProcessor.ts`
* `Reduce coupling in OrderManager.ts`

---

## Architecture

```
User Command
   ↓
GitLab Duo Agent Flow
   ↓
GitLab Orbit Query
   ↓
AI Analysis (LLM)
   ↓
GitLab Issue Creation
```

---

## Tech Stack

* GitLab Duo Agent Platform (YAML-based flows)
* LLM-powered analysis
* GitLab Orbit (repository intelligence)
* GitLab Issue API

---

## Key Features

* One-command execution
* Deep repository understanding via Orbit
* Automated issue generation
* High-impact prioritization
* Seamless GitLab integration

---

## Use Cases

* Onboarding into legacy codebases
* Continuous technical debt monitoring
* Sprint planning automation
* Codebase health audits

---

## Why This Matters

Technical debt slows down development, introduces bugs, and increases maintenance costs.

Technical Debt Hunter transforms this from:

Manual, reactive work
to
Automated, proactive insights

---

## Hackathon Context

Built for the **GitLab Transcend Hackathon (Showcase Track)**.

This project demonstrates:

* Meaningful use of **GitLab Orbit**
* A functional **AI agent workflow**, not just chat
* Real-world developer impact

---

## Future Improvements

* Risk scoring system
* Trend tracking over time
* Continuous monitoring through CI integration
* Smarter dependency analysis
* Team-based ownership insights

---

## Demo

Run the agent and watch GitLab issues appear automatically.

---

## Contributors

* Lumampao, Eugene S.
* Villamil, Paul lewis J.
* Rodriguez, Lebron James

# Special Thanks to
* Haban, Charrisa Althea I.

---

## License

MIT License

---

## Final Note

Technical Debt Hunter does not just find problems; it turns them into actionable work instantly.
