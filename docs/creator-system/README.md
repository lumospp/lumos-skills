# Lumos Creator System V0.3

> 从一个模糊念头开始，经由对话、思考、证据、判断、表达与现实反馈，逐渐形成属于自己的公开作品和世界模型。
>
> 当前状态：**可运行实验版。周末直接用，不再继续搭系统；真实创作暴露问题后再迭代。**

## 1. 这个系统解决什么

它不是“批量生产内容”的流水线，也不要求人在开始创作前就先想出一个好问题。

它解决的是：

> **如何让真实生活、学习、工作中的概念、经历、观察、困惑和半成品念头，在 AI 的辅助下逐渐长成一个值得公开表达的判断；同时不让 AI 替代人的理解、价值选择和责任。**

核心闭环：

```text
现实 / 学习 / 工作 / 对话
        ↓
Seed / Question
        ↓
澄清与结晶
        ↓
思考 + 必要调研
        ↓
形成判断 + 反证
        ↓
母稿 + 平台表达
        ↓
发布
        ↓
评论 / Case / 行动结果
        ↓
更新判断、模型与新问题
        ↺
```

创作最终是问题驱动，但**问题本身可以在高质量对话里生成**。

---

## 2. 两种合法入口

### A. Problem-first

你已经有比较清楚的问题：

```text
“为什么 AI 明明讲懂了，我关掉它却讲不出来？”
```

直接进入 Frame / Think / Research。

### B. Seed-first

你只有一点东西：

```text
“今天学到奈特不确定性，感觉挺有意思。”
“刚跟同事聊了两句，好像有个点，但说不清。”
“我觉得高薪可能和托付有关。”
```

这是完全合法的输入。

先由 [`progressive-elaboration`](../../progressive-elaboration/) 做低压力孵化：

```text
接住 → 展开 → 连接 → 轻问 → 结晶
```

不逼你先回答“核心问题是什么”。

详细创作实现见 [`INCUBATION.md`](./INCUBATION.md)。

---

## 3. 用户视角只需要记六个阶段

```text
1. CAPTURE      捕捉：先把 Seed 留住
2. CRYSTALLIZE  结晶：聊到问题 / 张力开始有形状
3. THINK        思考：竞争解释 + Thinking Router + 必要证据
4. JUDGE        判断：形成当前可承担的判断，再做 Red Team
5. CREATE       创作：母稿 → 平台适配 → 发布
6. LEARN        学习：现实反馈更新判断、模型和下一轮 Seed
```

内部仍可细分为 Frame / Research / Judge / Red Team / Draft / Adapt / Publish，但**不要求用户手工管理这些步骤**。

完整执行规则见 [`WORKFLOW.md`](./WORKFLOW.md)。

---

## 4. 四层能力架构

Creator System 是**状态与流程控制层**，不把多个 Skill 机械串成流水线。

```text
                    Creator System
                  状态 / 流程控制层
                          │
            ┌─────────────┼─────────────┐
            ▼             ▼             ▼
        Interaction     Reasoning      Evidence
            │             │             │
progressive-elaboration thinking-router research /
                                      evidence-audit
            └─────────────┬─────────────┘
                          ▼
                     Human Judge
                          │
                    Expression Layer
                  Editor / Adapter
                          │
                          ▼
                       Reality
                          │
                          ▼
                  Knowledge / Models
                          ↺
```

### `progressive-elaboration`

解决：**输入还很模糊，人不知道该问什么。**

允许一句话、一个概念、一点感觉启动，通过对话把共享状态逐渐长清楚。

### `thinking-router`

解决：**问题已经有形状，但不知道该从哪个思维模型切入。**

默认规则：

- 先建模，再选工具；
- 1 个主工具；
- 最多 3 个承担不同工位的补充 / 反证工具；
- 删除后不改变判断的模型不使用；
- 模型不能冒充证据。

### `research` / `evidence-audit`

解决：**世界事实上是什么、证据能支持多强的结论。**

固定纪律：

> **模型生成问题、结构和假说；证据裁决事实上是否成立。**

### Human Judge

人保留：

- 什么值得关心；
- 是否认可一个判断；
- 价值与风险权衡；
- 修正权；
- 是否愿意公开承担这句话。

注意：

> **判断所有权 ≠ 必须面对空白页亲手写出核心判断。**

AI 可以从多轮对话中提炼候选判断；人负责理解、确认、纠正、解释和承担。

### Reality

现实拥有最终否决权。

阅读量不能证明观点正确；评论、反例、Case、用户行为和行动结果都可能迫使系统更新。

