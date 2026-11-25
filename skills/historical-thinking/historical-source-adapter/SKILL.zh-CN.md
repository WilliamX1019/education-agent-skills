---
# AGENT SKILLS STANDARD FIELDS (v2)
name: historical-source-adapter
description: "为课堂教学改编历史一手史料——调整语言复杂度与篇幅，同时保留用于溯源、精读和互证的特征。适用于原始史料对目标年龄段过于复杂时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/historical-source-adapter"
skill_name: "历史史料改编器"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "moderate"
evidence_sources:
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg, Martin & Monte-Sano (2011) — Reading like a historian: teaching literacy in middle and high school history classrooms"
  - "Wineburg & Reisman (2015) — Disciplinary literacy in history: a toolkit for digital citizenship"
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Faggella-Luby, Graner, Deshler & Drew (2012) — Building a house on sand: why disciplinary literacy is not sufficient to replace general strategies for adolescent learners who struggle"
input_schema:
  required:
    - field: "original_source"
      type: "string"
      description: "原始一手史料的全文或待改编段落，附带完整的史料出处（作者、日期、出版物、创作语境）"
    - field: "student_level"
      type: "string"
      description: "目标学生的年龄/年级及阅读水平"
    - field: "target_skills"
      type: "string"
      description: "改编后的史料必须支持哪些历史思维技能——例如溯源、精读、语境化、互证——以便改编保留这些分析动作所需的特征"
  optional:
    - field: "target_length"
      type: "string"
      description: "改编后史料的期望大致长度——例如 '150 words'、'1 paragraph'、'half the original length'"
    - field: "central_question"
      type: "string"
      description: "该史料将用于调查的核心历史问题——确保改编保留与探究最相关的特征"
    - field: "key_passages"
      type: "string"
      description: "在改编版本中“必须”保留的具体段落或短语，因为它们在分析上很重要——例如用于精读的倾向性语言、用于互证的矛盾点"
    - field: "eal_considerations"
      type: "string"
      description: "班级是否包含英语作为附加语言（EAL）的学习者及其语言水平——影响所需词汇支持的程度"
    - field: "paired_documents"
      type: "string"
      description: "本课文献集中的其他文献——确保改编保留跨文献集互证所需的特征"
output_schema:
  type: "object"
  fields:
    - field: "adapted_source"
      type: "string"
      description: "改编后的史料版本，完整保留史料出处并清晰标明修改之处"
    - field: "adaptation_notes"
      type: "object"
      description: "对每一处改动的透明记录——删去了什么、简化了什么、注释了什么——以便教师核验改编是否保留了分析价值"
    - field: "preserved_features"
      type: "array"
      description: "为每项目标技能保留的特征明确清单——例如为精读保留了哪些用词选择、为溯源保留了哪些书目细节"
    - field: "word_bank"
      type: "array"
      description: "改编版本中保留的难词的词汇支持——仅提供定义，不替学生解读文献意义"
    - field: "analytical_value_check"
      type: "object"
      description: "简短核查，确认改编版本仍然支持每一项目标技能——标出改编可能削弱的任何分析动作"
chains_well_with:
  - "document-based-lesson-designer"
  - "historical-document-set-curator"
  - "central-historical-question-evaluator"
  - "sourcing-skill-builder"
  - "close-reading-skill-builder"
  - "text-complexity-analyser"
  - "vocabulary-tiering-tool"
  - "language-demand-analyser"
  - "scaffolded-task-modifier"
teacher_time: "3 分钟"
tags: ["source-adaptation", "historical-thinking", "primary-sources", "accessibility", "disciplinary-literacy", "differentiation", "DIG"]
---

# 历史史料改编器

## 本技能的作用

为课堂使用改编历史一手史料——调整语言复杂度、篇幅与呈现方式，同时保留使文献在历史思维上具有分析价值的特征。输出包括附带完整出处的改编史料、每处改动的透明记录、为每项目标技能保留的特征清单、针对保留难词的词库，以及确认改编版本仍支持预期历史思维技能的分析价值核查。

