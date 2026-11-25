---
# AGENT SKILLS STANDARD FIELDS (v2)
name: aspirational-systems-iceberg
description: "设计培育期望事件所需的深层模式、结构、人工制品与心智模式。适用于班级共同构想更美好未来的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "systems-thinking/aspirational-systems-iceberg"
skill_name: "愿景系统冰山"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Center for Systems Awareness (2022) — Guided Iceberg and Aspirational Iceberg practitioner resources"
  - "Senge (1990) — The Fifth Discipline (systems thinking, mental models, learning organisations)"
  - "Meadows (2008) — Thinking in Systems (patterns, structures, leverage points)"
  - "Böll & Senge (2021) — Compassionate Systems Framework, Centre for Systems Awareness (practitioner framework materials, not peer-reviewed)"
input_schema:
  required:
    - field: "desired_event"
      type: "string"
      description: "学生/教育者希望培育的可见事件或结果"
    - field: "context"
      type: "string"
      description: "班级、学校、社区、生态、课程或项目背景"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "current_reality"
      type: "string"
      description: "目前实际发生的情况"
    - field: "stakeholders"
      type: "array"
      description: "受影响的个人、群体或非人类利益相关方"
    - field: "constraints"
      type: "string"
      description: "时间、权力、政策、安全、资源或准入限制"
output_schema:
  type: "object"
  fields:
    - field: "aspirational_iceberg"
      type: "object"
      description: "期望事件、模式/行为、结构/人工制品以及心智模式"
    - field: "first_experiments"
      type: "array"
      description: "能够开始培育该愿景的安全微实验"
    - field: "classroom_sequence"
      type: "object"
      description: "便于教师实施的活动流程"
    - field: "quality_gates"
      type: "array"
      description: "检查设计是否可观察、具有系统性且切实可行"
chains_well_with:
  - "systems-awareness-iceberg"
  - "mental-model-mapper"
  - "agency-circles-for-systems-action"
  - "place-based-inquiry-anchor"
  - "agency-scaffold-generator"
  - "project-brief-designer"
teacher_time: "5 分钟"
tags: ["aspirational-iceberg", "systems-thinking", "future-design", "student-agency", "compassionate-systems", "mental-models", "regenerative"]
---

# 愿景系统冰山（Aspirational Systems Iceberg）

## 本技能的功能

设计“系统冰山”的翻转版本。本技能不是从一个不理想的事件出发追问其背后的深层模式、结构和心智模式，而是从学生或教育者**希望培育的可见事件**出发。随后追问：需要什么样的重复模式才能让这一事件成为常态？需要什么样的结构与人工制品来维系这些模式？又需要培育或转变什么样的心智模式？

这在课堂中尤为有效，因为它将系统思考转向了“可能性”。学生会明白，更美好的未来不是靠许愿或喊口号实现的。它需要条件：让期望事件更有可能发生的常规流程、角色分工、空间安排、支持机制、信息流动、激励机制、人际关系与信念。

## 循证依据

系统意识中心（Center for Systems Awareness）发布了“引导式冰山（愿景版）”实践资源，从“我们试图培育什么？”出发，追问哪些模式、结构、人工制品、价值观、信念和转变后的思维方式能够支撑这一愿景。本技能将该实践工具适配于课堂与课程设计，同时借鉴了 Senge 关于心智模式与学习型组织的研究，以及 Meadows 关于系统结构与杠杆点的研究。

## 输入规范

教师必须提供：
- **期望事件：** 一个可见、可识别的事件或结果。例如：“学生注意到排斥行为并带着关怀做出回应”或“我们班能够不带羞耻感地利用反馈改进作品”。
- **情境：** 这一愿景在何处重要，以及涉及哪些人。

可选上下文：
- **学生水平：** 年龄/年级。
- **当前现实：** 目前通常会发生什么。
- **利益相关方：** 谁受影响或需要参与。
- **限制条件：** 制约行动的因素。

## Prompt

