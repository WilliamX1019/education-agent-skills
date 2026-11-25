---
# AGENT SKILLS STANDARD FIELDS (v2)
name: perma-based-lesson-designer
description: "设计将 PERMA 身心健康要素与学业学习目标相融合的课程。适用于规划兼顾内容掌握与学生蓬勃发展（flourishing）的课堂。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/perma-based-lesson-designer"
skill_name: "基于 PERMA 的课程设计器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Seligman (2011) — Flourish: a visionary new understanding of happiness and well-being"
  - "Kern et al. (2015) — A multidimensional approach to measuring well-being in students: EPOCH"
  - "Norrish et al. (2013) — An applied framework for Positive Education at Geelong Grammar School"
  - "White & Kern (2018) — Positive Education: learning and teaching for wellbeing and academic mastery"
  - "Waters (2011) — A review of school-based positive psychology interventions"
input_schema:
  required:
    - field: "lesson_content"
      type: "string"
      description: "本节课的学科内容与学习目标"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "perma_focus"
      type: "string"
      description: "优先聚焦的 PERMA 要素——或选择‘全部’以设计均衡的课程"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：班级身心健康数据、投入模式、特殊需求"
    - field: "lesson_duration"
      type: "string"
      description: "课时长度"
    - field: "current_wellbeing_concerns"
      type: "string"
      description: "班级中的具体身心健康关切——焦虑、投入度低、人际关系紧张"
output_schema:
  type: "object"
  fields:
    - field: "perma_lesson_plan"
      type: "object"
      description: "将 PERMA 要素融入学科内容的教案——非独立的心理活动，而是通过学习实现福祉"
    - field: "perma_mapping"
      type: "object"
      description: "每个 PERMA 要素在课程中如何通过具体活动得到体现"
    - field: "teacher_moves"
      type: "array"
      description: "激活每个 PERMA 要素的具体教师策略"
    - field: "reflection_prompts"
      type: "array"
      description: "供学生将学习体验与自身福祉相连接的反思提示"
chains_well_with:
  - "wellbeing-learning-connection-mapper"
  - "motivation-diagnostic-task-redesign"
  - "belonging-classroom-culture-designer"
  - "flow-state-condition-designer"
teacher_time: "4 分钟"
tags: ["PERMA", "positive-education", "Seligman", "flourishing", "wellbeing", "lesson-design"]
---

# 基于 PERMA 的课程设计器（PERMA-Based Lesson Designer）

## 本技能的功能

设计将 Seligman 的 PERMA 框架（积极情绪 Positive Emotion、投入 Engagement、人际关系 Relationships、意义 Meaning、成就感 Accomplishment）融入学科教学内容的课程——不是生硬外挂的“心理健康活动”，而是学习体验本身的固有特征。核心原则在于：身心健康与学习并不是两条互不相干的议程：PERMA 可以作为规划透镜，帮助教师系统性地发掘诸如积极情绪（兴趣、好奇、满足感）、深度投入（心流、专注）、人际关系（协作、讨论）、意义（与重要事物的连接）以及成就感（攻克难题后的收获感）等契机。输出是一份将 PERMA 要素明确对应到教学活动的教案，并附带激活各要素的具体教师策略。AI 在此具有独特价值，因为它可以帮教师系统性地挑选相关 PERMA 条件而不强求五项全占——而且将福祉融入学科内容（而非单开一节“幸福课”）同时需要学科专业知识与积极心理学知识。

## 循证依据

Seligman（2011）提出了作为幸福感模型的 PERMA：积极情绪、投入、人际关系、意义与成就感。Norrish 等（2013）描述了吉隆文法学校（Geelong Grammar School）的积极教育应用框架；White 与 Kern（2018）探讨了将身心健康与学科教学相整合的路径。Kern 等（2015）提出了评估青少年身心健康的多维方法；但对相关构念的测量并不直接验证本教案设计本身。Waters（2011）综述了以学校为基础的积极心理学干预。综合而言，这些文献提供了课程规划的理论依据，但并不构成“生成的 PERMA 课程必然带来福祉或学业提升”“嵌入式方法总优于独立教学”或“研究成果可原封不动迁移至所有学校情境”的证明。

## 输入规范

教师必须提供：
- **课堂内容：** 本节课的主题。*例如：“8 年级科学：光合作用——理解植物如何将光能转化为化学能” / “10 年级英语：分析《麦克白》第一幕第五场中的麦克白夫人形象”*
- **学生水平：** 年级。*例如：“8 年级”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **PERMA 聚焦：** 优先聚焦的要素
- **学生档案：** 班级身心健康数据、投入模式
- **课时长度：** 课程时长
- **当前身心健康关切：** 具体问题

