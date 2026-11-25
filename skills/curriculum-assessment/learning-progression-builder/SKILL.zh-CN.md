---
# AGENT SKILLS STANDARD FIELDS (v2)
name: learning-progression-builder
description: "构建学习进阶图谱，展示目标技能或理解从前置基础到精通掌握的递进步骤。适用于内容排序、诊断任务设计或梳理前置知识缺口。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/learning-progression-builder"
skill_name: "学习进阶构建器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Heritage (2008) — Learning progressions: supporting instruction and formative assessment"
  - "Popham (2007) — The lowdown on learning progressions"
  - "Daro et al. (2011) — Learning trajectories in mathematics: a foundation for standards, curriculum, assessment, and instruction"
  - "Wilson & Bertenthal (2005) — Systems for state science assessment"
  - "Hattie & Donoghue (2016) — Learning strategies: a synthesis and conceptual model"
input_schema:
  required:
    - field: "target_skill"
      type: "string"
      description: "进阶末端的技能或理解——学生最终应当能够做到的内容"
    - field: "student_level"
      type: "string"
      description: "该进阶覆盖的年龄/年级范围"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "starting_point"
      type: "string"
      description: "学生通常的起点——他们的已有知识"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：显示不同学生当前处于进阶何处的班级数据"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：相关课程标准或进阶文档"
output_schema:
  type: "object"
  fields:
    - field: "progression_map"
      type: "array"
      description: "从新手到目标水平的有序阶段序列，每个阶段附带可观察指标"
    - field: "prerequisite_relationships"
      type: "object"
      description: "哪些阶段依赖于哪些阶段——先修结构"
    - field: "common_stuck_points"
      type: "array"
      description: "学生通常停滞的位置及原因"
    - field: "diagnostic_tasks"
      type: "array"
      description: "揭示学生当前处于哪个阶段的快速任务"
chains_well_with:
  - "competency-unpacker"
  - "formative-assessment-technique-selector"
  - "practice-problem-sequence-designer"
  - "backwards-design-unit-planner"
  - "curriculum-knowledge-architecture-designer"
  - "scope-and-sequence-designer"
teacher_time: "4 分钟"
tags: ["learning-progressions", "trajectories", "prerequisites", "diagnostic", "curriculum-mapping"]
---

# 学习进阶构建器

## 本技能的作用

为特定技能领域绘制从新手到目标熟练度的学习进阶图谱，识别出理解的连续阶段、各阶段之间的先修关系（什么必须先于什么）、常见卡点（学生通常在哪里停滞以及为什么），以及能够揭示学生当前处于哪个阶段的诊断性任务。输出是一份教师可用于三种用途的进阶图谱：规划教学（按正确顺序教学）、形成性评估（诊断学生当前位置）以及差异化教学（为每个学生的当前阶段提供恰当支持）。AI 在此尤为关键，因为构建有效的学习进阶需要同时具备深厚的学科内容知识（理解领域的逻辑结构）与教学法知识（了解学生**实际上**会在哪里卡住——而这并不总是内容逻辑所预测的地方）。

## 实证基础

Heritage（2008）将学习进阶定义为“对儿童在学习过程中围绕某一主题相继展现的、逐步精深思维方式的描述”。她强调进阶是假设性路径，而非僵化轨道——学生可能会跳过某些阶段、回访早期阶段或走替代路线。Popham（2007）指出，学习进阶对形成性评估至关重要，因为它们提供了“地图”，使教师能够定位学生当前的理解并确定下一步行动。没有进阶图谱，教师只知道学生在“挣扎”，却不知道困难究竟出在学习路径的**何处**。Daro 等人（2011）证明，数学学习轨迹——经过实证验证的进阶——为连贯的课程、评估与教学奠定了基础。Wilson & Bertenthal（2005）将学习进阶应用于科学评估，表明基于进阶的评估比基于单一标准的评估更具信息量，因为它揭示了发展路径，而不仅仅是一个二元标准是否达标。Hattie & Donoghue（2016）表明，不同学习策略在学习的不同阶段发挥作用——表层策略（记忆、复述）在早期有效；深层策略（精细加工、组织）在后期有效——这意味着教学方法应当匹配学生在进阶上的位置。

## 输入规范

教师必须提供：
- **目标技能（Target skill）：** 学生最终应能做到的内容。*例如：“解两边都含未知数的多步方程” / “围绕文学文本写出一篇充分展开的分析性段落” / “设计并评估公平的科学实验”*
- **学生水平（Student level）：** 年级范围。*例如：“7–9 年级” / “KS3” / “初中”*

