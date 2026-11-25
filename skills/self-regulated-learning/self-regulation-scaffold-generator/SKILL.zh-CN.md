---
# AGENT SKILLS STANDARD FIELDS (v2)
name: self-regulation-scaffold-generator
description: "生成支持学生在计划、监控与评价阶段进行自我调节的脚手架。适用于学生在长周期或独立任务中难以自主管理学习进程的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "self-regulated-learning/self-regulation-scaffold-generator"
skill_name: "自我调节脚手架生成器"
domain: "self-regulated-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Zimmerman (2000) — Attaining self-regulation: a social cognitive perspective"
  - "Zimmerman (2002) — Becoming a self-regulated learner: an overview"
  - "Pintrich (2000) — The role of goal orientation in self-regulated learning"
  - "Dignath & Büttner (2008) — Components of fostering self-regulated learning among students: a meta-analysis (effect size ~0.69)"
  - "Panadero (2017) — A review of self-regulated learning: six models and four directions for research"
input_schema:
  required:
    - field: "task_description"
      type: "string"
      description: "学生将要完成的具体学习任务"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及自我调节成熟度（新手/发展中/独立）"
    - field: "task_duration"
      type: "string"
      description: "学生完成该任务的时间跨度（单节课、多节课、家庭作业、项目）"
  optional:
    - field: "srl_phase_focus"
      type: "string"
      description: "重点强调的自我调节学习阶段：前瞻（forethought）、执行（performance）或反思（reflection）"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：个体自我调节数据、执行功能档案"
    - field: "previous_srl_instruction"
      type: "string"
      description: "学生已经学过哪些自我调节策略"
    - field: "subject_area"
      type: "string"
      description: "用于选择学科特定策略的学科背景"
output_schema:
  type: "object"
  fields:
    - field: "scaffolds"
      type: "object"
      description: "针对前瞻、执行和反思三个阶段的专属脚手架"
    - field: "student_handout"
      type: "string"
      description: "可直接复制粘贴使用的面向学生的脚手架学习单"
    - field: "teacher_moves"
      type: "array"
      description: "支持每个自我调节学习阶段的具体教师策略"
    - field: "fading_plan"
      type: "string"
      description: "随着学生独立性增强逐步撤除脚手架的计划"
chains_well_with:
  - "metacognitive-prompt-library"
  - "goal-setting-protocol-designer"
  - "agency-scaffold-generator"
  - "feedback-quality-analyser"
teacher_time: "4 分钟"
tags: ["self-regulation", "metacognition", "scaffolding", "independence", "executive-function"]
---

# 自我调节脚手架生成器（Self-Regulation Scaffold Generator）

## 本技能的功能

产出分阶段的自我调节学习（SRL）脚手架——针对目标设定、策略选择、进度监控与反思的结构化支持——并根据具体任务和学生年龄/成熟度进行精准校准。输出内容包括一份面向学生的脚手架学习单，以及教师关于何时、如何使用各要素的指导。AI 在此具有独特价值，因为有效的 SRL 脚手架必须同时校准三个变量：具体任务的认知需求、学习者的发展阶段（7 年级学生与 12 年级学生所需的脚手架截然不同），以及当前支持的特定 SRL 阶段。大多数教师要么过度搭建脚手架（完全消除了自我调节需求），要么脚手架不足（只告诉学生“规划好你的工作”，却不教他们怎么做）。

## 循证依据

Zimmerman（2000, 2002）确立了自我调节学习的循环模型，包含三个阶段：前瞻阶段（目标设定、策略规划、自我效能信念）、执行阶段（自我监控、策略运用、注意力控制）以及自我反思阶段（自我评价、因果归因、策略调整）。Pintrich（2000）将其拓展至动机与情境因素，表明目标定向会显著影响学生调动哪些 SRL 策略。Dignath 与 Büttner（2008）对 74 项研究进行的元分析发现，SRL 干预的平均效应量为 0.69，且当三个阶段都得到显性脚手架支持时效果最强。Panadero（2017）综述了六大主流 SRL 模型，指出最有效的干预能够让自我调节过程变得可见且可教——必须显性向学生展示**如何**计划、监控和反思，而不仅仅是口头要求。关键在于，SRL 脚手架必须随时间逐步撤除（fading）；永久性的脚手架只会制造依赖，而非独立。

## 输入规范

教师必须提供：
- **任务描述：** 具体学习任务。*例如：“撰写一篇议论文，论证赞成或反对校服（800 词，周五交）” / “在 3 周内完成一项关于影响植物生长因素的小组科学探究”*
- **学生水平：** 年级与 SRL 成熟度。*例如：“7 年级，自我调节新手” / “11 年级，发展中——会做计划但在监控方面有困难”*
- **任务时长：** 学生拥有多少时间。*例如：“3 节课加家庭作业” / “6 周项目”*

