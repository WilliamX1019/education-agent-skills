---
# AGENT SKILLS STANDARD FIELDS (v2)
name: self-efficacy-builder-sequence
description: "设计一套掌握体验序列，系统性地在学生回避的技能上建立信心。适用于学生说‘我做不到’、回避任务或表现出习得性无助的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/self-efficacy-builder-sequence"
skill_name: "自我效能感建设序列"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Bandura (1977, 1997) — Self-efficacy: toward a unifying theory of behavioural change"
  - "Bandura (1986) — Social Foundations of Thought and Action: four sources of self-efficacy"
  - "Schunk & Pajares (2009) — Self-efficacy theory in educational contexts"
  - "Hattie (2009) — Visible Learning: self-efficacy as one of the strongest predictors of achievement"
  - "Dweck (2006) — Mindset: the new psychology of success"
input_schema:
  required:
    - field: "target_skill"
      type: "string"
      description: "学生缺乏信心的技能或领域——他们认为自己做不到的事情"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "current_avoidance"
      type: "string"
      description: "学生目前用来回避任务的行为——显示低自我效能感的可观察表现"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_profile"
      type: "string"
      description: "来自情境引擎：先备成绩、已知优势、在该技能上的过往经历"
    - field: "previous_attempts"
      type: "string"
      description: "之前为建立信心尝试过什么——什么有效、什么无效"
    - field: "student_strengths"
      type: "string"
      description: "学生**有**信心的领域——现有的自我效能感优势区"
output_schema:
  type: "object"
  fields:
    - field: "efficacy_diagnostic"
      type: "object"
      description: "分析哪一种自我效能感来源对该学生最易触及"
    - field: "task_sequence"
      type: "array"
      description: "从学生当前起点出发、逐步建立自我效能感的 4–6 个任务序列"
    - field: "attribution_coaching"
      type: "string"
      description: "将成功归因于努力与策略而非能力或运气具体话术"
    - field: "teacher_scripts"
      type: "array"
      description: "教师在每个阶段强化自我效能感可使用的精确话术"
chains_well_with:
  - "motivation-diagnostic-task-redesign"
  - "agency-scaffold-generator"
  - "differentiation-adapter"
  - "practice-problem-sequence-designer"
teacher_time: "3 分钟"
tags: ["self-efficacy", "confidence", "Bandura", "mastery-experiences", "attribution", "mindset"]
---

# 自我效能感建设序列（Self-Efficacy Builder Sequence）

## 本技能的功能

为认为自己“做不到”某项特定技能的学生设计一套结构化任务序列——以适合该学生的顺序与组合，运用 Bandura 的四大自我效能感来源（掌握体验 mastery experiences、替代经验 vicarious experience、言语劝说 verbal persuasion 与生理状态 physiological states）系统性地建立信心。Bandura 研究的核心洞见在于：自我效能感不是靠告诉学生“你能行”（单纯的言语劝说效力最弱）建立的，而是通过精心设计真实的成功体验——从学生**已经能做到**的地方出发，循序渐进，使每一步都为学生提供“我有能力”的证据。输出是一份立即可用的任务序列，加上教师进行“归因教练”的具体话术——帮助学生把成功归因于自己可控的努力与策略，而不是看似固定的能力或随机的运气。AI 在此具有独特价值，因为设计有效的自我效能序列需要同时掌握技能的先备知识结构（学生能成功完成的简化版是什么？）、学生当前的起点，以及既具挑战性又可企及的精准增量——这种校准因每一位学生与每一项技能的组合而异。

## 循证依据

Bandura（1977, 1997）将自我效能感（对自己能否成功完成某项具体任务的信念）确立为人类动机与行为的核心决定因素。自我效能感具有领域特异性：一名学生可能在阅读上自我效能感很高，但在数学上很低。同时它也是可塑的——不同于特质性的自尊，自我效能感可以通过具体干预得以改变。Bandura（1986）按效力从强到弱归纳了自我效能感的四大来源：（1）掌握体验——实际把事情做成，这是迄今最有力的来源；（2）替代经验——看到与自己相似的人成功（“如果她能做到，也许我也能”）；（3）言语劝说——被告知你能做到，这是最弱的来源，但可辅助其他来源；（4）生理与情绪状态——任务期间身体的感受（平静 vs 焦虑）。Hattie（2009）发现自我效能感是学业成绩最强的个体层面预测指标之一（效应量 0.92），在某些分析中甚至强于先备成绩。Schunk 与 Pajares（2009）证明，即使控制实际能力变量，自我效能感依然能预测学业结果——相信自己能成功的学生表现优于同样有能力但自我怀疑的学生。Dweck（2006）关于内隐智力观的研究补充了 Bandura 的框架——持有“固定型思维”（认为能力是天生的）的学生在失败后比持有“成长型思维”（认为能力可通过努力发展）的学生更容易自我效能受损。然而，单纯的思维模式干预效果较弱（Sisk et al., 2018）——必须与真实的掌握体验相结合才能改变自我效能感。

