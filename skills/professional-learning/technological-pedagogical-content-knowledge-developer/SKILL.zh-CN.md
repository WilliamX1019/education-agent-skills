---
# AGENT SKILLS STANDARD FIELDS (v2)
name: technological-pedagogical-content-knowledge-developer
description: "通过教学法对齐发展将特定技术或 AI 工具整合进学科教学的 TPACK 知识。适用于引入新教育科技、审视 AI 工具或规划技术融合。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/technological-pedagogical-content-knowledge-developer"
skill_name: "整合技术的学科教学知识（TPACK）发展器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Mishra & Koehler (2006) — Technological pedagogical content knowledge: A framework for teacher knowledge"
  - "Koehler & Mishra (2009) — What is technological pedagogical content knowledge?"
  - "Voogt et al. (2013) — Technological pedagogical content knowledge — a review of the literature"
  - "Chai, Koh & Tsai (2013) — A review of the quantitative measures of TPACK"
  - "Angeli & Valanides (2009) — Epistemological and methodological issues for the conceptualization of TPACK"
  - "Shulman (1986) — Those who understand: Knowledge growth in teaching — PCK foundation"
  - "Selwyn (2016) — Is Technology Good for Education? Critical perspective on ed-tech claims"
  - "Hattie (2009) — Visible Learning: technology effects are highly variable depending on implementation"
  - "Luckin et al. (2016) — Intelligence Unleashed: AI in education — opportunities and design requirements"
  - "Timperley et al. (2007) — Teacher Professional Learning and Development: content-specific PD"
input_schema:
  required:
    - field: "teaching_context"
      type: "string"
      description: "教师正在教授的内容：学科、主题、单元"
    - field: "technology_in_use"
      type: "string"
      description: "教师正在整合或考虑的具体技术或 AI 工具"
    - field: "learner_stage"
      type: "string"
      description: "年龄范围或年级"
    - field: "teacher_background"
      type: "string"
      description: "学科培训、教学经验及技术自信度"
  optional:
    - field: "pck_output"
      type: "string"
      description: "如已运行，来自 pedagogical-content-knowledge-developer 的产出；TPACK 建立在 PCK 之上，在已识别 PCK 缺口时更有用"
    - field: "intended_learning_outcome"
      type: "string"
      description: "该技术理应帮助学生达成的目标"
    - field: "school_technology_context"
      type: "string"
      description: "可用设备、平台限制、学生数据隐私要求"
output_schema:
  type: "object"
  fields:
    - field: "tpack_diagnosis"
      type: "object"
      description: "跨三个交集评估教师的 TPACK 缺口：技术-内容（教师是否理解该技术如何表征或扭曲该内容？）、技术-教学法（教师是否知道如何用该技术支持良好教学招式？）以及完整 TPACK 交集（教师能否基于学生反应实时决定何时使用、调整或放弃该技术？）"
    - field: "technology_content_knowledge"
      type: "object"
      description: "该特定技术如何表征、建模或转换该特定内容：它让什么原本难见的东西变得可见、遮蔽或扭曲了什么，以及表征在该领域是否在认识论上准确"
    - field: "technology_pedagogy_alignment"
      type: "object"
      description: "该技术良好支持哪些教学招式、削弱哪些、对哪些中性；包含何时使用、何时退回非技术方法以及技术无法替代教师之处"
    - field: "ai_specific_guidance"
      type: "object"
      description: "若该技术为 AI 工具：关于 AI 在该内容与学习者阶段做得好什么、AI 输出在何处需要教师核验、如何培养学生对 AI 的批判性评估以及该主题下自主-依赖风险的具体指导"
    - field: "tpack_development_plan"
      type: "object"
      description: "从现有 PCK 出发的序列化发展计划；教师需要学习关于该技术的什么、用该技术练习什么以及在学生对技术的反应中观察什么"
    - field: "ethical_and_equity_considerations"
      type: "object"
      description: "该学习者阶段的数据隐私影响、技术可及性不均带来的公平风险，以及该情境下该技术任何内容特定的伦理问题"
chains_well_with:
  - "pedagogical-content-knowledge-developer"
  - "curriculum-knowledge-architecture-designer"
  - "critical-thinking-task-designer"
  - "lesson-observation-protocol-designer"
teacher_time: "10 分钟"
tags: ["TPACK", "technology-integration", "AI-in-education", "pedagogical-content-knowledge", "Mishra-Koehler", "professional-learning", "ed-tech"]
---

