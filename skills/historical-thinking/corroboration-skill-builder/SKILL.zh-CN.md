---
# AGENT SKILLS STANDARD FIELDS (v2)
name: corroboration-skill-builder
description: "培养学生跨多份历史史料比对记述的能力——识别一致、矛盾与空白之处。适用于学生将单一文献视为完整答案而非片面视角时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/corroboration-skill-builder"
skill_name: "历史史料互证技能构建器"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "moderate"
evidence_sources:
  - "Wineburg (1991) — Historical problem solving: cognitive processes in the evaluation of documentary and pictorial evidence"
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg & Reisman (2015) — Disciplinary literacy in history: a toolkit for digital citizenship"
  - "Wineburg & Martin (2004) — Reading and rewriting history"
  - "Wineburg, Martin & Monte-Sano (2011) — Reading like a historian: teaching literacy in middle and high school history classrooms"
  - "Wineburg, Smith & Breakstone (2018) — What is learned in college history classes?"
input_schema:
  required:
    - field: "historical_topic"
      type: "string"
      description: "学生正在调查的历史主题、时期或问题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前多文献分析的经验水平"
    - field: "current_challenge"
      type: "string"
      description: "学生目前在使用多份史料时做了什么或没做到什么——表明互证能力尚未发展起来的可观察行为"
  optional:
    - field: "available_documents"
      type: "string"
      description: "学生将使用的具体文献集描述——文献数量、类型以及内置的张力或矛盾"
    - field: "source_types"
      type: "string"
      description: "文献集中的史料类型组合——例如两份目击者记述、一份目击者加一位历史学家、一手与二手史料、文本与图像"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架"
    - field: "prior_instruction"
      type: "string"
      description: "学生已经接受过的互证教学，以及他们是否已发展出互证所依赖的溯源、精读与语境化技能"
output_schema:
  type: "object"
  fields:
    - field: "corroboration_progression"
      type: "object"
      description: "互证在初学、发展中和熟练水平上的表现——附区分“按顺序阅读多份史料”与“真正比对它们以确立可能性”的可观察指标"
    - field: "explicit_instruction_sequence"
      type: "object"
      description: "教授互证的三段式序列，针对多文献推理的复杂性而设计——包含使“比对”动作显性化而非假定学生会自然串联记述的策略"
    - field: "corroboration_prompts"
      type: "array"
      description: "引导学生跨文献比对的提示语——尽可能针对具体文献集校准"
    - field: "common_failure_patterns"
      type: "array"
      description: "学生未能互证的具体模式，包括将每份文献视为孤立阅读任务，以及默认“选边站”而非权衡证据"
    - field: "assessment_indicators"
      type: "object"
      description: "学生正在进行互证的可观察迹象——讨论中听什么、书面作业中看什么"
chains_well_with:
  - "sourcing-skill-builder"
  - "close-reading-skill-builder"
  - "contextualisation-skill-builder"
  - "historical-thinking-strategy-modelling-guide"
  - "document-based-lesson-designer"
  - "historical-document-set-curator"
  - "historical-thinking-assessment-designer"
  - "argument-structure-scaffold-generator"
teacher_time: "4 分钟"
tags: ["corroboration", "historical-thinking", "disciplinary-literacy", "multi-document-reasoning", "evidence-weighing", "document-analysis", "DIG"]
---

# 历史史料互证技能构建器

## 本技能的作用

设计针对性教学以培养学生的史料互证（corroboration）实践——跨多份史料比对记述，识别一致、矛盾、沉默与空白之处，并利用这些比对来确立“什么最有可能发生”，而不是把任何单一记述当作定论。输出包括发展进阶序列、针对多文献推理设计的显性教学序列、互证提示语、常见失败模式以及评估指标。

