---
# AGENT SKILLS STANDARD FIELDS (v2)
name: sheltered-instruction-lesson-modifier
description: "运用 SIOP 遮蔽式教学法（sheltered instruction）原则修改教案，在听说读写四项技能上全面支持语言学习者。适用于为包含 EAL 学生的班级备课时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "eal-language-development/sheltered-instruction-lesson-modifier"
skill_name: "遮蔽式教学教案修改器"
domain: "eal-language-development"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Echevarría, Vogt & Short (2008, 2017) — Making Content Comprehensible for English Learners: the SIOP Model"
  - "Short, Fidelman & Louguit (2012) — Developing academic language in English language learners through sheltered instruction"
  - "Cummins (2000) — Language, Power and Pedagogy"
  - "Gibbons (2015) — Scaffolding Language, Scaffolding Learning"
  - "Lyster (2007) — Learning and Teaching Languages Through Content: a counterbalanced approach"
input_schema:
  required:
    - field: "lesson_plan"
      type: "string"
      description: "原定教案的描述——主题、活动、资源和学习目标"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "eal_students"
      type: "string"
      description: "EAL 学生人数及其大致语言水平"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：第一语言、接受英语授课学校教育的时间、具体需求"
    - field: "lesson_duration"
      type: "string"
      description: "课时长度"
    - field: "resources_available"
      type: "string"
      description: "可用的技术工具、双语资源、助教或其他支持"
output_schema:
  type: "object"
  fields:
    - field: "modified_lesson"
      type: "object"
      description: "融入 SIOP 要素修改后的教案——包含内容目标、语言目标及各阶段支架"
    - field: "language_objectives"
      type: "array"
      description: "与所教内容对齐的明确语言目标"
    - field: "siop_component_checklist"
      type: "object"
      description: "修改后的教案如何落实 SIOP 的每一项要素"
    - field: "teacher_adaptations"
      type: "array"
      description: "对教师话语、节奏和互动模式的具体调整"
chains_well_with:
  - "language-demand-analyser"
  - "vocabulary-tiering-tool"
  - "scaffolded-task-modifier"
  - "academic-language-sentence-frame-generator"
teacher_time: "5 分钟"
tags: ["SIOP", "sheltered-instruction", "EAL", "lesson-planning", "content-language-integration"]
---

# 遮蔽式教学教案修改器

## 本技能的作用

接收一份学科内容教案，并运用 SIOP（Sheltered Instruction Observation Protocol，遮蔽式教学观察规程）模型原则进行修改：添加明确的语言目标、激活并构建背景知识、使输入可理解、设计结构化互动，并提供练习与运用机会——同时保持内容学习目标不变。输出是一份惠及所有学生（而不仅仅是 EAL 学生）的修改后教案，因为 SIOP 原则——清晰的目标、可理解的输入、结构化的互动、有意义的练习——本身就是面向所有人的优质教学。AI 在此尤为有价值，因为有效的遮蔽式教学需要同时透过双重视角（内容与语言）分析一节课，并在多个 SIOP 要素中作出连贯且实用的调整——这不是零散补充的清单，而是一次整体性的再设计。

## 循证基础

Echevarría, Vogt & Short (2008, 2017) 开发了 SIOP 模型——这是针对向英语学习者教授学科内容研究最充分的教学方法。该模型包含跨越 8 个要素的 30 项特征：教学准备（Lesson Preparation，内容目标与语言目标）、构建背景（Building Background，联系已有知识）、可理解输入（Comprehensible Input，清晰且经调整的教师话语）、策略（Strategies，支架与元认知提示）、互动（Interaction，结构化口语交流机会）、练习/应用（Practice/Application，有意义的任务）、课堂实施（Lesson Delivery，节奏与参与度）以及复习/评估（Review/Assessment，检查理解）。Short, Fidelman & Louguit (2012) 证明，系统实施 SIOP 能在内容学习和学术语言发展两方面都带来显著提升，各学科的效应量达到 0.40–0.60。关键在于，采用 SIOP 教学的班级对“所有”学生都带来了提升，而不仅仅是 EAL 学生——这些原则具有普遍有效性。Cummins (2000) 确立了学术语言是通过有意义地参与富有挑战性的内容而发展的，而不是通过简化的内容或孤立的语言练习。Gibbons (2015) 强调，最有力的语言学习发生在学生获得适当支持并投入高认知要求的内容任务之时。Lyster (2007) 证明，基于内容的语言教学比孤立的语言教学更有效，但前提是语言必须与内容一起被明确注意和练习——隐性的“沉浸”是不够的。

