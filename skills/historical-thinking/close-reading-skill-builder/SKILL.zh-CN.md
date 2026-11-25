---
# AGENT SKILLS STANDARD FIELDS (v2)
name: close-reading-skill-builder
description: "培养学生精读历史文献的能力——关注用词选择、语气与修辞作为作者视角的证据。适用于学生只概括史料内容而不分析语言时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/close-reading-skill-builder"
skill_name: "历史文献精读技能构建器"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "strong"
evidence_sources:
  - "Wineburg (1991) — Historical problem solving: cognitive processes in the evaluation of documentary and pictorial evidence"
  - "Wineburg (1998) — Reading Abraham Lincoln: an expert/expert study in historical cognition"
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg & Reisman (2015) — Disciplinary literacy in history: a toolkit for digital citizenship"
  - "Wineburg, Martin & Monte-Sano (2011) — Reading like a historian: teaching literacy in middle and high school history classrooms"
  - "Leinhardt & Young (1996) — Two texts, three readers: distance and expertise in reading history"
input_schema:
  required:
    - field: "historical_topic"
      type: "string"
      description: "学生正在调查的历史主题、时期或问题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前精读历史文本的经验水平"
    - field: "current_challenge"
      type: "string"
      description: "学生目前在精读历史文献时做了什么或没做到什么——表明精读能力尚未发展起来的可观察行为"
  optional:
    - field: "source_type"
      type: "string"
      description: "历史史料类型——例如演讲、信件、证言、公告、日记、报纸社论、条约、政治漫画"
    - field: "available_documents"
      type: "string"
      description: "学生将使用的具体文献描述"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架"
    - field: "prior_instruction"
      type: "string"
      description: "学生已经接受过的精读教学——包括语文/英语课上的文学精读"
output_schema:
  type: "object"
  fields:
    - field: "close_reading_progression"
      type: "object"
      description: "针对该年龄段学生，精读在初学、发展中和熟练水平上的表现——附区分“概括内容”与“将语言作为视角证据分析”的可观察指标"
    - field: "explicit_instruction_sequence"
      type: "object"
      description: "用指定史料类型教授精读的三段式序列（示范 → 引导练习 → 独立练习），包含展示专家读者如何将用词、语气和修辞策略作为证据的教师出声思维脚本"
    - field: "language_analysis_prompts"
      type: "array"
      description: "针对史料类型的提示语，引导学生关注语言如何揭示作者的视角、目的与可靠性——已按发展水平校准"
    - field: "common_failure_patterns"
      type: "array"
      description: "该水平学生在精读时通常失败的具体模式——附每项的针对性教学应对"
    - field: "assessment_indicators"
      type: "object"
      description: "学生正在将精读发展为分析性实践的可观察迹象——讨论中听什么、书面作业中看什么"
chains_well_with:
  - "sourcing-skill-builder"
  - "contextualisation-skill-builder"
  - "corroboration-skill-builder"
  - "historical-thinking-strategy-modelling-guide"
  - "document-based-lesson-designer"
  - "historical-source-adapter"
  - "historical-thinking-assessment-designer"
  - "disciplinary-writing-scaffold"
  - "text-complexity-analyser"
teacher_time: "3 分钟"
tags: ["close-reading", "historical-thinking", "disciplinary-literacy", "language-analysis", "document-analysis", "rhetoric", "DIG"]
---

# 历史文献精读技能构建器

## 本技能的作用

设计针对性教学以培养学生精读历史文献的能力——即关注作者的用词选择、主张、证据、语气与修辞策略，从而评估论证、视角与可信度。输出包括发展进阶序列、附带教师出声思维脚本的显性教学序列、针对史料类型的语言分析提示、常见失败模式及教学应对，以及评估指标。

历史学中的精读与语文/英语课中的精读截然不同。文学精读关注审美特征——意象、象征、叙事声音；历史精读则将语言视为作者视角、目的以及与所描述事件关系的“证据”。当历史学家精读一份文献时，他们会问：作者提出了什么主张？提供了什么证据？哪些词暴露了他们的立场？作者“说了什么”与他们“可能意味着什么”之间存在怎样的落差？Wineburg (1998) 在一项让历史学家阅读林肯文献的研究中展示了这一点：专家关注的是林肯对语言的策略性部署——而非文字之美——以此评估林肯的政治定位。驱动历史精读的问题不是“这段文字是什么意思？”，而是“这位作者的语言揭示了他的什么视角？这又告诉我们他的叙述在多大程度上可靠？”

