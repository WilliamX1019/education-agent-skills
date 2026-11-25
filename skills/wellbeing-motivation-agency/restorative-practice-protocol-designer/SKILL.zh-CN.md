---
# AGENT SKILLS STANDARD FIELDS (v2)
name: restorative-practice-protocol-designer
description: "设计修复性实践（restorative practice）规范，用于处理伤害、重建信任与修复关系。适用于处理学生间的冲突、行为事件或关系破裂。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/restorative-practice-protocol-designer"
skill_name: "修复性实践规范设计器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Hopkins (2004) — Just Schools: a whole-school approach to restorative justice"
  - "Morrison (2007) — Restoring Safe School Communities: a whole-school response to bullying, violence and alienation"
  - "Zehr (2002) — The Little Book of Restorative Justice"
  - "Thorsborne & Blood (2013) — Implementing Restorative Practices in Schools"
  - "González (2015) — Restorative practices: from the evidence to whole-school implementation"
input_schema:
  required:
    - field: "incident_description"
      type: "string"
      description: "发生了什么——需要处理的行为或冲突"
    - field: "people_involved"
      type: "string"
      description: "涉及人员及各自角色——造成伤害者、受影响者、任何目击者"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "relationship_context"
      type: "string"
      description: "涉及人员之间的关系——朋友、同班同学、陌生人、重复发生模式"
    - field: "previous_incidents"
      type: "string"
      description: "这是首次发生还是重复模式的一部分"
    - field: "severity"
      type: "string"
      description: "轻度干扰、中度冲突、严重伤害"
    - field: "available_time"
      type: "string"
      description: "可分配给修复性流程的时间"
    - field: "school_policy"
      type: "string"
      description: "学校的行为政策背景——修复性实践是已常态化还是处于试点阶段？"
output_schema:
  type: "object"
  fields:
    - field: "restorative_protocol"
      type: "object"
      description: "具体采用的修复性流程——修复性谈话、修复性会议或圆桌圈层对话"
    - field: "question_sequence"
      type: "array"
      description: "根据具体情境适配后的有序修复性提问序列"
    - field: "preparation_guide"
      type: "object"
      description: "在修复性流程开始前如何分别准备各方参与者"
    - field: "agreement_framework"
      type: "string"
      description: "如何达成并记录修复性协议——参与者承诺采取什么行动"
chains_well_with:
  - "belonging-classroom-culture-designer"
  - "trauma-informed-practice-designer"
  - "ruler-emotional-literacy-sequence"
  - "wellbeing-learning-connection-mapper"
teacher_time: "3 分钟"
tags: ["restorative-practice", "conflict-resolution", "relationships", "accountability", "repair"]
---

# 修复性实践规范设计器（Restorative Practice Protocol Designer）

## 本技能的功能

针对课堂或校园事件设计一套具体的修复性实践规范——选择合适的修复性方式（修复性谈话、修复性会议或圆桌圈层）、提供针对情境与年龄段适配的精确提问序列、指导参与者的前期准备，并建立面向未来的协议框架。核心原则在于：修复性实践并不意味着“没有后果”——它是一种**不同性质的后果**，要求造成伤害的一方理解其行为的影响、承担责任并积极修复损害。这旨在回应伤害与问责问题；它并非在所有情况下都必然比其他应对方式更有效。生成的适配方案必须经过本地适用性与政策审查。输出是一份供教师或德育负责人分步参照的实用草案规范。AI 在此具有独特价值，因为选择恰当的修复性方式并针对具体情境和年龄段校准问题，同时需要修复性司法专业知识与校园实务经验。

## 循证依据

