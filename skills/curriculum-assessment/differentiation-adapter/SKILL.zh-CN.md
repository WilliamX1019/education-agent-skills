---
# AGENT SKILLS STANDARD FIELDS (v2)
name: differentiation-adapter
description: "在完整保留核心学习目标的前提下，针对特定学习者需求调适课堂任务。适用于为 SEND、EAL、资优、ADHD、阅读障碍或焦虑症学生进行差异化教学。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/differentiation-adapter"
skill_name: "差异化教学适配器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Tomlinson (2001, 2014) — How to Differentiate Instruction in Academically Diverse Classrooms"
  - "Rose & Meyer (2002) — Teaching Every Student in the Digital Age: Universal Design for Learning"
  - "Vygotsky (1978) — Mind in Society: the zone of proximal development"
  - "Hattie (2009) — Visible Learning: differentiation and responsive teaching"
  - "CAST (2018) — Universal Design for Learning Guidelines version 2.2"
input_schema:
  required:
    - field: "original_task"
      type: "string"
      description: "为全班设计的原始任务"
    - field: "learner_profile"
      type: "string"
      description: "特定学习者需求——例如拓展、支持、EAL、ADHD、阅读障碍、焦虑症、资优"
    - field: "learning_objective"
      type: "string"
      description: "学习目标——在所有差异化版本中必须保持完全一致"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：具体诊断、支持计划、先前学业水平"
    - field: "available_support"
      type: "string"
      description: "助教（TA）配备情况、技术工具、专业资源"
output_schema:
  type: "object"
  fields:
    - field: "adapted_task"
      type: "object"
      description: "包含具体修改的差异化任务版本"
    - field: "what_changed"
      type: "string"
      description: "明确说明修改了什么以及保留了什么"
    - field: "objective_check"
      type: "string"
      description: "验证学习目标是否得到完整保留"
    - field: "implementation_notes"
      type: "string"
      description: "供教师实施该调适方案的实用说明"
chains_well_with:
  - "scaffolded-task-modifier"
  - "cognitive-load-analyser"
  - "formative-assessment-technique-selector"
  - "practice-problem-sequence-designer"
teacher_time: "3 分钟"
tags: ["differentiation", "UDL", "inclusion", "SEND", "adaptation"]
---

# 差异化教学适配器

## 本技能的作用

在明确保持相同学习目标的前提下，针对特定学习者画像——拓展、支持、EAL、ADHD、阅读障碍、焦虑症、视力障碍、自闭症谱系、资优生——调适课堂任务。核心原则在于：差异化修改的是通往学习的**路径（ROUTE）**，而不是**目的地（DESTINATION）**。一名患有阅读障碍、正在挑战与同伴相同学习目标的学生，可能需要不同的信息输入格式、不同的作答格式和不同的脚手架——但他们应当朝着相同的理解迈进。输出包括调适后的任务、对“改变了什么、保留了什么”的明确说明、对学习目标是否维持的核查，以及实施说明。AI 在此尤为关键，因为有效的差异化需要同时掌握学习者画像（该画像会制造哪些障碍？）与任务特征（任务的哪些要素会触发这些障碍？）——这是一项必须针对“任务 × 学习者需求”每一种组合分别开展的双向分析。

## 实证基础

Tomlinson（2001, 2014）确立了差异化教学框架，识别出差异化的三个维度：内容（学生学什么）、过程（他们如何学）与成果（他们如何展示学习）。她强调差异化应当基于准备度（readiness）、兴趣与学习者画像——**而非**基于“学习风格”（该理论因已被证伪而被本技能库排除）。Rose & Meyer（2002）提出了通用学习设计（UDL），主张课程从一开始就应通过三大原则面向所有学习者开放：多元参与方式（学习的“为什么”）、多元表征方式（“学什么”）与多元行动和表达方式（“怎么展示”）。Vygotsky（1978）确立了教学应当瞄准最近发展区（ZPD）——即学习者在恰当支持下能够完成、但尚不能独立完成的内容。Hattie（2009）发现差异化总体上具有中等效应量，但随实施质量差异极大——实施拙劣的差异化（给较弱学生更简单的作业）实际上会因降低期望而拉低学业成就。CAST（2018）提供了 UDL 指南 2.2 版，即此处用于实施策略的历史版本。CAST 于 2024 年发布了 3.0 版；本技能保留其既定的 2.2 版依据，不声称实施了新版。

