---
# AGENT SKILLS STANDARD FIELDS (v2)
name: udl-lesson-auditor
description: "对照 UDL 三大原则——参与、表征与行动/表达——审计现有教案。识别具体可及性障碍，并按影响力排序提出具体修改建议。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "inclusive-design/udl-lesson-auditor"
skill_name: "UDL 教案审计器"
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
    - field: "lesson_plan"
      type: "string"
      description: "需要审计的教案或单元计划。包括学习目标、活动、材料与评估。"
    - field: "learner_context"
      type: "string"
      description: "学生的简要描述——年龄、已知差异性（例如 EAL 学习者、拥有 IEP 的学生、阅读水平跨度大）"
  optional:
    - field: "specific_concerns"
      type: "string"
      description: "教师特别担忧的任何具体可及性障碍"
    - field: "constraints"
      type: "string"
      description: "教师无法改变的限制（例如指定必读文本、强制评估形式、时间上限）"
output_schema:
  type: "object"
  fields:
    - field: "principle_audits"
      type: "array"
      description: "针对每项 UDL 原则的审计发现：哪些有效、哪些制造了障碍、具体修改建议"
    - field: "priority_modifications"
      type: "array"
      description: "在尊重既定限制的前提下，最具影响力的 3–5 项修改"
    - field: "what_to_keep"
      type: "array"
      description: "教案中已经支持可及性的现有元素——予以强化保留"
    - field: "facilitation_notes"
      type: "array"
      description: "实施注意事项与教师专业判断核查"
chains_well_with:
  - "inclusive-design/udl-options-designer"
  - "inclusive-design/udl-barrier-anticipator"
  - "curriculum-assessment/differentiation-adapter"
  - "curriculum-assessment/formative-assessment-technique-selector"
  - "self-regulated-learning/self-regulation-scaffold-generator"
teacher_time: "10-15 分钟"
tags: ["UDL", "inclusive-design", "barrier-analysis", "access", "lesson-audit", "differentiation", "CAST"]
---

# UDL 教案审计器

## 本技能的作用

接收一份现有教案或单元计划，并对照通用学习设计（UDL）的三大原则及其指南进行评估。识别具体的可及性障碍，并按影响力排序提出切实可行的修改建议。对大多数教师而言，这是最具价值的 UDL 技能，因为起点是一份已经存在的教案，而不是一张白纸。

本技能不是合规性核查清单，而是一次障碍分析。目标是找出哪些设计选择——由于信息呈现的方式、要求学生回应的方式或维持参与度的方式——可能会在无意中排斥部分学习者，并在保持相同学习目标的前提下提出具体、实用的替代方案。并非所有内容都需要改动。输出会指出最具影响力的修改、尊重教师无法撼动的限制条件，并肯定教案已经做得好的地方。

## 循证基础

通用学习设计（UDL）是由 CAST 开发的设计框架（Rose & Meyer, 2002; CAST, 2018; Meyer, Rose & Gordon, 2014）。它建立在三大原则之上：多种表征方式（Multiple Means of Representation，信息如何呈现）、多种行动与表达方式（Multiple Means of Action and Expression，学生如何展示理解）以及多种参与方式（Multiple Means of Engagement，什么激发并维持注意力）。UDL 指南（CAST, 2018）在每项原则下提供了具体检查点，源自神经科学、认知科学与教育研究。

UDL 作为完整框架的证据强度为中等：该框架在实践界得到充分确立并植根于相关研究传统，但实施研究主要由准实验研究和案例研究构成，而非大型随机对照试验（Ok, Rao, Bryant & McDougall, 2017）。UDL 内部的单个策略——提供多种表征、提供学生选择、灵活评估——则拥有来自邻近研究传统的更强证据，包括多媒体学习（Mayer, 2009）、自我决定理论（Ryan & Deci, 2000）以及形成性评估（Black & Wiliam, 1998）。UDL 是一个帮助教师预测并减少障碍的设计框架，它不是一个保证所有学生都能接触学习的已验证干预方案；某些障碍仍需要 UDL 无法替代的专业评估与个性化支持。

## Prompt

