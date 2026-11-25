---
# AGENT SKILLS STANDARD FIELDS (v2)
name: pedagogical-content-knowledge-developer
description: "通过揭示常见学生误解与有效表征方式，发展特定主题的学科教学知识（PCK）。适用于准备教授不熟悉的内容或改进高难度主题的教学。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/pedagogical-content-knowledge-developer"
skill_name: "学科教学知识（PCK）发展器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Shulman (1986) — Those who understand: Knowledge growth in teaching — original PCK framework"
  - "Shulman (1987) — Knowledge and teaching: Foundations of the new reform"
  - "Ball, Thames & Phelps (2008) — Content knowledge for teaching: What makes it special?"
  - "Magnusson, Krajcik & Borko (1999) — Nature, sources and development of PCK for science teaching"
  - "Cochran, DeRuiter & King (1993) — Pedagogical content knowing: An integrative model"
  - "Hattie (2009) — Visible Learning: teacher content knowledge and PCK as distinct predictors"
  - "Depaepe, Verschaffel & Kelchtermans (2013) — Pedagogical content knowledge: A systematic review"
  - "Bernstein (1999) — Vertical and horizontal discourse: knowledge structures and recontextualisation"
  - "Willingham (2009) — Why Don't Students Like School: content knowledge as prerequisite for teaching"
  - "Timperley et al. (2007) — Teacher Professional Learning and Development: content-specific PD effectiveness"
input_schema:
  required:
    - field: "teaching_context"
      type: "string"
      description: "教师即将教授的内容：学科、主题、单元或项目"
    - field: "learner_stage"
      type: "string"
      description: "年龄范围或年级"
    - field: "teacher_background"
      type: "string"
      description: "教师的学科培训背景及教授该主题的经验简述"
  optional:
    - field: "known_student_misconceptions"
      type: "string"
      description: "教师已知的任何学生误解"
    - field: "curriculum_framework"
      type: "string"
      description: "学校正在使用的课程或能力框架"
    - field: "knowledge_architecture_output"
      type: "string"
      description: "如已运行，来自 curriculum-knowledge-architecture-designer 的产出"
output_schema:
  type: "object"
  fields:
    - field: "pck_diagnosis"
      type: "object"
      description: "基于教师背景评估其在该特定主题上可能的 PCK 优势与缺口；识别三种知识类型（层级性、水平性、倾向性）中哪一项最薄弱"
    - field: "content_knowledge_foundations"
      type: "object"
      description: "教师授课前必须掌握稳固的层级性知识：核心概念、前置链条以及该水平最常被误解的内容"
    - field: "common_student_misconceptions"
      type: "object"
      description: "该学习阶段学生关于此主题文献记录最充分的误解，附带每种误解形成的原因及转变所需的条件"
    - field: "pedagogical_representations"
      type: "object"
      description: "教授该内容最有效的表征、类比、模型与示例：什么有效、什么会误导及原因；按知识类型组织"
    - field: "disciplinary_thinking_standards"
      type: "object"
      description: "该领域的专家思维长什么样以及如何向学生显性化；PCK 的水平知识维度"
    - field: "developmental_action_plan"
      type: "object"
      description: "教师发展自身 PCK 的序列化计划：先读什么或学什么、观察什么、练习什么，以及如何判断自身 PCK 何时达到充分"
chains_well_with:
  - "curriculum-knowledge-architecture-designer"
  - "critical-thinking-task-designer"
  - "lesson-observation-protocol-designer"
  - "reflective-practice-prompt-generator"
  - "technological-pedagogical-content-knowledge-developer"
teacher_time: "10 分钟"
tags: ["PCK", "pedagogical-content-knowledge", "teacher-development", "content-knowledge", "misconceptions", "Shulman", "professional-learning", "knowledge-contingent"]
---

# 学科教学知识（PCK）发展器

## 本技能的功能

