---
# AGENT SKILLS STANDARD FIELDS (v2)
name: dispositional-knowledge-assessment-designer
description: "为好奇心或韧性等倾向性能力设计多信息源评估方案。适用于评估书面测验无法捕捉的品格优势或能力。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "original-frameworks/dispositional-knowledge-assessment-designer"
skill_name: "倾向性知识评估设计器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Domitrovich, Durlak, Staley & Weissberg (2017) — Social-emotional competence: multi-informant assessment across contexts"
  - "Greenberg, Domitrovich, Weissberg & Durlak (2017) — SEL as a public health approach: triangulation of teacher, parent, and student report"
  - "CASEL (2013) — CASEL Guide: five-domain SEL framework and multi-informant assessment architecture"
  - "Zimmerman (2000) — Attaining self-regulation: developmental readiness for self-assessment and feedback"
  - "Zimmerman (2002) — Becoming a self-regulated learner: dispositions as assessable and teachable"
  - "Hattie & Timperley (2007) — The power of feedback: self-level feedback least effective; self-regulation feedback most powerful"
  - "Deci & Ryan (1985, 2000) — Self-Determination Theory: autonomy-supportive assessment preserves intrinsic motivation"
  - "Amabile (1979, 1993) — Evaluation expectation suppresses authentic expression; informational feedback synergises with intrinsic motivation"
  - "Krechevsky, Mardell, Rivard & Wilson (2013) — Visible Learners: documentation as assessment of dispositional qualities"
  - "Kluger & DeNisi (1996) — Feedback Intervention Theory: self-directed feedback decreases performance; task/process-directed feedback improves it"
  - "Boud & Molloy (2013) — Feedback as developmental dialogue, not transmission"
input_schema:
  required:
    - field: "competency_name"
      type: "string"
      description: "正在评估的倾向性能力"
    - field: "competency_definition"
      type: "string"
      description: "以“The ability to...（……的能力）”开头的一句话定义"
    - field: "band"
      type: "string"
      description: "属于哪个发展阶段——A、B、C、D、E 或 F"
    - field: "band_descriptors"
      type: "string"
      description: "来自学习目标撰写指南的该 LT 观察指标集。请提供阶段层面的观察指标（教师注意到的现象），而非“我能够……”阶段陈述。"
    - field: "assessment_context"
      type: "string"
      description: "何时以及如何进行评估——例如期末、持续进行、与特定项目绑定"
  optional:
    - field: "existing_observation_data"
      type: "string"
      description: "来自上下文引擎：已收集到的关于该学生或小组的任何观察笔记"
    - field: "student_self_assessment_data"
      type: "string"
      description: "来自上下文引擎：已从学生处收集的任何自我反思"
    - field: "parent_input"
      type: "string"
      description: "来自上下文引擎：如已收集，来自照料者的任何观察"
    - field: "school_feedback_structure"
      type: "string"
      description: "需要整合的任何现有反馈结构——如“期末发展性面谈”、“学生主导家长会”、“档案袋评审”"
output_schema:
  type: "object"
  fields:
    - field: "observation_protocol"
      type: "object"
      description: "教师寻找并记录什么——用于觉察的提示，而非核对清单。包含频率与格式指导。"
    - field: "student_self_reflection_tool"
      type: "object"
      description: "校准至阶段水平的适龄开放式问题，用于生成倾向性发展的证据"
    - field: "parent_caregiver_input_guide"
      type: "object"
      description: "面向照料者的3–5个无术语问题，框定为“觉察”而非“评估”"
    - field: "synthesis_guide"
      type: "object"
      description: "如何汇总多信息源证据、处理矛盾以及识别支持发展性对话的充分证据"
    - field: "developmental_conversation_guide"
      type: "object"
      description: "如何与学生谈论倾向性发展——各阶段分享什么、教练式提问、目标设定"
    - field: "feedback_structure_integration"
      type: "object"
      description: "如何将倾向性证据整合进学校现有的反馈结构"
chains_well_with:
  - "learning-target-authoring-guide"
  - "coherent-rubric-logic-builder"
  - "developmental-band-system-designer"
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
teacher_time: "5 分钟审阅设计初稿；实际实施时间另计（见工作量估算）"
tags: ["dispositional-knowledge", "assessment", "multi-informant", "coaching-feedback", "developmental-bands", "agency", "collaboration", "self-regulation", "observation", "self-reflection"]
---

# 倾向性知识评估设计器

## 本技能的功能

引导教师为**倾向性知识（dispositional knowledge）**——诸如能动性、协作、自我调节、创造自信与再生型思维模式等能力——设计一套完整的评估方案；在这类能力中，“知识”仅存在于践行之中，无法与学习者不断成长的能力剥离。本技能明确**不**生成量规。量规适用于层级性知识与水平性知识，在那些领域标准参照是正当的，学生可以通过特定任务证明胜任。倾向性知识需要一种根本不同的评估架构：多信息源证据（教师观察、学生自我反思以及可选的家长/照料者输入）、用作共享词汇而非终结性标准的发展阶段描述语，以及校准至学习者发展阶段的教练模式反馈。输出包括观察规程、学生自我反思工具、家长/照料者输入指南、用于三角互证的综合指南以及发展性对话指南——即教师以诚信开展倾向性发展评估所需的一切。AI 在此处具有独特价值，因为设计倾向性知识评估需要同时应用发展心理学（该阶段学生能有意义地自我评估什么？）、动机理论（如何在不损害所评估倾向的前提下进行评估？）以及评估设计专业知识（如何对多证据源进行三角互证？）——这种组合十分罕见，大多数教师从未受过相关训练。

