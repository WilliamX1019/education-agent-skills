---
# AGENT SKILLS STANDARD FIELDS (v2)
name: historical-thinking-strategy-modelling-guide
description: "结合具体文献设计示范历史思维策略的教师出声思维（think-aloud）脚本。适用于规划显性策略教学，或学生机械遵循步骤却不理解背后推理时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/historical-thinking-strategy-modelling-guide"
skill_name: "历史思维策略示范指南"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "strong"
evidence_sources:
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Wineburg (1991) — Historical problem solving: cognitive processes in the evaluation of documentary and pictorial evidence"
  - "Wineburg (1998) — Reading Abraham Lincoln: an expert/expert study in historical cognition"
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Gottlieb & Wineburg (2012) — Between Veritas and Communitas: epistemic switching in the reading of academic and sacred history"
  - "Rosenshine (2012) — Principles of instruction: research-based strategies that all teachers should know"
input_schema:
  required:
    - field: "document_description"
      type: "string"
      description: "教师将用于示范的具体历史文献——包括其出处信息（作者、日期、出版背景）以及内容摘要或关键段落"
    - field: "target_strategies"
      type: "string"
      description: "需要示范的历史思维策略——溯源、精读、语境化、互证中的一项或多项。若包含互证，必须描述第二份文献。"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前的历史思维经验水平"
  optional:
    - field: "current_challenge"
      type: "string"
      description: "学生目前遇到的困难——使出声思维能够精准瞄准学生做法与专家读者做法之间的落差"
    - field: "second_document"
      type: "string"
      description: "与第一份文献比对的第二份文献。如果 target_strategies 中列出了互证，则必填——否则无法开展示范。"
    - field: "lesson_context"
      type: "string"
      description: "该示范在课程中的位置——例如开启新文献集、从引导练习过渡到独立练习、演示学生尚未接触过的新策略"
    - field: "prior_instruction"
      type: "string"
      description: "学生已经接受过的策略教学"
output_schema:
  type: "object"
  fields:
    - field: "think_aloud_script"
      type: "string"
      description: "结合指定文献示范目标策略的完整教师出声思维脚本——包含停顿、自问、假设以及对未知的明确界定（specification of ignorance）"
    - field: "cognitive_moves_annotated"
      type: "array"
      description: "附带标注标签以识别每一个认知动作的出声思维脚本——以便教师理解自己正在示范什么，并能向学生明确命名"
    - field: "common_pitfalls"
      type: "array"
      description: "教师在示范历史思维时常犯的错误——例如直接讲述答案而非思考过程、示范过快、不停顿以展示不确定性"
    - field: "transition_to_practice"
      type: "object"
      description: "如何从教师示范过渡到学生引导练习——移交什么、搭建什么支架、观察什么"
chains_well_with:
  - "sourcing-skill-builder"
  - "close-reading-skill-builder"
  - "contextualisation-skill-builder"
  - "corroboration-skill-builder"
  - "document-based-lesson-designer"
  - "historical-source-adapter"
  - "think-aloud-script-generator"
  - "explicit-instruction-sequence-builder"
teacher_time: "3 分钟"
tags: ["modelling", "think-aloud", "historical-thinking", "explicit-instruction", "worked-example", "strategy-instruction", "DIG"]
---

# 历史思维策略示范指南

## 本技能的作用

生成一份结合具体文献示范一项或多项历史思维策略（溯源、精读、语境化、互证）的教师出声思维（think-aloud）脚本。输出包括带有停顿与自言自语的完整脚本、识别每个认知动作的批注、需要避免的常见误区，以及从示范样例过渡到学生练习的指导。

Wineburg 研究的核心洞察在于：专家的历史阅读是不可见的。当历史学家阅读一份文献时，认知工作——在出处注处停顿、从书目信息中生成假设、注意倾向性语言、将文献与其历史时刻相连——都在内部完成。学生看到历史学家阅读然后给出阐释，但阅读与阐释之间的过程是一个黑箱。出声思维的目的正是打开这个黑箱：将内部推理外显化，使学生能够看见、听见并最终复制这一过程。

本技能不同于四个独立的技能构建器（溯源、精读、语境化、互证），后者设计的是完整教学序列；本技能仅生成示范部分——即“我做（I DO）”阶段——但比任何单一技能构建器都更具深度和针对性。它产出一份针对具体文献的、教师可以提前演练并现场演绎的脚本，并附带解释每个动作演示了什么以及为何重要的批注。

