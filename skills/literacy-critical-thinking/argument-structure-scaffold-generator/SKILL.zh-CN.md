---
# AGENT SKILLS STANDARD FIELDS (v2)
name: argument-structure-scaffold-generator
description: "针对特定主张或问题，使用 Toulmin、PEEL 或 CER 框架生成论证结构支架。适用于跨学科教授议论文或分析性写作时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "literacy-critical-thinking/argument-structure-scaffold-generator"
skill_name: "论证结构支架生成器"
domain: "literacy-critical-thinking"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Toulmin (1958) — The Uses of Argument: claim, data, warrant, backing, qualifier, rebuttal"
  - "Graham & Perin (2007) — Writing Next: effective strategies to improve writing of adolescents"
  - "Andrews (2010) — Argumentation in Higher Education: improving practice through theory and research"
  - "Hillocks (2011) — Teaching Argument Writing, Grades 6–12"
  - "Newell et al. (2011) — Teaching and Learning Argumentative Reading and Writing"
input_schema:
  required:
    - field: "argument_topic"
      type: "string"
      description: "学生正在论证的主张、问题或命题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前的写作能力"
    - field: "scaffold_type"
      type: "string"
      description: "要使用的论证框架——例如 Toulmin、PEEL、主张-证据-推理（CER）、历史论证、平衡论证"
  optional:
    - field: "subject_area"
      type: "string"
      description: "学科语境——不同学科的论证方式不同"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：写作水平、语言水平、具体需求"
    - field: "text_type"
      type: "string"
      description: "最终文本的体裁——例如议论文、演讲稿、信函、辩论提纲"
    - field: "example_evidence"
      type: "string"
      description: "学生可用于构建论证的证据或史料"
output_schema:
  type: "object"
  fields:
    - field: "scaffold"
      type: "object"
      description: "结构化论证支架，包含带标签的板块、各板块提示语以及例示句首"
    - field: "annotated_model"
      type: "string"
      description: "展示支架实际运用的简短批注范例"
    - field: "common_weaknesses"
      type: "array"
      description: "该水平学生在论证中常见的典型薄弱点及支架如何应对"
    - field: "differentiation"
      type: "object"
      description: "对支架的支持与拓展调整方案"
chains_well_with:
  - "disciplinary-writing-scaffold"
  - "critical-thinking-task-designer"
  - "feedback-quality-analyser"
  - "worked-example-fading-designer"
teacher_time: "3 分钟"
tags: ["argument", "writing", "Toulmin", "PEEL", "scaffold", "critical-thinking"]
---

# 论证结构支架生成器

## 本技能的作用

生成一份针对特定体裁的论证支架，精准匹配学生水平、学科门类以及所请求的论证框架。该支架包含带标签的结构板块、每个板块的引导提示语、例示句首以及展示支架实际运用的批注范例。不同学科的论证方式各不相同——科学的“主张-证据-推理（CER）”论证在结构要求上不同于历史论证或文学分析——本技能生成的支架反映这些学科差异，而不是套用千篇一律的“通用作文结构”。AI 在此尤为有价值，因为有效的论证支架必须同时编码论证形式的底层逻辑、为较弱写作者提供足够引导而不束缚较强写作者，并体现特定学科的写作规范——这项任务需要兼备写作教学法专长与学科知识。

## 循证基础

Toulmin (1958) 提出了论证结构的基础模型：主张（claim，你在论证什么）、数据（data，支持主张的证据）、理据（warrant，连接数据与主张的推理）、支撑（backing，对理据的支持）、限定（qualifier，对主张的限制条件）以及反驳（rebuttal，回应反方观点）。虽然 Toulmin 完整模型对低龄学生过于复杂，但其底层逻辑——论证需要主张、证据、推理以及对反方立场的承认——支撑着所有有效的论证支架。Graham & Perin (2007) 在其《Writing Next》综述中将显性教授写作策略与文本结构列为影响力最高的青少年写作干预措施之一（效应量 0.82），其中论证结构教学尤为有效。Andrews (2010) 证明，论证技能不会自然发展——必须通过让论证组成部分可见的结构化框架进行显性教学。Hillocks (2011) 表明，有效的论证教学要求学生理解每个组成部分的“功能”（为什么证据重要、为什么反方论证是强化而非削弱论点），而不仅仅是记住顺序。Newell 等 (2011) 发现，当论证教学嵌入学科语境中而非作为通用技能孤立教授时，效果最佳。

## 输入模式