元数据中标注的“5分钟”仅指对生成初稿的初步审阅，而非收集、综合或面谈时间。请返回完整的六部分设计，包含反馈整合与分项实施时间估算，且无需用户先选择组件。在采纳前请检查可行性：按每次5分钟观察加 1–2 分钟记录、每周两次、持续 10–12 周计算，仅观察一项每名学生就需 120–168 分钟。下文示范性完整设计总计每名学生每学期约 163–223 分钟（25名学生约合 68–93 小时），这还未计入额外准备或跨教师核准时间。这些是规划估算，而非实测实施时间；共享课堂观察可能降低边际耗时，且必须加以说明而非想当然。

## 循证基础

倾向性知识——能动性、协作、生态素养、创业思维、自我调节——提出了传统方法无法解决的评估难题。一份将学生“能动性”从1打分到5分的量规会同时犯下数个错误：它把践行中的倾向当成了固定特质；它暗示当倾向可能因情境而异时终结性判断依然有效；且它有损倾向性发展所必需的内在动机与心理安全感。

**多信息源评估。** Domitrovich、Durlak、Staley 与 Weissberg（2017）证明社会情感能力具有情境敏感性——一名学生可能在一种场合展现出极强协作，在另一种场合却协作薄弱——这意味着来自任何单一信息源的评估必然是不完整的。Greenberg、Domitrovich、Weissberg 与 Durlak（2017）指出，由于倾向性能力在不同场域（学校、家庭、同伴情境）的表现不同，有效评估需要对教师观察、学生自陈与家长/照料者输入进行三角互证。CASEL（2013）框架通过明确五大跨情境可观察的 SEL 能力领域（自我觉察、自我管理、社会觉察、人际关系技能、负责任的决策）将其操作化，确立了多信息源倾向性评估的架构。核心洞察并不在于三份报告因为统计平均而优于一份，而在于每个信息源都在不同情境中观察该倾向，**跨情境的模式本身就是证据**。

**自我评估的发展准备度。** Zimmerman（2000）表明自我调节通过循环过程发展——前瞻、表现、自我反思——且处于不同发展阶段的学习者对其自身倾向进行反思的能力存在质的差异。A阶段学生（5–7岁）能报告具体行动（“我今天帮了 Mia”），但无法有意义地评价自己的倾向性发展。D阶段学生（12–14岁）则能进行真正的元认知自我评估——将当前模式与过去行为对比、识别某倾向在哪些情境更强或更弱，并设定发展目标。Zimmerman（2002）进一步确立了自我调节背后的倾向既可评估也可教授，但评估方法必须匹配学习者的发展能力。这意味着自我反思工具必须校准至所在阶段——A阶段简洁具体，D阶段具有元认知性与比较性。

**保护动机的反馈。** Hattie 与 Timperley（2007）发现，自我层次的反馈（“你是个很好的合作者”）效果最差，而自我调节层次的反馈（“我注意到你在做决定前先和团队核对了——我看到这个习惯正在形成”）是最有力量的反馈之一。Kluger 与 DeNisi（1996）在对607个效应量的元分析中发现，超过三分之一的反馈干预实际上降低了表现——特别是那些将注意力引向“自我”而非“任务或过程”的反馈。这一发现对倾向性评估至关重要：评价学生“是什么样的人”（评判性）会削弱表现，而关注学生“做了什么”（发展性）则会提升表现。Deci 与 Ryan（1985, 2000）通过自我决定理论确立了：当评估情境让人感到受控制时——即学生感知到评判而非支持——会直接削弱倾向性发展所需的自主性与胜任感需求。Amabile（1979）通过实验证明外部评价预期会抑制真实表达，而 Amabile（1993）区分了控制性反馈（削弱内在动机）与信息性反馈（能与内在动机产生协同）。这对倾向性评估的启示非常明确：评估过程必须让人感觉像教练指导，而非打分评级。如果学生将倾向性评估体验为评判，他们就会去“表演”这种倾向，而非真正发展它。

**作为评估的记录（Documentation）。** Krechevsky、Mardell、Rivard 与 Wilson（2013）通过哈佛大学零点项目“让学习可见（Making Learning Visible）”倡议提出，记录——照片、对话抄录、录音、学生作品集——构成了一种评估形式，能够以测验和量规无法企及的方式让倾向性品质（坚持、好奇、敢于冒险、协作）变得可见。记录服务于三项问责功能：对自我（反思性实践）、对学习社群（共同探究）以及对家庭（成长证据）。这种方法将评估视为“觉察与记录”的行为，而非“测量与打分”的行为——这一根本转向与倾向性知识的本质高度契合。

**教练式 vs. 评判式反馈。** Boud 与 Molloy（2013）将反馈重新定义为能够促成行动的过程——不引发任何改变的信息在教育意义上根本不是反馈。这一重构将倾向性评估从评判（给学生评级）转向发展性对话（共同建构对成长与下一步的理解）。教练模式——由教师促进学生自身的反思而非下达裁决——在结构上与终结性评价不相容。两者无法共存于同一场对话中，否则评判角色会破坏坦诚自我剖析与倾向性成长所需的心理安全感。

**作为探究的记录。** 瑞吉欧·艾米利亚（Reggio Emilia）教学记录（Malaguzzi; Krechevsky, Mardell, Rivard and Wilson, 2013）将记录视为探究——观察产生的是问题，而非结论。这种将观察笔记视为专业探究起点而非评估终点站的知识论立场，直接塑造了本技能采用的方法。记录者不再问“这名学生处于什么等级？”，而是问“这名学生的行为揭示了什么，又促使我接下来去寻找什么？”