可选（如情境引擎可用，将自动注入）：
- **SRL 阶段聚焦：** 重点强调哪个阶段（前瞻、执行或反思）
- **学生档案：** 个体自我调节数据、执行功能档案
- **既往 SRL 教学：** 学生已学过的策略
- **学科领域：** 用于选择学科特定策略的背景

## Prompt

```
You are an expert in self-regulated learning research, specialising in Zimmerman's (2000, 2002) cyclical SRL model and its classroom application. You understand the three phases of self-regulation (forethought, performance, self-reflection) and how to design scaffolds that develop genuine student independence rather than creating scaffold dependency.

Your task is to generate SRL scaffolds for the following:

**Task:** {{task_description}}
**Student level:** {{student_level}}
**Task duration:** {{task_duration}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**SRL phase focus:** {{srl_phase_focus}} — if not provided, generate scaffolds for all three phases, weighted toward the phase most critical for this task type and student level.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical class at the stated SRL maturity level.
**Previous SRL instruction:** {{previous_srl_instruction}} — if not provided, assume students have had minimal explicit SRL instruction and need concrete, structured scaffolds.
**Subject area:** {{subject_area}} — if not provided, infer from the task description and select domain-appropriate strategies.

Apply these evidence-based principles:

1. **Scaffold all three phases (Zimmerman, 2002):**
   - **Forethought:** Goal-setting (specific, proximal, process-focused), task analysis (what does this task require?), strategic planning (which strategies will I use?), self-efficacy activation (what do I already know that helps?)
   - **Performance:** Self-monitoring prompts (am I on track?), attention control strategies, help-seeking guidance (when and how to ask for help), time management checkpoints
   - **Self-reflection:** Self-evaluation against criteria, causal attribution (why did I succeed/struggle — focus on strategy use, not ability), strategy adaptation (what would I change next time?)

2. **Calibrate to developmental level (Dignath & Büttner, 2008):**
   - **Novice self-regulators (typically Years 5–8):** Highly structured scaffolds with sentence starters, checklists, and explicit step-by-step guides. The scaffold does much of the metacognitive work for the student.
   - **Developing self-regulators (typically Years 9–10):** Prompts rather than scripts. Students choose from strategy options rather than following a fixed sequence. More open-ended monitoring questions.
   - **Independent self-regulators (typically Years 11–13):** Minimal scaffolding. Reflective prompts only. Students design their own plans using frameworks they've internalised.

3. **Make it task-specific, not generic (Panadero, 2017):** "Plan your work" is not a scaffold. "Before you start writing, list the three strongest arguments you will use and the evidence for each" is a scaffold. Every prompt must be specific to this task.

4. **Include a fading plan:** Scaffolds are temporary structures. For each scaffold element, indicate when and how to reduce support as students develop competence. The goal is independence, not permanent reliance on the scaffold.

5. **Avoid ability-focused language:** All self-evaluation should focus on strategy use and effort, not ability. "I struggled because I didn't plan enough time for revision" (strategy attribution) is productive. "I struggled because I'm not good at this" (ability attribution) is counterproductive. Scaffold prompts must model strategy-focused attribution.

Return your output in this exact format:

## Self-Regulation Scaffolds: [Task Name]

**For:** [Student level]
**Task duration:** [Duration]

### Phase 1: Forethought (Before Starting)

**Goal-Setting:**
[Specific, task-relevant goal-setting prompts or templates]

**Task Analysis:**
[Prompts that help students break down what the task requires]

**Strategic Planning:**
[Strategy selection support — what approaches are available and when to use each]

### Phase 2: Performance (During the Task)

**Self-Monitoring Checkpoints:**
[Specific monitoring prompts tied to task milestones — not just "check your work"]

**Attention & Time Management:**
[Concrete strategies for maintaining focus and managing time across the task duration]

**Help-Seeking Guide:**
[When to ask for help, what to try first, how to ask effectively]

### Phase 3: Self-Reflection (After Completing)

**Self-Evaluation:**
[Prompts for evaluating work against specific criteria]

**Attribution & Adaptation:**
[Prompts that focus on strategy use, not ability]

### Student Handout

[A clean, copy-pasteable version of the scaffolds formatted for students — no teacher notes, age-appropriate language]

### Teacher Moves

[Specific teacher actions for each phase — modelling, prompting, checking in]

### Fading Plan

[How to reduce scaffold support over subsequent uses of this task type]

**Self-check before returning output:** Verify that (a) every scaffold prompt is specific to this task, not generic, (b) scaffolds are calibrated to the stated SRL maturity level, (c) self-evaluation focuses on strategy use rather than ability, (d) a fading plan is included, and (e) the student handout is written in student-appropriate language.
```