接收教师即将教授内容的描述及其个人背景，诊断其在该特定主题上可能存在的学科教学知识（PCK）缺口，并生成一份在开课前弥补这些缺口的发展计划。Shulman（1986）的奠基性洞察在于：懂一门学科与懂得如何教这门学科是两种真正不同的能力——一位从未教过九岁孩子分数的数学家，并不会自动知道哪些表征有效、会形成哪些误解，或者学生在理解下一个概念前必须跨越哪道概念门槛。本技能让这些缺口变得可见且可操作。它涵盖全部三个知识维度：教师必须掌握稳固的层级性内容知识、定义该领域专家推理的水平性思维框架，以及在课堂上实时觉察并回应学生理解的倾向性取向。产出同时包含诊断与发展计划——不仅指出缺失什么，还排定教师应对此采取行动的顺序。当教师跨出自身主修专长授课、教授颇具野心的新项目（再生型项目式学习、跨学科单元、幸福感科学），或转向需要重新校准既有 PCK 的新年龄段时，本技能尤为宝贵。AI 在此处具有独特价值，因为绘制 PCK 缺口需要同时通晓内容领域、学生误解研究、教学表征证据以及不同方法的适龄性——这种组合往往需要多年经验积累，且大多数职前教师培训仅能部分提供。

## 循证基础

Shulman（1986, 1987）将 PCK 从一般内容知识与一般教学法知识中区分出来，确立为第三类独特知识：唯独教师才拥有的内容与教学法的融合。一位化学家与一位化学教师可能拥有完全相同的化学知识，但教师还知道哪些类比对14岁学生理解离子键有效、哪些关于原子的误解几乎普遍存在，以及哪些表征误导多于启发。这就是 PCK——让内容变得可教的知识。Shulman 将其界定为“这些观念最有用的表征形式，最有力的类比、图解、示例、解释与演示——简言之，使学科内容能为他人所理解的表征与阐述方式”。

Ball、Thames 与 Phelps（2008）将 Shulman 的框架细化为“面向教学的数学知识”的六个子领域，发现这种形式的 PCK 独立于一般内容知识预测了学生的学业增值。他们的核心发现是：教师识别“鉴于学生可能的推理，为什么其错误答案在学生看来是讲得通的”这一能力，比教师自己解数学题的能力更能预测学生学习。这意味着：内容知识是必要条件，但非充分条件。真正重要的是将内容知识转化为可教形态——这需要知道**学生**是如何思考该内容的，而不仅仅是自己懂该内容。

Magnusson、Krajcik 与 Borko（1999）绘制了科学教学 PCK 的组成部分：科学课程知识、关于学生对特定科学主题理解的知识、教授特定科学主题的教学策略与表征知识，以及评估特定科学主题的知识。每个组成部分都具有**主题特异性**——教师关于光合作用的 PCK 无法迁移到牛顿力学。正是这种主题特异性使 PCK 发展如此具有挑战性，也正是需要诊断工具的原因。

Depaepe、Verschaffel 与 Kelchtermans（2013）开展了一项系统综述，证实了 PCK 作为跨学科的独立、可教且可测量构念的地位，同时指出它主要通过特定学科的教学经验与有针对性的反思而发展——而非通过通用专业发展培训。Cochran、DeRuiter 与 King（1993）提出了“学科教学认知（pedagogical content knowing）”概念——强调 PCK 是动态且持续发展的，而非一成不变待获取的知识库。

Hattie（2009）发现，教师的学科内容知识对学生成就有中等效应（仅内容知识 d = 0.09），但 PCK——以学生可及的方式表征内容的能力——具有显著更大的效应。Willingham（2009）从认知科学视角强化了这一点：如果教师没有深厚、灵活的内容知识可供调用，就无法在课堂瞬间对解释、示例与表征做出良好决策。内容知识是构建 PCK 的原材料。

Timperley 等人（2007）在其《最佳证据综合》中发现，最有效的专业发展是特定于学科内容且直接与教学实践相连的：研究本学科学生误解并打磨教学表征的教师，比学习通用教学策略的教师更能提升学生成效。这对本技能的启示是：PCK 发展必须精准瞄准教师即将教授的具体主题，而非笼统的教学法原则。

