# Lumos Skills Architecture

> Platform-neutral first. Topic-neutral by design. Platform adapters stay outside the core Skills.

## 1. Goal

`lumos-skills` is a general public toolbox for reusable Agent Skills.

It is intentionally **not** limited to research, cognition, coding, robotics, writing, or any other single domain.

The repository is unified by structure and publishing discipline rather than subject matter.

A Skill belongs here when it solves a useful recurring problem, is portable enough to share, and its provenance permits redistribution.

The main architectural rule is:

> **A Skill has one canonical source. Platform-specific packaging may reference it, but should not fork or duplicate it unless a platform makes that unavoidable.**

This keeps Skill behavior portable across Claude Code, Codex, and other clients that support the Agent Skills format.

## 2. Canonical layout

```text
lumos-skills/
├── README.md
├── docs/
│   ├── ARCHITECTURE.md
│   └── PUBLISHING.md
│
├── <skill-a>/
│   ├── SKILL.md
│   ├── ORIGIN.md          # adapted/ported only
│   ├── references/
│   ├── scripts/
│   └── assets/
│
├── <skill-b>/
│   └── SKILL.md
│
└── .claude-plugin/
    └── marketplace.json
```

Each top-level Skill directory is a standalone Agent Skill and the canonical source for that capability.

A canonical Skill follows the public Agent Skills structure:

```text
skill-name/
├── SKILL.md          # required
├── references/       # optional
├── scripts/          # optional
└── assets/           # optional
```

`ORIGIN.md` is a Lumos repository convention for materially adapted or ported Skills; it is not part of the Agent Skills runtime requirement.

The `name` in `SKILL.md` must match the parent directory name.

## 3. Topic neutrality

Do not build repository-level assumptions that all Skills belong to one product or methodology.

Valid future examples could include:

```text
research/
robot-log-diagnosis/
repo-cleanup/
writing-review/
agent-migration/
knowledge-capture/
travel-planner/
...
```

These capabilities do not need a shared subject. They only need clear responsibilities and compatible packaging.

Related Skills may form a series or bundle, but that grouping must not redefine the entire repository.

For example, `research` and `evidence-audit` currently form a research-related bundle. They are two Skills in the toolbox, not the identity of the toolbox itself.

## 4. Core layer: Agent Skills

The canonical Skill layer must remain platform-neutral where practical.

Rules:

1. Use the public Agent Skills `SKILL.md` format.
2. Keep platform-specific manifests and install commands out of core Skill behavior unless the task itself requires them.
3. Use relative paths for supporting files.
4. Prefer progressive disclosure: keep `SKILL.md` focused and move detailed reference material into supporting files.
5. Do not add `allowed-tools` merely for convenience when cross-client support is uncertain.
6. Only add `compatibility` when the Skill truly requires a specific environment.
7. Do not maintain separate Claude/Codex copies just to change packaging.
8. Do not let repository-level branding leak into the Skill unless it is part of the actual capability.

## 5. Platform adapters

Platform adapters are distribution layers, not behavioral forks.

### Claude Code

Claude-specific marketplace metadata lives under:

```text
.claude-plugin/
└── marketplace.json
```

A Claude plugin may bundle one or several canonical Skills.

Current bundle:

```text
lumos-research
├── research
└── evidence-audit
```

This gives namespaced invocations such as:

```text
/lumos-research:research
/lumos-research:evidence-audit
```

Future unrelated Skills should normally use an appropriate new plugin or bundle instead of being added to `lumos-research` merely because they live in the same repository.

Example:

```text
lumos-research      → research-related Skills
lumos-dev           → future developer tools
lumos-robotics      → future robotics Skills
```

These are examples, not required categories. A single standalone Skill can also be exposed by itself.

### Codex / OpenAI

No Codex-specific copy is maintained while Codex can consume the common Agent Skills structure directly.

If OpenAI later requires special packaging, add an adapter or build artifact that derives from the canonical Skill rather than editing the core workflow solely for Codex.

### Other agents

Use the same rule:

> canonical Skill first, adapter only when a real platform requirement exists.

## 6. Provenance is part of architecture

The repository may contain:

- original Skills;
- adapted Skills;
- ported Skills.

Architecture must make those origins visible rather than pretending every directory was created from scratch.

For materially adapted or ported work, include `ORIGIN.md` and comply with the upstream license and notices.

Detailed rules live in [`PUBLISHING.md`](./PUBLISHING.md).

This also means a single repository-wide license should not be assumed to override Skill-specific or upstream license obligations.

## 7. Versioning model

Behavior belongs to the canonical Skill.

Platform package versions, if introduced, describe distribution state and must not silently redefine underlying Skill behavior.

A platform adapter should normally change only when one of these changes:

- packaged Skill set;
- platform manifest requirements;
- distribution metadata;
- platform runtime integration.

Behavioral changes belong in the canonical Skill first.

## 8. Validation model

Validation should be proportional to risk and complexity.

Do not force a tiny formatting utility through the same evaluation stack as an evidence-heavy research system or a destructive automation Skill.

A useful mental model:

```text
low consequence + simple behavior
→ real-use checks + obvious failure cases

complex / factual / long-running
→ structured evals + regression cases

security-sensitive / destructive / high-stakes
→ stronger safeguards + explicit verification
```

The common requirement is that a published Skill should not be a completely untested prompt whose behavior is unknown to the maintainer.

## 9. Release flow

For original work:

```text
real problem
    ↓
build Skill
    ↓
use / test
    ↓
understand failure modes
    ↓
publish canonical Skill
    ↓
platform adapters reference it
```

For adapted work:

```text
study upstream
    ↓
understand method and implementation
    ↓
check license
    ↓
adapt deliberately
    ↓
document origin + differences
    ↓
use / test
    ↓
publish
```

The repository can therefore grow from both personal invention and responsible open-source learning.

## 10. Future expansion

New stable capabilities should normally become new top-level Skills rather than being absorbed into an unrelated existing Skill.

There is no predetermined taxonomy.

Add categories, indexes, routers, or bundles only after the number of Skills creates a real navigation problem.

Do not design a hierarchy for fifty hypothetical Skills when the repository only contains a few.

## 11. Design tests

Before adding a platform-specific file, ask:

> **If this adapter disappeared tomorrow, would the canonical Skill still make sense and remain usable by another Agent Skills client?**

Before adding a new Skill, ask:

> **Does this solve a real reusable problem, or am I just storing a long prompt?**

Before publishing an adaptation, ask:

> **Can a reader clearly tell what came from upstream, what changed here, and whether the license permits it?**

If any answer is no, fix the structure before publishing.