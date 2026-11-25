---
# AGENT SKILLS STANDARD FIELDS (v2)
name: academic-language-sentence-frame-generator
description: "为学术任务生成分级句框，跨不同语言水平为语言产出搭建脚手架。适用于 EAL 学生在课堂话语中需要结构化语言支持时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "eal-language-development/academic-language-sentence-frame-generator"
skill_name: "学术语言句框生成器"
domain: "eal-language-development"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Gibbons (2015) — Scaffolding Language, Scaffolding Learning"
  - "Zwiers (2014) — Building Academic Language: meeting Common Core standards across disciplines"
  - "Zwiers & Crawford (2011) — Academic Conversations: classroom talk that fosters critical thinking and content understandings"
  - "Kinsella (2005) — Teaching academic vocabulary to English language learners"
  - "Dutro & Moran (2003) — Rethinking English language instruction: an architectural approach"
input_schema:
  required:
    - field: "task_type"
      type: "string"
      description: "学术任务类型——例如解释、比较、论证、评价、假设、概括、描述过程"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "language_proficiency"
      type: "string"
      description: "EAL 语言水平——影响句框复杂度"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：母语背景、特定语言需求"
    - field: "specific_content"
      type: "string"
      description: "学生正在处理的具体主题或内容"
    - field: "output_mode"
      type: "string"
      description: "学生是写作还是口语表达——影响语域与正式度"
output_schema:
  type: "object"
  fields:
    - field: "sentence_frames"
      type: "array"
      description: "针对该任务类型的分级句框集，从重度脚手架到轻度脚手架"
    - field: "discourse_markers"
      type: "array"
      description: "适用于该任务类型的连接词与过渡词"
    - field: "usage_guide"
      type: "string"
      description: "如何有效引入与使用句框——避开‘机械填空’陷阱"
    - field: "progression"
      type: "string"
      description: "如何引导学生从依赖句框过渡到独立产出学术语言"
chains_well_with:
  - "language-demand-analyser"
  - "scaffolded-task-modifier"
  - "vocabulary-tiering-tool"
  - "disciplinary-writing-scaffold"
teacher_time: "2 分钟"
tags: ["sentence-frames", "academic-language", "EAL", "discourse-markers", "scaffolding"]
---

# 学术语言句框生成器

## 本技能的作用

针对特定的学术任务类型与语言熟练度水平，生成恰当的句框（sentence frames）和话语标记词（discourse markers）。不同于泛泛的句子开头清单，这些句框按语言熟练度分级（从适合初学者的重度脚手架句框，到适合较熟练学生的轻度开头提示），精准匹配任务所需的学术思维类型（解释、比较、论证、评价），并配有跨句连接思想的话语标记词。输出还包含一份使用指南，帮助教师避开将句框变成“填空练习单”的常见陷阱——后者会把思考降格为填词游戏。AI 在此尤为关键，因为有效的句框必须把该任务类型的学术思维模式编码进去（比较需要“while X..., Y...”结构；评价需要“Although..., the evidence suggests...”），同时校准到特定熟练度水平——太复杂则学生用不了，太简单则教不会学术语言。

## 实证基础

Gibbons（2015）证明，当句框编码了任务的**思维结构**而不仅仅是语法结构时，它们是对 EAL 学生最有效的脚手架之一。像“The evidence suggests that ___ because ___”这样的句框同时教授了学术限定语的语言和循证论证的推理模式。Zwiers（2014）总结了核心学术语言功能——描述、解释、比较、说服、评价、假设——并表明每种功能都需要特定的语法结构与词汇，必须显性教授。Zwiers & Crawford（2011）强调，学术语言不仅用于写作，也用于口语话语，用于口语的句框（负责任对话句框 accountable talk frames）与写作句框同样重要。Kinsella（2005）表明，使用句框进行结构化语言练习显著提高了 EAL 学生对学术词汇与复杂句式的使用率。Dutro & Moran（2003）提出了语言教学的“建筑学”方法，指出学术语言具有系统、可教的特征——“砖块”（学科特定词汇）和“砂浆”（连接思想的通用语言结构）——而大多数教学只关注砖块，却忽视了将学术语言粘合在一起的砂浆。

## 输入规范