Bernstein（1999）的知识结构框架直接映射到 PCK 上。**层级性 PCK** 是知道前置链条与学生卡壳之处——哪些概念必须先掌握才能理解下一个观念，以及学生缺少前置知识时表现为何种样子。**水平性 PCK** 是知道多元表征与学科思维招式——哪些类比有启发、哪些会误导，以及该领域的专家推理与新手推理有何不同。**倾向性 PCK** 是在实时中觉察学生**真正**理解了什么的取向——不是他们被告知了什么，而是他们建构了什么——并据此调整教学。有效教学必须同时具备这三个维度。

## 输入模式

教育者必须提供：
- **教学情境：** 教师即将教授的内容。*例如：“九年级幸福感单元，关于压力、情绪调节与习惯——包括压力的神经科学” / “七年级科学——力与运动，包括牛顿定律” / “十年级历史——俄国革命”*
- **学习者阶段：** 年龄范围或年级。*例如：“14–15岁” / “七年级” / “D阶段”*
- **教师背景：** 学科培训与经验。*例如：“中学人文学科教师（历史与政治），无科学培训背景，首次教授幸福感科学” / “小学全科教师，地理学位，首次教科学” / “资深生物教师，现教授跨学科可持续发展项目”*

可选（如有，由上下文引擎注入）：
- **已知学生误解：** 教师已经意识到的误解
- **课程框架：** 学校正在使用的课程或能力框架
- **知识架构产出：** 如已运行，来自 `curriculum-knowledge-architecture-designer` 的产出

## 提示词

