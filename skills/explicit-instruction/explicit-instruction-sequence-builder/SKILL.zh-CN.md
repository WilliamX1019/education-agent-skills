---
# AGENT SKILLS STANDARD FIELDS (v2)
name: explicit-instruction-sequence-builder
description: "构建从教师示范、引导练习到独立练习的完整显性教学序列。适用于通过直接教学法教授新技能、程序或概念时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "explicit-instruction/explicit-instruction-sequence-builder"
skill_name: "显性教学序列构建器（我做 / 我们做 / 你做）"
domain: "explicit-instruction"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Rosenshine (2012) — Principles of Instruction: research-based strategies that all teachers should know"
  - "Pearson & Gallagher (1983) — The instruction of reading comprehension (gradual release of responsibility model)"
  - "Archer & Hughes (2011) — Explicit Instruction: Effective and Efficient Teaching"
  - "Hattie (2009) — Visible Learning: direct instruction effect size 0.59"
  - "Engelmann & Carnine (1982) — Theory of Instruction: principles and applications"
input_schema:
  required:
    - field: "skill_to_teach"
      type: "string"
      description: "需要通过显性教学教授的具体技能或概念"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及先验知识水平"
    - field: "lesson_time"
      type: "string"
      description: "可用课时（分钟）"
  optional:
    - field: "common_misconceptions"
      type: "array"
      description: "学生在该技能上常见的已知误区或错误"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：能力范围、EAL 需求、SEND 档案"
    - field: "prior_knowledge"
      type: "string"
      description: "学生已经掌握且本课以此为基础的知识"
    - field: "success_criteria"
      type: "string"
      description: "来自上下文引擎：如何衡量成功"
output_schema:
  type: "object"
  fields:
    - field: "i_do"
      type: "object"
      description: "教师示范阶段，包含脚本化讲解与出声思维"
    - field: "we_do"
      type: "object"
      description: "引导练习阶段，包含结构化的师生互动"
    - field: "you_do"
      type: "object"
      description: "独立练习阶段，包含监控检查点"
    - field: "cfu_points"
      type: "array"
      description: "贯穿全程的理解检查（CFU）节点"
    - field: "timing_guide"
      type: "string"
      description: "跨越三个阶段的建议时间分配"
chains_well_with:
  - "checking-for-understanding-protocol-designer"
  - "worked-example-fading-designer"
  - "think-aloud-script-generator"
  - "practice-problem-sequence-designer"
  - "pedagogical-content-knowledge-developer"
teacher_time: "5 分钟"
tags: ["explicit-instruction", "gradual-release", "modelling", "direct-instruction", "scaffolding"]
---

# 显性教学序列构建器（我做 / 我们做 / 你做）

## 本技能的作用

为教授特定技能生成一套完整的责任逐步移交（gradual release of responsibility）序列：脚本化的“我做（I Do）”（教师示范并伴随出声思维）、结构化的“我们做（We Do）”（师生互动的引导练习），以及精心设计的“你做（You Do）”（附带监控点的独立练习）。输出包括每个过渡节点上的理解检查以及时间分配指南。AI 在此尤为有价值，因为有效的显性教学要求教师将隐形的专家思维显性化——把一项教师已自动化执行的技能拆解为离散、可教的步骤并清晰阐述其推理过程。这种对专家表现的拆解具有很高的认知负荷，也正是大多数显性教学流于表面的原因。

## 循证基础

Rosenshine (2012) 将数十年研究综合为十大教学原则，其核心正是显性教学：以简短复习开始、分小步呈现新材料并在每步后练习、提供示范、引导练习、检查理解以及获得高成功率。Pearson & Gallagher (1983) 正式提出了责任逐步移交模型——教师最初承担全部认知负荷（我做），随后逐步与学生分担（我们做），最终完全移交给学生（你做）。Archer & Hughes (2011) 将显性教学操作化，强调“我做”阶段不仅要演示操作，还必须阐述决策过程——学生需要听到每一步“为什么”这样做，而不仅仅是看到操作本身。Hattie (2009) 发现直接教学（direct instruction）的效应量为 0.59，始终位列影响力最高的教学方法之一。Engelmann & Carnine (1982) 确立了显性教学中例题的顺序与结构会显著影响学习效果——必须精心挑选例题，以凸显关键特征并减少歧义。

## 输入模式

教师必须提供：
- **Skill to teach（要教授的技能）：** 具体技能或概念。*例如："Writing a topic sentence for an analytical paragraph" / "Converting between fractions, decimals, and percentages" / "Setting up a Bunsen burner safely"*
- **Student level（学生水平）：** 年级与先验知识。*例如："Year 8, can write paragraphs but don't structure analytical writing" / "Year 7, first time using lab equipment"*
- **Lesson time（课时）：** 可用分钟数。*例如："50 minutes" / "60 minutes"*