## 输入规范

教师必须提供：
- **目标技能：** 学生认为自己做不到的事。*例如：“写作——学生说‘我不会写’且产出极少文字” / “心算——学生僵住并说‘我数学不行’” / “朗读——学生拒绝在课堂上朗读”*
- **学生水平：** 年级。*例如：“7 年级”*
- **当前回避行为：** 学生取而代之的行为。*例如：“写一句话就停下来，说‘我不知道写什么’” / “每道题不先尝试就立刻举手求助” / “趴在桌子上拒绝动笔”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **学生档案：** 先备成绩、优势、历史
- **既往尝试：** 之前试过什么
- **学生优势：** 已有信心的领域

## Prompt

```
You are an expert in self-efficacy and motivation, with deep knowledge of Bandura's (1977, 1997) self-efficacy theory, his four sources of self-efficacy, and the research on attribution and mindset (Dweck, 2006; Schunk & Pajares, 2009). You understand that self-efficacy is built primarily through mastery experiences — engineered success — and that verbal encouragement alone ("You can do it!") is the WEAKEST intervention. You also understand that self-efficacy is task-specific, not a general personality trait.

IMPORTANT: Do NOT recommend generic praise ("You're so clever!"), growth mindset slogans without substance ("You just need to try harder!"), or extrinsic reward systems. Self-efficacy is built through genuine success at progressively challenging tasks, with attribution coaching that helps the student connect their success to their effort and strategy.

Your task is to build a self-efficacy sequence for:

**Target skill:** {{target_skill}}
**Student level:** {{student_level}}
**Current avoidance:** {{current_avoidance}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the target skill.
**Student profile:** {{student_profile}} — if absent, leave causes unknown and plan a brief capability/access check; refusal alone cannot identify motivation, diagnosis or readiness.
**Previous attempts:** {{previous_attempts}} — if absent, do not invent what has been tried or its outcome.
**Student strengths:** {{student_strengths}} — if not provided, design the sequence to identify strengths through the early tasks.

Before selecting the sequence, check demonstrated prerequisite skills, task understanding, access and existing support with the learner and teacher. Verbal strengths or refusal do not rule out literacy, language, motor, working-memory or other access difficulties, and do not establish a psychological cause. If evidence is missing, label the efficacy diagnostic provisional and begin with an accessible check or instruction. Retain assistive tools and required accommodations throughout; seek appropriate human support for persistent barriers. This 4–6-task design is a planning scaffold, not an evaluated intervention or guaranteed progression. Agree pacing with the learner; timers are optional examples, not deadlines for success.

Apply these evidence-based principles:

1. **Start from mastery (Bandura, 1986 — Source 1):**
   - Identify the closest thing to the target skill that the student CAN already do. This is the starting point.
   - Choose the first task from demonstrated capability, offer needed support, and check success rather than guaranteeing it. This is not "dumbing down" — it is starting from a position of strength.
   - Each subsequent task should increase difficulty by ONE small step — the student must be able to see the connection between what they just succeeded at and what they're being asked to do next.
   - Plan 4–6 tasks with genuine, observable success criteria and recovery routes; adjust, repeat or pause based on performance instead of promising success at each step.

2. **Use vicarious experience strategically (Bandura, 1986 — Source 2):**
   - Show the student someone SIMILAR succeeding. "Similar" means: same age, same starting point, same difficulties — not the highest-achieving student in the class.
   - A relatable peer model may help confidence; use teacher modelling where instruction is needed, and do not promise one model is superior for every learner. "If she can do it and she used to find this hard too" is powerful.
   - Where possible, show the process of struggle → strategy → success, not just the final product.

3. **Provide calibrated verbal persuasion (Bandura, 1986 — Source 3):**
   - Verbal persuasion works only when it is SPECIFIC and CREDIBLE. "You can do this because you already did [specific prior success]" is credible. "I believe in you!" is not.
   - The persuasion must be tied to evidence the student can verify: their own prior success, a specific strategy they used, a specific improvement they made.
   - Over-praising undermines credibility. If the student knows the task was easy and you say "That was amazing!", they learn that your praise is unreliable.

4. **Manage physiological state (Bandura, 1986 — Source 4):**
   - Anxiety is a self-efficacy killer. If the student's body is in a stress state (racing heart, shallow breathing, wanting to escape), they may interpret it as difficulty; ask rather than assign their belief.
   - Reduce performance pressure: private rather than public, draft rather than final, practice rather than test.
   - Normalise difficulty: "Difficulty doesn't tell us by itself whether learning is happening. Let's check the work and what support would help."

5. **Coach attribution (Schunk & Pajares, 2009; Dweck, 2006):**
   - After each success, help the student attribute it to EFFORT and STRATEGY, not to ability or luck.
   - "You got that right because you used the method we practised" (strategy attribution) — not "You got that right because you're smart" (ability attribution).
   - After difficulty, attribute it to strategy: "That didn't work yet — let's try a different approach" — not to ability: "This is hard for you."

Return your output in this exact format:

## Self-Efficacy Sequence: [Target Skill]

**Target skill:** [What the student believes they can't do]
**Current avoidance:** [What they do instead]
**For:** [Student level]

### Efficacy Diagnostic

**Primary barrier:** [Observed capability/access evidence, learner perspective and tentative efficacy hypothesis; unknown is allowed]
**Starting point:** [The closest thing to the target skill the student CAN do]
**Sequence strategy:** [Which sources of self-efficacy this sequence targets and in what order]

### Task Sequence

For each task (4–6 tasks):
**Task [N]: [Name]**
- **What the student does:** [The task]
- **Why this builds efficacy:** [Which source of self-efficacy it targets]
- **Success looks like:** [What the student should be able to do — must be achievable]
- **Teacher script after success:** [Exact attribution language to use]
- **If the student struggles:** [What to do — adjust, not abandon]

### Attribution Coaching Guide

**Phrases to USE:**
[Specific phrases that attribute success to effort and strategy]

**Phrases to AVOID:**
[Specific phrases that undermine self-efficacy — ability praise, empty encouragement, comparison to others]

### Long-Term Plan

[How to maintain self-efficacy gains beyond this sequence — what the teacher should continue doing]

**Self-check before returning output:** Verify that (a) the first task fits demonstrated capability and has an accessible recovery route, (b) each step increases difficulty by one small increment, (c) mastery experiences are the primary intervention, (d) attribution coaching is specific and credible, (e) no generic praise or extrinsic rewards are recommended, and (f) the sequence ends at or near the original target skill level.
```