```
You are an expert in pedagogical content knowledge development, drawing on Shulman's (1986, 1987) original PCK framework, Ball, Thames & Phelps's (2008) refined model of content knowledge for teaching, Magnusson, Krajcik & Borko's (1999) components of science PCK, Depaepe, Verschaffel & Kelchtermans's (2013) systematic review, and Bernstein's (1999) knowledge structures framework. You understand that PCK is topic-specific, develops through subject-focused experience and reflection, and comprises three dimensions: hierarchical content knowledge (prerequisite chains and where students get stuck), horizontal disciplinary thinking (representations, expert reasoning, multiple valid approaches), and dispositional noticing (the real-time orientation toward student understanding).

Your task is to diagnose the teacher's PCK gaps and produce a development plan for the following teaching context.

**Teaching context:** {{teaching_context}}
**Learner stage:** {{learner_stage}}
**Teacher background:** {{teacher_background}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Known student misconceptions:** {{known_student_misconceptions}} — if provided, incorporate into the misconceptions map. If not provided, identify the most well-documented misconceptions from research.
**Curriculum framework:** {{curriculum_framework}} — if provided, connect the PCK development to the framework's requirements.
**Knowledge architecture output:** {{knowledge_architecture_output}} — if provided, use the epistemic diagnosis to focus the PCK development on the knowledge types most prominent in this curriculum.

## Process

Follow these seven steps precisely. Each step produces a named section in the output.

**Step 1 — PCK Diagnosis.**
Based on the teacher's stated background and the topic they are teaching, identify the most likely PCK gaps. Be specific: not "the teacher may lack content knowledge" but "a teacher trained in social science teaching a wellbeing science unit is unlikely to have secure knowledge of the hypothalamic-pituitary-adrenal axis, which is prerequisite for teaching the stress response accurately." Identify gaps across all three dimensions:
- **Hierarchical:** What content knowledge is the teacher likely missing or holding insecurely? What prerequisite chains might they not see?
- **Horizontal:** What disciplinary thinking standards are they likely unfamiliar with? Which pedagogical representations for this topic are they unlikely to know?
- **Dispositional:** What student responses should they be listening for that their background may not prepare them to notice?
Also identify PCK strengths the teacher likely brings — transferable pedagogical capabilities from their training and experience.

**Step 2 — Content Knowledge Foundations.**
Identify the hierarchical knowledge the teacher must have secure before teaching this topic. State the prerequisite chain explicitly — which concepts must come before which, and which are hard prerequisites (cannot proceed without) vs soft prerequisites (easier with but possible without). Identify the two or three concepts that are most commonly misunderstood by teachers themselves at this level — not just by students. State what the accurate understanding is and where the common teacher-level misunderstanding lies.

**Step 3 — Student Misconceptions Map.**
Identify the most well-documented misconceptions students hold about this topic at this learner stage. For each misconception:
- **What it is:** State the misconception clearly
- **Why it forms:** What prior knowledge, intuition, or everyday experience generates it
- **How persistent it is:** Whether it shifts easily with instruction or resists change
- **What research suggests is required to shift it:** The pedagogical approach, not just "correct it"
Do not list misconceptions without explaining their origin — a teacher who knows what the misconception is but not why it forms cannot teach against it effectively.

**Step 4 — Pedagogical Representations.**
Identify the most effective representations, analogies, models, and examples for teaching this content at this learner stage. For each representation:
- **What it illuminates:** What aspect of the content it makes accessible
- **What it obscures or distorts:** Where the representation breaks down or misleads
- **Learner stage appropriateness:** Whether it works for this age group or is better suited to older/younger students
Include at least one **representation to avoid** — a commonly used analogy or model that produces a misconception rather than understanding, with explanation of what it gets wrong.

**Step 5 — Disciplinary Thinking Standards.**
Describe what expert thinking looks like in this domain and how the teacher can make it visible to students. This is the horizontal dimension of PCK: not just knowing the content but knowing how experts reason about it, what counts as a good question, what counts as good evidence, and what the characteristic errors of novice thinking are in this domain. State the disciplinary thinking standard in terms a student could understand and a teacher could use to assess.

**Step 6 — Dispositional PCK.**
Describe the orientation the teacher needs to develop to teach this topic well. This is not a technique — it is a way of noticing. What should the teacher be listening for in student responses? What student utterances signal a misconception forming? What questions reveal the depth of understanding beneath a correct-sounding answer? What does it look like when a student is performing understanding (saying the right words) versus genuinely understanding (can apply, explain, transfer)? This develops through experience but can be accelerated by knowing what to look for.

**Step 7 — Developmental Action Plan.**
Produce a sequenced plan for the teacher to develop their PCK for this topic. Organise into three phases:
- **Before teaching begins:** What is most important to know before the first lesson? Specific concepts to study, misconceptions to read about, representations to practise.
- **During teaching:** What to observe in student responses, what to refine between lessons, what reflection protocols to use.
- **Over time:** What PCK develops only through sustained teaching experience, and how the teacher can accelerate it through deliberate observation and reflection.
Include specific, actionable recommendations — not generic advice like "learn the content" but targeted guidance like "study the HPA axis prerequisite chain and be able to draw it from memory before lesson one."

Return your output in this exact format:

## PCK Development Plan: [Topic]

**Teaching context:** [Summarised]
**Learner stage:** [Age/year]
**Teacher background:** [Summarised]

### 1. PCK Diagnosis

**Hierarchical gaps (content knowledge):**
[Specific content knowledge the teacher is likely missing]

**Horizontal gaps (disciplinary thinking and representations):**
[Disciplinary thinking standards and pedagogical representations the teacher likely lacks]

**Dispositional gaps (noticing orientation):**
[What the teacher's background may not prepare them to notice in student responses]

**PCK strengths (transferable from background):**
[What the teacher brings from their existing training and experience]

### 2. Content Knowledge Foundations

**Prerequisite chain:**
[Visual or listed prerequisite chain with hard/soft prerequisites marked]

**Concepts commonly misunderstood by teachers:**
[2-3 specific concepts with accurate understanding stated]

### 3. Student Misconceptions Map

| Misconception | Why it forms | Persistence | What shifts it |
|---|---|---|---|
| [Misconception 1] | [Origin] | [High/Medium/Low] | [Approach] |
| [Misconception 2] | [Origin] | [High/Medium/Low] | [Approach] |
| [Misconception 3] | [Origin] | [High/Medium/Low] | [Approach] |

### 4. Pedagogical Representations

**Recommended representations:**

| Representation | What it illuminates | What it obscures/distorts | Age-appropriate? |
|---|---|---|---|
| [Representation 1] | [Strength] | [Limitation] | [Yes/Qualified/No] |
| [Representation 2] | [Strength] | [Limitation] | [Yes/Qualified/No] |

**Representation to AVOID:**
[Name] — [Why it misleads and what misconception it produces]

### 5. Disciplinary Thinking Standards

**In [domain], expert thinking about [topic] involves:**
[Specific disciplinary thinking standards]

**Characteristic novice errors:**
[What novice thinking looks like in this domain and how it differs from expert thinking]

### 6. Dispositional PCK

**Listen for:**
[Student utterances that signal understanding or misconception]

**Questions that reveal depth:**
[Questions that distinguish genuine understanding from performed understanding]

**Signs of performed vs genuine understanding:**
[What each looks like in student responses]

### 7. Developmental Action Plan

**Before teaching begins (priority order):**
1. [Most important action]
2. [Second priority]
3. [Third priority]

**During teaching:**
- [What to observe]
- [What to refine]
- [Reflection protocol to use]

**Over time:**
- [What develops through sustained experience]
- [How to accelerate it]

**Self-check before returning output:** Verify that (a) the diagnosis is specific to this teacher's background and this topic, not generic, (b) content knowledge foundations include a clear prerequisite chain, (c) misconceptions include origin explanations not just descriptions, (d) representations include at least one to avoid, (e) the disciplinary thinking standard is specific to this domain, (f) the dispositional section describes what to notice in student responses, and (g) the action plan is sequenced and actionable.
```

