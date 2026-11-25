---
# AGENT SKILLS STANDARD FIELDS (v2)
name: reflective-practice-prompt-generator
description: "为特定教学经历或专业学习挑战生成结构化反思提示。适用于课后复盘、撰写教学日志或筹备教练对话。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/reflective-practice-prompt-generator"
skill_name: "反思性实践提示生成器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Schön (1983) — The Reflective Practitioner: how professionals think in action"
  - "Timperley (2011) — Realizing the Power of Professional Learning"
  - "Dewey (1933) — How We Think: a restatement of the relation of reflective thinking to the educative process"
  - "Brookfield (2017) — Becoming a Critically Reflective Teacher"
  - "Kolb (1984) — Experiential Learning: experience as the source of learning and development"
input_schema:
  required:
    - field: "teaching_experience"
      type: "string"
      description: "待反思的具体课程、互动或事件——发生了什么"
    - field: "reflection_purpose"
      type: "string"
      description: "教师希望从本次反思中学到什么——解决问题、理解原因、获得成长"
  optional:
    - field: "teacher_context"
      type: "string"
      description: "教龄经验、学科、当前专业学习目标"
    - field: "emotional_response"
      type: "string"
      description: "教师对该经历的情绪感受——沮丧、惊讶、不确定、自豪"
    - field: "reflection_depth"
      type: "string"
      description: "表层（发生了什么？）、分析性（为什么发生？）或批判性（我预设了什么假设？）"
    - field: "time_available"
      type: "string"
      description: "可用于反思的时间——5分钟、15分钟、深度日志撰写"
output_schema:
  type: "object"
  fields:
    - field: "reflection_prompts"
      type: "array"
      description: "引导教师从描述经由分析走向行动的提示序列"
    - field: "lens_analysis"
      type: "object"
      description: "鼓励教师从多元视角审视经历的提示——学生、同事、理论、自传"
    - field: "action_prompts"
      type: "array"
      description: "将反思推向具体下一步行动的问题"
    - field: "journaling_scaffold"
      type: "string"
      description: "若教师偏好书面写作，提供结构化的书面反思框架"
chains_well_with:
  - "instructional-coaching-conversation-guide"
  - "lesson-observation-protocol-designer"
  - "teacher-inquiry-cycle-designer"
  - "lesson-study-cycle-designer"
  - "pedagogical-content-knowledge-developer"
teacher_time: "2 分钟"
tags: ["reflection", "Schön", "Timperley", "reflective-practice", "professional-learning", "journaling"]
---

# 反思性实践提示生成器

## 本技能的功能

生成校准至特定教学经历与反思目的的结构化反思提示——引导教师从表层描述（“发生了什么？”）经由分析性反思（“为什么会发生？”）走向批判性反思（“我当时预设了什么假设？”），并最终落脚于行动规划（“我将做哪些不同的改变？”）。来自 Schön 研究的核心洞察在于：专业人士主要不是从经验中学习——他们是从**反思**经验中学习。没有结构化反思，一名拥有20年教龄的教师可能只是把第一年的经验重复了20遍。产出包括深度递进的分层提示、Brookfield 的四重视角分析（从自传、学生、同事与理论视角审视经历），以及确保反思带来改变而非仅仅停留在理解层面的具体行动提示。AI 在此处具有独特价值，因为有效的反思提示必须精准校准至具体经历——笼统的提示（“这节课上得怎么样？”）只会产出笼统的反思，而具体提示（“你说小组合作散架了——究竟是在哪一秒崩盘的，当时你正在做什么？”）才会产出具体洞察。

## 循证基础

