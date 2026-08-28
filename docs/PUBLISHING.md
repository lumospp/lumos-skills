# Publishing & Provenance

`lumos-skills` is a general public toolbox, not a repository limited to one topic.

A Skill may be about research, coding, robotics, writing, productivity, automation, learning, content, business, or something else entirely. The unifying standard is not subject matter; it is **usefulness, portability, and provenance**.

## What belongs here

A Skill is a good candidate when:

1. it solves a concrete recurring problem;
2. it is useful beyond one throwaway conversation;
3. its behavior is clear enough to explain and test;
4. it follows the Agent Skills format where possible;
5. it has been used or evaluated enough that the maintainer understands its main failure modes;
6. its origin and license permit public redistribution.

The repository may contain both original Skills and responsibly adapted Skills.

## Origin types

### Original

Created primarily in Lumos workflows from personal practice, experiments, research, or problem solving.

Examples may include a method learned from a course and independently turned into a new Skill, or a workflow developed from repeated real tasks.

### Adapted

Derived materially from an existing public Skill or project and modified for a new goal, workflow, platform, or quality standard.

For an adapted Skill, preserve the upstream author's rights and make the relationship visible.

### Ported

Behavior is intentionally kept close to an upstream Skill, but packaging or integration is changed so it works in another Agent Skills environment.

Do not call a Skill original when it is substantially derived from someone else's implementation.

## `ORIGIN.md` for adapted or ported Skills

Any materially adapted or ported Skill should include an `ORIGIN.md` beside `SKILL.md`.

Recommended template:

```markdown
# Origin

- Type: adapted | ported
- Upstream: https://github.com/owner/repo/path/to/skill
- Original author: ...
- Upstream version / commit: ...
- Upstream license: ...

## What changed

- ...
- ...

## Why this fork/adaptation exists

...
```

If upstream attribution or license notices must remain with the work, keep them in the Skill directory.

## License rule

Before publishing a derivative Skill, check the actual upstream license.

- If modification and redistribution are allowed, comply with attribution, notice, share-alike, non-commercial, or other applicable terms.
- If the license is unclear, do not assume GitHub visibility means permission to redistribute derivatives.
- If the license forbids the intended redistribution or use, do not publish the derivative here.

Different Skills may carry different licenses. A Skill-specific license or upstream notice takes precedence for that Skill.

This is why the repository should not casually apply one blanket license to third-party-derived content without checking compatibility first.

## Canonical Skill structure

```text
skill-name/
├── SKILL.md          # required
├── ORIGIN.md         # required for adapted/ported Skills
├── references/       # optional
├── scripts/          # optional
└── assets/           # optional
```

Keep platform adapters outside the canonical Skill whenever possible.

## Release maturity

Not every Skill needs the same amount of formal evaluation. Match validation effort to risk and complexity.

A lightweight utility may only need several real runs and obvious failure checks. A Skill making factual, financial, destructive, security-sensitive, or long-running decisions needs a much higher bar.

Useful labels in documentation include:

- **experimental** — useful enough to share, but behavior is still changing;
- **usable** — has survived meaningful real use and known failure checks;
- **stable** — behavior and interfaces are intentionally maintained with regression discipline.

Do not use version numbers or polished documentation as a substitute for real validation.

## Learning from other Skill repositories

Studying, comparing, and improving public Skills is encouraged. Good open-source practice is:

```text
study upstream
→ understand the underlying method
→ identify what should change
→ verify license
→ adapt deliberately
→ document origin and differences
→ test in real use
→ publish transparently
```

The goal is not to collect other people's prompts. The goal is to learn from good implementations and contribute useful improvements back to the ecosystem.