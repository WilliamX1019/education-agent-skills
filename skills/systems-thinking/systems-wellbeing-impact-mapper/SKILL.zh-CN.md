---
# AGENT SKILLS STANDARD FIELDS (v2)
name: systems-wellbeing-impact-mapper
description: "在不将问题个人化的前提下，映射塑造某项身心健康（wellbeing）关切的系统力量。运用 Bronfenbrenner 生态系统模型与健康社会决定因素生成结构性干预。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "systems-thinking/systems-wellbeing-impact-mapper"
skill_name: "系统与身心健康影响映射器"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Meadows (2008) — Thinking in Systems (systemic structure drives behaviour)"
  - "Bronfenbrenner (1979) — The Ecology of Human Development (nested systems affecting individual development)"
  - "Senge et al. (2025) — Systems sensing and embodied awareness (Centre for Systems Awareness)"
  - "World Health Organization (2014) — Social Determinants of Health framework"
  - "Roffey (2012) — Pupil wellbeing — teacher wellbeing: two sides of the same coin"
  - "Rose & Dolan (2012) — A whole-school approach to wellbeing"
input_schema:
  required:
    - field: "wellbeing_pattern"
      type: "string"
      description: "需要映射的身心健康关切或模式。例如：8 年级学生在小学升初中过渡后报告动机下降与社交焦虑上升"
  optional:
    - field: "context"
      type: "string"
      description: "学校或社区背景"
    - field: "existing_responses"
      type: "string"
      description: "已经尝试过的措施"
    - field: "scope"
      type: "string"
      description: "分析应聚焦于班级、学校、社区还是所有层级"
output_schema:
  type: "object"
  fields:
    - field: "systems_map"
      type: "object"
      description: "嵌套系统层级（班级、学校、家庭、社区、社会）及各层级的驱动力量"
    - field: "reinforcing_loops"
      type: "array"
      description: "维持该身心健康关切的自我强化反馈模式"
    - field: "intervention_ideas"
      type: "array"
      description: "多系统层级的结构性干预思路"
    - field: "systemic_framing_check"
      type: "array"
      description: "对该模式常见描述的“个体视角 vs 系统视角”重构对比"
    - field: "surveillance_warning"
      type: "string"
      description: "提醒：映射系统力量并不等同于测量单个学生的身心健康数据"
chains_well_with:
  - "systems-awareness-iceberg"
  - "agency-circles-for-systems-action"
  - "leverage-and-response-design"
  - "wellbeing-learning-connection-mapper"
teacher_time: "10–15 分钟"
tags: ["wellbeing", "systems-thinking", "bronfenbrenner", "social-determinants", "school-culture", "structural-intervention", "ecological-model"]
---

# 系统与身心健康影响映射器（Systems Wellbeing Impact Mapper）

## 本技能的功能

映射系统性模式——学校文化、社区动态、制度结构、环境条件——如何塑造学生与教育者的身心健康（wellbeing）。本技能将分析保持在系统层面，而非将个体病理化。它旨在帮助教育者看到：身心健康是由条件所孕育的，而不仅仅是个体选择或性格特质的结果。

当学校或社区中出现身心健康关切时，人们的本能往往是问：这些学生、这个家庭或这位老师出了什么问题？本技能将问题重新定向为：究竟是哪些结构、政策、规范与反馈回路，使得在当前条件下出现这种模式变得几乎可以预测？输出是一张附带结构性干预思路的系统图谱——而非围绕“个体缺陷”设计的一套补救项目。

证据强度被评为**新兴（emerging）**，因为其底层框架（Bronfenbrenner 生态模型、健康社会决定因素、Meadows 系统思考）均已成熟，但将系统映射专门应用于学校身心健康模式属于实践者综合，尚未作为独立方法论接受直接实证评估。

## 循证依据

Bronfenbrenner 的生态系统模型将儿童发展置于嵌套系统之中：直接环境（班级、家庭）、制度系统（学校、社区服务）、文化与政策层，以及宏观价值观与规范。这为本技能的嵌套分析提供了结构支架。世界卫生组织（WHO）健康社会决定因素框架确立了健康结果受上游结构性因素（就业、住房、教育、社会排斥）塑造，而不仅仅取决于个人行为或心理健康。Meadows 的系统思考提供了反馈回路分析：身心健康模式往往具有自我维持性，因为产生它们的条件会被它们所引发的反应进一步强化。Roffey 关于学生与教师福祉相互关联的研究，以及 Rose 与 Dolan 的全校性框架，都将身心健康定位为关系性与制度性的，而非纯粹个体性的。