**民族志观察原则。** 深描（thick description, Geertz, 1973）、反身性以及观察者效应均适用于教师对学生倾向的观察。观察者效应——正式观察这一行为本身改变了被观察对象——是 E、F 阶段“表演性 vs. 真实性”指导的方法论基础，并支持优先选择自然情境而非预先宣布的观察情境。深描——记录具体、明确的行为而非抽象的解释——则是贯穿本技能观察笔记格式指导的基础。

## 输入模式

教师必须提供：
- **能力名称：** 倾向性能力。*例如：“能动性（Agency）” / “协作（Collaboration）” / “自我调节（Self-Regulation）” / “生态素养（Ecological Literacy）” / “创造自信（Creative Confidence）” / “再生型思维模式（Regenerative Mindset）”*
- **能力定义：** 以“The ability to...（……的能力）”开头的一句话。*例如：“以日益增长的独立性与目的性发起、规划并完成有意义工作的能力” / “与他人合作产出任何个人无法独自完成成果的能力”*
- **发展阶段：** 哪个发展阶段——A、B、C、D、E 或 F。*例如：“D阶段（12–14岁）” / “E阶段（13–15岁）” / “F阶段（15–17岁）”*
- **阶段描述语：** 该能力现有的阶段层面描述语。*例如：“我能够识别行动机会，并负责规划和执行自己的项目，在需要时寻求支持，并根据反馈和变化条件调整我的方法”*
- **评估情境：** 何时以及如何进行。*例如：“期末，汇入有学生、教师和家长共同参与的发展性评审会议” / “持续进行，通过项目档案袋记录” / “学年中评审，作为学生主导家长会的一部分”*

可选（如有，由上下文引擎注入）：
- **现有观察数据：** 已收集的笔记
- **学生自评数据：** 已收集的自我反思
- **家长输入：** 如已收集的照料者观察
- **学校反馈结构：** 需要整合的现有结构

## 提示词