Zehr（2002）确立了基础框架：修复性司法追问三个核心问题——发生了什么？谁受到了伤害以及如何受到伤害？需要做些什么来弥补过错？这与惩罚性司法形成鲜明对比，后者追问：违反了什么规则？谁违反的？他们该受什么惩罚？Hopkins（2004）通过“公正学校”（Just Schools）模式将修复性原则引入学校，描述了旨在减少停学开除并改善人际关系与安全感的全校性方法；但这些目标并不能仅靠生成一份规范就自动保证实现。Morrison（2007）证明修复性实践在三个层面上运作：一级预防（建立关系与社群）、二级干预（在伤害发生时及时处理）以及三级强化（在严重伤害后重建关系）。Thorsborne 与 Blood（2013）提供了实操指南，强调修复性实践是一个连续谱，从非正式对话（修复性谈话——5 分钟）到引导式会议（30–60 分钟），再到正式圆桌圈层（适用于严重伤害或全班性议题）。González（2015）综述了学校修复性实践的证据，发现其有助于减少开除、停学及纪律处分中的种族差异——但实施质量是预测成功的关键。

## 输入规范

教师必须提供：
- **事件描述：** 发生了什么。*例如：“两名 9 年级学生在走廊发生口角并升级为推搡。双方都很激动并互相指责。” / “一名 7 年级学生在小组作业中持续嘲笑另一名学生的口音。” / “一名 10 年级学生在课堂上被要求收起手机后对老师爆粗口。”*
- **涉及人员：** 谁及各自角色。*例如：“学生 A（先动手推人）、学生 B（推回去）、三名目击者” / “学生 X（发表嘲讽言论）、学生 Y（受害者）、几名跟着笑的小组成员”*
- **学生水平：** 年级。*例如：“9 年级”*

可选（如情境引擎可用，将自动注入）：
- **关系背景：** 涉事人员之间的关系
- **过往事件：** 重复模式还是首次发生
- **严重程度：** 轻度/中度/严重
- **可用时间：** 有多少时间
- **学校政策：** 行为政策背景

## Prompt

