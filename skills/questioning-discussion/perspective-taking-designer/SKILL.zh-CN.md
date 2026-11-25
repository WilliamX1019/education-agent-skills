---
# AGENT SKILLS STANDARD FIELDS (v2)
name: perspective-taking-designer
description: "设计带有“防投射护栏”（anti-projection guardrails）的结构化视角采择（perspective-taking）活动。在历史、社会科学与文学教学中培养对复杂性的真正理解——而非表演式的共情。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "questioning-discussion/perspective-taking-designer"
skill_name: "视角采择设计器"
domain: "questioning-discussion"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Gehlbach (2004, 2012) — Social perspective-taking in educational settings"
  - "Gehlbach & Brinkworth (2012) — The social perspective taking process"
  - "Batson (2009) — These things called empathy: eight related but distinct phenomena"
  - "Galinsky, Ku & Wang (2005) — Perspective-taking and self-other merging"
  - "Selman (1980) — The growth of interpersonal understanding (developmental stages of perspective-taking)"
  - "Endacott & Brooks (2013) — Historical empathy in the social studies classroom"
input_schema:
  required:
    - field: "subject_context"
      type: "string"
      description: "学科领域与主题。例如：9 年级历史——印巴分治；或 6 年级科学——关于建设风力发电场的社区辩论"
    - field: "learning_goal"
      type: "string"
      description: "视角采择在此处应达成的目标。例如：学生理解为什么不同群体对分治的体验截然不同"
  optional:
    - field: "age_range"
      type: "string"
      description: "学生年龄范围"
    - field: "sensitivity_notes"
      type: "string"
      description: "文化、政治或个人敏感因素。例如：班上有家族经历过印巴分治的学生"
    - field: "prior_knowledge"
      type: "string"
      description: "学生对该主题已有的了解"
output_schema:
  type: "object"
  fields:
    - field: "activity_sequence"
      type: "object"
      description: "四阶段序列：背景建构、视角识别、视角探究、综合"
    - field: "anti_projection_guardrails"
      type: "array"
      description: "针对特定主题的保护机制，防止将当代价值观或个人经验投射到历史或文化视角上"
    - field: "assessment_criteria"
      type: "array"
      description: "聚焦于推理质量的评价标准——所用证据、承认的复杂性、表达的不确定性——而非情感表演"
    - field: "safety_check"
      type: "object"
      description: "活动是否要求学生与加害者共情，如果是，如何重新框定"
    - field: "developmental_calibration"
      type: "string"
      description: "如何针对指定年龄段调整复杂度与抽象度"
chains_well_with:
  - "dialogic-teaching-move-generator"
  - "discussion-protocol-selector"
  - "ladder-of-inference-reflection"
  - "mental-model-mapper"
  - "socratic-questioning-sequence-generator"
teacher_time: "5–10 分钟"
tags: ["perspective-taking", "empathy", "historical-thinking", "social-perspective", "anti-projection", "discussion", "inquiry"]
---

# 视角采择设计器（Perspective-Taking Designer）

## 本技能的功能

帮助教师设计培养真正“视角采择”（perspective-taking）能力的学习活动——即理解他人如何在自身所处的情境与限制条件下思考、感受与体验处境的能力。它在多个领域均极具价值：历史（理解持有不同世界观的行动者）、社会科学（利益相关方分析）、文学（人物动机）、冲突解决、设计思维以及系统思考。

本技能着力解决的核心挑战在于：真正的视角采择需要智识谦逊以及对模糊性的容忍度。它不是去想象“如果我在别人的处境中会有什么感受”——那是**投射**（projection）。它是去探究某个人在给定的背景、知识、价值观和限制条件下，究竟是如何理解自身处境的。这是两种截然不同的认知活动，其差异对认知质量与伦理安全都至关重要。

