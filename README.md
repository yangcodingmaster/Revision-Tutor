# Revision Tutor · 复习导师

> A Claude skill for students who learn by understanding, not memorising.
>
> 专为"理解型学习者"设计的 Claude 复习技能。

---

## What is this? · 这是什么？

**English:** Revision Tutor is a Claude skill that acts as both a **patient explainer** during study and a **strict examiner** when you're ready to be tested. It's built around a specific learning loop:

1. Read your lecture notes / slides
2. Ask Claude to explain confusing concepts → understand deeply
3. Write it in your own words
4. Get quizzed → find your real blind spots

**中文：** 复习导师是一个 Claude skill，在学习时充当**耐心的解释器**，在你准备好接受检验时切换为**严格的考官**。它围绕一个具体的学习闭环设计：

1. 阅读讲义/课件
2. 请 Claude 解释不懂的概念 → 深度理解
3. 用自己的话写下来
4. 被拷问 → 找到真正的盲点

---

## Who is it for? · 适合谁？

- Students with **closed-book exams** requiring derivations or calculations
- Learners who understand concepts but need more **practice under pressure**
- Anyone studying **multiple related courses** with overlapping concepts
- Works for any subject: physics, chemistry, maths, economics, law, and more

---

- 需要参加**闭卷考试**（推导题/计算题）的学生
- 概念理解没问题但**练习量不足**的学习者
- 同时学**多门相关课程**、需要整合知识点的学生
- 适用于任何学科：物理、化学、数学、经济学、法律……

---

## How to use · 怎么使用

### 1. Configure your subject · 配置你的学科

At the start of a session (or in your `CLAUDE.md`), tell Claude:

```
I'm studying [subject]. My exams are [closed-book derivations / open-book / MCQ].
My courses are [Course A, Course B].
My weak point is [not enough calculation practice / concepts get confused / ...].
```

中文版：

```
我在学 [学科名]，考试类型是 [闭卷推导/开卷/选择题]，
课程包括 [课程A, 课程B]。
我的瓶颈是 [计算题练习不足/概念容易混淆/...]。
```

### 2. Study mode · 学习模式

Upload your lecture notes or just start asking questions. Claude explains every concept with three layers:

- **Intuitive picture** — what does this actually mean in plain language?
- **Mathematical structure** — key derivation steps, highlighting the tricky jumps
- **Exam angle** — how is this tested? ⚠️ marks high-frequency topics

After each explanation, Claude will gently ask:
> "Can you explain the core logic of [X] in your own words?"

If you're already writing notes or asking the next question, Claude skips this and won't interrupt your flow.

上传讲义后，Claude 会先给出章节骨架：
- 这个 topic 在解决什么核心问题？
- 主要概念/推导列表（只列名称）
- 考试热点 ⚠️

然后跟着你的节奏走，你问什么就解释什么。

### 3. Quiz mode · 拷问模式

Say **"quiz me"** / **"拷问我"** / **"I've finished [Chapter X]"**.

Claude switches to examiner mode and runs through:

1. **Concept distinction** (1 question): What's the difference between X and Y?
2. **Derivation / calculation from scratch** (2 questions): No notes, derive to the target result
3. **Variant question** (1 question, optional): Change one condition — what changes?

At the end you get a **blind spot report**:

```
=== [Chapter X] Report ===
✅ Solid: ...
⚠️ Review again: ...
❌ Real blind spots: ... (focus your revision here)
```

---

## Example conversation · 示例对话

**Learning mode · 学习模式**

> **User:** 我上传了量子力学第三章，帮我看一下
>
> **Claude:** 好，先给你章节骨架——
> 核心问题：如何处理哈密顿量中的微小扰动？
> 主要推导：一阶能量修正、二阶能量修正、一阶波函数修正
> 考试热点 ⚠️：一阶能量修正推导、简并 vs 非简并情况
>
> **User:** 一阶微扰论的能量修正是怎么推出来的？
>
> **Claude:** [核心图景] 把哈密顿量拆成已知部分加小扰动，对本征值做级数展开...
> [数学结构] 关键跳跃：左乘 ⟨n⁰| 后正交性消掉了未知项，直接得到 E¹ = ⟨n⁰|H'|n⁰⟩
> [考试视角] ⚠️ 高频：推导时必须说清楚为什么正交性让左边只剩 E¹
> "你现在能用自己的话说出一阶修正的核心逻辑吗？"

**Quiz mode · 拷问模式**

> **User:** 我学完了，拷问我
>
> **Claude:** 考官模式开启。第一题：简并微扰论和非简并微扰论，在处理方法上的根本区别是什么？
>
> **User:** 简并情况下要先对角化扰动矩阵……
>
> **Claude:** 正确部分：对角化方向是对的。不过你跳过了一步——为什么必须先对角化？你为什么这么写？
> *[定位断点，纠正，进入下一题]*
>
> **Claude:** === 第三章 检验报告 ===
> ✅ 掌握：一阶能量修正推导、波函数正交性应用
> ⚠️ 需要再看：二阶修正的求和项
> ❌ 真正的盲点：简并情况的前置步骤（为什么要先对角化）

---

## Customisation · 自定义

Edit `SKILL.md` to add your own must-know derivations list:

```markdown
## 必会推导清单

**[Course 1 name/code]**: [Derivation A] / [Derivation B] / [Derivation C]
**[Course 2 name/code]**: [Derivation A] / [Derivation B]

**跨科重叠（学一次用两次）**:
- [Concept X]: [Course 1 angle] ↔ [Course 2 angle]
```

---

## Installation · 安装

**Claude Code:**

```bash
# Copy SKILL.md to your skills directory
cp SKILL.md ~/.claude/skills/revision-tutor.md
```

The skill activates automatically when you start a revision session.

**claude.ai:**

Paste the contents of `SKILL.md` at the start of your conversation, or attach it as a file.

---

*Built for students who take their exams seriously.*
