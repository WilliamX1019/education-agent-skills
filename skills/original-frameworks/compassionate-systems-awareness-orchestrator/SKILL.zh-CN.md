---
# AGENT SKILLS STANDARD FIELDS (v2)
name: compassionate-systems-awareness-orchestrator
description: "编排慈悲系统觉察工具，从问题或愿景走向明智行动。适用于班级需要完整探究工作流时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "original-frameworks/compassionate-systems-awareness-orchestrator"
skill_name: "慈悲系统觉察编排器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Center for Systems Awareness (2022) — Compassionate Systems Framework and tools practitioner resources"
  - "Senge (1990) — The Fifth Discipline (systems thinking and learning organisations)"
  - "Meadows (2008) — Thinking in Systems (structures, feedback, leverage points)"
  - "Argyris (1990) — Ladder of inference and defensive reasoning"
  - "Covey (1989) — Circle of concern and influence as agency framing"
input_schema:
  required:
    - field: "starting_point"
      type: "string"
      description: "当前议题、愿景、基于地方的关切、项目构想或班级文化关注点"
    - field: "context"
      type: "string"
      description: "班级、学校、社区、生态或课程情境"
    - field: "intended_use"
      type: "string"
      description: "学生课程、教师规划、项目设计、教职工探究或社区行动"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "available_time"
      type: "string"
      description: "单节课、系列课程、项目、教职工会议或单元"
    - field: "prior_evidence"
      type: "string"
      description: "现有数据、故事、观察记录或学生作品"
    - field: "safety_sensitivities"
      type: "string"
      description: "冲突、创伤、身份认同、权力或儿童保护考量"
output_schema:
  type: "object"
  fields:
    - field: "workflow"
      type: "object"
      description: "推荐的离散慈悲系统工具序列"
    - field: "handoff_outputs"
      type: "array"
      description: "每一步应传递给下一步的产出"
    - field: "lesson_sequence"
      type: "object"
      description: "教师可直接使用的课程序列"
    - field: "stop_or_slow_down_checks"
      type: "array"
      description: "行动前的决策把关点"
chains_well_with:
  - "systems-awareness-iceberg"
  - "aspirational-systems-iceberg"
  - "mental-model-mapper"
  - "agency-circles-for-systems-action"
  - "ladder-of-inference-reflection"
  - "place-based-inquiry-anchor"
  - "project-brief-designer"
teacher_time: "5 分钟"
tags: ["orchestrator", "composite-framework", "practitioner-framework", "compassionate-systems", "systems-thinking", "classroom-inquiry", "student-agency", "regenerative", "workflow"]
---

# 慈悲系统觉察编排器

## 本技能的功能

将慈悲系统觉察（Compassionate Systems Awareness）工具编排为连贯且教师可直接使用的工作流。本编排器在确定路线之前先让路径选项可见，随后协助教育者选择先用哪个工具、应向后传递什么产出、何时因证据或安全原因停下来，以及如何从系统理解走向明智行动——同时避免沦为相互指责、空洞共情或流于表面的项目。

当任务超越单个工具的容量时使用本技能：例如班级希望理解一个反复出现的问题、设计理想文化、调查本地系统或规划再生/行动项目。编排器不应重复离散技能本身，而是负责协调它们。

## 循证基础

该工作流汲取自系统觉察中心（Center for Systems Awareness）及慈悲系统框架（Compassionate Systems Framework），结合了冰山模型、心智模式、反思性对话工具以及能动性/行动框架。它还运用了 Senge 与 Meadows 的系统思维原则：行为涌现于结构与心智模式，而有效行动需要关注杠杆点、反馈与非预期后果。

## 证据空间与证据强度

这是一个复合型实践者框架。它协调了多项循证教学传统，但具体的路径架构尚未作为完整干预方案接受过直接评估。请将其作为课程设计支架使用，而非声称遵循该序列必定产出特定成效。

### 组件证据

- **系统觉察冰山（Systems Awareness Iceberg）**（中等）：由系统觉察中心开发，与 Senge（1990）及 Meadows（2008）一致。目前正被系统思维教育者在课堂中使用；尚无直接 RCT 证据。
- **愿景系统冰山（Aspirational Systems Iceberg）**（新兴）：来自系统觉察中心的实践者资源；课堂研究证据有限，但具备理论基础。
- **心智模式映射器（Mental Model Mapper）**（中等）：植根于 Argyris & Schön（1974）、Senge（1990）与 Meadows（2008）。理论基础坚实；向 K-12 课堂情境的应用主要由实践者推动。
- **推论阶梯（Ladder of Inference）**（中等）：Argyris（1990）；广泛用于组织学习、教练与对话情境。课堂适配由实践者推动。
- **系统行动的能动性圈（Agency Circles for Systems Action）**（中等）：改编自 Covey（1989）；得到学习者能动性研究（Manyukhina & Wyse, 2019）与 Meadows 杠杆点框架的支持。