教师必须提供：
- **任务类型（Task type）：** 所需的学术思维。*例如：“比较两首诗” / “解释科学过程” / “评估史料的可靠性” / “支持或反对某一立场” / “对可能发生的情况提出假设” / “概括文本”*
- **学科领域（Subject area）：** 学科。*例如：“英语” / “科学” / “历史” / “地理”*
- **学生水平（Student level）：** 年级。*例如：“八年级”*

可选项（如可用则由上下文引擎注入）：
- **语言水平（Language proficiency）：** EAL 熟练度等级
- **学生画像（Student profiles）：** 母语、特定需求
- **具体内容（Specific content）：** 学生正在处理的具体主题
- **输出模式（Output mode）：** 写作或口语

## 提示词（Prompt）

```
You are an expert in academic language development and EAL pedagogy, with deep knowledge of Gibbons' (2015) approach to language scaffolding, Zwiers' (2014) academic language functions, Zwiers & Crawford's (2011) work on academic conversations, and Dutro & Moran's (2003) architectural approach to academic language instruction. You understand that sentence frames are powerful scaffolds only when they encode the THINKING STRUCTURE of the academic task, not just grammatical patterns.

Your task is to generate sentence frames for:

**Task type:** {{task_type}}
**Subject area:** {{subject_area}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Language proficiency:** {{language_proficiency}} — if not provided, generate frames at three levels: Early Acquisition (heavily scaffolded), Developing (moderately scaffolded), and Consolidating (lightly scaffolded).
**Student profiles:** {{student_profiles}} — if not provided, design for mixed EAL proficiency levels.
**Specific content:** {{specific_content}} — if provided, embed frames in this specific content. If not, use a generic academic context with notes on how to adapt.
**Output mode:** {{output_mode}} — if not provided, generate frames for both writing and speaking, noting differences in register.

Apply these evidence-based principles:

1. **Frames must encode thinking, not just grammar (Gibbons, 2015):**
   - Each frame should model the type of thinking required by the task.
   - Comparison frame: "While [X], [Y] differs because ___" — this teaches the student to identify a point of difference AND explain it.
   - Evaluation frame: "Although [claim], the evidence suggests ___ because ___" — this teaches the student to acknowledge a position AND evaluate it.
   - A frame that only provides grammatical scaffolding ("The first thing is ___, the second thing is ___") teaches sequencing but not academic thinking.

2. **Grade frames by proficiency level (Zwiers, 2014):**
   - **Early Acquisition:** Nearly complete sentences with small gaps for content words. The frame does most of the linguistic work; the student supplies the key concept. E.g., "___ is similar to ___ because both ___."
   - **Developing:** Sentence starters with more open endings. The student must construct more of the sentence. E.g., "Although some people argue that ___, the evidence suggests..."
   - **Consolidating:** Structural prompts rather than frames. The student constructs the sentence with minimal support. E.g., "Consider using: however, nevertheless, in contrast, despite..."
   - Provide frames at all three levels so the teacher can match to individual students.

3. **Include discourse markers (Dutro & Moran, 2003):**
   - Academic language requires connectives that signal relationships between ideas: addition (furthermore, moreover), contrast (however, nevertheless), cause (consequently, therefore), sequence (subsequently, finally), concession (although, despite).
   - Group discourse markers by function, matching to the task type.
   - Discourse markers are the "mortar" — they hold academic language together. Without them, students produce disconnected sentences.

4. **Distinguish writing and speaking frames (Zwiers & Crawford, 2011):**
   - Writing frames are more formal: "The evidence demonstrates that..."
   - Speaking frames are less formal but still academic: "I think the evidence shows that... because..."
   - For speaking: include accountable talk frames: "I agree with ___ because..." / "I'd like to build on what ___ said..."

5. **Avoid the fill-in-the-blank trap (Gibbons, 2015):**
   - Frames should require THOUGHT, not just slot-filling.
   - Bad frame: "___ is ___." (Can be completed without thinking: "The dog is brown.")
   - Good frame: "___ is significant because ___." (Requires evaluative reasoning to complete.)
   - The usage guide must address this: how to use frames to GENERATE thinking, not replace it.

Return your output in this exact format:

## Sentence Frames: [Task Type] in [Subject]

**For:** [Student level]
**Task type:** [Academic function]
**Output mode:** [Writing / Speaking / Both]

### Frames by Proficiency Level

**Early Acquisition (heavily scaffolded)**
[Complete sentence frames with small gaps — student supplies key content]

**Developing (moderately scaffolded)**
[Sentence starters with open endings — student constructs more of the response]

**Consolidating (lightly scaffolded)**
[Structural prompts and optional starters — student writes mostly independently]

### Discourse Markers

[Connectives and transition words grouped by function, matched to the task type]

### Usage Guide

[How to introduce frames effectively, how to avoid the fill-in-the-blank trap, and how to ensure frames generate thinking]

### Progression: From Frames to Independence

[How to move students from heavy scaffolding to independent academic language production — specific, practical steps]

**Self-check before returning output:** Verify that (a) frames encode the thinking structure of the task type, not just grammar, (b) frames are graded by proficiency level, (c) discourse markers are matched to the task type, (d) the usage guide addresses the fill-in-the-blank trap, (e) a progression from frames to independence is included, and (f) completing the frame requires genuine academic thinking, not just slot-filling.
```

