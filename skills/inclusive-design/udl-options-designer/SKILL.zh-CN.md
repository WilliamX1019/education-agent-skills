---
# AGENT SKILLS STANDARD FIELDS (v2)
name: udl-options-designer
description: "为给定学习目标生成多种参与、表征与行动/表达方式。产出具体、实用的替代方案——而非泛泛选项——并推荐最具影响力的单一改动。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "inclusive-design/udl-options-designer"
skill_name: "UDL 选项设计师"
domain: "inclusive-design"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Rose & Meyer (2002) — Teaching Every Student in the Digital Age: Universal Design for Learning"
  - "CAST (2018) — Universal Design for Learning Guidelines version 2.2"
  - "Meyer, Rose & Gordon (2014) — Universal Design for Learning: Theory and Practice"
  - "Ok, Rao, Bryant & McDougall (2017) — Universal Design for Learning in Pre-K to Grade 12 Classrooms: A Systematic Review of Research"
  - "Rao & Meo (2016) — Using Universal Design for Learning to Design Standards-Based Lessons"
  - "Edyburn (2010) — Would You Recognize Universal Design for Learning if You Saw It?"
input_schema:
  required:
    - field: "learning_goal"
      type: "string"
      description: "具体的学习目标或靶向。示例：学生将解释光合作用如何将光能转化为化学能。"
    - field: "current_approach"
      type: "string"
      description: "教师目前计划如何教授这一目标。示例：阅读课本章节、观看视频、完成练习纸。"
  optional:
    - field: "learner_context"
      type: "string"
      description: "已知的学生差异性——年龄、语言背景、学习档案、已知挑战"
    - field: "available_resources"
      type: "string"
      description: "可用的技术、材料与空间。示例：1:1 Chromebook、无打印机、共用教室。"
output_schema:
  type: "object"
  fields:
    - field: "engagement_options"
      type: "array"
      description: "“多种参与方式”的 2–3 个具体替代方案，附带每个方案支持哪些学习者的依据"
    - field: "representation_options"
      type: "array"
      description: "“多种表征方式”的 2–3 个具体替代方案，附带依据"
    - field: "action_expression_options"
      type: "array"
      description: "“多种行动与表达方式”的 2–3 个具体替代方案，附带依据"
    - field: "minimum_viable_udl"
      type: "string"
      description: "如果教师只能改变一件事，最具影响力的单一改动"
    - field: "implementation_notes"
      type: "array"
      description: "如何在不让学生不知所措的前提下提供选项的实用建议"
chains_well_with:
  - "inclusive-design/udl-lesson-auditor"
  - "inclusive-design/udl-barrier-anticipator"
  - "curriculum-assessment/differentiation-adapter"
  - "curriculum-assessment/formative-assessment-technique-selector"
  - "self-regulated-learning/self-regulation-scaffold-generator"
teacher_time: "5-10 分钟"
tags: ["UDL", "inclusive-design", "options", "multiple-means", "access", "differentiation", "CAST"]
---

# UDL 选项设计师

## 本技能的作用

给定一个学习目标与当前教学方法，跨通用学习设计（UDL）的三大原则生成真正的替代方案：多种参与方式、多种表征方式以及多种行动与表达方式。这些替代方案在保持相同学习目标的同时改变通达路径。这是 UDL 的设计思维技能——不是事后硬凑的选项清单，而是认真思考不同学习者如何通过不同路径达成相同理解。

关键区别在于具体性。本技能不生成泛泛的选项（“提供视觉支持”），而是生成具体方案："Create a labelled diagram of the photosynthesis process with colour-coded inputs and outputs, so students can trace the energy conversion visually before or alongside reading the text." 每个替代方案都标明特别支持哪些学习者，并将依据连接到学习科学，而不仅仅是贴 UDL 标签。输出还包括“最小可行 UDL（minimum viable UDL）”建议——即如果教师只能做一处改变，最具影响力的那一项改动。

## 循证基础

通用学习设计（UDL）是由 CAST 开发的设计框架，建立在源自神经科学、认知科学与教育研究的三大原则之上（Rose & Meyer, 2002; CAST, 2018）。该框架认为，学习者差异不是例外而是常态，教学设计应当预先顺应差异，而不是在学习失败后再被动补救。UDL 作为完整框架的证据强度为中等：在实践中确立已久并植根于相关研究，但实施证据主要为准实验性质（Ok, Rao, Bryant & McDougall, 2017）。

UDL 内部的各项具体策略则拥有更坚实的证据基础。提供多种表征建立在多媒体学习研究之上，表明跨多模态编码的信息比单一模态呈现能产生更深层的理解（Mayer, 2009）。在学生如何展示学习上提供选择连接到自我决定理论，该理论一致表明感知自主性支持内在动机（Ryan & Deci, 2000）。多样化参与策略借鉴了对兴趣、注意力和执行功能差异性的研究。UDL 是一个帮助教师预测并降低可及性障碍的设计框架——它不是经过验证的干预方案，也不保证所有学习者都能同等顺畅地接触所有内容。

## Prompt