Reisman (2012) 发现，显性策略教学——示范、引导练习、独立练习——是“像历史学家一样阅读”课程中教授历史思维技能的教学结构。然而 Reisman 也发现，教师对示范的实施保真度较低：大多数教师在保真度量表上的得分低于基线，全班讨论（示范最可见的场域）更是极少出现。本技能的存在正是为了提供一份具体、可演练的脚本，使示范更易落地，而不必让教师在课堂上即兴发挥专家级历史推理。

## 循证基础

Wineburg (2007) 通过哈里森宣言的案例展示了专家示范能揭示什么。一位博士生的出声思维呈现了一连串认知动作：读到日期、立即激活关于 19 世纪 90 年代的语境知识、将该语境与文献语言相连，并得出关于其政治目的的假设——全部在不到一分钟内完成。这种出声思维显性化了 Wineburg 所称的“无知的明确化（specification of ignorance）”：专家利用文献清晰界定自己不知道、需要进一步查明的内容，而不是急于下结论。

Wineburg (1991, 1998) 通过出声思维研究确立了历史学家在阅读文献时所从事的在质上截然不同的认知过程。这些过程——阅读前先溯源、将语言作为视角证据来关注、将文献与其历史时刻相连、跨史料比对记述——正是示范的目标行为。用于研究专家的出声思维方法论，在“像历史学家一样阅读”课程中转化为用于教授新手的教学方法。

Gottlieb & Wineburg (2012) 表明，专家阅读的质量在于推理的深度，而不在于策略使用的频率。科学家和历史学家可能都会注意到作者姓名，但历史学家会深挖这些信息，推断文本可能的立场。因此，示范不仅要展示动作（看一眼出处注），更要展示推理（在读正文一个字之前，出处信息告诉了你什么）。

Reisman (2012) 通过三段式结构将显性策略教学操作化：教师示范策略、学生在引导下练习、学生独立应用。示范阶段是基础——没有它，学生学会的只是“做什么”（检查出处），而不是“如何思考”（利用出处生成假设）。Reisman 发现教师对完整课堂结构的保真度较低，这表明示范是教师最难落实的环节，很可能是因为它要求教师实时表演专家级历史推理。

Rosenshine (2012) 将示范与出声思维确定为跨领域的十大有效教学原则之一。他指出，当专家的思维无法通过观察其外显行为直接看出时，让认知过程可见对复杂技能尤为重要。历史思维正是这样一种技能——新手与专家阅读同一份文献时的差异完全发生在内部。

## 输入模式

教师必须提供：
- **Document description（文献描述）：** 用于示范的具体文献，包含出处信息与关键内容。*例如："President Benjamin Harrison's 1892 proclamation declaring a national holiday for the 400th anniversary of Columbus's arrival. Source note: 'Benjamin Harrison, Presidential Proclamation, July 21, 1892, published in the New York Times.' Key passage: 'On the 12th day of October, 1892, let the people, so far as possible, cease from toil, and devote themselves to... the world-changing event which shall have been thus commemorated.'"*
- **Target strategies（目标策略）：** 要示范哪些策略。*例如："Sourcing and contextualisation" / "Close reading only" / "All four — sourcing, close reading, contextualisation, then corroboration with a second document"*
- **Student level（学生水平）：** *例如："Year 8, first encounter with think-aloud modelling of historical reading" / "Year 11, familiar with sourcing but need to see contextualisation modelled"*

可选：
- **Current challenge（当前挑战）：** 学生遇到困难的地方——精准定位出声思维
- **Second document（第二份文献）：** 示范互证时必填
- **Lesson context（课堂语境）：** 示范在课中的位置
- **Prior instruction（先前教学）：** 学生已经学过什么

## Prompt

