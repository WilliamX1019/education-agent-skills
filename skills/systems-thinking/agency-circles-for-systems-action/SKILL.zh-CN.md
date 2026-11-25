---
# AGENT SKILLS STANDARD FIELDS (v2)
name: agency-circles-for-systems-action
description: "在系统分析之后绘制控制圈、影响圈与关注圈。适用于学生需要展现明智的能动性、同时避免让他们为所有系统问题承担个人责任的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "systems-thinking/agency-circles-for-systems-action"
skill_name: "系统行动能动性圈"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Covey (1989) — The 7 Habits of Highly Effective People (circle of concern/influence)"
  - "Zimmerman (2002) — Becoming a self-regulated learner (agency and self-regulation)"
  - "Manyukhina & Wyse (2019) — Learner agency and the curriculum: a critical realist perspective"
  - "Meadows (2008) — Thinking in Systems (leverage points and systemic action)"
input_schema:
  required:
    - field: "system_issue_or_aspiration"
      type: "string"
      description: "学生正在思考的系统议题或愿景"
    - field: "context"
      type: "string"
      description: "班级、学校、社区、生态或项目背景"
  optional:
    - field: "iceberg_or_system_map"
      type: "string"
      description: "可供借鉴的先前系统分析"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "stakeholders"
      type: "array"
      description: "在系统中扮演角色的个人或群体"
    - field: "constraints"
      type: "string"
      description: "安全、权限、政策、时间或资源限制"
output_schema:
  type: "object"
  fields:
    - field: "agency_map"
      type: "object"
      description: "控制区、直接影响区、集体/制度影响区与关注区"
    - field: "action_options"
      type: "array"
      description: "与各区域相匹配的安全行动选项"
    - field: "adult_responsibility_flags"
      type: "array"
      description: "不应推卸给学生的议题标记"
    - field: "reflection_prompts"
      type: "array"
      description: "不带自责的能动性反思提示"
chains_well_with:
  - "systems-awareness-iceberg"
  - "aspirational-systems-iceberg"
  - "mental-model-mapper"
  - "agency-scaffold-generator"
  - "self-regulation-scaffold-generator"
  - "project-brief-designer"
teacher_time: "5 分钟"
tags: ["agency", "circle-of-control", "systems-action", "student-voice", "wellbeing", "influence", "collective-action"]
---

# 系统行动能动性圈（Agency Circles for Systems Action）

## 本技能的功能

帮助学生和教育工作者将可能的应对行动分类为：他们能够直接控制的事项、能够通过关系与影响推动的事项、需要集体或制度行动的事项，以及目前只需如实指认而无需个人背负的关注事项。它将“控制圈 / 影响圈 / 关注圈”传统框架适配于慈悲系统（compassionate systems）工作之中。

核心设计举措在于避免将系统性问题过度个人化。不应告诉学生结构性问题仅仅是他们自己的心态问题；与此同时，系统思考也不应让他们感到无力崩溃。本技能将分析转化为明智的能动性：微小的行动、关系建立、证据分享、伙伴合作、倡导发声以及审慎地指认现实限制。

## 循证依据

Covey 推广了关注圈与影响圈，使其成为实用的能动性框架。关于学习者能动性的教育研究提醒我们，能动性是关系性的、受结构制约的，而不仅仅是个体意志。Meadows 的杠杆点框架有助于将能动性与系统结构而非孤立的个人努力联系起来。两者结合形成了一个兼具谦逊与行动力量的工具：在可能之处行动，与他人共同施加影响，并如实指认更大层面的责任归属。

## 输入规范

必填：
- **系统议题或愿景：** 学生想要回应的问题，或想要培育的愿景。
- **情境：** 该行动可能发生的场所。

可选：
- **冰山图或系统图：** 先前的分析成果。
- **学生水平：** 年龄/年级。
- **利益相关方：** 谁拥有正式或非正式权力。
- **限制条件：** 权限、安全、政策、时间、资源。

## Prompt

