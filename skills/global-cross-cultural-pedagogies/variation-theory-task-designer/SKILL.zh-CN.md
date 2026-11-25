---
# AGENT SKILLS STANDARD FIELDS (v2)
name: variation-theory-task-designer
description: "运用变式理论（variation theory）通过对比、分离和融合来设计教学任务，以教授概念的关键特征。适用于学生混淆相似概念或未能辨别核心区别时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/variation-theory-task-designer"
skill_name: "变式理论任务设计师"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Marton (2015) — Necessary Conditions of Learning"
  - "Marton & Booth (1997) — Learning and Awareness"
  - "Lo (2012) — Variation Theory and the Improvement of Teaching and Learning"
  - "Kullberg, Runesson Kempe & Marton (2017) — What is made possible to learn when using the variation theory of learning in teaching mathematics?"
  - "Gu, Huang & Marton (2004) — Teaching with variation: a Chinese way of promoting effective Mathematics learning"
input_schema:
  required:
    - field: "object_of_learning"
      type: "string"
      description: "学生需要学会辨别的具体概念、技能或区分——任务结束后他们应当能看清的内容"
    - field: "common_confusion"
      type: "string"
      description: "学生通常混淆、混同或未能区分的内容——他们遗漏的关键特征"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及先验知识"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "current_task"
      type: "string"
      description: "需要运用变式理论重新设计的现有任务或活动"
    - field: "lesson_context"
      type: "string"
      description: "本任务在教学序列中的位置——引入、巩固、复习"
output_schema:
  type: "object"
  fields:
    - field: "variation_analysis"
      type: "object"
      description: "对学习对象（object of learning）的分析——为了让学生辨别关键特征，什么必须变化、什么必须保持不变"
    - field: "task_sequence"
      type: "array"
      description: "运用系统性变式的例题/任务序列——对比、分离、泛化、融合"
    - field: "teacher_guidance"
      type: "object"
      description: "如何呈现变式——引导学生关注什么、提出什么问题"
    - field: "assessment_check"
      type: "string"
      description: "如何验证学生现在能够辨别该关键特征"
chains_well_with:
  - "explicit-instruction-sequence-builder"
  - "worked-example-fading-designer"
  - "cpa-sequence-designer"
  - "diagnostic-question-generator"
  - "curriculum-knowledge-architecture-designer"
teacher_time: "3 分钟"
tags: ["variation-theory", "Marton", "discernment", "contrast", "critical-features", "Hong-Kong", "Sweden", "mathematics-education"]
---

# 变式理论任务设计师

## 本技能的作用

运用变式理论（Variation Theory）设计学习任务——这是由 Ference Marton 及其在瑞典和香港的同事发展起来的框架，解释学习者如何通过“变化与不变”的系统性模式来辨别概念的关键特征。核心原则看似简单却极具力量：要觉察某一个特征，学习者必须体验到它在“变化”，而与此同时其他特征保持“不变”。如果所有东西同时变化，没有任何单一特征会凸显出来。本技能分析学习对象以识别其关键特征（学生必须辨别之物），识别常见混淆（学生未能区分之处），并设计一组例题序列，系统性地使恰当的维度发生变化或保持不变，从而让关键特征清晰显现。输出包括变式分析、运用四种变式模式（对比、分离、泛化、融合）的任务序列、引导注意变式的教师指导以及评估检查。AI 在此尤为有价值，因为设计有效的变式序列需要同时统筹什么变化、什么不变以及序列中每个例题与前后例题的关系——这是一个适合系统性设计的组合难题。

## 循证基础

Marton & Booth (1997) 奠定了理论基础：学习是一个人体验或理解事物方式的变化，而这种变化要求学习者辨别出先前未曾注意的特征。辨别需要变式——你无法注意到从未变化过的特征。Marton (2015) 将此形式化为四种变式模式：对比（CONTRAST，将“它是什么”与“它不是什么”并置体验）、分离（SEPARATION，保持其他维度不变而只变化一个关键维度，以孤立出关键特征）、泛化（GENERALISATION，保持关键特征不变而变化无关特征，以表明概念跨语境成立）以及融合（FUSION，同时变化多个关键特征，以发展整合性理解）。Lo (2012) 展示了变式理论在香港课堂教学设计中的应用，证明使用系统性变式设计课程的教师比只使用无系统多样化例题的教师能产出显著更好的学生理解——重要的不是多样性本身，而是变式的“模式”。Kullberg, Runesson Kempe & Marton (2017) 将变式理论应用于数学教育，展示每次只变化一个特征的精心排序例题如何帮助学生辨别原本会错过的数学结构。Gu, Huang & Marton (2004) 记录了中国的“变式教学”传统，表明中国数学教学早在 Marton 将该理论形式化之前，就已系统性地运用变式来发展概念理解。

