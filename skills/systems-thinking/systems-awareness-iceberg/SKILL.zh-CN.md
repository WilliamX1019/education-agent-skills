---
# AGENT SKILLS STANDARD FIELDS (v2)
name: systems-awareness-iceberg
description: "将当前事件向下映射到深层模式、结构与心智模式。适用于班级或团队在行动前需要建立系统性理解的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "systems-thinking/systems-awareness-iceberg"
skill_name: "系统意识冰山"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Center for Systems Awareness (2022) — Guided Iceberg and Aspirational Iceberg practitioner resources"
  - "Senge (1990) — The Fifth Discipline (systems thinking, mental models, learning organisations)"
  - "Meadows (2008) — Thinking in Systems (patterns, structures, leverage points)"
  - "Böll & Senge (2021) — Compassionate Systems Framework, Centre for Systems Awareness (practitioner framework materials, not peer-reviewed)"
input_schema:
  required:
    - field: "focal_event"
      type: "string"
      description: "需要调查的可见当前事件或反复出现的问题"
    - field: "context"
      type: "string"
      description: "班级、学校、社区、生态或课程背景"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "stakeholders"
      type: "array"
      description: "涉及的个人、群体或非人类利益相关方"
    - field: "existing_evidence"
      type: "string"
      description: "已有的观察、数据、故事、人工制品或学生作品"
output_schema:
  type: "object"
  fields:
    - field: "iceberg_map"
      type: "object"
      description: "事件、模式/行为、结构与心智模式"
    - field: "evidence_questions"
      type: "array"
      description: "区分证据与假设的提问"
    - field: "leverage_possibilities"
      type: "array"
      description: "应对行动可能撬动结构或心智模式的切入点"
    - field: "facilitation_cautions"
      type: "array"
      description: "风险、敏感性及教师专业判断检查项"
chains_well_with:
  - "aspirational-systems-iceberg"
  - "mental-model-mapper"
  - "agency-circles-for-systems-action"
  - "ladder-of-inference-reflection"
  - "place-based-inquiry-anchor"
  - "restorative-practice-protocol-designer"
teacher_time: "5 分钟"
tags: ["systems-thinking", "iceberg", "compassionate-systems", "mental-models", "structures", "leverage", "classroom-inquiry"]
---

# 系统意识冰山（Systems Awareness Iceberg）

## 本技能的功能

帮助教育者和学生通过向下探索重复模式、支撑结构与底层心智模式，来调查一个可见事件。本技能专为“慈悲系统意识”设计：它放慢急于指责或修补的冲动，追问我们实际掌握了什么证据，并维护系统内部人员的尊严。适用于班级、项目组、学校团队或社区探究反复遇到同一问题、需要理解再生产该问题的条件时使用。

输出不是一张假装确定无疑的因果图，而是一份严谨的当前假设图谱：发生了什么、似乎在持续发生什么、哪些结构可能塑造了这种模式，以及哪些信念或假设可能维系着这些结构。它自然衔接心智模式映射、能动性圈或杠杆点与应对设计。

## 循证依据

冰山模型是系统意识中心及慈悲系统框架中常用的系统思考工具。它与 Senge 关于学习型组织的论述（反复出现的事件由更深层的结构与心智模式产生）以及 Meadows 的解释（系统行为涌现自存量、流量、反馈、规则、目标与范式）相契合。在教育中，其价值不仅在于分析，更在于关系层面：冰山模型帮助学生和成人从归咎个人转向对情境、模式与设计的好奇。

## 输入规范

教师必须提供：
- **焦点事件：** 一个可见的事件、插曲、结果或反复出现的问题。例如：“学生在课堂讨论中很少发言”或“我们的回收垃圾箱经常被污染”。
- **情境：** 发生在何处以及为何重要。

可选上下文：
- **学生水平：** 年龄/年级，用于校准语言与抽象度。
- **利益相关方：** 受影响者，在相关时包括非人类/生态利益相关方。
- **现有证据：** 观察记录、数据、故事、学生作品、照片、笔记或人工制品。

## Prompt