Schön（1983）区分了行动中反思（reflection-in-action，教学过程中当场随机应变思考）与对行动的反思（reflection-on-action，事后回溯思考）。两者皆不可或缺，但对行动的反思——事后对实践的系统性、结构化审视——正是专业知识建构之所在。Dewey（1933）确立了反思不仅仅是“回想”一段经历，而是一个严谨的探究过程：识别问题、提出假设、对照证据检验并得出结论。Timperley（2011）强调，最有力的专业学习涉及教师审视自身实践对学生学习的**影响**——不仅反思自己做了什么，更反思学生因此实际学到了什么。Brookfield（2017）提出了批判性反思的四个透镜：自传透镜（审视自身假设与经历）、学生之眼（从学生视角看教学）、同事感知（同伴会如何解读该事件）以及理论文献（研究对该议题怎么说）。运用多重视角能防止最常见的反思陷阱：不断印证自己原本就相信的东西。Kolb（1984）提出了经验学习圈：具体经验 → 反思性观察 → 抽象概念化 → 积极实验。这一循环表明，没有行动的反思是不完整的——反思的目的在于产出改变后的实践，而不仅仅是改变后的理解。

## 输入模式

教师必须提供：
- **教学经历：** 发生了什么。*例如：“我第一次在十年级班上尝试小组合作，结果一片混乱——两个小组合作得不错，三个小组完全跑偏，还有一个小组爆发冲突搅乱了全班” / “我自以为给出了一项任务的清晰指令，结果发现半个班完全不知道该做什么” / “一名学生告诉我我的课很无聊，我不知道该如何回应”*
- **反思目的：** 想学到什么。*例如：“我想弄明白小组合作为什么失败，以便下次做得更好” / “我想找出为什么我的指令总是落不了地” / “我想消化这份反馈并决定是否要做出改变”*

可选（如有，由上下文引擎注入）：
- **教师背景：** 经验水平、学科、目标
- **情绪反应：** 当时的感受
- **反思深度：** 表层、分析性或批判性
- **可用时间：** 可用于反思的时间

## 提示词

```
You are an expert in reflective practice, with deep knowledge of Schön's (1983) reflection-on-action, Dewey's (1933) disciplined inquiry process, Timperley's (2011) focus on impact on student learning, Brookfield's (2017) four critical lenses, and Kolb's (1984) experiential learning cycle. You understand that effective reflection is structured, specific, and leads to action — it is not vague self-evaluation or unfocused worrying.

CRITICAL PRINCIPLES:
- **Specific, not generic.** "How did the lesson go?" produces "OK, I suppose." A specific prompt targeted at the exact experience produces insight. Match the prompt to the experience.
- **Layered depth.** Start with description (what happened?), move to analysis (why did it happen?), then to critical reflection (what assumptions was I making?). Don't start with the deepest level — teachers need to describe before they can analyse.
- **Multiple lenses (Brookfield, 2017).** Encourage the teacher to view the experience from their own perspective, the students' perspective, a colleague's perspective, and a research/theory perspective. Single-lens reflection confirms existing beliefs; multi-lens reflection challenges them.
- **Reflection must lead to action (Kolb, 1984).** If reflection doesn't change practice, it's rumination, not professional learning. Every reflection sequence should end with "What will I do differently?"
- **Honour the emotional response.** Teaching experiences carry emotions — frustration, pride, shame, confusion, satisfaction. The prompts should acknowledge the emotion before moving to analysis. Skipping the emotion produces intellectual reflection that doesn't connect to practice.

Your task is to generate reflection prompts for:

**Teaching experience:** {{teaching_experience}}
**Reflection purpose:** {{reflection_purpose}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Teacher context:** {{teacher_context}} — if not provided, design prompts for a general teaching context.
**Emotional response:** {{emotional_response}} — if not provided, include a prompt that surfaces the emotional response.
**Reflection depth:** {{reflection_depth}} — if not provided, design prompts at all three levels (descriptive, analytical, critical).
**Time available:** {{time_available}} — if not provided, design for 15 minutes of structured reflection.

Return your output in this exact format:

## Reflection Prompts: [Experience Summary]

**Experience:** [Brief description]
**Purpose:** [What the teacher wants to learn]

### Layer 1 — Description (What happened?)

[2–3 prompts that help the teacher describe the experience specifically and accurately]

### Layer 2 — Analysis (Why did it happen?)

[2–3 prompts that help the teacher analyse causes and connections]

### Layer 3 — Critical Reflection (What assumptions am I making?)

[2–3 prompts from Brookfield's four lenses — examining the experience from multiple perspectives]

### Layer 4 — Action (What will I do differently?)

[2–3 prompts that move from understanding to concrete next steps]

### Quick Reflection Option

[A 5-minute version for teachers with limited time — 3 essential prompts that cover description, analysis, and action]

**Self-check before returning output:** Verify that (a) prompts are specific to the described experience, (b) prompts are layered from description to analysis to critical reflection to action, (c) at least one prompt uses Brookfield's student lens, (d) the action layer generates concrete next steps, and (e) the quick option is genuinely quick — 5 minutes maximum.
```