## 输入模式

教师必须提供：
- **Object of learning（学习对象）：** 学生需要学会辨别的内容。*例如："The difference between area and perimeter — students confuse the two because they both involve measuring shapes" / "When to use 'effect' vs 'affect' — students use them interchangeably" / "The distinction between speed and velocity — students treat them as synonyms"*
- **Common confusion（常见混淆）：** 学生常弄错的地方。*例如："Students think bigger shapes always have bigger perimeters" / "Students default to 'effect' in all contexts" / "Students don't understand why direction matters in velocity"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级及先验知识
- **Subject area（学科领域）：** 课程学科
- **Current task（当前任务）：** 需要重新设计的现有任务
- **Lesson context（课堂语境）：** 本任务在教学序列中的位置

## Prompt

```
You are an expert in variation theory as developed by Ference Marton and colleagues, with deep knowledge of Marton & Booth (1997), Marton (2015), Lo (2012), Kullberg et al. (2017), and the Chinese tradition of teaching with variation (Gu, Huang & Marton, 2004). You understand that learning requires discernment, discernment requires variation, and effective variation is SYSTEMATIC — not random variety, but carefully designed patterns where specific features vary while others are held constant.

CRITICAL PRINCIPLES:
- **Identify the critical feature.** The object of learning has multiple features, but the CRITICAL feature is the one students must discern to understand the concept. Everything else in the design serves to make this feature visible.
- **Use the four patterns of variation:**
  - **Contrast:** Show what the concept IS alongside what it IS NOT (e.g., show area AND perimeter of the same shape, so the difference becomes visible)
  - **Separation:** Vary the critical feature while holding everything else constant (e.g., change the perimeter of a shape while keeping the area the same — this separates perimeter from area in the learner's experience)
  - **Generalisation:** Hold the critical feature constant while varying irrelevant features (e.g., show that area = length × width works for rectangles of different sizes, orientations, and colours — the concept generalises across surface variations)
  - **Fusion:** Vary multiple critical features simultaneously (e.g., vary both area and perimeter together, so students must attend to both — this develops integrated understanding)
- **Sequence matters.** Contrast first (to create awareness), then separation (to isolate), then generalisation (to extend), then fusion (to integrate). This sequence scaffolds discernment from initial noticing to full understanding.
- **Less is more.** A few carefully chosen examples with systematic variation are more powerful than many random examples. Each example should differ from the previous one in a deliberate, minimal way.

Your task is to design a variation theory task for:

**Object of learning:** {{object_of_learning}}
**Common confusion:** {{common_confusion}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the object of learning.
**Current task:** {{current_task}} — if not provided, design a new task from scratch.
**Lesson context:** {{lesson_context}} — if not provided, design for an introduction to the distinction.

Return your output in this exact format:

## Variation Theory Task: [Object of Learning]

**Object of learning:** [What students must discern]
**Critical feature:** [The specific feature that must become visible]
**Common confusion:** [What students currently conflate]

### Variation Analysis

[Analysis of the object of learning: what are its features, which is the critical feature, what must vary and what must remain invariant for the critical feature to become visible]

### Task Sequence

**Phase 1 — Contrast (What IS it vs. what ISN'T it?)**
[Examples that place the concept alongside its common confusion, making the difference visible]

**Phase 2 — Separation (Isolating the critical feature)**
[Examples where ONLY the critical feature varies while everything else stays the same]

**Phase 3 — Generalisation (The concept across contexts)**
[Examples where the critical feature stays constant but surface features vary — showing the concept holds across different cases]

**Phase 4 — Fusion (Integrating multiple features)**
[Examples where multiple features vary simultaneously — requiring students to attend to and coordinate several dimensions]

### Teacher Guidance

[How to present these examples — what to point to, what questions to ask, how to draw students' attention to the variation]

### Assessment Check

[A task that tests whether students can now discern the critical feature — distinguishing cases that they previously confused]

**Self-check before returning output:** Verify that (a) the critical feature is clearly identified, (b) each phase uses the correct pattern of variation, (c) within each phase only the intended feature varies while others are held constant, (d) the sequence moves from contrast through separation and generalisation to fusion, (e) the examples are minimal — each differing from the last in a deliberate way, and (f) the assessment check tests discernment of the critical feature specifically.
```

## 示例输出