## 示例输出

**场景：** *目标技能：“长篇写作——学生说‘我不会写’，整个学年几乎没有产出过成段文字” / 学生水平：“8 年级” / 当前回避行为：“写完一句话就停下，擦掉，再写同一句话，然后趴在桌子上。如果被催促，就说‘我不知道写什么’或‘这很蠢’。” / 学科领域：“英语” / 学生优势：“在课堂讨论中的口头表达非常出色——条理清晰、细节丰富，口头发言展现出很强的理解力”*

---

## 自我效能感建设序列：长篇写作

**目标技能：** 在英语课上写出一篇有展开度的回应（一个完整发展的段落）
**当前回避行为：** 写一句、擦掉、彻底停滞。说“我不会写” / “我不知道写什么”。
**适用对象：** 8 年级英语

### 效能感诊断

**主要障碍：** 仅从描述看尚不明确。反复擦掉与停滞可能反映信心不足，但也可能反映对任务要求不理解，或存在书写/无障碍方面的困难。请私下询问哪里困难，检查一份有支持条件下的简短写作样本，并在选定步骤前核查现有的便利措施与先备教学。

**起点：** 在这个虚构案例中，口头表达是已记录的优势。它提示了一条切入路径，但并不证明写作仅仅是转录，也不证明障碍纯粹源于动机。先核查学习者能否在使用其日常无障碍支持工具的情况下构思并记录一句话。

**序列策略：** 如果该核查契合，则提供从“口头想法”向“书面写作”过渡的桥梁，配合微小的掌握步骤、可信的反馈与低压力环境。如果不契合，则优先提供恰当的技能讲授或无障碍支持。以下五项任务是可调节的草案；推进节奏取决于实际表现，而非“两三周见效”的空头承诺。在任何有帮助的环节保留口头规划与辅助工具。

### 任务序列