史料改编的核心张力在于“可及性（accessibility）”与“真实性（authenticity）”之间。被简化成现代白话转述的史料读起来很容易，但在分析上已经死亡——如果作者的用词选择被替换掉了，就没有什么可精读的了；如果古旧措辞被彻底现代化，文献就不再像其所处时代的产物。反之，一份未经修改的 17 世纪文献在语言上可能晦涩难懂，以至于学生把所有认知资源都耗费在解码字面上，无暇顾及分析。目标是找到中间地带：一份学生需要稍加努力才能读懂、但保留了使历史思维成为可能的特征——倾向性语言、出处信息、时代标记、修辞策略——的文献。

Reisman (2012) 在“像历史学家一样阅读”课程中直接应对了这一问题。83 节基于文献的课程使用了“为可及性而修改（modified for accessibility）”的一手史料——针对城市 11 年级学生的阅读水平（其中许多学生阅读水平低于第 25 百分位）进行了改编。关键在于，这些改编保留了文献的分析特征：出处注完整保留、关键用词选择得以保留，且修改过程透明（原文与改编版常并排呈现，如 Wineburg, Martin & Monte-Sano, 2011 的宝嘉康蒂一章）。溯源与精读的显著处理效应表明，精心改编的史料即使对阅读困难学生也能有效支持学科阅读。

## 循证基础

Reisman (2012) 证明，为可及性而修改的一手史料能带来历史思维的显著提升。实验组学生——包括阅读水平低于第 25 百分位的学生——在使用改编文献时，在溯源和精读上均表现出显著进步。RLH 课程中的改编涉及缩短篇幅、为古旧词汇加注以及同时提供原文和改编版——但没有转述作者的声音或删去出处信息。阅读困难学生在实验组中在历史思维（ηp² = .17）和事实知识（ηp² = .22）上均优于对照组，这一发现表明，只要谨慎操作，可及性修改并不会损害分析价值。

Wineburg, Martin & Monte-Sano (2011) 在宝嘉康蒂一章中提供了史料改编的具体范例。史密斯 1608 年和 1624 年的记述同时以原版和改编版呈现，并为古旧术语配备词库。改编版保留了关键分析特征：史料出处（作者、日期、出版物）、形成对比的语言（"kindly" vs. "barbarous"）以及叙事结构。被修改的是句式复杂度和古旧拼写——这些改动降低了字面解码负担，却未改变分析空间。

Wineburg & Reisman (2015) 主张，历史学中的学科素养要求接触作者的真实语言——溯源依赖出处注，精读依赖用词选择，语境化依赖时代标记。通用阅读策略（概括、预测）可以应用于转述后的文献，但学科策略不能。这意味着史料改编必须在修改阻碍阅读的特征的同时，保留学科阅读所瞄准的特征。

Faggella-Luby 等 (2012) 指出，通用阅读策略“甚至可能构成流畅阅读的基石”——无法解码文本的学生就不可能分析文本。这为史料改编提供了依据：如果一份文献在语言上复杂到学生无法流畅阅读，那么依赖流畅阅读的历史思维技能就无从谈起。改编不是向低标准妥协，而是实现学科参与的前提条件。

## 输入模式

教师必须提供：
- **Original source（原始史料）：** 附带完整出处的全文。*例如：史密斯 1624 年《General History》段落全文，附带："John Smith (1624), General History of Virginia, New England and the Summer Isles, Vol. 2, Chapel Hill: University of North Carolina Press, p. 151."*
- **Student level（学生水平）：** *例如："Year 7, average reading age 10–11" / "Year 10, includes several EAL students at intermediate proficiency" / "Year 8, mixed ability with some students reading significantly below age"*
- **Target skills（目标技能）：** 史料必须支持哪些历史思维技能。*例如："Sourcing and close reading" / "All four — this is the main document in a document-based lesson" / "Corroboration — this source will be compared with two others"*

