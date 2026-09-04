<div align="center">

# 🧰 Lumos Skills

**Open Agent Skills I build, adapt, use, and want to share.**

基于开放的 **Agent Skills** 格式，核心 Skill 保持平台中立；Claude Code、Codex 等平台通过外层适配接入。

</div>

`lumos-skills` 是我的公开 Agent Skills 工具箱。

这里**不限定主题**。只要一个 Skill 来自真实问题、实际使用或值得保留下来的思考，并且可能对别人也有用，就可以在这里发布。

以后可能包括：调研与判断、编程与工程、AI / Agent 工作流、机器人、学习与知识管理、写作与内容、自动化与效率工具，以及其他有趣但确实有用的东西。

我不想把这里做成 Prompt 收藏夹。更希望它像一个不断生长的开源工具箱：**自己先用，确认有价值，再整理成别人也能安装的 Skill。**

---

## Skills

| Skill | What it does | Status |
|---|---|---|
| 🌱 [`progressive-elaboration`](./progressive-elaboration) | 允许弱输入，通过低压力对话把模糊 Seed 渐进澄清并交接给领域能力 | Experimental |
| 🧭 [`thinking-router`](./thinking-router) | 先建模再自动选择少量高杠杆思维工具，不要求用户先知道模型名 | Experimental |
| 🔬 [`research`](./research) | 证据优先的 L1 综合调研：读懂一个对象当前最可靠的已有知识 | V0.3 |
| 🧪 [`evidence-audit`](./evidence-audit) | 审核一份答案 / 报告的 Claim → Evidence 链条到底站不站得住 | V0.2 |

新的 Skill 会直接作为新的顶层目录加入，不要求属于同一个领域。

---

## Composable pattern

这些 Skill 可以独立使用，也可以按状态组合。

例如 Lumos Creator System 当前采用：

```text
low-resolution input
   ↓
progressive-elaboration
   ↓
thinking-router
   ↓
research / evidence-audit when needed
   ↓
domain workflow / artifact
   ↓
reality feedback
```

关键不是机械执行整条流水线，而是：**只调用当前真正需要的能力。**

Creator System 实验文档见：

- [`docs/creator-system/README.md`](./docs/creator-system/README.md)
- [`docs/creator-system/QUICKSTART.md`](./docs/creator-system/QUICKSTART.md)

---

## Repository structure

```text
lumos-skills/
├── progressive-elaboration/
│   ├── SKILL.md
│   └── references/
│       └── workbench-notes.md
│
├── thinking-router/
│   ├── SKILL.md
│   ├── ORIGIN.md
│   └── references/
│       └── tool-index.md
│
├── research/
│   ├── SKILL.md
│   └── references/
│
├── evidence-audit/
│   └── SKILL.md
│
├── .claude-plugin/
│   └── marketplace.json
│
└── docs/
    ├── ARCHITECTURE.md
    ├── PUBLISHING.md
    └── creator-system/
```

每个顶层 Skill 目录都是那项能力的 **canonical source**。

- [Architecture & portability](./docs/ARCHITECTURE.md)
- [Publishing, adaptation & provenance](./docs/PUBLISHING.md)

---

## Install

### Claude Code — Marketplace

当前已经提供 `lumos-research` bundle：

```text
/plugin marketplace add lumospp/lumos-skills
/plugin install lumos-research@lumos-skills
```

安装后：

```text
/lumos-research:research
/lumos-research:evidence-audit
```

`progressive-elaboration` 与 `thinking-router` 当前仍处于真实 Case 验证阶段，先作为 standalone canonical Skills 使用；等行为稳定后再决定是否加入新的 Claude bundle。

### Claude Code — install one standalone Skill

可以把任意 Skill 目录直接交给 Claude Code，例如：

```text
帮我安装这个 Skill：
https://github.com/lumospp/lumos-skills/tree/main/progressive-elaboration
```

```text
帮我安装这个 Skill：
https://github.com/lumospp/lumos-skills/tree/main/thinking-router
```

### Codex / other Agent Skills clients

核心 Skill 使用公共 Agent Skills 结构，因此兼容客户端直接消费相同目录，不维护一套 Codex-only / Claude-only Skill：

```text
https://github.com/lumospp/lumos-skills/tree/main/progressive-elaboration
https://github.com/lumospp/lumos-skills/tree/main/thinking-router
https://github.com/lumospp/lumos-skills/tree/main/research
https://github.com/lumospp/lumos-skills/tree/main/evidence-audit
```

具体安装命令由各 Agent 客户端决定，Skill 核心源码保持同一份。

---

## 🌱 progressive-elaboration

它解决：