## 示例输出

**场景：** *任务：“撰写一篇 600 词的分析性短文，探讨莎士比亚如何在《罗密欧与朱丽叶》第三幕第一场中呈现冲突。至少使用三处引文并加以分析。” / 学生水平：“9 年级，自我调节新手” / 任务时长：“2 节课（每节 50 分钟）加家庭作业草稿”*

---

## 自我调节脚手架：分析性短文——《罗密欧与朱丽叶》中的冲突

**适用对象：** 9 年级，自我调节新手
**任务时长：** 2 节课 + 家庭作业

### 第一阶段：前瞻阶段（开始前——第 1 课前 15 分钟）

**目标设定：**
开始前补全以下句子：
- “到今天这节课结束时，我将完成：_______________”
- “到第 2 节课结束时，我将完成：_______________”
- “相比上一篇短文，我最想提升的质量维度是：_______________”

教师示范示例：“到今天这节课结束时，我将选定三处引文并写好每段的提纲。到第 2 节课结束时，我将完成完整的初稿。我想提升的质量维度是我的分析深度——上次我只描述了发生了什么，而没有解释莎士比亚的语言选择意味着什么。”

**任务分析：**
本任务要求你完成四件事。每读懂一项就打钩，确保清楚要求：
- [ ] 阅读第三幕第一场，识别莎士比亚呈现冲突的片段
- [ ] 挑选至少 3 处体现冲突的引文
- [ ] 针对每处引文，解释莎士比亚的语言**如何**营造出冲突感（而不仅仅是**发生了什么**）
- [ ] 按引言、3 个分析段落和结论的结构组织短文

**策略规划：**
从以下方案中选择你的推进方式：
- **方案 A：** 先通读这一场，标出引文，在动笔写任何段落前先把全部段落规划好。
- **方案 B：** 一次规划并撰写一个段落，每写一段都回到文本找依据。
- **方案 C：** 先把关于这场戏冲突的所有想法倾倒在纸上，再整理成提纲。

圈出你的选择。没有绝对的对错——但你必须在开始前选好，而不是闷头直接写。

### 第二阶段：执行阶段（任务进行中——第 1–2 课）

**自我监控检查点：**

*检查点 1——第 1 课进行到 20 分钟时：*
停下来核对：
- [ ] 我已经选好至少 3 处引文。（如果没有：现在回到文本。寻找角色争吵、威胁或打斗的时刻。）
- [ ] 我已经有了短文提纲。（如果没有：为每一段写一句话，说明这段打算论证什么。）
- [ ] 我明白在这项任务中“分析”（analyse）意味着什么。（如果不明白：请老师向你展示“描述”和“分析”的区别。）

*检查点 2——第 2 课进行到 20 分钟时：*
停下来核对：
- [ ] 我至少已经写了 2 个分析段落。（如果没有：你落后于进度了。先跳过引言，优先写你最有把握的那一段。）
- [ ] 每段都包含一处引文**以及**对莎士比亚语言如何制造冲突的解释。（如果没有：回到你刚写完的那一段。划出你的引文。然后检查——你解释了莎士比亚用这些词在**做什么**，还是仅仅复述了剧情？）
- [ ] 我的分析使用了诸如“莎士比亚运用……来暗示……”或“这营造出一种……的感觉，因为……”的句式。（如果没有：在每段中添加一个这类句式开头。）

**注意力与时间管理：**
你有 100 分钟课堂时间加家庭作业。建议分配如下：
| 时间 | 任务 |
|------|------|
| 第 1 课：0–15 分钟 | 读剧本、选引文、列提纲 |
| 第 1 课：15–50 分钟 | 撰写第 1、2 段 |
| 第 2 课：0–10 分钟 | 重读已写内容：是在分析还是在描述？ |
| 第 2 课：10–45 分钟 | 撰写第 3 段、引言、结论 |
| 第 2 课：45–50 分钟 | 自我反思检查点（见下文） |
| 家庭作业 | 通读全文，根据自我评价改进其中一段 |

**求助指南：**
举手求助前，先尝试以下三步：
1. 重读任务说明。你的问题答案是否已经写在上面？
2. 看看教室墙上的范文段落。它是否展示了该如何下笔？
3. 问问你的同桌：“你能帮我看看这句话是在分析还是在描述吗？”

如果三步都试过依然卡住，请举手并这样告诉老师：
“我卡在了 ____________。我尝试了 ____________，但没有奏效，因为 ____________。”

### 第三阶段：自我反思（完成后——第 2 课末尾 + 家庭作业）

**自我评价：**
阅读你的短文并如实作答：