## 示例输出

**情景：** *任务类型：“比较小说中的两个人物” / 学科领域：“英语文学” / 学生水平：“九年级” / 具体内容：“比较《蝇王》中的 Ralph 和 Jack” / 输出模式：“写作”*

---

## 句框：英语文学中的人物比较

**适用对象：** 九年级英语文学
**任务类型：** 比较（识别异同并解释意义）
**输出模式：** 写作（附带用于课堂讨论的口语句框）

### 按语言熟练度分级的句框

**初阶习得（重度脚手架）**

*这些句框承担了绝大部分语言结构工作，学生只需填入核心内容词与想法。*

识别相似点：
- "Both Ralph and Jack ___. For example, Ralph ___ and Jack also ___."
- "Ralph and Jack are similar because they both ___."
- "One thing Ralph and Jack have in common is ___."

识别不同点：
- "Ralph ___, but Jack ___."
- "While Ralph is ___, Jack is ___."
- "Ralph and Jack are different because Ralph ___ whereas Jack ___."

解释意义：
- "This difference is important because it shows ___."
- "Golding presents Ralph as ___ and Jack as ___ to show the reader that ___."

**发展阶段（中度脚手架）**

*这些句首提供开篇结构，学生必须自行建构句子的其余部分与推理。*

带分析的比较：
- "Although both Ralph and Jack ___, they differ significantly in ___. This suggests that Golding..."
- "On the surface, Ralph and Jack appear similar because ___. However, a closer reading reveals that..."
- "While Ralph represents ___, Jack represents ___. This contrast is central to the novel because..."
- "The most significant difference between Ralph and Jack is ___. This matters because Golding uses it to..."

嵌入证据：
- "This difference is evident when Ralph ___ (Chapter ___), whereas Jack ___ (Chapter ___)."
- "Golding highlights this contrast through [technique]: for example, Ralph is described as '___' while Jack is described as '___'."

评价性比较：
- "Of the two characters, ___ is presented more sympathetically because..."
- "Golding appears to [approve of / critique] ___ more than ___, which suggests his message about human nature is..."

**巩固阶段（轻度脚手架）**

*提供结构性提示而非完整句框，学生参照这些模式独立写作。*

可瞄准的学术比较结构：
- 让步从句 + 对比："Although [similarity], [key difference that matters]..."
- 嵌入式引文对比："[Quote about X]... contrasts sharply with [quote about Y], suggesting..."
- 评价性比较："While both characters [share trait], it is [Character] who [demonstrates something more significant] because..."

争取使用：however, in contrast, whereas, conversely, on the other hand, nevertheless, despite, although

目标：让比较导向对 Golding 写作意图的分析——不要仅仅罗列差异，要解释这些差异**意味着**什么。

### 话语标记词（Discourse Markers）

**用于比较（核心任务）：**

| 功能 | 标记词 | 示例 |
|------|--------|------|
| 相似 | similarly, likewise, in the same way, both...and, equally | "Both Ralph and Jack desire leadership. Similarly, they both..." |
| 差异 | however, in contrast, whereas, while, on the other hand, conversely, unlike | "Ralph values democracy; however, Jack increasingly..." |
| 让步 | although, despite, even though, while it is true that | "Although Jack shows courage, his leadership style..." |
| 强调 | significantly, crucially, most importantly, notably | "Most significantly, the way they respond to power reveals..." |
| 后果 | therefore, consequently, as a result, this means that | "Jack's rejection of rules therefore represents..." |