**场景：** *Object of learning: "The difference between area and perimeter — students need to understand that these are two different measurements of a shape, not two words for the same thing" / Common confusion: "Students assume that if you make a shape bigger, both the area and the perimeter increase — they don't realise that you can change one without changing the other" / Student level: "Year 7, beginning of a geometry unit — students can calculate area and perimeter separately but confuse them conceptually" / Subject area: "Mathematics"*

---

## 变式理论任务：面积 vs. 周长

**学习对象：** 面积与周长的区别——它们是彼此独立的两个度量，可以各自独立变化
**关键特征：** 面积与周长可以独立变化——你可以在减小面积的同时增大周长，或在改变一个的同时保持另一个不变
**常见混淆：** 学生认为面积和周长正相关——“图形越大，所有数值都越大”

### 变式分析

面积和周长都是二维图形的属性，但它们度量的是不同的东西：面积度量内部所占空间（平方单位），周长度量边缘一圈的长度（长度单位）。学生必须辨别的关键特征是这两个度量彼此“独立”——改变一个并不必然改变另一个。这有悖直觉，因为在日常经验中，“更大”的物体往往在各个维度上都更大。因此，任务必须通过展示“一个变化而另一个不变”的案例来使这种独立性可见——如果学生见到的每个例题都是面积和周长同时增大，他们永远不会发现这一点。

变式维度包括：
- **面积**（关键维度 1）：图形内部的空间
- **周长**（关键维度 2）：边缘一圈的距离
- **图形类型**（无关维度）：矩形、L 形等
- **朝向**（无关维度）：旋转、翻转
- **网格大小**（无关维度）：视觉呈现方式

### 任务序列

**第 1 阶段——对比（什么是面积 vs. 什么是周长？）**

呈现两个完全相同的矩形（方格纸上 3 × 4）。在矩形 A 上，用蓝色涂满内部方格；在矩形 B 上，用红色描出外围边缘。

| 图形 | 蓝色（内部） | 红色（边缘） |
|---|---|---|
| 矩形 A（3 × 4） | 12 个方格涂色 | — |
| 矩形 B（3 × 4） | — | 描出 14 个单位长 |

提问："Rectangle A shows 12. Rectangle B shows 14. They're the SAME shape — why are the numbers different?"

这一对比使“面积和周长是同一个图形的不同度量”清晰可见。图形本身不变，度量类型变化。

**第 2 阶段——分离（面积不变而改变周长）**

呈现四个全部由恰好 12 块正方形瓦片拼成的图形（因此面积全为 12），但排列方式不同：

| 图形 | 排列方式 | 面积 | 周长 |
|---|---|---|---|
| 图形 A | 3 × 4 矩形 | 12 | 14 |
| 图形 B | 2 × 6 矩形 | 12 | 16 |
| 图形 C | 1 × 12 矩形 | 12 | 26 |
| 图形 D | L 形（3×3 带 3×1 延伸） | 12 | 16 |

提问："Every shape has exactly 12 squares inside. But look at the perimeters. What's happening?"

这将周长从面积中分离出来：面积“不变”（始终为 12），周长“变化”（14、16、26、16）。学生必须直面“面积相同并不意味着周长相同”的事实。关键特征——独立性——被孤立出来。

接着反转：呈现四个周长全为 16、但面积不同的图形：

| 图形 | 排列方式 | 周长 | 面积 |
|---|---|---|---|
| 图形 E | 4 × 4 正方形 | 16 | 16 |
| 图形 F | 2 × 6 矩形 | 16 | 12 |
| 图形 G | 1 × 7 矩形 | 16 | 7 |
| 图形 H | T 形 | 16 | 10 |

提问："Every shape has the same perimeter — 16 units around the edge. But look at the areas. What do you notice?"

这从另一个方向确认了分离：周长相同并不意味着面积相同。

**第 3 阶段——泛化（独立性适用于所有图形类型）**

展示面积与周长的独立性并不局限于矩形：

| 图形 | 类型 | 面积 | 周长 |
|---|---|---|---|
| 图形 I | 点阵纸上的三角形 | 6 | 12 |
| 图形 J | 另一个三角形 | 6 | 14.5 |
| 图形 K | 不规则四边形 | 6 | 16 |
| 图形 L | 五边形 | 6 | 13.2 |

提问："These are all different types of shapes — triangles, quadrilaterals, pentagons. They all have area 6. Do they all have the same perimeter?"

关键特征（独立性）保持不变——它对“所有”图形都成立，而不仅仅是矩形。表面特征（图形类型）发生变化。这将该原理泛化到矩形这一特定情境之外。

**第 4 阶段——融合（同时变化面积与周长）**

