---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ai-learning-boundary-mapper
description: "绘制任务边界图谱，区分哪些作业环节受益于 AI 辅助、哪些环节会因使用 AI 而受损。适用于为 AI 时代课堂重新设计作业，或为特定任务制定有理有据的 AI 使用政策。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-literacy/ai-learning-boundary-mapper"
skill_name: "AI 学习边界映射器"
domain: "ai-literacy"
version: "1.0"
contributor: "Gareth Manning"
evidence_strength: "moderate"
evidence_sources:
  - "Wiggins & McTighe (2005) — Understanding by Design (backward design and assessment alignment)"
  - "Bjork et al. (2013) — Self-regulated learning: beliefs, techniques, and illusions"
  - "Kazemitabaar et al. (2023) — Studying the effect of AI code generators on supporting novice learners"
  - "Kirschner, Sweller & Clark (2006) — Why minimal guidance during instruction does not work"
  - "Wineburg & McGrew (2019) — Lateral reading and the nature of expertise"
input_schema:
  required:
    - field: "assignment_description"
      type: "string"
      description: "现有作业描述——要求学生做什么、产出什么或展示什么"
    - field: "learning_objectives"
      type: "string"
      description: "该作业旨在培养的技能、知识或素养"
  optional:
    - field: "current_ai_policy"
      type: "string"
      description: "目前对该作业允许、限制或未明确的 AI 使用规则"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "学科领域"
    - field: "assessment_context"
      type: "string"
      description: "作业如何评估——形成性、终结性、备考、档案袋"
    - field: "tool_comparison_needed"
      type: "boolean"
      description: "是否需要为作业中的信息搜集环节附带 Google 与 AI 聊天机器人的工具对比"
output_schema:
  type: "object"
  fields:
    - field: "objective_analysis"
      type: "object"
      description: "针对每项学习目标，分析 AI 辅助是支持还是削弱它——并附带推理"
    - field: "component_boundary_map"
      type: "object"
      description: "逐环节分析作业：AI 受益、AI 中性、AI 削弱，以及建议的修改方案"
    - field: "ai_policy_recommendations"
      type: "object"
      description: "针对该作业的具体、有理有据的 AI 使用建议——不是一刀切的允许或禁止，而是分环节指导"
    - field: "tool_comparison"
      type: "object"
      description: "针对作业中信息搜集环节的“何时用搜索 vs. 何时用 AI”指南"
    - field: "redesign_suggestions"
      type: "array"
      description: "具体的作业修改建议，在关键学习环节保留挑战性，同时在真正有帮助的环节允许使用 AI"
chains_well_with:
  - "metacognitive-monitoring-ai-contexts"
  - "backwards-design-unit-planner"
  - "assessment-validity-checker"
teacher_time: "5 分钟"
tags: ["AI-literacy", "assignment-design", "AI-policy", "backward-design", "tool-selection", "learning-objectives", "AI-boundaries"]
---

# AI 学习边界映射器

## 本技能的作用

针对特定作业生成逐环节分析，依据作业所服务的学习目标，绘制出哪些要素受益于 AI 辅助、哪些属于中性、哪些会因 AI 介入而受损。这是面向教师的 AI 时代作业重构设计工具：它接收一份现有作业，产出一份边界图谱，使教师能够制定具体、有理有据的 AI 使用政策，而非采取“全面允许”或“全面禁止”的一刀切立场。核心洞见在于：在任何单个作业内部，不同环节服务于不同的学习目标——在一个环节有帮助的 AI 辅助，在另一个环节可能会架空学习。例如，一篇既需要文献调研（AI 可协助概括背景）又需要原创论证（AI 辅助会绕过建构论证的认知工作）的论文，适合采用分环节政策，而非统一禁令。输出包括目标分析（针对每项学习目标分析 AI 辅助是支持还是削弱它）、环节边界图谱、有理有据的 AI 政策建议、面向信息搜集任务的 Google vs. AI 聊天机器人工具对比（可选），以及在保留关键学习挑战的同时允许 AI 在有益处发挥作用的重构建议。本技能是 `metacognitive-monitoring-ai-contexts` 在教师设计端的互补技能：边界映射防患于未然，元认知监控则在风险发生时予以应对。

