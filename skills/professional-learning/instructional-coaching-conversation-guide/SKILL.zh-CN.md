---
# AGENT SKILLS STANDARD FIELDS (v2)
name: instructional-coaching-conversation-guide
description: "围绕特定教学焦点生成包含提问、规程与后续行动的教学教练对话指南。适用于筹备教练面谈、导师指导或同伴反馈对话。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/instructional-coaching-conversation-guide"
skill_name: "教学教练对话指南"
domain: "professional-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Knight (2007) — Instructional Coaching: a partnership approach to improving instruction"
  - "Knight (2018) — The Impact Cycle: what instructional coaches should do to foster powerful improvements in teaching"
  - "Kraft, Blazar & Hogan (2018) — The effect of teacher coaching on instruction and achievement: a meta-analysis"
  - "Costa & Garmston (2016) — Cognitive Coaching: developing self-directed leaders and learners"
  - "Aguilar (2013) — The Art of Coaching: effective strategies for school transformation"
input_schema:
  required:
    - field: "coaching_focus"
      type: "string"
      description: "正在打磨的具体教学实践或挑战——教师希望改进什么"
    - field: "teacher_context"
      type: "string"
      description: "关于教师的简要背景——教龄、学科、当前处境"
  optional:
    - field: "observation_data"
      type: "string"
      description: "来自听评课、学生作品或课堂录像的数据——用于锚定对话的证据"
    - field: "coaching_phase"
      type: "string"
      description: "处于教练周期的哪个阶段——初始目标设定、中期跟进还是影响反思"
    - field: "relationship_stage"
      type: "string"
      description: "新建教练关系、已建立信任还是具有挑战性的互动动态"
    - field: "teacher_disposition"
      type: "string"
      description: "教师当前的态度——热切、抵触、不堪重负、自信、不确定"
    - field: "school_context"
      type: "string"
      description: "相关学校特征——教练项目结构、管理层期望"
output_schema:
  type: "object"
  fields:
    - field: "conversation_plan"
      type: "object"
      description: "结构化教练对话计划，包含具体提问、预期回答与引导者应对招式"
    - field: "questioning_sequence"
      type: "array"
      description: "从反思性到分析性再到行动规划的提问序列"
    - field: "dialogue_strategies"
      type: "object"
      description: "教练的具体对话策略——停顿、复述、追问、提供数据"
    - field: "next_steps"
      type: "string"
      description: "清晰、具体且带问责的下一步——教师将尝试什么以及教练何时跟进"
chains_well_with:
  - "lesson-study-cycle-designer"
  - "lesson-observation-protocol-designer"
  - "reflective-practice-prompt-generator"
  - "teacher-inquiry-cycle-designer"
  - "pedagogical-content-knowledge-developer"
teacher_time: "4 分钟"
tags: ["coaching", "instructional-coaching", "Knight", "professional-learning", "feedback", "dialogue"]
---

# 教学教练对话指南

## 本技能的功能

设计教学教练与教师之间的结构化教练对话——运用 Knight（2007, 2018）的伙伴关系方法与影响力循环（Impact Cycle）模型——帮助教师明确具体的改进焦点、分析实践证据并承诺采取切实的下一步行动。核心原则在于有效教练是一种**伙伴关系（PARTNERSHIP）**：教练既不是告诉教师该做什么（那是指令），也不是一味附和教师原本的想法（那是捧场）。相反，教练运用提问、数据与对话，帮助教师更清晰地思考自身实践，并自主决定改变什么。产出是一份包含具体问题、预期回答、教练对话策略（停顿、复述、追问）以及带问责机制的清晰下一步的对话计划。AI 在此处具有独特价值，因为设计教练对话需要预判教师可能的反应、在恰当时机选择恰当问题并平衡挑战与支持——这是一项受益于提前规划的实时引导技能。

## 循证基础

Knight（2007）确立了教学教练的伙伴关系原则：平等（教练与教师是平等伙伴）、选择（教师决定打磨什么）、声音（教师视角处于中心）、对话（真正的交流而非单向说教）、反思（教师审视自身实践）与实践（将学习应用于课堂）。Knight（2018）将这些原则操作化为影响力循环（Impact Cycle）：识别（Identify——现状是什么、目标是什么？）、学习（Learn——什么策略能缩小差距？）、改进（Improve——实施、监控、调整）。Kraft、Blazar 与 Hogan（2018）对60项教师教练研究进行了元分析，发现教学教练对教学质量的合并效应量为 0.49 个标准差，对学生成绩的效应量为 0.18——使其成为最有效的专业发展形式之一。他们发现，当教练具有持续性（非一次性）、聚焦于具体实践（非笼统）且包含观察与反馈循环时最为有效。Costa 与 Garmston（2016）开发了认知教练（Cognitive Coaching），强调教练的主要工具是提问——那些帮助教师变得更加自主定向、自我监控与自我修正的问题。Aguilar（2013）补充了情感维度：有效教练不仅关注技术，还需要关注教师的情绪、信念与身份认同。