```text
You are helping students and/or educators translate systems analysis into wise agency using agency circles.

Inputs:
System issue or aspiration: {{system_issue_or_aspiration}}
Context: {{context}}
Iceberg/system map: {{iceberg_or_system_map}}
Student level: {{student_level}}
Stakeholders: {{stakeholders}}
Constraints: {{constraints}}

Rules:
1. Use four zones, not three:
   - Control: what students/teacher can directly do or choose.
   - Direct influence: what they can affect through relationship, evidence, modelling, invitation, or dialogue.
   - Collective/institutional influence: what requires adults, leaders, community partners, policy, money, or coordinated action.
   - Concern: what matters but is outside current influence; name it without pretending students must fix it.
2. Never place systemic responsibility only on students.
3. Connect each action to prior systems analysis: which pattern, structure, or mental model does it touch?
4. Prefer small safe experiments over heroic action.
5. Include wellbeing: acting should not require students to sacrifice safety, dignity, or belonging.
6. Include partnership: who needs to be invited, informed, or asked?

Return exactly:

## Agency Circles for Systems Action: [Issue/Aspiration]

**Context:** [brief]
**Important stance:** Agency is real, but responsibility is shared across the system.

### Circle 1: Direct Control
Things we can directly do or choose:
- **Action:** [specific]
  - **Touches:** [pattern/structure/mental model]
  - **Evidence of effect:** [what to notice]
  - **Safety check:** [risk]

### Circle 2: Direct Influence
Things we may influence through relationships, evidence, modelling, or dialogue:
- **Influence move:** [specific]
  - **Who is involved:** [stakeholder]
  - **How to approach:** [language/process]
  - **Evidence of effect:** [what to notice]

### Circle 3: Collective or Institutional Influence
Things that require partnership, adult authority, policy, resources, or coordination:
- **Collective move:** [specific]
  - **Who holds authority/resources:** [stakeholder]
  - **Student role:** [evidence, voice, proposal, participation]
  - **Adult/institutional responsibility:** [what adults must own]

### Circle 4: Concern to Name Without Carrying Alone
Things that matter but are not currently controllable:
- [Concern]
  - **Why it matters:** [reason]
  - **How to hold it:** [learn, name, witness, seek allies, avoid self-blame]

### Recommended First Step
[One low-risk action or experiment that fits the current sphere of control/influence]

### Reflection Prompts
- What are we taking responsibility for that is truly ours?
- What belongs to adults, leaders, institutions, or wider systems?
- What can we influence together that none of us can influence alone?
- What evidence would show that our action is helping rather than only making us feel busy?

Self-check: Do not tell students to fix structural harm alone. Include collective/institutional responsibility. Every action should be specific, safe, and connected to the system map.
```

## 常见误区

1. **把控制圈画得太大。** 学生无法直接控制他人的信念、学校政策或资源分配。
2. **把影响圈画得太小。** 学生往往能够通过证据、示范、邀请、设计与集体发声产生影响。
3. **把关注圈与冷漠混为一谈。** 如实指认超出控制范围的关注事项，本身就是诚实且富有同理心的做法。
4. **英雄式个人主义。** 系统行动通常是集体性的、关系性的。
5. **忽视成人责任。** 有些议题必须由成年人或机构承担行动责任。

## 已知局限性

1. **无法判定实际的权限或准入条件。** 本技能提供控制、影响与关注的一般分类，但特定学生、班级或教师的真实行动空间必须在当地具体评估。输出是一张地图，而非授权书。
2. **较高的元认知要求。** 对于低龄学生而言，如果没有大量成人脚手架支持，“集体影响”与“制度责任”之间的区分可能较难理解。本工具假定学生具备一定的抽象自我反思能力。
3. **不负责具体行动方案的规划。** 能动性圈负责识别区域与选项；设计具体行动或项目需要后续使用 `project-brief-designer` 或 `agency-scaffold-generator`。
4. **存在让结构性伤害显得“容易解决”的风险。** 将行动归入不同圆圈，可能会无意中暗示系统性问题可以通过个人和小型集体行动解决。教师必须明确指出何时需要超越学生能动性的结构性变革。

## 核查清单

- [ ] 使用了四个区域。
- [ ] 行动具体且安全。
- [ ] 在恰当之处明确体现了制度/成人责任。
- [ ] 学生能动性真实存在但有合理边界。
- [ ] 第一步足够小，能够很快付诸尝试。
- [ ] 该图谱减少了无力感，而非淡化了问题本身。
