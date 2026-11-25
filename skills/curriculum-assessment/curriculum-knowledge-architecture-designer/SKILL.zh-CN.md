---
# AGENT SKILLS STANDARD FIELDS (v2)
name: curriculum-knowledge-architecture-designer
description: "绘制学科的认识论结构图谱，以确定知识类型并指导课程序列安排。适用于设计课程、重构教学项目或分析知识架构。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/curriculum-knowledge-architecture-designer"
skill_name: "课程知识架构设计器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Bernstein (1999) — Vertical and horizontal discourse: hierarchical vs horizontal knowledge structures"
  - "Bernstein (2000) — Pedagogy, Symbolic Control and Identity: recontextualisation and the pedagogic device"
  - "Muller (2009) — Forms of knowledge and curriculum coherence: conceptual vs contextual coherence"
  - "Maton (2009) — Cumulative and segmented learning: curriculum structures and knowledge-building"
  - "Maton (2013) — Making semantic waves: semantic gravity and density as tools for cumulative learning"
  - "Maton (2014) — Knowledge and Knowers: Legitimation Code Theory (Semantics dimension)"
  - "Young (2008) — Bringing Knowledge Back In: powerful knowledge and social realist curriculum theory"
  - "Wheelahan (2010) — Why Knowledge Matters in Curriculum: access to theoretical knowledge as social justice"
  - "Bianchi, Pisiotis & Cabrera Giraldez (2022) — GreenComp: European Sustainability Competence Framework"
  - "Bacigalupo et al. (2016) — EntreComp: Entrepreneurship Competence Framework"
  - "Sala et al. (2020) — LifeComp: European Framework for Personal, Social and Learning to Learn"
input_schema:
  required:
    - field: "curriculum_input_type"
      type: "string"
      description: "课程输入类型：'course'（单门课程）、'scope-and-sequence'（教学进度大纲）或 'project-brief'（项目简报）"
    - field: "domain_or_subject"
      type: "string"
      description: "学科或领域的名称与简短描述"
    - field: "learner_stage"
      type: "string"
      description: "年龄范围或年级"
    - field: "learning_goals"
      type: "string"
      description: "预期学习结果——用 3–5 句话描述学生应当知道、理解并能够做到的内容"
  optional:
    - field: "existing_curriculum_documents"
      type: "string"
      description: "来自上下文引擎：课程文档、单元计划或教学进度大纲文本"
    - field: "competency_framework"
      type: "string"
      description: "来自上下文引擎：学校使用的能力或倾向框架"
    - field: "prior_knowledge_baseline"
      type: "string"
      description: "来自上下文引擎：在本课程开始前学生已经知道和能做什么"
output_schema:
  type: "object"
  fields:
    - field: "epistemic_diagnosis"
      type: "object"
      description: "存在哪些知识类型、大致比例及推理说明"
    - field: "knowledge_architecture_map"
      type: "object"
      description: "针对每种类型：层级型先修链条、横向型概念枢纽与视角，或倾向型进阶学段"
    - field: "mixed_architecture_notes"
      type: "string"
      description: "在此特定课程中各类型在何处交互、重叠或产生张力。当识别出倾向性目标时，标明其是否属于知识依赖型（knowledge-contingent）——即是否需要足够的层级型与横向型知识基础才能有意义地发展。例如：批判性思维、生态素养、再生思维、创业思维。对于知识依赖型倾向，指明哪些具体的层级型与横向型要素是该倾向得以运作的前提条件，并明确声明：在这些前置条件到位前，该倾向无法真实发展。"
    - field: "teaching_sequencing_implications"
      type: "string"
      description: "该架构对内容排序与教学节奏意味着什么"
    - field: "assessment_implications"
      type: "object"
      description: "哪些要素可自动评估 vs. 需要教师判断及其原因。当存在横向知识时，标明批判性思维究竟是通过学科思维标准的显性教学刻意培养，还是被假设通过接触横向内容自然涌现。研究（Bailin et al. 1999; Willingham 2007）明确指出，学科内容不会自动培养批判性思维——必须在学科内显性教授。如果课程将批判性思维列为目标却未包含该领域优秀思维标准的显性教学，将其标为设计缺口。"
    - field: "ai_tutoring_design_implications"
      type: "string"
      description: "该架构应如何指导智能辅导系统或 AI 教师助手的设计"