Reisman (2012) 发现，精读与溯源一样，是其干预研究中仅有的两项显示出显著处理效应的历史思维技能之一（F(1,181) = 9.62, p = .002, ηp² = .05）。与溯源类似，精读包含具体、可演示的动作——划出带有倾向性的词语、识别主张与证据、标注语气转变——这些动作可以在单份文献上示范。这种具体性使其比需要跨文本推理的语境化或互证更易于直接教授。

## 循证基础

Wineburg (1991) 将精读确定为专家历史推理的核心组成部分。其研究中的历史学家将文献语言视为视角的证据——注意揭示作者立场的用词选择、识别超出证据支撑的主张，并察觉旨在说服的修辞策略。相比之下，学生阅读是为了获取内容：他们从文献中提取信息，却不关注信息是如何呈现的，也不关注这种呈现方式揭示了作者的什么。

Leinhardt & Young (1996) 深化了这一发现，表明专家历史学家会建构所谓的“事件模型（Event Model）”——一种基于密切关注多份文献如何用不同语言描述同一事件而形成的整合表征。不同叙述之间的语言差异不是需要过滤掉的噪音，而是需要分析的信号：为什么一位作者用 "rebellion（叛乱）"，而另一位作者用 "revolution（革命）"？答案揭示的不是词汇偏好，而是政治立场。

Wineburg (1998) 通过历史学家阅读林肯文献的研究展示了行动中的历史精读。专家关注林肯对语言的策略性运用——他如何针对不同受众定位自己、他的用词如何随时间推移而变化，以及他的公开声明与私人信件之间的落差揭示了他的真实想法。这不是作为文学鉴赏的精读，而是作为证据分析的精读：作者的语言就是关于作者视角的数据。

Reisman (2012) 在“像历史学家一样阅读”课程中通过引导问题将精读操作化：作者提出了什么主张？作者使用了什么证据？作者使用了什么语言来说服读者？文献的语言如何表明作者的视角？精读的处理效应显著，表明这些具体的分析动作可以通过显性教学与练习来习得。

Wineburg & Reisman (2015) 将精读置于学科素养之中，将其与通用阅读理解区分开来。通用阅读策略（概括、预测、回溯）对历史阅读是必要的，但远远不够。历史精读要求对“作为证据的语言”保持学科特有的敏锐度——这是通用阅读教学无法培养的实践。

## 输入模式

教师必须提供：
- **Historical topic（历史主题）：** *例如："Causes of the French Revolution" / "The debate over Japanese American internment" / "Perspectives on British imperialism in India"*
- **Student level（学生水平）：** *例如："Year 9, can summarise documents but don't analyse language choices" / "Year 11 IB History, familiar with close reading from English class but apply literary rather than historical analysis"*
- **Current challenge（当前挑战）：** *例如："They summarise what the document says but don't notice HOW it says it" / "They can identify 'persuasive language' but can't connect it to the author's historical position" / "They treat all documents as neutral information sources — they don't notice that language reveals perspective"*

可选：
- **Source type（史料类型）：** 影响哪些语言特征最具分析价值
- **Available documents（可用文献）：** 允许针对具体文本定制
- **Curriculum framework（课程框架）：** 将提示与所用框架对齐
- **Prior instruction（先前教学）：** 尤其需要了解学生是否已有文学精读经验可供借力（或可能混淆历史精读的要求）

## Prompt

