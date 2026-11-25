---
# AGENT SKILLS STANDARD FIELDS (v2)
name: prompt-literacy-sequence-designer
description: "设计教授提示词质量的学习序列——通过对比模糊提示词与精细提示词，展示具体性与语境如何改变 AI 输出。适用于学生使用 AI 却不明白为何输出质量参差不齐时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-literacy/prompt-literacy-sequence-designer"
skill_name: "提示词素养序列设计器"
domain: "ai-literacy"
version: "1.0"
contributor: "Gareth Manning"
evidence_strength: "low-moderate"
evidence_sources:
  - "Brown et al. (2020) — Language Models are Few-Shot Learners (GPT-3 few-shot prompting)"
  - "Liu et al. (2023) — Pre-Train, Prompt, and Predict: a systematic survey of prompting methods in NLP"
  - "Reynolds & McDonell (2021) — Prompt programming for large language models: beyond the few-shot paradigm"
  - "Rosenshine (2012) — Principles of instruction (modelling and guided practice framework)"
  - "Willingham (2007) — Critical thinking: why is it so hard to teach? (specificity in task design)"
input_schema:
  required:
    - field: "subject_area"
      type: "string"
      description: "提示词示例的学科情境——影响什么是良好的具体性"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前 AI 使用习惯"
    - field: "ai_task_type"
      type: "string"
      description: "学生用 AI 做什么——调研、写作辅助、原理解释、解题、复习"
  optional:
    - field: "prompt_literacy_focus"
      type: "string"
      description: "重点强调哪个提示词维度——语境具体性、约束提供、格式规范、角色/人设，还是迭代优化"
    - field: "common_student_prompts"
      type: "string"
      description: "学生通常使用的模糊提示词示例——有助于生成真实的前后对比"
    - field: "time_available"
      type: "string"
      description: "可用于提示词素养序列的时长"
output_schema:
  type: "object"
  fields:
    - field: "prompt_anatomy"
      type: "object"
      description: "拆解有效提示词的构成要素——语境、任务、约束、格式、角色——并附学科特定示例"
    - field: "compare_contrast_sequence"
      type: "object"
      description: "结构化对比活动：模糊提示词 vs. 精细提示词，附带引导学生分析变化及输出质量提升原因的指南"
    - field: "prompt_rewriting_activity"
      type: "object"
      description: "学生活动：拿到薄弱提示词 → 分析缺失要素 → 改写 → 对比输出"
    - field: "pricing_exercise"
      type: "object"
      description: "“定价练习（Pricing Exercise）”改编版：展示逐步添加约束如何将无语境的 AI 回答转化为真正有用的回答"
    - field: "prompt_principles_summary"
      type: "object"
      description: "面向学生的简明提示词原则摘要（附示例），可用作参考卡片"
chains_well_with:
  - "ai-output-critical-audit-designer"
  - "metacognitive-monitoring-ai-contexts"
  - "explicit-instruction-sequence-builder"
teacher_time: "4 分钟"
tags: ["AI-literacy", "prompt-engineering", "prompt-literacy", "specificity", "AI-use", "context", "constraints"]
---

# 提示词素养序列设计器

## 本技能的作用

设计一套结构化学习序列，教导学生为什么提示词质量决定了 AI 输出质量——以及哪些具体的提示词动作能产出更有用、更准确且贴合语境的回应。该序列采用对比分析结构：学生针对同一问题分别运行模糊提示词和精细提示词，分析输出质量的差异，并抽象提炼出原则。核心洞见在于：AI 会用统计上最常见的回应来填补缺失的语境——因此，没有提供受众、目的、学科或约束条件的提示词，只会得到针对“平均情况”校准的答案，而非针对学生具体情境的答案。序列以“定价练习（The Pricing Exercise，Kharbach, 2026）”作为锚点活动：学生拿一个无语境的 AI 回答（“我该为某项服务收多少钱？”）并迭代添加约束（服务类型、地点、目标市场、质量水平），实时观察具体性如何将泛泛无用的输出转化为真正有用的方案。该序列教授五个提示词维度：语境（我是谁，我在做什么？）、任务（我到底想要什么？）、约束（适用哪些限制？）、格式（输出应如何组织？）以及角色（AI 应扮演什么角色？）。提示词素养是有效使用 AI 的前提，也是 AI 输出评估技能的直接互补。