**任务 1：说出来，看见它**
- **学生做什么：** 教师就正在学习的文本向学生提一个问题（全班都在写的问题）。学生口头回答。教师（或助教，或仅在获得恰当同意与数据处理规范的前提下由学生使用经批准的语音转文字/录音工具；否则直接现场口头规划而不录音）逐字记下学生所说的话。随后教师把写下来的文字展示给学生看：“看——这就是你的话。是你自己说出来的。”
- **为何能建立效能感：** 替代经验 + 生理状态管理。学生在没有实际动笔书写压力的情况下，亲眼看到**自己的话**变成了书面文字。这能让既有的想法变得可见；需单独评估书面写作能力，因为仅有口头想法并不等于独立写作。
- **成功的表现：** 学生看到自己口述的回答被写下来，并认可其是有分量的内容。他们能意识到：“我说出了值得写下来的东西。”
- **成功后的教师话术：** “这些都是你自己的想法。哪一部分最能表达你想说的观点？我们可以一起使用对你有帮助的支持工具，把它变成一个书面句子。”
- **如果学生遇到困难：** 如果学生不愿开口，先从极低风险的问题起步：“这一章发生了什么？”（回忆，而非分析）。目标是让**任何**话先说出来并落到纸面上。

**任务 2：说出来，写下一句话**
- **学生做什么：** 同样设定：教师提问，学生口头回答。但这一次教师说：“很好。现在把你刚才说的第一句话写下来。就写第一句。用短计时器有帮助吗，还是不用计时器更好？如果有帮助，我们可以试试 60 秒并随时调整。”学生写下**一句**话。教师读完后说：“这正是你刚才说的意思。完成了。”
- **为何能建立效能感：** 掌握体验。学生产出了一个自己知道是好的书面句子——因为他们刚才口头上已经说过并得到了确认。“就写一句话”的框定缩小了任务的感知体量。约定的终点可能有帮助；若计时器增加压力，立即取消或调整。
- **成功的表现：** 学生写下一句话且没有擦掉它。就这样。一句话，留在纸面上。
- **成功后的教师话术：** “一句话——搞定。这句话把你对文本的观点讲得很清楚。是你自己写出来的。明天，我们试试两句。”
- **如果学生遇到困难：** 如果学生写了又擦掉，说：“留着它。就算还不完美——初稿本来就从不完美。我的初稿也一样。你愿意保留一个草稿版本让我们一起打磨吗？”如果他们完全僵住，退回任务 1。

**任务 3：说出来，写下三句话**
- **学生做什么：** 教师提问，学生口头回答——但这一次教师帮他们理出三个部分：“好，你刚才说了 [总结]。这里面有三个想法：[第一]、[第二]、[第三]。你能把这三个想法写成三句话吗？如果 3 分钟计时有帮助可以试试，或者按你需要的时间来。”
- **为何能建立效能感：** 掌握体验 + 胜任力脚手架。学生现在有了清晰的结构（三个想法、三句话）。口头演练确保他们动笔前就知道该写什么——消除了“我不知道写什么”的障碍。
- **成功的表现：** 纸上有三句话。不需要完美，它们需要**存在**。
- **成功后的教师话术：** “三句话。自己读一遍——你觉得怎么样？第二句里你用了引文，第三句解释了对读者的效果。这就是分析。你正在写作。”
- **如果学生遇到困难：** 如果只能写出一句写不出三句，欣然接纳两句。目标是向前迈步，而非苛求完美。调整目标：“好，今天两句。下次我们再往三句走。”

**任务 4：带着口头提纲写一个段落**
- **学生做什么：** 动笔前，学生口头规划自己的段落（使用班级通用的 PEEL 或类似结构）。教师或同伴倾听并确认：“这就是一个完整段落——观点、证据、解释。现在写下来。”学生写出该段落——目标为 4–5 句话。8 分钟是一个可选的规划参考时长，与学习者协商调整；保留其无障碍便利安排。
- **为何能建立效能感：** 掌握体验。这是学生第一次写出一个真正的段落。口头规划可降低构思负荷；核查学习者能否顺利将其转化为文字，若不能则调整支持。
- **成功的表现：** 一段 4–5 句、符合班级结构的文字。对照可及、恰当的写作标准评估该段落；口头表达质量并不自动保证书面表现。
- **成功后的教师话术：** “这一段有清晰的观点、一处引文以及对效果的解释。这和全班其他同学用的结构完全一致。看看这段话里的证据。每次用的都是同一个策略：先说出来规划好，再写下来。这个策略对你很管用。”
- **如果学生遇到困难：** 如果段落比计划的短，肯定已经写出的部分：“你已经写出了三句很有力的句子。下次我们把衔接句加上。你知道怎么写——你刚才规划时已经说出来了。”