可选项（如可用则由上下文引擎注入）：
- **学科领域（Subject area）：** 课程学科
- **起点（Starting point）：** 学生的起始位置
- **学生画像（Student profiles）：** 显示当前所处位置的班级数据
- **课程框架（Curriculum framework）：** 相关标准或进阶文档

## 提示词（Prompt）

```
You are an expert in learning progressions and curriculum coherence, with deep knowledge of Heritage's (2008) framework for learning progressions, Popham's (2007) work on progression-based assessment, and Hattie & Donoghue's (2016) research on stage-appropriate learning strategies. You understand that learning progressions are hypothesised pathways — they describe the typical developmental sequence but acknowledge that individual students may follow different routes.

Your task is to build a learning progression for:

**Target skill:** {{target_skill}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the target skill.
**Starting point:** {{starting_point}} — if not provided, identify the typical entry point for students at the beginning of the stated level range.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical class where students are at various points along the progression.
**Curriculum framework:** {{curriculum_framework}} — if not provided, build on general curriculum expectations.

Apply these evidence-based principles:

1. **Identify sequential stages (Heritage, 2008):**
   - Define 5–7 stages from novice to target proficiency.
   - Each stage should describe a qualitatively different level of understanding or capability — not just "more" of the same thing.
   - Each stage should be OBSERVABLE — described in terms of what the student can DO, not what they "understand" internally.
   - Stages should be ordered by typical developmental sequence, acknowledging that some students may not follow this exact order.

2. **Map prerequisite relationships (Daro et al., 2011):**
   - Which stages MUST come before which? (Not just which usually do, but which logically must.)
   - Identify both linear prerequisites (A must come before B) and parallel prerequisites (both C and D must be in place before E).
   - Distinguish hard prerequisites (the stage cannot be attempted without the prior) from soft prerequisites (the stage is easier with the prior but possible without it).

3. **Identify common stuck points (Popham, 2007):**
   - Where do students typically stall? These are the diagnostic priorities.
   - For each stuck point: what does "stuck" look like, and what is usually causing it?
   - Stuck points often occur at transitions between qualitatively different types of thinking (e.g., from procedural to conceptual, from concrete to abstract).

4. **Design diagnostic tasks (Heritage, 2008; Popham, 2007):**
   - For each stage, provide a quick task (2–5 minutes) that reveals whether a student has reached that stage.
   - Diagnostic tasks should be efficient — they test the KEY indicator of each stage, not everything a student at that stage can do.
   - The task should distinguish between adjacent stages — a student at Stage 3 should pass the Stage 3 diagnostic but fail the Stage 4 diagnostic.

5. **Stage-appropriate teaching approaches (Hattie & Donoghue, 2016):**
   - Early stages: surface strategies — explicit instruction, modelling, practice with feedback.
   - Middle stages: deep strategies — elaboration, connection-making, explaining reasoning.
   - Later stages: transfer strategies — application to new contexts, evaluation, independent problem-solving.

Return your output in this exact format:

## Learning Progression: [Target Skill]

**From:** [Starting point]
**To:** [Target proficiency]
**For:** [Student level range]

### Progression Map

For each stage:
**Stage [N]: [Name]**
- **What the student can do:** [Observable indicators]
- **Key shift from previous stage:** [What's qualitatively different]
- **Prerequisite:** [What must be in place first]
- **Diagnostic task:** [Quick task that reveals whether the student is at this stage]

### Prerequisite Diagram

[Visual or textual representation of which stages depend on which]

### Common Stuck Points

For each stuck point:
**Stuck between Stage [X] and Stage [Y]**
- **What "stuck" looks like:** [Observable signs]
- **What usually causes it:** [The underlying difficulty]
- **How to unstick:** [Targeted teaching intervention]

### Teaching Implications

[How the progression should inform instruction — what to teach first, where to invest time, when to use which teaching strategies]

**Self-check before returning output:** Verify that (a) stages are qualitatively distinct, (b) each stage has observable indicators, (c) prerequisite relationships are explicit, (d) diagnostic tasks distinguish between adjacent stages, (e) stuck points are based on common patterns, and (f) the progression represents a developmental pathway, not just a list of topics.
```

## 示例输出

**情景：** *目标技能：“围绕文学文本写出一篇充分展开的分析性段落，嵌入引文并解释语言对读者产生的效果” / 学生水平：“7–9 年级” / 学科领域：“英语文学”*

---

## 学习进阶：关于文学作品的分析性写作

**起点：** 能够复述文本中发生了什么（叙事概括）
**终点：** 能够使用嵌入式引文写出一篇充分展开的分析性段落，并解释语言选择对读者产生的效果
**适用对象：** 7–9 年级英语文学