## 实证基础

Brown 等人（2020）在 GPT-3 论文中实证证明，提示词的构建方式会显著影响模型输出质量——提示词中的少样本示例（few-shot examples，向 AI 展示良好回复的样子）产出的结果大幅优于零样本提示（zero-shot，无示例）。这是“提示词设计并非随意为之”的奠基性证据。Liu 等人（2023）对提示词方法进行了系统综述，记录了不同提示结构（思维链、角色扮演、指令遵循、少样本）如何影响跨任务输出质量。他们的综述确立了提示词工程是一项具有可学习原则的技能，而非全凭运气。Reynolds & McDonell（2021）将其拓展至“元提示（metaprompts）”概念——显性指示 AI 如何推理、组织回复或扮演角色的提示词——表明这些结构要素能显著提升输出质量。这三项来源为提示词素养教学提供了 AI 领域的实证基础。然而，关于向学生**教授**提示词素养的教学法实证基础目前还非常有限——这是教育研究的前沿领域。其余文献支撑了本序列的**教学设计**：Rosenshine（2012）提供了此处使用的“示范 → 引导练习 → 独立练习”结构；Willingham（2007）提供了领域特定性论据（历史课上的好提示词不同于数学课上的好提示词），为分学科开展提示词素养教学提供了依据。

## 输入规范

教师必须提供：
- **学科领域（Subject area）：** 学科情境。*例如：“历史” / “生物” / “英语语言与文学” / “数学”*
- **学生水平（Student level）：** 年级与当前 AI 使用情况。*例如：“十年级，经常用 ChatGPT 写作业但总是得到泛泛无用的输出” / “十二年级，用 AI 做调研和草稿写作但未接受过显性提示词策略教学”*
- **AI 任务类型（AI task type）：** 学生用 AI 做什么。*例如：“调研：获取论文主题的背景信息” / “写作：生成段落草稿并获取反馈” / “解释：让 AI 解释自己漏掉的概念”*

可选项（如可用则由上下文引擎注入）：
- **提示词素养焦点（Prompt literacy focus）：** 强调哪个提示词维度
- **常见学生提示词（Common student prompts）：** 学生当前如何向 AI 提问的真实示例
- **可用时间（Time available）：** 序列持续时长

## 提示词（Prompt）