## Prompt

```
You are an expert in Positive Education and the PERMA framework, with deep knowledge of Seligman's (2011) model of wellbeing, Norrish et al.'s (2013) applied framework from Geelong Grammar School, and White & Kern's (2018) practical integration guidance. You understand that Positive Education does NOT mean "happy lessons" or "avoiding difficult content" — it means designing learning experiences that simultaneously develop academic knowledge AND wellbeing through the five PERMA elements.

IMPORTANT: PERMA elements should be INTEGRATED into the academic content, not bolted on. "Five minutes of gratitude journaling at the start, then a normal lesson" is NOT PERMA-based lesson design. Use PERMA to identify relevant opportunities within academic activity. Learning and wellbeing are related aims with separate evidence; this design is not a clinical intervention or a guarantee of either.

IMPORTANT: Not every lesson needs to hit all five elements equally. Some lessons will naturally emphasise Engagement and Accomplishment (a challenging problem-solving lesson); others will emphasise Relationships and Meaning (a collaborative project connected to real-world issues). Design for the PERMA elements that naturally fit the content — don't force all five into every lesson.

Your task is to design a PERMA-integrated lesson for:

**Lesson content:** {{lesson_content}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the lesson content.
**PERMA focus:** {{perma_focus}} — if not provided, design for the elements that best fit the content.
**Student profiles:** {{student_profiles}} — use relevant aggregated/non-identifying access needs; if absent, offer accessible and low-disclosure options without assuming interests or emotions.
**Lesson duration:** {{lesson_duration}} — if not provided, assume 50–60 minutes.
**Current wellbeing concerns:** {{current_wellbeing_concerns}} — if not provided, design for general wellbeing enhancement.

In the mapping, "not targeted in this lesson" with a reason is valid for any element. Retain the learning objective and existing access supports; no emotion or personal disclosure is required. Sensitive/political reflection may use a historical or fictional third-person example, private reflection or a pass, with an accessible academic task still available. Provide seated/written alternatives to movement, debate or public opinion-taking. Check learning from the actual work separately from enjoyment or absorption.

Apply these principles:

1. **Positive Emotion (Seligman, 2011):**
   - Design moments that generate genuine interest, curiosity, surprise, or satisfaction.
   - Positive emotion may accompany engagement; its presence or absence does not establish learning or wellbeing.
   - Avoid forced positivity — "Isn't this fun?" undermines genuine emotion. Let the content create the emotion.

2. **Engagement (Seligman, 2011; Csikszentmihalyi, 1990):**
   - Design for absorption — tasks that are challenging enough to require full attention but achievable enough to sustain effort.
   - Reduce interruptions during deep work periods.
   - Clear goals, immediate feedback, and matched challenge create flow conditions.

3. **Relationships (Seligman, 2011):**
   - Build in structured interaction that requires genuine collaboration — not "sit together and work alone."
   - Design tasks where students need each other's contributions.
   - Create opportunities for peer feedback, discussion, and shared problem-solving.

4. **Meaning (Seligman, 2011):**
   - Connect the content to something larger — why this matters beyond the exam, beyond the classroom.
   - Help students see how this learning serves a purpose they care about.
   - Even abstract content can be connected to meaning: "Understanding photosynthesis helps us understand why deforestation threatens our climate."

5. **Accomplishment (Seligman, 2011):**
   - Design clear checkpoints where students can experience "I did that."
   - Make progress visible — students should be able to see what they've learned during the lesson.
   - Celebrate effort and strategy, not just outcomes.

Return your output in this exact format:

## PERMA Lesson Design: [Lesson Title]

**Content:** [What students learn]
**For:** [Student level]
**Duration:** [Lesson length]

### PERMA Mapping

| PERMA Element | How It's Addressed | Through Which Activity |
|---|---|---|
| Positive Emotion | [Specific feature, or not targeted with reason] | [Activity name/phase] |
| Engagement | [Specific feature, or not targeted with reason] | [Activity name/phase] |
| Relationships | [Specific feature, or not targeted with reason] | [Activity name/phase] |
| Meaning | [Specific feature, or not targeted with reason] | [Activity name/phase] |
| Accomplishment | [Specific feature, or not targeted with reason] | [Activity name/phase] |

### Lesson Plan

[Time-structured lesson plan with PERMA elements embedded in each phase]

### Teacher Moves

[Specific teacher actions that activate each PERMA element — not "be positive" but concrete moves]

### Reflection Prompts

[2–3 prompts that help students notice the connection between their learning experience and their wellbeing]

**Self-check before returning output:** Verify that (a) PERMA elements are integrated into academic content, not bolted on, (b) the lesson maintains academic rigour — it teaches the stated content, (c) not all five elements are forced if the content doesn't naturally support them all, (d) positive emotion comes from genuine intellectual engagement, not from "making it fun," and (e) the lesson could be taught by a subject teacher, not just a wellbeing specialist.
```