```text
You are a UDL specialist with expertise in learning variability and barrier analysis. Your task is to audit the lesson plan below against Universal Design for Learning's three principles. You are looking for access barriers — design choices that may unintentionally exclude learners — and you will suggest specific, practical modifications ranked by impact.

Inputs:
Lesson plan: {{lesson_plan}}
Learner context: {{learner_context}}
Specific concerns: {{specific_concerns}}
Constraints (cannot change): {{constraints}}

Work through the three UDL principles in order. For each principle:
1. Identify what the lesson currently does well (name specific elements, not generalities)
2. Identify specific barriers — name the barrier, explain which learners it affects, and explain why it creates an access problem
3. Suggest concrete modifications — not "provide multiple representations" but "add a labelled diagram alongside the written instructions" or "offer a sentence frame for the oral response"

UDL Principle 1: Multiple Means of Engagement (the WHY of learning)
Examine: How does the lesson recruit interest? Does it sustain effort and persistence across different learners? What supports self-regulation? Barriers to look for: single mode of engagement, no choice in how to pursue the task, no explicit connection to relevance, no scaffolding for attention or persistence variability.

UDL Principle 2: Multiple Means of Representation (the WHAT of learning)
Examine: How is information presented? Is it accessible to learners with visual, auditory, language, or cognitive processing variability? Are vocabulary and symbols explicitly addressed? Are comprehension scaffolds present? Barriers to look for: text-only or audio-only presentation, complex vocabulary without support, single medium for complex concepts, no advance organiser or background knowledge activation.

UDL Principle 3: Multiple Means of Action and Expression (the HOW of learning)
Examine: How do students demonstrate their learning? Are expression options varied? Are executive function demands made explicit? Is physical or digital access considered? Barriers to look for: single response format, high executive function demands without scaffolding, no opportunity to practise before high-stakes demonstration, assessment format that creates barriers unrelated to the learning goal.

After auditing all three principles:
- Prioritise modifications: identify the 3-5 highest-impact changes. Not everything needs to change. Prioritise barriers that affect the most learners or create the most significant access problems.
- Respect constraints: if the teacher has named things they cannot change, suggest supports around those constraints, not changes to them.
- Name what to keep: identify existing lesson elements that already support access. These should be reinforced, not accidentally removed.

Self-check before returning output: Are modifications specific and actionable (not generic UDL advice)? Have I respected the stated constraints? Am I suggesting changes that address real barriers, not just adding options for the sake of UDL compliance? Have I named what the lesson does well, not just what it gets wrong?

Return in this format:

## UDL Audit: [Lesson Title or Brief Description]

**Learner context:** [brief]
**Constraints respected:** [list or "none stated"]

### Principle 1: Multiple Means of Engagement
**What works:** [specific existing elements]
**Barriers identified:** [specific barriers with affected learners]
**Suggested modifications:** [specific, named modifications]

### Principle 2: Multiple Means of Representation
**What works:** [specific existing elements]
**Barriers identified:** [specific barriers with affected learners]
**Suggested modifications:** [specific, named modifications]

### Principle 3: Multiple Means of Action and Expression
**What works:** [specific existing elements]
**Barriers identified:** [specific barriers with affected learners]
**Suggested modifications:** [specific, named modifications]

### Priority Modifications (3-5 highest impact)
1. [Modification — why high impact — which learners it helps]
2. [...]

### What to Keep
[Existing elements that already support access — reinforce these]

### Facilitation Notes
[Implementation cautions, teacher judgement checks, anything that depends on knowing the specific students]
```

## 常见误区

1. **为了 UDL 合规而非为了可及性进行审计。** 问题不是“这节课是否勾上了所有 UDL 检查点？”，而是“学习者可能在何处遇到设计本可以降低的障碍？”。合规与可及性并非一回事。
2. **建议所有东西都需要改变。** 有效的 UDL 审计产出的是一份按优先级排序的高影响力修改清单，而不是全面推翻重来。如果每个元素都被标红，审计就失去了可操作性。
3. **泛泛的修改建议而非具体建议。** “提供多种表征”不是修改建议——“在书面指令旁添加一张标注清晰的示意图”才是。具体性才让建议可用。
4. **忽略教师的限制条件。** 如果教师无法更换必读文本，建议他们换一本书毫无帮助。应当围绕限制提供支持：词汇表、作为补充材料的低阅读难度平行文本、文本转语音选项。
5. **把 UDL 当作专业支持的替代品。** 对于有已识别需求（IEP、专业评估）的学生，UDL 修改是底线，而非上限。应明确点出这一点，而不要暗示单靠 UDL 就足够了。

## 已知局限性

1. **无法评估未曾谋面的特定学生所面临的障碍。** 审计基于所描述的学习者差异性，而这总是不完整的。教师了解自己的学生，本技能并不了解。审计基于一般学习者多样性识别可能障碍，而非教室里具体的某个人。
2. **无法替代对有已识别需求学生的专业评估。** 教育心理学家评估、言语-语言评估以及作业治疗报告识别障碍与支持的精细度是本技能无法企及的。UDL 审计是设计工具，专业评估是诊断工具。
3. **在存在未披露限制时，可能提出不切实际的修改建议。** 教师面临的资源、时间和制度限制未必能从教案中看出来。某些建议的修改可能需要教师并不具备的技术、备课时间或学校支持。
4. **审计教案不同于课堂观课。** 实施障碍——教师如何授课、同伴动态、教室环境、学生情绪状态——不同于教案中可见的设计障碍。设计精良的课可能因授课方式而制造障碍，设计欠佳的课也可能因娴熟的课堂引导而化险为夷。

## 验证清单

- [ ] 每项 UDL 原则均被具体而非泛泛地审计。
- [ ] 障碍被具体命名并附带对特定学习者的影响，而非抽象类别。
- [ ] 修改建议具体且可操作，而非泛泛的 UDL 标签。
- [ ] 优先清单真正排定了优先级（不只是列出所有修改）。
- [ ] 尊重了限制条件——建议围绕限制展开，而非试图突破不可动摇的限制。
- [ ] 识别并保留了现有优势。
- [ ] 未宣称 UDL 能确保或保证所有学习者无障碍。
