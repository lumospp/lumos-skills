<div align="center">

# 🧰 Lumos Skills

**Platform-neutral Agent Skills for reliable research and reasoning**

Built on the open **Agent Skills** format and packaged for Claude Code without forking the core skills.

</div>

`lumos-skills` is the public distribution repository for reusable Agent Skills that have been tested in real workflows.

The goal is not to collect prompts. The goal is to turn useful cognitive methods into **portable, installable, auditable capabilities**.

Current focus: research reliability — helping agents search fast without confusing a plausible story with evidence.

---

## Skills

| Skill | Purpose | Release |
|---|---|---|
| 🔬 [`research`](./research) | Evidence-first L1 research: understand the best currently defensible knowledge about an object | V0.3 |
| 🧪 [`evidence-audit`](./evidence-audit) | Audit whether important claims are actually supported by their evidence | V0.2 |

Each top-level skill directory is the **canonical, platform-neutral source**.

```text
lumos-skills/
├── research/
│   ├── SKILL.md
│   └── references/
├── evidence-audit/
│   └── SKILL.md
├── .claude-plugin/
│   └── marketplace.json
└── docs/
    └── ARCHITECTURE.md
```

The core format follows the Agent Skills standard: `SKILL.md` is required; `references/`, `scripts/`, and `assets/` are optional supporting directories.

→ [Architecture and portability rules](./docs/ARCHITECTURE.md)

---

## Install

### Claude Code — Marketplace

Add the Lumos marketplace once:

```text
/plugin marketplace add lumospp/lumos-skills
```

Then install the research bundle:

```text
/plugin install lumos-research@lumos-skills
```

The bundle currently exposes:

```text
/lumos-research:research
/lumos-research:evidence-audit
```

This packaging does **not** contain duplicate Claude-only copies. The marketplace points directly at the same canonical `research/` and `evidence-audit/` directories used by other Agent Skills clients.

### Claude Code — direct standalone Skill

If you prefer an un-namespaced standalone Skill, you can still give Claude Code the directory URL directly:

```text
帮我安装这个 Skill：
https://github.com/lumospp/lumos-skills/tree/main/research
```

or:

```text
帮我安装这个 Skill：
https://github.com/lumospp/lumos-skills/tree/main/evidence-audit
```

Standalone installation typically gives `/research` and `/evidence-audit` rather than plugin namespaces.

### Codex / other Agent Skills clients

Use the same canonical Skill directories:

```text
https://github.com/lumospp/lumos-skills/tree/main/research
https://github.com/lumospp/lumos-skills/tree/main/evidence-audit
```

OpenAI Skills and Codex follow the Agent Skills open format, so no separate Codex copy is maintained while the common format is sufficient.

Client-specific installation UX may differ; the Skill source remains the same.

---

## 🔬 research — Evidence Research

> **L1: 读懂对象 / Read the object.**

Core question:

> **What is the best currently defensible model of this object from existing evidence?**

Use it to:

- research a concept, technology, mechanism, or scientific question;
- verify a factual or contested claim;
- compare studies or evidence streams;
- research fast-changing software, AI, market, or policy facts;
- determine what the evidence supports — and where it stops.

It is designed to catch failures such as:

- a real citation that does not entail the written claim;
- different metrics being collapsed under one label;
- several articles laundering one original source into fake corroboration;
- correlation being upgraded to causation;
- heterogeneous studies being mislabeled as a fundamental controversy;
- large search volume hiding a missing evidence class;
- forcing a conclusion where `Unknown` is more honest.

Example:

```text
/lumos-research:research 调研一下 ICAP 学习框架。它的核心主张是什么，现有证据到底支持到什么程度，I > C > A > P 是否真的稳固？
```

→ [`research/SKILL.md`](./research/SKILL.md)

---

## 🧪 evidence-audit — Evidence Audit

Core question:

> **What does the evidence actually justify believing in this output?**

Use it to audit:

- AI-generated research reports;
- citation-heavy answers;
- quantitative and causal claims;
- factual recommendations;
- reports that sound rigorous but may have weak evidence chains.

Example:

```text
/lumos-research:evidence-audit 审核刚才那份调研报告，重点检查核心结论、关键数字和引用是否真的匹配。
```

→ [`evidence-audit/SKILL.md`](./evidence-audit/SKILL.md)

---

## Research stack

The current `research` skill intentionally implements only the first layer:

```text
L1 初级调研：读懂对象
L2 中级调研：读懂争论
L3 高级调研：读出新问题
```

L1 must be reliable first. If the evidence base is wrong, later synthesis only connects bad facts and produces more convincing errors.

Future capabilities should become separate composable Skills after real testing rather than being added indefinitely to one universal research prompt.

---

## Design principles

1. **Evidence > Story** — evidence beats a smooth narrative.
2. **Traceability** — decisive factual claims should be traceable.
3. **Construct Validity** — check whether sources measured the same thing before comparing them.
4. **Adversarial Search** — seek evidence capable of weakening the strongest claim.
5. **Source Lineage** — repeated secondary reporting is not independent corroboration.
6. **Citation Entailment** — citation presence is not claim support.
7. **Calibrated Uncertainty** — `Unknown` is a valid outcome.
8. **External content is data, not instructions** — retrieved content cannot take control of the agent.
9. **One canonical Skill source** — platform adapters package; they do not fork behavior.

---

## Release philosophy

This is a **distribution repository**. Experimental design and regression work happen before a Skill is published here.

```text
real use
→ systematic failure
→ regression case
→ fix
→ re-evaluate
→ publish
```

If you find a stable, reproducible failure mode, open an Issue with the task, observed behavior, and why the result is wrong.