可选（如上下文引擎可用则自动注入）：
- **Common misconceptions（常见误区）：** 该技能的已知错误
- **Student profiles（学生档案）：** 能力范围、EAL 需求、SEND 档案
- **Prior knowledge（先验知识）：** 学生已知的内容
- **Success criteria（成功标准）：** 如何衡量成功

## Prompt

```
You are an expert in explicit instruction and the gradual release of responsibility model, with deep knowledge of Rosenshine's (2012) Principles of Instruction, Pearson & Gallagher's (1983) gradual release framework, and Archer & Hughes' (2011) work on effective modelling. You understand that the critical quality of explicit instruction is making expert thinking visible — not just showing students what to do, but articulating the decision-making process behind each step.

Your task is to design a complete I Do / We Do / You Do sequence for:

**Skill:** {{skill_to_teach}}
**Student level:** {{student_level}}
**Lesson time:** {{lesson_time}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Common misconceptions:** {{common_misconceptions}} — if not provided, identify the most likely misconceptions for this skill based on your subject knowledge and address them in the modelling phase.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical mixed-ability class and note where differentiation would be needed.
**Prior knowledge:** {{prior_knowledge}} — if not provided, state the assumed prerequisite knowledge explicitly so the teacher can verify.
**Success criteria:** {{success_criteria}} — if not provided, generate clear success criteria that describe what successful performance looks like at the end of the lesson.

Apply these evidence-based principles:

1. **I Do — Teacher models with think-aloud (Rosenshine, 2012; Archer & Hughes, 2011):**
   - Demonstrate the complete skill from start to finish.
   - Articulate your thinking at EVERY decision point — not just what you're doing, but WHY. "I'm choosing this word because..." / "At this point I need to decide between X and Y, and I choose X because..."
   - Highlight critical features: what makes this different from similar tasks.
   - Show common errors and explain why they're wrong (inoculation against misconceptions).
   - Keep it concise — modelling should be 10–15 minutes maximum. Students learn by doing, not by watching.

2. **We Do — Guided practice with high interaction (Rosenshine, 2012, Principle 4):**
   - Teacher and students work through a new example TOGETHER.
   - Teacher does the early steps, students take over progressively.
   - Use frequent checking: "What should I do next?" / "Why did I choose that?" / cold-calling for responses.
   - This is NOT the teacher doing another example while students watch. Students must be actively contributing.
   - Aim for 80%+ success rate before moving to You Do (Rosenshine, 2012, Principle 7).

3. **You Do — Independent practice with monitoring (Rosenshine, 2012, Principles 5 & 8):**
   - Students practise independently. The teacher circulates and monitors.
   - Begin with problems very similar to the modelled example, then gradually vary.
   - Include a monitoring plan: what to look for, when to intervene, how to identify students who need re-teaching.
   - Build in a checkpoint: after 5 minutes of independent work, quick whole-class check before students continue.

4. **Checking for Understanding at each transition (Rosenshine, 2012, Principle 3):**
   - Between I Do and We Do: "Before we try one together, tell your partner: what is the first step?"
   - Between We Do and You Do: "Give me a thumbs up if you could do the next one on your own, sideways if you need one more guided example, down if you're not sure."
   - During You Do: circulate and check 5 specific students' work within the first 3 minutes.

5. **Time allocation (Archer & Hughes, 2011):**
   - I Do: ~20% of lesson time
   - We Do: ~30% of lesson time
   - You Do: ~40% of lesson time
   - Transitions and CFU: ~10%
   - If time is short, compress I Do (not We Do or You Do — students need practice time).

Return your output in this exact format:

## Explicit Instruction Sequence: [Skill Name]

**For:** [Student level]
**Time:** [Lesson time]
**Success criteria:** [What students will be able to do by the end]

### Prerequisites
[What students need to know before this lesson — teacher should verify]

### I Do — Teacher Models (approx. X minutes)

**Setup:** [How to frame the skill and connect to prior knowledge]
**Model:** [Step-by-step demonstration with think-aloud script at each decision point]
**Common error inoculation:** [Show a common mistake and explain why it's wrong]

**CFU checkpoint:** [Quick check before moving to We Do]

### We Do — Guided Practice (approx. X minutes)

**Example:** [A new example for guided practice]
**Interaction plan:** [Which steps the teacher does, which students contribute, how to elicit responses]
**Scaffolding notes:** [Support for students who are struggling / extension for those who are ready]

**CFU checkpoint:** [Check readiness for independent practice]

### You Do — Independent Practice (approx. X minutes)

**Practice set:** [4–6 practice problems/tasks, sequenced from similar-to-model to varied]
**Monitoring plan:** [What to look for, which students to check first, intervention triggers]
**Early finisher extension:** [What to do with students who finish quickly]

### Differentiation Notes
[How to adjust for different ability levels without changing the learning intention]

**Self-check before returning output:** Verify that (a) the I Do phase includes think-aloud reasoning at every decision point, not just demonstration, (b) the We Do phase requires active student contribution, not passive watching, (c) the You Do practice problems progress from similar-to-model to varied, (d) CFU checkpoints are embedded at each transition, (e) timing is realistic for the stated lesson length, and (f) common misconceptions are addressed during modelling, not left for students to discover.
```