**用于分析（将比较连接到意义）：**

| 功能 | 标记词 |
|------|--------|
| 作者意图 | Golding uses this to..., this suggests that..., this reveals..., this is significant because... |
| 读者效果 | the reader is positioned to..., this creates a sense of..., the audience recognises that... |
| 主题联结 | this connects to the novel's theme of..., this reflects Golding's wider message about... |

### 使用指南

**如何引入句框：**

1. **先做示范。** 在把句框发给学生之前，用其中一个句框在黑板上写一句比较句并出声思考：“我想比较 Ralph 和 Jack 如何对待规则。我用句框 ‘While Ralph ___, Jack ___’——于是写成：‘While Ralph insists on maintaining rules and order, Jack increasingly dismisses them as unnecessary.’ 看到句框怎样帮我搭建对比结构了吗？现在我还需要加上**为什么**这很重要……”

2. **区分“句框”与“思考”。** 告诉学生：“句框给了你**词语**。但你必须提供**想法**。句框 ‘While Ralph ___, Jack ___’ 在你决定比较**什么**以及**为什么**重要之前是空的。句框是容器；你的分析才是内容。”

3. **将句框匹配给学生。** 给初阶习得学生重度脚手架句框，给发展阶段学生中度句框，给巩固阶段学生仅提供结构提示。同一个班的不同学生应使用不同层级。

**如何避开“机械填空”陷阱：**

- **糟糕用法：** 学生在句框里填上“Ralph is brave but Jack is mean”就停笔了。这是描述，不是分析。
- **优秀用法：** 学生写出“While Ralph uses his courage to protect the younger boys, Jack uses his to dominate and intimidate — suggesting that Golding sees courage as morally neutral, defined by how it's used.”这是导向分析的比较。
- **区别在于：** 追问“because” / “which suggests” / “this shows”。如果学生用简单描述填完了句框，回应：“很好的比较。现在告诉我**为什么**这个差异重要。Golding 在向我们展示什么？”

**核心规则：** 填完一个句框不应该是学生思考的**终点**——而应该是**起点**。句框帮助学生顺利下笔；真正的思考发生在他们决定如何补全它以及接下来写什么的时候。

### 进阶路线：从句框到独立表达

| 阶段 | 学生做什么 | 教师行动 |
|------|-----------|----------|
| **第 1–2 周** | 每个比较句都使用重度脚手架句框。可能只产出简单描述。 | 接纳句框使用。每次填完后追问“because...”。示范分析性补全。 |
| **第 3–4 周** | 过渡到中度脚手架句框。开始独立补充推理。 | 提供中度句框。展示学生超越句框限制的优秀范例。撤除初阶习得句框。 |
| **第 5–6 周** | 使用句首提示，但独立建构句子大部分内容。无需提示即可开始使用话语标记词。 | 仅对最复杂结构（让步从句、嵌入引文）提供句首。撤除词汇库。 |
| **第 7–8 周** | 独立撰写比较段落。可能参考话语标记词清单，但不再需要句框。 | 提供话语标记词清单作为参考，不提供句框。反馈聚焦分析质量，而非语言脚手架。 |
| **第 9 周及以后** | 独立产出分析性比较写作。 | 无脚手架。反馈聚焦内容、论证与文风——与任何学生一视同仁。 |

**核心原则：** 脚手架要**逐个撤除**，不要一下子全部抽走。如果学生已经准备好脱离句框但仍需要话语标记词清单，完全没问题——他们在不同语言特征上处于不同的独立阶段。

---

## 已知局限

1. **如果不逐步撤除，句框可能变成永久拐杖。** 总是依赖句框写作的学生可能会写出结构正确但千篇一律的八股文。进阶计划对此有所应对，但需要教师在数周内主动管理脚手架的撤除——无法在单次任务内自动完成。

2. **句框提供的是学术语言的结构，而不是内容。** 不理解人物的学生，无论句框设计得多好，都写不出有意义的比较。句框支持语言产出，而非内容理解——两者必须同时到位，任务才能成功。

3. **这些句框反映的是标准学术英语惯例，可能与学生的母语模式不同。** 有些学生的母语以不同方式组织比较、论证或评价——例如，有些语言更偏好间接评价而非直接陈述。句框教授的是英语学术惯例（这正是目标），但教师应意识到学生同时在学习一种新的修辞模式，而不仅仅是新词汇。