```text
You are facilitating an Aspirational Systems Iceberg. Start with the desired visible event and work downward to the deeper system that would make it more likely.

Inputs:
Desired event: {{desired_event}}
Context: {{context}}
Student level: {{student_level}}
Current reality: {{current_reality}}
Stakeholders: {{stakeholders}}
Constraints: {{constraints}}

Rules:
1. Make the desired event observable. If the aspiration is vague, translate it into visible evidence: what would someone see, hear, read, or experience?
2. Work downward from aspiration to conditions:
   - Event: What are we trying to grow? What visible evidence would show it is happening?
   - Patterns and behaviours: What repeated actions, habits, interactions, and trends would need to become normal?
   - Structures and artefacts: What routines, roles, spaces, tools, protocols, schedules, policies, resources, rituals, feedback loops, or artefacts would sustain those patterns?
   - Mental models: What beliefs, values, assumptions, identities, and definitions of success would need to be strengthened, questioned, or shifted?
3. Include current reality without letting it dominate. The purpose is design, not complaint.
4. Avoid magical thinking. Every aspiration must be connected to concrete structures and small experiments.
5. Preserve agency and responsibility. Do not imply students alone must fix institutional or systemic problems.
6. End with first safe experiments that the class or teacher can try within their real sphere of influence.

Return exactly:

## Aspirational Systems Iceberg: [Desired Event]

**Context:** [brief]
**Design stance:** We are identifying the conditions that could help this aspiration grow.

### 1. Desired Event
**What we want to see happen:** [observable event]
**How we would recognise it:**
- [Visible/heard evidence]
- [Student/community experience evidence]
- [Artefact/product/data evidence]

### 2. Patterns and Behaviours to Grow
- [Repeated behaviour/habit/interaction]
- [Trend over time]
- [Pattern of response when difficulty appears]

### 3. Structures and Artefacts to Create or Strengthen
- **Routines:** [repeatable practices]
- **Roles:** [who holds what responsibility]
- **Spaces/materials:** [physical/digital/environmental supports]
- **Protocols/tools:** [scripts, forms, prompts, checklists, dialogue moves]
- **Time and rhythms:** [when this happens]
- **Feedback loops:** [how the system notices whether it is growing]
- **Institutional supports:** [adult, policy, resource, community supports]

### 4. Mental Models to Cultivate or Shift
For each mental model:
- **Current model that may limit growth:** [belief/story]
- **Aspirational model to cultivate:** [belief/story]
- **What would make the new model credible:** [experience/evidence/practice]

### 5. First Safe Experiments
Suggest 3 small experiments:
1. **Experiment:** [small action]
   - **Why this tests the system:** [pattern/structure/mental model]
   - **Evidence to notice:** [what to watch]
   - **Risk/safety check:** [how to keep it low-harm]

### 6. Classroom Facilitation Sequence
- **Opening prompt:** [student-friendly]
- **Individual think time:** [what students write/draw]
- **Group mapping:** [how groups build the iceberg]
- **Gallery walk or discussion:** [how patterns across groups are noticed]
- **Action selection:** [how to choose one experiment]
- **Reflection:** [what to revisit later]

### Quality Gates
- [ ] Desired event is observable.
- [ ] Patterns are repeated behaviours, not one-off hopes.
- [ ] Structures are concrete enough to design.
- [ ] Mental models are examined with humility, not used to judge people.
- [ ] First experiments sit within real control or influence.
- [ ] Institutional responsibility is named where needed.
```

## 课堂应用示例

- 建设包容性班级文化：“平时觉得自己透明的学生在无需教师提示的情况下被邀请加入小组。”
- 重塑反馈文化：“学生利用批评建议改进作品，同时依然为自己的尝试感到自豪。”
- 规划学生能动性：“学生提出改变校园生活的建议，成年人认真对待他们的论证。”
- 设计再生行动：“学校社区将当地溪流视为一个我们对其负有责任的生命系统。”

## 常见误区

1. **从口号出发。** “每个人都属于这里”还不是一个事件。请将其转化为可见的证据。
2. **只列价值观不设结构。** 价值观很重要，但它们需要常规流程、人工制品、角色分工和反馈回路来支撑。
3. **忽视当前限制。** 怀抱愿景不等于脱离现实。
4. **把重担全压在学生身上。** 同样需要指认成人与制度层面的结构。
5. **把心智模式当成墙上的标语。** 新的心智模式是通过反复的真实体验变得可信的，而不仅仅是墙上的几行字。

## 已知局限性

1. **产出的是设计假设，而非经过验证的项目方案。** 愿景冰山及其支撑结构需要通过真实课堂实验加以检验，才能宣称其有效性。
2. **可能生成遥不可及的结构。** 识别出的部分结构可能超出教师或学生的控制圈。在投入完整设计前，需要教师运用专业判断筛选可行性。
3. **遇到空泛愿景时效果会打折扣。** 相较于“平时独自吃饭的学生在无需教师提示下被同伴邀请加入”，像“一个温馨的班级文化”这样宽泛的表述更难用于设计。本工具需要一个可观察、具体的期望事件才能良好运作。
4. **不测算所需的时间或人力承载力。** 本技能指明需要哪些结构，但不会测算这些结构需要多久才能扎根、需要多少教职工投入，或必须停掉什么现有工作来为它们腾出空间。

## 核查清单

- [ ] 愿景被表述为一个可观察的事件。
- [ ] 至少指认了五项模式/行为。
- [ ] 结构涵盖了常规流程、角色、人工制品、时间、反馈与支持。
- [ ] 心智模式的转变均配有能使其显得可信的体验。
- [ ] 第一个微实验足够小，能够很快付诸尝试。
- [ ] 该活动可以由学生直接参与引导，而不仅限于成人使用。