## 输入规范

教师必须提供：
- **原始任务（Original task）：** 按原样设计的任务。*例如：“阅读《圣诞颂歌》节选并写一段话分析狄更斯如何呈现斯克鲁奇的转变，使用原文引文作为证据。”*
- **学习者画像（Learner profile）：** 具体需求。*例如：“拓展——完成很快且需要更深挑战的学生” / “支持——患有阅读障碍、在重阅读任务上吃力的学生” / “ADHD——在长篇写作上难以维持专注的学生”*
- **学习目标（Learning objective）：** 所有学生都应学会的内容。*例如：“运用文本证据分析狄更斯如何呈现人物变化。”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级
- **学科领域（Subject area）：** 课程学科
- **学生画像（Student profiles）：** 具体诊断、支持计划、先前学业水平
- **可用支持（Available support）：** 助教、技术、专业资源

## 提示词（Prompt）

```
You are an expert in differentiated instruction and inclusive education, with deep knowledge of Tomlinson's (2001, 2014) differentiation framework, Rose & Meyer's (2002) Universal Design for Learning principles, and CAST's (2018) UDL Guidelines version 2.2. This is the historical edition used here, not a claim to implement version 3.0 (released in 2024). You understand that effective differentiation modifies the ROUTE to learning, not the DESTINATION — all students work toward the same learning objective, but the pathway is adapted to remove barriers specific to each learner's profile.

IMPORTANT: Differentiation by learning style (visual/auditory/kinaesthetic preferences) is NOT supported — this is excluded from this library as debunked (Pashler et al., 2008). Differentiation by readiness, specific learning needs, and learner profile IS supported.

Your task is to adapt:

**Original task:** {{original_task}}
**Learner profile:** {{learner_profile}}
**Learning objective:** {{learning_objective}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the task.
**Subject area:** {{subject_area}} — if not provided, infer from the task.
**Student profiles:** {{student_profiles}} — if not provided, base adaptations on general research about the stated learner profile.
**Available support:** {{available_support}} — if not provided, assume standard classroom resources with no specialist TA.

Apply these evidence-based principles:

1. **Same objective, different route (Tomlinson, 2001):**
   - The learning objective must be identical for the adapted and original task.
   - Modify HOW the student engages with the content or demonstrates their learning, not WHAT they learn.
   - If the adaptation reduces cognitive demand, it has gone too far — it should reduce barriers, not reduce thinking.

2. **Profile-specific adaptations (UDL, CAST 2018):**
   Adapt based on what the research says about each learner profile:
   - **Extension/Gifted:** Increase depth and complexity — not more of the same, but qualitatively different challenge. Abstract thinking, multiple perspectives, evaluation, creation.
   - **Support/Below expected level:** Additional scaffolding — sentence frames, graphic organisers, reduced volume (not reduced difficulty), worked examples to reference.
   - **Dyslexia:** Reduce reading load without reducing thinking. Larger font, coloured overlay, audio version of text, key quotations pre-selected, scribe option for writing. Focus on demonstrating UNDERSTANDING, not reading fluency.
   - **ADHD:** Break task into shorter chunks with check-in points. Reduce unnecessary information. Provide movement breaks. Use timers for focused bursts. Minimise distractions in the task presentation.
   - **EAL:** Language scaffolds (sentence frames, word banks, glossary, bilingual support) — see the EAL domain skills for detailed approaches.
   - **Anxiety:** Reduce performance pressure. Allow draft attempts. Provide clear structure. Offer choice of response format. Avoid cold-calling or public demonstration of work-in-progress.
   - **Autism:** Provide explicit, unambiguous instructions. Avoid figurative language in task instructions (or gloss it). Provide predictable structure. Allow additional processing time.
   - **Visual impairment:** Enlarged text, high contrast, audio alternatives, tactile resources where appropriate.

3. **UDL multiple means (Rose & Meyer, 2002):**
   - **Multiple means of representation:** Can the content be presented differently? (Audio, visual, simplified text alongside original, graphic organiser)
   - **Multiple means of action and expression:** Can the student demonstrate learning differently? (Verbal instead of written, diagram instead of essay, recorded instead of live)
   - **Multiple means of engagement:** Can the task be connected to the student's interests or motivations?

4. **Avoid common differentiation errors (Hattie, 2009):**
   - Do NOT give a simpler version of the task to struggling students — this lowers expectations and reduces learning.
   - Do NOT give "more work" to extension students — depth, not volume.
   - Do NOT assume that the adapted version is inherently "lower" — it should be equally demanding but differently accessible.

Return your output in this exact format:

## Adapted Task: [Learner Profile]

**Original task:** [Brief description]
**Adapted for:** [Learner profile]
**Learning objective:** [Must be identical to original]

### The Adapted Task

[Complete adapted version of the task with all modifications in place]

### What Changed and What Stayed the Same

**Changed:** [Specific modifications — what was adapted and why]
**Maintained:** [What was deliberately kept the same — especially cognitive demand and learning objective]

### Objective Check

[Explicit verification: "The adapted task still requires the student to [learning objective] because..."]

### Implementation Notes

[Practical advice for the teacher: how to introduce the adaptation, how to avoid singling the student out, what to watch for]

**Self-check before returning output:** Verify that (a) the learning objective is identical, (b) adaptations address the specific barriers of the stated learner profile, (c) cognitive demand is maintained — the adapted task is not easier, just more accessible, (d) the adaptation is based on research about the learner profile, not on learning style preferences, and (e) the implementation notes address how to manage the adaptation in a classroom without stigmatising the student.
```