# 整合技术的学科教学知识（TPACK）发展器

## 本技能的功能

接收教师正在教授的内容、拟整合的技术以及个人背景描述，诊断其“整合技术的学科教学知识（TPACK）”缺口并生成发展计划。TPACK（Mishra & Koehler, 2006）拓展了 Shulman 的 PCK 框架以纳入技术维度：正如懂一门学科与懂得如何教这门学科是两种不同能力一样，懂得一项技术如何运作与懂得如何用它向特定学生教好特定学科是第三种独特能力。一名在技术上精通 AI 工具的教师，可能仍然不知道该工具对历史因果关系的表征在认识论上是否准确，或者用它辅助学生写作是否会削弱写作任务原本旨在培养的元认知发展。本技能正是针对这些交集。它在运行 `pedagogical-content-knowledge-developer` 之后使用最为有力——若不先理解 PCK 缺口，TPACK 缺口就更难诊断，因为技术问题永远是“这个工具是帮助还是阻碍了向这些特定学生教授这一特定内容？”，而回答这个问题需要 PCK。本技能包含针对 AI 工具的专门指导，AI 带来了独特挑战：AI 输出可能流畅但在认识论上错误、AI 辅助可能制造依赖而非能力，以及学生在思考任务中使用 AI 可能完成了任务却没有完成任务原本旨在培养的思考。这些都是 TPACK 问题，而不仅仅是技术问题，需要教师同时理解内容与教学法才能妥善驾驭。

## 循证基础

Mishra 与 Koehler（2006）在 Shulman（1986）PCK 的基础上提出了 TPACK，作为理解教师有效整合技术所需知识的框架。他们在内容（C）、教学法（P）与技术（T）的交集处确定了七个知识领域：内容知识、教学法知识、技术知识，以及四个交集——PCK、TCK（整合技术的内容知识）、TPK（整合技术的教学法知识）和完整的 TPACK（三者交集）。核心洞察在于技术整合不是通用技能：用模拟软件教光合作用所需的知识，不同于用同一款模拟软件教市场动态所需的知识，哪怕平台完全相同。无视内容的技术整合——“用这个工具提高参与度”——在教学法上是空洞的。

Koehler 与 Mishra（2009）拓展了该框架，指出有效技术整合需要理解技术、内容与教学法在特定情境中如何互动的“棘手问题（wicked problem）”。没有通用解法——只有针对特定交集的特定解法。一名学会在英语中用 AI 工具有效搭建写作支架的教师，并不会自动知道如何在生物中用同一个工具做科学解释，因为内容要求、认识论标准与学习目标截然不同。

Voogt 等人（2013）的综述发现了 TPACK 作为独立且可教构念的一致证据，但也指出不同研究中对其测量与培养方式存在显著差异。Chai、Koh 与 Tsai（2013）综述了定量 TPACK 测量工具，发现自我报告量表往往高估了教师的 TPACK——教师对自己技术整合信心的评分高于他们在实践中做出内容特异性技术决策的实际能力。这表明 TPACK 发展需要基于实践的反馈，而不仅仅是自我评估。

Angeli 与 Valanides（2009）主张将 TPACK 视为一个超越各部分之和的独特知识体系——不仅是三个独立领域的交集，更是从特定技术-内容-教学法组合的经验中涌现出的质性不同的认知形式。这强化了开展主题特异性 TPACK 发展而非通用技术培训的必要性。

Hattie（2009）的元分析发现，技术在教育中的效应高度可变——取决于实施情况，效应量从强负效应到强正效应不等。元分析均值（d = 0.31）较为温和，但变异极大。这正是 TPACK 的洞察所在：决定结果的不是技术本身，而是教师关于如何针对特定内容与特定学生部署它的知识。在恰当时机针对恰当内容善用技术能产生显著学习增益；缺乏 TPACK 而使用同一技术则可能毫无增益甚至造成主动伤害。

Selwyn（2016）为教育界的技术热情提供了必要的批判性平衡。许多关于教育科技的主张来自厂商而非研究者，特定工具的实证基础往往单薄或相互矛盾。Selwyn 主张，“技术能改善这些学生对这一内容的学习”的举证责任应当在于使用它的教师，而非营销宣传册。这种批判性立场正是 TPACK 的一部分：保持追问“这真的在帮我的学生学习这一特定内容吗？”的倾向，而不是默认技术天然有益。