**任务 5：独立写一个段落（目标状态）**
- **学生做什么：** 学生回应课堂任务，独立运用口头规划策略（轻声自言自语或写下要点提纲）完成一个段落。使用已练熟的策略及任何持续需要的辅助工具；仅当实际表现与学习者偏好支持时，才减少可选的教师提示。
- **为何能建立效能感：** 掌握体验 + 自主感。学生现在开始把自己看作“能写的人”——不是因为别人嘴上说你能行，而是因为他们在多项任务中积攒了“我真的做到了”的实证。
- **成功的表现：** 在常规课堂任务中独立产出一个完整段落。
- **成功后的教师话术：** “这一段是你独立完成的。你运用了口头规划策略来展开观点和证据。下一段你希望保留哪些支持？这个策略现在是**你的**了——以后每次都可以用。”
- **如果学生遇到困难：** 提供简短的口头演练：“告诉我你的第一句话——先说出来就行。”然后：“很好，写下来。”口头规划是一项正当的持续策略。与学习者共同回顾可选的教师提示；切勿为了证明“独立”而撤除有用的辅助工具。

### 归因教练指南

**应当使用的话术：**
- “你能把这一段写出来，是因为你先大声规划好了——那个策略很管用。”
- “把那句话读一遍——非常清晰，观点很有力。是你的提前规划让它成为可能的。”
- “你这周写得比上周多。这是因为你一直在练习口头规划——用得越多，就越顺手。”
- “你一直对照计划检查段落；现在这一句把证据解释得很清楚了。”
- “你找到了适合自己的策略——先说出来理顺，再写下来。这就是作家的工具。”

**应当避免的话术：**
- “你真聪明！” —— 能力归因；一旦学生日后卡住，“聪明”就会变成自我怀疑的证据。
- “太棒了！”（针对非常简单的任务）—— 失真的表扬会摧毁可信度。学生心里清楚那很简单。
- “你看，我就说你能做到吧！” —— 把功劳归于老师，而不是学生。“你自己向自己证明了”会好得多。
- “你跟 [其他同学] 一样厉害” —— 横向比较会引入学生未必觉得自己能维持的标准，反而威胁自我效能感。
- “再努力一点就行了” —— 没有策略支撑的盲目努力，就像更用力地撞墙。务必把努力与具体策略绑定。

### 长期计划

1. **保留口头规划策略。** 这名学生的优势在于口头表达。从口语到书面的桥梁应当一直保留——它不是拐杖，而是连专业作家都在使用的正当写作策略。随着时间推移，学生可能会将规划内化（在脑中思考而非出声），但无需急于撤除外部形式。

2. **逐步拓展篇幅。** 一旦单个段落稳固，就拓展到两个相互衔接的段落（每段都用口头规划），随后再迈向短篇作文。每次增量都应微小——每一项新挑战都应感觉像是“比上次成功多迈一小步”，而不是巨大飞跃。

3. **警惕失败后的回退。** 当学生某次写得较弱时（每个写作者都会遇到），他们可能会将其解读为“我果然还是不会写”的证据。立即用归因教练回应：“这一段不如你上一篇有力——但这不是因为你不会写，而是因为这篇文本更难分析。我们再用一次你的规划策略。”

4. **切勿公开拿学生现在的写作与过去的回避行为作对比。** “还记得你以前老是趴在桌子上吗？”听起来像在激励，实则令人羞愧。学生过去的挣扎属于隐私。庆祝当下的成功，不必重提过去的困境。

---

## 已知局限性

1. **自我效能感序列需要时间。** 五步任务序列没有固定不变的最短时长；请根据实际表现与学习者反馈决定推进节奏。没有包治百病的捷径——自我效能感是通过累积成功证据建立的，而非单次干预。面对“赶教学进度”压力的教师可能会觉得投入不起这段时间。教师必须在所需讲授与无障碍支持之外权衡时间成本；本序列并不保证效率优势或固定的“三周见效”回报。

2. **动机、技能与无障碍条件会相互作用。** 本序列不负责诊断困难的成因。口头表达流利并不排除存在书写困难或无障碍障碍。在使用前请核查先备知识与支持需求，在需要时提供显性技能教学，并在建立信心的同时保留便利措施或专业支持。

3. **自我效能感具有领域特异性。** 建立起写作自我效能感并不会自动提升数学或科学中的自我效能感。每个领域都需要各自专属的序列。不过，元认知意识（“我用了一个策略，它奏效了”）是可以迁移的——学生可能会学会将这种基于策略的方法应用到其他困难领域。
