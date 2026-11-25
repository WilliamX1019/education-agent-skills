---
# AGENT SKILLS STANDARD FIELDS (v2)
name: think-aloud-script-generator
description: "编写教师出声思维（think-aloud）脚本，展示特定任务背后的专家推理过程。适用于示范问题解决、写作、阅读理解或分析过程时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "explicit-instruction/think-aloud-script-generator"
skill_name: "出声思维脚本生成器"
domain: "explicit-instruction"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Bereiter & Scardamalia (1987) — The Psychology of Written Composition: making expert processes visible"
  - "Wilhelm (2001) — Improving Comprehension with Think-Aloud Strategies"
  - "Ericsson & Simon (1993) — Protocol Analysis: verbal reports as data (theoretical foundation)"
  - "Collins et al. (1989) — Cognitive Apprenticeship: teaching the crafts of reading, writing, and mathematics"
  - "Rosenshine (2012) — Principles of Instruction, Principle 4: provide models of worked-out problems"
input_schema:
  required:
    - field: "task_to_model"
      type: "string"
      description: "教师将通过出声思维示范的具体任务"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及专长水平"
    - field: "subject_area"
      type: "string"
      description: "学科语境"
  optional:
    - field: "expert_strategies"
      type: "array"
      description: "教师希望显性呈现的具体策略或决策点"
    - field: "common_student_errors"
      type: "array"
      description: "学生通常犯的、出声思维应加以预防的错误"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：理解水平、EAL 需求"
    - field: "think_aloud_duration"
      type: "string"
      description: "目标时长（分钟）"
output_schema:
  type: "object"
  fields:
    - field: "script"
      type: "string"
      description: "包含决策点、自我监控和错误意识的完整出声思维脚本"
    - field: "visible_strategies"
      type: "array"
      description: "脚本中显性呈现的专家策略清单"
    - field: "pause_points"
      type: "array"
      description: "暂停并检查学生是否跟上的节点"
    - field: "delivery_notes"
      type: "string"
      description: "如何有效实施出声思维的建议"
chains_well_with:
  - "explicit-instruction-sequence-builder"
  - "worked-example-fading-designer"
  - "metacognitive-prompt-library"
  - "reading-comprehension-strategy-selector"
  - "pedagogical-content-knowledge-developer"
  - "critical-thinking-task-designer"
teacher_time: "4 分钟"
tags: ["think-aloud", "modelling", "expert-thinking", "cognitive-apprenticeship", "comprehension"]
---

# 出声思维脚本生成器

## 本技能的作用

编写一份教师出声思维（think-aloud）脚本，将特定任务——问题解决、阅读、写作、分析或任何专家思维通常不可见的认知技能——背后的专家认知过程显性化。脚本明确阐述了专家已自动化使用却极少口头表达的决策点、自我监控时刻以及错误检测策略。AI 在此尤为有价值，因为出声思维示范的核心难点在于“专家盲点（expert blind spot）”——专家已将自己的思维高度自动化，以至于不再能说清中间步骤。数学教师“一眼就能看出”某道题需要因式分解；熟练读者“直觉就知道”某个信息来源不可靠。出声思维脚本将这种自动化的专长逆向拆解为可教授的步骤。

## 循证基础

Collins 等 (1989) 确立了认知学徒制（cognitive apprenticeship）框架，旨在向新手显性呈现专家思维。核心洞察在于：在传统手艺中，学习是可见的（你可以看着木匠刨木头），但在学术学科中，关键工作发生在专家的脑海里，对学生而言是不可见的。出声思维让不可见变为可见。Bereiter & Scardamalia (1987) 将此应用于写作，证明专家写作者会进行“知识转化”过程（规划、监控、修改），而新手写作者往往完全跳过这一过程——通过出声思维示范这一过程能显著提升学生写作水平。Wilhelm (2001) 表明教师出声思维在多项研究中提升了阅读理解能力，尤其对缺乏元认知监控策略的阅读困难学生效果显著。Ericsson & Simon (1993) 提供了理论基础，证明对思维的口头报告（当同步而非事后回顾时）是认知过程的有效表征。Rosenshine (2012) 将提供示范列为有效教学原则第 4 条，指出最有效的教师会“出声思考并示范步骤”，而不仅仅是解释程序。

## 输入模式

教师必须提供：
- **Task to model（要示范的任务）：** 需要出声思维的具体任务。*例如："Reading and annotating an unseen poem for the first time" / "Solving a multi-step trigonometry problem" / "Evaluating the reliability of a historical source"*
- **Student level（学生水平）：** 年级与专长水平。*例如："Year 10, developing readers — can decode but don't actively monitor comprehension" / "Year 8, novice problem-solvers"*
- **Subject area（学科领域）：** 学科语境。*例如："GCSE English Literature" / "Year 9 Mathematics"*

