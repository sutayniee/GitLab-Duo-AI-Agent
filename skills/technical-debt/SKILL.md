---
name: technical-debt
description: Analyze repository using Orbit and generate actionable GitLab issues for technical debt.
---

## Workflow

1. Query Orbit for:
   - Large files
   - Dependency graph
   - Test coverage

2. Identify:
   - Dead code
   - Circular dependencies
   - High complexity modules

3. Generate Issues:
   - Title: Clear problem
   - Description: Why it matters
   - Suggested fix

## Output Format

- Issue Title
- Affected Files
- Severity (Low, Medium, High)
- Recommendation