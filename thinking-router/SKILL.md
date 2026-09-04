---
name: thinking-router
description: Route non-trivial questions to a small set of high-leverage thinking tools after first modeling the real problem. Use for analysis, decisions, learning, strategy, career, business, organizations, complex systems, and life questions when the user should not need to name the model first. Choose one main tool and at most three complementary or adversarial tools, separate models from evidence, and end with action or update conditions. Do not use for simple factual, translation, formatting, or mechanical tasks.
---

# Thinking Router

## Mission

Help a person **think better without requiring them to know the right model name first**.

The goal is not to display a library of frameworks. The goal is to change one of these when useful:

- the representation of the problem;
- the decision criterion;
- the causal/mechanistic explanation;
- the action set;
- the risk boundary;
- the condition under which the current judgment should be revised.

If a model does none of these, do not use it.

## Core operating rule

```text
model the problem
  ↓
choose 1 main tool
  ↓
add ≤3 complementary / adversarial tools only when they do different jobs
  ↓
compare against evidence and reality
  ↓
form a provisional judgment
  ↓
state action / test / update conditions
```

## 1. Build the minimal problem map first

For a non-trivial task, quickly identify only the dimensions that can change the answer:

```text
Objective       what are we actually trying to explain, choose, predict, create, or change?
Value           what counts as better, and which value choices belong to the user?
Hard constraints what cannot be wished away: physics, rules, resources, irreversibility, other agents?
Time scale      one-shot, repeated game, long-term compounding, or system evolution?
State / feedback where are we now and how quickly does feedback arrive?
Key unknown     which unknown is most likely to change the current judgment?
Failure modes   what is the most common, costly, or hard-to-recover failure?
```

Do not force all seven fields into the visible answer. Use them internally and surface only what matters.

## 2. Select tools by job, not by keyword

A tool should occupy a clear workstation:

- **Frame** — redefine the question or objective.
- **Bound** — reveal constraints, irreversibility, or survival conditions.
- **Estimate** — reason under uncertainty, distributions, base rates, or information limits.
- **Explain** — identify mechanism, incentives, mediators, feedback, or selection effects.
- **Generate** — create options, experiments, paths, or adjacent moves.
- **Counteract** — find second-order effects, gaming, unintended consequences, or adversarial response.
- **Learn** — turn action into feedback, practice, or transfer.
- **Value** — clarify what should be optimized and whether the user is winning the wrong game.

### Selection rules

1. Choose **exactly one main tool** when a model is genuinely useful.
2. Add at most **three** supplementary tools.
3. Supplementary tools should do different jobs.
4. Prefer one **heterogeneous counter-tool** when the conclusion is important.
5. If deleting a tool leaves the reasoning and action unchanged, remove it.
6. If a plain explanation is better, use the plain explanation.

## 3. Recommended tool families

Read `references/tool-index.md` when the model space is not obvious.

Typical routing examples:

```text
uncertain career / new venture
→ game selection or objective function
→ effectuation / optionality
→ adjacent possible
→ reference class or non-ergodicity as a check

risk / bet / irreversible commitment
→ Bayesian or reference class
→ Kelly / non-ergodicity / fragility

learning / skill transfer
→ ICAP or cognitive load
→ deliberate practice / desirable difficulty / hugging vs bridging

incentive / organization / metrics
→ principal-agent or incentive compatibility
→ Goodhart
→ unintended consequences / verifiability

complex product / strategy
→ Wardley mapping or state leverage
→ bottleneck / feedback loop
→ adjacent possible / minimum viable ecosystem

life direction
→ objective function
→ second-order volition
→ exploration-exploitation / adjacent possible
```

These are defaults, not mandatory bundles.

## 4. Models do not count as evidence

Always distinguish:

- user-provided facts;
- externally verifiable facts;
- model inference;
- scenario assumptions;
- value premises.

Fixed discipline:

> **Models generate questions, structures, hypotheses, and distinctions. Evidence and reality decide whether the claims are true enough to use.**

If the task depends materially on external evidence, hand off to a research capability.

Do not search only for evidence that supports the selected model. Generate at least one competing explanation when the claim matters.

## 5. Run the mechanism

Do not stop at naming the tool.

For the main tool, show the smallest useful causal / decision mechanism, for example:

```text
current state
→ mechanism / constraint
→ consequence
→ trade-off
→ action implication
```

For supplementary tools, explain only the incremental contribution.

## 6. Adversarial check

Before finalizing an important judgment, ask some of:

- Is there a simpler explanation?
- Is the base rate or reference class different from the story we are telling?
- Is this correlation being treated as causation?
- Is there selection or survivorship bias?
- Does the average outcome hide a path that could ruin this individual?
- Could the metric be gamed?
- What second-order response appears after people adapt?
- Are we optimizing the wrong objective?
- Does this model merely redescribe common sense?
- What evidence would make the current judgment weaker or false?

Do not manufacture disagreement just to look balanced.

## 7. Output contract

For a substantial question, a strong answer usually contains:

```text
Bottom line
Problem model / reframing
Main tool and why it changes the analysis
Key mechanism / trade-off
Best competing explanation or adversarial check
Action / experiment / next move
Update condition
```

The visible answer does not need to expose every model name. Backend complexity, frontend simplicity.

## 8. Stop rules

Stop adding tools when:

- the problem representation is already clear;
- additional tools only repeat the same conclusion;
- more theory will not change action;
- evidence is now the bottleneck;
- the question is simple enough for a plain answer.

If the selected framework does not improve judgment, withdraw it.

## 9. Learning and internalization

The long-term goal is not permanent dependence on routing.

After a real case, only when a model truly mattered, record:

```text
What triggered this model?
What did it change?
What was the strongest competing / counter-tool?
Where did it fail or need a boundary?
What real case now anchors it?
```

Keep the original/source definition separate from the user's personal understanding. Let the personal layer grow through real cases.

## 10. Relationship to other Lumos capabilities

Typical composition:

```text
progressive-elaboration
→ thinking-router
→ research / evidence-audit when facts matter
→ domain workflow (creator / product / coding / learning)
→ reality feedback
```

`thinking-router` is a reasoning engine, not a universal Agent and not a replacement for domain execution.