可选（如上下文引擎可用则自动注入）：
- **Expert strategies（专家策略）：** 要显性呈现的具体策略
- **Common student errors（常见学生错误）：** 要预防的错误
- **Student profiles（学生档案）：** 理解水平、EAL 需求
- **Think-aloud duration（出声思维时长）：** 目标分钟数

## Prompt

```
You are an expert in cognitive apprenticeship and think-aloud modelling, with deep knowledge of Collins et al.'s (1989) cognitive apprenticeship framework, Bereiter & Scardamalia's (1987) work on making expert writing processes visible, and Wilhelm's (2001) research on think-aloud strategies for reading. You understand the "expert blind spot" — the phenomenon where experts have automated their thinking so thoroughly that they can no longer articulate the intermediate steps novices need to see.

Your task is to write a think-aloud script for:

**Task:** {{task_to_model}}
**Student level:** {{student_level}}
**Subject:** {{subject_area}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Expert strategies:** {{expert_strategies}} — if not provided, identify the 3–5 most important expert strategies for this task type and make them visible in the script.
**Common student errors:** {{common_student_errors}} — if not provided, identify the most common errors students make with this task type and include moments in the script where the expert catches and avoids them.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class with students who perform the task mechanically without monitoring their thinking.
**Think-aloud duration:** {{think_aloud_duration}} — if not provided, design for 8–10 minutes (long enough to model the full process, short enough to maintain attention).

Apply these evidence-based principles:

1. **Make decisions visible, not just actions (Collins et al., 1989):**
   - An action: "Now I underline this phrase."
   - A decision made visible: "I'm re-reading this line because something doesn't make sense yet. I expected the poet to continue the positive imagery, but this word 'shattered' breaks the pattern. That's important — let me underline it and write 'tone shift?' in the margin."
   - Every action in the script must be preceded by the reasoning that drives it.

2. **Show self-monitoring (Bereiter & Scardamalia, 1987):**
   - Experts constantly monitor their own comprehension and progress. Make this visible:
   - "Wait — do I actually understand this line? Let me try to paraphrase it... No, I can't. That means I need to re-read it more carefully."
   - "I've been working for 5 minutes and I've only done one paragraph. Am I spending too long, or is this the right depth for this task?"

3. **Show error detection and recovery (Wilhelm, 2001):**
   - Experts make errors and catch them. Show this:
   - "My first thought is to add these two numbers, but wait — that doesn't seem right because the answer would be larger than... Let me re-read the question."
   - Do NOT present a flawless performance. Show a realistic process with wrong turns and corrections.

4. **Distinguish "doing the task" from "showing how to think through the task":**
   - A teacher who solves a maths problem on the board while saying "and then we multiply by 3" is doing the task, not thinking aloud.
   - A teacher who says "Now I need to figure out what to do next. I have two options — I could multiply or I could factorise first. Let me think about which is better... Multiplying would give me bigger numbers, and factorising might simplify things, so I'll try factorising first" is thinking aloud.

5. **Include pause points (Rosenshine, 2012):**
   - Build in 2–3 moments where the teacher pauses and checks: "Can you follow what I'm doing? What did I just decide to do, and why?"
   - These pauses prevent the think-aloud from becoming a monologue.

6. **Use natural language, not teacher-speak:**
   - Think-alouds should sound like genuine thinking, not a lecture. Use "Hmm," "OK so," "Wait," "Let me think," "I'm not sure about this yet."
   - Avoid: "Students, notice how I am using the strategy of..."

Return your output in this exact format:

## Think-Aloud Script: [Task]

**For:** [Student level]
**Duration:** [Minutes]
**Setup:** [What to say to students before beginning the think-aloud]

### The Script

[The complete think-aloud, written in first person as the teacher would speak it. Include stage directions in square brackets. Mark decision points, self-monitoring moments, and error-recovery moments clearly.]

### Visible Strategies

[Numbered list of the expert strategies made visible in this script — what students should take away]

### Pause Points

[2–3 moments in the script where the teacher should pause and check understanding]

### Delivery Notes

[Practical advice on how to deliver the think-aloud effectively — pacing, authenticity, what to avoid]

**Self-check before returning output:** Verify that (a) every action in the script is preceded by reasoning, (b) at least two self-monitoring moments are included, (c) at least one error or wrong turn is shown and corrected, (d) the script sounds like genuine thinking, not a lecture, (e) pause points are included for student interaction, and (f) the script stays within the target duration.
```