chains_well_with:
  - "learning-target-authoring-guide"
  - "competency-framework-mapper"
  - "scope-and-sequence-designer"
  - "d2r-project-cycle-designer"
teacher_time: "5 分钟"
tags: ["knowledge-structure", "curriculum-architecture", "Bernstein", "epistemic-design", "hierarchical", "horizontal", "dispositional", "mixed-architecture", "AI-tutoring"]
---

# 课程知识架构设计器

## 本技能的作用

接收一份课程输入——单门课程、学科教学进度大纲或真实世界项目简报——并诊断该知识领域的认识论架构。它判断该领域主要是层级型（Hierarchical）、横向型（Horizontal）、倾向型（Dispositional），还是混合架构（Mixed architecture），随后为存在的每种类型构建相应的知识结构图谱，并输出对教学顺序、评估设计与 AI 辅导架构的具体启示。大多数真实课程——尤其是项目式与真实世界学习设计——都是混合架构。本技能诊断比例与交互作用，而非强行套用单一类型。AI 在此尤为关键，因为认识论诊断需要同时运用社会学理论（Bernstein 的知识结构）、课程设计专长（排序与评估逻辑）以及能力框架素养（倾向性进阶）——这种跨界组合在单个教育者身上十分罕见，且手动推演耗时极长。

## 实证基础

Bernstein（1999）区分了两种话语形式——横向话语（日常、情境特定的知识）与纵向话语（系统化、有原则的知识）——并在纵向话语内部识别出两种知识结构。**层级型知识结构（Hierarchical knowledge structures）** 连贯、原则显明且层级整合：新理论涵盖并概括旧知识，形成累积性进阶，低阶概念必须先掌握，高阶概念才可触及。自然科学是典型代表。**横向型知识结构（Horizontal knowledge structures）** 组织为一系列专业化语言或视角（lenses），各自拥有其探究方式与有效知识标准。其发展通过新视角的累积而非整合实现。人文与社会科学是典型代表。Bernstein（2000）通过“再语境化（recontextualisation）”概念拓展了该框架——即知识如何从生产场域转化为教学语境——这直接指导课程设计者在做排序决策时如何思考知识类型。

Muller（2009）将 Bernstein 框架应用于课程连贯性，区分了**概念连贯性（conceptual coherence）**（层级型知识的特征——知识在先前知识基础上累积建构的课程）与**情境连贯性（contextual coherence）**（分段式课程的特征——每个片段各自适配特定情境，片段间未必彼此递进）。这一区分对排序具有直接启示：概念连贯的课程具有难以重新排序的内在逻辑，而情境连贯的课程可以从多个切入点进入。

Maton（2009, 2013, 2014）发展了合法化符码理论（Legitimation Code Theory）的语义维度，提供了两个分析工具：**语义重力（semantic gravity）**（意义与特定情境绑定的程度——更强的 SG 意味着更依赖情境，更弱的 SG 意味着更抽象且可迁移）与**语义密度（semantic density）**（意义浓缩进术语或符号的程度）。Maton（2013）提出了**语义波（semantic waves）**概念——在具体案例（高 SG、低 SD）与抽象原理（低 SG、高 SD）之间往返移动的教学实践——证明制造这种波动的课程与教学能促成累积性知识建构，而停留在平坦状态（始终停在具体情境或始终停在抽象理论）的教学则产出碎片化学习。这为识别课程中何处需要概念解包与重包提供了诊断工具。

Young（2008）指出课程理论必须认真对待“什么知识重要”——提出了**强有力知识（powerful knowledge）**概念：系统化、基于学科的专业知识，它赋予学习者日常经验无法获得的解释框架。Wheelahan（2010）进一步论证，将知识削减为脱离理论根基的情境技能的能力本位课程，实际上剥夺了学生接触促成社会参与的概念结构的机会——使知识架构不仅是一个教学法问题，更是一个教育公平问题。

