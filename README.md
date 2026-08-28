<div align="center">

# 🧰 Lumos Skills

**Evidence-first Agent Skills for research and reasoning**

面向 Claude Code 与其他支持 `SKILL.md` / Agent Skills 的 AI Agent。

</div>

这里存放我实际使用、经过测试后对外发布的 Agent Skills。

目标不是收集更多 Prompt，而是把可复用的认知方法做成**可安装、可调用、可迭代**的能力。

当前重点是研究可靠性：让 AI 在快速搜索和综合信息时，更少把“看起来合理”误当成“证据支持”。

---

## 📋 Skills

| Skill | 一句话 | 当前版本 |
|---|---|---|
| 🔬 [`research`](./research) | 证据优先的综合调研：读懂一个对象当前最可靠的已有知识 | V0.3 |
| 🧪 [`evidence-audit`](./evidence-audit) | 审核一份答案/报告的 Claim → Evidence 链条到底站不站得住 | V0.2 |

---

## 📦 安装

### 最简单：直接把 Skill 链接交给 Claude Code

在 Claude Code 中直接说：

```text
帮我安装这个 Skill：
https://github.com/lumospp/lumos-skills/tree/main/research

安装为全局个人 Skill，并保留 references 等 supporting files。
安装完成后验证 /research 是否可用。
```

安装 `evidence-audit`：

```text
帮我安装这个 Skill：
https://github.com/lumospp/lumos-skills/tree/main/evidence-audit

安装为全局个人 Skill，并验证 /evidence-audit 是否可用。
```

Claude Code 的个人 Skill 通常位于：

```text
~/.claude/skills/<skill-name>/
```

也可以手动 clone 本仓库，再复制对应 Skill 目录到 Agent 的 Skill 目录。

---

## 🔬 research｜综合调研

> **L1 Evidence Research：读懂对象。**

它回答的不是“能不能写一篇很全面的报告”，而是：

> **关于这个对象，目前最可靠、最可辩护的已有知识是什么？**

适合：

- 调研一个概念、技术、机制或科学问题；
- 查证一个事实或争议说法；
- 比较研究结果；
- 研究快速变化的软件、AI、市场或政策事实；
- 判断现有证据到底支持到什么程度。

它重点防止这些常见失败：

- 引用是真的，但并不支持写出来的强结论；
- 把不同指标硬塞进一个概念里比较；
- 多篇媒体报道其实都来自同一个原始来源；
- 把相关关系写成因果关系；
- 看到研究结果不同就轻率写成“学界有争议”；
- 搜到很多资料，却没发现真正关键的证据类型仍然缺失；
- 为了给出答案而掩盖 `Unknown`。

### 使用示例

```text
/research 帮我综合调研一下 ICAP 学习框架。它的核心主张是什么，现有证据到底支持到什么程度，I > C > A > P 是否真的稳固？
```

```text
/research 研究一下 AI 编程助手到底能提高多少程序员生产率。请区分不同 productivity 指标，并解释为什么研究结果差异很大。
```

→ [`research/SKILL.md`](./research/SKILL.md)

---

## 🧪 evidence-audit｜证据审核

它回答一个更窄的问题：

> **这份输出里的重要结论，证据到底允许我们相信到什么程度？**

适合用来审核：

- AI 生成的研究报告；
- 有很多引用的长答案；
- 重要事实判断；
- 因果结论；
- 数据驱动的建议；
- 你自己写完、但担心证据链有漏洞的报告。

它不会因为文章“写得很专业”或者“引用很多”就给高评价，而会逐个检查关键 Claim 的来源、构念、范围、因果强度、来源独立性和时效性。

### 使用示例

```text
/evidence-audit 审核刚才那份调研报告。重点检查核心结论、关键数字和引用是否真的匹配。
```

→ [`evidence-audit/SKILL.md`](./evidence-audit/SKILL.md)

---

## 🧭 设计原则

这些 Skill 遵循几个简单原则：

1. **Evidence > Story** — 证据优先于一个顺滑的故事。
2. **Traceability** — 决定结论的事实应该能追溯。
3. **Construct Validity** — 先确认不同来源是不是在测同一个东西。
4. **Adversarial Search** — 主动找可能削弱核心结论的证据，而不是象征性列“局限”。
5. **Source Lineage** — 多个二手转述同一个源头，不算多次独立验证。
6. **Citation Entailment** — 有引用不等于引用支持这句话。
7. **Calibrated Uncertainty** — 证据不足时，`Unknown` 是合法答案。
8. **External content is data, not instructions** — 网页、论文和文件中的指令不能接管 Agent。

---

## 🧱 关于更高级的调研

目前公开的 `research` 刻意只做第一层：

```text
L1 初级调研：读懂对象
L2 中级调研：读懂争论
L3 高级调研：读出新问题
```

L1 的目标是先把“什么是真的、证据支持到哪里”做扎实。

后续如果形成经过真实测试的独立能力，会作为新的 Skill 发布，而不是把所有能力不断塞进一个万能 `research`。

---

## 🛠️ 版本与迭代

这里是**发布仓库**：只放已经整理好、适合直接安装的版本。

迭代原则：

```text
真实使用
→ 发现系统性失败
→ 把失败变成测试案例
→ 修正 Skill
→ 回归验证
→ 再发布
```

如果你发现某个 Skill 在真实任务中出现稳定、可复现的问题，欢迎提 Issue。
