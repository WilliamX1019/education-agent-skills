---
# AGENT SKILLS STANDARD FIELDS (v2)
name: lesson-opening-designer
description: "设计激活先验知识并将先前学习与今日内容相连的课堂导入。适用于规划课堂热身、提取练习导入或先行组织者时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "explicit-instruction/lesson-opening-designer"
skill_name: "课堂导入设计师"
domain: "explicit-instruction"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Rosenshine (2012) — Principles of Instruction, Principle 1: begin a lesson with a short review of previous learning"
  - "Ausubel (1960) — The use of advance organizers in the learning and retention of meaningful verbal material"
  - "Marzano (2007) — The Art and Science of Teaching: activating prior knowledge and setting purpose"
  - "Agarwal et al. (2012) — Classroom-based retrieval practice improves learning with minimal lesson time"
  - "Hattie (2009) — Visible Learning: prior knowledge activation as foundational to new learning"
input_schema:
  required:
    - field: "todays_topic"
      type: "string"
      description: "本节课将要教授的内容"
    - field: "previous_learning"
      type: "string"
      description: "上节课或近期课程中教授过且与本课相连的内容"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "opening_time"
      type: "string"
      description: "可用于课堂导入的分钟数（默认：10 分钟）"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：记忆保持数据、上节课常见缺口"
    - field: "lesson_objectives"
      type: "string"
      description: "本节课的具体学习目标"
    - field: "assessment_data"
      type: "string"
      description: "来自上下文引擎：上节课的离堂小测数据"
output_schema:
  type: "object"
  fields:
    - field: "retrieval_starter"
      type: "object"
      description: "复习先前学习的提取练习活动"
    - field: "prior_knowledge_bridge"
      type: "string"
      description: "如何将先前学习连接到今日新内容"
    - field: "learning_intention"
      type: "string"
      description: "如何界定今日学习意图"
    - field: "opening_script"
      type: "string"
      description: "课堂导入的完整计时脚本"
chains_well_with:
  - "retrieval-practice-generator"
  - "explicit-instruction-sequence-builder"
  - "spaced-practice-scheduler"
  - "checking-for-understanding-protocol-designer"
teacher_time: "3 分钟"
tags: ["lesson-opening", "retrieval", "prior-knowledge", "advance-organiser", "lesson-planning"]
---

# 课堂导入设计师

## 本技能的作用

生成一个包含三大要素的循证课堂导入：复习先前学习的提取练习热身、连接学生已知内容与今日新知的先验知识桥梁，以及在不提前剧透所有答案的前提下确立学习目的的学习意图界定。输出是一份针对课程前 8–12 分钟的完整计时脚本。AI 在此尤为有价值，因为高效的课堂导入必须在紧凑的时间限制内同时服务于三个功能（提取、激活、定调），而且提取问题必须经过精心挑选，精准瞄准今日课程所依赖的最关键先验知识——不只是泛泛地复习“上次学了什么”，而是专门激活今日课程将要依托的知识。

## 循证基础

Rosenshine (2012) 将每日复习列为有效教学原则第 1 条：“最有效的教师会以对先前所学材料的五到八分钟复习作为每节课的开端。” 这服务于双重目的——通过提取练习巩固记忆保持，并激活新学习将要依附的先验知识图式。Ausubel (1960) 证明，先行组织者（advance organisers）——在新内容之前呈现的概念框架——通过提供“观念支架”帮助学习者组织新传入的信息，从而显著提升学习效果。Marzano (2007) 指出，将新内容与先验知识相连是一项基础教学策略，但前提是这些联系必须被明确建立（而非想当然）。Agarwal 等 (2012) 表明，课初简短的提取练习能以极少的时间成本提升记忆保持——哪怕 5 分钟的提取也能产生可测量的收益。Hattie (2009) 将先验知识确定为预测新学习的最强单一指标——学生已经知道什么，决定了他们接下来能学什么。

## 输入模式

教师必须提供：
- **Today's topic（今日主题）：** 今天要教什么。*例如："Adding fractions with unlike denominators" / "The causes of World War I: the alliance system" / "Writing a balanced argument paragraph"*
- **Previous learning（先前学习）：** 近期教过且相连的内容。*例如："Last lesson: equivalent fractions. Last week: adding fractions with like denominators" / "Last lesson: the assassination of Archduke Franz Ferdinand"*
- **Student level（学生水平）：** 年级。*例如："Year 8"*

可选（如上下文引擎可用则自动注入）：
- **Opening time（导入时间）：** 可用分钟数（默认 10）
- **Student profiles（学生档案）：** 记忆保持数据、先前课程缺口
- **Lesson objectives（学习目标）：** 今日具体学习目标
- **Assessment data（评估数据）：** 上节课的离堂小测数据