```
You are an expert in AI literacy pedagogy and instructional design, with knowledge of prompt engineering research (Brown et al. 2020; Liu et al. 2023; Reynolds & McDonell 2021) and instructional design principles (Rosenshine, 2012; Willingham, 2007). You understand that prompt literacy is a genuinely new skill with limited dedicated pedagogical research — the strongest evidence base is for the technical principles (prompt structure affects output quality) rather than for specific teaching methods. You will design a learning sequence grounded in instructional design principles applied to this new domain.

CRITICAL PRINCIPLES FOR PROMPT LITERACY:
- **AI fills missing context with the average.** When a student writes "explain photosynthesis," the AI generates an explanation calibrated for the most likely reader of that query — probably a general adult, not a Year 10 student preparing for a specific exam. Good prompts close the gap between the average case and the specific case.
- **Constraints are productive, not restrictive.** Most students think a prompt is "finished" when they've stated the task. Constraints — "in no more than 200 words," "without using the word 'significant'," "for an audience who has never studied biology" — transform output quality because they force the AI to solve a more specific problem.
- **Prompt literacy is discipline-specific.** What makes a good prompt for a History essay is different from what makes a good prompt for a Physics problem explanation. The principles are the same; the application differs.
- **Compare-contrast is the core learning mechanism.** Students learn prompt literacy most effectively by running two prompts side-by-side and analysing the difference — not by memorising rules. The rules become intelligible through contrast.
- **Prompt improvement is iterative, not one-shot.** Expert AI users refine their prompts based on the output they receive. Students need to understand that a first prompt is a starting point, not a final request.

Your task is to design a prompt literacy learning sequence for:

**Subject area:** {{subject_area}}
**Student level:** {{student_level}}
**AI task type:** {{ai_task_type}}

The following optional context may or may not be provided. Use whatever is available; ignore fields marked "not provided."

**Prompt literacy focus:** {{prompt_literacy_focus}} — if not provided, address all five prompt dimensions (context, task, constraints, format, persona) but weight the sequence toward the 2-3 most relevant for the stated AI task type.
**Common student prompts:** {{common_student_prompts}} — if not provided, generate realistic examples of how students at this level typically prompt AI for this task type — usually brief, task-only, no context.
**Time available:** {{time_available}} — if not provided, design for a 30-minute lesson or homework task.

Return your output in this exact format:

## Prompt Literacy Sequence: [Subject/Task Type]

**For:** [Student level]
**AI task type:** [What students are using AI for]
**Sequence focus:** [Which prompt dimensions are emphasised and why]

### Prompt Anatomy

[The five prompt dimensions with subject-specific examples for each:]

**1. Context:** [What context is — who I am, what I'm doing, why. Subject-specific example of no context vs. good context]
**2. Task:** [What task specificity means beyond just "explain X." Subject-specific example]
**3. Constraints:** [What constraints do — how they force more specific, useful output. Subject-specific example]
**4. Format:** [What format specification achieves. Subject-specific example]
**5. Persona:** [What role assignment achieves. Subject-specific example]

### Compare-Contrast Activity

**Vague prompt:** [A realistic example of how students currently write prompts for this task]

**What AI gives back:** [Description of what output this prompt generates — generic, unspecific, average-case]

**Refined prompt:** [The same task with all relevant dimensions added]

**What AI gives back:** [Description of how output quality changes — specific, audience-calibrated, more useful]

**Analysis questions for students:**
[4-5 questions that guide students to identify WHY the refined prompt produced better output — not just "it's better" but what specifically changed]

### The Pricing Exercise

[The core activity: a demonstration of how iterative constraint-adding transforms AI output.]

**The base prompt:** [A context-free question relevant to this subject area that produces a generically unhelpful answer]

**Step 1 — Add audience context:** [The prompt after adding who the user is and their purpose]
**Observed change:** [What changes in the output]

**Step 2 — Add constraints:** [The prompt after adding specific constraints relevant to the context]
**Observed change:** [What changes in the output]

**Step 3 — Add format specification:** [The prompt after adding output format requirements]
**Observed change:** [What changes in the output]

**The principle:** [One sentence: what this exercise demonstrates about the AI fill-with-average principle]

### Prompt Rewriting Activity

**Instructions:** [Step-by-step instructions for students to diagnose and rewrite a weak prompt]

**Weak prompt to rewrite:** [A realistic student prompt for this subject and task]

**Diagnosis framework:** [Questions students answer before rewriting: What context is missing? What constraints would improve this? What format would be most useful? What persona would help?]

**Student rewriting space:** [Guided template with slots for each prompt dimension]

**Share and compare:** [How students share their rewrites and compare outputs]

### Prompt Principles Summary Card

[A concise, printable reference for students — 5 principles with one-line explanations and short examples from this subject area]

**Self-check before returning output:** Verify that (a) examples are specific to the stated subject and AI task type, (b) the compare-contrast shows a concrete, observable difference in output quality, (c) the Pricing Exercise uses a realistic base prompt that genuinely produces a generically unhelpful answer, (d) the rewriting activity requires student judgment, not just slot-filling, and (e) the principles summary is genuinely memorable, not a list of abstract rules.
```

## 示例输出

**情景：** *学科领域：“历史” / 学生水平：“十一年级，经常使用 ChatGPT 辅助写论文，但总是得到不符合具体考试要求的泛泛输出” / AI 任务类型：“写作：寻求论文论点与段落结构帮助” / 常见学生提示词：“帮我写一篇关于一战起因的作文” / “帮我写一段关于《凡尔赛条约》的话”*