互证是四项历史思维技能中最复杂的一项，因为它本质上是互文性的（intertextual）。溯源、精读和语境化都可以在单份文献上练习；互证则不能——它要求同时在脑海中保持多份记述，并推理它们之间的关系。这使得它最难教授，也最晚发展成熟。Reisman (2012) 在其六个月的干预研究中发现，互证（与语境化一样）未显示出显著处理效应。她将其部分归因于实验班课堂中全班讨论的普遍缺失——互证可能比其他技能更需要对话式教学（讨论、辩论、协作比对），因为其推理本身就是比较性的。

互证还以另外三项技能作为先决条件。为了富有成效地比对史料，学生必须先能够对每份文献进行溯源（谁写的以及为什么）、精读每份文献（究竟主张了什么以及如何表达）以及语境化每份文献（什么处境塑造了它）。没有这些基础，互证就会退化为表面观察（"these two accounts say different things"），而不是关于“为什么”它们不同以及差异揭示了什么的分析性推理。

## 循证基础

Wineburg (1991) 将互证确立为区分专家历史学家与新手读者的三大核心启发法之一（与溯源和语境化并列）。历史学家系统性地比对记述，标出一致与分歧之处，并将矛盾当作诊断工具——两份史料之间的矛盾不是通过挑出“正确”的那一份来解决的问题，而是一个需要解释的线索。为什么两位观察者会对同一事件做出不同描述？答案总是指向作者的视角、处境与目的。

Wineburg & Martin (2004) 通过宝嘉康蒂单元展示了课程实践中的互证。学生对比约翰·史密斯 1608 年和 1624 年的两份记述——同一作者自相矛盾——随后审视使用相同证据得出不同结论的四位历史学家。这一设计的教学威力在于层层递进的矛盾：首先，同一个人与早先的自己相矛盾；接着，专业历史学家使用同一批文献彼此意见相左。学生由此领悟到，历史知识并非现成躺在任何单一史料之中，而是通过对多份记述的比对与权衡建构出来的。

Wineburg, Martin & Monte-Sano (2011) 在宝嘉康蒂一章中通过结构化比对工具将互证操作化。学生使用练习纸，要求写出每份史料说了什么、史料在何处一致与分歧，以及什么可以解释这些差异。课程架构——分轮次阅读史料，每轮后开展全班讨论——正是为了给互证所要求的比较推理搭建支架。

Reisman (2012) 未能发现互证的显著处理效应。她的解释有两方面：互证需要在文献之间建立联结（比溯源更难用离散动作示范），且其研究中的教学条件可能未能充分支持它——实验班中很少开展全班讨论，而全班讨论正是使比较推理变得可见且可练习的关键场域。这表明互证可能需要比常规基于文献的课堂结构更多的对话式、讨论式教学。

Wineburg, Smith & Breakstone (2018) 揭示了大学生中互证能力的缺失。当拿到关于美菲战争的两份文献——描述暴行的参议院证词与为战争辩护的上校信件——超过 80% 的学生孤立地分析每份文献。他们没有追问“同时存在这两份文献（一份调查与一份辩护）”揭示了当时更广泛的公共辩论。每份文献都被当作独立的阅读任务，而不是更大证据图景中的一块拼图。

## 输入模式

教师必须提供：
- **Historical topic（历史主题）：** *例如："Did Pocahontas rescue John Smith?" / "What caused the fall of the Roman Republic?" / "Was the dropping of the atomic bomb justified?"*
- **Student level（学生水平）：** *例如："Year 8, can analyse individual documents but don't compare them" / "Year 10, compare documents superficially (this one says X, that one says Y) but don't reason about why they differ" / "Year 12, can compare two sources but struggle to synthesise across three or more"*
- **Current challenge（当前挑战）：** *例如："They read each document separately and don't connect them" / "They pick the source they find most convincing and ignore the others" / "They note that sources disagree but treat this as a dead end rather than a starting point for analysis"*

可选：
- **Available documents（可用文献）：** 文献集描述——对互证尤为重要，因为分析空间取决于史料之间存在何种张力
- **Source types（史料类型）：** 史料类型组合很关键——比对两份目击者记述不同于将目击者与历史学家比对
- **Curriculum framework, prior instruction** —— 同其他技能构建器

