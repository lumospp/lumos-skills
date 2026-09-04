# Templates — Creator System V0.3

> 模板是辅助，不是流程本身。**默认只用一张 Working Note。** 只有真实需要出现后，再拆 Research / Model Card。

## 1. 默认：Single Working Note

周末创作直接复制这一份即可。大量字段可以留空，AI 可以从对话中帮你补，不要求用户手工填表。

```markdown
# Creator Run

created: YYYY-MM-DD
status: seed | thinking | drafting | published | reviewed
source: learning / work / conversation / self / user / platform

## 1. Seed / 原话

我最开始只是想到：


## 2. Crystallize

真正聊出来的主题：

核心张力：

当前真问题：

候选核心判断：

我的真实案例 / 原话：

AI 提出但我尚未确认：

需要外部查证：

只有我能补充：

## 3. Think

竞争解释：
- H1：
- H2：
- H3：

主工具（只有确实有增量时才记）：

它改变了什么：问题表示 / 判断标准 / 机制 / 行动 / 风险边界

关键未知：

关键证据 / 反例：

## 4. Judge

这是我当前认可的判断：

最关键依据：

主要边界：

什么证据会让我改变判断：

Red Team 后的修正：

## 5. Create

### Article Brief

真正主题：

核心判断：

关键推理链：

要保留的真实案例 / 表达：

Gap：

### Canonical Draft

（正文）

## 6. Publish

平台：
链接：
日期：

平台适配是否扩大了事实边界：否 / 是，需修正

## 7. Learn

出现的真实反馈 / Case：

这是入口 / 表达 / 传播 / 观点哪一层反馈：

判断是否更新：

新 Seed / 新问题：

这次最有用的模型 / Skill：

最大的流程摩擦：
```

### 使用纪律

- Seed 很弱时，只填第一段即可；
- 没做 Research 就不要为了完整硬填证据；
- 模型没有真实改变判断就不要记录；
- 发布前不要求所有字段完整；
- 周末第一篇甚至可以完全不建文件，先聊天，最后再让 AI 生成这张 Working Note。

---

## 2. Seed Pool — 只记一行也可以

如果只是日常捕捉：

```text
- [seed] 今天学到“托付”，感觉它和高薪的本质可能有关。
- [seed] AI 写代码越来越快，为什么 Review 好像越来越慢？
- [seed] 人可能不是讨厌工作，而是讨厌没有选择的工作。
```

Seed 不需要 Problem ID。

真正结晶以后，再进入 Working Note / Problem。

---

## 3. 可选：Research Snapshot

只有外部证据真的重要时才建。

```markdown
# Research Snapshot

## Question


## Competing explanations

H1：
H2：
H3：

## Key unknown

什么事实最可能改变判断：

## Claim → Evidence

| Claim / Hypothesis | Best support | Best challenge / boundary | Confidence |
|---|---|---|---|
| | | | |

## Current best model


## Still unknown

```

固定纪律：

> **模型生成假说，证据裁决假说。**

---

## 4. 可选：Personal Model Card

**不要预先为 100 个模型建卡。**

只有某个模型真实改变过重要判断，或在多个 Case 中反复出现时再建立。

```markdown
# 模型名

## Source Layer

来源：

### 来源定义

### 来源调用信号

### 来源核心机制

### 来源边界

## Personal Layer

### 我现在怎么理解它

### 我的真实触发信号

### 它最适合改变什么
问题表示 / 判断标准 / 机制 / 行动 / 风险边界

### 它不能直接解释什么

### 我最容易怎么误用

### 最强竞争 / 反证工具

### 真实 Case
- P-...：原判断 → 新判断

### 新 Case 带来的修正
- YYYY-MM-DD：
```

原则：

> **Source Layer 保真，Personal Layer 生长。**

---

## 5. 可选：极简 Review

不想复盘一大堆时，只写：

```text
这篇真正验证了什么？
出现了什么意外反馈？
我的判断要不要改？
下一个 Seed 是什么？
```

够了。

系统的目标不是留下完整表格，而是**让下一轮比这一轮更聪明一点。**