```
You are an expert in historical thinking pedagogy and explicit strategy instruction, with deep knowledge of Wineburg's (1991, 1998, 2007) research on expert historical reading, Reisman's (2012) three-part explicit instruction model (I DO → WE DO → YOU DO), and Rosenshine's (2012) principles of instruction. You understand that the purpose of a think-aloud is to make visible the invisible cognitive processes of expert historical reading — showing students not just WHAT to do (check the source, read closely, contextualise, compare) but HOW to think while doing it.

Your task is to generate a teacher think-aloud script that models historical thinking with a specific document:

**Document description:** {{document_description}}
**Target strategies:** {{target_strategies}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available.

**Current challenge:** {{current_challenge}} — if provided, design the think-aloud to specifically target the gap between what students currently do and what the think-aloud demonstrates.
**Second document:** {{second_document}} — required if corroboration is a target strategy.
**Lesson context:** {{lesson_context}}
**Prior instruction:** {{prior_instruction}}

Generate the following:

1. **Think-aloud script:** A complete, rehearsable teacher script (300–500 words depending on how many strategies are targeted) that models the target strategies with the specified document. The script must:
   - Be written in first person as the teacher speaking aloud to the class
   - Include explicit pauses marked with [PAUSE] where the teacher stops to think visibly
   - Show uncertainty and hypothesis-generation, not just confident interpretation — expert readers don't know the answer immediately; they generate questions and possibilities
   - Demonstrate the "specification of ignorance" (Wineburg, 2007): using the document to articulate what the reader does NOT know and needs to find out
   - Be specific to this document — not a generic demonstration of "how historians read" but a concrete example of what THIS document reveals when read with disciplinary skill
   - If multiple strategies are targeted, show them in the natural order an expert would use them (typically: sourcing → contextualisation → close reading → corroboration), making the transitions between strategies visible

2. **Cognitive moves annotated:** The same script presented a second time with annotations in [brackets] labelling each cognitive move. For example: "Let me look at who wrote this [SOURCING: checking author before reading]. 1892 — what do I know about 1892? [CONTEXTUALISATION: activating period knowledge]." These annotations serve two purposes: they help the teacher understand what they are modelling, and they can be shared with students after the think-aloud to name the strategies explicitly.

3. **Common pitfalls:** 3–4 mistakes teachers commonly make when modelling historical thinking, with guidance on how to avoid them. Include:
   - Narrating the answer rather than the thinking process
   - Modelling too quickly without showing the pauses and uncertainty that characterise genuine expert reasoning
   - Performing confidence rather than demonstrating the productive discomfort of not knowing
   - Modelling strategies generically rather than showing what they reveal with this specific document

4. **Transition to practice:** How to move from the teacher's think-aloud to guided student practice. Specify:
   - What to hand over (which strategy, which document)
   - How to scaffold the transition (e.g., students try the same strategy on a new document with sentence starters; pairs practise while teacher circulates)
   - What to watch for (signs students are replicating the cognitive moves vs. just copying the surface behaviours)

Return your output in this exact format:

## Think-Aloud Modelling Plan

**Document:** [Brief description]
**Target strategies:** [List]
**Students:** [Level]

### Think-Aloud Script

[Complete script with [PAUSE] markers, written in first person as the teacher speaking aloud]

### Cognitive Moves Annotated

[Same script with [STRATEGY: description] annotations after each move]

### Common Pitfalls

[3–4 pitfalls with guidance]

### Transition to Practice

**Hand over:** [What students will now try]
**Scaffold:** [How to support the transition]
**Watch for:** [Signs of genuine vs. surface-level replication]

**Self-check before returning output:** Verify that (a) the script is specific to this document, not generic, (b) the script shows uncertainty and hypothesis-generation, not just confident analysis, (c) the annotations correctly label each cognitive move, (d) the pitfalls address the difference between narrating answers and modelling thinking, and (e) the transition to practice specifies what genuine replication of the modelled thinking looks like.
```

## 示例输出

**场景：** *Document: "John Smith's 1624 General History passage describing his capture and rescue by Pocahontas. Source note: 'John Smith (1624), General History of Virginia, New England and the Summer Isles, Vol. 2, Chapel Hill: University of North Carolina Press, p. 151.' Key passage: 'having feasted him after their best barbarous manner they could, a long consultation was held, but the conclusion was, two great stones were brought before Powhatan: then, as many as could laid hands on him, dragged him to them, and thereon laid his head, and being ready with their clubs, to beat out his brains, Pocahontas the King's dearest daughter, when no entreaty could prevail, got his head in her arms, and laid her own upon his to save him from death.'" / Target strategies: "Sourcing and close reading" / Student level: "Year 8, first encounter with think-aloud modelling of historical reading"*

---

## 出声思维示范方案

**文献：** 史密斯 1624 年《General History》——宝嘉康蒂营救段落
**目标策略：** 溯源与精读
**学生：** 八年级，首次接触示范性历史阅读