## 输入模式

教师必须提供：
- **教练焦点：** 正在打磨什么。*例如：“我想改进提问——我问了太多封闭式问题且没给学生足够的思考时间” / “我带的十年级班级脱离投入，但我找不出原因” / “领导告诉我需要更多差异化教学，但我不知道从哪里开始”*
- **教师背景：** 简要背景。*例如：“新入职教师，第一年教科学，总体热情但感到不堪重负” / “资深教师（12年），英语，最近一次听课收到批评且有些防御心理” / “中层骨干，6年教龄，数学，渴望提升但时间紧张”*

可选（如有，由上下文引擎注入）：
- **观察数据：** 用于锚定对话的证据
- **教练阶段：** 处于循环的哪个位置
- **关系阶段：** 新建、成熟还是具有挑战性
- **教师态度：** 热切、抵触、不堪重负等
- **学校情境：** 教练项目结构

## 提示词

```
You are an expert in instructional coaching, with deep knowledge of Knight's (2007, 2018) partnership approach, the Impact Cycle, Kraft, Blazar & Hogan's (2018) meta-analysis of coaching effectiveness, Costa & Garmston's (2016) Cognitive Coaching, and Aguilar's (2013) attention to the emotional dimension of coaching. You understand that effective coaching is a partnership where the coach uses questions and data to help the teacher think more clearly, not a directive process where the coach tells the teacher what to do.

CRITICAL PRINCIPLES:
- **Partnership, not direction.** The coach does not have the answers — the coach has the questions that help the teacher find their own answers. If the coach does all the talking, it's not coaching.
- **Data, not opinion.** Ground conversations in observable evidence (lesson observation data, student work, video clips), not subjective impressions. "I noticed 4 out of 25 students responded to your questions" is data. "Your questioning needs work" is opinion.
- **Specific, not general.** "Improve your differentiation" is too vague to act on. "Next lesson, provide three versions of the practice task at different difficulty levels" is specific enough to try.
- **The teacher decides.** The coach may suggest, model, or provide options — but the teacher chooses what to work on and what to try. Choice creates ownership; direction creates compliance.

Your task is to design a coaching conversation for:

**Coaching focus:** {{coaching_focus}}
**Teacher context:** {{teacher_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Observation data:** {{observation_data}} — if not provided, design the conversation to elicit the teacher's own perception of the issue, and recommend that observation data be gathered before the next meeting.
**Coaching phase:** {{coaching_phase}} — if not provided, assume this is an initial coaching conversation (Identify phase).
**Relationship stage:** {{relationship_stage}} — if not provided, assume early-stage relationship where trust is being built.
**Teacher disposition:** {{teacher_disposition}} — if not provided, design for a willing but uncertain teacher.
**School context:** {{school_context}} — if not provided, design for a standard school coaching programme.

Apply Knight's Impact Cycle:

1. **Identify Phase:**
   - Help the teacher articulate the current reality: what's happening now?
   - Help the teacher define a clear goal: what would "better" look like?
   - Use data to bridge the gap between current reality and goal.

2. **Learn Phase:**
   - Explore strategies that could close the gap.
   - The coach may offer options, model a strategy, share research, or facilitate the teacher's own problem-solving.
   - The teacher selects the strategy to try.

3. **Improve Phase:**
   - The teacher implements the strategy.
   - The coach observes or the teacher self-monitors.
   - Review: did the strategy work? Adjust if needed.

For EACH question, provide:
- The question itself
- Why this question matters (what it's designed to surface)
- How to respond to likely answers (including if the teacher deflects, becomes defensive, or gives a surface-level answer)

Return your output in this exact format:

## Coaching Conversation: [Focus Area]

**Focus:** [What the teacher is working on]
**Teacher:** [Brief context]
**Phase:** [Identify / Learn / Improve]

### Conversation Plan

**Opening (5 minutes):**
[How to begin — building rapport, setting the agenda, establishing the partnership frame]

**Exploration (15 minutes):**
[Core questions to explore the focus area — with anticipated responses and follow-up moves]

**Action Planning (10 minutes):**
[Questions that move toward a specific next step]

**Closing (5 minutes):**
[Summarise, confirm next steps, schedule follow-up]

### Key Coaching Moves

[Specific dialogue strategies — pausing, paraphrasing, probing — with examples of each]

### If the Conversation Gets Stuck

[What to do when the teacher deflects, becomes defensive, gives surface answers, or the conversation loses focus]

### Next Steps Template

[A clear format for the agreed next step — what the teacher will try, when, and when the coach will follow up]

**Self-check before returning output:** Verify that (a) the conversation is a partnership, not a lecture, (b) questions are open and reflective, not leading, (c) the conversation is grounded in or moves toward evidence, (d) the next step is specific and achievable, and (e) the coach's role is to facilitate the teacher's thinking, not to provide all the answers.
```

