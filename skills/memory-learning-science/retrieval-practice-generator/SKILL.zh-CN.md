---
# AGENT SKILLS STANDARD FIELDS (v2)
name: retrieval-practice-generator
description: "围绕主题或概念生成不同难度层级的提取练习题。适用于设计课堂导入小测、复习活动或低风险测试材料。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/retrieval-practice-generator"
skill_name: "提取练习题目生成器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Roediger & Butler (2011) — The critical role of retrieval practice in long-term retention"
  - "Karpicke & Roediger (2008) — The critical importance of retrieval for learning"
  - "Rowland (2014) — Meta-analysis: the effect of testing versus restudy on retention (effect size 0.50)"
  - "Agarwal et al. (2012) — Classroom-based retrieval practice studies with middle school students"
  - "Dunlosky et al. (2013) — Practice testing rated as high-utility learning strategy"
input_schema:
  required:
    - field: "topic"
      type: "string"
      description: "学生需要提取的具体概念或技能"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及大致先验知识水平"
    - field: "question_count"
      type: "integer"
      description: "需要生成的题目数量（建议 6–10 题）"
  optional:
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：个体语言水平、先验知识缺口"
    - field: "competency_framework"
      type: "string"
      description: "来自上下文引擎：学校的评估框架或课程标准"
    - field: "time_since_learning"
      type: "string"
      description: "学生距离首次学习该材料已过去多长时间"
    - field: "known_misconceptions"
      type: "array"
      description: "在该群体中已观察到的具体常见误解"
output_schema:
  type: "object"
  fields:
    - field: "questions"
      type: "array"
      description: "提取练习题列表，每题包含题干、提取类型标签（自由回忆 / 线索回忆 / 再认）以及难度估计"
    - field: "spacing_recommendation"
      type: "string"
      description: "相对于初次学习，何时使用这些题目"
    - field: "answer_notes"
      type: "string"
      description: "正确答案要点及需警惕的常见错误"
    - field: "teacher_script"
      type: "string"
      description: "简短的实施建议话术（如何组织该提取活动）"
chains_well_with:
  - "spaced-practice-scheduler"
  - "formative-assessment-technique-selector"
  - "gap-analysis-from-student-work"
  - "cognitive-load-analyser"
teacher_time: "3 分钟"
tags: ["retrieval", "memory", "assessment", "spaced-practice", "testing-effect"]
---

# 提取练习题目生成器

## 本技能的功能

生成以“从记忆中重构知识”为核心（而非重读或基于熟悉感的猜测）的练习题，并附带针对新手学习者或热身环节的明确标注型再认例外题。本技能区分自由回忆（无提示）、线索回忆（部分提示）与再认（从选项中选择）题型，并根据学生水平与距离学习的时间校准题型配比。AI 在此处具有独特价值，因为设计针对“重构”而非“再认”的题目需要深入理解测试效应文献——大多数教师自编的测验题往往在不经意间只测试了再认能力。

## 循证基础

测试效应（testing effect）是认知心理学中最稳健的发现之一。Karpicke 与 Roediger（2008）证明，即便重新学习（restudy）投入了更多的总接触时间，提取练习仍能产生显著更好的长期记忆保持。Roediger 与 Butler（2011）确立了提取练习通过不同于编码的独特机制强化记忆痕迹——重构行为本身就会改变记忆。Rowland（2014）对159项研究的元分析发现，测试相比重学的平均效应量为 0.50，且在跨年龄段、材料类型与延迟间隔中均表现稳健。关键的是，Agarwal 等人（2012）在初中生的真实课堂环境中复现了这些效应，证实了从实验室向课堂的迁移。Dunlosky 等人（2013）在其具有里程碑意义的十项学习技术综述中，将练习测试（practice testing）评为仅有的两项“高效用”学习策略之一。

## 输入模式

教师必须提供：
- **主题：** 学生需要提取的具体概念或技能。*例如：“第一次世界大战的起因” / “光合作用光反应” / “解一元一次方程”*
- **学生水平：** 年级与大致先验知识。*例如：“九年级，中等水平，两周前学过本主题” / “十二年级生物，高先验知识”*
- **题目数量：** 需要生成的题目数量。*例如：8*

可选（如有，由上下文引擎注入）：
- **学生档案：** 个体语言熟练度水平、从先前评估中识别出的知识缺口
- **能力框架：** 所针对的具体课程标准或评估框架
- **距离学习的时间：** 距离首次教授该材料经过的时长（影响难度校准）
- **已知误解：** 在学生作答中已观察到的具体误解

## 提示词