## Prompt

```
You are an expert in historical thinking pedagogy, with deep knowledge of Wineburg's (1991) identification of corroboration as a core historical thinking heuristic, Reisman's (2012) finding that corroboration did NOT show significant treatment effects in a six-month intervention (suggesting it requires different or more sustained instructional strategies than sourcing and close reading), and the Document-Based Lesson structure from Wineburg, Martin, and Monte-Sano (2011) that scaffolds multi-document comparison through successive rounds of reading and discussion.

You understand that corroboration is the most complex of the four historical thinking skills because it is inherently intertextual — it requires holding multiple accounts in mind and reasoning about relationships between them. You also understand that corroboration depends on sourcing, close reading, and contextualisation as prerequisites: students must be able to analyse individual documents before they can compare them productively.

Your task is to design targeted corroboration instruction for:

**Historical topic:** {{historical_topic}}
**Student level:** {{student_level}}
**Current challenge:** {{current_challenge}}

The following optional context may or may not be provided. Use whatever is available.

**Available documents:** {{available_documents}} — if provided, design the corroboration instruction around the specific tensions and contradictions in this document set. If not, design generalisable instruction with guidance on what kinds of document pairings create productive comparison opportunities.
**Source types:** {{source_types}}
**Curriculum framework:** {{curriculum_framework}}
**Prior instruction:** {{prior_instruction}} — particularly important to know whether students have developed sourcing, close reading, and contextualisation skills. If they have not, note that corroboration instruction should be preceded by work on those foundational skills.

Design the following:

1. **Corroboration progression:** What corroboration looks like at three levels:
   - **Novice:** The student reads each document as an isolated task. Even when given multiple sources, they analyse them one at a time without connecting them. If asked what the documents tell us together, they summarise each one separately. Describe what this looks like with observable indicators.
   - **Developing:** The student notices that sources agree or disagree but treats this as an observation rather than an analytical tool. They may say "Source A says X and Source B says Y" but do not reason about WHY they differ or what the differences reveal. They may default to picking the source they find most convincing rather than weighing the accounts against each other. Describe what this surface-level comparison looks like.
   - **Proficient:** The student uses agreements and contradictions between sources as diagnostic tools. When sources agree, they consider whether this confirms an account or whether both sources might share the same bias. When sources disagree, they reason about WHY — considering each author's perspective, circumstances, and purpose — and use the disagreement to build a more nuanced understanding than any single source provides. Describe what this analytical corroboration looks like.

2. **Explicit instruction sequence:**
   - **I DO:** A think-aloud script (150–200 words) showing the teacher modelling corroboration — reading a passage from one document, then turning to another and explicitly comparing them. The think-aloud should model the reasoning: "Document A says ___, but Document B says ___. Why might they differ? If I think about who wrote each one and when..."
   - **WE DO:** A guided practice activity that structures the comparison. Consider using a comparison matrix (what does Source A say about X? What does Source B say about X? Do they agree? If not, what might explain the difference?) or a structured discussion protocol where pairs argue for different sources before the class synthesises. The key is making the comparison step DELIBERATE rather than hoping students will do it naturally.
   - **YOU DO:** Independent corroboration with monitoring criteria.

3. **Corroboration prompts:** Prompts that guide multi-document comparison. For each prompt, include the prompt, why it matters, and a sentence starter. Prompts should push students beyond noting disagreement toward reasoning about what disagreement reveals.

4. **Common failure patterns:** 3–4 patterns including the "isolated reading" pattern (treating each document as a separate task) and the "picking a winner" pattern (choosing the most convincing source rather than weighing all accounts).

5. **Assessment indicators:** What to listen for, what to look for, and the key test.

Return your output in this exact format:

## Corroboration Instruction Plan

**Topic:** [Historical topic]
**Students:** [Level and current challenge]
**Document set:** [Description of available documents or "general"]

### Corroboration Progression

**Novice — reading documents in isolation:**
[Observable indicators]

**Developing — noting agreement/disagreement without reasoning about it:**
[Observable indicators]

**Proficient — using comparison as a diagnostic tool:**
[Observable indicators]

### Explicit Instruction Sequence

**I DO — Teacher Think-Aloud**
[Script, 150–200 words]

**WE DO — Guided Practice**
[Structured comparison activity]

**YOU DO — Independent Practice**
[What to monitor for]

### Corroboration Prompts

[Prompts with rationale and sentence starters]

### Common Failure Patterns

[3–4 patterns]

### Assessment Indicators

**In discussion:** [What to listen for]
**In written work:** [What to look for]
**The key test:** [Single most reliable indicator]

**Self-check before returning output:** Verify that (a) the progression distinguishes between noting that sources disagree and reasoning about WHY they disagree, (b) the think-aloud models cross-document reasoning, not sequential single-document analysis, (c) the guided practice includes a structure that makes comparison deliberate, (d) the failure patterns address both "isolated reading" and "picking a winner," and (e) the instruction design accounts for the finding that corroboration requires dialogic instruction and builds on the other three skills.
```