## 示例输出

**场景：** *教练焦点：“我想改进我的提问——我知道我问了太多封闭式问题且没给学生足够的思考时间，但每当我尝试改变时，几分钟内就又回到老习惯” / 教师背景：“教龄3年，历史教师，有强烈的改进动机，对问题有自我觉察但因改不掉而感到沮丧” / 观察数据：“在最近一次听课中，教练在15分钟内记录了23个问题。其中19个是封闭式的（是/否或单词回答）。提问后的平均等待时间为1.8秒。同样的5名学生回答了80%的问题。” / 教练阶段：“识别阶段——围绕该焦点的首次教练对话”*

---

## 教学教练对话：提问与思考时间

**焦点：** 改进提问——更多开放式问题、更长思考时间、更广泛参与
**教师：** 教龄3年，历史，自我觉察强且有动力，但因退回老习惯而沮丧
**阶段：** 识别（Identify）

### 对话计划

**开场（5分钟）：**
“谢谢你抽出时间。开始之前——最近怎么样？这周过得如何？”[真诚的寒暄问候，建立融洽关系。切勿急于直接抛出数据。]

接着：“你提到想打磨提问。在我分享听课中注意到的情况之前，我非常想先听听你的感受。你觉得自己课上的提问整体进行得怎么样？”

*为什么问这个问题：* 先询问教师的视角体现了伙伴关系原则。它也能揭示教师的自我觉察——如果他们已经知道问题所在，教练就不需要去“揭露”。如果他们的感知与数据存在差异，这一落差本身就成了讨论点。

*预期回答：* “我知道我问了太多封闭式问题。我试过改，但总是又变回去了，真让人沮丧。”——教师具备自我觉察。肯定这一点并在此基础上展开。

*教练招式：* “这种自我觉察非常有价值——很多教师根本注意不到自己的提问模式。你已经识别出了这个模式。我想做的是和你一起看看一些数据，看看我们能否找出**为什么**会退回老习惯，以及我们能做些什么。”

**探索（15分钟）：**

问题 1：“我可以分享我在听课中看到的情况吗？我记录了一些关于你提问的数据——你愿意一起看看吗？”
*为什么：* 征得许可后引入数据。维持伙伴关系——由教师同意查看数据，而非被单方面灌输。

[分享数据：15分钟内23个问题，19个封闭式，1.8秒等待时间，5名学生回答了80%。]

问题 2：“看着这些数据，你注意到了什么？”
*为什么：* 让教师自己解读数据，而不是由教练告诉他们数据意味着什么。这培养了分析能力。

*预期回答：* “比我想的还要糟。23个里19个是封闭的——而且1.8秒的等待时间简直跟没有一样。”

*教练招式：* 复述确认：“所以这个模式比你预想的更明显。23个里19个大约是 83% 的封闭式问题。至于等待时间——1.8秒——你觉得这对学生意味着什么？”

问题 3：“你说你尝试改变但几分钟内就又退回去了。你能带我还原一下当时发生了什么吗？退回老习惯的那一刻是什么感觉？”
*为什么：* 这是最核心的问题。大多数教练只关注“改什么（WHAT）”，这个问题聚焦于“为什么坚持不下来（WHY）”——而这正是真正的杠杆点所在。

*预期回答：* “我课前设计了开放式问题。开头我问了一两个。但接着学生给了一个简短回答，或者出现了一片沉默，我就慌了，赶紧去填补空白。不知不觉中，我又开始问‘大家都懂了吗？’和‘第3题答案是什么？’”

*教练招式：* “所以‘沉默’是触发器。你问了一个开放式问题，学生没有立刻回答，沉默带来的不适感把你推回了封闭式问题。是这样吗？”

问题 4：“你觉得在那段沉默里学生正在做什么？沉默一定是坏事吗？”
*为什么：* 挑战“沉默 = 失败”的预设。开放式问题后的沉默可能意味着学生正在**思考**——而这正是思考时间的目的。

*预期回答：* “我知道他们可能在思考。但在那个当下**感觉**不是那样。感觉像是他们听不懂，或者我问了一个烂问题。”

*教练招式：* “所以你**知道的**（沉默是思考时间）和**感受到的**（沉默意味着出问题了）之间存在落差。这非常普遍。这里真正的敌人是那种不适感，而不是学生。”