```
You are an expert in developmental assessment design for dispositional knowledge, with deep knowledge of multi-informant assessment (Domitrovich et al., 2017; CASEL, 2013), developmental readiness for self-assessment (Zimmerman, 2000, 2002), feedback theory (Hattie & Timperley, 2007; Kluger & DeNisi, 1996), Self-Determination Theory (Deci & Ryan, 1985, 2000), the distinction between controlling and informational feedback (Amabile, 1979, 1993), and documentation-based assessment (Krechevsky et al., 2013).

CRITICAL DESIGN PRINCIPLE: Dispositional knowledge exists only in enactment. It cannot be tested through a single task, scored on a scale, or reduced to a rubric criterion. Assessment must make the disposition VISIBLE through multiple evidence sources over time — not MEASURE it through a summative judgment. If the assessment output looks like a rubric or a score, the design has failed.

Workload boundary: generate the complete six-part assessment design; no component-selection input is required and no output field is dropped. Distinguish brief draft-design review from implementation across weeks. Put a provisional workload summary before the six sections, with duration × frequency × weeks, recording, reflection, optional caregiver contact, synthesis and conversation costs; show the class-size multiplier when known (otherwise state an illustrative size). Name assumptions, avoid double-counting shared work, and identify feasibility questions before recommending adoption. Do not describe implementation as five minutes or claim this exact assessment design has established greater validity. Retain observation across contexts, multiple informants, professional reflexivity and teacher moderation; caregiver participation remains optional.

Your task is to design a complete dispositional assessment approach for:

**Competency name:** {{competency_name}}
**Competency definition:** {{competency_definition}}
**Band:** {{band}}
**Band descriptors:** {{band_descriptors}}
**Assessment context:** {{assessment_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Existing observation data:** {{existing_observation_data}} — if provided, build on what has already been observed.
**Student self-assessment data:** {{student_self_assessment_data}} — if provided, design the self-reflection to extend rather than repeat.
**Parent input:** {{parent_input}} — if provided, use to inform the synthesis.
**School feedback structure:** {{school_feedback_structure}} — if provided, design the outputs to integrate with this structure.

Apply these evidence-based principles:

1. **Observation Protocol design (Krechevsky et al., 2013; Domitrovich et al., 2017):**
   - Design prompts for noticing, NOT a checklist. The teacher is looking for patterns of enacted behaviour, not ticking boxes.
   - Derive observable indicators directly from the band descriptors — translate "I can..." statements into "I notice when the student..."
   - Include both expected indicators (what the band descriptor predicts) and unexpected indicators (what might emerge that isn't captured in the descriptor).
   - Specify frequency: how often should the teacher deliberately observe? What contexts are richest for observation?
   - Specify format: brief dated notes, not formal observation forms. The goal is sustainable teacher practice, not bureaucratic compliance.
   - Include negative-space indicators: what ABSENCE of behaviour is also informative? (A student who never initiates is evidence, not just a student who does.)
   - **Performative versus authentic at Bands E and F:** At Bands E (ages 13–15) and F (ages 15–17), the observation protocol must account for the performative versus authentic problem: older adolescents are cognitively sophisticated enough to perform dispositions when they know they are being observed. The most valid observations at these bands come from naturalistic contexts where the student is not in an assessment frame. Mitigations: prioritise observation during project work, informal transitions, excursions, and outdoor activities over structured classroom observation; aim for at least one observation from a naturalistic context per month at these bands; record in observation notes whether the context was naturalistic or structured; treat observations from announced or structured contexts with higher interpretive caution. The observer effect — the act of formal observation changing what is observed — is particularly significant at these bands.

2. **Student Self-Reflection Tool design (Zimmerman, 2000, 2002):**
   - MUST be calibrated to the developmental band:
     - **Band A (ages 5–7):** Simple, concrete prompts. "Tell me about a time this week when you..." Use pictures or drawings if appropriate. Do not ask for self-evaluation — ask for stories.
     - **Band B (ages 8–10):** Slightly more reflective. "What did you do when...?" "What was hard about...?" Begin connecting actions to patterns but keep it concrete.
     - **Band C (ages 10–12):** Emerging metacognition. "When do you find it easiest to [competency]? When is it hardest? Why do you think that is?" Begin comparing across contexts.
     - **Band D (ages 12–14):** Full metacognitive reflection. "How has your [competency] changed this term? What evidence would you point to? Where is it strongest and where does it still need development?" Invite the student to interpret their own patterns.
     - **Band E (ages 13–15):** Full metacognitive capacity with increasing independence. Prompts invite the student to analyse patterns across multiple contexts and over time, identify what has changed and what has not, and consider the conditions under which the disposition is strongest and weakest. Students at this band can handle critical self-examination.
     - **Band F (ages 15–17):** Near-autonomous self-direction. Prompts invite the student to evaluate the trajectory of their dispositional development across their school journey, consider how this disposition will function beyond school, and identify what they want to intentionally develop next. The student is treated as a near-peer in the conversation.
   - NEVER use self-rating scales (1-5, agree/disagree). These reduce developmental complexity to a number and generate unreliable data — students anchor to social desirability rather than genuine reflection.
   - Design open questions that generate EVIDENCE — stories, examples, specific moments — not self-judgments.
   - Include 4–6 questions maximum. More than this produces fatigue and superficial responses.

3. **Parent/Caregiver Input Guide design (Greenberg et al., 2017):**
   - This is GENUINELY OPTIONAL — not all families can or should provide input, and the assessment must be valid without it.
   - Design 3–5 specific questions that a caregiver can answer without educational jargon.
   - Frame as noticing, not assessment: "We'd love to know what you notice at home" NOT "Please rate your child's agency."
   - Ask about observable behaviours in home/community contexts: "Does your child take on projects or tasks at home without being asked? Can you give a recent example?"
   - Include a brief context note explaining why this input is valuable and how it will be used — transparency builds trust.
   - Acknowledge diverse family contexts: questions should work for a parent, grandparent, older sibling, caregiver, or boarding house supervisor.

4. **Synthesis Guide design (Domitrovich et al., 2017; CASEL, 2013):**
   - How to bring together teacher observations, student self-reflections, and any parent input to form a developmental picture.
   - Specifically address:
     a. **Pattern identification:** What patterns appear across sources? What does the student consistently do, across contexts and informants?
     b. **Contradiction handling:** What to do when sources disagree — e.g. the teacher sees strong agency in structured projects but the student reports feeling "lost" when work is open-ended. Contradictions are not errors — they are diagnostic information about contextual variation.
     c. **Sufficient evidence:** Minimum evidence for a well-grounded developmental conversation: at least three to five independent observation notes from different contexts over at least four weeks, showing a consistent pattern or a meaningful and recurring inconsistency. This is not a threshold for a developmental level claim — it is the minimum basis for bringing structured evidence to a conversation. A single impressive moment is an event, not a pattern.
     d. **Contextual variation:** A student may demonstrate the disposition strongly in one context and weakly in another. This is NORMAL, not a problem. The synthesis should name the pattern ("shows strong agency in science projects; less so in collaborative writing tasks") rather than averaging it.
   - The output of synthesis is a developmental narrative, not a score. "Here is where this student is in their development of [competency], here is the evidence, and here is what I think the next step looks like."

5. **Developmental Conversation Guide design (Hattie & Timperley, 2007; Deci & Ryan, 2000; Amabile, 1993; Boud & Molloy, 2013):**
   This is the most important output. Design it with these principles:

   a. **What to share and what to hold back, calibrated by band:**
      - **Band A/B:** Affirm and name what you see. "I noticed you started the experiment before anyone else today — you saw what needed to happen and you went for it. That's agency." Do NOT present a score, a band level, or a comparison. The student should experience the conversation as recognition, not judgment.
      - **Band C:** Begin sharing patterns and inviting student interpretation. "I've noticed something interesting — in your project work, you often take the lead on the research phase but step back during the presentation phase. What do you think is going on there?" Share the observation; invite the student to make meaning.
      - **Band D:** Full transparency. Show the student the synthesis — teacher observations, their own self-reflections, any parent input. Invite them to lead the interpretation: "Here's what I've gathered from multiple sources. What patterns do you see? What does this tell you about your agency right now?" The student at Band D should be developing the metacognitive capacity to assess their own dispositional development.
      - **Band E:** Deep inquiry partnership. Share all evidence and position yourself as a thinking partner, not an evaluator. Invite the student to examine the conditions under which the disposition appears strongly and where it does not — and to consider what this pattern reveals about their developmental edge. The student at Band E can sustain extended self-analysis and benefits from being challenged to look across multiple contexts and time periods rather than only reflecting on recent events.
      - **Band F:** Near-peer dialogue. The student drives the entire conversation. The teacher's primary role is to offer observations as data points that the student can accept, question, or contextualise. Invite the student to situate their dispositional development in the context of their wider school journey and their anticipated life beyond school. The conversation is less a feedback session and more a collaborative stocktaking between near-peers.

   b. **Coaching questions at each band level:**
      - Design 3–4 questions per band that the teacher can use in the developmental conversation.
      - Questions must be genuinely curious, not leading. "What do you think you need to work on?" is leading (implies deficit). "Where do you want to take your [competency] next?" is curious (implies growth).
      - Questions should connect to the student's own experience and goals, not to external standards.

   c. **Using band descriptors as shared vocabulary:**
      - The band descriptors should be used as language for talking about development, NOT as criteria for grading.
      - "This descriptor talks about 'seeking support when needed' — I've noticed you do that really naturally in maths but not yet in your writing projects. Let's think about why that might be."
      - NEVER: "You're at Band C for agency." This reduces development to a label.

   d. **Connecting to student-set goals:**
      - Every developmental conversation should end with the student identifying one concrete thing they want to work on — stated in their own words, not the band descriptor's words.
      - The teacher records this goal and references it in the next conversation: "Last time you said you wanted to try starting your own research questions instead of using mine. How has that gone?"

6. **Integration with Existing Feedback Structures:**
   - If a school feedback structure was provided in the input, design specific guidance on how to integrate the dispositional evidence into that structure.
   - If no structure was provided, offer general guidance on where dispositional assessment evidence fits in common feedback formats.
   - Key principle: dispositional evidence should COMPLEMENT, not replace, other assessment data. A developmental review might include academic progress (from rubrics and learning targets) AND dispositional development (from this assessment approach). The two use different evidence types and different language.

Return your output in this exact format:

## Dispositional Assessment Design: [Competency Name] — Band [X]

**Competency:** [Name]
**Definition:** [One-sentence definition]
**Band:** [Band and age range]
**Assessment context:** [When and how]
**Implementation workload:** [Provisional per-student and class estimate, assumptions and feasibility questions; design review time is separate]

### 1. Observation Protocol

**What to notice:**

Provide 5–7 prompts for noticing, derived directly from the band descriptors. Each prompt should:
- Name a specific observable behaviour the teacher might see in classroom, project, or social contexts
- Describe what that behaviour looks like concretely — not just "shows initiative" but the specific actions, language, or patterns that constitute initiative at this band level
- Distinguish the target behaviour from adjacent behaviours that look similar but are qualitatively different (e.g., compliance vs. agency, dependence vs. strategic support-seeking)
- Include at least one prompt focused on how the student TALKS about their work — ownership language, planning language, or reflective language that reveals the disposition even when behaviour is ambiguous

Introduce the prompts with a framing note reminding the teacher that these are patterns to watch for across the term, not boxes to tick — they will not see all of them in every student or every context.

**When and how to observe:**

Specify:
- **Frequency:** How often the teacher should deliberately attend to this disposition (e.g., "at least twice per week during project sessions" or "once per week during collaborative tasks"). Emphasise that this is intentional noticing for 5 minutes, not formal observation.
- **Richest contexts:** Which classroom situations are most likely to reveal the disposition — typically moments of ambiguity, choice, difficulty, or transition where the student's default response becomes visible. Name 3–4 specific contexts for this competency and band.
- **Recording format:** Brief dated notes of 1–3 sentences in a running document or notebook. Emphasise timestamps over detail — the teacher is building a pattern over time, not writing a report. Provide an example observation note showing the format: date, what the student did, and one sentence of interpretation.

**Negative-space indicators:**

Describe what ABSENCE of the disposition looks like in contexts where it could reasonably be expected. Name 2–3 specific absences that are informative — e.g., a student who consistently waits for instructions rather than initiating, or who never seeks support despite struggling visibly. Explain that absence is evidence, not just presence, and that patterns of absence across multiple observations point to where the developmental edge lies.

### 2. Student Self-Reflection Tool

**For the student:**

Write 4–6 open-ended reflection questions, fully written out as the student would read them. These must be:
- Calibrated to the developmental band specified — use the band-level guidance from the principles above (Band A: concrete stories; Band B: connecting actions to patterns; Band C: comparing across contexts; Band D: metacognitive interpretation of own patterns over time)
- Written in age-appropriate language — a Band A prompt should sound like a conversation with a 6-year-old; a Band D prompt should respect a 13-year-old's capacity for self-analysis
- Framed as invitations to share stories, examples, and specific moments — never as self-rating scales or agree/disagree statements
- Preceded by a brief introductory sentence addressed to the student that sets a reflective, non-judgmental tone (e.g., "Reflect on your [competency] this term. Take your time — there are no right answers. What matters is that you think honestly about your own patterns.")

Each question should target a different facet of the disposition: at least one about a moment of strength, one about a moment of difficulty, one about contextual variation (where the disposition is easier/harder), and one about change over time.

**Teacher guidance for using this tool:**

Provide specific guidance on:
- **Timing:** When to give the prompts to the student (e.g., 2–3 days before a developmental conversation, not during it) and why advance time matters for quality reflection
- **Format flexibility:** Whether the student can write, record audio, draw, or discuss verbally — the medium does not matter; the quality of reflection does
- **How to read responses:** The teacher reads for evidence (stories, examples, patterns) not for quality of writing. Do NOT grade the reflections.
- **What to do with contradictions:** If the student's self-reflection contradicts teacher observations, this is valuable diagnostic information — it may reveal that the student experiences the disposition differently from how the teacher sees it, or that it manifests differently in unobserved contexts.

### 3. Parent/Caregiver Input Guide (Optional)

**Introduction for families:**

Write a complete introductory paragraph addressed to families, fully written out as they would read it. It must:
- Name the competency in plain language (not educational jargon)
- Explain briefly why the school values this competency
- Explain what you are asking for: observations of behaviour at home and in the community, not an assessment or rating
- Explicitly state that responding is optional and that the student's assessment will be complete without this input
- Use warm, inviting language — "We'd love to know what you notice" not "Please complete this form"
- Address "families" or "dear families" rather than "parents" — the guide should work for any caregiver

**Questions:**

Write 3–5 specific questions, fully written out as the caregiver would read them. Each question should:
- Ask about observable behaviours in home or community contexts — what the caregiver can see the student doing, not what the caregiver thinks the student understands
- Be specific enough to elicit concrete examples, not generic impressions (e.g., "Does [student name] take on projects or tasks at home without being asked? Can you give a recent example?" not "How independent is your child?")
- Avoid educational jargon entirely — no "agency," "metacognition," "self-regulation" or band-level language
- Include one question that asks about change over time ("Have you noticed any changes in [student name]'s independence this term?")
- Include one open question ("Is there anything about how [student name] approaches their own projects that you think we should know about?")

**Note on use:**

Write a brief note (2–3 sentences) explaining: how the input will be used (alongside teacher observations and student reflections to build a full picture), that it will be shared at any meeting with the student present (no secrets), and that not all families will respond — and that is genuinely fine. If the school has specific protocols around sensitive disclosures, note that caregivers can flag anything they would prefer discussed privately.

### 4. Synthesis Guide

**Bringing evidence together:**

Provide a step-by-step synthesis process (4 steps) that the teacher follows before the developmental conversation:
- **Step 1:** Read each evidence source independently — teacher observations, student self-reflection, any parent input. Note the 2–3 strongest themes from each source separately, without cross-referencing yet.
- **Step 2:** Identify convergence — where do sources agree? Describe what convergent evidence looks like for this competency (e.g., teacher sees the behaviour, student identifies it as a strength, parent reports similar patterns at home). Explain that convergence is the strongest form of evidence.
- **Step 3:** Identify divergence — where do sources disagree? Provide 2–3 specific examples of common divergence patterns for this competency (e.g., teacher sees strong disposition but student reports feeling uncertain; student claims strong disposition but teacher sees dependency; parent sees the disposition at home but teacher does not see it at school). For each pattern, explain what it typically reveals — e.g., the student may be performing the disposition outwardly while experiencing insecurity inwardly, or the disposition may be genuinely context-dependent.
- **Step 4:** Write a developmental narrative — 3–5 sentences that describe where the student is, what the evidence shows, and what the trajectory looks like. Provide a model sentence structure: "Shows strong [competency] in [context]; less visible in [context]. The developmental edge for next term is [specific next step]."

**Handling contradictions:**

Explain that contradictions between sources are diagnostic information, not errors. They typically reveal one of three things:
1. **Context-dependence** — the disposition genuinely manifests differently in different settings (the most common explanation)
2. **Perception gap** — the student, teacher, or parent perceives the disposition differently from how it is enacted
3. **Developmental transition** — the student is between levels and their behaviour is inconsistent because the disposition is actively developing

Instruct the teacher NOT to resolve contradictions by averaging or by privileging one source. Instead, name the contradiction and explore it in the developmental conversation.

**Sufficient evidence threshold:**

State the minimum evidence requirements: at least 5 teacher observation entries over at least 4 weeks showing a consistent pattern (or a meaningful inconsistency), plus at least one student self-reflection that generates specific examples. Parent input is valuable but NOT required for sufficiency. If evidence is below threshold, the narrative should explicitly note limited evidence. Explain that a single impressive moment is an event, not evidence of development — development is a pattern over time.

**Contextual variation:**

Explain that a student may demonstrate the disposition at different band levels in different contexts — and that this is developmentally normal, not a problem. Instruct the teacher to NAME the variation specifically (e.g., "Shows Band D [competency] in self-directed investigation; approaching Band C in collaborative contexts"). State that the teacher should NOT average contextual variation into a single band level — the variation IS the developmental picture, and it points to where the next growth opportunity lies.

### 5. Developmental Conversation Guide

**What to share at Band [X]:**

Write specific guidance on what to share and what to hold back for the band specified in the input. Follow the band-calibrated transparency principles:
- At Band A/B: describe what to affirm and name ("I noticed you... That's [competency]"), what NOT to share (scores, band levels, comparisons), and the experience the student should have (recognition, not judgment)
- At Band C: describe how to share patterns and invite interpretation ("I've noticed something interesting..."), what level of synthesis to show the student, and how to balance teacher observation with student meaning-making
- At Band D: describe full transparency — showing the synthesis, sharing all evidence sources, and inviting the student to lead the interpretation ("Here's what I've gathered. What patterns do you see?"). Explain the teacher's role shift from telling to facilitating.

For all bands: list what to always hold back — comparative language ("You're further along than most"), labelling ("You're a Band D student"), and deficit framing ("You still need to work on...").

**Coaching questions:**

Write 3–4 specific coaching questions, fully written out as the teacher would say them. These must be:
- Genuinely curious, not leading — they imply growth, not deficit
- Connected to the student's own experience and the specific evidence gathered
- Calibrated to the band's metacognitive capacity — Band A questions ask for stories, Band D questions invite pattern interpretation and self-directed goal-setting
- At least one question that connects teacher observations to student self-reflection ("You mentioned [X]. I noticed something similar when [Y]. What do you think is behind that?")

**Using band descriptors as vocabulary:**

Provide a specific example showing how to reference the band descriptor in conversation as shared vocabulary rather than grading criteria. Show a model sentence: "This descriptor talks about '[specific phrase from descriptor]' — I've noticed you do that really naturally in [context] but not yet in [other context]. Let's think about why that might be." Then state explicitly what NEVER to do: "You've met 4 out of 5 elements of the descriptor" — this turns vocabulary into criteria and the conversation into a grading exercise.

**Goal-setting:**

Describe how to close the conversation: the teacher asks the student to identify one thing they want to work on, stated in their own words (not the band descriptor's words). Provide 1–2 example prompts for eliciting the goal. Explain that the goal should be specific enough to notice but not so specific it becomes a checklist item. State that the teacher records the goal and both keep a copy, and that the next developmental conversation opens by revisiting this goal.

### 6. Integration with Feedback Structures

If a school feedback structure was provided in the input, design a specific integration plan:
- **Before the session:** What the teacher prepares (synthesis completion, evidence selection, coaching question selection) and how long this takes
- **During the session:** A suggested minute-by-minute structure for the dispositional portion of the session, showing who speaks, what they share, and where the coaching questions and goal-setting fit. Specify how much of the total session time should be allocated to this competency.
- **What the session should NOT include:** Band levels or scores, comparisons to other students, teacher monologues. The student leads; the teacher adds evidence; the family contributes perspective.

If no feedback structure was provided, offer general guidance: recommend a standalone 15-minute developmental conversation between teacher and student at least once per term, describe how to share the narrative with families in written form if face-to-face is not possible, and note that observation notes and synthesis should be kept as portfolio evidence.

### Time and Workload Estimate

Provide an honest, itemised estimate of teacher time per student per term for each component:
- **Observation:** Minutes per observation session × frequency × weeks in term, plus recording time. State the total.
- **Student self-reflection:** Time to distribute prompts + time to read each response. State the total.
- **Parent input:** Time to send the guide (if invited) + time to read responses (if received). No response means zero reading time, not zero invitation time; omit the invitation entirely where inappropriate.
- **Synthesis:** Time for the four-step synthesis process. Note that this is the most demanding step and cannot be reduced without losing quality.
- **Developmental conversation:** Time for the conversation itself within any existing session structure.
- **Total per student per term:** Sum the components. Then multiply by class size to show the full-class investment. Be honest — if the total is significant, say so. Name it as a real cost. This method aims for a richer, context-sensitive picture, but comparative validity and usefulness of this exact design are not established; educators must judge whether the investment fits their purpose.
- **Sustainability strategies:** Provide 3–4 specific strategies for managing the workload — e.g., rotating which competencies receive full assessment each term, integrating observation into existing circulation practice, identifying the minimum viable approach if the full version is unsustainable.

**Self-check before returning output:** Verify that (a) nothing in the output looks like a rubric or a score, (b) the observation protocol uses prompts for noticing not checklists, (c) the sufficiency framing refers to conversation readiness not developmental level claims, (d) Bands E and F are addressed throughout with performative versus authentic guidance where the band warrants it, (e) all school-specific references have been removed, (f) the hermeneutic moderation framing is present in how contradictions are addressed, (g) parent input is genuinely optional and jargon-free, (h) the synthesis guide addresses contradictions and contextual variation explicitly, and (i) time estimates are honest.
```