```
You are an expert in historical thinking pedagogy, with deep knowledge of Wineburg's (1991, 1998) research on how expert historians read documents closely for evidence of perspective, Leinhardt and Young's (1996) work on how language differences between accounts function as historical evidence, and Reisman's (2012) evidence that close reading is teachable through explicit instruction. You understand that close reading in history is distinct from literary close reading: the goal is not to appreciate aesthetic features but to analyse language as evidence of the author's perspective, purpose, and reliability.

Your task is to design targeted close reading instruction for:

**Historical topic:** {{historical_topic}}
**Student level:** {{student_level}}
**Current challenge:** {{current_challenge}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Source type:** {{source_type}} — if not provided, design for written primary sources as the default.
**Available documents:** {{available_documents}} — if provided, tailor the instruction to these specific documents.
**Curriculum framework:** {{curriculum_framework}} — if not provided, use the DIG framework as the default.
**Prior instruction:** {{prior_instruction}} — if provided, build on existing skills. If students have literary close reading experience, explicitly address how historical close reading differs.

Design the following:

1. **Close reading progression:** What close reading looks like at three levels for this age group:
   - **Novice:** The student extracts content from the document — they can tell you WHAT it says but not HOW it says it or WHY the author chose those words. Describe what this looks like with specific observable indicators.
   - **Developing:** The student notices some language features (e.g., identifies "persuasive language" or "emotive words") but treats them as generic categories rather than connecting them to the author's specific historical position and purpose. Describe what superficial close reading looks like.
   - **Proficient:** The student analyses specific word choices, claims, and rhetorical strategies as evidence of the author's perspective, connecting language to the author's historical circumstances. Describe what this looks like — the specific analytical moves a proficient student makes.

2. **Explicit instruction sequence:**
   - **I DO:** A think-aloud script (150–200 words) showing the teacher modelling close reading of a specific passage — pausing at key word choices, asking what they reveal about the author's stance, identifying claims and evaluating the evidence offered for them, noticing what the author does NOT say.
   - **WE DO:** A guided practice activity where students close-read a passage together with teacher support.
   - **YOU DO:** Independent close reading with monitoring criteria.

3. **Language analysis prompts:** Source-type-specific prompts that direct students' attention to historically significant language features. For each prompt, include the prompt itself, why it matters for this source type, and a sentence starter. Adapt prompts to the source type — a speech demands attention to rhetorical strategy and audience; a private letter demands attention to what the author says differently in private than in public; testimony demands attention to what is claimed vs. what is evidenced.

4. **Common failure patterns:** 3–4 patterns with descriptions, explanations, and instructional responses.

5. **Assessment indicators:** What to listen for in discussion, what to look for in written work, and the key test that distinguishes a student who close-reads analytically from one who only summarises content.

Return your output in this exact format:

## Close Reading Instruction Plan

**Topic:** [Historical topic]
**Students:** [Level and current challenge]
**Source type:** [Type of source]

### Close Reading Progression

**Novice — reading for content only:**
[Observable indicators]

**Developing — noticing language without connecting it to perspective:**
[Observable indicators]

**Proficient — analysing language as evidence of perspective:**
[Observable indicators]

### Explicit Instruction Sequence

**I DO — Teacher Think-Aloud**
[Script, 150–200 words]

**WE DO — Guided Practice**
[Activity with teacher prompts]

**YOU DO — Independent Practice**
[What to monitor for]

### Language Analysis Prompts

[Source-type-specific prompts with rationale and sentence starters]

### Common Failure Patterns

[3–4 patterns]

### Assessment Indicators

**In discussion:** [What to listen for]
**In written work:** [What to look for]
**The key test:** [Single most reliable indicator]

**Self-check before returning output:** Verify that (a) the progression distinguishes between summarising content and analysing language as evidence, (b) the think-aloud models attention to SPECIFIC word choices, not generic "language features," (c) the prompts are adapted to the source type, (d) the failure patterns distinguish between literary and historical close reading where relevant, and (e) the assessment indicators describe analytical close reading, not comprehension.
```

## 示例输出

**场景：** *Historical topic: "Did Pocahontas rescue John Smith?" / Student level: "Year 8, can summarise documents but don't analyse language choices" / Current challenge: "They tell me what Smith says happened but don't notice the difference in tone and word choice between his two accounts" / Source type: "Written first-person accounts" / Available documents: "Smith's 1608 True Relation and 1624 General History"*

---

## 精读教学计划

