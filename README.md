<div align="center">

# 🧰 Lumos Skills

**Open Agent Skills I build, adapt, use, and want to share.**

基于开放的 **Agent Skills** 格式，核心 Skill 保持平台中立；Claude Code 等平台通过外层适配接入。

</div>

`lumos-skills` 是我的公开 Agent Skills 工具箱。

这里**不限定主题**。只要一个 Skill 来自真实问题、实际使用或值得保留下来的思考，并且可能对别人也有用，就可以在这里发布。

以后可能包括：

- 调研与判断；
- 编程与工程；
- AI / Agent 工作流；
- 机器人；
- 学习与知识管理；
- 写作与内容；
- 自动化与效率工具；
- 其他有趣但确实有用的东西。

我不想把这里做成 Prompt 收藏夹。更希望它像一个不断生长的开源工具箱：**自己先用，确认有价值，再整理成别人也能安装的 Skill。**

---

## Skills

| Skill | What it does | Release |
|---|---|---|
| 🔬 [`research`](./research) | 证据优先的 L1 综合调研：读懂一个对象当前最可靠的已有知识 | V0.3 |
| 🧪 [`evidence-audit`](./evidence-audit) | 审核一份答案/报告的 Claim → Evidence 链条到底站不站得住 | V0.2 |

新的 Skill 会直接作为新的顶层目录加入，不要求属于同一个领域。

---

## Repository structure

```text
lumos-skills/
├── <skill-name>/               # canonical platform-neutral Skill
│   ├── SKILL.md
│   ├── ORIGIN.md               # adapted/ported Skill 时使用
│   ├── references/             # optional
│   ├── scripts/                # optional
│   └── assets/                 # optional
│
├── research/
├── evidence-audit/
│
├── .claude-plugin/             # Claude Code distribution adapter
│   └── marketplace.json
│
└── docs/
    ├── ARCHITECTURE.md
    └── PUBLISHING.md
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

未来如果出现其他领域的 Skill，可以增加新的 Claude plugin bundle，而不是把所有 Skill 强塞进 `lumos-research`。

### Claude Code — install one standalone Skill

也可以把任意 Skill 目录直接交给 Claude Code，例如：

```text
帮我安装这个 Skill：
https://github.com/lumospp/lumos-skills/tree/main/research
```

Standalone 安装通常可直接使用 `/research`。

### Codex / other Agent Skills clients

核心 Skill 使用公共 Agent Skills 结构，因此其他兼容客户端直接消费相同目录，不维护一套 Codex-only / Claude-only Skill：

```text
https://github.com/lumospp/lumos-skills/tree/main/research
https://github.com/lumospp/lumos-skills/tree/main/evidence-audit
```

具体安装命令由各 Agent 客户端决定，Skill 源码保持同一份。

---

## 🔬 research — Evidence Research

> **L1：读懂对象。**

它回答：

> **关于这个对象，目前最可靠、最可辩护的已有知识是什么？**

适合调研概念、技术、机制、科学问题、快速变化的软件/市场/政策事实，以及查证有争议的说法。

它重点防止：

- 引用是真的，但并不支持写出来的强结论；
- 不同指标被硬塞进同一个概念；
- 多篇二手报道实际来自同一个原始来源；
- 相关关系被写成因果关系；
- 异质研究被轻率包装成“学界争议”；
- 搜了很多资料，却没发现关键证据类型缺失；
- 为了完成回答而掩盖 `Unknown`。

```text
/lumos-research:research 调研一下 ICAP 学习框架。它的核心主张是什么，现有证据到底支持到什么程度，I > C > A > P 是否真的稳固？
```

→ [`research/SKILL.md`](./research/SKILL.md)

---

## 🧪 evidence-audit — Evidence Audit

它回答：

> **这份输出里的重要结论，证据到底允许我们相信到什么程度？**

适合审核 AI 研究报告、引用密集的答案、关键数字、因果结论以及看起来很专业但证据链可能有漏洞的材料。

```text
/lumos-research:evidence-audit 审核刚才那份调研报告，重点检查核心结论、关键数字和引用是否真的匹配。
```

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

---

## Original, adapted, and ported Skills

这里既可以发布我自己从零形成的 Skill，也可以发布在许可证允许范围内对优秀开源 Skill 的改造。

对于 materially adapted / ported Skill，会在目录中增加：

```text
ORIGIN.md
```

记录：

- upstream URL；
- 原作者；
- 上游版本 / commit；
- 上游 license；
- 我修改了什么；
- 为什么要做这次改造。

详细规则见 [Publishing & Provenance](./docs/PUBLISHING.md)。

---

## Inspiration

我会持续学习优秀的公开 Skill 项目，包括但不限于：

- [KKKKhazix/khazix-skills](https://github.com/KKKKhazix/khazix-skills)
- [dontbesilent2025/dbskill](https://github.com/dontbesilent2025/dbskill)

学习一个 Skill 不等于复制它。真正值得留下来的，是理解它为什么有效、哪里可以改进，再在许可证允许的范围内做出清楚、可追溯的改造。

---

## Release philosophy

不同 Skill 风险不同，不强求所有能力使用同一套重型测试，但至少应该知道它解决什么、在哪些场景会失败。

```text
real problem
→ build / adapt
→ use it
→ observe failures
→ improve
→ publish transparently
```

复杂或高风险 Skill 会使用更严格的 eval / regression；简单工具则保持轻量，不为了“显得工程化”而过度设计。

如果你发现某个 Skill 有稳定、可复现的问题，欢迎提 Issue。