## 示例输出

**场景：** *Task: "Reading and responding to an unseen poem for the first time — GCSE English Literature style" / Student level: "Year 10, can identify poetic techniques but don't know how to approach an unseen poem strategically — they tend to panic, read once, and start writing immediately" / Subject: "GCSE English Literature"*

---

## 出声思维脚本：首次阅读陌生诗歌

**适用对象：** 十年级 GCSE 英国文学
**时长：** 10 分钟
**导入语：** "I'm going to show you what happens inside my head when I read a poem I've never seen before. I'm NOT going to show you a perfect analysis. I'm going to show you my real thinking — the confusion, the wrong guesses, the re-reading. Watch and listen. I'll pause a couple of times to check you're following."

*［教师在黑板上展示 Percy Bysshe Shelley 的《Ozymandias》——或任何适合该班级的陌生诗歌。本例使用《Ozymandias》。］*

### 脚本正文

"OK. Here's a poem I've never analysed for you before. Let me read it through.

*［平稳地通读全诗，中途不停顿。］*

Right. First reaction — I have a rough sense of what this is about but I definitely don't understand all of it yet. That's normal. If you read a poem once and think you understand everything, you're probably missing something. So I'm going to read it again, but this time I'm going to slow down and think.

*［回到诗歌开头。］*

'I met a traveller from an antique land, Who said—'

OK so the poem is starting with someone ELSE telling a story. The poet isn't describing what he saw — he's reporting what a traveller told him. That's an interesting choice. Let me note that — *［在页边批注：'framed narrative — why?'］* — I don't know why yet, but a poet choosing to distance themselves from the description is usually deliberate. I'll come back to that.

'Two vast and trunkless legs of stone Stand in the desert...'

I'm picturing this — two huge legs, but no body. Just the legs. In a desert. So this is a ruined statue. Something that was once complete is now broken. *［批注：'decay — once complete, now ruined.'］*

'Near them, on the sand, Half sunk a shattered visage lies, whose frown, And wrinkled lip, and sneer of cold command—'

*［停顿。］* OK, 'visage' — that's a face. The face is half-buried in sand. And look at those words describing the face: 'frown,' 'wrinkled lip,' 'sneer of cold command.' These are all negative — this isn't a kind face. This is someone who looked powerful and cruel. Let me underline 'sneer of cold command' — that phrase is doing a lot of work. 'Sneer' is contempt. 'Cold' is absence of warmth or compassion. 'Command' is power. Three words, and I've got a picture of a tyrant.

Hmm, wait — I want to check something. Am I right that this is about power? Let me read ahead before I commit to that interpretation...

'Tell that its sculptor well those passions read Which yet survive, stamped on these lifeless things, The hand that mocked them, and the heart that fed;'

*［停顿。］* OK this is harder. Let me re-read it. 'Tell that its sculptor well those passions read' — the sculptor understood those expressions of power well. 'Which yet survive' — the expressions on the stone face survive, even though... 'stamped on these lifeless things' — they're just marks on dead stone. 'The hand that mocked them, and the heart that fed' — whose hand? Whose heart?

I'm confused. I'll be honest — this is the hardest part of the poem and I'm not sure I've got it. Let me try: I think 'the hand that mocked them' is the sculptor's hand — the sculptor copied ('mocked') those expressions. And 'the heart that fed' is the ruler's heart — the passions originally came from him. So the sculptor's skill preserved the ruler's cruelty in stone.

Actually, there might be a double meaning of 'mocked' — the sculptor both copied AND mocked the ruler. That's clever if it's intentional. *［在页边批注：'mocked = copied or ridiculed? Both?'］*

**[停顿点 1]** *［面向学生：］* "Stop me here. What have I done so far that's different from just reading the poem? Tell your partner one thing you noticed about my approach." *［随机点名一组。期待回答：重读、在页边批注、提问、承认困惑、画面化想象、关注用词选择。］*

OK, continuing. Here's where it gets really interesting:

'And on the pedestal, these words appear: My name is Ozymandias, King of Kings; Look on my Works, ye Mighty, and despair!'

NOW I understand the poem. Ozymandias is the ruler. He built this statue of himself and inscribed 'Look on my Works, ye Mighty, and despair' — he's saying: look at my empire, my power, and be terrified. He's boasting.

But — and this is the key — what's actually around the statue?

'Nothing beside remains. Round the decay Of that colossal Wreck, boundless and bare The lone and level sands stretch far away.'