## 实证基础

Wiggins & McTighe（2005）确立了逆向设计原则：评估设计应从学习目标（阶段一）出发，经由学习证据（阶段二）逆向推导出学习活动（阶段三）。这一原则直接适用于设定 AI 边界：问题不在于“这项作业该不该用 AI？”，而在于“这项作业服务于哪些学习目标，AI 辅助究竟是在支持还是绕过这些目标所需的认知工作？”Bjork 等人（2013）记录了胜任力错觉——学习者感觉自己学得比实际更多的情形。AI 辅助会产生流畅度错觉：借助 AI 完成的任务看起来完整且正确，但产生持久学习的认知工作却被绕过了。边界图谱旨在识别哪些作业环节最容易受此效应影响。Kazemitabaar 等人（2023）提供了直接实证证据：使用 AI 辅助的编程学生完成任务更快、错误更少，但在随后没有 AI 支持的任务中表现出了更弱的理解力。这一效应被用作识别“AI 削弱型”环节的模型——即任何以认知过程（而不仅仅是成品）为学习目标的任务。Kirschner、Sweller & Clark（2006）确立了极少引导的教学对初学者效果不如显性教学，因为初学者需要任务本身的认知挑战来建构通往专长所需的知识结构。这支持了我们的判断：通过 AI 移除认知挑战的环节，往往也移除了学习本身。Wineburg & McGrew（2019）为工具对比维度提供了间接支持：不同信息工具具有不同的认识论属性（可验证引文 vs. 综合推论），学生受益于关于“针对何种信息需求使用何种工具”的显性指导。

## 输入规范

教师必须提供：
- **作业描述（Assignment description）：** 学生要做什么。*例如：“十年级历史论文：撰写 600 词议论文——《凡尔赛条约》是否是二战的主要原因？必须使用至少三位具名历史学家的观点。下周提交” / “九年级科学：为反应速率实验撰写实验报告——方法、结果、分析、结论” / “十二年级英语：针对课堂学过的两部文本撰写比较论文”*
- **学习目标（Learning objectives）：** 作业旨在培养什么。*例如：“学生学会建构基于证据的历史论证、评价相互竞争的史学阐释，并恰当运用史料证据” / “学生学会根据自己收集的数据撰写科学分析，得出有效结论”*

可选项（如可用则由上下文引擎注入）：
- **当前 AI 政策（Current AI policy）：** 目前允许哪些使用方式
- **学生水平（Student level）：** 年级
- **学科领域（Subject area）：** 学科
- **评估情境（Assessment context）：** 形成性、终结性、备考
- **是否需要工具对比（Tool comparison needed）：** 是否包含 Google vs. AI 指南

## 提示词（Prompt）