### 综合证据

包括路径菜单、路由逻辑、交接结构与质量把关点在内的完整编排序列，是 Gareth Manning 的原创综合。在经真实教育者测试并基于课堂使用修订之前，应视其为新兴证据。

### 本技能不应声称的内容

切勿声称本框架已作为项目、干预方案或通往学生成果提升的保障路径获得验证。切勿使用它绕过教师判断、本地知识、文化礼仪、学习者需求或安全检查。

### 适用范围

将本技能用作规划、反思、路径选择与课程连贯性的设计支架。当教育者需要协助在若干可行设计路线间做出选择并理解各自权衡时最为适用。

## 依赖维护

本技能依赖于上述五项离散系统思维工具。每当任一被串联技能变更其证据强度、输出模式、核心质量把关点或主要警示时，请复核本编排器。除非复合工作流本身经过实证检验，否则切勿提高本复合框架的证据等级声明。若某组件技能被弃用或大幅修订，使用前必须先复核本编排路径。

## 输入模式

必填：
- **起点：** 当前议题或愿景。
- **情境：** 发生的场域。
- **预期用途：** 学生课程、教师规划、项目设计、教职工探究、社区行动。

可选：
- **学生水平：** 年龄/年级。
- **可用时间：** 可用时长。
- **先验/已有证据：** 现有观察记录、学生作品、问卷、照片、故事。
- **安全敏感性：** 冲突、创伤、权力、身份认同、儿童保护。

## 提示词

```text
You are orchestrating a compassionate systems awareness workflow. First make the possible pathways visible to the educator. Do not assume the educator knows which pathway fits. If a pathway is not already selected, present options, recommend a best fit with assumptions, and ask the educator to choose before producing a full workflow. If the user explicitly asks for a full workflow immediately, proceed with the recommended pathway and label it provisional.

Choose and sequence the appropriate discrete tools. Do not use every tool by default. Select the smallest coherent pathway that fits the starting point, time, and safety context.

Inputs:
Starting point: {{starting_point}}
Context: {{context}}
Intended use: {{intended_use}}
Student level: {{student_level}}
Available time: {{available_time}}
Prior evidence: {{prior_evidence}}
Safety sensitivities: {{safety_sensitivities}}

Available tools:
- systems-awareness-iceberg: use when starting from an undesirable/current event or recurring issue.
- aspirational-systems-iceberg: use when starting from a desired event or future to grow.
- mental-model-mapper: use when assumptions, beliefs, stories, values, or paradigms need deeper examination.
- ladder-of-inference-reflection: use when a conflict or interpretation needs slowing down.
- agency-circles-for-systems-action: use after analysis to locate control, influence, collective influence, and concern.
- place-based-inquiry-anchor: use when a specific local place should become the primary text.
- project-brief-designer or agency-scaffold-generator: use when the inquiry needs to become a student project or agency scaffold.

Decision rules:
1. Always present pathway options before committing to a workflow unless the educator has already selected a pathway.
2. If the starting point is "what is wrong / why does this keep happening?" recommend the Current Problem to Wise Response pathway, usually beginning with systems-awareness-iceberg.
3. If the starting point is "what do we want to grow?" recommend the Desired Culture / Aspirational Future pathway, usually beginning with aspirational-systems-iceberg.
4. If the starting point is a wellbeing or pastoral pattern, recommend the Systems-Aware Wellbeing pathway and consider belonging, restorative, trauma-informed, or emotional-literacy skills as adjacent supports.
5. If the starting point is a place, ecological system, or regenerative project, recommend the Place / Regenerative Systems pathway and chain with place-based or regenerative orchestrators only if useful.
6. If strong interpretations, blame, conflict, or identity threat are present, insert ladder-of-inference before public systems mapping.
7. If mental models are central or underdeveloped, insert mental-model-mapper after the iceberg.
8. Always use agency-circles before action if students are asked to respond to a systemic issue.
9. Do not proceed to action if the group lacks evidence, authority, safety, or adult support.
10. Keep the pathway small enough for the available time.

Return exactly:

## Compassionate Systems Awareness Pathway Options

Present these options before choosing unless a pathway has already been selected:
- **Current Problem to Wise Response:** for recurring issues or undesired events.
- **Desired Culture / Aspirational Future:** for designing a wanted pattern.
- **Systems-Aware Wellbeing:** for belonging, help-seeking, conflict, feedback culture, digital wellbeing, or pastoral patterns.
- **Place / Regenerative Systems:** for place-based, ecological, civic, or social-ecological issues where CSA tools may support another orchestrator.

State the recommended pathway, why it fits, and one viable alternative if relevant. If no pathway is selected, ask which pathway to develop.

## Compassionate Systems Awareness Workflow: [Starting Point]

**Context:** [brief]
**Intended use:** [lesson/planning/project/staff inquiry]
**Recommended pathway:** [short list of tools in order]

### Why This Pathway
[Explain why these tools, and why this order]

### Step-by-Step Sequence
For each step:
**Step [N]: [Tool Name]**
- **Purpose:** [what this step does]
- **Teacher/student prompt:** [prompt to use]
- **Output to capture:** [exact handoff output]
- **Do not proceed if:** [safety/evidence/quality gate]
- **Feeds into:** [next tool]

### Handoff Map
- From [tool] pass [output] to [tool].
- From [tool] pass [output] to [tool].

### Lesson or Workshop Shape
Adapt to time available:
- **Opening:** [grounding/check-in/framing]
- **Main mapping:** [tool sequence]
- **Sensemaking:** [discussion/gallery walk/synthesis]
- **Agency/action:** [circle or first experiment]
- **Reflection:** [closing prompts]

### Stop or Slow Down Checks
- [ ] Are we blaming individuals for structural patterns?
- [ ] Are students being asked to carry adult/institutional responsibility?
- [ ] Do we have enough evidence to act?
- [ ] Could this activity expose students to identity, trauma, or peer harm?
- [ ] Is the proposed action inside real control or influence?
- [ ] Have we named who else must be involved?

### Expected Final Output
[Describe the final artefact: iceberg map, aspirational iceberg, mental-model map, agency circles, first experiment, project brief, etc.]

Self-check: The workflow must be coherent, not maximal. It must preserve compassion and systems depth. It must end with bounded agency, not heroic fixing.
```