### 出声思维脚本

"Before I read this, I'm going to do what historians do — look at who wrote it and when. It says John Smith, 1624. [PAUSE] OK. John Smith is the person this story is about. He's writing about himself. That immediately makes me pay attention, because when someone tells a story where THEY are the hero, I want to think about why they're telling it that way.

1624. The event was supposed to have happened in 1607. That's a 17-year gap. [PAUSE] I'm trying to think — do I remember what happened 17 years ago? Not very well. So either Smith has an extraordinary memory, or he's reconstructing. And here's something else I know: Pocahontas went to England in 1616 and became very famous before she died in 1617. By 1624, she's a well-known figure. Is Smith attaching his name to her fame? I don't know yet. But I'm going to read with that question in mind.

Now let me read the passage. 'Having feasted him after their best barbarous manner they could.' [PAUSE] I'm stopping at 'barbarous.' That's a strong word. Smith could have said 'their traditional manner' or 'their customary manner.' He chose 'barbarous.' That tells me something about how he wants his readers to see the Powhatan people — as savage, uncivilised. Why? [PAUSE] Maybe because it makes the rescue more dramatic. You need danger to have a rescue.

'Pocahontas the King's dearest daughter, when no entreaty could prevail, got his head in her arms and laid her own upon his to save him from death.' [PAUSE] 'The King's dearest daughter.' That's significant. Not just 'a girl' or 'Powhatan's daughter' — 'the King's DEAREST daughter.' Smith is elevating Pocahontas. And by making her the one who saved him, he's also elevating himself — he's important enough that a princess risked her life for him.

So here's what I'm thinking after reading this: I don't know whether this happened. But I do know that Smith had reasons to tell this story in 1624 — reasons that have nothing to do with what actually happened in 1607. The question I want to investigate next is: did Smith mention this rescue in his FIRST account, written in 1608? If he didn't, that would be very interesting."

### 认知动作批注版

"Before I read this, I'm going to do what historians do — look at who wrote it and when. [溯源：阅读内容前先检查作者与日期] It says John Smith, 1624. [PAUSE] OK. John Smith is the person this story is about. He's writing about himself. [溯源：识别作者与事件的关系] That immediately makes me pay attention, because when someone tells a story where THEY are the hero, I want to think about why they're telling it that way. [溯源：推理作者立场如何塑造记述]

1624. The event was supposed to have happened in 1607. That's a 17-year gap. [溯源：推理事件与记述之间的时间距离] [PAUSE] I'm trying to think — do I remember what happened 17 years ago? Not very well. [溯源：借助个人经验评估详细回忆的可信度] So either Smith has an extraordinary memory, or he's reconstructing. And here's something else I know: Pocahontas went to England in 1616 and became very famous before she died in 1617. [语境化：激活时代背景知识] By 1624, she's a well-known figure. Is Smith attaching his name to her fame? [溯源 + 语境化：从语境中生成关于动机的假设] I don't know yet. But I'm going to read with that question in mind. [无知的明确化：将假设保持为问题而非结论]

Now let me read the passage. 'Having feasted him after their best barbarous manner they could.' [PAUSE] I'm stopping at 'barbarous.' [精读：关注具体用词选择] That's a strong word. Smith could have said 'their traditional manner' or 'their customary manner.' He chose 'barbarous.' [精读：思考替代用词以揭示实际用词的意义] That tells me something about how he wants his readers to see the Powhatan people — as savage, uncivilised. Why? [精读：将用词选择与作者目的相连] [PAUSE] Maybe because it makes the rescue more dramatic. You need danger to have a rescue. [精读：推理修辞策略]

'Pocahontas the King's dearest daughter, when no entreaty could prevail, got his head in her arms and laid her own upon his to save him from death.' [PAUSE] 'The King's dearest daughter.' [精读：关注特定短语] That's significant. Not just 'a girl' or 'Powhatan's daughter' — 'the King's DEAREST daughter.' Smith is elevating Pocahontas. [精读：分析语言选择如何建构叙事] And by making her the one who saved him, he's also elevating himself. [精读 + 溯源：将语言与作者的自利动机相连]

So here's what I'm thinking after reading this: I don't know whether this happened. [无知的明确化：保持不确定性而非急于下判断] But I do know that Smith had reasons to tell this story in 1624 — reasons that have nothing to do with what actually happened in 1607. The question I want to investigate next is: did Smith mention this rescue in his FIRST account, written in 1608? If he didn't, that would be very interesting. [无知的明确化 + 桥接至互证：生成下一个探究问题]"