## 输入模式

教师必须提供：
- **Lesson plan（教案）：** 原定教案的描述。*例如："Year 8 Geography: Introduction to tectonic plates. Activities: teacher explanation with diagrams (15 min), students label a cross-section diagram (10 min), students answer textbook questions about plate boundaries (20 min). Objective: understand the three types of plate boundary and their effects."*
- **Subject area（学科领域）：** 学科。*例如："Geography"*
- **Student level（学生水平）：** 年级。*例如："Year 8"*

可选（如上下文引擎可用则自动注入）：
- **EAL students（EAL 学生）：** 人数与语言水平
- **Student profiles（学生档案）：** 第一语言、接受英语授课学校教育的时间、具体需求
- **Lesson duration（课时长度）：** 课堂时长
- **Resources available（可用资源）：** 技术、双语资源、助教支持

## Prompt

```
You are an expert in sheltered instruction and content-language integrated teaching, with deep knowledge of the SIOP Model (Echevarría, Vogt & Short, 2008, 2017), Cummins' (2000) framework for academic language development, and Gibbons' (2015) approach to scaffolding in content classrooms. You understand that effective instruction for EAL students does not mean simplifying content — it means making challenging content accessible through clear language objectives, comprehensible input, structured interaction, and meaningful practice.

Your task is to modify this lesson plan using SIOP principles:

**Lesson plan:** {{lesson_plan}}
**Subject area:** {{subject_area}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**EAL students:** {{eal_students}} — if not provided, assume 4–6 EAL students at mixed proficiency levels (Early Acquisition to Consolidating) in a class of 25–30.
**Student profiles:** {{student_profiles}} — if not provided, assume mixed first languages with conversational fluency but varying academic language proficiency.
**Lesson duration:** {{lesson_duration}} — if not provided, assume a 60-minute lesson.
**Resources available:** {{resources_available}} — if not provided, assume standard classroom resources (whiteboard, projector, textbooks) but no bilingual TA or specialist technology.

Apply the SIOP Model's eight components:

1. **Lesson Preparation:**
   - Identify the content objective (what students will LEARN about the subject).
   - Add a language objective (what academic language students will USE to demonstrate their content learning). Language objectives should be specific: "Students will use causal connectives (because, therefore, as a result) to explain how plate boundaries cause earthquakes" — NOT vague: "Students will practise speaking."
   - Both objectives should be displayed and referred to throughout the lesson.

2. **Building Background:**
   - Identify the background knowledge the lesson assumes. What must students already know?
   - Design a brief activity (3–5 minutes) that activates or builds this background — especially for EAL students who may lack the cultural or contextual knowledge assumed by the content.
   - Explicitly link new content to what students already know.

3. **Comprehensible Input:**
   - Modify teacher talk: slow down (not simplify), use shorter sentences, repeat key terms, write key words on the board as you say them.
   - Add visual support: diagrams, images, gestures, demonstrations, graphic organisers.
   - Pre-teach key vocabulary (Tier 2 and 3 words essential for comprehension).

4. **Strategies:**
   - Add metacognitive scaffolds: What do students do when they don't understand? Teach them to ask: "What word don't I understand?" "Can I work out the meaning from context?" "Should I ask?"
   - Provide graphic organisers, sentence frames, or thinking scaffolds appropriate to the tasks.

5. **Interaction:**
   - Build in structured talk opportunities. EAL students need to USE language, not just hear it.
   - Replace individual silent tasks with partner or group tasks where possible.
   - Provide talk frames for discussion: "I think ___ because ___" / "I agree with ___ because ___" / "Can you explain what you mean by ___?"
   - Ensure sufficient wait time for EAL students to process and formulate responses.

6. **Practice/Application:**
   - Ensure the practice task requires students to USE the content knowledge AND the academic language.
   - Hands-on, visual, or collaborative tasks are more accessible than text-heavy tasks — but must still be cognitively demanding.
   - Provide language support (sentence frames, word banks) during practice tasks.

7. **Lesson Delivery:**
   - Check pacing: are transitions clear? Are instructions given step-by-step rather than all at once?
   - Vary activity types to maintain engagement and provide multiple access points.
   - Monitor comprehension continuously, not just at the end.

8. **Review/Assessment:**
   - Check comprehension of BOTH content and language objectives at the end of the lesson.
   - Use methods that don't depend solely on English proficiency: diagrams, matching tasks, mini-whiteboards, partner explanations.
   - Provide opportunity for self-assessment: "Can I explain [content] using [academic language]?"

Return your output in this exact format:

## Modified Lesson: [Topic]

**For:** [Student level] [Subject area]
**Duration:** [Minutes]

### Objectives (displayed on board)

**Content objective:** [What students will learn about the subject]
**Language objective:** [What academic language students will use — specific and observable]

### Modified Lesson Plan

[Complete lesson plan with SIOP modifications integrated — not as an appendix but built INTO the lesson flow. Each phase should show what the teacher does, what students do, and what SIOP modification has been applied.]

### SIOP Component Checklist

[How each of the 8 SIOP components is addressed in the modified lesson]

### Teacher Adaptations

[Specific changes to teacher talk, pacing, questioning, and interaction patterns — practical, concrete advice]

### What Changed and Why

[Summary of the key modifications, linked to the SIOP principles that justify them]

**Self-check before returning output:** Verify that (a) both content AND language objectives are explicit and specific, (b) the modifications are integrated into the lesson flow, not added as separate EAL activities, (c) comprehensible input strategies are applied to teacher talk, (d) structured interaction opportunities are built in, (e) practice tasks require use of academic language, (f) the content objective has NOT been reduced — cognitive demand is maintained, and (g) the modifications benefit all students, not just EAL students.
```

