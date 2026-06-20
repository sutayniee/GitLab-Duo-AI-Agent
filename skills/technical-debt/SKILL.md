---
name: technical-debt
description: Analyze a mixed repository using GitLab Orbit and automatically generate actionable GitLab issues for technical debt.
---

# Technical Debt Analysis Skill

## Objective
Detect technical debt across a mixed-language repository and create GitLab issues automatically.

---

## Execution Flow

### Step 1: Gather Repository Context (via Orbit)

Use GitLab Orbit to analyze the repository graph:

- Identify relationships between files and modules
- Detect dependency chains and circular references
- Determine which files are frequently modified together
- Identify unused or disconnected components

Use this graph context (NOT just file scanning) to detect technical debt.

---

### Step 2: Identify Technical Debt

Detect the following:

#### 1. Large Files
- Files > 500 lines

#### 2. Complex Functions
- Functions > 50 lines
- Deep nesting

#### 3. Circular Dependencies
- Modules depending on each other

#### 4. Dead Code
- Files or functions not referenced anywhere

#### 5. Missing Tests
- Business-critical logic without tests

---

### Step 3: Prioritize Issues

Assign severity:

- HIGH → Core modules, circular dependencies, no tests
- MEDIUM → Large files, complex logic
- LOW → Minor structure issues

---

### Step 4: Create GitLab Issues

For EACH issue:

#### Title
[Tech Debt] <Short Problem Description>

#### Description
- Problem explanation
- Why it matters (impact)
- Evidence (files, modules)
- Suggested fix

#### Labels
- technical-debt
- severity::<low|medium|high>

---

## Example Output

### Issue
Title:
[Tech Debt] Refactor UserService (High Complexity)

Description:
- File exceeds 800 lines and contains multiple responsibilities
- High coupling with AuthModule and PaymentModule
- Difficult to maintain and test

Suggested Fix:
- Split into smaller services
- Introduce clear interfaces

---

## Key Rules

- Do NOT generate vague issues
- Do NOT duplicate findings
- Focus on actionable improvements
- Prefer fewer high-quality issues over many low-value ones

## Issue Creation Execution

After identifying issues:

1. For each issue, call GitLab API to create an issue.

2. Use the following structure:

- title: [Tech Debt] <summary>
- description: detailed explanation + suggested fix
- labels: technical-debt, severity::<level>

3. Ensure:
- No duplicate issues
- Only high-confidence findings are created