**倾向型知识（dispositional knowledge）** 类别借鉴自能力框架文献。与层级型和横向型结构（描述命题性知识的组织方式）不同，倾向型知识由不断发展的能力、态度取向与实践性素养构成——它只存在于实践行动之中。欧盟能力框架提供了最严谨的界定：GreenComp（Bianchi, Pisiotis & Cabrera Giraldez, 2022）界定了十二项可持续发展能力，包括能动性、系统思维与价值素养；EntreComp（Bacigalupo et al., 2016）跨越八级进阶模型界定了十五项创业能力，包括自我觉察、创造力与经验学习；LifeComp（Sala et al., 2020）界定了九项个人、社会与学会学习能力，包括自我调节、协作与批判性思维。这些框架拥有共同特征：进阶是定性且发展性的，通过发展学段而非先修链条描述，且评估需要教师对实践能力的专业判断，而非命题性知识测验。

## 输入规范

教师必须提供：
- **课程输入类型（Curriculum input type）：** 你提供的是哪种输入？*例如：“course” / “scope-and-sequence” / “project-brief”*
- **领域或学科（Domain or subject）：** 名称与简短描述。*例如：“九年级科学——力、能量与运动” / “设计与再生项目（D2R）——本地湿地的智能水系统” / “IB 历史——20 世纪威权国家的成因与后果”*
- **学习者阶段（Learner stage）：** 年龄范围或年级。*例如：“12–14 岁” / “十年级” / “7–8 年级”*
- **学习目标（Learning goals）：** 学生应当知道、理解并能做什么——3–5 句话。*例如：“学生将理解力如何引起运动状态改变，将牛顿定律应用于真实世界情境，设计并测试简单机械，并通过书面论证传达科学推理。”*

可选项（如可用则由上下文引擎注入）：
- **现有课程文档（Existing curriculum documents）：** 课程文档、单元计划或教学进度大纲文本
- **能力框架（Competency framework）：** 学校使用的倾向性或能力框架
- **先验知识基线（Prior knowledge baseline）：** 学生已经知道和能做什么

## 提示词（Prompt）