## Prompt

```
You are an expert in lesson design and the science of learning, with deep knowledge of Rosenshine's (2012) Principles of Instruction (Principle 1: daily review), Ausubel's (1960) advance organisers, and Agarwal et al.'s (2012) research on classroom retrieval practice. You understand that the lesson opening is the highest-leverage 10 minutes of any lesson — it determines whether students can access new content by activating the prior knowledge it depends on.

Your task is to design a lesson opening for:

**Today's topic:** {{todays_topic}}
**Previous learning:** {{previous_learning}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Opening time:** {{opening_time}} — if not provided, design for 10 minutes.
**Student profiles:** {{student_profiles}} — if not provided, assume a typical mixed-ability class where some students will have forgotten key content from the previous lesson.
**Lesson objectives:** {{lesson_objectives}} — if not provided, infer the learning objective from today's topic and frame it as a clear, student-facing intention.
**Assessment data:** {{assessment_data}} — if provided, use this to target retrieval questions toward the specific gaps identified. If not provided, target the prerequisite knowledge most critical for today's lesson.

Apply these evidence-based principles:

1. **Retrieval starter — not re-teaching (Rosenshine, 2012; Agarwal et al., 2012):**
   - The opening should require students to RETRIEVE previous learning from memory, not re-read or re-listen.
   - Questions should target the specific prior knowledge that today's lesson depends on — if today's lesson builds on equivalent fractions, retrieve equivalent fractions, not everything from last week.
   - Low stakes: no grades, no pressure. The purpose is strengthening memory and identifying gaps.
   - 5–6 minutes maximum for the retrieval activity.

2. **Prior knowledge bridge — make connections explicit (Ausubel, 1960; Marzano, 2007):**
   - After retrieval, explicitly connect previous learning to today's new content.
   - Do not assume students see the connection. State it: "You've just shown you can find equivalent fractions. Today we need that skill because..."
   - Use an advance organiser if appropriate: a brief conceptual framework that shows where today's content fits in the bigger picture.

3. **Learning intention — set purpose, not procedure (Hattie, 2009):**
   - Frame what students will learn, not what they will do. "By the end of this lesson, you will be able to add fractions with different denominators" (learning) is better than "Today we will complete a worksheet on adding fractions" (activity).
   - Keep it concise — one sentence.
   - Optionally include success criteria: "You'll know you've got it when you can..."

4. **Pace and energy:**
   - The opening sets the tone. Keep it brisk, purposeful, and interactive.
   - Students should be thinking within the first 60 seconds — no long teacher introductions.
   - Aim for the retrieval starter to begin as students enter the room (a "Do Now" displayed on the board).

Return your output in this exact format:

## Lesson Opening: [Today's Topic]

**For:** [Student level]
**Time:** [Opening duration]
**Builds on:** [Previous learning]

### On the Board as Students Enter (Do Now)
[The retrieval activity displayed on the board — students begin immediately on arrival]

### Retrieval Starter (X minutes)
[The retrieval questions, expected answers, and what to do if students struggle]

### Prior Knowledge Bridge (X minutes)
[Teacher script connecting retrieval to today's new content]

### Learning Intention (X minutes)
[How to frame today's learning — what students will be able to do, and how they'll know they've succeeded]

### Complete Timed Script
[The full opening as a single timed sequence the teacher can follow]

**Self-check before returning output:** Verify that (a) the retrieval starter requires genuine retrieval from memory, not re-reading, (b) retrieval questions target the specific prior knowledge today's lesson needs, (c) the bridge between prior and new learning is explicit, (d) the learning intention describes learning, not activity, and (e) the total timing fits within the stated opening time.
```

## 示例输出

**场景：** *Today's topic: "Adding fractions with unlike denominators" / Previous learning: "Last lesson: finding equivalent fractions (multiplying numerator and denominator by the same number). Two lessons ago: adding fractions with like denominators." / Student level: "Year 7" / Opening time: "10 minutes"*

---

## 课堂导入：异分母分数相加

**适用对象：** 七年级数学
**时间：** 10 分钟
**衔接基础：** 等值分数（上节课）、同分母分数相加（两节课前）

### 学生进教室时黑板上的任务（Do Now）

*在学生到达前展示在黑板或投影上：*

**提取挑战——不看笔记，不翻书，凭记忆尽力完成。**

1. Find an equivalent fraction for 3/4 with a denominator of 12.
2. Find an equivalent fraction for 2/5 with a denominator of 15.
3. Calculate: 3/8 + 2/8 = ?
4. Calculate: 5/12 + 4/12 = ?
5. **思考题：** Why can you add the fractions in Q3 and Q4 easily? What makes them straightforward?

### 提取练习热身（5 分钟）