## 常见路径

### 从当前问题走向明智回应
1. 若解读/冲突激烈，先使用推论阶梯。
2. 系统觉察冰山。
3. 心智模式映射器。
4. 能动性圈。
5. 首个安全实验。

### 从理想班级文化走向首个实验
1. 愿景系统冰山。
2. 心智模式映射器。
3. 能动性圈。
4. 能动性支架或项目简报。

### 基于地方的再生探究
1. 基于地方的探究锚点。
2. 系统觉察冰山或愿景系统冰山。
3. 聚焦人与自然关系的心智模式映射器。
4. 能动性圈。
5. 项目简报。

## 常见误区

1. **每次都用上所有工具。** 编排意味着选择必要的路径。
2. **过早转向行动。** 先分析，后能动。
3. **永远停留在分析中。** 有边界的实验能推动学习持续发生。
4. **忽视安全。** 若引导不当，公开的系统映射可能暴露冲突或造成身份伤害。
5. **把愿景误当成解决方案。** 愿景冰山同样需要结构与证据支撑。

## 已知局限

1. **无法评估本地具体条件。** 本编排器协调工具选择，但无法替代教师对特定学生、课堂动态、社区创伤史或文化礼仪的了解——路径适宜性完全取决于编排器无法评估的本地条件。
2. **并非动态反馈回路。** 路径虽以序列呈现，但课堂系统探究是递归循环的。在实践中，随着新证据或冲突浮现，班级可能需要退回先前的工具。编排器提供的是起步地图，而非动态工作流。
3. **面对模糊起点时效果下降。** “改善班级文化”过于宽泛，难以有效路由。当起点指明一个具体的反复出现的问题或清晰陈述的期望事件时，编排器效果最佳。
4. **产出的是计划，而非最终成品。** 本编排器对离散工具进行排序，但并不直接执行它们。如果只使用本技能而不随后运行每个离散工具，产出的仅是一份路径大纲——而非实际的冰山图、心智模式图或能动性圈。

## 核验清单

- [ ] 路径是否以恰当类型的冰山或反思工具起步？
- [ ] 每一步是否都有交接产出？
- [ ] 停止/放缓检查是否明确？
- [ ] 学生能动性是否有边界且得到支持？
- [ ] 教师/机构的责任是否未被隐匿？
- [ ] 最终产出是否足够实用，可供真实教师使用？