## 示例输出

**场景：** *教学经历：“我第一次在十年级班上尝试小组合作，结果一片混乱——两个小组合作得不错，三个小组完全跑偏，还有一个小组爆发冲突搅乱了全班。我最后不得不大吼着把注意力拉回来，这是我最讨厌做的事。下课时，我觉得自己浪费了40分钟，学生什么也没学到。” / 反思目的：“我想弄明白哪里出了问题，以便决定是再试一次小组合作，还是干脆退回个人独立作业。” / 情绪反应：“沮丧、尴尬，甚至怀疑自己是不是当老师的料” / 教师背景：“教龄2年，科学教师，在个人/结对作业时课堂管理总体良好”*

---

## 反思提示：小组合作混乱——十年级科学

**经历：** 首次在十年级尝试小组合作；多数小组跑偏；一组爆发冲突；教师大吼控场；感觉浪费了时间。
**目的：** 理解问题出在哪里，并决定是否再次尝试小组合作。

### 第一层——描述（发生了什么？）

**提示 1：** “让我们放慢脚步，重现这节课。究竟是在哪一个确切时刻开始失控的？你说两个小组做得不错、三个没有——那些‘在工作’的小组和‘跑偏’的小组之间有什么不同？你能描述一下工作中的小组当时**在做什么**，以及跑偏的小组当时在做什么吗？”

*为什么问这个：* 教师的叙事是“一片混乱”。但混乱并非铁板一块——有两个小组运作良好。理解运作良好小组与失控小组之间的**差异**，能揭示到底缺少了什么条件，而非证明小组合作不可行。

**提示 2：** “你说你‘最后不得不大吼’。带我走一遍你大吼前的60秒。你先尝试了什么？你从班级里捕捉到了什么信号？在哪个节点你判定局势已经超出了常规管理范围？”

*为什么问这个：* 教师对大吼感到羞愧。该提示审视导致大吼的序列——这可能会揭示问题不在于教师的管理能力，而在于任务设计（缺乏足够结构的小组、过于开放的任务，或未对协作进行充分铺垫）。

**提示 3：** “爆发冲突的那个小组——冲突是关于什么的？是关于任务的（对科学问题的分歧）、关于角色的（谁做什么），还是关于人际关系的（原本就相处不来的学生）？”

*为什么问这个：* 不同类型的冲突有不同的成因与解法。科学分歧是富有成效的冲突，需要引导而非压制；人际冲突需要审慎分组；角色冲突需要结构化分工。教师需要识别这次属于哪一种。

### 第二层——分析（为什么会发生？）

**提示 4：** “回头看，你为这次小组合作提供了多少结构？你是否明确规定了：每位组员的角色是什么、产出应该长什么样、他们有多少时间，以及‘成功的小组合作’是什么样子？如果其中有任何缺失，你认为哪一项影响最大？”

*为什么问这个：* 大多数初次小组合作的失败是因为结构不足，而非小组合作本身无效。该提示帮助教师自行诊断结构缺口，无需教练直接指出。

**提示 5：** “你说学生‘什么也没学到’。你怎么知道？有没有可能那两个合作得不错的小组确实学到了一些东西，哪怕整体印象是混乱的？你在课前、课中或课后有没有在任何节点检查过理解？”

*为什么问这个：* 教师的情绪反应（“浪费了40分钟，什么也没学到”）可能比现实更极端。六个组里有两个运作良好并非彻底失败——而是带有明确改进空间的部分成功。该提示挑战灾难化叙事，同时不否定其挫败感。

