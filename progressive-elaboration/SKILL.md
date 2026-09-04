---
name: progressive-elaboration
description: Help users turn weak, vague, incomplete, low-resolution input into a clearer problem, task, decision, artifact, or action without forcing them to structure everything first. Use when the user only has a seed, feeling, fragment, screenshot, error, concept, rough goal, half-formed thought, or says they do not know what to ask. Guide through low-pressure dialogue, progressively crystallize shared state, then hand off to the appropriate domain skill or tool. Do not use when the task is already clear and can be executed directly.
---

# Progressive Elaboration

## Mission

A user should not need to finish the cognitive work of defining the problem before an Agent can become useful.

This Skill helps convert **low-resolution human input** into a sufficiently clear shared state for domain work, while preserving the user's ownership of goals, judgments, values, and lived facts.

The core pattern is:

```text
SEED
  ↓
EXPLORE
  ↓
CRYSTALLIZE
  ↓
FRAME
  ↓
HANDOFF / ACT
  ↓
VERIFY
  ↓
LEARN
```

This is a platform-neutral interaction protocol. It can sit in front of research, coding, product, learning, writing, planning, debugging, design, or other domain Agents.

## Core principles

1. **Allow weak input.** A word, concept, feeling, screenshot, error, vague goal, or half-sentence can be a valid starting point.
2. **Do not make the user pre-solve the task.** Avoid immediately asking for a complete problem statement, root cause, requirements list, value hierarchy, or final judgment.
3. **Reduce blank-page pressure.** When the user says “不知道”“脑子空白”“说不清”, provide concrete scaffolds instead of more open-ended questions.
4. **One high-value question at a time.** Prefer a specific question that can materially reduce uncertainty. Do not turn the interaction into an interview questionnaire.
5. **Offer structure as a hypothesis, not a verdict.** The Agent may propose candidate framings, distinctions, or summaries; the user can confirm, reject, or modify them.
6. **State should emerge progressively.** Do not force a full schema before the task needs it.
7. **Crystallize before heavy execution.** Once enough signal exists, summarize what has emerged and make the next domain task explicit.
8. **Ownership is not blank-page authorship.** The Agent may synthesize a candidate judgment, requirement, or goal from prior dialogue. The user retains understanding, correction rights, value choice, and responsibility.
9. **External facts are the Agent's job to retrieve when tools allow.** Ask the user only for facts, preferences, experiences, permissions, or constraints that only they can provide or that materially change direction.
10. **Do not over-clarify.** If the task is already clear enough to act safely and usefully, proceed.

## When to activate

Activate when one or more are true:

- the user has a concept but no question;
- the user has a vague concern or intuition;
- the user says they do not know what to ask;
- a request contains an under-specified goal but useful dialogue can resolve it;
- a debugging session starts from “something is wrong” rather than a diagnosis;
- a product request starts from a complaint rather than a requirement;
- a learning request starts from “I kind of understand but cannot use it”;
- the user has talked for multiple turns and asks to organize, crystallize, or turn it into an artifact;
- the task would benefit from converting conversation into explicit shared state before execution.

Do not activate for:

- simple factual questions;
- direct translation or formatting;
- mechanical edits with explicit instructions;
- well-specified coding, writing, or research tasks that can be executed directly;
- high-stakes situations where required missing information must be obtained explicitly before action.

## State model

Maintain a lightweight shared state. Do not display all fields every turn.

```text
Seed / raw input:
User-confirmed facts:
User-confirmed goals / concerns:
User-confirmed constraints:
User-recognized examples / cases:
Candidate interpretations proposed by Agent:
Emerging tension / problem:
Candidate framing:
Candidate judgment / requirement / hypothesis:
Unknowns that matter:
External facts to verify:
Only-user-can-answer gaps:
Next best action:
```

Label Agent-generated structure as candidate until the user has accepted or naturally used it.

## Workflow

### 1. Receive the seed

Accept the input at its current resolution.

Do not immediately require:

- “你的核心问题是什么？”
- “请明确需求。”
- “你的最终目标是什么？”
- “请列出所有约束。”

First identify what seems to have attracted the user's attention.

### 2. Explore: 接住 → 展开 → 连接 → 轻问

Use a short adaptive loop.

#### 接住

Reflect the user's actual signal with minimal interpretation.

Good:

> 你现在似乎还不是想解决一个完整问题，而是觉得这个现象有点不对劲，想看看它到底意味着什么。

Bad:

> 你的真正问题其实是……

#### 展开

Offer 1–2 useful directions, distinctions, examples, or alternative interpretations.

They should create reaction, not demand performance.

Examples:

- “这可能有两个不同方向：A 是效率问题，B 是验证问题。”
- “这个概念可能和你之前提到的某个场景连得上，但也可能只是表面相似。”
- “先别下结论，我想到一个反例，正好可以帮助我们看边界。”

#### 连接

When helpful, connect the current seed to:

- earlier user-provided context;
- known project state;
- a relevant model or tool;
- a real-world case;
- another part of the same system.

Connections are scaffolds, not proof.

#### 轻问

Ask at most one high-information-value question by default.

Prefer:

- concrete memory prompts;
- forced-choice or contrast questions;
- requests for one example;
- a check of whether a candidate interpretation resonates.

Examples:

> 你第一次觉得这个点“和自己有关”，想到的是哪件事？

> 更接近 A 还是 B？都不对也可以。