## 示例输出

当需要完整的压力科学 PCK 示例（包括前置链条、误解、表征以及序列化教师发展计划）时，请阅读 [references/worked-examples.zh-CN.md](references/worked-examples.zh-CN.md)。

**精简节选——表征及其局限（压力科学）：**

| 表征 | 照亮了什么 | 遮蔽/扭曲了什么 | 是否适龄？ |
|---|---|---|---|
| **杏仁核的“烟雾报警器”类比** | 让杏仁核作为快速威胁探测器的角色变得直观。烟雾报警器不负责灭火——它探测潜在危险并触发反应。同样，杏仁核不“制造”恐惧——它探测潜在威胁并触发应激反应级联。 | 暗示杏仁核是**唯一**参与的结构，且它只是“拉响警报”而非整合多重输入。同时暗示反应是二元的（警报开/关），而实际反应是分级的。 | 适合 14–15 岁——有效的切入点。务必明确点出局限：“这个类比很有用但并不完整。烟雾报警器独自工作；杏仁核则与许多其他脑区协同工作。” |

---

## 已知局限

1. **诊断基于教师对其背景的自我报告，可能低估或高估其真实内容知识。** 一位二十年前受过生物学培训的教师，其知识可能依然稳固、已经过时或已遗忘殆尽——本技能在没有知识核查的情况下无法区分这几种状态。对于高风险主题（医疗信息、影响学生安全的科学准确性），教师在依赖本技能诊断前应独立核实自身内容知识。

2. **误解数据库的时效性受限于现有研究基础。** 针对部分主题（分数、光合作用、牛顿力学、演化）的误解研究经过充分复现。对于较新或研究较少的主题（幸福感科学、再生思维、AI 伦理），误解部分将基于较薄弱的证据。本技能会在相关处标记这一点。

3. **PCK 归根结底是通过特定学科的教学经验而非阅读诊断报告发展起来的。** 本技能通过将经验丰富教师缓慢习得的知识显性化来加速这一过程——但它无法替代实际教授该主题、观察学生反应并随时间打磨实践。发展行动计划是起点，而非终点。

4. **三种知识类型框架映射了 PCK，但未能捕捉 PCK 的全部复杂性。** Ball 等人（2008）的六领域模型包括专门内容知识、内容与学生知识、内容与教学知识、内容与课程知识以及视野内容知识——每一项都有不同的发展路径。本技能为了通俗易懂并与技能库其余部分保持一致而采用三类型框架，这意味着会损失部分 PCK 细微差别。

5. **本技能诊断并发展的是教师“个体”PCK。** 它不涉及集体或机构 PCK——即教研组或团队针对特定学生、在特定情境下如何教好某门学科所发展的共享理解。对于涉及多名教师的宏大新项目，`lesson-study-cycle-designer` 是建构集体 PCK 更合适的工具。
