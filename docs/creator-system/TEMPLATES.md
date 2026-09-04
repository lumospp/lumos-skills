# Templates — Creator System V0.2

这些模板不是为了把创作变成填表。只在对应阶段真的需要时使用；普通问题允许大量留空。

---

## 0. Seed / Incubation Note

只有一点模糊想法时，用这个就够了，不需要立刻建 Problem Card。

```markdown
# Seed

created: YYYY-MM-DD
source: self / conversation / learning / work / user / platform

## 原话 / 种子


## 为什么我停了一下（可空）


## 对话里逐渐长出的材料

- 我明确说过的：
- 我认可 / 修正过的：
- 真实例子：
- 出现的张力：
- AI 提出的候选连接：
- 需要查证：
```

目标：**允许很不完整。**

---

## 1. Crystallize Card

当 Seed 经过几轮对话开始有形状时再用：

```markdown
# Crystallize

真正聊出来的主题：
我似乎最在意的是：
核心张力：

候选真问题：
1.
2.
3.

候选核心判断：

已有案例 / 材料：

AI 提出但我尚未确认：

需要外部查证：

只有我能补充：
```

候选判断可以由 AI 从对话中提炼；用户只需要确认、修正或否定。

---

## 2. Capture / Problem Note

当已经形成值得继续研究的问题后，再建立 Problem ID。

```markdown
# P-YYYY-MMDD-XX 标题

status: captured
source: self / user / comment / platform / learning / work / conversation
created: YYYY-MM-DD

## 现象 / 原话


## 真问题


## 来源 Seed（如有）

```

---

## 3. Frame Card

```markdown
# 真问题

我这篇只想回答：

## 可观察现象


## 冲突


## 最小问题地图（按需）

目标：
时间尺度：
硬约束：
关键未知：
主要失败方式：
```

只填真正会改变题目的项目。

---

## 4. Research Card

```markdown
# Research

## 初始解释（有就写，没有不强制）


## 竞争解释

H1：
H2：
H3：

## Key Unknown

哪个未知最可能改变当前判断：
什么证据最能区分 H1/H2/H3：

## 最小证据表

| Claim / Hypothesis | Support | Challenge / Boundary | Confidence |
|---|---|---|---|
| | | | |

## 当前最可信解释


## 仍未知

```

固定纪律：**模型生成假说，证据裁决假说。**

---

## 5. Judge + Red Team Card

```markdown
# Judge

## Thinking Route

主工具：
它改变了什么：问题表示 / 判断标准 / 机制 / 行动 / 风险边界
为什么适用：

补充工具：
- 工具：
  工位：定题 / 定界 / 估计 / 找机制 / 造选项 / 找反作用 / 落地 / 查价值

异质反证工具：
它攻击什么：

如果删掉哪个工具后结论不变：

## AI 提炼的候选判断（如来自对话）

版本 A：
版本 B：
我确认 / 修正后：

## 当前判断

这是我当前认可的判断：
最关键依据：
这个判断不适用于：
什么证据会让我改变判断：

## Red Team

最强攻击：
更简单解释：
证据薄弱处：
最危险外推：
主要边界：
修正后的判断：
```

对于简单题，不需要创建这张卡。

---

## 6. Article Brief / Gap Check

当用户说“把刚才聊的整理成文章”时，AI 内部先检查：

```markdown
# Article Brief

真正主题：
用户已经认可的核心判断：
关键推理链：
用户自己的例子 / 原话 / 转折：
AI 提出但尚未确认：
需要外部查证：
只有用户能补充：

## Gap Check

- [ ] 外部事实缺口 → AI Research
- [ ] 只有用户知道且会改变文章 → 提 1~3 个具体问题
- [ ] 只是小细节 → 保守处理 / 删除 / 标明不确定

当前材料适合：L1 / L2 / L3
```

---

## 7. Canonical Draft Card

```markdown
# Canonical Draft

## 核心判断


## 1. 真实现象 / 冲突


## 2. 常见解释


## 3. 为什么不够


## 4. 更好的机制 / 解释


## 5. 现实案例


## 6. 边界 / 反例


## 7. 读者可以带走的判断 / 行动

```

写作时后台模型可以隐藏。**案例优先于术语，机制优先于模型名。**

---

## 8. Publish / Adapt Card

```markdown
# Publish

平台：
发布日期：
链接：

## 入口
用户为什么会停下来：

## 事实边界检查
平台稿有没有比母稿更夸张：
有没有把推断写成事实：
有没有删掉不可缺少的边界：
```

---

## 9. Review / Learn Card

```markdown
# Review

## 内容反馈

被反复引用 / 评论的点：
主要误解：
强反驳：
新案例 / 反例：
新 Seed / 新问题：

## 数据反馈

只保留 2~3 个真正需要看的指标：

## Update Condition 检查

发布前我说什么证据会让我改判：
现在是否出现：
- [ ] 没有，只是传播反馈
- [ ] 只修正量级
- [ ] 修正边界
- [ ] 足以推翻核心机制

判断更新：
是否需要回到 Research / Judge：

## AI 与流程复盘

AI 最有价值的步骤：
AI 最越界的步骤：
AI 有没有在我脑子空白时降低负担：
AI 有没有产生太多我只是被动点头的观点：
卡最久的步骤：
删掉哪个步骤会更轻：

## Thinking Learn

真正改变判断的主工具：
只是标签的工具：
我现在对这个工具有什么新的理解：
新增触发信号：
新增边界 / 反例：
是否值得写回 Model Card：
```

---

## 10. Personal Model Card

不要预先为 100 个模型逐一建卡。只有模型经过真实 Case 多次使用，或确实改变过重要判断时再建立。

```markdown
# 模型名

## Source Layer

来源：

### 来源定义


### 来源中的调用信号


### 来源中的核心机制


### 来源中的边界


## Personal Layer

### 我现在怎么理解它


### 我的真实触发信号


### 它最适合改变什么
问题表示 / 判断标准 / 机制 / 行动 / 风险边界：

### 它不能直接解释什么


### 我最容易怎么误用


### 最强竞争工具 / 反证工具


### 我真实用过的 Problem ID
- P-...

### 它曾经怎样改变过我的判断
- P-...：原判断 → 新判断

### 新 Case 带来的修正
- YYYY-MM-DD / P-...：
```

原则：**Source Layer 保真，Personal Layer 生长。**