**主题：** 宝嘉康蒂救了约翰·史密斯吗？
**学生：** 八年级，能概括文献但不会分析语言选择
**史料类型：** 书面第一人称记述

### 精读发展进阶

**初学——仅阅读内容：**
学生能说出每份记述里发生了什么——"In the first one, Smith meets Powhatan and they're friendly. In the second one, they try to kill him and Pocahontas saves him." 他们把文献当作信息的容器并提取故事，却没有注意到 1608 年的记述使用了 "kindly"、"friendship" 和 "kindness" 等词，而 1624 年的记述使用了 "barbarous"、"fearful" 和 "beat out his brains"。如果被问及两份记述为何不同，他们会猜测事件本身（"maybe he forgot"），而不是猜测语言（"maybe he chose different words for a reason"）。

**发展中——注意到语言但未将其与视角相连：**
学生能识别出两份记述使用了不同的语言："The first one sounds friendlier and the second one sounds scarier." 他们可能会把语言贴上“积极”或“消极”的标签。但他们把这当作对文本的描述，而非关于作者的证据。他们不会追问“为什么”史密斯在 1608 年选择友好语言而在 1624 年选择带有威胁性的语言，也不会思考语气的转变揭示了他目的的什么变化。

**熟练——将语言作为视角证据进行分析：**
学生将具体的用词选择与作者的处境联系起来。他们可能会说："In 1608, Smith describes Powhatan with words like 'kindly' and 'friendship' — he's writing a report for his sponsors and wants to show he has good relations with the natives. By 1624, he uses 'barbarous' and describes a dramatic rescue — he's writing a book for a public audience and wants an exciting story. The language shift tells us more about Smith's changing purposes than about what actually happened."

### 显性教学序列

**我做（I DO）——教师出声思维**

*教师投影展示史密斯 1608 年《True Relation》中的一段并慢速朗读：*

"Let me read this carefully. 'He kindly welcomed me with good words and great platters of sundry victuals, assuring me his friendship.' I'm going to pause on the word 'kindly.' Smith chose that word. He could have said 'he received me' or 'he allowed me to enter' — neutral descriptions. But 'kindly' tells me Smith wants the reader to see Powhatan as welcoming. And 'assuring me his friendship' — that's not just describing what happened, that's interpreting Powhatan's intentions. Smith is telling us what Powhatan MEANT, not just what Powhatan did.

Now I'm going to hold that in mind while I look at the 1624 version of the same meeting. 'Having feasted him after their best barbarous manner they could.' There's 'barbarous.' Same meeting, same author — but now the Powhatan are barbarous, not kind. That single word change tells me something shifted in how Smith wanted readers to see this encounter. The question isn't which version is true — it's why the same person described the same event so differently."

**我们做（WE DO）——引导练习**

学生并排拿到两段文本。结对在每份记述中划出三个揭示史密斯对波瓦坦态度的词或短语。对于划出的每个词，完成句子："Smith chose the word ___ instead of ___, which suggests he wanted the reader to think ___."

教师巡视。核心纠偏：
- 如果学生划出的是内容词（"victuals"、"clubs"）："Those tell us what happened. I want words that tell us what Smith THOUGHT about what happened."
- 如果学生识别了语气但停留在贴标签："You said the 1608 version sounds 'friendly.' Which SPECIFIC word makes it sound friendly? What word could he have used instead?"

**你做（YOU DO）——独立练习**

学生拿到一段新文本——一位历史学家的阐释之一。他们识别出该历史学家做出的两处具体语言选择，并解释每一处揭示了该历史学家在营救问题上的什么立场。教师不提供提示。

### 语言分析提示语

1. **作者用什么词来描述人物或群体，这些词传达了什么态度？**
   *为何重要：* 描述性用词选择（"kindly" vs. "barbarous"，"rescued" vs. "claimed to have been rescued"）是作者视角最直接的证据。
   *句首提示：* "The author describes [person/group] as ___, which suggests they see them as..."

2. **作者宣称发生了什么，他们为该宣称提供了什么证据？**
   *为何重要：* 第一人称记述常把阐释包装成事实。区分“这件事发生了”和“我相信这件事发生了”是核心的精读动作。
   *句首提示：* "The author claims that ___, but the evidence they give is only..."