可选：
- **Target length（目标篇幅）：** 改编版本的期望长度
- **Central question（核心问题）：** 探究问题——指导保留哪些内容
- **Key passages（关键段落）：** 必须保留的具体语言
- **EAL considerations（EAL 考量）：** 影响词汇支持程度
- **Paired documents（配对文献）：** 文献集中的其他史料——确保保留互证特征

## Prompt

```
You are an expert in adapting historical primary sources for classroom use, with deep knowledge of how the Reading Like a Historian curriculum (Reisman, 2012; Wineburg, Martin & Monte-Sano, 2011) modified sources for accessibility while preserving their analytical value for historical thinking. You understand the central tension in source adaptation: accessibility vs. authenticity. Your goal is the middle ground — a document students can read with effort that retains the features necessary for sourcing, close reading, contextualisation, and corroboration.

Your task is to adapt the following source:

**Original source:** {{original_source}}
**Student level:** {{student_level}}
**Target skills:** {{target_skills}}

The following optional context may or may not be provided. Use whatever is available.

**Target length:** {{target_length}} — if not provided, use your judgement to reduce the source to a length manageable for the student level while preserving analytical value.
**Central question:** {{central_question}} — if provided, prioritise preserving features that are most relevant to investigating this question.
**Key passages:** {{key_passages}} — if provided, these passages MUST appear in the adapted version with minimal modification.
**EAL considerations:** {{eal_considerations}} — if provided, adjust the word bank and glossing accordingly.
**Paired documents:** {{paired_documents}} — if provided, ensure the adaptation preserves features needed for comparison with these other sources.

Apply these adaptation principles:

1. **Preserve the source note in full.** Author, date, publication context — never simplify, abbreviate, or remove source attribution. This is what students need for sourcing.

2. **Preserve the author's voice.** The adapted version should still sound like the original author, not like a modern textbook. If Smith wrote "barbarous," keep "barbarous" and gloss it in the word bank — do not replace it with "uncivilised." The author's word choices are what students need for close reading.

3. **Preserve analytically significant language.** Identify the words, phrases, and rhetorical features that carry analytical weight for the target skills. These must survive the adaptation. Flag them in the preserved features list.

4. **Simplify sentence structure, not vocabulary.** Long, complex sentences with multiple embedded clauses can be broken into shorter sentences. Archaic syntax can be modernised. But content-bearing vocabulary — especially loaded or evaluative words — should be retained and glossed rather than replaced.

5. **Provide both versions where possible.** For key passages, include the original text alongside the adapted version so students can see what was changed. This models transparency about textual modification — itself a historical thinking principle.

6. **Use a word bank, not inline definitions.** Difficult words should be defined in a separate word bank at the bottom of the source, not replaced or defined inline. Inline definitions interrupt the reading flow and remove the opportunity for students to encounter and wrestle with unfamiliar language.

7. **Mark all cuts and modifications.** Use [...] for omitted passages and (adapted) in the source note to signal that the text has been modified. Transparency about modification is non-negotiable.

8. **Do not interpret the source.** The word bank should define words, not explain what the author meant. "Barbarous: savage, uncivilised" is a definition. "Barbarous: Smith is showing his negative attitude toward the Powhatan" is an interpretation that pre-empts the student's close reading.

Produce the following:

1. **Adapted source:** The modified document with full source attribution, [...] for cuts, and (Adapted) in the source note. Include original and adapted versions of key passages side by side where this is instructive.

2. **Adaptation notes:** A transparent list of every modification, grouped by type:
   - **Cut:** What was removed and why (e.g., "Removed three sentences describing the geography of Werowocomoco — not relevant to the central question and adds length without analytical value")
   - **Simplified:** What was syntactically modified and how (e.g., "Split one 47-word sentence into two shorter sentences — original embedded clause structure exceeded target reading level")
   - **Retained:** What was deliberately kept despite being difficult, and why (e.g., "Retained 'barbarous' — essential for close reading comparison with 'kindly' in the 1608 account")

3. **Preserved features:** For each target skill, list the specific features preserved:
   - **For sourcing:** What source information is retained
   - **For close reading:** Which word choices, rhetorical features, or tone markers are preserved
   - **For contextualisation:** Which temporal or situational markers remain
   - **For corroboration:** Which features enable comparison with paired documents

4. **Word bank:** Definitions for difficult retained vocabulary. Definitions only — no interpretations.

5. **Analytical value check:** For each target skill, confirm that the adapted version still supports it. If any adaptation has compromised a skill, flag it explicitly and explain the trade-off.

Return your output in this exact format:

## Adapted Source

**Source:** [Full attribution with (Adapted) marker]

[Adapted text with [...] for cuts]

**Original version of key passage(s):**
[Side-by-side where instructive]

### Word Bank
[Vocabulary with definitions only]

## Adaptation Notes

**Cut:** [What was removed and why]
**Simplified:** [What was modified and how]
**Retained:** [What was kept despite difficulty, and why]

## Preserved Features

**For sourcing:** [What's preserved]
**For close reading:** [What's preserved]
**For contextualisation:** [What's preserved]
**For corroboration:** [What's preserved]

## Analytical Value Check

[Confirmation for each target skill, with any trade-offs flagged]

**Self-check before returning output:** Verify that (a) the source attribution is complete and unmodified, (b) the author's voice is preserved — the adapted version sounds like the original author, not a textbook, (c) analytically significant language is retained and glossed, not replaced, (d) all modifications are transparently documented, (e) the word bank defines without interpreting, and (f) the analytical value check honestly assesses whether each target skill can still be practised.
```