## 示例输出

**场景：** *Historical topic: "Did Pocahontas rescue John Smith?" / Student level: "Year 8, can source and close-read individual documents but don't compare across documents" / Current challenge: "They analyse Smith's 1608 account, then analyse his 1624 account, but don't connect them — they don't reason about why the same person told different stories" / Available documents: "Smith's 1608 True Relation, Smith's 1624 General History, Adams's 1867 critique, Lemay's 1991 defence" / Source types: "Two primary accounts by the same author, two secondary interpretations by different historians"*

---

## 互证教学计划

**主题：** 宝嘉康蒂救了约翰·史密斯吗？
**学生：** 八年级，能分析单个文献但不会跨文献比对
**文献集：** Smith 1608、Smith 1624、Adams 1867、Lemay 1991

### 互证发展进阶

**初学——孤立阅读文献：**
学生为每份文献写出各自独立的分析。被问及 1608 年记述时，他们概括史密斯说了什么；被问及 1624 年记述时，他们单独概括那一份。没有明确提示时，他们甚至可能注意不到矛盾。即使注意到了，也只是觉得困惑而非在分析上加以利用："I don't know which one is true." 文献各自住在独立的心理隔间里，学生尚未理解史料“之间”的关系本身就是证据。

**发展中——只指出一致/分歧而不加推理：**
学生观察到记述有所不同："In the 1608 version, Smith doesn't mention the rescue, but in the 1624 version he does." 他们也可能注意到 Adams 和 Lemay 意见不同。但这一观察成了终点，而非分析的起点。他们可能会说 "So we don't know what really happened" 然后停下，或者挑出自己觉得最有说服力的那一份——往往是更具戏剧性的 1624 年版本——却不解释为什么该史料应优先于其他史料。

**熟练——将比对作为诊断工具：**
学生将史密斯两份记述之间的矛盾转化为研究问题："Why would Smith add the rescue story 16 years later?" 他们调动溯源与语境化来回答这个问题：1624 年记述写于宝嘉康蒂在英国成名之后。他们利用 Adams 的批判质疑史密斯的可信度，并利用 Lemay 的辩护思考替代解释。他们的结论不是非黑即白的“营救发生了/没发生”，而是对证据的权衡："The fact that Smith didn't mention the rescue in 1608 when it supposedly happened, but added it in 1624 when Pocahontas was famous, suggests he may have been enhancing his own reputation — but Lemay argues he had different purposes for each account, which could also explain the differences."

### 显性教学序列

**我做（I DO）——教师出声思维**

*教师并排展示史密斯的两份记述：*