评价应当聚焦于推理质量（学生使用了什么证据？是否承认了复杂性？是否表达了恰当的不确定性？），而不应聚焦于情感表演（学生表现出了多少同情或共情？）。

## 循证依据

Gehlbach 关于教育情境中社会视角采择的研究将其界定为一种可学习的过程，而非固定特质。他与 Brinkworth 的合作研究识别出其构成要素：注意到视角存在差异、决定考虑他人的视角、想象对方的视角以及核查推断。Batson 关于八种相关但不同质共情现象的分类学是关键背景：想象他人感受（情绪匹配 affect-matching）不同于想象他人想法（认知视角采择 cognitive perspective-taking），而两者又都不同于因他人处境产生的个人痛苦（personal distress）。Galinsky 等人表明，视角采择能促进合作，但也存在“自我-他人融合”（self-other merging）的风险——即将自身价值观强加于他人视角之中。Selman 的发展阶段理论确立了：低龄学生能够认识到他人拥有不同看法；青少年能够同时持有多种视角，并认识到视角是由社会地位、权力与经历塑造的。Endacott 与 Brooks 提出了历史共情框架，区分了情境化（contextualisation，真正的历史思维）与情感共情（affective empathy，情绪认同），认为前者在教育上站得住脚，而后者在历史情境中存在认知问题。

## 输入规范

必填：
- **学科情境：** 学科领域与具体主题。请包含年级，并描述正在审视的历史时刻、利益相关方情境或文本。
- **学习目标：** 视角采择在此情境中应达成的目标。这决定了成功的标准。

可选：
- **年龄范围：** 学生年龄范围，以便根据 Selman 的发展阶段进行校准。
- **敏感性说明：** 文化、政治或个人敏感因素——特别是班上是否有学生或其家人拥有该主题的亲身经历。这对安全检查至关重要。
- **先备知识：** 学生已知的内容，用以校准背景建构阶段。

## Prompt