### 进阶图谱

**第 1 阶段：复述（Retelling）**
- **学生能做什么：** 按时间顺序概括文本中发生的事情。“斯克鲁奇是一个讨厌圣诞节的刻薄老头。后来三个幽灵拜访了他，他就变好了。”
- **与上一阶段的关键跃迁：** 入口起点——无需前置阶段。
- **前置条件：** 基础阅读理解（能读懂文本情节）。
- **诊断任务：** “告诉我第一章发生了什么。”如果学生能准确复述，他们处于第 1 阶段。如果他们**只能**复述（做不到第 2 阶段），则需要向前推进。

**第 2 阶段：识别特征（Identifying Features）**
- **学生能做什么：** 指认语言特征但不作分析。“作者用了明喻。”“这句话里有头韵。”看到技巧时能叫出名称。
- **与上一阶段的关键跃迁：** 从“发生了什么”转向“是如何写的”——从内容转向写作工艺的根本转变。
- **前置条件：** 第 1 阶段（必须先读懂文本才能分析）。必须知道至少 5 种技巧的名称。
- **诊断任务：** “在这一段中标出并命名你能找到的任何语言技巧。”如果学生能正确识别 2 种以上技巧，他们处于第 2 阶段。

**第 3 阶段：引文 + 简评（Quotation + Comment）**
- **学生能做什么：** 挑选一句引文并对其做出评论：“作者说‘dark and stormy night’，这表明当时很吓人。”评论相关但未展开——只是一句陈述，而非解释。
- **与上一阶段的关键跃迁：** 从仅仅命名技巧转向挑选证据并围绕其提出主张。
- **前置条件：** 第 2 阶段（必须能识别特征）。必须理解引文作为证据的作用。
- **诊断任务：** “从文本中选出一句引文，解释它展示了什么。”如果学生选了相关引文并做出一句相关评论（哪怕简短），他们处于第 3 阶段。

**第 4 阶段：解释效果（Explaining Effect）**
- **学生能做什么：** 解释语言对读者产生了什么作用：“‘raging（狂怒的）’一词暗示大海暴烈且失控，这让读者为人物感到恐惧。”解释具体——点明了读者体验到的感受、画面或想法。
- **与上一阶段的关键跃迁：** 从评论文本**说了什么**转向解释文本**做了什么**——从内容转向效果。这是核心的分析性跃迁。
- **前置条件：** 第 3 阶段（必须能挑选证据并评论）。必须理解作者做出选择是为了在读者身上制造效果。
- **诊断任务：** “‘raging’一词对读者有什么效果？它让你想到或感受到什么？”如果学生能说出具体效果（而非“这很有效”或“这让人想继续读”），他们处于第 4 阶段。

**第 5 阶段：充分展开的分析性段落（Developed Analytical Paragraph）**
- **学生能做什么：** 写出遵循连贯结构的段落：论点 → 嵌入式引文 → 对具体词语的分析 → 效果解释 → 联系更广泛的意义。各部分逻辑衔接紧密。
- **与上一阶段的关键跃迁：** 从孤立评论转向持续、结构化的分析——多个句子层层递进。
- **前置条件：** 第 4 阶段（必须能解释效果）。必须理解段落结构与衔接。
- **诊断任务：** “写一段话，分析作者在这段节选中如何营造紧张感。”如果段落有清晰论点、嵌入式证据、词级具体分析与效果解释，学生处于第 5 阶段。

**第 6 阶段：评价性与比较性分析（目标）**
- **学生能做什么：** 写出的分析性段落能考量多种可能阐释、比较不同技巧、评价哪一种最有效，并将分析联系到作者更广泛的意图与主题。使用评价性与比较性语言：“虽然隐喻制造了视觉冲击力，但真正传达出人物痛苦的却是句式结构。”
- **与上一阶段的关键跃迁：** 从单一阐释的分析转向评价性、比较性、多层次的分析——学生思考作者**为什么**选择这种手法而非替代方案。
- **前置条件：** 第 5 阶段（必须能写出充分展开的分析性段落）。必须对整部文本与背景有足够了解。
- **诊断任务：** “分析作者在这段节选中如何制造【某效果】。至少考量两种技巧，并评价哪一种更有效。”如果学生能对比技巧并有理有据地评价，他们处于第 6 阶段。

### 先修关系图

```
第 1 阶段（复述）
    ↓
第 2 阶段（识别特征）← [需要：技巧名称知识]
    ↓
第 3 阶段（引文 + 简评）
    ↓
第 4 阶段（解释效果）← [关键跃迁：内容 → 效果]
    ↓
第 5 阶段（充分展开的段落）← [需要：段落结构技能]
    ↓
第 6 阶段（评价性分析）← [需要：更广泛的文本知识]
```