教师必须提供：
- **Argument topic（论证主题）：** 主张、问题或命题。*例如："Should school uniforms be compulsory?" / "Was the Treaty of Versailles the main cause of World War II?" / "Does the evidence support the conclusion that increasing temperature increases enzyme activity?"*
- **Student level（学生水平）：** 年级与写作水平。*例如："Year 9, can write paragraphs but struggle to structure a whole argument" / "Year 12, competent essay writers refining analytical depth"*
- **Scaffold type（支架类型）：** 论证框架。*例如："Toulmin" / "PEEL" / "Claim-Evidence-Reasoning (CER)" / "Historical argument" / "Balanced argument"*

可选（如上下文引擎可用则自动注入）：
- **Subject area（学科领域）：** 学科语境
- **Student profiles（学生档案）：** 写作水平、语言水平、具体需求
- **Text type（文本类型）：** 最终文本体裁（论文、演讲、信函、辩论提纲）
- **Example evidence（示例证据）：** 学生可用的史料或证据

## Prompt

```
You are an expert in argumentation pedagogy and writing instruction, with deep knowledge of Toulmin's (1958) argument model, Graham & Perin's (2007) Writing Next evidence synthesis, and Hillocks' (2011) approach to teaching argument writing. You understand that argument structure varies by discipline — a scientific argument is not structured like a historical argument or a persuasive speech — and that effective scaffolds make the FUNCTION of each component visible, not just its position.

Your task is to generate an argument scaffold for:

**Argument topic:** {{argument_topic}}
**Student level:** {{student_level}}
**Scaffold type:** {{scaffold_type}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer the most likely discipline from the argument topic and generate a discipline-appropriate scaffold.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class where some students can structure paragraphs but struggle with whole-text argument organisation.
**Text type:** {{text_type}} — if not provided, assume an academic essay format.
**Example evidence:** {{example_evidence}} — if not provided, generate 2–3 plausible pieces of evidence students might use, to demonstrate how the scaffold works.

Apply these evidence-based principles:

1. **Make the function of each component explicit (Hillocks, 2011):**
   - Each section of the scaffold should explain WHY it's there, not just what goes in it.
   - Students who understand that counter-arguments STRENGTHEN their position (by showing they've considered alternatives) write better arguments than students who think counter-arguments weaken their position.
   - Label each section with its rhetorical function: "This section shows you've considered the opposing view — which makes your argument MORE convincing, not less."

2. **Match the scaffold to the argument framework requested:**
   - **Toulmin:** Claim → Data → Warrant → Qualifier → Rebuttal → Backing
   - **PEEL:** Point → Evidence → Explain → Link
   - **CER (Claim-Evidence-Reasoning):** Claim → Evidence → Reasoning (explicit connection)
   - **Historical argument:** Context → Claim → Evidence (primary/secondary) → Analysis → Counter-argument → Judgement
   - **Balanced argument:** Introduction (both sides) → Arguments for → Arguments against → Evaluation → Conclusion with justified position
   - Adapt the framework to the student level — younger students may need a simplified version.

3. **Provide sentence starters that teach, not just fill (Graham & Perin, 2007):**
   - Sentence starters should model the kind of thinking each section requires, not just provide grammatical scaffolding.
   - Good: "The strongest evidence for this claim is... because it shows..." (teaches evidence selection + reasoning)
   - Bad: "Firstly... Secondly... Thirdly..." (teaches sequencing but not argumentation)

4. **Discipline-specific conventions (Newell et al., 2011):**
   - Science: evidence is empirical data; reasoning connects data to scientific principles.
   - History: evidence is from primary/secondary sources; analysis considers provenance and reliability.
   - English: evidence is textual quotation; analysis considers authorial intent and effect.
   - General: evidence can be facts, statistics, examples, expert opinion; reasoning connects to values or principles.

5. **Include an annotated model (Andrews, 2010):**
   - Show a brief example of the scaffold in use — a short, annotated argument that labels each component.
   - The model should be good but not perfect — showing a realistic student-level response, not a professional essay.

Return your output in this exact format:

## Argument Scaffold: [Scaffold Type] — [Topic]

**For:** [Student level]
**Framework:** [Scaffold type with brief explanation]
**Text type:** [Essay/speech/letter/etc.]

### The Scaffold

[The complete scaffold with labelled sections, guiding prompts for each section, rhetorical function labels, and sentence starters]

### Annotated Model

[A brief example (one key paragraph or section) showing the scaffold in use, with annotations labelling each component]

### Common Weaknesses at This Level

[3–4 typical weaknesses in student arguments at this level, and how the scaffold specifically addresses each one]

### Differentiation

**Support:** [How to simplify the scaffold for struggling writers]
**Extension:** [How to challenge stronger writers beyond the scaffold]

**Self-check before returning output:** Verify that (a) each section explains its rhetorical FUNCTION, not just what goes in it, (b) sentence starters model argumentative thinking, not just grammatical structure, (c) the scaffold matches the requested framework, (d) the scaffold is appropriate for the stated student level, (e) the annotated model is realistic for students at this level, and (f) disciplinary conventions are reflected if a subject area is specified or inferred.
```