```
You are an expert in curriculum and assessment design, with deep knowledge of Wiggins & McTighe's (2005) backward design, Bjork et al.'s (2013) research on illusions of competence, Kazemitabaar et al.'s (2023) empirical findings on AI assistance and learning, Kirschner et al.'s (2006) findings on minimally guided instruction, and Wineburg & McGrew's (2019) work on information tool evaluation. You understand that the question for AI boundary-setting is not "is AI helpful?" but "does AI assistance support or bypass the specific cognitive work this assignment requires?"

CRITICAL PRINCIPLES:
- **The learning objective is the boundary.** If the learning objective is "students will construct an argument," then AI-generated arguments bypass the learning, regardless of whether the final product is good. If the learning objective is "students will edit their argument for clarity," AI assistance does not bypass the learning — it supports a stage after the core cognitive work.
- **Blanket AI policies are not justified by this analysis.** The answer is almost never "no AI anywhere" or "AI everywhere." Within any assignment, some components are AI-beneficial, some AI-neutral, some AI-undermining. A defensible policy is component-specific.
- **Process components are more vulnerable than product components.** AI undermines learning most severely when the PROCESS of doing the task is the learning objective. Research, drafting, data analysis, problem construction — these are process objectives. Formatting, spell-checking, citation formatting — these are product objectives where AI assistance is generally neutral.
- **Novelty and transferability are the indicators.** AI is most harmful where students are building new knowledge structures or practising a transfer of learning to a new situation. It is least harmful for rote or clerical tasks. The boundary map should identify which components are knowledge-building and which are not.
- **The tool comparison matters.** For information-gathering tasks, search engines (verifiable citations, current information) and AI chatbots (synthesised inference, no attribution, training cutoff) have fundamentally different epistemic properties. Students should be explicitly directed to the appropriate tool for each information need.

Your task is to generate an AI learning boundary map for:

**Assignment description:** {{assignment_description}}
**Learning objectives:** {{learning_objectives}}

The following optional context may or may not be provided. Use whatever is available; ignore fields marked "not provided."

**Current AI policy:** {{current_ai_policy}} — if not provided, assume no formal policy has been set.
**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the assignment.
**Assessment context:** {{assessment_context}} — if not provided, treat as a formative assessment task.
**Tool comparison needed:** {{tool_comparison_needed}} — if not provided, include tool comparison guidance if the assignment has a research or information-gathering component.

Return your output in this exact format:

## AI Learning Boundary Map: [Assignment Name]

**Assignment:** [Brief description]
**Key learning objectives:** [List]
**Assessment context:** [How this is assessed]

### Objective Analysis

[For each learning objective, a one-paragraph analysis of whether AI assistance supports, is neutral to, or undermines it — with explicit reasoning from the backward design principle]

| Learning Objective | AI Impact | Reasoning |
|---|---|---|
| [Objective] | Supports / Neutral / Undermines | [Why] |

### Component Boundary Map

[Break the assignment into 4-8 components. For each:]

**Component [N]: [Name]**
- **What students do:** [Description]
- **Serves objective:** [Which learning objective]
- **AI boundary:** AI-BENEFICIAL / AI-NEUTRAL / AI-UNDERMINING
- **Reasoning:** [Why this boundary — what cognitive work AI bypasses or supports]
- **Specific policy:** [Exactly what AI use is permitted or restricted for this component]

### AI Policy Recommendations

[Based on the component analysis, a specific, defensible AI use policy for this assignment. Not blanket allow/prohibit — component-specific guidance in plain language for students]

**Recommended policy statement:**
> [The exact wording a teacher could use in an assignment brief]

**Rationale for each restriction:** [Brief, student-accessible rationale for each restricted component — "AI is restricted here because this component develops [specific skill] that requires you to do the cognitive work yourself"]

### Tool Comparison

[If the assignment has information-gathering components — or if tool_comparison_needed is true:]

**For [information component]: Use [search / AI / library] because:**
[Guidance on which tool to use for which information need, with reasoning about the epistemic properties of each tool]

| Task | Best tool | Why |
|---|---|---|
| [Task] | [Tool] | [Epistemic reason] |

### Redesign Suggestions

[3-5 specific modifications to the assignment that strengthen the boundary between AI-assisted and learning-critical components, without fundamentally changing the assignment]

**Suggestion [N]: [Name]**
- **Current design:** [What the assignment currently asks]
- **Modification:** [What to change]
- **Why it helps:** [How this modification makes the learning-critical component more AI-resistant or makes AI assistance more obviously beneficial]

**Self-check before returning output:** Verify that (a) the objective analysis is specific to these learning objectives, not generic, (b) each component boundary is justified by a clear reasoning from the backward design principle, (c) the policy is component-specific rather than blanket, (d) the policy statement is in plain, student-accessible language, and (e) redesign suggestions are practical modifications, not wholesale rewrites.
```

## 示例输出

**情景：** *作业描述：“十年级历史论文：600 词议论文——《凡尔赛条约》是否是二战的主要原因？必须使用至少三位具名历史学家的观点。下周提交。” / 学习目标：“学生将建构基于证据的历史论证；评价相互竞争的史学阐释；恰当选择并部署史料证据；用历史论证的分析语域写作” / 评估情境：“终结性评估——占单元成绩的 30%”*

---

## AI 学习边界映射：《凡尔赛条约》议论文

**作业：** 撰写 600 词议论文，探讨《凡尔赛条约》是否是二战的主要原因
**核心学习目标：** 建构历史论证；评价史学阐释；部署史料证据；使用分析语域写作
**评估情境：** 终结性评估——占单元成绩的 30%

### 目标分析