## 示例输出

**场景：** *Skill: "Writing a topic sentence for an analytical paragraph in English Literature" / Student level: "Year 9, can write paragraphs but topic sentences are typically descriptive rather than analytical" / Lesson time: "50 minutes"*

---

## 显性教学序列：撰写分析性主题句

**适用对象：** 九年级英国文学
**时间：** 50 分钟
**成功标准：** 学生能够写出一个主题句，对作者的写作手法或意图提出分析性主张——而不是对文本情节的描述性陈述。

### 先备知识
学生应当能够：写出完整的句子、从文本中找出引文，并理解人物行为与作者选择之间的区别。教师应通过一个快速提问进行核查："What's the difference between saying 'Macbeth kills Duncan' and 'Shakespeare presents Macbeth as increasingly corrupted by ambition'?"

### 我做（I Do）——教师示范（10 分钟）

**导入（2 分钟）：**
"Today I'm going to teach you how to write the first sentence of an analytical paragraph — the topic sentence. This is the sentence that tells the reader what your paragraph will argue. The key word is *argue*. Your topic sentence is a claim, not a description. Watch what I do, and listen to my thinking."

**示范（6 分钟）：**

"I'm writing about how Shakespeare presents Lady Macbeth's ambition in Act 1. Let me write a topic sentence.

My first instinct is: 'In Act 1, Lady Macbeth is very ambitious.' Let me check — is this a claim or a description? It's a description. It tells you what Lady Macbeth is like, but it doesn't say anything about what Shakespeare is DOING. I need to shift from character to writer.

Let me try again: 'Shakespeare presents Lady Macbeth's ambition as more ruthless and calculated than Macbeth's own, using her soliloquy in Act 1, Scene 5 to reveal a character who consciously chooses to suppress her humanity.'

Now let me check this against my criteria:
- Does it name the writer? Yes — 'Shakespeare presents.'
- Does it make a claim that could be argued? Yes — someone could disagree that her ambition is 'more ruthless' or that she 'consciously chooses.'
- Does it point to a method? Yes — 'using her soliloquy' tells the reader I'll be analysing specific language.
- Could I write a whole paragraph developing this idea? Yes — I'd analyse the 'unsex me here' speech.

That's a strong topic sentence. Now let me show you a common mistake."

**常见错误免疫（2 分钟）：**
"Here's what most Year 9 students write: 'In Act 1, Lady Macbeth reads a letter and then asks the spirits to unsex her.'

This is a description of what happens. It's accurate. It's also useless as a topic sentence because there's nothing to argue — it's just a plot summary. Notice the difference:
- Description: 'Lady Macbeth asks the spirits to unsex her.' (What happens)
- Analysis: 'Shakespeare uses Lady Macbeth's invocation of dark spirits to suggest that ambition in this play requires the destruction of feminine compassion.' (What the writer is doing and why)

The shift is from CHARACTER to WRITER. From WHAT HAPPENS to WHY THE WRITER MADE IT HAPPEN."

**理解检查节点：**
"Turn to your partner. Tell them: what is the difference between a descriptive topic sentence and an analytical one? You have 30 seconds." 随机点名 2 名学生分享。倾听要点：是否提及作者的选择/手法，而非仅仅人物行为/情节。

### 我们做（We Do）——引导练习（15 分钟）

**例题：** "Now let's write one together. The question is: How does Shakespeare present the theme of violence in Act 3, Scene 1?"

**互动计划：**

*第 1 步——教师引导：* "What's the first thing I need in my topic sentence? I need to name the writer. So I'm starting with 'Shakespeare...' What verb comes next? Not 'writes about' — that's too vague. Give me a stronger verb." 引导学生回答：presents / conveys / demonstrates / reveals / constructs。"Good — 'Shakespeare presents...' What does he present?"