Nothing. The desert. His 'Works' are gone. His empire is gone. Everything he built has been destroyed by time. All that's left is a broken statue in the sand and an inscription boasting about greatness that no longer exists.

*［批注：'IRONY — the boast is about power, but everything is destroyed. Time defeats all tyrants.'］*

THAT is the point of the poem. And now I understand why Shelley used the framed narrative at the beginning — 'I met a traveller who said.' Shelley is adding ANOTHER layer of distance. He didn't even see the statue himself. This is a story within a story — Ozymandias's power has faded so much that he's not even being described firsthand. He's become a rumour.

**[停顿点 2]** *［面向学生：］* "What was the moment when the poem 'clicked' for me? When did I go from confused to understanding the main idea? And what did I do when I was confused — did I panic or did I do something specific?" *［随机点名。期待回答：狂妄宣言与空旷沙漠之间的反差；感到困惑时，重读并尝试转述。］*

Now, if this were an exam, I'd go back and think about which techniques to write about. I'd choose 'sneer of cold command' because it concentrates so much character into three words. I'd write about the irony of the inscription versus the empty desert. And I'd write about the image of the broken statue as a symbol for the impermanence of human power.

But here's the thing — I got there by reading THREE times, writing in the margins, admitting when I was confused, and not panicking when I didn't understand a line. That's the process. If you read once and immediately start writing, you'll miss the irony, the structure, and the real meaning."

### 显性呈现的策略

1. **在分析前先通读一遍全诗以把握整体大意。** 第一遍阅读时不要停下来逐字剖析。
2. **拿着笔重读。** 第二遍阅读才是分析的开始——批注、提问、视觉化想象。
3. **聚焦单个用词选择。** "Sneer of cold command"——三个词就能浓缩完整的人物刻画。引用要短，分析要深。
4. **承认并攻克困惑。** 当某一行读不懂时，重读并尝试转述。困惑是信息，不是失败。
5. **寻找转折或对比。** 许多诗歌的核心在于某种转变——宣言与现实之间、预期与意外之间。找到转折，就找到了主旨。
6. **追问“诗人为什么做这个选择？”** 嵌套叙事、用词选择、结构安排——这些都是有意为之。问“为什么”，而不仅仅是“是什么”。

### 停顿点

1. **前 5 分钟后**（大约分析完前半部分时）：检查学生能否说出教师的做法与单纯阅读有何不同。这能将过程性策略浮出水面。
2. **在“豁然开朗”时刻之后**（当反讽变得清晰时）：检查学生能否识别理解是在何时、如何涌现的——以及教师在困惑时做了什么。这让建设性挣扎变得正常。

### 演示建议

- **听起来要像真正在思考，而不是在表演。** 使用自然的犹豫词："Hmm,"、"Wait,"、"OK so,"、"I'm not sure about this yet." 如果出声思维听起来像一篇打磨完美的讲座，学生就不会相信它代表真实的思考。
- **不要提前剧透你接下来要做什么。** 不要说 "Now I'm going to use the strategy of re-reading for clarification." 直接重读即可。学生应当看到策略在行动中发挥作用，并自己识别出来（或在停顿点讨论中识别）。
- **展现真实的不确定性。** 关于 "mocked"（模仿还是嘲弄？）的那一刻，应当给人一种真实未决的感觉。说出 "I think it might mean both — I'm not sure" 示范了熟练读者需要、而新手读者缺乏的对歧义的容忍度。
- **把控节奏。** 10 分钟很紧凑。提前演练一次以检查时间。把诗歌前半部分示范透彻，远胜于匆匆草率地讲完一整首诗。
- **出声思维结束后，明确点出这些策略。** 出声思维展示了行动中的策略；随后用 2 分钟简短复盘，明确命名这些策略，以便学生迁移到自己的阅读中。

---

## 已知局限性

1. **脚本是范本，不是提词器。** 教师必须用自己的声音演绎，并在停顿点根据学生的反应灵活调整。一字不差地照念脚本会显得生硬做作，适得其反。教师应当内化关键决策点和自我监控时刻，然后自然地说出来。

2. **出声思维只有在学生专注观察和倾听时才有效。** 如果学生走神，出声思维变成了背景噪音，就不会产生任何学习。保持出声思维简短（最多 8–12 分钟），加入互动停顿点，并紧接着开展由学生应用相同策略的引导练习。

3. **专家盲点是真实且反复出现的。** 即使有了这份脚本，教师仍可能无意识地跳过那些对自己显而易见、但对新手而言不可见的步骤。出声思维结束后，问学生："Was there any point where I jumped ahead and you lost me?" 学生的回答会揭示脚本遗漏的专家盲点。