```
You are an expert in cognitive psychology specialising in the testing effect and retrieval-based learning. You have deep knowledge of Roediger & Butler's (2011) work on retrieval practice, Karpicke & Roediger's (2008) research on the critical importance of retrieval for learning, and Rowland's (2014) meta-analysis demonstrating robust effect sizes for testing versus restudy.

Your task is to generate {{question_count}} retrieval practice questions on the topic "{{topic}}" for {{student_level}}.

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Time since learning:** {{time_since_learning}} — if not provided, assume the material was taught within the last 1–2 weeks and calibrate difficulty accordingly.
**Known misconceptions:** {{known_misconceptions}} — if not provided, include questions targeting the most common misconceptions for this topic based on your subject knowledge.
**Competency framework:** {{competency_framework}} — if not provided, generate questions aligned to general curriculum expectations for the stated year group.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical mixed-ability class with no specific language or learning needs.

Apply these evidence-based criteria when generating questions:

1. **Retrieval type distribution:** Include a mix of:
   - Free recall questions (no cues — e.g. "Explain the process of..." / "List the factors that...") — these produce the strongest learning effect but are hardest
   - Cued recall questions (partial cues — e.g. "The three main causes were _____, _____, and _____" / "Complete this diagram...") — moderate difficulty, good scaffolding
   - Recognition questions (select from options — e.g. multiple choice) — weakest retrieval effect but useful for building confidence in novice learners
   Weight toward free and cued recall. Only include recognition questions for novice learners or as warm-up.

2. **Reconstruction with a novice/warm-up exception:** Free and cued recall questions require reconstruction from memory. Recognition questions may be included under rule 1 for novices or warm-up; label them honestly and do not count selecting an option as free recall. Use meaningful distractors and feedback rather than surface matching; invite a brief explanation where accessible. Check questions and answer notes against supplied taught material. If only a topic is supplied, label them a subject-knowledge draft and ask the teacher to verify terminology, coverage and answers against what was actually taught before use.

3. **Target the right knowledge:** Questions should target the core concepts, relationships, and procedures — not trivial details, dates, or definitions unless those are genuinely important to understanding.

4. **Difficulty calibration:** If time since learning is recent (< 1 week), include more cued recall. If time since learning is longer (> 2 weeks), free recall becomes more valuable as it provides stronger retrieval practice during the forgetting phase.

5. **Misconception targeting:** If known misconceptions are provided, include at least 2 questions specifically designed to surface those misconceptions.

Return your output in this exact format:

## Retrieval Practice Questions: [Topic]

**For:** [Student level]
**Spacing recommendation:** [When to use these questions — e.g. "Use 3–7 days after initial teaching as a practical starting point; adapt timing to prior learning, retrieval success, retention goals and the timetable. Re-use a subset at 2–4 weeks for a second retrieval opportunity."]

### Questions

For each question, provide:
- The question text
- **Type:** [Free Recall / Cued Recall / Recognition]
- **Targets:** [What specific knowledge this retrieves]

### Answer Notes

For each question, provide:
- Key points for a correct answer
- Common errors or misconceptions to watch for

### Implementation Script

A brief (3–4 sentence) script for how the teacher should run this retrieval activity in class, including:
- Whether to allow notes (no — that defeats the purpose)
- How long to give students (typically 8–12 minutes for 6–10 questions)
- What to do after (discuss answers, identify gaps, do NOT grade — low-stakes is essential)

**Self-check before returning output:** Verify that (a) recall questions require reconstruction and any recognition items are labelled novice/warm-up exceptions, (b) the mix of retrieval types is appropriate for the student level, (c) no question is answerable from the question text alone without prior knowledge, and (d) the questions target meaningful knowledge, not trivia, and (e) taught-source verification is complete or explicitly pending teacher review.
```

## 示例输出

**场景：** *主题：“侵蚀作用的成因与过程” / 学生水平：“七年级地理，混合能力，10天前学过此主题” / 题目数量：8*

---

## 提取练习题目：侵蚀作用的成因与过程

**适用对象：** 七年级地理，混合能力
**核验说明：** 学科知识初稿；未提供实际授课材料。使用前请教师对照实际授课内容核对术语、覆盖范围与答案要点。第8题属于面向新手支持的再认热身题，不作为自由回忆的证据。
**间隔建议：** 可在授课后第10天作为实用的复习契机使用；这并非针对本班的已证实最优间隔。2–3周后可重复使用第1、3、5、7题进行第二次提取机会。此后，每半学期将侵蚀作用提取练习融入跨主题混合小测一次。

### 题目

**第1题：** 不查看任何笔记，解释侵蚀作用（erosion）与风化作用（weathering）的区别。为什么它们不是同一回事？
- **类型：** 自由回忆
- **目标：** 区分两个常被混淆的过程；理解侵蚀涉及物质的搬运

**第2题：** 说出河流造成的四种主要侵蚀类型。针对每一种，描述岩石或河床在物理上发生了什么。
- **类型：** 自由回忆
- **目标：** 水力作用、磨蚀作用、磨圆/互磨作用、溶蚀作用——以及每种作用的具体机制，而不仅是名称标签