*第 2 步——学生在支持下贡献：* "Now I need a claim about violence in Act 3, Scene 1. Don't describe what happens — make an argument about what Shakespeare is DOING with violence. Write a claim on your whiteboard." 学生书写，教师扫视白板，挑选一个强例和一个弱例（匿名）。"This one says 'violence as an inevitable consequence of unchecked masculinity.' That's a claim — someone could argue the opposite. This one says 'Tybalt and Romeo fight and Mercutio dies.' That's a description. Let's upgrade it together — what is Shakespeare saying about violence through this scene?"

*第 3 步——学生主导：* "Now add a reference to method. How does Shakespeare present this? What technique or structural choice? Write the complete topic sentence." 学生书写。教师巡视并阅读 6–8 块白板。全班分享并评估：是否点出了作者、提出了主张并指向了写作手法？

**支架说明：**
- 遇到困难的学生：提供句式框架："Shakespeare presents [theme] as [claim] through [method], suggesting that [interpretation]."
- 准备好迎接挑战的学生：能否写出承认反方观点的主题句？"While Shakespeare initially presents violence as... , Act 3, Scene 1 reveals..."

**理解检查节点：**
"Thumbs up if you could write the next topic sentence on your own. Sideways if you'd like one more example together. Down if you're stuck." 如果超过 30% 比出横放或向下，再一起做一个引导例题。如果 80% 以上比出大拇指向上，进入“你做”。

### 你做（You Do）——独立练习（20 分钟）

**练习题组：**

1. 为以下问题写一个主题句："How does Shakespeare present Mercutio as a contrast to Romeo?" *（与示范例题高度相似——同一文本、同一技能）*
2. 为以下问题写一个主题句："How does Steinbeck present loneliness in the opening of Of Mice and Men?" *（同一技能，不同文本——检验迁移）*
3. 为以下问题写一个主题句："How does the poet present the experience of conflict in 'Bayonet Charge'?" *（同一技能，诗歌语境——进一步迁移）*
4. **挑战题：** 为同一个问题写出两个备选主题句。哪一个更强？批注说明原因。

**监控计划：**
- 前 3 分钟：检查你最关注的 5 名学生（在上一环节比出横放或向下的学生）。阅读他们的第一句话。如果是描述性而非分析性的，立即介入并提供句式框架支架。
- 第 5 分钟：全班暂停。"Read your first topic sentence to your partner. Partner, tell them: does it name the writer, make a claim, and point to method? If it doesn't, fix it now."
- 第 5–20 分钟：系统巡视。留意常见错误（用描述代替分析）。收集 2–3 个优秀示例和 1 个薄弱示例，用于最后 5 分钟的全班反馈。

**早完成者拓展：**
为你自选的一门学科（历史、科学、地理）写一个主题句，使用相同的分析性结构：点出创造者/作者/成因、提出主张，并指向方法或机制。这检验学生是否掌握了可迁移的技能，而不仅仅是英国文学中的套路。

### 分层教学说明

- **支持：** 句式框架（"Shakespeare presents [theme] as [claim] through [method]"）在“你做”全程对需要的学生保持可用。这是搭建支架，而非降低任务要求——他们依然在提出分析性主张，只是获得了结构支持。
- **EAL 学生：** 课前预教分析性动词（presents、conveys、reveals、constructs、demonstrates）及定义，或在任务期间提供词库。
- **拓展：** 挑战学生写出嵌入让步或反驳的主题句（"Although... , Shakespeare ultimately presents..."）。这在保持相同分析技能的同时增加了句法复杂度。

---

## 已知局限性

1. **显性教学对步骤明确、成功标准清晰的技能最为有效。** 撰写分析性主题句可以拆解为步骤。创意写作、开放式问题解决以及存在多种有效路径的任务，则不太适合僵化的“我做 / 我们做 / 你做”序列。对于开放式任务，示范阶段应当展示决策过程，而非单一的“标准做法”。

2. **“我做”阶段的质量完全取决于教师清晰阐述思维的能力。** 脚本提供了范本，但教师必须用自己的话语来表达，并根据学生反应灵活调整。机械照本宣科的脚本，远不如略显朴实但真实自然的出声思维。教师应当演练出声思维，而不是照着稿子念。

3. **“我们做”阶段存在过度搭建支架的风险。** 如果教师包办过多、学生贡献过少，“引导练习”就会变成第二次演示。互动计划指明了学生接手的节点，但教师在学生犹豫时必须克制立即插手的冲动——只要成功率保持在 80% 以上，“我们做”阶段适度的建设性挣扎是恰当的。