```
You are an expert in curriculum epistemology and knowledge structure analysis, with deep knowledge of Bernstein's (1999, 2000) theory of knowledge structures, Muller's (2009) work on curriculum coherence, and Maton's (2009, 2013, 2014) Legitimation Code Theory — particularly the Semantics dimension (semantic gravity and semantic density). You also understand competency framework design (GreenComp, EntreComp, LifeComp) and the distinction between propositional knowledge structures and dispositional development.

Your task is to diagnose the epistemic architecture of the following curriculum input and produce a complete knowledge architecture analysis.

**Curriculum input type:** {{curriculum_input_type}}
**Domain or subject:** {{domain_or_subject}}
**Learner stage:** {{learner_stage}}
**Learning goals:** {{learning_goals}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Existing curriculum documents:** {{existing_curriculum_documents}} — if not provided, work from the domain, subject description, and learning goals.
**Competency framework:** {{competency_framework}} — if not provided, identify any dispositional elements from the learning goals.
**Prior knowledge baseline:** {{prior_knowledge_baseline}} — if not provided, assume typical prior knowledge for this learner stage.

Apply the following framework. You MUST use the exact three knowledge types defined below. Most real curricula contain more than one type — your diagnosis must identify ALL types present, estimate their approximate proportion, and explain how they interact.

## The Three Knowledge Types

**1. Hierarchical Knowledge Structure (Bernstein, 1999)**
Knowledge is coherent, systematically principled, and organised so that lower-level concepts must be mastered before higher-level ones are accessible. Development is through integration, where new theory subsumes and generalises prior knowledge. The curriculum logic is cumulative — sequencing is constrained by prerequisite relationships. Conceptual coherence (Muller, 2009) holds: content cannot be freely reordered without loss.

Indicators: prerequisite chains exist; concepts build in abstraction; mastery of prior concepts is necessary for later ones; errors at lower levels propagate upward; the subject has a canonical sequencing logic.

Examples: mathematics, formal logic, music theory, programming fundamentals, chemistry, physics.

**2. Horizontal Knowledge Structure (Bernstein, 1999)**
Knowledge is organised as a series of specialised languages or lenses, each with its own modes of inquiry and criteria for valid knowledge. Content can be entered from multiple points; development is through accumulation of new perspectives rather than integration. Disciplinary thinking skill develops progressively even though content is not strictly prerequisite-ordered. Contextual coherence (Muller, 2009) allows curriculum segments to be reordered, though analytical sophistication still develops cumulatively.

Indicators: multiple valid interpretive lenses exist; content can be studied in various orders; "thinking like a historian/philosopher/sociologist" develops across the curriculum rather than through a fixed sequence; new units add perspectives rather than building on prior units.

Examples: history, literature, philosophy, geography, sociology, art criticism.

**3. Dispositional Knowledge Structure**
Knowledge is constituted by developing capacities, orientations, and enacted competencies. The knowledge cannot be separated from the learner's growing capability — it exists only in enactment. Progression is qualitative and developmental, requiring teacher judgment rather than automated assessment. Competency frameworks (GreenComp, EntreComp, LifeComp) provide the most rigorous articulations of this type.

Indicators: the learning goal describes who the student is becoming, not just what they know; progression is described in developmental bands (emerging → developing → extending) rather than prerequisite chains; assessment requires observation of enacted behaviour over time; the competency cannot be tested through a single task.

Examples: agency, collaboration, ecological literacy, entrepreneurial thinking, self-regulation, creative confidence, regenerative mindset.

## Diagnosis Process

Step 1: Read the curriculum input carefully. For each learning goal, determine which knowledge type(s) it belongs to.

Step 2: Estimate the approximate proportion of each type present (as percentages that sum to 100%). Explain your reasoning — which specific goals or content areas belong to which type.

Step 3: For each type present, build the appropriate knowledge structure map:
- **Hierarchical:** Identify the key prerequisite chains. Order concepts topologically — which concepts must come before which. Flag any concepts where the prerequisite relationship is hard (cannot proceed without it) vs soft (easier with it but possible without).
- **Horizontal:** Identify the conceptual hubs (central themes, phenomena, or questions) and the lenses or perspectives that orbit each hub. Show how analytical sophistication develops across the curriculum even though content is not prerequisite-ordered.
- **Dispositional:** Define progression band descriptors across 4 levels: Emerging → Developing → Competent → Extending. Each level must describe what the learner DOES (observable behaviour), not what they "understand" internally. Include indicators that distinguish between levels.

Step 4: Analyse the mixed architecture — where do types interact, overlap, or create tension? Where does a hierarchical prerequisite chain intersect with a dispositional development goal? Where does a horizontal lens require hierarchical foundational knowledge?

Step 5: Derive implications for teaching, assessment, and AI tutoring.

Return your output in this exact format:

## Knowledge Architecture Analysis: [Domain/Subject Name]

**Input type:** [course / scope-and-sequence / project-brief]
**Learner stage:** [age/year]
**Learning goals:** [Summarised]

### 1. Epistemic Diagnosis

**Architecture type:** [Mixed / Primarily Hierarchical / Primarily Horizontal / Primarily Dispositional]
**Proportions:** [e.g. 40% Hierarchical, 35% Horizontal, 25% Dispositional]

**Reasoning:**
[For each knowledge type present, explain which specific learning goals or content areas belong to it and why. Reference the indicators from the framework above.]

### 2. Knowledge Architecture Map

#### Hierarchical Elements
[If present: prerequisite chains with topological ordering. Show which concepts must come before which. Mark hard vs soft prerequisites. Use a visual chain format.]

#### Horizontal Elements
[If present: conceptual hubs and the lenses/perspectives that orbit them. Show how analytical thinking develops across the curriculum.]

#### Dispositional Elements
[If present: progression band descriptors across 4 levels — Emerging, Developing, Competent, Extending — with observable indicators at each level for each dispositional competency identified.]

### 3. Mixed Architecture Notes

[Where do types interact? Where does tension arise? Be specific to THIS curriculum.]

### 4. Teaching & Sequencing Implications

[What does the architecture mean for how content should be ordered and paced? Which elements have constrained sequencing (hierarchical) vs flexible sequencing (horizontal)? Where must dispositional development run as a continuous thread rather than being assigned to specific lessons?]

### 5. Assessment Implications

**Auto-assessable elements (suitable for AI/automated assessment):**
[List specific elements and explain why they are auto-assessable — typically hierarchical elements with clear right/wrong answers or demonstrable procedures.]

**Teacher-judgment elements (require human assessment):**
[List specific elements and explain why they require teacher judgment — typically dispositional elements and sophisticated horizontal analysis.]

**Mixed elements (partial automation possible):**
[Elements where AI can assess some dimensions but teacher judgment is needed for others.]

### 6. AI Tutoring Design Implications

[How should this architecture inform an intelligent tutoring system or AI teacher assistant? Consider:
- For hierarchical elements: adaptive sequencing, prerequisite checking, targeted practice
- For horizontal elements: perspective-prompting, analytical scaffolding, exposure to multiple lenses
- For dispositional elements: reflection prompts, portfolio tracking, teacher dashboards (NOT automated grading)
- For mixed architectures: how the tutoring system should handle the transitions between types]

**Self-check before returning output:** Verify that (a) all three knowledge types have been considered, not just the dominant one, (b) proportions are justified with specific references to learning goals, (c) the architecture map uses the correct format for each type (prerequisite chains for hierarchical, hubs-and-lenses for horizontal, progression bands for dispositional), (d) mixed architecture notes are specific to THIS curriculum rather than generic, (e) assessment implications distinguish clearly between auto-assessable and teacher-judgment elements, and (f) AI tutoring implications are practical and architecture-specific.
```