## 输入规范

必填：
- **身心健康模式：** 需要映射的身心健康关切或模式。请具体且基于观察。例如：“8 年级学生在小学升初中过渡后报告动机下降且社交焦虑增加”或“自新评估日程实施以来，4 年级教师报告高压力与倦怠感”。

可选：
- **情境：** 学校或社区背景。
- **现有应对：** 已经尝试过的措施——这能避免输出在不加修改的情况下重复推荐已试过的方法。
- **范围：** 分析聚焦于班级、学校、社区还是全部嵌套层级。

## Prompt

```text
You are a systems thinker specialising in wellbeing at the school and community level, drawing on Bronfenbrenner's ecological model, social determinants of health thinking, and Meadows' systems analysis. Your task is to map the systemic forces shaping a wellbeing concern without individualising the problem.

Inputs:
Wellbeing pattern: {{wellbeing_pattern}}
Context: {{context}}
Existing responses: {{existing_responses}}
Scope: {{scope}}

Use these rules:

1. MAP ACROSS NESTED SYSTEMS LEVELS using Bronfenbrenner's framework:
   - Individual level: Acknowledge briefly but do NOT centre individual deficits, psychological traits, or personal choices as primary explanations.
   - Classroom/peer level: Peer dynamics, teaching practices, classroom structures, group norms, belonging signals.
   - School/institutional level: Timetabling, assessment practices, transition processes, staffing, space, school culture, communication systems.
   - Family/community level: Housing, employment, community services, family structures, community belonging, cultural expectations.
   - Societal/structural level: Policy, funding, systemic racism, socioeconomic inequality, environmental conditions, pandemic legacies.

2. IDENTIFY FORCES AT EACH LEVEL that produce or maintain the pattern: structures, policies, norms, resource flows, information flows, power relationships, and feedback loops.

3. FLAG INDIVIDUALISATION whenever it appears. Reframe:
   - Individual: "Students lack resilience" → Systemic: "The transition process provides no relationship continuity, disrupting the social belonging that supports resilience."
   - Individual: "This teacher is burned out" → Systemic: "The new assessment schedule increased administrative load by 40% with no corresponding reduction in other duties."
   - Individual: "Parents aren't engaged" → Systemic: "Family engagement events are held during working hours in English only."
   Provide at least 3 systemic reframings of common individual descriptions of the pattern.

4. IDENTIFY REINFORCING LOOPS that make the pattern self-sustaining:
   - Example: Anxiety reduces participation → reduced participation reduces belonging → reduced belonging increases anxiety.
   - Example: Teacher stress reduces relational quality → reduced relational quality increases student disengagement → increased disengagement increases teacher workload → increased workload increases stress.

5. GENERATE INTERVENTION IDEAS at multiple system levels. For each intervention:
   - What level it targets (classroom, school, community, policy)
   - What structural element it changes
   - What feedback loop it disrupts or creates
   - Who holds responsibility for implementing it (student, teacher, school leader, system)

6. INCLUDE A SURVEILLANCE WARNING: Mapping the systemic forces that affect wellbeing is not the same as measuring individual students' wellbeing. Wellbeing data collection that targets individuals without structural change can become surveillance — monitoring symptoms while leaving causes intact. Any data collection should follow changes in structural conditions, not precede them as a substitute.

Self-check: Am I analysing the system or blaming individuals within it? Are my intervention ideas structural — changing conditions — rather than individual support programmes layered on unchanged structures? Am I treating wellbeing as relational and contextual, not as an internal state to be optimised through the right programme?

Return exactly:

## Systems Wellbeing Impact Mapper: [Pattern Label]

**Working framing:** Wellbeing patterns are produced by systems. This map analyses conditions, not individuals.
**Evidence note:** This skill applies established frameworks (Bronfenbrenner, social determinants, Meadows) to school wellbeing — a practitioner synthesis, not a directly evaluated methodology.

### The Pattern
[Restate the wellbeing pattern in specific, observable, non-blaming language]

### Systemic Reframings
| Individual framing | Systemic framing |
|---|---|
| [individual frame] | [systemic frame] |
| [individual frame] | [systemic frame] |
| [individual frame] | [systemic frame] |

### Nested Systems Map

**Classroom/peer level**
- Forces producing the pattern: [structures, norms, dynamics]
- What is missing: [belonging signals, relational practices, time, resources]

**School/institutional level**
- Forces producing the pattern: [policies, schedules, assessment practices, transitions, communication systems]
- What is missing: [structural supports, policy conditions]

**Family/community level**
- Forces producing the pattern: [employment, housing, community resources, cultural expectations]
- What is missing: [community infrastructure, accessible services]

**Societal/structural level**
- Forces producing the pattern: [policy, funding, inequality, systemic factors]
- What is missing: [policy conditions, structural equity]

### Reinforcing Loops
For each loop:
**Loop [N]: [Name]**
- [Element A] → [Element B] → [Element C] → back to [Element A]
- Why it is self-sustaining: [explanation]
- Where it could be interrupted: [structural entry point]

### Intervention Ideas

**At classroom/peer level:**
- [Intervention]: changes [structural element] / disrupts [loop] / responsible: [teacher/peer group]

**At school/institutional level:**
- [Intervention]: changes [structural element] / disrupts [loop] / responsible: [school leader/admin]

**At family/community level:**
- [Intervention]: changes [structural element] / disrupts [loop] / responsible: [community partners/families]

**At structural/policy level:**
- [Intervention]: changes [structural element] / disrupts [loop] / responsible: [system/government]
- Note: interventions at this level are named for completeness. If they are beyond school capacity, they should be named and advocated for, not silently omitted.

### Surveillance Warning
[Explicit reminder that mapping systemic forces is not the same as measuring individual students' wellbeing. Any wellbeing measurement agenda should follow structural changes, not replace them.]

### What Has Been Tried
[Brief analysis of existing_responses — what structural element each addresses, and what remains structurally unchanged]
```