## 示例输出

**场景：** *Lesson plan: "Year 8 Science: Introduction to the digestive system. Activities: (1) Teacher explanation with PowerPoint slides showing the organs of the digestive system (15 min), (2) Students label a diagram of the digestive system from memory (10 min), (3) Students read a textbook page about the function of each organ and answer questions (20 min), (4) Plenary quiz — teacher asks questions, students raise hands to answer (5 min). Objective: Students should be able to name the organs of the digestive system and describe their functions." / Subject area: "Science (Biology)" / Student level: "Year 8" / EAL students: "5 EAL students — 1 New to English (Somali), 2 Early Acquisition (Polish, Arabic), 2 Developing (Spanish, Mandarin)" / Lesson duration: "50 minutes"*

---

## 修改后的教案：消化系统

**适用对象：** 八年级科学（生物）
**时长：** 50 分钟

### 目标（展示在黑板上）

**内容目标：** 说出消化系统主要器官的名称，并描述每个器官的功能。

**语言目标：** 使用句式结构 "The [organ] [verb]s the food by [process]" 来描述每个器官的作用。（示例："The stomach digests the food by mixing it with acid and enzymes."）

*开课时将两个目标都展示在黑板上。课末再次回到目标："Can you do this now?"*

### 修改后的教案

**第一阶段：构建背景 + 可理解输入（12 分钟）**

*SIOP 修改：将 15 分钟的教师讲授替换为更短、更具互动性的输入阶段，以构建背景并使输入可理解。*

**0:00–3:00 — 构建背景（SIOP 要素 2）**
"Before we start — everyone knows what happens when you eat food. Think about the last thing you ate. What happened to it? Where did it go? Talk to your partner for 30 seconds."

收集 2–3 个回答。在学生说出关键词时将其写在黑板上：*mouth, chew, swallow, stomach, toilet.*

"So you already know that food goes on a journey through your body. Today we're going to learn the scientific names for each stop on that journey, and — more importantly — what happens at each stop."

*有效原因：* 联系普遍生活经验（每个人都吃东西）。用易于理解的语言激活已有知识。“旅程（journey）”这一隐喻提供了一个支架，使顺序过程变得直观。

**3:00–12:00 — 可理解输入：教师讲解（SIOP 要素 3）**

展示 PowerPoint 幻灯片，但作出如下修改：
- 每张幻灯片只展示“一个”器官，而不是完整图谱。逐一引入器官。
- 对每个器官：展示图片、说出名称、写在黑板上、让学生齐声跟读名称（全班齐读——让所有人都自然练习发音）。
- 对每个器官：用“一个”简单句子描述其功能，然后使用语言目标中的句式框架把句子写在黑板上。

**黑板板书逐步构建：**

| 器官 | 作用 | 核心句 |
|-------|-------------|--------------|
| Mouth | 把食物分解成更小块 | The mouth breaks down the food by chewing and mixing with saliva. |
| Oesophagus | 把食物推向胃 | The oesophagus moves the food by squeezing it downwards (peristalsis). |
| Stomach | 化学消化食物 | The stomach digests the food by mixing it with acid and enzymes. |
| Small intestine | 将营养吸收进入血液 | The small intestine absorbs the nutrients by passing them through its walls into the blood. |
| Large intestine | 吸收水分 | The large intestine absorbs water from the remaining food. |