"I've read both of these documents individually. Now I need to put them next to each other and ask: what happens when I compare them? In 1608, Smith writes 'He kindly welcomed me with good words and great platters of sundry victuals, assuring me his friendship.' In 1624, for the same meeting, he writes 'having feasted him after their best barbarous manner they could... being ready with their clubs to beat out his brains.'

Same person. Same event. Completely different language. The 1608 version: friendly, generous, safe. The 1624 version: barbarous, violent, near-death. I can't explain this by saying Smith just forgot the details — you don't forget someone trying to beat your brains out. So something ELSE is going on.

What changed between 1608 and 1624? Smith's circumstances changed. Pocahontas became famous. The relationship between colonists and Powhatan deteriorated. Smith was writing for a different audience with different purposes. The contradiction doesn't mean one account is true and the other false — it means both accounts are shaped by the moment they were written. And THAT is more historically interesting than either account alone."

**我们做（WE DO）——引导练习**

学生拿到一张四列比对矩阵：这份史料关于营救说了什么？| 何时撰写？| 作者为什么会这样呈现？| 它与其他史料一致还是分歧，为什么？

结对为 Smith 1608 和 Smith 1624 各填一行，然后写一句话回答："What does the DIFFERENCE between these two accounts tell us that neither account tells us on its own?"

教师巡视。核心纠偏：
- 如果学生填完了表格行却跳过比对句："You've analysed each source. Now — what do they tell us TOGETHER that neither tells us alone? The contradiction IS the evidence."
- 如果学生写“其中必有一人在说谎”："Maybe. But what if neither is lying and both are just telling the story that suited their purpose at the time? What would that mean for how we use these sources?"

全班讨论：2–3 对学生分享他们的比对句。教师示范如何将比对延伸到历史学家："Now let's see what Adams and Lemay do with this same contradiction. Do they agree about what the contradiction means?"

**你做（YOU DO）——独立练习**

学生拿到 Adams 和 Lemay 的阐释。独立撰写一段话回答："Adams and Lemay both examine the same evidence — Smith's two accounts. They reach different conclusions. What does each one argue, and which do you find more persuasive based on the evidence?" 该任务要求学生比对两位历史学家的论证，而不仅仅是概括他们。

教师监控学生是在比对两份阐释，还是孤立地分别分析。

### 互证提示语

1. **这些史料在何处一致，这种一致能证明什么吗？**
   *为何重要：* 学生常以为只要两份史料说法一致，主张就一定是真的。但两份史料一致可能是因为它们共享同一视角或源自同一信息源。一致是证据，而非铁证。
   *句首提示：* "Sources A and B both say ___, but this might be because they both..."

2. **这些史料在何处分歧，什么能解释这种分歧？**
   *为何重要：* 这是核心的互证动作。分歧不是死胡同，而是诊断工具——对“为什么”史料会分歧的解释，往往比任何单一史料揭示出更多关于过去的信息。
   *句首提示：* "Source A says ___ while Source B says ___. This might be because..."

3. **每份史料省略了什么另一份却包含的内容？**
   *为何重要：* 沉默与陈述同样重要。作者省略了什么——以及另一位作者纳入了什么——揭示了各自认为什么是重要的、无关的或不便提及的。
   *句首提示：* "Source A doesn't mention ___, even though Source B says it was significant. This might be because..."

4. **综合所有史料，我们认为最有可能发生了什么——我们能有多大把握？**
   *为何重要：* 这推动学生走向历史学家的目标：通过权衡多份记述确立可能性，而不是挑出一份并称之为真相。限定词 "probably（最有可能）" 很重要——它传递出历史知识是暂定且基于证据的。
   *句首提示：* "Based on the evidence from all the sources, it seems most likely that ___, although we can't be certain because..."

### 常见失败模式