**提示 6：** “你说你在个人和结对作业时课堂管理‘总体良好’。小组合作到底是什么改变了管理动态？是音量上升、身体走动、失去中央控制，还是其他因素？”

*为什么问这个：* 帮助教师识别具体的管理挑战——这是解决问题的第一步。从“我管不好小组合作”转向“当噪音升高时我很难听清单个小组，从而感到失控”，会变成一个更容易解决的问题。

### 第三层——批判性反思（我预设了什么假设？）

**提示 7——学生透镜（Brookfield）：** “如果你问一个跑偏小组的学生发生了什么，你觉得他会怎么说？他会说‘我们就是趁机胡闹’，还是‘我们其实不太确定该干嘛’，还是别的什么？而那些在认真工作的小组学生又会怎么解释**他们**为什么能搞定？”

*为什么问这个：* 教师正从自己的视角（混乱、失败、尴尬）看待这段经历。学生可能有着完全不同的解读——他们可能是困惑，而非挑衅。透过学生的眼睛看问题，往往会发现问题出在设计，而非纪律。

**提示 8——理论透镜（Brookfield）：** “关于小组合作的研究（如 Johnson & Johnson, Mercer）表明，有效协作需要明确教学——在被要求开展小组合作之前，学生需要被教授**如何**在小组中工作。你的十年级学生懂得如何协作吗，还是你默认他们早就应该会了？”

*为什么问这个：* 挑战“学生天然就该懂得如何小组合作”的预设。协作就像其他任何技能一样，需要教授和练习。这把失败重构为设计问题（未先教技能），而非学生问题（他们不适合小组合作）。

**提示 9——自传透镜（Brookfield）：** “你说你在怀疑自己‘是不是当老师的料’。仅仅一节艰难的课就让你质疑整个职业生涯。这种反应从何而来？是否存在一种模式——你在一次糟糕经历后容易灾难化思考，还是这件事触动了某个特定的脆弱点？”

*为什么问这个：* 这是最深层也最具挑战性的提示。它直击情绪核心——教师的自我效能感。目的不是做心理治疗，而是帮助教师认识到“一节糟糕的小组课 ≠ 我是个糟糕的老师”。如果这种失败后灾难化的模式反复出现，它就值得被正视。

### 第四层——行动（我将做哪些不同的改变？）

**提示 10：** “基于你的反思，你打算再试一次小组合作吗？如果试——你会改什么？请具体说明：你会在结构上**增加**什么、在任务前你会教学生哪些关于协作的知识，以及你会如何监控各小组？”

**提示 11：** “如果你明天可以对同一个班重上这节课，你会做出哪**三个**改变？（只改三个——不是推倒重来。）”

**提示 12：** “你的下一步是什么？不是模糊的打算（‘我以后找机会再试试小组合作’），而是一个具体计划：‘下周[星期几]在十年级关于[主题]的课上，我将带着[这些具体结构改动]尝试小组合作。’你什么时候做，以及你如何判断情况有所改善？”

### 快速反思选项（5分钟）

如果时间有限，回答这三个问题：

1. **发生了什么？** “那两个运作良好的小组拥有 ___，而那三个跑偏的小组没有。”
2. **为什么？** “出问题最可能的原因是 ___ [结构不足 / 任务不清 / 学生不懂得如何协作 / 分组不当]。”
3. **下一次：** “如果我再试一次小组合作，我要增加的**一件事**是 ___。”

---

## 已知局限

1. **反思提示是工具，而非心理治疗。** 上述提示专为针对教学实践的专业反思而设计。如果教师对一节困难课程的情绪反应非常剧烈（持续痛苦、长期自我怀疑、影响身心健康），他们可能需要与导师或心理咨询师进行支持性谈话，而不仅仅是反思提示。

2. **书面反思不是唯一形式。** 部分教师通过对话（与同事、教练或导师）比通过写作反思得更有效。这些提示既可用于对话，也可用于写日志——媒介不如结构重要。

3. **没有行动的反思只是反刍（rumination）。** 如果教师反思得很深，却对实践没有任何改变，那这种反思在智识上或许有趣，在专业上却毫无用处。行动层是不可妥协的——每一次反思都必须以具体的下一步结尾。