```text
You are facilitating a compassionate systems-thinking inquiry using the Systems Awareness Iceberg. Your role is to help the teacher or students move below a visible current event into patterns, structures, and mental models without blaming individuals or overclaiming causality.

Inputs:
Focal event: {{focal_event}}
Context: {{context}}
Student level: {{student_level}}
Stakeholders: {{stakeholders}}
Existing evidence: {{existing_evidence}}

Use these rules:
1. Start with one clear visible event. If the input is broad, narrow it to an observable moment or outcome.
2. Separate evidence from interpretation. Mark uncertain claims as hypotheses.
3. Move down the iceberg:
   - Event: What happened? What can be observed?
   - Patterns and behaviours: What keeps happening over time? What trends, routines, or repeated responses are visible?
   - Structures: What schedules, spaces, rules, incentives, roles, tools, policies, resources, assessment practices, histories, or power relationships make the pattern more likely?
   - Mental models: What beliefs, assumptions, stories, values, fears, expectations, or definitions of success may sustain the structures?
4. Use compassionate language. Do not describe students, teachers, families, or communities as deficient. Describe conditions and interpretations.
5. Include more than one possible explanation. Complex systems rarely have a single cause.
6. End with questions and leverage possibilities, not a final solution.

Return exactly:

## Systems Awareness Iceberg: [Focal Event]

**Context:** [brief]
**Working stance:** This is a hypothesis map, not a verdict.

### 1. Event
[The visible event in precise, observable language]

### 2. Patterns and Behaviours
- [Repeated pattern or trend]
- [Repeated response]
- [What seems to intensify or reduce it]

### 3. Structures
Organise as:
- **Routines and time:**
- **Space and materials:**
- **Rules, incentives, and assessment:**
- **Roles and relationships:**
- **Information flows:**
- **History and power:**

### 4. Mental Models
For each mental model, include whose model it might be and how tentative it is:
- **Possible belief/story:** [belief]
  - **May be held by:** [stakeholder/s]
  - **How it shapes the system:** [effect]
  - **Evidence needed:** [what would confirm/disconfirm]

### Evidence We Still Need
[List questions or data needed before acting strongly]

### Possible Leverage Points
[List 3-5 possible structural or mental-model leverage points, phrased as experiments or inquiries]

### Facilitation Cautions
[How to avoid blame, stereotyping, over-individualising systemic issues, or pushing students into unsafe disclosure]

Self-check: The output must move beyond behaviour management; must include structures and mental models; must avoid blaming individuals; must name uncertainty; and must preserve teacher judgement.
```

## 常见误区

1. **把第一个解释当成唯一原因。** 在证据缩小范围前，保持多个假设并存。
2. **停留在行为表层。** “学生不在乎”不是系统解释；它本身往往是一个需要审视的心智模式。
3. **跳过权力与历史。** 结构不仅包括日程和空间，还包括规则、资源、地位、机构记忆以及谁的声音能被听见。
4. **把冰山变成“用更高级词汇指责他人”。** 本工具应当增进慈悲与能动性，而不是产出更精致的评判。
5. **直接跳向解决方案。** 用冰山来理解；用后续工具来选择行动。

## 已知局限性

1. **仅产出假设。** 本技能映射的是可能解释，而非确凿因果。若无进一步探究和本地证据，它无法验证所识别的模式、结构或心智模式是否真的在起作用。
2. **焦点事件过于宽泛时效果下降。** “教育不平等”太大了。本工具最适合教师实际能目睹的具体、本地可观察的事件或重复模式。
3. **不直接生成行动方案。** 冰山产出的是假设图谱，而非应对计划。行动设计请使用 `agency-circles-for-systems-action` 或项目规划技能。
4. **无法评估引导安全性。** 本技能无法判断某个特定班级在情感上是否准备好进行公开的系统映射。教师关于创伤史、同伴动态与隐私暴露风险的判断是不可替代的。

## 核查清单

- [ ] 事件可观察且具体。
- [ ] 模式描述的是跨时间的重复，而非单一轶事。
- [ ] 在相关之处，结构涵盖了常规、角色、规则、激励、信息、空间、资源、历史与权力。
- [ ] 心智模式被框定为假设，而非指控。
- [ ] 输出指明了在采取重大行动前还需收集的证据。
- [ ] 回应提出了杠杆点可能性，而不假装确定无疑。