---

## 5. 十条运行原则

1. **允许弱输入**：概念、一句话、一点感觉都能开始。
2. **不把澄清工作甩回给人**：脑子空白时给具体支架，不连续开放式拷问。
3. **问题驱动，但不要求问题先存在**：问题可以在对话中生成。
4. **模型要真正改变判断**：不是为了展示知识而套模型。
5. **模型与证据分开**：思维工具决定怎样看，证据决定事实上是什么。
6. **后台复杂，前台简单**：一篇只打一颗钉子，模型名能藏就藏。
7. **外部资料 AI 自己补**：只有用户本人知道、且会改变文章的信息才问用户。
8. **母稿优先**：先有一个平台无关的 canonical draft，再做平台适配。
9. **发布是实验**：发布不是交卷，现实反馈进入下一轮。
10. **先创作，再优化系统**：连续真实 Case 暴露同一问题后再改流程。

---

## 6. 内容可以停在不同层级

不是每个 Seed 都要变成长文。

```text
L-1 Seed / Connection  一条还没成熟的连接
L0 Problem             一个值得继续的问题
L1 Insight Atom        100~500 字观点原子
L2 Short Content       小红书 / 微博 / X / 短视频口播
L3 Canonical Essay     公众号 / 长文母稿
L4 Reusable Asset      方法、Prompt、Skill、产品洞见、成熟 Model Card
```

如果材料只够 L1，就停在 L1。不要为了“完整”硬灌成 3000 字。

---

## 7. 周末最小运行方式

真正开始创作时只做这件事：

1. 打开 [`QUICKSTART.md`](./QUICKSTART.md)；
2. 选一个最近最有感觉的 Seed / Question；
3. 把它交给 Creator Copilot；
4. 一路聊到一个当前可承担的判断；
5. 需要事实时让 AI 自己调研；
6. 整理成母稿；
7. **只选 1 个主平台发布**；
8. 发布后记录一个真实反馈。

周末禁止：

- 做工作台；
- 预建 100 个 Model Card；
- 配复杂自动化；
- 同时运营四个平台；
- 为了“准备好”继续改 Prompt。

**V0.3 成功标准：这个周末真的产出并发布至少一条内容。**

---

## 8. 思维工具如何慢慢变成自己的

课程和 Skill 是高质量起点，不是收藏品，也不是圣经。

```text
真实问题
  ↓
thinking-router 调用一个工具
  ↓
它真的改变判断 / 行动
  ↓
现实验证 / 修正
  ↓
写回 Personal Model Card
  ↓
形成自己的触发器 / 边界 / 案例
  ↓
以后更容易自己 pass@1 想到
```

Model Card 分两层：

- **Source Layer**：忠实保存来源定义与边界；
- **Personal Layer**：自己的理解、触发信号、真实 Case、误用和修正。

详见 [`KNOWLEDGE_BASE.md`](./KNOWLEDGE_BASE.md)。

---

## 9. 文件导航

### 周末真正会用

- [`QUICKSTART.md`](./QUICKSTART.md) — 从一个 Seed 直接跑完一篇内容。
- [`PROMPT.md`](./PROMPT.md) — 单入口 Creator Copilot Prompt。
- [`WORKFLOW.md`](./WORKFLOW.md) — 六阶段主流程与后台退出条件。

### 出问题时再查

- [`INCUBATION.md`](./INCUBATION.md) — Seed-first 对话孵化细节。
- [`AI_PROTOCOL.md`](./AI_PROTOCOL.md) — AI 模式、人机边界和 Skill 路由。
- [`TEMPLATES.md`](./TEMPLATES.md) — 可选中间产物模板。
- [`KNOWLEDGE_BASE.md`](./KNOWLEDGE_BASE.md) — Obsidian / Markdown 沉淀方式。
- [`EVAL.md`](./EVAL.md) — 每 5 次再做一次系统评测。
- [`PLATFORMS.md`](./PLATFORMS.md) — 平台适配原则。
- [`INSPIRATION.md`](./INSPIRATION.md) — 对标创作者能力来源。

---

## 10. V0.3 的最终目标

不是建立一台越来越复杂的“内容机器”。

而是：

> **让真实好奇可以低压力启动，让高质量对话帮助问题浮现，让经过筛选的思维工具真正参与判断，让证据约束故事，让 AI 帮助表达而不夺走主体性，再让现实反馈持续训练人与系统。**

内容是可见产物；真正长期积累的是：**问题感、判断力、模型触发器、知识网络、作品、用户 Case 和更大的行动自由。**