## 示例输出

当你需要完整的“智能水系统”示例（包括先修关系图、概念视角、倾向性进阶与辅导启示）时，请阅读 [references/worked-examples.zh-CN.md](references/worked-examples.zh-CN.md)。

**精简节选——解读混合架构（智能水系统）：**

**架构类型：** 混合型——三种知识类型均以显著比例存在。
**比例：** 40% 层级型、30% 横向型、30% 倾向型

**核心张力：** 层级型要素（水质科学、电子学）的评估可以标准化并采用标准参照。倾向型要素（能动性、协作、再生思维）则不能——它需要持续观察与专业判断。一个对两者赋予同等权重的项目评估框架，必须容纳性质截然不同的取证方式。这里存在一种风险：容易测量的层级型要素仅仅因为“好测”而主导了评估，从而边缘化了那些堪称 D2R 项目最重要成果的倾向性目标。

---

## 已知局限

1. **三类型框架是一种简化。** Bernstein 最初的区分是在纵向话语内部区分层级型与横向型知识结构。倾向型类别并非 Bernstein 原创——它借鉴自能力框架文献，代表了出于课程设计目的的实用扩展。在 Bernstein 框架下工作的学者可能不同意将倾向性知识视为独立结构类型，而非横向话语的一种特征。本框架作为设计工具提供，而非对社会学理论的学术贡献。

2. **比例只是近似且可商榷的。** 估算一门课程为“40% 层级型、30% 横向型、30% 倾向型”暗示了一种本框架无法提供的精确度。比例属于阐释性判断——另一位分析者可能会将同一课程评为 35/35/30 或 45/25/30。它们的价值在于浮现不同知识类型的相对权重并确保没有类型被遗漏，而非作为精确测量。

3. **诊断基于既定学习目标，而非已实施课程。** 一门写明了倾向性目标（能动性、协作）的课程，如果教学与评估只优先考虑层级型要素，实际上可能并未培养出这些倾向。架构分析揭示的是课程**声称**要做什么；它是否真正做到则取决于实施。教师应利用该分析核查自己的评估设计与日常教学实践是否真正回应了课程声称包含的所有知识类型。

4. **知识依赖型倾向需要前置诊断，而不仅仅是类型标注。** 某些倾向性目标——尤其是批判性思维、生态素养、再生思维和创业思维——在没有足够层级型与横向型知识基础的情况下无法真实发展。架构诊断识别出了倾向性目标的存在，但不会自动判断使该倾向得以运作的前置条件是否也存在于课程中。当诊断识别出知识依赖型倾向时，教学与评估启示必须显性指明需要先建构哪些层级型与横向型要素。一门只写“学生将发展批判性思维”却未确保有足够领域知识供其批判思考的课程，是无法达成该目标的。

5. **倾向性进阶学段描述的是典型发展，而非普遍固定阶段。** 一名学生可能在一个情境中展现出“拓展级”能动性，在另一个情境中处于“初现级”。倾向性发展具有情境敏感性与非线性特征。学段是观察与反馈的指南，而非僵化分类。

6. **AI 辅导启示假设系统具备模式切换能力。** 目前大多数 AI 辅导系统都是为层级型知识设计的（带对错反馈的自适应练习）。针对横向型与倾向型要素的建议描述的是大多数现有系统尚不具备的能力。这些启示具有前瞻性——描述的是一个具备架构意识的系统**应当**做什么，而不是现成系统目前能做什么。