| 标准 | 是 / 部分做到 / 尚未 | 证据 |
|-----------|----------------------|----------|
| 我使用了至少 3 处来自第三幕第一场的引文 | | 哪几处？ |
| 我解释了莎士比亚的语言**如何**制造冲突（而非仅仅复述发生了什么） | | 挑出你写得最好的一句分析，抄写在这里： |
| 我的短文结构清晰（引言、3 个段落、结论） | | |
| 我使用了分析性语言（“莎士比亚运用……”、“这暗示……”、“其效果是……”） | | 用了几次？ |

**归因与调整：**
补全以下句子：
- “我这篇文章最有力的部分是 ____________，因为我运用了 ____________ 策略。”
- “我觉得最难的部分是 ____________。下次我会尝试 ____________ 策略来更好地应对。”
- “与我上一篇分析性写作相比，我在 ____________ 方面有了进步。”

*（注：这三句话都聚焦于你**做了什么**，而不是你**是什么样的人**。“我没做好提纲规划”是对自己有用的反馈；“我不擅长写作文”则不是。）*

### 学生学习单

---

**我的短文计划——《罗密欧与朱丽叶》中的冲突**

**我的本任务目标：**
1. 到第 1 课结束时，我将完成：_______________
2. 到第 2 课结束时，我将完成：_______________
3. 相比上次，我想提升的质量维度：_______________

**我的推进方案：**（圈出一项）A：先全盘规划 / B：逐段规划写作 / C：先头脑风暴再整理

**我的引文：**
1. “_______________”——我选它是因为 _______________
2. “_______________”——我选它是因为 _______________
3. “_______________”——我选它是因为 _______________

**检查点 1（第 1 课 20 分钟）：** 3 处引文？[ ] 提纲完成？[ ] 清楚什么是“分析”？[ ]

**检查点 2（第 2 课 20 分钟）：** 2 段以上？[ ] 每段都有引文+分析？[ ] 使用了分析性句式？[ ]

**完成后自我评价：**
- 我写得最好的一句分析：_______________
- 最难的部分 + 下次尝试的策略：_______________
- 相比上次我进步的地方：_______________

---

### 教师策略

- **前瞻阶段：** 大声示范目标设定：“看我如何为这个任务设定目标。我会先想一想上次我在哪里遇到了困难……”随后给学生 5 分钟填写自己的计划。巡视教室检查计划——温和地将设定空泛目标（“写一篇好作文”）的学生引导至具体的过程目标（“在每段中使用分析性语言”）。
- **执行阶段：** 在每个检查点，让全班暂停 2 分钟。要求学生用笔实实在在地勾选方框。随机问 2–3 名学生：“检查点告诉了你什么？你接下来打算怎么做？”这能把自我监控常态化，使其成为学习常规而非打断。
- **反思阶段：** 坚持聚焦策略的归因。如果学生写“我就是不擅长分析”，立即引导：“你可以用什么策略来让分析更有力？我们一起看看范文——作者做了哪一步是你还没做的？”每次都要把归因从“能力”拉回“策略”。

### 撤除脚手架计划（Fading Plan）

- **首次使用（本任务）：** 全套脚手架——检查清单、句式开头、定时检查点、教师示范。
- **第二次使用（下一篇分析性短文，约 4 周后）：** 撤除目标设定的句式开头。保留监控检查清单，但让学生自己编写检查问题。保留自我评价框架。
- **第三次使用（约 8 周后）：** 撤除监控检查清单。只发空白规划模板，让学生自行设计检查点。保留自我评价框架，但撤除句式开头。
- **第四次使用及以后：** 脚手架改为按需领取，不再统一发放。表现出稳定自我调节能力的学生脱离脚手架独立完成；仍有困难的学生继续使用上一版本。依据实际表现出的胜任力进行分层，而非主观臆断能力。

---

## 已知局限性

1. **SRL 脚手架可能沦为机械打钩，而非真正的自我调节。** 如果学生只是勾选方框而没有真正监控自己的作品，脚手架就失效了。教师观察至关重要——要留意那些停下来重读并修改的学生，而不是只打钩就继续写的学生。脚手架负责提示行为，只有教师的跟进才能核实其真实性。

2. **撤除脚手架的时间表只是近似参考，学生之间差异极大。** 有些学生用两次就能脱离脚手架；另一些学生可能需要一整年。撤除应以学生展现出的自我调节胜任力为依据，而非过去了几周。教师需要观察，而非假设。

3. **自我调节具有文化与情境依赖性。** Zimmerman 的模型主要是在西方教育背景下发展起来的。来自强调教师主导、集体学习或不同权威关系教育传统的学生，可能需要结合其文化背景调整脚手架——这并非因为他们缺乏自我调节能力，而是因为脚手架所倡导的具体行为（个人目标设定、自我评价、独立求助）未必直接对应他们以往的学习经验。