## 示例输出

**场景：** *Argument topic: "Was the Treaty of Versailles the main cause of World War II?" / Student level: "Year 10, can write structured paragraphs but tend to narrate rather than argue — they tell the story of the Treaty rather than evaluating its significance" / Scaffold type: "Historical argument" / Subject area: "History"*

---

## 论证支架：历史论证——《凡尔赛条约》是第二次世界大战的主要原因吗？

**适用对象：** 十年级历史
**框架：** 历史论证（背景语境 → 主张 → 证据与分析 → 反方论证 → 综合评判）
**文本类型：** 分析性议论文

### 论证支架

**第 1 部分：背景语境（1 段）**
*功能：在开始论证“之前”向考官证明你理解历史处境。这不是“引言套话”，而是证明你能把问题置于其历史语境之中。*

铺设场景：《凡尔赛条约》是什么？何时签署？核心条款有哪些？

句首提示：
- "The Treaty of Versailles, signed in [date], imposed [key terms] on Germany following..."
- "The treaty was significant because it..."
- "To evaluate whether the treaty was the MAIN cause, we must consider..."

**重要提示：** 保持简短。背景不是论证本身——它只是地基。写一段即可，不要流水账式地叙述条约的全部历史。

---

**第 2 部分：你的主张（背景段末尾的 1–2 句话）**
*功能：告诉读者你的“论点”——你将捍卫的立场。主张不是话题（"This essay is about the Treaty of Versailles"），而是一个立场（"The Treaty of Versailles was the most significant cause because..."）。*

句首提示：
- "This essay will argue that the Treaty of Versailles was / was not the main cause of World War II because..."
- "While the Treaty contributed to the outbreak of war, it was [other factor] that was the decisive cause because..."

**重要提示：** 强有力的主张包含 "because"——它不仅陈述立场，还指明了推理方向。

---

**第 3 部分：论证段落——证据与分析（2–3 段）**
*功能：这是你论证的核心。每一段呈现一条证据并“分析”它——即解释它说明了什么以及为什么支持你的主张。叙述发生了什么不是分析；解释“为什么”它重要才是分析。*

对于每个论证段：

**证据：** 有什么具体证据支持你的主张？
- "The [specific term/event/statistic] demonstrates that..."
- "Source [X] shows that..."
- "According to [historian/primary source]..."

**分析：** 这条证据“说明了什么”？为什么它支持你的主张？这是绝大多数学生丢分的地方——他们列出了证据，却不解释其重要性。
- "This is significant because it shows that..."
- "This supports the argument that the Treaty was the main cause because..."
- "This evidence suggests that without the Treaty, [consequence] would/would not have occurred because..."

**重要提示：** 每一条证据都需要分析。模式是：证据 → "This shows..." → "This matters because..." 如果你只写了一个事实却不解释它为何重要，你就是在叙事，而非论证。

---

**第 4 部分：反方论证（1 段）**
*功能：展示你已经考虑了相反观点。这“不会”削弱你的论证——反而会“强化”它。考官奖励那些能考虑替代解释并随后解释为何自己立场依然更强的学生。忽略反方论证会让你的文章显得片面且天真。*

句首提示：
- "However, some historians argue that [alternative cause] was more significant because..."
- "It could be argued that [counter-evidence/counter-interpretation]..."
- "While this is a valid point, the Treaty remains the more significant cause because..."

**重要提示：** 反方论证段包含三个部分：(1) 公平呈现相反观点，(2) 承认其中合理之处，(3) 解释为何你原本的主张依然更强。不要立一个稻草人靶子来轻易打倒——要回应最强的反方论证。

---

**第 5 部分：综合评判（1 段）**
*功能：你最终的、经过权衡的评判。这“不是”对前文已说内容的简单复述，而是你的“评价”——权衡各方证据并得出结论。最好的评判会使用程度副词与限定表达："the most significant"、"a contributing factor but not the primary cause"、"necessary but not sufficient"。*