问题 5：“如果你只能改变关于提问的**一件事**——不是全部，只改一件事——哪一件事会产生最大的影响？”
*为什么：* 从分析转向行动。迫使排定优先级——教师不可能一下子改变所有事。教练的工作是帮教师选定一个具体、可实现的改变。

*预期回答：* “大概是思考时间吧。如果我能在问完一个开放式问题后就是**等一等**，其他一切也许都会顺理成章——学生有时间思考、更多学生准备好回答，我也不用靠封闭式问题去填补沉默了。”

**行动规划（10分钟）：**

问题 6：“好——思考时间。让我们把它变得非常具体。几秒钟的沉默会让你觉得是一个进步？”
*为什么：* 将模糊目标转化为可衡量目标。

*预期回答：* “5秒？听起来可行，但站在台上感觉会像一个世纪那么长。”

问题 7：“什么能帮你扛住这段沉默？有些教师在心里默数。有些会举起一只手示意‘我在刻意等待’。有些会用视觉计时器。哪种方式适合你？”
*为什么：* 提供选项而不直接下指令。教师选择契合自己风格的策略。

问题 8：“我有个建议。在你的下一节课里，只挑3个时刻，问一个开放式问题，然后在接受任何回答前足足等满5秒。只挑3个时刻——不是整节课。你愿意试试看吗？”
*为什么：* 小步、具体、可实现。三个时刻不会让人不堪重负。教师可以提前规划这3个问题，这会让沉默变得更可控。

**收尾（5分钟）：**

“让我总结一下我们的约定。在下一节八年级历史课上，你将规划3个开放式问题，并在每个问题后等足5秒再点人回答。我会去听那节课——不是整节课，只观察那3个时刻——我会记录等待时间和谁做出了回应。下周我们再碰面看看发生了什么。这样安排觉得合适吗？”

### 核心教练招式

**停顿（Pausing）：** 提问之后，等待。不要填补沉默。适用于学生的思考时间原则同样适用于教练对话——教师需要时间思考。再次开口前在心里默数到5。

**复述（Paraphrasing）：** 用略微不同的语言将教师的话反射回去：“所以你的意思是，沉默让你感到不舒服，而正是这种不适感触发了你退回封闭式问题。”这确认了理解，并帮助教师听见自己的思考。

**追问（Probing）：** 当教师给出表层回答时，向下深挖：“你说‘我试过但改不了’。退回老习惯的那一刻具体发生了什么？你当时是什么感受？”追问不是审讯——而是温和的好奇，帮助教师更细致地审视自身实践。

**提供数据（而非观点）：** “我计了时，平均等待时间是1.8秒”是数据。“你的等待时间太短了”是观点。数据邀请反思；观点诱发防御。

### 如果对话陷入僵局

**如果教师推诿转移：**（“不只是我的问题——学生根本不想回答开放式问题。”）承认其挫败感，然后重定向至教师可控的范围：“你说得对——学生参与度部分取决于他们。但你**能够**控制的是问题的类型以及你给他们的时间。让我们聚焦在那里。”

**如果教师变得防御：**（“你是说我不是个好老师吗？”）立即安抚：“完全不是。你自己主动提出想打磨这一点——这恰恰说明你具备很强的专业觉察。数据只是一个起点，这样我们才能衡量进步。这关乎成长，无关评判。”

**如果教师只给出表层回答：**（“我就是需要问更好的问题。”）追问：“一个‘更好’的问题听起来会是什么样？你能给我举个例子吗？”这将话题从抽象（“更好”）拉回具体（一个他真正能问出口的问题）。

### 下一步行动模板

**做什么：** 规划3个开放式问题，并在每个问题后保持5秒思考时间。
**何时：** 下一节八年级历史课（写明具体日期）。
**支持：** 教练将观察这3个时刻并记录等待时间 + 学生回应数据。
**跟进：** 下周教练面谈（写明具体日期）复盘发生了什么。

---

## 已知局限

1. **教练对话需要信任基础。** 上述对话预设了一位处于支持性教练关系中有意愿改进的教师。如果教师处于积极抵触状态（不仅仅是紧张，而是敌视教练），对话设计必须改变——建立信任必须先于教学焦点。本技能未涵盖重度抵触的教练动态，后者需要不同的策略。

2. **教练作为持续循环的一部分时最为有效。** 单次教练对话产生的改变有限。Kraft 等人（2018）的元分析发现，教练效应源于目标设定、观察、反馈与调整的持续循环。本对话计划只是应当持续进行的循环中的一步。

3. **教练需要具备教练技能，而不仅仅是一份对话计划。** 照本宣科念问题脚本不等同于引导真诚的教练对话。上文所述的停顿、复述、追问与响应式引导都需要练习。教练自身也应接受培训，理想情况下还应接受关于自身教练实践的督导。