```text
You are a UDL specialist and learning designer. Your task is to generate specific, practical learning options across Universal Design for Learning's three principles for the learning goal below. You are NOT generating a generic UDL checklist. You are generating genuine alternatives that maintain the same learning goal while varying the path — each option must be specific enough to implement immediately.

Inputs:
Learning goal: {{learning_goal}}
Current approach: {{current_approach}}
Learner context: {{learner_context}}
Available resources: {{available_resources}}

For EACH UDL principle, generate 2-3 genuine alternatives. For each alternative:
- Name the specific option (not a category — a concrete activity, format, or tool)
- Note which learners it particularly supports and WHY (connect to learning science where you can: cognitive load, dual coding, self-determination, executive function, language processing — not just "UDL labels")
- Note any resource or preparation requirements

Rules for generating options:
1. SPECIFICITY: "Use a graphic organiser" is not specific enough. "Provide a partially completed T-chart with the inputs and outputs of photosynthesis already labelled, so students complete the energy conversion relationships" is specific.
2. PRACTICALITY: Options must be achievable in a real classroom. If resources are constrained, work within them.
3. GOAL INTEGRITY: Every option must target the same learning goal. Options that inadvertently reduce cognitive demand or shift to a different goal should be flagged, not presented as equivalent.
4. RATIONALE: For each option, briefly explain WHY it supports particular learners — not because UDL says so, but because of how learning works for those learners.

UDL Principle 1: Multiple Means of Engagement (the WHY — recruiting interest, sustaining effort, supporting self-regulation)
Generate 2-3 specific engagement alternatives. Consider: How can the learning connect to different student interests or contexts? How can students have some agency in how they pursue the goal? What supports persistence for students with attention variability?

UDL Principle 2: Multiple Means of Representation (the WHAT — perception, language, comprehension)
Generate 2-3 specific representation alternatives. Consider: What information do students need to reach this goal, and how can it be presented in more than one modality? What vocabulary or symbols need explicit support? What background knowledge might be missing?

UDL Principle 3: Multiple Means of Action and Expression (the HOW — physical action, communication, executive function)
Generate 2-3 specific alternatives for how students demonstrate their understanding. Consider: What response formats maintain the cognitive demand of the goal while varying how students show their thinking? What executive function scaffolds help students organise their response?

After generating all options:
- Minimum viable UDL: Identify the single highest-impact change if the teacher can only do ONE thing differently. This should be the option most likely to reduce the most significant barrier for the most learners in this specific context.
- Implementation note: Not every lesson needs all options simultaneously. That is UDL-as-checkbox, not UDL-as-design-thinking. Suggest how to offer options without overwhelming students with choice — particularly for students with executive function challenges, for whom more options can reduce rather than increase access.

Self-check before returning output: Are all options specific enough to implement tomorrow? Do they all maintain the same learning goal? Am I connecting rationale to learning science, not just UDL category labels? Have I recommended a minimum viable UDL (not just a list)?

Return in this format:

## UDL Options: [Learning Goal]

**Current approach:** [brief]
**Learner context:** [brief or "not specified"]

### Multiple Means of Engagement
1. **[Option name]** — [Description, which learners, why]
2. **[Option name]** — [Description, which learners, why]
3. **[Option name — optional]** — [Description, which learners, why]

### Multiple Means of Representation
1. **[Option name]** — [Description, which learners, why]
2. **[Option name]** — [Description, which learners, why]
3. **[Option name — optional]** — [Description, which learners, why]

### Multiple Means of Action and Expression
1. **[Option name]** — [Description, which learners, why]
2. **[Option name]** — [Description, which learners, why]
3. **[Option name — optional]** — [Description, which learners, why]

### Minimum Viable UDL
[The single highest-impact change, with rationale]

### Implementation Notes
[How to offer options without overwhelming students; any practical cautions]
```

## 常见误区

1. **泛泛的选项而非具体选项。** 输出应当无需进一步阐释即可实施。“提供视觉支持”在变成行动前还需要另一次设计决策；“制作一张已预填词汇、连接关系留空的标注图”则是一个可直接执行的行动。
2. **在无意中降低认知要求的选项。** 有些替代方案看似更易接触，实则降低了学习目标的严谨性。阅读一篇文章与观看一段视频并不是通往同一理解的等价路径——它们对认知的要求不同，与目标的关系也不同。应当标出这一点，而非将所有选项呈现为可互换。
3. **同时提供过多选项。** 更多选择并不总是更易接触，尤其是对有执行功能挑战的学生。最小可行 UDL 建议正是为此而设。
4. **把 UDL 选项当作永久支架而非前瞻性设计。** UDL 的目标是从一开始就为差异性而设计，而不是搭建繁复的支架系统。选项应当融入教学设计本身，而非生硬外挂。

## 已知局限性

1. **生成选项不等于知道特定班级需要哪些选项。** 教师对自己学生的了解始终是第一位的。这里生成的选项基于一般学习者差异性与所描述的语境——教师最清楚哪些选项在自己的教室里真正有效。
2. **看似等价的选项未必真的等价。** 阅读文本与观看视频是认知任务不同、与学习目标关系也不同的两件事。部分选项可能在无意中改变任务难度、语言需求或认知路径。本技能会标出明显不匹配，但无法评估选项与目标之间所有可能的交互作用。
3. **本技能无法验证所建议的替代方案是否保持了完全同等的严谨度。** 某些看似支持可及性的修改可能在无意中降低了认知要求，改变了学生实际在学的内容。教师对照预期目标逐一审视每个选项至关重要。
4. **选项过多反而可能降低部分学习者的可及性。** 有执行功能挑战、决策疲劳或焦虑的学生，面对同时出现的多种选择可能会感到不知所措。更多选择并不总是更包容——结构化选择（从 A 栏中选一项）往往比完全开放的选择更易接触。

## 验证清单

- [ ] 所有选项都具体到无需进一步设计决策即可实施。
- [ ] 所有选项均保持相同的学习目标——无意外的难度降低。
- [ ] 每个选项均包含与学习科学相连的依据，而非仅贴 UDL 标签。
- [ ] 包含最小可行 UDL 建议。
- [ ] 实施说明探讨了如何在不让人因选择过载而不知所措的前提下提供选项。
- [ ] 未宣称提供多种选项就能保证所有学习者获得同等可及性。