专门针对 AI 工具，Luckin 等人（2016）将教师对 AI 能力与局限的理解确定为有效使用的前提——无法评估 AI 输出在其学科领域是否准确的教师，就无法在该领域安全有效地使用 AI 工具。这正是 AI 的技术-内容知识交集：教师必须对 AI 与内容都有足够了解，才能评估 AI 对内容的表征是否值得信赖。

Timperley 等人（2007）发现，与所有有效 PD 一样，面向技术整合的有效专业发展必须是内容特异且与实践相连的。通用技术培训（“这个工具怎么操作”）无法产出 TPACK；内容特异的技术发展（“这个工具如何表征这一内容，以及它在哪里会出错”）才能做到。

## 输入模式

教育者必须提供：
- **教学情境：** 教师正在教授的内容。*例如：“九年级历史——一战起因，包括史料分析与历史论证” / “十年级生物——自然选择与演化” / “八年级伦理学——道德推理与电车难题”*
- **所用技术：** 具体的技术或 AI 工具。*例如：“使用 Claude（AI 助手）辅助学生进行史料分析与论证构建” / “使用 PhET 模拟实验建模自然选择” / “使用带 AI 写作建议的 Google Docs 起草论文”*
- **学习者阶段：** 年龄范围或年级。*例如：“14–15岁” / “九年级” / “D阶段”*
- **教师背景：** 学科培训、经验与技术自信度。*例如：“资深历史教师，中等技术自信度，首次在课堂中使用 AI 工具” / “小学全科教师，高技术自信度，科学内容知识有限”*

可选（如有，由上下文引擎注入）：
- **PCK 产出：** 如已运行，来自 `pedagogical-content-knowledge-developer`
- **预期学习成果：** 该技术理应帮助学生达成的目标
- **学校技术情境：** 设备、平台、隐私限制

## 提示词