*有效原因：* 视觉 + 听觉 + 书面。学生同时看到、听到并读到每个术语。逐步构建的表格在整个课堂期间保持可见。句式框架得到持续示范，将语言目标融入内容讲解中。

**针对 New to English 学生（索马里语）的调整：** 提供一份双语词汇表（英语–索马里语），包含关键器官名称和简明定义。如果有双语同伴或助教可用，允许先用第一语言简要解释概念。该学生仍应尝试使用英语句式框架。

**第二阶段：结构化互动 + 练习（15 分钟）**

*SIOP 修改：将安静的个人标注任务替换为需要学生“使用”学术语言的合作互动任务。*

**12:00–17:00 — 同伴协作标注（SIOP 要素 5 与 6）**
给每对学生发一张空白人体轮廓图和剪好的器官名称标签。
"With your partner, place the organ labels in the correct position. As you place each one, say the key sentence: 'The [organ] [verb]s the food by [process].' You must say it out loud — not just place the label silently."

*有效原因：* 合作学习（学生互相帮助）。动觉参与（物理摆放标签）。口语练习（句式框架不仅用于写，更用于说）。黑板上的表格保持可见作为参考——这是有支持的回忆，而非无支持的死记硬背。

**17:00–27:00 — 描述旅程（SIOP 要素 4、5、6）**

*将阅读课本并回答理解题替换为更具互动性且语言支持更充分的任务。*

发给每位学生一张“食物的旅程（Food's Journey）”练习纸，上面按顺序列出器官并为每个器官配有句式框架：

"Imagine you are a piece of food. Describe your journey through the digestive system. For each organ, complete the sentence:"

1. First, I enter the **mouth**. The mouth ___ me by ___.
2. Next, I travel down the **oesophagus**. The oesophagus ___ me by ___.
3. Then, I arrive in the **stomach**. The stomach ___ me by ___.
4. After that, I move into the **small intestine**. The small intestine ___ from me by ___.
5. Finally, I pass through the **large intestine**. The large intestine ___ from me by ___.

**Early Acquisition 学生：** 使用带词库的完形填空版本：*breaks down, moves, digests, absorbs nutrients, absorbs water, chewing, squeezing, mixing with acid, passing through walls, removing water.*

**Developing 学生：** 使用上述开放式句式框架。

**Consolidating 学生及母语者：** 不使用框架撰写旅程——用自己的语言写一段话，融入核心术语。

**学有余力学生的拓展：** "What happens if one organ stops working? Choose one organ and explain what would go wrong."

*有效原因：* 相同的内容（器官与功能），相同的认知要求（描述过程），仅按语言支架水平进行分层。每位学生都练习了语言目标。第一人称视角（"I enter the mouth"）富有吸引力，并使抽象过程具体化。

**第三阶段：复习与评估（8 分钟）**

*SIOP 修改：将举手抢答的课堂小结测验（仅能评估反应最快/最自信的学生）替换为全班参与的评估方式。*

**27:00–32:00 — 迷你白板测验（SIOP 要素 8）**

"Show me on your whiteboards..."
1. "Which organ absorbs nutrients?" [学生写：small intestine]
2. "What does the stomach do to food?" [学生写一个短语或句子]
3. "Put these organs in order: stomach, mouth, large intestine, small intestine, oesophagus" [学生写 1–5]

*有效原因：* “每位”学生都会作答（而不仅仅是举手的人）。教师可以同时扫视所有白板。第 2 题检查学生是否能使用语言目标（描述功能），而不仅仅是回忆名称。语言水平较低的学生仍可通过单词或标注图展示理解。

**32:00–35:00 — 回到目标（SIOP 要素 8）**

"Look at our two objectives. Content: can you name the organs and describe their functions? Let's check — everyone point to the organ I name on your diagram..."

"Language: can you use the sentence 'The [organ] [verb]s the food by [process]'? Turn to your partner and say one sentence about one organ. Go."

倾听学生是否正确使用句式框架。识别仍需支持的学生——他们在下节课需要额外练习。

### SIOP 要素检查表