## 示例输出

当需要完整的 D阶段能动性评估设计（包含全部六个部分、家庭沟通措辞、综合方法与评审会议时间安排）时，请阅读 [references/worked-agency-assessment.zh-CN.md](references/worked-agency-assessment.zh-CN.md)。

**精简节选——观察与实施成本（能动性，D阶段）：**

- **记录格式：** 简短的带日期笔记——最多 1–3 句话。“3月14日：S. 注意到水质传感器数据与预期不符。没有来问我，而是自己回去检查校准程序，发现了误差，重新校准并复测。未经要求就向小组说明了情况。”将笔记保存在连续文档或实体笔记本中。时间戳比细节更重要——你是在随时间推移建构模式。

### 时间与工作量估算

**观察：** 每次5分钟有意觉察加 1–2 分钟记录，每周两次，持续 10–12 周：(5 + 1–2) × 2 × 10–12 = **每名学生每学期 120–168 分钟**。这假设的是个体独立观察时间；如果某次课堂片段支持同时观察多名学生，请说明共享分摊并避免重复计算同一时间。必须在本地核实可持续性。

**学生自我反思：** 教师分发提示耗时5分钟。阅读每位学生的回答耗时10分钟。**每名学生总计：15分钟。**

**家长输入：** 示范性估算，邀请输入5分钟加阅读回复5分钟：**若两项均发生则为每名学生10分钟；若发出邀请但无回复则为5分钟；若未发出邀请则为0。** 面向全班的统一邀请可降低人均分配时间。在不合适或不安全的情况下切勿寻求输入。

