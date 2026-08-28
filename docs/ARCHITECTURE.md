# Lumos Skills Architecture

> Platform-neutral first. Platform adapters stay outside the core skills.

## 1. Goal

`lumos-skills` is the public distribution repository for reusable Agent Skills.

The repository follows one rule:

> **A skill has one canonical source. Platform-specific packaging may reference it, but must not fork or duplicate it unless a platform makes that unavoidable.**

This keeps research logic portable across Claude Code, Codex, ChatGPT, and other clients that support the Agent Skills format.

## 2. Canonical layout

```text
lumos-skills/
├── README.md
├── docs/
│   └── ARCHITECTURE.md
├── research/
│   ├── SKILL.md
│   └── references/
├── evidence-audit/
│   └── SKILL.md
└── .claude-plugin/
    └── marketplace.json
```

Each top-level skill directory is a standalone Agent Skill and is the canonical source for that skill.

A canonical skill follows the Agent Skills structure:

```text
skill-name/
├── SKILL.md          # required
├── references/       # optional
├── scripts/          # optional
└── assets/           # optional
```

The `name` in `SKILL.md` must match the parent directory name.

## 3. Core layer: Agent Skills

The core layer must remain platform-neutral.

Rules:

1. Use the public Agent Skills `SKILL.md` format.
2. Keep platform-specific manifests and commands out of the core skill unless they are essential to the task itself.
3. Use relative paths for supporting files.
4. Prefer progressive disclosure: keep the main `SKILL.md` focused; move detailed material into `references/`.
5. Do not add `allowed-tools` merely for convenience; it is experimental and support varies across clients.
6. Only add `compatibility` when the skill truly requires a specific environment.
7. Optional metadata must not become a second source of truth for release state.

## 4. Platform adapters

Platform adapters are packaging and distribution layers, not forks of the skill.

### Claude Code

Claude-specific marketplace metadata lives under:

```text
.claude-plugin/
└── marketplace.json
```

The marketplace entry uses the repository root as its source and explicitly points Claude Code to the canonical top-level skill directories.

Current bundle:

```text
lumos-research
├── research
└── evidence-audit
```

This gives Claude Code namespaced invocations such as:

```text
/lumos-research:research
/lumos-research:evidence-audit
```

No duplicate copy of either skill exists under a Claude-only directory.

### Codex / OpenAI

No Codex-specific copy is maintained while Codex can consume the Agent Skills format directly.

If OpenAI later requires platform-specific packaging, add an adapter that references or packages the canonical skill rather than editing the core workflow for Codex alone.

### Other agents

Use the same rule: first try the canonical Agent Skills directory. Add a platform adapter only when the platform has a real packaging or runtime requirement that cannot be expressed by the common standard.

## 5. Versioning model

Skill behavior is versioned by the release process in the development repository and documented in this public repository.

Platform package versions, if introduced, are distribution versions and must not silently redefine the underlying skill behavior.

A platform adapter should change only when one of these changes:

- the set of packaged skills;
- platform-specific manifest requirements;
- distribution metadata;
- platform-specific runtime integration.

A change to research methodology belongs in the canonical skill first.

## 6. Release flow

```text
private development / evaluation
        ↓
behavior tests and regression checks
        ↓
canonical Skill release
        ↓
public lumos-skills repository
        ↓
platform adapters reference the same canonical files
```

The public repository is a distribution surface, not the primary place for experimental prompt iteration.

## 7. Future expansion

When new capabilities become stable, add them as new top-level skills rather than growing one universal skill indefinitely.

Example direction:

```text
research/             # L1: read the object
investigation/        # possible L2 capability
hypothesis/           # possible L3 hypothesis work
evidence-audit/
experiment-design/
```

These names are architectural placeholders, not commitments to implement them now.

Claude bundles can then group related canonical skills without changing their portable form.

## 8. Design test

Before adding any platform-specific file, ask:

> **If this adapter disappeared tomorrow, would the canonical Skill still make sense and remain usable by another Agent Skills client?**

If the answer is no, platform-specific concerns have leaked into the core layer and the design should be reconsidered.