## 示例输出

**情景：** *原始任务：“阅读《圣诞颂歌》节选并写一段话分析狄更斯如何呈现斯克鲁奇的转变，使用原文引文作为证据。” / 学习者画像：“阅读障碍——学生阅读年龄比生理年龄低约 2 年，长文本解码吃力，回避阅读任务，但在课堂讨论中展现出很强的口头分析能力” / 学习目标：“运用文本证据分析狄更斯如何呈现人物变化” / 学生水平：“九年级” / 学科领域：“英语文学”*

---

## 调适后的任务：阅读障碍（Dyslexia）

**原始任务：** 阅读《圣诞颂歌》节选并写一段话分析狄更斯如何呈现斯克鲁奇的转变，使用原文引文作为证据。
**调适对象：** 阅读障碍——口头分析能力强，阅读年龄比生理年龄低约 2 年
**学习目标：** 运用文本证据分析狄更斯如何呈现人物变化

### 调适后的任务

**阅读节选：**
- 将节选印在米黄色/浅棕褐色纸张上（降低视觉对比度压力），使用至少 14 号字体和 1.5 倍行距。
- 预先高亮标出 4 处展现斯克鲁奇转变的关键引文——这些是学生应聚焦的引文。这消除了在密集文本中扫描查找证据的障碍（一项阅读流畅度任务），同时保留了**分析**证据的要求（真正的学习目标）。
- 如果有音频资源，提供该节选的录音，让学生可以边听边对照文本阅读。这支持解码过程，而不必完全撤掉文本。

**分析与写作：**
- 提供 PEEL 段落框架：
  - **Point（观点）：** “Dickens presents Scrooge's transformation by...”
  - **Evidence（证据）：** “This is shown when Dickens writes '___'（高亮引文之一）”
  - **Explain（解释）：** “This quotation suggests that Scrooge has changed because...”
  - **Link（联系）：** “This shows the reader that...”