线性进阶，在第 2、5、6 阶段存在横向先修要求。

### 常见卡点

**卡在第 2 阶段与第 3 阶段之间：能识别技巧，但不会挑选证据**
- **“卡住”的表现：** 学生积极地高亮并标注各种技巧，但被要求“选一句引文并解释它”时却僵住了。他们能找特征，却选不出**最值得**写的那一句。
- **常见原因：** 学生被训练成了找出**所有**技巧（找特征），却没学过评估哪句引文有分析价值。他们把技巧当成寻找的对象，而非分析的对象。
- **疏通方法：** 教授引文筛选：“这里有三句引文。哪一句能让你写出最多内容？为什么？”在让学生自己找引文前，先练习在给定引文间做选择。

**卡在第 3 阶段与第 4 阶段之间：能评论但不会解释效果（最常见卡点）**
- **“卡住”的表现：** 学生写“这表明……”并做出相关评论，但评论描述的是内容而非效果。“隐喻表明大海很危险”（内容）vs.“隐喻让读者感到恐惧”（效果）。或者学生退回到万能套话：“这很有效，让读者想继续读下去。”
- **常见原因：** 学生没有区分文本**说了什么**与文本**做了什么**。他们学会了从文本里找意思，却没学会考量读者的体验。这是一个概念障碍——他们需要理解分析关注的是语言的**效果**，而不仅仅是字面意思。
- **疏通方法：** 两问技巧：每写完一句引文，追问“这让你**看到**什么？”和“这让你**感受到**什么？”这两个问题迫使注意力转向读者体验。大量示范：把内容评论与效果分析并排展示对比。

**卡在第 5 阶段与第 6 阶段之间：能写好一段，但不会评价或比较**
- **“卡住”的表现：** 学生能写出合格的 PEEL 段落，一次分析一种技巧，但无法比较技巧、考量替代阐释或评价相对有效性。他们的段落扎实却彼此孤立——没有聚合成更大的分析性论证。
- **常见原因：** 学生掌握了程序性技能（写分析段落），但尚未发展出超越它的评价性思维。比较与评价是高阶技能，要求学生同时在脑海中保有多个分析对象。
- **疏通方法：** 显性教授比较：“你已经写了隐喻。现在再写一下句式结构。现在——哪种技巧在制造紧张感上**更**有效，为什么？”提供比较句框：“虽然【技巧 1】制造了【效果】，但可以说【技巧 2】更有效，因为……”

### 教学启示

1. **把最多时间投入第 3→4 阶段的过渡。** 这里是大多数学生停滞的地方，也是关键分析性跃迁发生的地方。能解释效果的学生就能快速通过第 5 和第 6 阶段；解释不出效果的学生无论写多少字都会停滞不前。

2. **不要跳阶段。** 还不能识别技巧（第 2 阶段）的学生不应被要求直接写分析性段落（第 5 阶段）。各阶段层层相扣——在基础尚未打牢时直接跳到终点任务只会制造超载，而非学习。

3. **使用诊断任务进行差异化教学。** 在任何八年级班级中，学生都会分布在第 2–5 阶段。用诊断任务定位每位学生，然后提供匹配其阶段的教学：第 2 阶段学生练习识别，第 3 阶段学生练习选证，第 4 阶段学生练习解释效果，第 5 阶段学生练习段落建构。

4. **将教学方法与阶段匹配。** 第 1–3 阶段：显性教学、示范、带反馈的引导练习（表层策略）。第 4 阶段：出声思考、样例、同伴讨论（深层策略）。第 5–6 阶段：独立练习、对照标准自评、比较写作任务（迁移策略）。

---

## 已知局限

1. **学习进阶是假设性路径，而非固定轨道。** 个别学生可能会跳阶段、暂时回退或以不同顺序发展技能。进阶描述的是**典型**发展序列——当学生不按预期路径走时，教师必须运用专业判断。

2. **进阶描述的是“单一领域”内的技能发展。** 一名学生可能在诗歌分析上处于第 5 阶段，而在散文分析上处于第 3 阶段，因为底层文本呈现的挑战不同。进阶具有领域特定性——教师应分领域单独评估。

3. **诊断任务提供的是快照，而非全面评估。** 在某一次通过第 4 阶段诊断任务的学生，未必能稳定保持第 4 阶段水平。诊断定位的是学生的大致位置——持续的形成性评估才能提供更完整的图景。
