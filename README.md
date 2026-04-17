# Revision Tutor

> A Claude skill for students who learn by understanding, not memorising.
>
> 专为"理解型学习者"设计的 Claude 复习技能。

📄 [SKILL.md（中文版）](./SKILL.md) · [SKILL.en.md (English)](./SKILL.en.md)

---

## What is this? · 这是什么？

 Revision Tutor is a Claude skill that acts as both a **patient explainer** during study and a **strict examiner** when you're ready to be tested. It's built around a specific learning loop:

1. Read your lecture notes / slides
2. Ask Claude to explain confusing concepts → understand deeply
3. Write it in your own words
4. Get quizzed → find your real blind spots

Revision Tutor是一个 Claude skill，在学习时充当**耐心的解释器**，在你准备好接受检验时切换为**严格的考官**。围绕一个具体的学习闭环设计：

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

### 1. Install · 安装

**Claude Code:**
```bash
cp SKILL.md ~/.claude/skills/revision-tutor.md
# English version:
cp SKILL.en.md ~/.claude/skills/revision-tutor.md
```

**claude.ai:** Paste the contents of `SKILL.md` or `SKILL.en.md` at the start of your conversation.

### 2. Configure your subject · 配置学科

Tell Claude at the start of a session:

```
我在学 [学科名]，考试类型是 [闭卷推导/开卷/选择题]。
课程包括 [课程A, 课程B]。我的瓶颈是 [计算题不足/概念混淆]。
```

```
I'm studying [subject]. Exams are [closed-book derivations / open-book / MCQ].
Courses: [Course A, Course B]. Weak point: [not enough practice / concepts get confused].
```

### 3. Study mode · 学习模式

Upload lecture notes or ask about a concept. Claude explains with three layers:
- **Core picture** — intuition in one sentence
- **Mathematical structure** — key steps, flagging the tricky jump
- **Exam angle** — how this is tested ⚠️

### 4. Quiz mode · 拷问模式

Say **"quiz me"** / **"拷问我"** / **"I've finished [Chapter X]"**.

Claude quizzes you with concept distinctions, derivations from scratch, and variant questions — prioritising your weak spots, not a fixed order.

At the end you get a **blind spot report** and a **Revision Card** to paste into your next session.

---

## Example conversation · 示例对话

**Learning mode · 学习模式**

> **User:** 我上传了量子力学第三章
>
> **Claude:** 在我给你骨架之前——你觉得这章主要解决什么问题？猜猜主要推导有哪些？
>
> **User:** 应该是扰动相关的？有一阶修正？
>
> **Claude:** 猜对了核心方向。完整骨架是：核心问题是如何处理不可精确求解的哈密顿量；主要推导：一阶能量修正、二阶能量修正、一阶波函数修正；考试热点 ⚠️：一阶推导全过程、简并 vs 非简并的处理差异。
>
> **User:** 一阶能量修正怎么推？
>
> **Claude:** [核心图景] 把哈密顿量拆成已知加扰动，对本征值做级数展开...
> [数学结构] 关键跳跃：左乘 ⟨n⁰| 后正交性消掉未知项，直接得到 E¹ = ⟨n⁰|H'|n⁰⟩
> [考试视角] ⚠️ 高频：必须说清楚正交性为什么让左边只剩 E¹

*(After 2–3 concepts)*
> **Claude:** 刚才讲的一阶修正，现在不看上面，你能说出核心逻辑吗？

**Quiz mode · 拷问模式**

> **User:** 拷问我
>
> **Claude:** 考官模式开启。根据你刚才学的，先从薄弱点开始——简并和非简并微扰论的根本区别是什么？
>
> **User:** 简并情况要先对角化……
>
> **Claude:** 方向对。不过你跳过了关键前提——为什么必须先对角化？你为什么这么写？
>
> *(End of session)*
>
> **Claude:**
> ```
> === 第三章 检验报告 ===
> ✅ 掌握：一阶能量修正推导、正交性应用
> ⚠️ 需要再看：二阶修正的求和项
> ❌ 真正的盲点：简并情况的前置步骤
>
> === 复习记录卡 · 第三章 ===
> 上次盲点：简并微扰前置对角化步骤
> 建议下次先考：简并 vs 非简并处理差异
> ```

---

## What's in v3 · v3 更新内容

- **检验时机修正**：不再在解释后立即提问，改为解释 2~3 个概念后回头检验（修正"流利性幻觉"）
- **讲义上传预激活**：先让用户猜骨架，再对照给出（pre-testing effect）
- **灵活出题顺序**：根据薄弱点动态调整题序，不再固定
- **卡住协议**：三级提示阶梯，不直接给答案
- **计时模式**：可选，模拟真实考试压力
- **复习记录卡**：每次结束生成可粘贴的记录，解决跨对话无记忆问题

---

*Built for students who take their exams seriously.*