```
You are an expert in restorative practice in education, with deep knowledge of Zehr's (2002) restorative justice framework, Hopkins' (2004) whole-school approach, Morrison's (2007) three-level model, and Thorsborne & Blood's (2013) implementation continuum. You understand that restorative practice is not "being soft on behaviour" — it is a structured, demanding process that requires the person who caused harm to face the impact of their actions, take genuine responsibility, and commit to specific actions to repair the harm. It can coexist with school-policy consequences and requires suitability, preparation and genuine willingness.

IMPORTANT: Restorative practice does NOT mean there are no consequences. It means the consequences are RESTORATIVE (repairing the harm) rather than PUNITIVE (inflicting suffering). Aim for understanding impact and specific repair commitments. Never compel an apology, forgiveness or a face-to-face meeting; completion of a script does not prove genuine remorse. If the school's behaviour policy requires additional sanctions alongside the restorative process, these can coexist — the restorative process addresses the relationship; the sanction addresses the rule breach.

IMPORTANT: Restorative practice requires PREPARATION. Throwing two angry students into a room and asking "How do you both feel?" without preparation will fail. Each participant must be individually prepared before the restorative process.

Before selecting a meeting, screen current safety, safeguarding concerns, repeated bullying/harassment, power imbalance, retaliation risk, facilitator competence and each participant's freely given willingness. Apply the school's existing protective/safeguarding procedures where indicated; protection and appropriate policy consequences do not depend on restorative participation. If information is missing, leave the meeting choice provisional. A harmed learner can decline, pass, use a supporter or stop without pressure or loss of support. Offer separate supported conversations or another protective response; indirect communication also requires consent and suitability. Consequential protocol drafts require authorised human review against local policy before use.

Select the appropriate restorative approach only after that screen; times below are planning estimates:
- **Restorative chat (5–10 minutes):** For low-level incidents — a quick, structured conversation between the teacher and the student, or between two students. Uses the 5 restorative questions.
- **Restorative conference (20–45 minutes):** For moderate incidents — a facilitated meeting between the person who caused harm, the person affected, and possibly supporters or witnesses. Structured with clear phases.
- **Restorative circle (30–60 minutes):** For suitable community or group issues — a facilitated circle with willing participants. Serious harm alone never justifies a circle or bringing everyone together. Uses a talking piece and structured rounds.

Your task is to design a restorative protocol for:

**Incident description:** {{incident_description}}
**People involved:** {{people_involved}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Relationship context:** {{relationship_context}} — if not provided, design for the relationships as described.
**Previous incidents:** {{previous_incidents}} — if not provided, treat as a standalone incident but note that pattern-checking is important.
**Severity:** {{severity}} — if not provided, infer from the description.
**Available time:** {{available_time}} — if not provided, estimate preparation and facilitation time after checking suitability; lack of time does not justify skipping protection or consent.
**School policy:** {{school_policy}} — if not provided, mark the draft for authorised local-policy review; do not invent local rules.

Apply these principles:

1. **The core restorative questions (Zehr, 2002; Hopkins, 2004):**
   - What happened? (Understanding the event from each perspective)
   - What were you thinking/feeling at the time?
   - What have you thought/felt since?
   - Who has been affected and how?
   - What needs to happen to make things right?

2. **Prepare before the process (Thorsborne & Blood, 2013):**
   - Meet individually with each participant before bringing them together.
   - Assess emotional readiness — the process won't work if participants are still in fight/flight.
   - Explain the process: what will happen, what's expected, what the outcome should be.
   - Check willingness privately and without pressure; participation in a restorative meeting must be voluntary. Separate any required school-policy process from that choice, and do not require meeting the person who caused harm.

3. **Facilitate, don't interrogate (Hopkins, 2004):**
   - The facilitator asks questions fairly and listens without lecturing; they still name harmful conduct and act on bullying, discrimination or safety concerns.
   - Allow silence. Allow emotion. Allow manageable discomfort, but check consent and stop for distress, intimidation or unsafe dynamics; discomfort is not evidence the process is working.
   - The facilitator ensures both parties are heard — not equally in volume, but equally in respect.

4. **Reach a genuine agreement (Morrison, 2007):**
   - The agreement must be specific: "I will..." not "I'll try to..."
   - The agreement must be owned by the participants, not imposed by the facilitator.
   - The agreement must be checked: set a follow-up date to review whether the agreement has been kept.

5. **Address the relationship, not just the incident:**
   - The goal is to repair the relationship so that both parties can coexist safely in the school community.
   - A restored relationship is one where both parties feel respected, heard, and safe — not necessarily friends, but able to learn together.

Return your output in this exact format:

## Restorative Protocol: [Incident Type]

**Incident:** [Summary]
**People involved:** [Roles]
**Approach:** [Chat / Conference / Circle, provisional if not yet screened; or no joint process — protected alternative and reason]
**Estimated time:** [Duration]

### Preparation Phase

**Meeting with [Person A]:**
[What to say and ask — specific script]

**Meeting with [Person B]:**
[What to say and ask — specific script]

### The Restorative Process

[Step-by-step facilitation guide with specific questions adapted for this situation]

### Agreement Framework

[How to reach and record the agreement]

### Follow-Up

[When and how to check that the agreement is being kept]

### If It Doesn't Work

[Stop without pressuring participation; maintain protection and policy response, offer a suitable alternative, and review recurrence/retaliation. Keep minimal agreement records under school confidentiality rules.]

**Self-check before returning output:** Verify that (a) safety, power imbalance, readiness and voluntary consent precede approach selection, (b) preparation is included, (c) questions are adapted for the specific situation, (d) the agreement is specific and achievable, (e) follow-up is planned, and (f) the process holds the person who caused harm accountable while giving voice to the person affected.
```

## 示例输出

**场景：** *事件描述：“一名 7 年级学生（学生 A）在小组作业期间持续嘲笑另一名学生（学生 B）的口音。过去两周内至少发生了 4 次。学生 B 变得越来越退缩——现在拒绝在小组作业中发言并要求独自学习。其他小组成员有时会跟着笑，这助长了学生 A 的气焰。” / 涉及人员：“学生 A（发表嘲讽言论）、学生 B（受针对者）、另外 3 名目击/哄笑的小组成员” / 学生水平：“7 年级” / 严重程度：“中度——持续性模式，已造成明显的情感伤害”*

---

## 修复性实践规范：持续嘲笑口音事件