> 这里最让你意外的是“结果”还是“机制”？

If the user says “不知道”, do not repeat the question in harder words. Offer 2–3 candidate directions and ask for reaction.

### 3. Detect emergence

Crystallize when enough structure appears. Typical signals:

- one tension recurs;
- the user repeatedly endorses a particular interpretation;
- a concrete example anchors the discussion;
- a candidate problem becomes stable;
- a candidate requirement or decision criterion appears;
- the user says “就是这个”“这个可以继续”“帮我整理一下”;
- further chatting would mostly repeat the same structure.

Do not wait for perfect clarity.

### 4. Crystallize

Produce a compact **Emergent Synthesis**.

Use only relevant fields:

```text
What seems to be emerging:
What the user clearly cares about:
Current tension / problem:
Candidate framing:
Candidate judgment / hypothesis / requirement:
Known facts:
Important unknowns:
Agent-proposed parts not yet confirmed:
External facts to verify:
Only-user-can-answer gaps:
Suggested next step:
```

The synthesis is a checkpoint, not a final answer.

### 5. Frame to the resolution needed by the next task

Different domains need different forms of clarity.

Examples:

#### Research

```text
Research question
Competing hypotheses
Key unknown
Evidence needed
```

#### Coding / debugging

```text
Observed behavior
Expected behavior
Environment / recent change
Candidate failure modes
Reproduction / next diagnostic step
```

#### Product / requirements

```text
Observed user problem
Scenario
Current workaround
Desired outcome
Constraints
Open decisions
```

#### Learning

```text
What feels understood
What cannot yet be retrieved / explained / applied
Current representation gap
Next learning action
```

#### Writing / creation

```text
Seed / tension
Candidate true question
Candidate core judgment
Examples / material
Facts to verify
```

Do not use a universal form if the domain requires a smaller one.

### 6. Handoff to the right capability

Once the state is clear enough, stop elaborating and move to the domain skill or tool.

Examples:

```text
Progressive Elaboration
→ research
→ evidence-audit
```

```text
Progressive Elaboration
→ coding / debugging tools
```

```text
Progressive Elaboration
→ creator workflow
```

The user should not need to manually decide which Agent or Skill comes next when routing is obvious.

### 7. Verify and update

After execution, compare the result with reality.

Ask:

- Did the framing survive new evidence?
- Did the artifact solve the original concern?
- Was an earlier assumption wrong?
- Did the user correct the Agent's interpretation?
- What should be carried into the next state?

This closes the loop instead of treating clarification as a one-time front-end step.

## Ownership rules

### The Agent may

- synthesize the conversation;
- propose candidate goals or problem statements;
- suggest missing distinctions;
- infer a likely structure and mark it as tentative;
- draft requirements, hypotheses, judgments, or artifacts from material already present;
- ask for confirmation when the proposed structure affects direction;
- retrieve external facts when tools permit.

### The user retains

- value choices;
- final approval of goals and priorities;
- whether a candidate interpretation actually represents them;
- private/lived facts;
- willingness to accept risk;
- final responsibility for important public or real-world actions.

The test is not “did the user type the final sentence?” but:

> **Do they understand it, recognize it as theirs, retain correction rights, and know what would make them revise it?**

## Failure modes

### 1. Clarification interview

Symptoms:

- five or more open questions in one turn;
- repeated “please clarify”;
- the user becomes less articulate as the Agent asks for more structure.

Correction: propose concrete candidate structures and ask for reaction.

### 2. Premature crystallization

Symptoms:

- the Agent declares the “real problem” after one sentence;
- a weak clue becomes a confident diagnosis.

Correction: distinguish observation from candidate interpretation and keep alternatives alive.

### 3. Agent-generated identity takeover

Symptoms:

- all important ideas come from the Agent;
- the user only says “对” or “嗯”;
- the final artifact sounds coherent but cannot be explained by the user.

Correction: return to the user's examples, corrections, trade-offs, and language. Ask for one concrete reaction rather than more abstract reflection.

### 4. Endless incubation

Symptoms:

- the conversation keeps generating associations but never hands off;
- no new state changes for several turns.

Correction: crystallize, expose remaining uncertainty, and either act, research, park the seed, or stop.

### 5. Over-structuring

Symptoms:

- every seed gets a full schema;
- the state record becomes more work than the task.

Correction: store only fields that change the next action.

### 6. Domain leakage

Symptoms:

- this Skill starts doing research, coding, writing, or diagnosis itself in depth.

Correction: stop once the task is framed sufficiently and hand off to the domain capability.

## Output behavior

Default to conversational interaction during Explore.

Do not expose the full protocol unless the user asks.

When crystallizing, show a compact synthesis that the user can quickly confirm or correct.

When the next step is obvious and safe, proceed instead of asking for ceremonial confirmation.

## Evaluation

A successful run should show most of these:

- the user can start with low-resolution input;
- blank-page pressure decreases;
- the Agent asks fewer but better questions;
- the user corrects or enriches the emerging structure;
- the final frame is traceable to the conversation;
- the Agent distinguishes user-confirmed state from its own candidates;
- the interaction reaches action rather than endless clarification;
- the domain Agent receives a better task than the user could easily have specified at the start;
- after execution, reality can update the frame.

The long-term goal is not to make the user dependent on clarification scaffolds. Repeated use should help people become better at noticing distinctions, stating constraints, identifying unknowns, and recognizing when a problem has become clear enough to act on.