| 学习目标 | AI 影响 | 推理说明 |
|---|---|---|
| 建构基于证据的历史论证 | 削弱 | 如果由 AI 建构论证，学生练习的是阅读和编辑 AI 文本，而非历史论证。选择立场并为其建立证据支撑的认知工作被绕过了。这是首要学习目标——此处限制 AI 最为关键。 |
| 评价相互竞争的史学阐释 | 削弱 | 对比并评价 Fischer 与 Clark 等历史学家的观点，要求学生理解双方立场、比较证据质量并做出有理有据的判断。由 AI 代劳对比会绕过评价性的认知工作。 |
| 选择并部署史料证据 | 削弱 | 学生选择使用哪些证据并将其嵌入论证属于知识建构。AI 挑选证据会绕过这一过程。但须注意：AI 帮忙找出某位历史学家的著作是否存在（文献索引辅助）属于中性——目标在于证据的**运用**，而非文献检索本身。 |
| 用历史论证的分析语域写作 | 部分削弱 | 掌握新语域需要练习。然而，用 AI 改进学生自己写出的草稿（发展性编辑）与用 AI 直接生成草稿截然不同。前者支持学习，后者削弱学习。 |

### 环节边界图谱

**环节 1：文献调研——识别相关历史学家及其观点**
- **学生做什么：** 调研哪些历史学家写过《凡尔赛条约》作为二战起因的问题，他们的核心论点是什么
- **服务目标：** 评价史学阐释
- **AI 边界：** 附带保留条件的 AI 中性（AI-NEUTRAL）
- **推理说明：** 查明 Fischer 主张了 X 是一项检索任务；理解并评价 Fischer 的论点才是学习任务。AI 可以协助回答“有哪些相关历史学家”——但学生必须亲自阅读并理解这些论点。
- **具体政策：** 你可以使用 AI 识别相关历史学家并获取其立场的简短摘要。但对于你引用的每一位历史学家，你都必须亲自阅读至少一份一手或二手文献。

**环节 2：规划论证提纲**
- **学生做什么：** 确定立场，并为该立场规划基于证据的论证框架
- **服务目标：** 建构历史论证
- **AI 边界：** AI 削弱（AI-UNDERMINING）
- **推理说明：** 论证建构是核心学习目标。由 AI 规划会绕过决定“论证什么”及“如何支撑”的关键认知工作。
- **具体政策：** 论证规划禁止使用 AI。你的提纲必须手写或在无 AI 辅助下完成。

**环节 3：撰写论文初稿**
- **学生做什么：** 用历史写作的分析语域写出完整论证
- **服务目标：** 历史论证与语域表达
- **AI 边界：** AI 削弱（AI-UNDERMINING）
- **推理说明：** 这里是主要学习发生的地方。写作即思考——产出论证的过程就是建构理解的过程。AI 代写会彻底绕过这一过程。
- **具体政策：** 初稿必须由你本人撰写。我们将核查提交文本的原创性。

**环节 4：修改与润色**
- **学生做什么：** 改进草稿——清晰度、结构、论证力度
- **服务目标：** 用分析语域写作（发展编辑阶段）
- **AI 边界：** 附带约束条件的 AI 中性至 AI 受益（AI-NEUTRAL to AI-BENEFICIAL）
- **推理说明：** 一旦学生写出了真正的初稿，使用 AI 识别论证结构中的薄弱点或建议更清晰的措辞属于发展性反馈，而非论证生成。原创思考属于学生本人。
- **具体政策：** 当你有了完整的本人撰写的初稿后，可以向 AI 提问：“你认为我的论证结构有什么薄弱之处？”或“这一段表达清晰吗？”不要让 AI 改写段落——让它指出问题，由你自己修改。

**环节 5：引文格式排版**
- **学生做什么：** 按规范格式编排参考文献与引文
- **服务目标：** 不涉及上述核心学习目标
- **AI 边界：** AI 受益（AI-BENEFICIAL）
- **推理说明：** 引文格式排版是事务性工作，不服务于既定学习目标。AI 辅助在此节省时间而不影响学习。
- **具体政策：** 允许并鼓励使用 AI 引文格式工具。

### AI 政策建议