呈现一组面积和周长“同时”变化的图形，要求学生同时关注两者：

| 图形 | 面积 | 周长 | 面积比图形 M 大还是小？ | 周长比图形 M 大还是小？ |
|---|---|---|---|---|
| 图形 M | 12 | 14 | — | — |
| 图形 N | 8 | 18 | 更小 | 更大 |
| 图形 O | 15 | 16 | 更大 | 更大 |
| 图形 P | 20 | 14 | 更大 | 相同 |
| 图形 Q | 6 | 14 | 更小 | 相同 |

提问："Look at Shape N compared to Shape M. The area is smaller but the perimeter is bigger. How is that possible? Can you draw Shape N?"

接着："Shape P has a much bigger area than Shape M but the SAME perimeter. Shape Q has a much smaller area but also the same perimeter. What does this tell us about the relationship between area and perimeter?"

这一阶段将两个维度融合在一起——学生必须独立追踪面积与周长，并认识到所有组合都是可能的（面积更大但周长更小、面积相同但周长不同等）。

### 教师指导

**如何呈现序列：**
1. 使用方格纸或在黑板上展示网格。让图形“可见”——不要只给数字。学生需要同时“看到”面积（涂色方格）和周长（描出的边缘）。
2. 在每个阶段，“并排”呈现例题，而不是一次只呈现一个。变式的力量来自比较——学生必须同时看到各个例题，才能注意到什么变了、什么没变。
3. 在每一次过渡时都问："What's the same? What's different?" 这是变式理论最核心的问题。训练学生寻找“同与异”的模式。
4. 不要提前解释规律——让学生自己发现。呈现例题，提出问题，等待。如果学生卡住，增加一个让规律更清晰的例题。在学生有机会自己看出来之前，不要直接告诉他们“面积和周长是独立的”。

**核心提问：**
- 第 1 阶段："They're the same shape. Why are the numbers different?"
- 第 2 阶段："The area is always 12. What happens to the perimeter?" / "The perimeter is always 16. What happens to the area?"
- 第 3 阶段："Does this work for all shapes, or just rectangles?"
- 第 4 阶段："Can you have a big area with a small perimeter? A small area with a big perimeter? Prove it with a drawing."

**常见学生回答及应对：**
- "Bigger shapes have bigger perimeters" → 将图形 N（面积 8，周长 18）放在图形 M（面积 12，周长 14）旁边。"Is Shape N 'bigger'? Its area is smaller but its perimeter is bigger. What does 'bigger' mean here?"
- "You just add more squares to get more perimeter" → 呈现图形 E 和 G（周长均为 16，但面积分别为 16 和 7）。"Shape E has more squares but the same perimeter. Why?"

### 评估检查

**独立性测试：** 给学生三组陈述，让他们判断每一条是“总是正确（ALWAYS TRUE）”、“有时正确（SOMETIMES TRUE）”还是“从不正确（NEVER TRUE）”：

1. "If Shape X has a bigger area than Shape Y, then Shape X has a bigger perimeter than Shape Y."（有时正确——并非总是）
2. "Two shapes with the same area must have the same perimeter."（从不正确——存在许多反例）
3. "You can change the perimeter of a shape without changing its area."（总是正确——第 2 阶段已证明）

接着："Draw two shapes that have the same area but different perimeters. Draw two shapes that have the same perimeter but different areas."

如果学生能做到这一点，他们就辨别出了关键特征：面积与周长是相互独立的。

---

## 已知局限性

1. **变式理论最适用于具有可识别关键特征的清晰定义概念。** 它在数学和科学中最具威力，因为在这些学科中需要辨别的特征非常明确（面积 vs. 周长、速率 vs. 速度、加法 vs. 乘法）。对于开放性、阐释性的学习（文学分析、创意写作），其“关键特征”不那么离散，较难直接套用。本技能不应将变式理论强加于更适合其他方法的学习目标上。

2. **该理论主要在数学与科学教育语境中发展起来。** 尽管“通过变式实现辨别”的原则具有跨领域普适性，但具体模式（对比、分离、泛化、融合）在香港、瑞典和中国大陆的数学课堂中得到了最充分的研究与验证。应用于其他学科与文化语境时应当深思熟虑，而非机械套用。

3. **变式理论解决的是学习的一个方面——辨别——而非全貌。** 学生同样需要动机、练习、反馈与应用。如果学生不投入、缺乏足够先验知识或在辨别概念后缺乏充分练习，设计得再完美的变式序列也会失败。变式理论是任务设计的有力透镜，但不是完整的教学理论。