## 示例输出

**场景：** *Original source: Smith's 1624 General History passage (full archaic text) / Student level: "Year 7, first time working with primary sources, average reading age 10–11" / Target skills: "Sourcing and close reading" / Central question: "Did Pocahontas rescue John Smith?" / Key passages: "'barbarous' and 'Pocahontas the King's dearest daughter, when no entreaty could prevail, got his head in her arms, and laid her own upon his to save him from death'"*

---

## 改编后的史料

**出处：** John Smith (1624), *General History of Virginia, New England and the Summer Isles*, Vol. 2.（改编版）

At last they brought Smith to Meronocomoco, where Powhatan, their Emperor, was waiting. At his entrance, all the people gave a great shout. [...] Having feasted him after their best barbarous manner they could, a long consultation was held. But the conclusion was, two great stones were brought before Powhatan. Then, as many as could laid hands on him, dragged him to them, and laid his head on the stones. Being ready with their clubs to beat out his brains, Pocahontas, the King's dearest daughter, when no entreaty could prevail, got his head in her arms, and laid her own upon his to save him from death. The Emperor was contented that Smith should live.

Two days after, Powhatan [...] came to Smith and told him they were now friends. Soon Smith should go to Jamestown, and send Powhatan two great guns and a grindstone. For this, Powhatan would forever esteem Smith as his son.

**关键段落原版对照：**

| 原文（1624） | 改编版 |
|---|---|
| "having feasted him after their best barbarous manner they could, a long consultation was held, but the conclusion was, two great stones were brought before Powhatan: then, as many as could layd hands on him, dragged him to them, and thereon laid his head, and being ready with their clubs, to beate out his braines, Pocahontas the Kings dearest daughter, when no intreaty could prevaile, got his head in her armes, and laid her owne upon his to save him from death" | "Having feasted him after their best barbarous manner they could, a long consultation was held. But the conclusion was, two great stones were brought before Powhatan. Then, as many as could laid hands on him, dragged him to them, and laid his head on the stones. Being ready with their clubs to beat out his brains, Pocahontas, the King's dearest daughter, when no entreaty could prevail, got his head in her arms, and laid her own upon his to save him from death." |

### 词库

- **barbarous:** 野蛮的、未开化的
- **consultation:** 商议、为决定某事召开的会议
- **entreaty:** 恳切的请求或哀求
- **prevail:** 成功、奏效
- **esteem:** 珍视、敬重
- **contented:** 满意的、愿意同意的

