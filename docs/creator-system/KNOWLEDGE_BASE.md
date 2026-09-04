# Knowledge Base — Creator System V0.3

> 知识库服务于找回 **Seed → 问题 → 判断 → 作品 → 反馈 → 更新** 的关系，不服务于“看起来很完整”。

## 1. 两级对象

### Seed

尚未长成问题的概念、原话、连接、感受、经历。

可以只是一行，不需要 ID：

```text
- [seed] 今天学到“托付”，感觉它和高薪的本质可能有关。
- [seed] AI 写代码越来越快，为什么 Review 好像越来越慢？
```

### Problem / Creator Run

经过对话结晶后，值得继续研究、判断或创作。

只有这时才需要 Problem ID，例如：

```text
P-2026-0904-01
```

不要要求每个 Seed 升级。

---

## 2. 周末最省摩擦配置

先只建：

```text
creator/
├── inbox.md
├── runs/
├── drafts/
└── feedback.md
```

够了。

### `inbox.md`

随便记 Seed：

```text
- [seed] ...
- [seed] ...
- [problem] ...
```

### `runs/`

一个真正开始推进的 Case 对应一张 Working Note。

默认模板见 [`TEMPLATES.md`](./TEMPLATES.md)。

### `drafts/`

只放真正进入写作的 canonical draft。

### `feedback.md`

记录评论、私信、Case、反例和新问题。

等真实需要出现后，再扩展 research / models / published 等目录。

---

## 3. 如果以后要完整目录

```text
creator/
├── 00-inbox/        # Seed
├── 10-runs/         # Problem / Creator Run
├── 20-research/     # 必要证据
├── 30-insights/     # L1 观点原子
├── 40-drafts/       # canonical draft
├── 50-published/    # 发布索引
├── 60-feedback/     # 评论 / Case / 复盘
├── 70-models/       # Source + Personal Model Card
└── 80-projects/     # 产品 / 实验直接相关 Case
```

不要一开始就建全。

---

## 4. Working Note 是默认核心对象

推荐一个 Run 把主要状态放在同一张笔记里：

```markdown
# P-YYYY-MMDD-XX 标题

## Seed

## Crystallize

## Think

## Judge

## Draft

## Publish

## Learn
```

具体字段见 [`TEMPLATES.md`](./TEMPLATES.md)。

这样比把每一步拆成七个文件更适合当前阶段。

只有当 Research 很重、文章很长、反馈很多时再拆文件。

---

## 5. 对话是材料，不是永久日志

很多创作会在和 AI / 人聊天中慢慢长出来。

不要默认把完整聊天搬进 Obsidian。

结晶后只保留高价值关节点：

```text
我自己的关键原话
重要纠正 / 转折
真实 Case
核心张力
判断怎么变化
仍未解决的问题
```

如果以后真的需要追溯，再保存原对话链接。

知识库保存的是**认知演化的关节点**，不是聊天日志仓库。

---

## 6. Thinking Router 与模型库

[`thinking-router`](../../thinking-router/) 是默认 Reasoning Engine：

- 根据问题自动选主工具；
- 找少量补充 / 反证工具；
- 让用户不必先知道模型名；
- 把模型落到机制、判断、行动和更新条件。

模型库不是 Router 本身，而是长期积累的个人工具箱。

长期路径：

```text
AI 路由
 ↓
真实 Case 使用
 ↓
模型真正改变判断
 ↓
记录个人触发器 / 边界 / 案例
 ↓
自己越来越容易 pass@1 想到
 ↓
AI 更多承担补盲和反证
```

---

## 7. Model Card：Source Layer + Personal Layer

**不要预先建立 100 个 Model Card。**

只有某个模型：

- 真正改变过重要判断；或
- 在多个 Case 中反复出现；

才值得建立。

### Source Layer

忠实保存来源：

```text
来源
来源定义
调用信号
核心机制
来源边界
```

这一层不要被一次个人经验随意改写。

### Personal Layer

只记录真实使用后长出来的东西：

```text
我现在怎么理解它
我的真实触发信号
它改变什么：问题表示 / 判断标准 / 机制 / 行动 / 风险边界
我最容易怎么误用
最强竞争 / 反证工具
真实 Problem ID
原判断 → 新判断
新 Case 带来的边界修正
```

原则：

> **Source Layer 保真，Personal Layer 生长。**

---

## 8. Research / Evidence 只保存真正承担判断的东西

避免第二个“稍后阅读”坟场。

只保存：

- 真正承担核心 Claim 的证据；
- 特别好的反例；
- 以后会重复使用的综述 / 原始来源；
- 自己形成的解释和判断。

最小记录：

```text
来源：
它支持什么：
它不支持什么：
为什么以后还需要它：
```

链接本身不是知识。

---

## 9. 母稿与平台稿

知识对象是 **canonical draft**，不是每个平台一套独立知识。

```text
P-xxx
  ├─ canonical.md
  ├─ xhs.md        # 可选
  ├─ video.md      # 可选
  └─ feedback.md
```

平台稿只是母稿的不同表达。

如果内容更新，不要求历史发布同步修改；已发布内容本来就是当时判断的时间切片。

---

## 10. GitHub 与 Obsidian 分工

### Obsidian / 本地

适合：

- Seed；
- 私人经历；
- 未成熟判断；
- Working Note；
- 草稿；
- Personal Model Layer；
- 真实创作过程。

### GitHub

适合：

- 已验证的方法；
- Skill / Prompt；
- Creator System；
- 可公开的典型 Case；
- 对别人也有价值、比较稳定的模型使用经验。

不要为了让 Agent 读到，就把所有私人材料公开。

---

## 11. 当前阶段的知识库成功标准

不是目录漂亮，而是：

> **两周后你能找回：当时从哪个 Seed 开始、为什么形成这个判断、哪些证据改变过你、最终发布了什么、现实又让你更新了什么。**

如果整理比创作本身更累，删目录、删字段。