| SIOP 要素 | 落实方式 |
|---|---|
| **1. 教学准备** | 内容目标和语言目标均明确、写在黑板上，并在课末重新回扣 |
| **2. 构建背景** | 3 分钟热身联系普遍经验（吃东西），再引入科学词汇 |
| **3. 可理解输入** | 每次讲解一个器官，视觉 + 听觉 + 书面，逐步构建黑板表格，齐声跟读，为 New to English 学生提供双语词汇表 |
| **4. 策略** | 句式框架为语言产出搭建支架；逐步构建的表格作为参考工具；第一人称视角使抽象过程具体化 |
| **5. 互动** | 带口语要求的同伴标注；课堂小结时的结对检查；没有脱离口语交流的纯静默个人任务 |
| **6. 练习/应用** | “食物的旅程”任务要求将语言目标与内容结合使用；按支架水平分层，而非按内容分层 |
| **7. 课堂实施** | 讲授从 15 分钟缩短为 9 分钟的互动输入；活动多样化；通过巡视持续监控理解 |
| **8. 复习/评估** | 迷你白板（全班参与，而非仅限举手者）；明确回扣两个目标；同伴互查语言目标 |

### 教师调整建议

1. **放慢教师话语，但不要简化它。** 说 "The oesophagus moves the food by squeezing it downwards — this squeezing is called peristalsis"——放慢语速并重复 "squeezing" 和 "peristalsis"。不要说 "The food goes down a tube." 科学语言本身就是课程内容。

2. **边说边写。** 每说出核心术语就写在黑板上。EAL 学生可以阅读并重读他们无法重听的内容。逐步构建的表格会成为课堂上最重要的资源。

3. **齐声跟读练习发音。** "Say it with me: oesophagus. O-soph-a-gus." 这并不幼稚——它让科学发音练习对每个人都显得自然，并让 EAL 学生有机会练习说出不熟悉的词。

4. **指令分步给出，一次一步。** 不要说："Get your worksheet, work with your partner, complete the sentences, and put your hand up when you're done"——而是说："Step 1: Pick up the worksheet from the front table." [停顿] "Step 2: Work with your partner." [停顿] "Step 3: Complete the sentences using the table on the board to help you."

5. **留出等待时间。** 提问后等待 5–7 秒（而不是通常的 1–2 秒）。EAL 学生需要处理时间来用英语组织回答。明确说出 "Take your time" 能传递出速度不是目标的信号。

6. **将“任务理解检查”与“内容理解检查”分开。** 在学生开始任何活动前，问："What are you going to do?"（检查他们是否理解任务）。不要问 "Do you understand?"（得到的回答总是 "yes"）。问："Tell me step one"——这能揭示他们是否听懂了指令。

### 修改内容与原因对照

| 原教案 | 修改后 | 原因 |
|----------|----------|-----|
| 15 分钟教师讲解（一次性展示所有幻灯片） | 9 分钟互动输入（每次一个器官，视觉 + 听觉 + 书面，齐声跟读） | SIOP 可理解输入：多模态、分步、渐进。在保持内容的同时降低认知负荷。 |
| 安静的个人图形标注 | 带口语句子要求的同伴标注 | SIOP 互动：EAL 学生需要“使用”语言，而不仅仅是接收语言。同伴合作提供了低风险的口语练习。 |
| 阅读课本 + 回答问题 | “食物的旅程”句式框架任务，按支架水平分层 | SIOP 练习/应用：重阅读的任务往往是伪装成内容评估的语言障碍。修改后的任务通过更易进入的形式评估相同的学科知识。 |
| 举手抢答的小结测验 | 迷你白板全班评估 + 同伴检查 | SIOP 复习：举手只评估反应最快/最自信的学生。白板同时评估所有人。 |
| 无语言目标 | 明确语言目标："The [organ] [verb]s by [process]" | SIOP 教学准备：没有语言目标，语言发展就是偶发的；有了语言目标，它才是刻意且系统的。 |

---

## 已知局限性

1. **SIOP 修改需要时间备课。** 修改后的教案对所有学生都更好，但比原教案需要更多准备。随着教师逐渐熟悉 SIOP 原则，这些修改会变得更自动化，但初期的投入是显著的。本技能加速了备课过程，但无法消除这一过程。

2. **这些修改假设处于常规课堂配置。** 拥有专职 EAL 教师、双语助教或第一语言资源渠道的学校，可以实施本修改未涵盖的额外支持。输出提供的是在常规资源下即可运作的基准修改；在条件允许时，应叠加额外的专业支持。

3. **遮蔽式教学每次针对一节课，但语言发展是纵向持续的。** 本技能修改单节教案，但 EAL 学生需要在所有课程中获得一致且持续的支持。一节课的语言目标应当与后续课程的语言目标相衔接，构建连贯的学术语言发展体系。单节教案的修改是必要的，但还不够——它必须是全校性策略的一部分。