## 示例输出

**场景：** *课堂内容：“9 年级历史：妇女参政运动（the suffragette movement）——理解‘温和派’（suffragists）与‘激进派’（suffragettes）所采用的不同方法，并评估哪一种在争取女性选举权方面更有效” / 学生水平：“9 年级” / 课时长度：“55 分钟” / 学科领域：“历史”*

---

## PERMA 课程设计：妇女参政运动——方法与效力

**内容：** 温和派与激进派采用的方法；评估其效力
**适用对象：** 9 年级历史
**时长：** 55 分钟

### PERMA 映射

| PERMA 要素 | 如何体现 | 依托活动 |
|---|---|---|
| 积极情绪（Positive Emotion） | 好奇心——由开场两难问题（为了正义是否应该违法？）激发；惊奇感——发现部分抗争手段之激进；满足感——构建出有理有据的论证。 | 开场两难问题 + 史料分析 |
| 投入（Engagement） | 史料分析期间的持续专注（任务清晰、挑战适度、节奏可调）；辩论准备期间的潜在深度投入（对证据的钻研）。 | 史料分析挑战 + 结构化辩论 |
| 人际关系（Relationships） | 两两合作分析史料。结构化辩论要求倾听并回应他人论点——真正的智识交锋，而不仅仅是轮流发言。 | 配对史料分析 + 全班辩论 |
| 意义（Meaning） | 直接连接正义、平等与权利——学生关心的现实议题。“为了信念违法是否正当？”这一问题连接着他们自身的生活与价值观。 | 开场两难问题 + 结课反思 |
| 成就感（Accomplishment） | 清晰可见的进步：学生从“不太了解妇女参政运动”走到“能运用具体历史证据就哪种方法更有效构建论证”，在结课书面论证中直观体现。 | 史料分析卡片完成 + 结课书面论证 |

### 教案流程

**开场——两难困境（5 分钟）**
展示一个历史问题：“当和平手段未能达成目标时，社会运动者曾考虑过哪些选择？有哪些证据可以支持或质疑每种选择？”切勿要求学生想象针对自身群体的歧视或公开披露当下的政治信仰。

给学生 60 秒静默思考，随后 90 秒同伴讨论。邀请 3–4 名学生自愿基于历史视角分享初步想法；提供私下书面作答或跳过公开讨论的选项。收集多元回应——有人会说“不能做违法的事”，也有人会说“不惜一切代价”。暂不解决这个两难，顺势引出：“这正是 20 世纪初女性面临的真实抉择。今天，我们来看看她们**实际做了什么**——以及这究竟管不管用。”

**PERMA 激活：** 积极情绪（好奇心——两难困境极具思辨张力）；意义（连接正义与个人价值观）；人际关系（同伴讨论）。

**史料分析挑战（20 分钟）**
提供 6 张史料卡——3 张展示温和派方法（和平请愿、演讲、致信议员），3 张展示激进派方法（砸碎橱窗、纵火、绝食抗议、埃普索姆赛马事件）。每张卡包含一手史料摘录、图片及简要背景。

学生两两合作，分析每张史料卡并填写对比表格：
| 方法 | 她们做了什么 | 影响证据 | 风险与代价 |

任务结构清晰（需完成的表格）、挑战适度（分析一手史料有难度但有格式支撑），并设定约 20 分钟的参考时段，根据无障碍与加工速度需求灵活调整，不假定时间压力对所有人都有益。

15 分钟后，每对搭档必须做出判断：“基于你们的分析，哪种方式在赢得选举权上**更有效**？你们需要为自己的判断辩护。”

**PERMA 激活：** 投入（聚焦分析）；人际关系（协作分析）；成就感（完成表格 + 形成立场）。

**结构化辩论（15 分钟）**
将教室分作两侧：温和派支持方在左侧，激进派支持方在右侧。学生可选择坐姿/书面回应、采取暂定立场，或在不披露个人观点的前提下双向评估两种论证；身体移动为可选项且兼顾无障碍。双方各有 3 分钟利用史料卡证据准备最有力的论点。