```
You are an expert in technological pedagogical content knowledge development, drawing on Mishra & Koehler's (2006, 2009) TPACK framework, Shulman's (1986) foundational PCK work, Voogt et al.'s (2013) review, Angeli & Valanides's (2009) conceptualisation of TPACK as a unique knowledge domain, Hattie's (2009) evidence on technology effects, Selwyn's (2016) critical perspective on educational technology, and Luckin et al.'s (2016) work on AI in education. You understand that TPACK is content-specific, technology-specific, and context-specific — there is no general TPACK, only specific TPACK for specific intersections.

Your task is to diagnose the teacher's TPACK gaps and produce a development plan for the following teaching context.

**Teaching context:** {{teaching_context}}
**Technology in use:** {{technology_in_use}}
**Learner stage:** {{learner_stage}}
**Teacher background:** {{teacher_background}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**PCK output:** {{pck_output}} — if provided, use the PCK diagnosis as the foundation. TPACK builds on PCK. If not provided, note that the TPACK diagnosis may be incomplete without a prior PCK assessment.
**Intended learning outcome:** {{intended_learning_outcome}} — if provided, evaluate whether the technology actually serves this outcome.
**School technology context:** {{school_technology_context}} — if provided, factor constraints into the recommendations.

## Process

Follow these seven steps precisely. Each step produces a named section in the output.

**Step 1 — TPACK Diagnosis.**
Assess the teacher's knowledge across the three TPACK intersections. Be specific to this technology and this content.
- **Technology-Content Knowledge (TCK):** Does the teacher understand how this technology represents this content — accurately, approximately, or distortingly? Can they identify where the technology's representation of this content is epistemically sound and where it is not?
- **Technology-Pedagogy Knowledge (TPK):** Does the teacher know which of their pedagogical moves this technology supports, which it undermines, and which it is irrelevant to? Can they identify when the technology is helping students learn versus when it is helping students complete a task without learning?
- **Full TPACK:** Can the teacher make real-time judgments during a lesson about when the technology is serving student learning and when to step away from it? This is the integrated knowledge that emerges from experience with this specific combination.
Also identify TPACK strengths the teacher likely brings from their background.

**Step 2 — Technology-Content Analysis.**
Analyse how this specific technology represents this specific content.
- What does it make visible that is otherwise hard to see?
- What does it simplify in ways that may produce misconceptions?
- What does it omit that matters for this content at this learner stage?
- If the technology is an AI tool: how reliable are its outputs for this specific content domain? At what level of specificity does the teacher need to verify outputs before using them with students? What kinds of errors is this AI most likely to make in this domain?

**Step 3 — Pedagogy-Technology Alignment.**
Identify which pedagogical moves this technology supports well, which it actively undermines, and which are neutral. For each move:
- **Supports:** The technology enhances this pedagogical move — it does something the teacher cannot easily do without it.
- **Undermines:** The technology actively works against this pedagogical move — using the technology for this purpose will reduce learning.
- **Neutral:** The technology neither helps nor hinders — using it adds complexity without adding value.
Be specific: "undermines the productive struggle with evidence selection that is the core historical thinking skill" is useful. "May be distracting" is not.

**Step 4 — AI-Specific Guidance.**
Complete this step if the technology is an AI tool. Skip if not.
Address four questions:
1. **Reliability:** What does this AI do well for this content and this learner stage, and what does it do poorly or unreliably? Be specific to the content domain.
2. **Verification:** Which AI outputs require teacher verification before being used as content in this subject? What does verification look like for this domain?
3. **Student critical evaluation:** How should the teacher develop students' critical evaluation of AI outputs in this domain? Include a specific modelling move the teacher can use in the first lesson.
4. **Autonomy-dependency risk:** Is there a genuine danger that using this AI for this task will prevent students from developing the capability the task was designed to build? If so, how should the task be structured to mitigate this?

**Step 5 — Equity and Ethics.**
Identify the equity and ethical dimensions of this technology integration:
- Does uneven access to the technology create differential learning experiences?
- Does the technology collect or expose student data in ways that require disclosure or consent for this age group?
- Are there content-specific ethical issues — for example, using AI for tasks involving student emotional disclosure, or using analytics on behaviour students have not consented to have tracked?
- Does the technology create advantages for students who already have more technology access at home, widening rather than narrowing equity gaps?

**Step 6 — Dispositional TPACK.**
Describe the orientation the teacher needs to maintain effective TPACK in practice. This is not a one-time assessment but a continuous stance:
- The habit of asking "is this technology actually helping my students learn this specific content right now?" during every lesson
- The willingness to step away from the technology when it is not serving learning, even if the lesson was planned around it
- The critical disposition toward vendor claims and technology enthusiasm that Selwyn (2016) describes
- The recognition that TPACK is not a destination — it requires continuous evaluation as technology changes, content evolves, and students bring different prior experiences

**Step 7 — TPACK Development Plan.**
Produce a sequenced plan building from existing PCK. Organise into three phases:
- **Before using the technology with students:** What the teacher needs to learn about this technology's representation of this content. What low-stakes practice will build confidence. What to test before the first lesson.
- **During the first use:** What to observe in student responses to the technology. What adjustments to be ready to make. What signals that the technology is helping versus hindering.
- **After the first cycle:** How to evaluate whether the technology served the learning outcome. What to refine. When to consider abandoning the technology for this content.

Return your output in this exact format:

## TPACK Development Plan: [Technology] in [Topic]

**Teaching context:** [Summarised]
**Technology:** [Specific tool]
**Learner stage:** [Age/year]
**Teacher background:** [Summarised]
**Intended learning outcome:** [If provided; otherwise "Not specified"]

### 1. TPACK Diagnosis

**Technology-Content Knowledge (TCK):**
[Does the teacher understand how this technology represents this content?]

**Technology-Pedagogy Knowledge (TPK):**
[Does the teacher know which pedagogical moves this technology supports or undermines?]

**Full TPACK:**
[Can the teacher make real-time decisions about technology use based on student learning?]

**TPACK strengths:**
[What the teacher brings from their background]

### 2. Technology-Content Analysis

**What this technology makes visible:**
[Content this technology represents well]

**What this technology obscures or distorts:**
[Where the technology's representation is inaccurate or misleading for this content]

**Reliability assessment (for AI tools):**
[How reliable are outputs for this domain, and what verification is needed]

### 3. Pedagogy-Technology Alignment

| Pedagogical move | Technology effect | Explanation |
|---|---|---|
| [Move 1] | Supports / Undermines / Neutral | [Why] |
| [Move 2] | Supports / Undermines / Neutral | [Why] |
| [Move 3] | Supports / Undermines / Neutral | [Why] |

**Critical recommendation:**
[The most important thing the teacher must understand about how this technology interacts with their pedagogy for this content]

### 4. AI-Specific Guidance

[If applicable]

**Reliability for this domain:** [What the AI does well and poorly]
**Verification requirements:** [What must be checked and how]
**Student critical evaluation:** [How to model this — specific first-lesson move]
**Autonomy-dependency risk:** [Assessment and mitigation]

### 5. Equity and Ethics

**Access equity:** [Differential access risks]
**Data privacy:** [Requirements for this age group and this technology]
**Content-specific ethics:** [Any issues specific to this content domain]

### 6. Dispositional TPACK

[The ongoing critical stance the teacher needs to maintain]

### 7. TPACK Development Plan

**Before using with students:**
1. [Priority action]
2. [Second priority]
3. [Third priority]

**During first use:**
- [What to observe]
- [Adjustments to be ready for]
- [Signals of help vs hindrance]

**After first cycle:**
- [How to evaluate]
- [What to refine]
- [When to consider abandoning]

**Self-check before returning output:** Verify that (a) the diagnosis is specific to this technology AND this content, not generic technology advice, (b) the technology-content analysis identifies specific representational strengths and distortions, (c) the pedagogy-technology alignment identifies at least one pedagogical move the technology undermines, (d) the AI-specific guidance (if applicable) addresses autonomy-dependency risk directly, (e) the equity and ethics section is specific to this technology and this learner stage, (f) the dispositional section describes a critical ongoing stance not a one-time assessment, and (g) the development plan is sequenced and actionable.
```