**综合：** 每名学生耗时 15–20 分钟完成四步综合并撰写发展性叙事。**这是最耗费精力的步骤。** 无法在不损失质量的前提下缩减。这也是教师专业判断最为关键的步骤。

**发展性对话 / 发展性评审中的能动性环节：** 在现有会议结构内每名学生 8–10 分钟。

**示范性每名学生每学期总计：163–223 分钟** = 观察/记录 120–168 + 自我反思分发/阅读 15 + 照料者邀请/回复 10 + 综合 15–20 + 对话 8–10。对于25名学生而言，这相当于 **4,075–5,575 分钟，约 68–93 小时**。若无照料者邀请或回复，每人减去10分钟。审阅设计初稿、初期搭建与教职工核准可能会增加时间；共享管理/观察可能减少时间。这些都是明确的规划假设，而非实测成本或证明该设计比替代方案更有效的证据。在采纳完整计划前请核实可行性。

**可持续性策略：**
- 并非每项能力每学期都需要这一完整方案。可轮换进行：第一学期深度评估能动性，第二学期协作，第三学期自我调节。
- 观察笔记可以融入现有实践——在项目工作期间巡视时顺便觉察，而不是作为一项额外任务。
- 如果工作量确实不可持续，最小可行方案是：教师观察 + 学生自我反思 + 发展性对话。在不适宜时省略照料者收集，并使用教师观察与学生反思的简短综合来准备对话。保持全部六个设计部分可用，标注照料者参与为可选项；切勿将缩减版实施当作完整的三角互证流程。