**1. “孤立阅读”——逐一分析文献而不加联结**
*表现：* 学生写完一段关于史料 A 的话，接着写一段关于史料 B 的话，两者之间毫无关联。每份文献都是独立的阅读任务。
*原因：* 课堂常规往往强化顺序加工——“先读文献 1 并回答问题，再读文献 2 并回答问题”。比对步骤被默认存在，却未被结构化。
*应对：* 使用比对矩阵或并排展示，使文献在物理上相邻。在允许学生写其他内容之前，强制要求先写一句比对句（"These sources agree/disagree about ___ because ___"）。用结构倒逼比对。

**2. “选出赢家”——挑选最有说服力的史料并忽略其余**
*表现：* "I believe Source B because it has more detail" 或 "Source A is more reliable because it's a primary source." 学生把互证当成史料之间的淘汰赛，而非权衡所有记述的过程。
*原因：* 学生习惯于寻找“正确答案”。当史料分歧时，他们去寻找“对的那一份”，而不是推理分歧揭示了什么。
*应对：* 明确禁止在初稿中使用 "I believe Source ___"。改为要求写："Source A is more convincing on the question of ___ because ___, but Source B is more convincing on ___ because ___." 这迫使学生认识到不同史料针对不同问题各有优势。

**3. “把矛盾当死胡同”——将分歧视为无法获知任何真相的证明**
*表现：* "The sources disagree, so we can't really know what happened." 学生把矛盾当作放弃的理由，而非深挖的起点。
*原因：* 这反映了一个认识论阶段：学生已经走出了朴素实在论（一份史料 = 真相），但尚未达到“历史知识是通过权衡证据建构的”这一理解，从而卡在了相对主义里。
*应对：* "You're right that we can't know for certain. But historians don't give up when sources disagree — that's where the interesting work begins. The question isn't 'which one is true?' It's 'what does the disagreement TELL us?' WHY do these sources disagree? What does that reveal about the people who wrote them and the times they lived in?"

### 评估指标

**讨论中：** 倾听学生在讨论某份史料时是否自发引用另一份史料："But in the other document, Smith said..." 或 "Adams disagrees with Lemay about this because..." 互证的标志正是交叉参照——在彼此的关联中谈论文献，而非孤立谈论。同时倾听学生在遇到主张时是否会追问："What do the other sources say about this?"

**书面作业中：** 寻找将多份史料置于张力之中而非按顺序流水账式罗列的段落。发展中的学生会写："Source A says X. Source B says Y." 熟练的学生会写："While Source A claims X, Source B's account suggests Y. The disagreement may be explained by the fact that A was writing for ___ while B was writing for ___." 结构标志正是把史料彼此相连的连接词——"while"、"however"、"this contradicts"、"which is consistent with"。

**核心检验：** 完成多文献活动后，问学生："What do these sources tell us TOGETHER that no single source could tell us on its own?" 能够回答这一问题——阐述比对如何产出单一分析无法产出的知识——的学生，才真正理解了互证的目的；只是分别复述每份史料说什么的学生则尚未理解。

---

## 已知局限性

1. **互证在 Reisman (2012) 中未显示出显著处理效应。** 与语境化一样，这里的教学策略借鉴了专家阅读行为与课程设计原则，而非经过实验验证的干预措施。证据强度因此评级为“moderate（中等）”。关于互证比常规基于文献的课程需要更多对话式教学（全班讨论、结构化辩论）的建议，是一个合理但尚未经过检验的假设。

2. **互证以另外三项技能为先决条件。** 无法对单个文献进行溯源、精读或语境化的学生，不可能富有成效地互证它们——他们只会比对表面内容，而无法推理记述为何不同。教师在重点训练互证之前，应确保学生已在另外三项技能上达到至少“发展中”水平。

3. **互证的质量高度依赖于文献集本身。** 两份实质内容完全相同的史料无法为比对提供分析杠杆。富有成效的互证需要能够制造真实张力的史料——对同一事件的不同视角、细节或侧重点的矛盾，或者一份记述省略了另一份所包含内容的明显沉默。关于如何设计内置分析张力的文献集，参见 historical-document-set-curator。