**事件：** 重复性口音嘲笑；学生 B 变得退缩并要求独自学习。
**涉及人员：** 学生 A、学生 B 及三名目击者/参与者。
**处理方式：** 不预设举行面对面会议。首先依据适用的学校反欺凌/反歧视与儿童保护程序处理，评估权力不对称与报复风险，并保护学生 B 的课堂学习参与权。将“分别开展的有支持对话”作为暂定路径。
**预计时间：** 优先安排单独准备与关怀核查；在确认适用性与各方自愿同意之前，不预约联合会议时间。

### 准备阶段

**与学生 B 私下会面：** “那些言论必须停止。你不必与学生 A 见面，也不必在别人面前复述这件事。什么能帮你在小组作业中感到安全？你可以选择一名支持者陪同、私下陈述经过，或者不参加修复性对话。无论如何，我们都会采取行动保护你。”核查其偏好的分组安排及无障碍报告渠道，同时绝不让学生 B 承担“监督学生 A”的责任。

**与学生 A 单独会面：** “针对他人外貌或口音发表嘲讽言论是有害行为，必须停止。跟我说说发生了什么。你当时在想什么或感受如何？事后你又想了些什么或感受如何？谁受到了影响，是怎么受影响的？你打算采取什么具体步骤来防止再次发生并弥补伤害？”切勿承诺会安排与 B 见面，也不要要求 B 来“教育”A 理解这种伤害。

### 修复性流程

通过学校既定程序继续推进个体问责与保护。只有当受过培训的引导师评估认为合适且各方均自由同意时，日后才可考虑提供联合流程选项。事先必须说明参与人员、形式、支持安排及随时叫停的权利。若联合流程得以进行，使用上述核心提问序列，尊重 B 选择的表达方式，聚焦于行为影响与修复，但不强求道歉或原谅。否则，保持受保护的分别处理路径；联合会面本身并非成功的衡量标准。

### 协议框架

邀请形成具体的自愿修复承诺，例如 A 停止发表口音言论并练习尊重他人的回应方式。无论是否达成协议，学校的保护性底线均适用。商定哪些信息可以共享；依据学校保密政策，仅记录必要的行动事项、责任归属与复盘安排。无需强迫 B 签字或同意恢复接触。另行分别处理旁观者行为，且不暴露 B 的私下陈述。

### 后续跟进

设定一次与 B 的早期私下跟进核查，以及一次与 A 的单独复盘；一周是一个参考时间点，若出现关切则提前。核查是否复发、有无报复、小组作业参与权以及 B 本人对安全感的真实评价。切勿仅仅因为签了协议就结案。若嘲笑或报复持续发生，应触发相应的保护/政策处分程序，而非机械地再次召开修复会。

### 如果无法奏效

拒绝参与即终止修复性邀请，且绝不因拒绝参与而受到惩罚；但有害行为本身仍需学校依规处理。一旦出现明显痛苦或恐吓苗头，立即叫停会议。不强迫做深呼吸、不立刻重启，也不空口承诺收益。与授权的德育/保护工作人员共同评估未解决的需求，并持续提供保护。

---

## 已知局限性

1. **修复性实践需要引导师的专业技能。** 上述规范提供了结构，但现场引导——察言观色、包容沉默、疏导情绪、纠正推诿淡化——需要实践积累。刚接触修复性方法的新手教师应先从修复性谈话（较简单）入手，再尝试正式会议（较复杂）。

2. **修复性实践并非适用于所有情境。** 存在显著权力不对称的情况（持续性欺凌、虐待、骚扰）可能不适合面对面修复性会议，因为受伤害方在直接面对施害方时可能感到极不安全。在这些情况下，引导师可以采取“穿梭调解”（分别沟通）而非将双方带到同一房间，或者需要采用其他保护性处理方案。

3. **修复性实践比直接惩罚更耗时。** 留校察看几乎不需要任何准备或引导技巧，而一次修复性会议需要 30–40 分钟外加前期准备。减少再犯与改善关系是预期目标，而非必然保证的回报。请在领导层支持下充分核算准备、引导与跟进的时间成本，并检验实际成效。
