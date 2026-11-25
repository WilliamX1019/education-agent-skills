---
# AGENT SKILLS STANDARD FIELDS (v2)
name: udl-barrier-anticipator
description: "在授课前根据学习者差异特征预测学习任务中的参与和理解障碍。区分可通过教学设计解决的障碍与需要专家支持的障碍。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "inclusive-design/udl-barrier-anticipator"
skill_name: "UDL 障碍预测器"
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
    - field: "task_description"
      type: "string"
      description: "学生将完成的学习任务。包括学生阅读、书写、讨论、产出的内容以及如何接受评估。"
    - field: "learner_variability"
      type: "string"
      description: "群体中已知差异性的描述。示例：3 名 EAL 学生（母语为普通话、阿拉伯语、匈牙利语）、2 名 ADHD 学生、阅读水平跨度大（相当于 9–13 岁）、1 名视觉加工困难学生。"
  optional:
    - field: "environment"
      type: "string"
      description: "物理与数字学习环境。示例：共用教室、1:1 Chromebook、无安静分组空间。"
    - field: "time_available"
      type: "string"
      description: "学生完成该任务的可用时间。"
output_schema:
  type: "object"
  fields:
    - field: "barrier_analysis"
      type: "array"
      description: "识别出的障碍，包含：具体障碍名称、受影响的学习者、严重程度（高/中/低）、前瞻性设计调整"
    - field: "design_addressable_barriers"
      type: "array"
      description: "可通过 UDL 设计调整降低的障碍"
    - field: "specialist_referral_barriers"
      type: "array"
      description: "超出通用设计范围、需要个性化支持的障碍"
    - field: "environmental_barriers"
      type: "array"
      description: "物理、数字和社交环境障碍"
    - field: "assessment_barriers"
      type: "array"
      description: "与学习目标无关的评估形式障碍"
chains_well_with:
  - "inclusive-design/udl-lesson-auditor"
  - "inclusive-design/udl-options-designer"
  - "curriculum-assessment/differentiation-adapter"
  - "curriculum-assessment/formative-assessment-technique-selector"
  - "self-regulated-learning/self-regulation-scaffold-generator"
teacher_time: "5-10 分钟"
tags: ["UDL", "inclusive-design", "barrier-analysis", "preventive-design", "access", "learner-variability", "CAST"]
---

# UDL 障碍预测器

## 本技能的作用

根据任务描述与学习者差异特征，在授课前预测可能出现的学习障碍，并提出前瞻性的设计调整建议。这是一项预防性设计技能——它将通用学习设计（UDL）从被动调适（在学生失败后才修改）转向有意识的前置设计（在障碍产生影响前将其移除）。

本技能跨越 UDL 全部三大原则分析障碍，关注容易被忽视的环境障碍，并标出评估形式中与学习目标无关的障碍。关键在于，它明确区分“可以通过教学设计减少的障碍”与“需要超出通用设计之外的专家支持的障碍”。诚实承认这一界限至关重要：声称 UDL 能解决它解决不了的问题，会导致教师低估学生对专业干预的需求而延误转介。

## 循证基础

通用学习设计（UDL）是由 CAST 开发的前瞻性设计框架（Rose & Meyer, 2002; CAST, 2018）。其核心前提——学习环境应当从一开始就为人类全部的差异性而设计，而非事后被动修补——源自神经科学证据：学习差异是常态，而非例外（Meyer, Rose & Gordon, 2014）。前瞻性障碍分析正是这一前提的设计思维应用：在任务、环境或评估中的问题演变为学习失败之前，先行识别它们可能制造障碍的位置。

UDL 作为完整框架的证据强度为中等：在实践界得到广泛认可并植根于相关研究，但实施研究主要由准实验研究和案例研究构成，而非大型随机对照试验（Ok, Rao, Bryant & McDougall, 2017）。然而，这里审视的各个具体障碍类别依托于更强的研究证据：语言需求障碍依托于 EAL/二语习得研究；执行功能障碍依托于工作记忆与自我调节的认知科学研究；感官与知觉障碍依托于无障碍与残障研究；评估形式障碍依托于教育测量中的效度研究。UDL 是一个帮助教师预测并减少障碍的设计框架，它并不能保证完全消除障碍；对于部分有复杂需求的学生而言，它是支持计划的起点，而非全部。

## Prompt