> **用户只有一个模糊念头、感觉、错误现象或半成品目标时，Agent 怎么帮助结构逐渐长出来，而不是要求用户先把问题想清楚？**

核心模式：

```text
SEED
→ EXPLORE
→ CRYSTALLIZE
→ FRAME
→ HANDOFF / ACT
→ VERIFY
→ LEARN
```

它是平台无关的人机协作协议，可以放在创作、研究、Coding、产品、学习等 Agent 前面。

→ [`progressive-elaboration/SKILL.md`](./progressive-elaboration/SKILL.md)

---

## 🧭 thinking-router

它解决：

> **问题已经有形状，但用户不知道应该调用哪个思维工具时，Agent 怎么先建模、再自动路由少量真正改变判断的模型？**

核心纪律：

- 先建模，再选工具；
- 1 个主工具；
- 至多 3 个不同工位的补充 / 反证工具；
- 删除后结论不变的模型不用；
- 模型不能冒充证据；
- 最终落到行动 / 实验 / 更新条件。

该实现受到万维钢《现代思维工具100讲》及用户提供对应 Skill 的重要启发，但不直接复制上游长文；来源与适配说明见 `ORIGIN.md`。

→ [`thinking-router/SKILL.md`](./thinking-router/SKILL.md)

---

## 🔬 research — Evidence Research

> **L1：读懂对象。**

它回答：

> **关于这个对象，目前最可靠、最可辩护的已有知识是什么？**

适合调研概念、技术、机制、科学问题、快速变化的软件 / 市场 / 政策事实，以及查证有争议的说法。

→ [`research/SKILL.md`](./research/SKILL.md)

---

## 🧪 evidence-audit — Evidence Audit

它回答：

> **这份输出里的重要结论，证据到底允许我们相信到什么程度？**

适合审核 AI 研究报告、引用密集答案、关键数字、因果结论，以及看起来很专业但证据链可能有漏洞的材料。

→ [`evidence-audit/SKILL.md`](./evidence-audit/SKILL.md)

---

## About the research series

`research` 只是当前仓库里的一个系列，不代表整个仓库的主题。

它目前采用：

```text
L1 初级调研：读懂对象
L2 中级调研：读懂争论
L3 高级调研：读出新问题
```

当前只先把 L1 做扎实。未来如果 L2 / L3 形成稳定、独立、经过真实测试的能力，会发布成新的可组合 Skill，而不是无限膨胀一个万能 Prompt。

---

## Principles

仓库不统一主题，但统一这些原则：

1. **Real use first** — 优先沉淀真实用过、确实解决问题的能力。
2. **One canonical source** — 一个 Skill 一份核心源码，平台适配器只负责包装。
3. **Platform-neutral core** — 尽量遵循公共 Agent Skills 格式，不把 Claude / Codex 特性写死进核心。
4. **Clear boundary** — 一个 Skill 尽量解决清楚的一类问题，而不是变成 God Skill。
5. **Progressive disclosure** — 主流程留在 `SKILL.md`，大块资料拆到 supporting files。
6. **Transparent provenance** — 原创就是原创；基于别人 Skill 改造就明确标注来源和差异。
7. **Respect licenses** — 公开可见不等于可以任意复制修改，二创前先确认上游许可证。
8. **Reality feedback** — 真实使用暴露的问题比继续堆 Prompt 规则更有价值。
9. **Human ownership** — Agent 可以降低结构化和执行成本，但不能偷偷夺走目标、价值、修正权与责任。

---

## Original, adapted, and ported Skills

这里既可以发布自己从真实实践中形成的 Skill，也可以发布在许可证允许范围内对优秀开源 Skill 的改造。

对于 materially adapted / ported Skill，使用 `ORIGIN.md` 记录：

- upstream URL；
- 原作者；
- 上游版本 / commit；
- 上游 license；
- 修改了什么；
- 为什么改。

详细规则见 [Publishing & Provenance](./docs/PUBLISHING.md)。

---

## Inspiration

会持续学习优秀公开 Skill 项目，包括但不限于：

- [KKKKhazix/khazix-skills](https://github.com/KKKKhazix/khazix-skills)
- [dontbesilent2025/dbskill](https://github.com/dontbesilent2025/dbskill)

学习一个 Skill 不等于复制它。真正值得留下来的，是理解它为什么有效、哪里可以改进，再在许可证允许的范围内做出清楚、可追溯的实现。

---

## Release philosophy

```text
real problem
→ build / adapt
→ use it
→ observe failures
→ improve
→ publish transparently
```

不同 Skill 风险不同，不强求统一重型测试，但至少应该知道它解决什么、在哪些场景会失败。

如果一个流程一直“看起来越来越完整”，但没有更多真实产出或更好的现实判断，那不是进步。