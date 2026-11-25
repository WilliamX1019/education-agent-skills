---
# AGENT SKILLS STANDARD FIELDS (v2)
name: scoping-for-transformative-learning-inquiry
description: "在系统映射或未来推演开始前，界定复杂探究的范围与目的。适用于班级或小组需要就探究对象、利益相关方及尺度达成共识的场景。"
disable-model-invocation: false
user-invocable: true
effort: low

# EXISTING FIELDS
skill_id: "original-frameworks/scoping-for-transformative-learning-inquiry"
skill_name: "变革性学习探究范围界定器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "H3Uni Scoping tutorial and facilitation guide (CC BY-SA 4.0, practitioner method)"
  - "Fazey, I. et al. (2018). Ten essentials for action-oriented and second order energy transitions, transformations and climate change research. Energy Research & Social Science, 40, 54–70."
  - "Rajagopalan, R., & Midgley, G. (2015). Knowing differently in systemic intervention. Systems Research and Behavioral Science, 32, 546–561."
input_schema:
  required:
    - field: "topic_or_concern"
      type: "string"
      description: "群体希望探索的宽泛议题、机遇或挑战——现阶段可以较为模糊"
    - field: "context"
      type: "string"
      description: "探究所处的学校、社区、场所或机构背景"
  optional:
    - field: "student_level"
      type: "string"
      description: "年级或年龄范围"
    - field: "focal_actor_or_system"
      type: "string"
      description: "探究所聚焦的特定个人、群体、组织、生态系统或机构"
    - field: "purpose"
      type: "string"
      description: "探究的目的——理解、规划、倡导、设计或管家式照料"
    - field: "time_available"
      type: "string"
      description: "是单节课、一个单元、一个学期还是更长期的项目"
output_schema:
  type: "object"
  fields:
    - field: "scoping_statement"
      type: "string"
      description: "2–3句话的陈述，明确点出探究场域、焦点行动者与目的"
    - field: "focal_actor_or_system"
      type: "string"
      description: "处于探究中心的具体个人、群体、场所或系统"
    - field: "transactional_environment"
      type: "array"
      description: "与焦点行动者发生直接互动的人员、群体与力量"
    - field: "contextual_environment"
      type: "array"
      description: "间接塑造情境的更宏观力量、历史、政策与条件"
    - field: "time_horizon"
      type: "string"
      description: "探究将考量的时间尺度"
    - field: "evidence_available"
      type: "array"
      description: "群体已经掌握的证据或信息"
    - field: "evidence_needed"
      type: "array"
      description: "探究需要回应的关键问题或信息缺口"
    - field: "boundary_decisions"
      type: "array"
      description: "被刻意划在探究范围之外的内容及原因"
    - field: "quality_gate_results"
      type: "object"
      description: "对范围界定陈述进行结构质量检查的结果"
chains_well_with:
  - "hexagon-complexity-mapper"
  - "three-horizons-learning-transition-mapper"
  - "place-based-inquiry-anchor"
  - "project-brief-designer"
  - "seeds-regenerative-inquiry-cycle"
  - "regenerative-project-design-orchestrator"
teacher_time: "5 分钟"
tags: ["h3uni", "scoping", "inquiry-design", "systems-thinking", "original-framework", "emerging-evidence", "programme-planning"]
---

# 变革性学习探究范围界定器

## 本技能的功能

帮助教师或班级在应用任何其他方法之前，先界定探究的精确场域、焦点行动者与目的。范围界定（Scoping）是 H3Uni 序列的第一步。它防止了系统与未来推演工作中最常见的失败：团队尚未就“我们在调查什么、在什么尺度上调查、从谁的视角出发”达成一致，就直接跳进映射或愿景描绘。

本技能产出一份范围界定陈述——一段 2–3 句话的宣言，明确探究关于什么、对谁重要、在何种尺度上运作以及团队希望达成什么目标。这份陈述成为所有后续方法的锚点。无法追溯回清晰范围界定陈述的三地平线图谱、六边形图谱或两难驾驭练习极易跑偏。

## 证据空间与证据强度

本技能编码了 H3Uni 范围界定（Scoping）方法——一种在应用其他引导工具之前界定复杂探究目的与边界的实践者框架。

### 组件证据