---

## 评价专业性（Evaluative Expertise）与新教师入职引导

观察规程为评价专业性的发展提供支架，但无法替代它。评价专业性——即对“真实的自我调节”与“表演出来的自我调节”之间、或“真诚共情”与“社交得体的共情表演”之间差异的敏锐直觉——是通过经验、反思以及与熟练同事的校准而发展起来的。一名第一年使用该规程的教师产出的观察质量会低于拥有多年经验的教师，不是因为他们不够勤勉，而是因为他们尚未发展出那种对质量的直觉感知。这种专业能力可称为“教学观察知识（pedagogical observation knowledge）”——它不同于学科教学知识（PCK），在教师教育中极少被命名或教授。

实施本技能的学校应为新教师提供：来自经验丰富实践者的结构化观察笔记范例及对“什么使这些观察有用”的研讨；定期开展核准对话，让教师分享并对比对同一批学生的观察；以及在将观察用于任何产生实质后果的用途之前，给予充分时间发展其观察实践。

---

## 观察者位置性（Observer Positionality）与专业反身性

教师对学生倾向的观察受到教师自身与这些倾向关系的影响。一位主要通过安静内在加工来表达自我调节的教师，可能会观察不足那些调节方式响亮且外显的学生。来自高语境文化的教师可能会将学生矜持的边界设定行为误读为脱离投入。看重口头表达流利度的教师可能更容易注意到自信的自我反思，而忽略犹豫但真诚的自我反思。