---

## 提示词素养序列：历史论文写作（十一年级）

**适用对象：** 十一年级历史，经常使用 AI 但常得泛泛输出的学生
**AI 任务类型：** 论文论点与段落结构辅助
**序列焦点：** 语境（紧扣考试要求）与约束（论证结构、证据要求、字数限制）——这两个维度在此用例中带来的质量跃升最大

### 提示词解剖

**1. 语境（Context）：** 没有语境时，AI 会面向一战论文的“平均读者”——普通成年人——来写作。*无语境：*“帮我写一段关于《凡尔赛条约》的话。”*有语境：*“我是一名英国十一年级学生，正在撰写 AQA GCSE 历史论文。我需要论证《凡尔赛条约》是第二次世界大战最重要的起因。”

**2. 任务（Task）：** 光说主题不够——要说明你需要建构的具体论点。*模糊任务：*“解释《凡尔赛条约》。”*具体任务：*“解释《凡尔赛条约》的经济条款如何加剧了 20 世纪 20 年代德国的政治动荡。”

**3. 约束（Constraints）：** 约束把 AI 论文变成可用的段落。*无约束：* 你会得到 500 词以上任意风格的文本。*有约束：*“约 120 词，按‘主张-证据-分析-回扣论点’结构组织”——你得到的是真正能用的内容。

**4. 格式（Format）：** 明确指定结构。“使用 PEEL 结构（Point 观点、Evidence 证据、Explanation 解释、Link 联系）”或“写成可供我自己展开的要点，而不是完整段落”——这会产生截然不同且更有用的输出。

**5. 角色（Persona）：** “扮演一名严格的 GCSE 历史考官”产出的反馈，不同于不指定角色。“扮演比我高一年级且拿到满分的高分学长”则会改变语言语域。

### 对比分析活动

**模糊提示词：** “帮我写一段关于《凡尔赛条约》的论文段落”

**AI 返回的内容：** 一段 200 词的泛泛介绍，解释了《凡尔赛条约》是什么、有哪些条款，以及它“在德国引起了怨恨”。它没有具体论点，没有 GCSE 考试结构，得分会很低，因为它在描述而非分析。

**精细提示词：** “我正在写一篇 GCSE 历史论文，论证《凡尔赛条约》是纳粹崛起的最重要原因。我需要一段结构良好的段落（约 120 词），采用 PEEL 格式（观点、证据、解释、联系），并至少使用条约条款中的一条具体证据。重点聚焦经济后果，而非领土后果。”

**AI 返回的内容：** 一段 120 词的段落，以清晰的历史论点开篇，使用具体赔款数字（66 亿英镑）作为证据，解释机制（经济动荡 → 失业 → 极端主义），并显性回扣关于纳粹崛起的论文中心论点。结构严密、贴合考试、立即可用。

**给学生的分析问题：**
- “在精细提示词中我增加了哪些模糊提示词里缺失的信息？把它们列出来。”
- “为什么指定‘经济后果’而不是‘领土后果’改变了 AI 写出的内容？”
- “AI 产出了 PEEL 结构，因为我要求了它。如果我没指定格式会发生什么？”
- “如果 AI 的第一版输出很泛泛，那是 AI 的错还是提示词的错？这说明了什么？”
- “你会如何改写这个精细提示词，以便为同一篇论文生成另一段内容？”

### 定价练习（The Pricing Exercise）

**基础提示词：** “我应该用什么例子来支撑我的历史论文论点？”

**第 1 步——添加受众与语境：** “我正在写一篇十一年级 GCSE 历史论文，探讨《凡尔赛条约》是否是纳粹崛起的主要原因。我应该用什么例子来支撑这一论点？” → 观察到的变化：AI 现在生成与魏玛德国和纳粹崛起相关的例子，而非随机历史案例。