## 改编说明

**删减：** 删去了开头对波瓦坦宫廷的描写（"proudly lying upon a bedstead a foot high upon ten or twelve mats"）——增添了氛围细节，但与核心问题无关。删去了史密斯对波瓦坦“以所能想象的最恐怖方式装扮”的描述——属于次要细节，会增加篇幅却不对营救段落的溯源或精读产生分析价值。

**简化：** 通篇将古旧拼写现代化（layd → laid, braines → brains, intreaty → entreaty, armes → arms, owne → own, prevaile → prevail）。在保留所有实义词的同时，将长达 73 词的营救长句拆分为四个短句。为清晰起见，将 "thereon laid his head" 改为 "laid his head on the stones"。

**保留：** "Barbarous"——对于精读时与 1608 年记述中的 "kindly" 进行对比至关重要。"The King's dearest daughter"——精读关键短语（为什么用 "dearest"？为什么用 "King" 而不是 "chief"？）。"When no entreaty could prevail"——揭示史密斯叙事建构的戏剧性措辞。"Esteem him as his son"——对于“这次相遇意味着什么（收养仪式 vs. 真实威胁）”这一问题至关重要。完整保留史料出处，包括作者、日期和出版物标题。

## 保留的特征

**用于溯源：** 完整出处注（John Smith, 1624, General History of Virginia）。从出处注与时间轴语境中可以清楚看到事件（1607 年）与出版（1624 年）之间相隔 17 年。学生可以识别史密斯既是作者又是故事主人公。

**用于精读：** "Barbarous"（揭示史密斯态度的倾向性语言）；"the King's dearest daughter"（抬升地位的语言）；"when no entreaty could prevail"（戏剧性叙事建构）；"beat out his brains"（制造戏剧效果的暴力意象）；"esteem him as his son"（历史学家有不同阐释的收养语言）。

**用于语境化：** 出处注中保留了日期（1624 年）。段落保留了足够的时代细节（木棒、大石、皇帝、磨刀石），足以将其定位在早期弗吉尼亚殖民时期。

**用于互证：** 改编版保留了与史密斯 1608 年记述差异最大的特征——威胁性语气、营救情节以及 "barbarous" 用词——支持直接对比。

## 分析价值核查

**溯源：** ✓ 完全支持。出处注完整。学生可以识别作者、日期以及作者与事件的关系。

**精读：** ✓ 完全支持。所有在分析上重要的用词选择均已保留。拆句未改变词汇或语气——学生仍然可以分析 "barbarous"、"dearest daughter" 以及戏剧化的营救语言。

**语境化：** ✓ 支持，附带说明。改编版保留了日期和时代标记，但删减减少了有助于学生想象场景的氛围细节。教师可能需要补充关于 Werowocomoco 的简短背景信息。

**互证：** ✓ 完全支持。与 1608 年记述比对的关键特征——对比鲜明的语言（"barbarous" vs. "kindly"）、营救情节的有无、语气转变——全部得以保留。

---

## 已知局限性

1. **每一次改编都伴随权衡。** 简化句式结构可能会削弱原文的修辞力量；删减段落可能会移除与教师尚未预料到的问题相关的语境。提供改编说明正是为了让教师能够评估这些权衡——如果判断原文特征值得学生承担额外阅读难度，可以随时恢复特定改动。

2. **本技能改编文本，而非图像或实物。** 历史史料还包括照片、地图、政治漫画、文物等需要不同改编策略的非文本材料（例如批注、引导观察规程、语境说明）。本技能专为文本一手史料设计。

3. **改编不能替代阅读教学。** 完全无法解码字面的学生，在接触哪怕经过改编的一手史料之前都需要先获得阅读支持。本技能假设学生具备接近其年龄段的阅读能力，瞄准的是通用阅读能力与历史文本特定要求之间的落差。对于阅读水平显著低于年龄段的学生，参见 text-complexity-analyser 与 scaffolded-task-modifier 获取额外支持策略。