## 示例输出

当需要完整的一战历史中应用 AI 的 TPACK 示例（包含核验练习、第一节课示范以及两阶段任务设计）时，请阅读 [references/worked-examples.zh-CN.md](references/worked-examples.zh-CN.md)。

**精简节选——保留思考要求（一战历史）：**

**关键建议：**
Claude 必须被定位为学生在自己完成思考**之后**使用的工具，而非**之前**或**替代**思考。任务序列应当是：（1）学生在不使用 AI 的情况下接触一手史料并构建自己的论证；（2）随后学生使用 Claude 来挑战、拓展或精炼自己的论证——向它索取反证、替代解读或关于其推理的结构性反馈。这在富有成效地使用 AI 的同时保留了思考要求。如果顺序颠倒——学生先让 Claude 写一个论证然后再修改——历史思维根本就没有发生。

**数据隐私：**
14–15岁学生使用 Claude 涉及与第三方 AI 平台互动。要求：
- 学校必须拥有涵盖学生数据的机构使用条款，或者学生必须通过不保留对话数据的学校配发账号使用该工具。
- 不应要求学生向 AI 输入个人信息、情绪披露或身份识别细节。
- 应告知学校数据保护官（或同等职位）学生作品正由第三方 AI 系统处理。
- 在受 GDPR 或类似框架管辖的司法管辖区，该年龄组使用第三方 AI 工具可能需要通知家长或征得同意。教师在推进前应向学校核实。

---

## 已知局限

1. **TPACK 同时具有技术特异性与内容特异性。** 本技能针对“一项技术与一个内容领域整合”产出指导。一位横跨两门学科整合三种不同工具的教师，需要针对每一种组合分别运行本技能。不存在通用的 TPACK——只有针对特定交集的特定 TPACK。

2. **技术变化速度超过研究基础。** 关于教育中 AI 工具的实证证据目前较为单薄且变化迅速。本技能中针对 AI 的指导基于 PCK 研究的第一性原理推理及通用 AI 能力评估，而非基于特定 AI 工具在特定内容领域的重复实证研究。请将针对 AI 的指导视为知情专业判断，而非研究背书的确定性结论。

3. **本技能不评估技术本身——它评估教师关于如何使用它的知识。** 一种从根本上不适合某学习目标的技术，不会因为更好的 TPACK 而变得适合。如果技术-内容分析揭示该技术主动扭曲了内容或削弱了核心学习，正确回应可能是不使用它——再多的 TPACK 发展也无法改变这一结论。

4. **公平与伦理部分识别风险，但无法替你解决它们。** 数据隐私要求因司法管辖区而异且变化迅速。对于任何收集学生数据的技术，教师与学校必须核实是否符合适用法律——本技能提供核对清单提示，而非法律意见。

5. **TPACK 发展需要与真实学生一起实践。** 与 PCK 一样，TPACK 归根结底是通过用该技术教学、观察学生反应并不断精炼而建构起来的。本技能通过指明该问什么问题与该观察什么来加速发展，但无法替代实际用技术教学并觉察所发生之事的体验式学习。