- **H3Uni 范围界定方法**（实践者框架）：H3Uni 的《范围界定教程与引导指南》阐述了交易环境（transactional environment）与背景环境（contextual environment）的区分以及范围界定陈述格式。这些是用于成人政策与战略群体的实践者资源，而非经过评估的课堂工具。
- **Fazey 等人（2018）面向行动研究的十项要素**（中等）：Fazey 与同事将范围界定、目的设定与边界协商确定为有效行动导向探究的基础。他们的框架支持“范围不清晰是探究失败的首要原因”这一论断，尤其在复杂的社会-生态情境中。
- **Rajagopalan & Midgley（2015）系统性干预**（中等）：Midgley 的边界批判确立了“选择将什么纳入或排除在系统探究之外”本身就是一项政治与伦理行为，而非中立的技术步骤。这支撑了本技能对“明确边界决策及受这些决策影响者”的强调。

### 综合证据

课堂范围界定模板——包括交易/背景环境框架、2–3 句话的范围界定陈述格式以及质量把关点——由 Gareth Manning 在布达佩斯 REAL School 基于 H3Uni 的成人引导指南改编，以供学龄学生使用。这一课堂改编方案尚未接受过独立评估。

H3Uni 方法由 Anthony Hodgson 与 Bill Sharpe 创立的 H3Uni 以 CC BY-SA 4.0 协议发布。H3Uni 的正式运营已于 2026 年 5 月结束；其资源库现由 Future Stewards 作为开放共享资源维护。

### 本技能不应声称的内容

H3Uni 范围界定原本面向与专业及政策群体合作的成人引导者设计。此处的课堂改编版本并不声称具备经过同行评审的证据以证明其能提升探究质量、学生学习成果或向其他情境的迁移。教师应将范围界定视为防止过早收窄探究的实用工具，而非拥有已验证学生效应的循证干预方案。

### 适用范围

在任何即将使用 H3Uni 方法（六边形映射、三地平线、两难驾驭）或其他复杂探究工具（SEEDS、项目式学习、再生型项目设计）的探究开始时使用本技能。当学生怀有真诚的关切但不确定如何划定边界或聚焦时，或当不同学生暗自探究着不同问题时，本技能尤为有价值。

## 输入模式

教师必须提供：
- **主题或关切：** 群体希望探索的宽泛议题或机遇。可以较为模糊——本技能将协助聚焦。例如：“气候”、“校园心理健康”、“AI 与学习”、“我们本地的河流”。
- **情境：** 探究发生的地方——塑造相关性的学校、社区、场所或学科情境。

可选：
- **学生水平：** 年级或年龄范围，用于校准语言。
- **焦点行动者或系统：** 如果群体已经知道以谁的视角作为探究锚点，请在此命名。
- **目的：** 探究的最终目的——理解处境、设计回应、提出提案或管家式照料一种关系。
- **可用时间：** 是一节课的探究还是长达一学期的项目，会影响范围大小。

## 提示词