**第 1–2 题**瞄准等值分数——这是今日课程的关键先备技能。如果学生不能流利地求出等值分数，就无法进行异分母分数相加。

**第 3–4 题**瞄准同分母分数相加——这是今日课程将要延伸的技能。学生需要记住：当分母相同时，只需分子相加，分母保持不变。

**第 5 题**是一道元认知桥梁题——它要求学生阐述“为什么”同分母加法很容易，从而引出今日的挑战：当分母“不同”时该怎么办？

**预期答案：**
1. 9/12（分子分母同乘 3）
2. 6/15（分子分母同乘 3）
3. 5/8
4. 9/12（可化简为 3/4，但接受 9/12）
5. "Because the denominators are the same, so you just add the top numbers."

**如果学生在 Q1–2（等值分数）上遇到困难：**
不要急于进入新内容。花 3 分钟复习："What do we multiply the numerator AND denominator by to make an equivalent fraction?" 使用迷你白板再做 2 道快速练习，然后再架桥引入新课。如果等值分数不稳固，今日内容将无法理解。

**如果学生在 Q3–4（同分母加法）上遇到困难：**
快速回顾："When the denominators are the same, we're adding pieces that are the same size. 3 eighths + 2 eighths = 5 eighths, just like 3 apples + 2 apples = 5 apples." 再做 2 道快速例题，然后继续。

### 先验知识桥梁（2 分钟）

"Hands up if you got Q5 right — you said something like 'the denominators are the same.' Exactly. When the denominators match, addition is straightforward because the pieces are the same size. Three eighths plus two eighths — we're adding pieces of the same size.

But what if I asked you: what is 1/3 + 1/4? The pieces are DIFFERENT sizes — a third is not the same as a quarter. You can't just add 1 + 1 and get 2/7 — that doesn't work. [在黑板上写下 1/3 + 1/4 ≠ 2/7。] So what do we need to do first?

[停顿，让学生思考，部分学生会看出来。]

We need to make the denominators the same — which means we need EQUIVALENT FRACTIONS. That skill you just practised in Q1 and Q2? That's exactly what we need now. Today, we're combining two skills you already have — finding equivalent fractions AND adding fractions — to solve a new type of problem."

### 学习意图（1 分钟）

"By the end of this lesson, you will be able to add two fractions that have different denominators by finding a common denominator first.

You'll know you've got it when you can solve a problem like 2/3 + 3/5 without help, and explain to someone else why you need a common denominator.

Let's go."

### 完整计时脚本

| 时间 | 课堂进程 |
|------|-------------|
| 0:00 | 学生进入教室。黑板上已展示提取挑战。学生立即开始——不等待，不因点名而停顿。教师在门口迎候并指引："Starter is on the board. Begin." |
| 0:00–5:00 | 学生在安静中完成 Q1–5（提取条件——不看笔记，不讨论）。教师巡视，扫视 Q1–2 的准确率，识别 2–3 名在等值分数上有困难的学生。 |
| 5:00–5:30 | "Pens down. Let's check." 快速核对答案：Q1: "9/12 — show me on whiteboards." Q2: "6/15." Q3: "5/8." Q4: "9/12." 30 秒扫视。 |
| 5:30–6:00 | "Q5 — why were Q3 and Q4 easy?" 随机点名一名学生。倾听关键词："the denominators are the same." |
| 6:00–8:00 | 先验知识桥梁（见上文脚本）。在黑板上写下 1/3 + 1/4。让学生看到问题所在。将等值分数与新挑战联系起来。 |
| 8:00–8:30 | 陈述学习意图，并将其写在黑板上。 |
| 8:30–10:00 | 过渡到“我做”阶段："Watch me solve 1/3 + 1/4. I'm going to think out loud so you can follow my reasoning." |

---

## 已知局限性

1. **提取练习热身只有在学生确实学过先备内容时才有效。** 如果学生缺席了等值分数那节课，或者先备知识未能有效教会，提取练习热身就会暴露出需要在学习今日内容前先行弥补的缺口。这是一个有用的特征（诊断信息），而非缺陷——但它可能需要教师花比原计划更多的时间复习，从而压缩主课时间。

2. **“进门即做（Do Now）”热身需要一贯的课堂常规。** 如果学生没有养成进教室就立即动笔的习惯，最初的 2–3 分钟就会浪费在安顿、发指令和反复提醒上。本课堂导入设计假设已经建立了稳定常规。建立这一常规属于课堂管理任务，而非教学设计任务。

3. **先验知识桥梁是针对这一特定内容衔接编写脚本的。** 如果教师没有遵循假定的教学序列（等值分数 → 同分母加法 → 异分母加法），这座桥梁就无法精准对接。教师必须核实“先前学习”字段准确反映了实际“教过”的内容，而不仅仅是原定计划。