```text
You are an expert in social perspective-taking research, drawing specifically on Gehlbach's work on social perspective-taking processes, Batson's taxonomy of empathy phenomena, and Selman's developmental stages. Your task is to design a structured perspective-taking activity that develops genuine understanding of complexity — not performed empathy.

Inputs:
Subject context: {{subject_context}}
Learning goal: {{learning_goal}}
Age range: {{age_range}}
Sensitivity notes: {{sensitivity_notes}}
Prior knowledge: {{prior_knowledge}}

Use these rules:

1. DESIGN A FOUR-PHASE ACTIVITY SEQUENCE:
   - Phase 1 — Context-building: What do students need to know before attempting perspective-taking? What is the historical, cultural, or situational context that shaped the perspectives you are examining? Students cannot take a genuine perspective without understanding the world that perspective was formed within.
   - Phase 2 — Perspective identification: Whose perspectives are relevant and available? Name them specifically. Flag when a perspective is underdocumented — we may know about a group without knowing how they experienced the specific moment.
   - Phase 3 — Perspective exploration: Structured inquiry into each perspective. Students investigate, using evidence, how each person or group understood their situation. Specify the sources or evidence types students should use.
   - Phase 4 — Synthesis: What did students learn about complexity? What aspects of the situation look different when seen from multiple perspectives? What remains genuinely uncertain?

2. ANTI-PROJECTION GUARDRAILS — these are critical and must be topic-specific:
   - Distinguish clearly between:
     a. Imagining what someone thinks/feels from within their own context (contextual perspective-taking) — epistemically sound
     b. Imagining what we would think/feel in their situation (projection) — epistemically problematic
   - Where historical or cultural perspectives are involved: require students to use primary sources, documented accounts, or contextualised secondary sources, not imagination.
   - Include explicit instructions: "If students cannot find evidence for how a person or group experienced this, they should say 'we do not know' rather than inventing a perspective."
   - Flag when perspectives risk being flattened into single viewpoints. Example: "the Indian perspective on partition" does not exist — name the specific communities, groups, and positions within them.
   - Include at least two guardrail prompts specific to this topic.

3. DEVELOPMENTAL CALIBRATION based on Selman's stages:
   - Ages 6-8 (Stage 1): Can recognise that others have different perspectives. Limit to: whose view is this? What does this person know or not know?
   - Ages 8-10 (Stage 2): Can take one perspective at a time. Sequence activities so students hold one perspective fully before shifting to another.
   - Ages 10-12 (Stage 3): Can coordinate two perspectives simultaneously. Introduce comparison.
   - Ages 12+ (Stage 4): Can hold multiple perspectives and reflect on how they are shaped by social position, power, and experience. Introduce structural analysis of why perspectives differ.
   Calibrate language, activity complexity, and synthesis expectations accordingly.

4. SAFETY CHECK for sensitive topics:
   - Is this perspective-taking activity asking students to empathise with perpetrators of harm? If yes, reframe: understanding why someone acted is not the same as empathising with their actions. Students can analyse motivations, contextual pressures, and available choices without being asked to feel what an oppressor felt.
   - Does the topic involve lived experiences that some students in the class may personally hold? If sensitivity notes indicate this, design the activity so that students are never required to speak for their own group or correct others' perspective-taking.
   - Are there perspectives that should NOT be included in the activity because including them would require treating harmful worldviews as epistemically equivalent? Name these where relevant.

5. ASSESSMENT CRITERIA:
   Focus on quality of reasoning, not emotional performance:
   - Evidence quality: Did students use appropriate sources? Did they cite context, not just imagination?
   - Complexity acknowledgement: Did students recognise that the perspective is not monolithic?
   - Uncertainty expression: Did students say "we do not know" where evidence is absent, rather than inventing a position?
   - Contextualisation: Did students situate the perspective within its historical/cultural conditions, rather than applying contemporary values?
   Do NOT assess: how much empathy students expressed, how emotionally engaged they seemed, or whether they felt sad, troubled, or moved.

Self-check: Am I designing an activity that develops genuine understanding of complexity, or one that asks students to perform empathy? Are the anti-projection guardrails specific to this topic, not generic? Is the activity developmentally appropriate? Have I checked whether any perspectives in this activity risk asking students to empathise with perpetrators rather than understand them?

Return exactly:

## Perspective-Taking Designer: [Topic Label]

**Subject and learning goal:** [Brief restatement]
**Epistemic stance:** The goal is contextual understanding, not emotional identification. Evidence replaces imagination where it exists; uncertainty is named where it does not.

### Safety Check
- **Perpetrator empathy risk:** [Yes/No — and how it is addressed if yes]
- **Lived experience in class:** [How to handle if yes]
- **Perspectives to exclude or handle carefully:** [If any]

### Developmental Calibration
- **Age range:** [Student age range]
- **Selman stage:** [Stage and implications]
- **Adjustments made:** [How complexity, language, and synthesis expectations are calibrated]

### Activity Sequence

**Phase 1: Context-Building (before perspective-taking begins)**
- What students need to know: [specific content]
- Recommended sources or materials: [types]
- Time estimate: [brief]
- Key question to anchor the phase: [question]

**Phase 2: Perspective Identification**
- Perspectives available and evidenced: [list with brief description of evidence base for each]
- Perspectives that are underdocumented: [and what to say to students about this]
- What to avoid: [common flattening — e.g. treating a diverse group as a single perspective]

**Phase 3: Perspective Exploration**
- Student task: [specific activity — e.g. read primary source, annotate, respond to guiding questions]
- Guiding questions (for each perspective):
  - What did [person/group] know or not know at this moment?
  - What pressures, loyalties, or constraints shaped their choices?
  - What evidence do we have for how they understood this situation?
  - What do we not know, and why might that knowledge be absent?
- Evidence requirement: [What sources students must use; what substitutes are not acceptable]

**Phase 4: Synthesis**
- Discussion prompt: [How does this situation look different from each perspective? What aspects remain uncertain?]
- Synthesis task: [Brief — written, visual, or verbal — that requires students to hold multiple perspectives simultaneously and name what they do not know]

### Anti-Projection Guardrails (topic-specific)
1. [Guardrail specific to this topic]
2. [Guardrail specific to this topic]
3. [General instruction: "If students cannot find evidence for how a person or group experienced this, they should say 'we do not know' rather than inventing a perspective."]

### Assessment Criteria
| Criterion | Strong evidence of understanding | Needs development |
|---|---|---|
| Evidence use | Uses specific sources; cites context | Relies on imagination or presentism |
| Complexity | Names diversity within the perspective | Treats group as single voice |
| Uncertainty | Names what is unknown with reasons | Invents positions where evidence is absent |
| Contextualisation | Situates perspective in its historical/cultural conditions | Applies contemporary values to past/other context |

Note: Emotional engagement is not an assessment criterion. Students who engage with careful reasoning and intellectual humility have succeeded, regardless of affective response.
```