**第3题：** 一位农民注意到山坡田地里的土壤一年比一年薄。这片田地没有树木或树篱。用正确的地理学术语解释为什么土壤正在消失。
- **类型：** 线索回忆（情境提供了上下文线索）
- **目标：** 土壤侵蚀过程、植被在防止侵蚀中的作用、地表径流

**第4题：** 补全以下序列：岩石被风化作用分解 → 松散物质被侵蚀作用__________ → 物质被河流携带，这称为__________ → 当河流流速减慢时物质被放下，这称为__________。
- **类型：** 线索回忆
- **目标：** 搬运/侵蚀、搬运作用、沉积作用——完整循环

**第5题：** 画一幅简图展示瀑布是如何由侵蚀作用形成的。标注至少四个特征，并解释每个位置正在发生哪种类型的侵蚀。
- **类型：** 自由回忆（凭记忆绘图）
- **目标：** 下切/掏蚀、硬岩/软岩、跌水潭、溯源后退——对过程的空间理解

**第6题：** 一名学生写道：“侵蚀作用就是岩石被天气分解成更小碎块的过程。”这句话有什么错误？请写一个更准确的版本。
- **类型：** 线索回忆（纠错）
- **目标：** 区分风化与侵蚀；理解侵蚀的核心是移动，而不仅是分解

**第7题：** 为什么某些地方的侵蚀发生得比其他地方更快？给出三个具体因素，并解释每个因素如何影响侵蚀速率。
- **类型：** 自由回忆
- **目标：** 岩石类型/硬度、气候/降雨、植被覆盖、人类活动——因果推理

**第8题：** 以下哪项是磨蚀作用（abrasion）的例子？
(a) 盐晶体在悬崖岩缝中膨胀
(b) 河流携带的卵石摩擦撞击河床
(c) 雨水中的二氧化碳溶解石灰岩
(d) 海浪将空气压缩进岩石裂缝
- **类型：** 再认
- **目标：** 将磨蚀作用与盐风化（a）、化学风化/溶蚀作用（c）及水力作用（d）区分开

### 答案要点

- **第1题：** 核心区分——风化作用在**原地**分解岩石，侵蚀作用涉及物质的**搬运**。常见错误：学生说“侵蚀就是岩石破碎”（与风化混淆）。
- **第2题：** 水力作用（水流的冲击力）、磨蚀作用（沉积物刮擦河床）、互磨作用（颗粒相互碰撞研磨）、溶蚀作用（化学溶解）。常见错误：混淆磨蚀作用与互磨作用。
- **第3题：** 没有植被根系固土，降雨会产生地表径流，将表土冲刷下坡。核心术语：地表径流、土壤侵蚀、截留缺失。常见错误：只说“被风吹走了”而未解释基于水的机制。
- **第4题：** 被搬运（或被卷走/移动）、搬运作用、沉积作用。常见错误：三个空全部填“侵蚀”。
- **第5题：** 必须展示硬岩覆于软岩之上、软岩被掏蚀、悬空岩檐、坍塌、跌水潭以及通过溯源后退形成峡谷。常见错误：把它画成单一瞬间事件，而非随时间推移的过程。
- **第6题：** 该陈述描述的是风化作用，而非侵蚀作用。侵蚀作用特指物质的**移动**。更准确的表述：“侵蚀作用是指风化后的物质被河流、海浪、风或冰川等营力拾取并搬运的过程。”
- **第7题：** 可接受：岩石硬度/类型、降雨量与强度、植被覆盖度、坡度、人类活动（砍伐森林、工程建设）。必须解释机制，而非仅罗列因素。
- **第8题：** 正确答案：(b)。干扰项分析：(a) = 盐风化，(c) = 化学风化/溶蚀作用，(d) = 水力作用。

### 实施话术

将此作为低风险提取热身活动开展——不准看笔记、不准翻课本、不使用电子设备。告诉学生：“这不是计分考试，而是一次记忆锻炼。卡壳是正常的，而且实际上有助于你们学习——这就是研究的发现。”给足10分钟完成全部8题。提前完成的学生应回头补充更多细节。时间到后，全班一起讨论答案，重点讲解第1题和第6题（最常见的误解）。不要收卷或打分——学习发生在提取尝试本身，而不是分数里。

---

## 已知局限

1. **无法对照特定教材或考纲核验事实准确性。** 这些题目是基于通用学科知识生成的。教师应核对术语与预期答案是否与实际授课内容一致——尤其是第2题和第4题，不同课程体系中的具体术语可能存在差异。

2. **自由回忆题可能会让先验知识极低或英语水平有限的学生感到不堪重负。** 对于 EAL 学生或存在明显知识缺口的学生，应提高线索回忆与再认题的比例。可与“支架式任务修改器”联动以生成语言适配版本。

3. **间隔建议是基于间隔效应研究的实用起点，而非针对该班级的已证实最优方案。** 现实中的课堂排课限制（课表空档、假期、考试窗口）可能使建议间隔难以完全落地。在时间安排上始终需要教师的专业判断。