句首提示：
- "In conclusion, the evidence suggests that the Treaty of Versailles was [the main / a significant but not the main / a contributing] cause because..."
- "While [other factors] also contributed, the Treaty was the most significant because without it, [consequence]..."
- "Ultimately, [factor] was the decisive cause, though the Treaty created the conditions that made [consequence] possible."

**重要提示：** 你的评判应当让人感觉是从你的证据中自然“推演”出来的，而不是事先武断决定的。如果你的证据很强但反方论证也很强，请承认这种复杂性："The Treaty was the most significant single cause, though it operated alongside other factors that amplified its effects."

### 批注范例

*展示支架实际运用的一个论证段：*

**[证据]** The Treaty's "war guilt" clause (Article 231) forced Germany to accept sole responsibility for the war, while reparations of £6.6 billion crippled the German economy throughout the 1920s. **[分析——它说明了什么]** This is significant because it created widespread resentment among the German population, who saw the terms as unjust and humiliating. **[分析——为何对主张重要]** This resentment was directly exploited by Hitler and the Nazi Party, who promised to overturn the Treaty and restore German pride. Without the Treaty's harshness, the political conditions that enabled Hitler's rise would not have existed. **[回扣主张]** This supports the argument that the Treaty was the main cause, because it created the specific grievances that the Nazi movement channelled into popular support for aggressive expansionism.

*说明：本段遵循“证据 → This is significant because... → This supports the argument because...”的模式。证据之后的每一句话都在做分析工作——而不仅仅是堆砌更多事实。*

### 该水平常见薄弱点

1. **以叙代议（Narrating instead of arguing）。** 十年级学生常写："The Treaty of Versailles said that Germany had to pay reparations. Then in 1923 the French invaded the Ruhr..."——这只是在讲故事，没有评估重要性。本支架通过在每条证据后强制要求分析（"This is significant because..."）来解决这一问题，迫使学生进行评价而非叙述。

2. **没有反方论证，或只有敷衍的反方论证。** 学生要么无视相反观点，要么写一句 "Some people disagree but they are wrong." 本支架明确教授反方论证能够强化文章，并提供三段式结构（公平呈现 → 承认合理性 → 解释为何己方主张更强）。

3. **结论只是重复引言。** 本支架将“综合评判”与“总结复述”区分开来，并提供示范评价性语言（"the most significant"、"necessary but not sufficient"）而非总结套话（"In this essay I have discussed..."）的句首提示。

4. **没有 "because" 的主张。** 学生常写 "The Treaty of Versailles caused World War II"——有立场无推理。本支架坚持主张必须包含 "because"，迫使学生从一开始就亮明推理逻辑。

### 分层教学

**支持（针对在段落结构上遇到困难的学生）：**
- 缩减至 3 个部分：主张 → 一个证据段 → 评判。在基础结构稳固前暂不要求反方论证。
- 提供部分填好的支架，证据已预先选好——学生的任务是写出分析（"This is significant because..."）。
- 直接将批注范例作为模板："Write your paragraph following exactly this pattern."

**拓展（针对自信的写作者）：**
- 增加要求：回应“两个”反方论证而非一个——并对它们进行权衡比较。
- 完全撤除句首提示——挑战学生自主建构分析性语言。
- 要求介入史学争论："Historian A argues X, while Historian B argues Y. Evaluate which interpretation is better supported by the evidence."
- 加入（来自 Toulmin 模型的）“限定词”要求："To what extent was the Treaty the main cause?"——迫使学生提出细微、有限定的主张，而非绝对化立场。

---

## 已知局限性

1. **支架教授的是结构，而非内容知识。** 如果学生历史知识匮乏，即使完美套用支架也依然会写出薄弱的论证。支架能确保论证组织良好、结构具分析性，但无法弥补学科知识的不足。教师在要求学生论证前，应确保学生已具备足够的学科知识。

2. **支架可能变成拐杖。** 如果学生总是依赖句首提示和带标签的板块写作，撤掉支架后他们可能会无所适从。支架应当渐进撤除——早期练习时明确使用，随着学生内化结构逐步撤走。可串联使用“样例渐隐设计师（Worked Example Fading Designer）”来规划支架撤除。

3. **不同学科的论证规范差异比支架所能完全捕捉的更为细微。** 历史论文、科学报告与哲学论证拥有根本不同的证据标准、推理模式与修辞规范。本技能生成契合学科的支架，但教师仍应结合自身学科的具体要求审视产出并在需要时加以修改。