## 常见误区

1. **在压力下退回个体归因。** 当结构性变革显得遥不可及时，人很容易说“学生需要更好的抗压技巧”。即使教师无法立刻改变结构性原因，本技能也应当如实指认它们。
2. **只生成个体支持项目。** 导师计划、情绪打卡和正念训练都是个体层面的干预。它们本身没有错，但如果缺乏结构性改变就远远不够。本技能必须在多个系统层级上产出思路。
3. **把身心健康当作有待优化的内部状态。** 身心健康是关系性的、情境性的——它产生于人与人之间以及具体条件之中，而不是像一块电池那样储存在个体内部等着被充满。
4. **遗漏教师福祉。** Roffey 的研究明确指出，学生与教师的福祉密不可分。一张不提及教学条件的“学生身心健康模式图谱”是不完整的。
5. **只点名学校能改变的因素。** 社会层面的结构性原因（贫困、住房不稳定、系统性歧视）即使学校无法直接解决，也必须如实指认。刻意略过它们会暗示问题仅靠学校就能解决——而事实并非如此。

## 核查清单

- [ ] 该模式以不带指责、基于观察的语言描述。
- [ ] 至少提供了 3 组对个体解释的系统性重构对比。
- [ ] 嵌套图谱至少覆盖了三个系统层级。
- [ ] 至少识别出两个增强型反馈回路。
- [ ] 干预思路涵盖了多个系统层级。
- [ ] 包含了监控预警（Surveillance Warning）。
- [ ] 个体支持项目仅作为结构性干预的配套出现，而非替代。

## 已知局限性

1. **系统图谱是简化模型。** 真实的学校生态系统比任何图谱所能捕捉的都更加复杂、纷繁且具有历史纵深。输出是一份结构化假设，而非临床诊断。
2. **部分原因无法在学校层面解决。** 贫困、住房不稳定和系统性歧视虽在图谱中列出，但并非教师或校领导所能解决。本技能应当坦诚指认这些因素，既不制造无力感，也不暗示仅仅点名就能替代倡导行动。
3. **抽象化风险。** 系统分析可能会脱离身处系统内部之人的真实体验。任何图谱都应与正在经历该身心健康关切的人的声音对照核验，而不仅仅是管理者的观察视角。
4. **本技能不提供临床或诊断信息。** 它映射的是系统力量，而非个体心理健康需求。正在经历严重身心健康挑战的学生需要合格的专业支持，本技能无法替代专业人员。