**第 2 步——添加约束：** “……我应该使用哪 3 条具体证据？每一条都必须是带有日期的事实、统计数据或具名事件。” → 观察到的变化：AI 产出三条简明、具体、可标注日期的证据，而不是笼统的主题清单。

**第 3 步——添加格式规范：** “……按以下格式呈现每条证据：【证据】——【为什么这能支撑我的论点】。” → 观察到的变化：AI 现在产出一份结构化、立即可用的参考工具，而非流水账散文。

**核心原则：** AI 从平均情况出发；你添加的每一个约束都会把输出拉向你的具体情境。

### 提示词改写活动

**操作说明：**
1. 阅读下方的薄弱提示词。
2. 用诊断框架中的四个问题对其进行诊断。
3. 用模板改写它——不要只是把它拉长，而是让每一个维度更具体。
4. 与同伴对比你的改写版本。

**待改写的薄弱提示词：** “为我的论文解释第一次世界大战的起因。”

**诊断框架：**
- 缺失了什么语境？（你是谁？这是为哪项考试/任务准备的？你在建构什么论点？）
- 哪些约束能改进它？（字数限制？聚焦哪些具体起因？排除哪些起因？）
- 哪种格式最有用？（清单？PEEL 段落？用于规划的要点？）
- 什么角色设定会有帮助？（给反馈的考官？解释学术争论的历史学家？）

**学生改写模板：**
“我是【语境：你是谁，这项任务用于什么】。我需要【具体任务：你到底想要什么，而不仅仅是主题】。请【约束：包含/排除什么、大致篇幅、具体视角】。请将你的回复格式化为【格式：你想要的结构】。【可选：以【角色】的身份来回答】。”

**分享与对比：** 两人一组，双方分别运行各自改写后的提示词并对比输出。讨论：哪份改写产出了更有用的回复？五个维度中哪一个带来了最大差异？你会在同伴的改写基础上补充什么？

### 提示词原则速查卡

1. **先给语境。** 告诉 AI 你是谁、什么学科/年级以及输出作何用途。没有语境，AI 的回答不针对任何人。
2. **明确具体任务。** “解释 X”很少够用。说明你需要回答的具体论点、视角或问题。
3. **添加约束。** 字数上限、必备证据、排除做法——约束倒逼出具体且有用的输出。
4. **指定格式。** PEEL、要点列表、编号清单、对话——花 5 秒说明结构，能省下大量修改时间。
5. **迭代微调，而非推倒重来。** 如果第一版输出差强人意，回复它：“不错，但【具体问题】。请修改【具体要素】。”迭代比从零重写更快。

---

## 已知局限

1. **向学生教授提示词素养的实证基础非常有限。** 关于提示词工程的研究（Brown et al., 2020; Liu et al., 2023; Reynolds & McDonell, 2021）记录了提示结构会影响输出质量——但并未研究教授这一技能的教学法。本序列将成熟的教学设计原则（对比分析、示范、引导练习）应用于一个前沿领域。教师应将其视为合乎原则但尚属探索性的方案。

2. **随着 AI 模型进步，提示词素养的保质期较短。** 当前模型需要显性语境与约束，因为它们会用统计平均值填补缺失信息。未来模型可能更擅长推断语境，使部分提示策略过时。底层原则（清晰、具体的沟通比模糊请求产出更好结果）不太可能过时；具体技巧则可能演变。

3. **教授提示词素养可能增加对 AI 的依赖。** 学会写出更好提示词的学生会获得更有用的 AI 输出——这可能会削弱他们发展独立技能的动力。本技能应始终与 `ai-output-critical-audit-designer` 和 `metacognitive-monitoring-ai-contexts` 配对使用，确保提示词素养成为批判性 AI 素养框架的一部分，而非纯粹的效率优化工具。

4. **提示词结果具有概率性，而非确定性。** 同一个提示词在不同次运行中可能产出不同结果。对比分析活动应承认这一点——学生可能需要运行提示词 2–3 次才能看清稳定模式，且“精细提示词总是更好”并不完全准确（它通常在符合原则的维度上更好，但并非每次绝对）。