流程结构：A 方陈述（2 分钟）→ B 方回应（2 分钟）→ A 方回应（2 分钟）→ B 方陈述（2 分钟）。随后邀请学生自愿用口头或书面方式调整基于证据的解读。剩余 4 分钟用于环节过渡与总结回应。

规则：每一条论点都必须引用具体史料。“她们很勇敢”不是论证。“史料 4 中的绝食抗议赢得了公众同情，因为……”才是论证。

**PERMA 激活：** 投入（对自身立场的投入）；人际关系（真正的智识交流——倾听与回应）；积极情绪（辩论的张力、提出有力论证的满足感）；意义（探讨正义与策略）。

**结课论证与反思（15 分钟）**
每位学生独立撰写：“在赢得女性选举权方面，哪种方式——温和派还是激进派——更有效？请至少引用两份史料的证据支撑你的论点。”（写作 10 分钟）

随后在纸张背面进行简短反思（5 分钟）：“今天这节课最让你惊讶的是什么？你的观点在过程中有发生改变吗——如果有，是什么改变了你？”

收齐学业论证部分作为学习证据；个人反思可保留私密、采用历史/虚构人物视角或跳过不填。切勿对个人身心健康/情感披露进行评分。

**PERMA 激活：** 成就感（独立完成一份有证据支撑的完整论证——学生能亲眼看到自己的收获）；意义（反思连接学习与个人思考）；积极情绪（完成扎实作品后的满足感）。

### 教师策略

1. **激发积极情绪：** 让内容本身说话。妇女参政运动本身就充满戏剧张力与思辨性。不要过度旁白渲染（“这难道不令人着迷吗？”）——直接呈现史料，让学生自己产生反应。他们真实的好奇与惊叹远胜教师的单方面热情。

2. **促进深度投入：** 在史料分析期间维持清晰、可调节的工作时段。“你们有 15 分钟——还剩 5 分钟时我会提醒。”留意节奏把握是否有益或制造了不必要压力；保留无障碍支持安排。辩论期间退居幕后——让学生交锋。在需要时支持推理、无障碍、安全与尊重的讨论秩序，并把关“必须引用史料”规则。

3. **培育人际关系：** 在同伴合作期间倾听对话。若某对学生卡住，提示：“史料 3 关于公众反应告诉了你什么？”若一对学生意见相左，肯定道：“很好——历史学家对此也有分歧。支持你们各自观点的证据是什么？”

4. **凸显意义感：** 在开场明确建立与学生生活的联系：“这不仅仅是过去的历史。为了正义是否应该触犯法律这个问题今天依然鲜活——气候抗议、民权运动、政治行动。你们今天学习的妇女参政史，也是关于社会变革如何发生的历史。”

5. **强化成就感：** 下课前学生离开教室时，引导道：“看看你们刚刚写下的论证。哪些史料支撑了它，还有什么能让它更有力？用实际作品来确认真实的进步，而不是想当然地预设大家原本就知道多少。”

### 反思提示

1. “关于激进派与温和派的方法，你今天觉得最惊讶的是什么？有什么挑战了你原本以为自己知道的观念？”
2. “在今天的课上，有没有哪一刻你感到真正沉浸其中——暂时忘了其他杂念？那一刻你在做什么？”
3. “这节课中你的看法有变化吗？如果有，是什么促成了改变——一份史料、同学的一个论点，还是你自己的重新思考？”

---

## 已知局限性

1. **并非每节课都能天然支撑全部五项 PERMA 要素。** 一节数学程序练习课可能主要支撑“投入”与“成就感”，在“意义”或“人际关系”上空间有限。把五个要素硬塞进每一节课只会产出生硬的拼凑。本技能识别内容天然支持哪些要素并围绕它们设计——切勿将其用作强制每节课五项全满的教条。

2. **PERMA 是框架，而非死板配方。** 各要素相互作用、彼此重叠：真正的投入往往带来积极情绪，成就感能建立人际关系（共同成功），意义感能深化投入。映射表是设计工具，而非打钩清单——目标是让一节课浑然一体，而不是机械凑齐五个框。

3. **积极教育研究主要来自资源优渥的学校情境。** 吉隆文法学校（Norrish et al., 2013）的实践发生在一所资源丰厚的私立学校。向其他情境的迁移属于设计假设，而非已确立的结果；资源、文化与准入条件都会改变恰当的实施方式。资源有限的高贫困率学校教师可能需要因地制宜地调整做法——底层框架是扎实的，但实施必须贴合本土情境。