3. **作者“没有”说什么本该被提及的内容？**
   *为何重要：* 省略与纳入同样具有揭示性。史密斯在 1608 年对营救的沉默，与他在 1624 年对营救的写入同样意味深长。
   *句首提示：* "It's significant that the author doesn't mention ___, because..."

4. **如果由另一位立场不同的人来写，这段话的读感会有何不同？**
   *为何重要：* 这促使学生认识到文献只是“一种”可能的记述，由这位特定作者的立场塑造——而非通向过去的透明窗户。
   *句首提示：* "If this had been written by [different person], they might have described ___ as ___ instead of ___."

### 常见失败模式

**1. “以概括代分析”——复述文献说了什么**
*表现：* "Smith says Powhatan welcomed him and gave him food." 学生准确转述了内容，但没有对语言做任何分析。
*原因：* 学生接受过阅读理解训练（文本说了什么？），但未接受过精读训练（文本如何表达以及这揭示了什么？）。
*应对：* 追问："You've told me WHAT Smith says. Now tell me HOW he says it. Pick one word and explain why he chose THAT word instead of a different one."

**2. “泛化贴标签”——识别语气却缺乏具体性**
*表现：* "The author uses emotive language to persuade the reader." 学生掌握了文学精读词汇，但将其当作公式套用。
*原因：* 往往迁移自语文/英语课，在那里识别“说服技巧”是常见任务。学生学会了贴标签，但未将标签与历史语境相连。
*应对：* "WHICH emotive language? Point to the specific word. Now — why would THIS author, writing at THIS time, choose THAT word? What was happening in their world that makes that word choice significant?"

**3. “两份记述都对”——未能认识到语言塑造意义**
*表现：* "The 1608 version describes a friendly meeting and the 1624 version describes a rescue. Both things could have happened."
*原因：* 学生把两份记述都当作对不同事件的透明报告，而不是对同一事件的不同建构版本。他们尚未将语言视为塑造报道内容的透镜。
*应对：* "These describe the SAME meeting. Smith can't have been both kindly welcomed AND dragged to the stones to have his brains beaten out. The language isn't just describing — it's constructing a version of events. Which version, and why?"

### 评估指标

**讨论中：** 倾听学生在就文献提出主张时是否引用具体词句——"Smith says 'barbarous,' which shows..." 而非 "Smith describes the meeting." 从概括内容转向引用语言作为证据，正是关键标志。

**书面作业中：** 寻找对具体词语加引号后紧跟分析“为何这些词重要”的写法。发展中的学生会写："Smith describes the meeting in a negative way." 熟练的学生会写："Smith's use of 'barbarous' to describe the same people he called 'kind' sixteen years earlier suggests his purpose for writing had changed."

**核心检验：** 给学生两份对同一事件的记述，两者在语言上存在明显差异。不要问“发生了什么？”，而是问“每位作者希望你如何看待这一事件，你如何从他们的用词选择中看出来？” 能够用具体文本证据回答第二个问题的学生，就是在历史地精读。

---

## 已知局限性

1. **历史精读与语文/英语课精读既有重叠又存在区别。** 具备较强文学精读技能的学生可能需要明确指导，学会将这些技能转向历史分析——将语言作为视角的证据，而非审美工艺。本技能点明了这一区别，但在跨学科语境中工作的教师应与语文/英语同事协调，相互强化而非混淆这两种应用。

2. **精读是 Reisman (2012) 中显示出处理效应的两项技能之一，但该研究的测量工具评估的是策略应用，而非分析深度。** 学会识别用词选择和修辞策略的学生，是否也发展出了将所有文本视为建构而非透明窗口的深层倾向，现有证据尚未解决这一开放问题。

3. **精读历史文献需要一定的语言熟练度，这可能对 EAL 学生或阅读困难学生构成障碍。** 本技能强调分析用词选择，假设学生能感知 "kindly" 与 "barbarous" 等词之间的内涵差异。教师在要求学生将语言作为证据分析之前，应确保词汇支持（参见 text-complexity-analyser 与 vocabulary-tiering-tool）已到位。
