# Workbench Notes — future visualization of progressive elaboration

These notes are **not** a product requirement and should not trigger immediate implementation. They capture architectural ideas for a future Codex/Agent workbench after enough real cases exist.

## 1. Product principle

Do not design the workbench as an Agent launcher.

Avoid a home screen dominated by buttons such as:

```text
Research Agent
Writing Agent
Product Agent
Coding Agent
...
```

The primary object should be:

> **the thing the user is currently trying to understand, make, decide, debug, or move forward.**

Agents and Skills are backstage capabilities selected from state.

## 2. State-driven, not process-driven

Prefer:

```text
What is already known?
What has the user confirmed?
What is still uncertain?
What candidate interpretations exist?
What is the next highest-value action?
What artifact or action has been produced?
What did reality say back?
```

over:

```text
Step 1 complete
Please fill Step 2
Please fill Step 3
```

The workflow should exist internally, while the UI only exposes the state and next useful action.

## 3. Candidate shared state

A future workspace may expose a subset of:

```text
Seed
User-confirmed facts
User-confirmed goals / concerns
Constraints
Examples / cases
Candidate interpretations
Emerging problem / tension
Current framing
Thinking route
Evidence
Unknowns
Candidate judgment / requirement
Next action
Artifact
Reality feedback
State updates
```

Not every domain needs every field.

## 4. Example UI behavior

A user enters:

> 今天学到“托付”，感觉挺有意思。

The workbench could progressively surface:

```text
🌱 Seed
托付可能和高薪有关

🔗 Connections
组织为什么愿意把重要事情交给某些人
降低不确定性
职业价值

💭 Emerging ideas
高薪买的也许不只是技能

❓ Emerging question
为什么有些人技术不是最强，却越来越值得组织托付？

🔎 Need evidence
高薪与责任范围 / 决策权是否存在可靠证据

🧠 Thinking
尚未正式路由

📦 Artifact
尚未形成
```

As dialogue continues, this state updates without requiring the user to maintain forms manually.

## 5. Routing model

A useful long-term architecture may look like:

```text
Human
  ↓
low-resolution input
  ↓
Progressive Elaboration
  ↓
Shared State
  ↓
Router
  ├─ Thinking Engine
  ├─ Research / Evidence
  ├─ Coding / Debugging
  ├─ Product / Requirements
  ├─ Learning
  ├─ Creator
  └─ other domain Skills
  ↓
Artifact / Action
  ↓
Reality
  ↓
State Update
```

The user should not need to choose the correct Agent first.

## 6. Implementation constraint

Do not build this from imagination alone.

Before implementing a substantial workbench, collect roughly 5–10 real cases across one or more workflows and observe:

- which state fields recur;
- which state transitions actually matter;
- which actions repeat often enough to deserve buttons or commands;
- where users lose context;
- what needs visualization versus plain dialogue;
- which data should persist;
- which steps should stay invisible.

The future workbench should be a visualization of a validated workflow, not a workflow invented to justify a dashboard.

## 7. Relationship to Lumos direction

The workbench should support a human-as-principal model:

> AI reduces the cost of externalizing, structuring, researching, testing, and executing thought, while the human retains goals, values, correction rights, and responsibility.

A successful workbench should make it easier to begin from ambiguity and easier to see how a thought became a problem, a decision, an artifact, an action, and eventually a revised understanding.