## 常见误区

1. **要求学生想象“他们自己会有什么感受”。** 这是投射，而非视角采择。活动必须追问该人物或群体**实际上**经历了什么（并依据证据），而不是如果把学生传送到那个时代他们会有什么感受。
2. **把群体当作单一视角。** “日本人对广岛的看法”不是一个单一视角——它涵盖了极其广泛的经历、信仰和反应。务必具体指明社群、派系或角色。
3. **跳过背景建构。** 学生如果事先不了解塑造那些视角的社会世界，就不可能形成真正的历史或文化视角。跳过背景建构直接进入角色扮演或“热点座椅”（hot seating）的活动，只会产出表面生动但认知浅薄的投射。
4. **评价情感表演。** 根据表现出的共情程度或情感投入来给视角采择活动打分，奖励的是表演，而非理解。对于与主题有个人渊源的学生来说，这也可能造成心理痛苦。
5. **要求学生与加害者共情。** 理解某人为何参与施害——背后的结构性压力、有限的替代选择、反抗的代价——是正当的历史与伦理探究。而与他们共情（感受他们的感受、从他们的道德框架内部去认同）则是另一回事，在学校情境中往往并不恰当。

## 核查清单

- [ ] 四阶段序列完整，每个阶段都有具体任务。
- [ ] 防投射护栏针对具体主题设计，而非泛泛而谈。
- [ ] 为每个视角至少指定了一种史料/证据类型。
- [ ] 明确指示学生在缺乏证据时说出“我们不知道”。
- [ ] 没有将任何视角呈现为铁板一块的单一声音。
- [ ] 安全检查处理了与加害者共情的风险。
- [ ] 评价标准聚焦于推理质量，而非情感表演。
- [ ] 根据指定年龄段提供了发展阶段校准。

## 已知局限性

1. **本技能负责设计活动，但无法确保学生必然发展出真正的视角采择能力。** 课堂引导的质量比活动设计更重要。如果教师重想象轻证据，或按情感投入打分，那么无论活动设计得多么精良，护栏都会形同虚设。
2. **敏感历史或文化主题的视角采择需要本技能无法提供的学科专业知识。** 即使印巴分治的活动设计得再好，如果教师不了解这段历史，依然会失败。本技能搭建的是教学法脚手架，而非学科内容知识。
3. **防投射护栏能减少但无法彻底消除投射。** 学生会将自己的认知框架和经历带入任何视角采择练习。护栏指明了认知上更严谨的路径，但无法阻止学生走更省力的老路。
4. **对于由学生从未经历过的处境所塑造的视角，活动可以培养智识理解，但无法带来体验式共情。** 未经历过贫困、流离失所或歧视的学生，能够理解产生这些处境的结构性条件；但他们无法被“强行变成”切身感受过这些处境，活动也不应宣称能做到这一点。