- 学生必须在每个环节提供自己的分析思考——框架结构化的是写作，而不是分析本身。
- **替代作答选项：** 如果书写本身是主要障碍（而非分析），让学生选择口头录制这段分析（语音录制或口述给记录员），替代手写。分析要求完全相同，改变的仅是输出形式。

### 改变了什么与保留了什么

**改变了：**
- 文本呈现方式：更大字号、米色纸张、加宽行距——降低解码负荷
- 预先高亮引文：免去通篇扫读找证据的环节——那是阅读流畅度任务，而非分析任务
- 音频支持：可选的边听边读
- 写作脚手架：提供 PEEL 框架组织段落
- 替代输出：提供口头作答选项

**保留了：**
- 学习目标：运用文本证据分析狄更斯如何呈现人物变化
- 使用具体引文作为证据的要求
- 分析深度要求：学生必须解释引文展示了**什么**以及**为什么**重要
- 质量期望：分析的敏锐度应当与其他同学一样高
- 文本本身：同一份节选，而非简化改写版

### 目标核查

调适后的任务仍然要求学生**运用文本证据分析狄更斯如何呈现人物变化**，因为：
- 学生依然需要**阅读**节选（有支持，但读的是同一份文本）
- 学生依然需要**选择**一处引文并解释其意义
- 学生依然需要**分析**——解释引文揭示了斯克鲁奇转变的什么方面，以及狄更斯为何选择这样呈现
- 预先高亮消除的是阅读流畅度障碍，而非分析障碍——学生依然要自己决定选用哪条高亮引文并独立解释其意义
- PEEL 框架结构化了写作，但不提供分析内容——每一个“解释”和“联系”部分都需要学生自己的思考

### 实施说明

1. **低调自然地引入调适。** 不要宣布“这是阅读障碍专用版”。相反，让部分调适面向全班开放：全班都用米色纸张印制节选（对所有读者都有益）；音频版本向全班开放；至于预先高亮的引文，则私下个别发放而非投影展示。

2. **关注分析本身，而非书写。** 这名学生的强项是口头分析。如果书面作答比预期弱，先核查障碍究竟出在写作机械技能（拼写、书写、造句）还是分析上。如果学生能口头清晰解释分析却写不出来，障碍在于书面产出而非理解——此时应主动提供语音录制选项。

3. **不要降低对分析质量的期望。** 这名有阅读障碍的学生具备很强的口头分析能力，他的分析应当适用与其他学生相同的质量标准。调适移除的是障碍，而不是降低门槛。如果他的书面段落流于单薄，回应方式应当是“能多说说这句引文展示了什么吗？”——推动深度——而不是“愿意尝试就不错了”。

4. **随时间逐步撤除预先高亮。** 预先挑选引文是一个脚手架，应随着学生阅读耐力与信心的提升而逐步减少。下一次可以高亮 6 处引文，让学生挑出最好的 2 处。最终提供无高亮文本，看学生是否能（或许配合更充裕的时间）独立找出证据。

---

## 已知局限

1. **调适基于关于该学习者画像的一般研究，而非针对具体个体。** 阅读障碍在不同学生身上的表现各异——有的主要卡在解码，有的卡在阅读速度，有的卡在工作记忆。教师对具体学生的了解对于精细化调适至关重要。如果学生的阅读障碍主要影响拼写而非阅读，调适方案就应有所不同。

2. **明确排除了基于“学习风格”的差异化。** 本技能不依据“视觉型”、“听觉型”或“动觉型”偏好调适任务——实证研究不支持这种做法（Pashler et al., 2008）。调适基于与特定学习需求相关的实证障碍，而非偏好。

3. **调适后的任务可能无意中传递低期望信号。** 如果一名学生总是拿到“不一样的”作业，他可能会内化“我能力较差”的讯息。实施说明已对此做出应对，但教师必须始终保持警惕，将调适定位为无障碍支持（就像近视的人戴眼镜一样），而非降低标准。目标是公平——相同的学习目标，不同的抵达方式——而不是降级分流。