**推荐政策声明（可直接写入作业说明）：**
> 关于本篇论文，AI 可用于：（1）识别相关历史学家并获取其立场的简短摘要——但对于你引用的每位历史学家，必须亲自阅读至少一份原始或二手资料；（2）对你**自己已经写好**的草稿提供反馈——向它提问“我的论证哪里薄弱？”，而不是“帮我写一个更好的版本”；（3）排版引文格式。AI **不得**用于规划论证、生成初稿或改写论文段落。你的提纲必须手写，初稿必须由你亲自完成。

**每项限制的理据（面向学生）：**
- “禁止用 AI 规划提纲：决定论证什么及如何支撑，正是这篇论文要培养的核心技能。如果由 AI 做决定，你就失去了练习机会。”
- “禁止用 AI 起草正文：亲手写出论证是你建立本单元历史思维的方式。如果由 AI 代写，你就错过了学习本身。”

### 工具对比

| 任务 | 最佳工具 | 原因 |
|---|---|---|
| 查找哪些历史学家研究过凡尔赛条约 | 搜索引擎（Google Scholar、图书馆数据库） | 搜索提供真实、可引用的文献；AI 可能给出真实历史学家姓名，但可能捏造具体论文 |
| 快速了解某位历史学家的核心论点 | AI 聊天机器人（需核实） | AI 适合做快速概览，但在依赖前必须对照真实文献核实摘要 |
| 核实出版日期或文献完整标题 | 图书馆数据库或出版社网站 | AI 可能给出看似合理但错误的书目信息；务必核实 |
| 检查自己的论证结构是否清晰 | AI 聊天机器人 | 对已完成的草稿提供结构反馈是 AI 的良好用例 |

### 重构建议

**建议 1：增加手写提纲提交环节**
- **当前设计：** 学生直接提交成稿论文，无需中间过程件
- **修改方式：** 要求学生在论文截止前一天提交手写论文提纲（核心论点 + 证据大纲）
- **为何有效：** 使 AI 规划更容易被察觉，并改变激励机制——未亲自规划的学生无论如何都必须从头产出提纲

**建议 2：增加“历史学家选用理由”说明栏**
- **当前设计：** 学生直接引用历史学家而无需解释为何选择他们
- **修改方式：** 增加要求：每引用一位历史学家，附带一句话说明“我为什么选择这位历史学家的论点，它为我的论证增添了什么”
- **为何有效：** 这句话如果由 AI 生成很容易显露痕迹——它要求学生清晰表达自己的评价性推理

**建议 3：用教师提供的史料包替代开放检索阶段**
- **当前设计：** 学生完全独立检索文献
- **修改方式：** 为学生提供 4–5 份历史学家节选材料——规定只能使用材料包内的历史学家
- **为何有效：** 完全剥离了开放检索阶段（消除了该环节的 AI 幻觉风险），将所有学习时间聚焦在基于限定史料集的论证与评价上

---

## 已知局限

1. **本技能分析的是“作业设计”，而非“学生行为”。** 有理有据的 AI 政策并不能物理阻止 AI 使用——它能让边界背后的学习理据变得清晰，改变激励结构，并为教师提供有原则的检测与反馈依据。执意全程使用 AI 的学生依然可能这样做。

2. **AI 检测工具并不可靠。** 声称能检测 AI 生成文本的工具存在较高的误报率与漏报率。边界建议不应依赖于可靠检测——而应通过设计，使 AI 的使用要么真正无害，要么在教育上清晰可见。

3. **边界设定具有教育公平层面的影响。** 负担不起私人辅导的学生可能会像使用昂贵私教一样依赖 AI 作为认知脚手架——一刀切的 AI 禁令可能不成比例地使他们处于劣势。教师应考虑对于有明确支持需求的学生，是否在 AI 中性环节给予更宽松的权限。

4. **逆向设计在 AI 边界设定上的具体应用缺乏直接实证检验。** 逆向设计原则（Wiggins & McTighe, 2005）以及认知负荷/胜任力错觉的实证基础在一般学习设计中证据充分。将其具体应用于 AI 边界设定合乎原则但属创新之举——关于何种 AI 边界最能在允许有益使用的同时有效保护学习，目前尚无大量实证研究。