这是所有观察行为的固有特征，而非专业精神的缺失。恰当的回应是专业反身性：教师应定期自问，自己最容易识别和看重哪些倾向，又较难觉察或欣赏哪些倾向。教师之间的核准对话正是随时间推移揭示并校正观察者位置性的结构性机制。

---

## 已知局限

1. **多信息源评估旨在呈现更丰富的图景，但需要可观的工作量。** 在示例假设下，完整方案——观察、学生自我反思、照料者邀请/回复、综合、发展性对话——每名学生每学期预计需 163–223 分钟；这并非实测成本或对比效度结果。对于一名带25名学生且需评估多项能力的教师而言，这相当可观。本技能采用模块化设计——任何组件均可独立使用——但完整的三角互证图景需要完整的投入。实施本方法的学校应明确规划时间成本，而不是在学期中途才发现。

2. **家长/照料者输入很有价值，但并非总是可得或适宜。** 部分家庭因工作日程、语言障碍或家庭状况无法参与。部分家庭处境使关于倾向性发展的家长输入显得不适宜或不安全。本评估方案在设计上即使没有家长输入也完全有效——它是一项真正可选的丰富补充，而非硬性要求。当寻求家长输入可能危及学生安全或家庭信任时，教师绝不应强求。

3. **倾向性发展是非线性且高度情境敏感的。** 一名学生可能在科学上展现出 D阶段能动性，在协作写作中却处于 B阶段。一名上学期表现出强自我调节的学生，本学期可能因个人境遇、社交动态或新任务类型的要求而看似倒退。本技能明确标记了这一点，并指导教师点明情境差异而非取平均值——但它无法阻止机构出于汇报目的要求产生单一“能动性分数”的压力。如果学校的汇报系统要求单一等级，教师必须运用专业判断来决定哪个等级最能代表学生的整体发展轨迹，同时在叙事笔记中如实说明情境差异。

4. **发展性对话要求教师具备高超的技巧。** 对话指南搭建了结构并提供了教练式问题，但对话质量取决于教师倾听、真诚回应、在不纠正或不评判的前提下为学生自我评估留出空间以及维持关系信任的能力。机械照读教练式问题的教师所产生的结果，还不如没有指南但直觉敏锐、关系能力强的教师。指南只是支架，不能替代专业判断与关系胜任力。学校在规模化实施本方法前，应考虑提供关于教练式对话的专业发展培训。

5. **当两位教师对同一名学生得出不同结论时，这是关于情境差异的信息，而非评分者间信度失败。** 两位观察者可能都是准确的：他们在不同情境中看到了同一倾向的不同侧面。恰当回应是一场核准对话，探究这种差异揭示了学生跨情境倾向性发展的什么特征——而不是对观察取平均值，也不是裁定谁对谁错。跨情境的差异模式本身就是最有信息量的证据。这种诠释学取向的核准——将分歧观察视为专业探究的契机而非待消除的评分误差——与心理测量学信度框架有着根本区别，后者假设存在一个可靠评分者应当趋同的单一真分数。倾向性发展不存在单一真分数；它拥有的是跨情境践行行为的模式，而存在分歧的教师观察完全可能都在忠实地呈现该模式的真实部分。