```text
You are facilitating a scoping exercise at the start of a transformative learning inquiry. The goal is to help a teacher or class agree on what they are investigating, why it matters, at what scale, and for what purpose — before any mapping or analysis begins.

Inputs:
Topic or concern: {{topic_or_concern}}
Context: {{context}}
Student level: {{student_level}}
Focal actor or system: {{focal_actor_or_system}}
Purpose: {{purpose}}
Time available: {{time_available}}

Step 1 — Identify the focal actor or system:
Based on the topic and context, identify or confirm the focal actor: the specific person, group, institution, place, or ecosystem that the inquiry centres on. If the input is vague (e.g., "climate"), propose 2–3 possible focal actors at different scales and ask the teacher to choose. Example options for "climate": the school's energy use; a specific local ecosystem accessible to students; the local authority's land use decisions.

Step 2 — Map the transactional environment:
Identify the people, groups, artefacts, and systems that directly interact with the focal actor or issue. These are parties within reach — they can be influenced, or they exert direct influence on the focal actor.

Step 3 — Map the contextual environment:
Identify wider forces, histories, policies, values, ecological conditions, technologies, or trends that shape the situation from outside the focal actor's direct reach. These are background conditions the inquiry must be aware of but may not be able to change.

Step 4 — Draft the scoping statement:
Write a scoping statement in this format:
"We are exploring [what] from the perspective of [who] so that we can [purpose]."

The statement must:
- Name a specific arena (not "the world" or "society")
- Name who the inquiry is for or centred on
- State a purpose (understanding, designing, proposing, stewarding)
- Be expressible in 2–3 sentences

Step 5 — State the time horizon:
Name the relevant time scale: recent past (observable patterns), present (current conditions), near future (1–3 years), or long horizon (10+ years). The time horizon should match the purpose.

Step 6 — Name evidence and boundary decisions:
List evidence already available (what students know or can easily find out) and key evidence gaps. Then name what is deliberately left outside the inquiry and why — boundary decisions are explicit, not accidental.

Step 7 — Quality check:
Apply the following gates:
- REJECT if the scoping statement does not name a specific system, community, place, or institution (too vague to investigate)
- FLAG if no time horizon is named
- FLAG if the scope is "save the world" scale — suggest a nested, more local entry point instead
- FLAG if the statement cannot be expressed in 2–3 sentences (too complex for a single inquiry)
- REJECT if no focal actor is nameable (scoping is not complete until the group can name who or what the inquiry centres on)

Return exactly:

## Inquiry Scope: [Topic]

**Focal actor or system:** [specific name]

**Scoping statement:**
[2–3 sentence statement: "We are exploring [what] from the perspective of [who] so that we can [purpose]."]

**Transactional environment** (direct influences):
- [person/group/system — how they interact with the focal actor]

**Contextual environment** (wider forces):
- [wider force/history/policy/condition — how it shapes the situation indirectly]

**Time horizon:** [named time scale with brief explanation]

**Evidence available:**
- [what students already know or can access]

**Evidence needed:**
- [key questions or information gaps]

**Boundary decisions:**
- [what is deliberately outside this inquiry and why]

### Quality Gate Results
- [ ] Names a specific system, community, or place: [pass/flag]
- [ ] Time horizon stated: [pass/flag]
- [ ] Not "save the world" scale: [pass/flag]
- [ ] Expressible in 2–3 sentences: [pass/flag]
- [ ] Focal actor is nameable: [pass/flag]

### Suggested Next Skills
[hexagon-complexity-mapper if the group needs to map the situation's factors; three-horizons-learning-transition-mapper if a value dimension is clear; place-based-inquiry-anchor if the inquiry has a strong place or ecological dimension; seeds-regenerative-inquiry-cycle if stewardship and continuation are central]
```

## 常见误区

1. **接受模糊的范围。** “我们在调查气候变化”不是范围界定陈述。必须追问具体性：谁的经验、哪个系统的哪个方面？
2. **跳过焦点行动者。** 没有命名焦点行动者的探究会在不同视角间漂移，无法建立共同理解。每项探究都需要一个锚点。
3. **混淆交易环境与背景环境。** 交易环境包含学生能够互动或影响的对象；背景环境从外部塑造处境。两者之间的边界对于现实的行动设计至关重要。
4. **为了迎合预设答案而设定范围。** 旨在产出预设结论的范围界定不是真正的探究。范围应足够宽广以允许意外发现。
5. **把范围当成终局定论。** 范围界定陈述是一个起点，而非契约。当新证据改变了团队实际探究的对象时，请重温并修订它。

## 已知局限

1. **范围只是一项假设。** 在探究伊始看似正确的范围，一旦开始映射往往需要修订。本技能产出的是起点，而非永久框架。
2. **无法评估群体准备度。** 本技能不评估学生是否具备负责任地调查敏感话题所需的背景知识、情感成熟度或社区信任。
3. **焦点行动者的模糊性。** 部分探究存在多个合理的焦点行动者。本技能会标记这一张力，但无法替你裁定——这是教师的教学决策。
4. **不生成证据本身。** 本技能识别所需的证据，但不产出证据。在范围界定与后续方法之间，需要开展研究、实地考察或社区协商。

## 核验清单

- [ ] 范围界定陈述点明了具体场域，而非宽泛类别或全球议题。
- [ ] 焦点行动者或系统已命名且具体。
- [ ] 交易环境与背景环境彼此清晰区分。
- [ ] 明确陈述了时间视野。
- [ ] 边界决策明确说明了排除什么以及为什么。
- [ ] 全部五项质量把关点均已应用并报告。
- [ ] 建议的后续技能按真实名称引用了本技能库中的技能。