```text
You are a UDL specialist with expertise in barrier analysis and proactive instructional design. Your task is to predict access barriers in the learning task below, given the learner variability profile provided, before the lesson runs. You will suggest proactive design changes and be honest about where barriers require specialist support beyond what universal design can address.

Inputs:
Task description: {{task_description}}
Learner variability: {{learner_variability}}
Environment: {{environment}}
Time available: {{time_available}}

Analyse the task systematically for barriers across all three UDL principles. For EACH barrier you identify:
- Name the barrier specifically (not a category — the specific design element or feature that creates the access problem)
- Explain which learners it most affects and why
- Rate the severity: HIGH (likely to prevent task completion or significantly disadvantage specific learners), MEDIUM (likely to slow progress or increase cognitive load), LOW (minor friction that may affect some learners)
- Suggest a proactive design change — a specific modification to the task design, not just "add support"

Examine barriers across ALL of the following:

**UDL Principle 1: Engagement barriers**
What in the task design may fail to recruit or sustain engagement for some learners? Consider: lack of choice, unclear relevance, high anxiety triggers (timed tasks, public performance, competitive formats), no self-regulation scaffolding for learners with attention variability.

**UDL Principle 2: Representation barriers**
What in how information is presented may exclude some learners? Consider: text complexity and reading level, vocabulary and domain language demands, assumed background knowledge, single-modality presentation (text-only, audio-only), lack of advance organisers, language barriers for EAL learners.

**UDL Principle 3: Action and Expression barriers**
What in how students are expected to respond may exclude some learners? Consider: writing demand for tasks where the goal is not writing, oral performance demand for learners with language anxiety or communication differences, executive function demand (planning, organising, managing time across a complex task), physical or digital access requirements.

**Environmental barriers**
What in the physical or digital environment may create access problems? Consider: noise and distraction, technology access and reliability, lack of quiet space, seating and physical access, peer dynamics and social anxiety triggers.

**Assessment barriers**
Does the assessment format create barriers that are UNRELATED to the learning goal? If the goal is to demonstrate scientific understanding, and the assessment requires extended writing, the writing demand may be a barrier to demonstrating the science — not the science itself. Flag these clearly: they are assessment validity issues as well as access issues.

After analysing barriers:
- Distinguish clearly: which barriers can be reduced through proactive design? Which require individualised accommodations or specialist support beyond what UDL can provide?
- Be honest when a barrier cannot be fully addressed through universal design. Some students need specialist assessment, personalised accommodations, or direct intervention that goes beyond what a teacher can build into a lesson design. Naming this clearly is more helpful than implying UDL can address everything.

Self-check before returning output: Am I naming specific barriers (not generic UDL categories)? Am I distinguishing between barriers I can help design around and barriers requiring specialist support? Am I being honest about the limits of universal design? Have I attended to environmental and assessment barriers, not just instructional ones?

Return in this format:

## Barrier Analysis: [Task Description]

**Learner variability:** [brief]
**Environment:** [brief or "not specified"]

### Barriers by Category

#### Engagement Barriers
| Barrier | Affected learners | Severity | Proactive design change |
|---------|------------------|----------|------------------------|
| [specific barrier] | [specific learners] | HIGH/MEDIUM/LOW | [specific change] |

#### Representation Barriers
| Barrier | Affected learners | Severity | Proactive design change |
|---------|------------------|----------|------------------------|
| [specific barrier] | [specific learners] | HIGH/MEDIUM/LOW | [specific change] |

#### Action and Expression Barriers
| Barrier | Affected learners | Severity | Proactive design change |
|---------|------------------|----------|------------------------|
| [specific barrier] | [specific learners] | HIGH/MEDIUM/LOW | [specific change] |

#### Environmental Barriers
[If present — specific barriers with design changes. If none identified, state "None identified from the information provided."]

#### Assessment Barriers
[If present — barriers in the assessment format unrelated to the learning goal. If none identified, state "None identified."]

### Barriers Requiring Specialist Support
[Be specific about which students and which needs exceed what universal design can address. Do not leave this section empty if complex needs are present in the learner variability — that would imply UDL can address everything.]

### Priority Design Changes (3-5 highest impact)
[The highest-impact proactive design changes, ranked. These are the ones to implement before the lesson runs.]
```

## 常见误区

1. **识别了障碍却未区分严重程度。** 并非所有障碍都同等紧迫。阻碍任务完成的障碍不同于仅仅增加摩擦的障碍。严重程度评级有助于排定优先级。
2. **遗漏环境障碍与评估障碍。** 教学层面 UDL 分析常聚焦于学习活动本身，而环境障碍与评估障碍往往被忽略——但对特定学习者而言，它们恰恰可能是最重大的障碍。
3. **暗示 UDL 能解决所有识别出的障碍。** 对于有复杂需求或未确诊需求的学生，UDL 只是底线。专家转介、个性化便利条件与专业评估往往必不可少。忽略这一区分是有害的。
4. **泛泛的“前瞻性设计调整”。** “提供支架”不是设计调整。“为书面回答提供句式框架：'The evidence shows ____. This suggests ____. I conclude ____.'”才是设计调整。

## 已知局限性

1. **无法预测特定学生面临的所有障碍。** 分析基于所描述的学习者差异特征，而这一描述总是不完整的。许多学生存在尚未被识别、评估或披露的需求。基于任务描述的障碍预测必然是局部的。
2. **可能低估有未识别需求的学生所面临的障碍。** 学习差异经常未被诊断，尤其是对 EAL 学习者（语言困难可能掩盖学习差异）、较少有机会获得专业评估社区的学生，以及已经发展出有效应对策略从而掩盖自身困难的学生。
3. **仅凭任务描述较难预测环境与社交障碍。** 同伴动态、班级文化、创伤反应、围绕表现与失败的文化期望以及师生关系，都会以无法从任务描述中预测的方式塑造可及性。
4. **通用设计存在真实局限——部分学生需要 UDL 无法替代的个性化便利条件或专业干预。** 声称并非如此是有害的：它可能让教师误以为良好的课程设计就足以满足需要专业支持的学生，从而延误恰当转介。UDL 与专业支持不是非此即彼的替代品，而是互补关系：UDL 惠及所有学生，专业支持回应具体识别出的需求。

## 验证清单

- [ ] 障碍具体明确，而非泛泛的 UDL 类别。
- [ ] 每项障碍均已评级严重程度。
- [ ] 明确审视了环境障碍与评估障碍。
- [ ] 前瞻性设计调整具体且可操作。
- [ ] 包含且诚实撰写了“需要专家支持的障碍”部分。
- [ ] 未宣称 UDL 能确保或保证所有学习者无障碍。
- [ ] 可通过设计解决的障碍与需专家转介的障碍之间界限清晰。