### 常见误区

**1. 直接讲述答案，而不是示范思考过程**
*错误做法：* 教师说 "Smith wrote this in 1624, which was 17 years after the event, and by that time Pocahontas was famous, so he was probably trying to capitalise on her fame." 这直接抛出了阐释结果，却没有展示教师是如何推导出它的。
*修正：* 放慢速度。展示产生这一阐释的思考过程。在 "1624" 处停顿，显性地计算时间差，出声怀疑自己是否能记住 17 年前的细节，回想起宝嘉康蒂赴英成名的背景，然后再提出假设。过程本身才是教学重点，而非结论。

**2. 表演胸有成竹，而不是示范建设性的不确定性**
*错误做法：* 教师把每一步都讲得像答案显而易见："Of course Smith chose 'barbarous' to make the rescue seem more dramatic." 这示范的是确定性，与真正的专家历史推理恰好相反。
*修正：* 刻意使用不确定性表达："Maybe... I wonder... That could mean... I'm not sure yet, but..." 专家读者生成的是假设，而非结论。学生需要看到，不知道答案是一种富有成效的状态，而非失败。

**3. 匆匆扫过出处注**
*错误做法：* 教师瞥一眼出处注说 "OK, it's by John Smith in 1624"，然后立即开始读正文。溯源动作被表演了，但没有被真正示范——学生看到你检查了出处，却没看到检查出处对阅读“起了什么作用”。
*修正：* 仅在出处注上就至少花 60 秒。在触碰正文之前，单从出处注中生发出多个观察与问题。相对于出处注极少的字数而言，在上面花费“不成比例”的时间本身就是一堂课：这短短几行信息彻底改变了你阅读下文的方式。

**4. 在同一详略度上同时示范所有策略**
*错误做法：* 试图在一次出声思维里同时演示溯源、精读、语境化和互证，结果变成一场 15 分钟的漫长表演，每项策略都流于表面。
*修正：* 每次示范聚焦一到两项策略并讲深讲透。让学生看到结合一份文献把溯源示范得淋漓尽致，远胜于蜻蜓点水地把四项策略都过一遍。

### 向练习过渡

**移交内容：** 学生拿到史密斯 1608 年的《True Relation》——同一事件的早期记述。他们的任务是对这份文献做教师刚才示范的事情：先检查出处注、从中提出问题，然后再阅读正文并关注具体用词选择。

**支架：** 提供呼应教师出声思维的句首提示："This was written by ___ in ___. That makes me wonder..." / "I notice the word ___. The author could have said ___ instead, which suggests..." 学生结对练习，互相出声说出阅读过程。教师巡视并倾听认知动作，而不仅仅是正确答案。

**观察重点：** 区分复制“认知动作”的学生与仅仅复制“表面套话”的学生。说 "I notice the word 'kindly' — the author could have said something else" 的学生只是在套用句式结构；而说 "Smith says 'kindly' here, but in the 1624 version he says 'barbarous' for the same meeting — so one of these descriptions is being shaped by something other than what actually happened" 的学生才是在复制认知动作。后者理解了语言是视角的证据，前者只是在不理解目的的情况下表演策略。

---

## 已知局限性

1. **出声思维脚本只是起点，而非成品演出。** 教师必须演练脚本、内化其推理并用自己的声音表达出来。对着学生照念脚本不是示范——只是朗读。认知动作必须显得真实自然，这要求教师理解自己“为什么”在此停顿、提问和提出假设，而不仅仅是知道“应该”这样做。

2. **本技能仅生成示范部分。** 它不负责设计完整的课程结构（参见 document-based-lesson-designer）或跨时间的技能发展序列（参见各独立技能构建器）。示范是“我做（I DO）”阶段；随后的引导练习与独立练习需要单独设计，不过“向练习过渡”部分提供了初步指导。

3. **示范历史思维要求教师自身具备专家阅读所依托的历史知识。** 示例中展示的语境化（将 1624 年日期与宝嘉康蒂 1616 年访英联系起来）要求教师知道这一史实。如果教师缺乏相关背景知识，出声思维就会显得单薄。教师在示范前应先阅读文献的史学背景——这是备课工作的一部分，而非本技能的局限。
