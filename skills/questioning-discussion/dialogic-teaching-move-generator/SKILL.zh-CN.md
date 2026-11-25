---
# AGENT SKILLS STANDARD FIELDS (v2)
name: dialogic-teaching-move-generator
description: "在学生给出具体的课堂回答后，生成能够延伸学生思维的跟进教学策略（teaching moves）。适用于学生说出值得深挖的内容、教师希望深化对话的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "questioning-discussion/dialogic-teaching-move-generator"
skill_name: "对话式教学策略生成器"
domain: "questioning-discussion"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Mercer (2000) — Words and Minds: how we use language to think together"
  - "Alexander (2008, 2020) — Towards Dialogic Teaching: rethinking classroom talk"
  - "Michaels et al. (2008) — Deliberative discourse idealized and realized: accountable talk in the classroom"
  - "Resnick et al. (2015) — Accountable talk: instructional dialogue that builds the mind"
  - "Cazden (2001) — Classroom Discourse: the language of teaching and learning"
input_schema:
  required:
    - field: "student_response"
      type: "string"
      description: "教师需要跟进的具体学生回答"
    - field: "learning_goal"
      type: "string"
      description: "教师希望学生理解或能够做到的目标"
    - field: "subject_context"
      type: "string"
      description: "正在讨论的学科领域与主题"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及口头表达自信度"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：语言水平、讨论自信度、文化因素"
    - field: "response_quality"
      type: "string"
      description: "教师对该回答的评估——正确、部分正确、错误、不清晰或流于表面"
    - field: "classroom_context"
      type: "string"
      description: "全班、小组或一对一；课程所处阶段"
output_schema:
  type: "object"
  fields:
    - field: "move_options"
      type: "array"
      description: "3–5 个具体的教师跟进策略，包含精确话术、策略类型标签和理论依据"
    - field: "move_selection_guidance"
      type: "string"
      description: "根据不同情境和目标选择各策略的时机建议"
    - field: "dialogue_extension"
      type: "object"
      description: "在每个策略之后如何进一步延伸对话——可能的学生回应及第二轮跟进"
    - field: "common_pitfalls"
      type: "string"
      description: "在此情境下应避免的策略及原因"
chains_well_with:
  - "socratic-questioning-sequence-generator"
  - "discussion-protocol-selector"
  - "checking-for-understanding-protocol-designer"
  - "think-aloud-script-generator"
teacher_time: "2 分钟"
tags: ["dialogic-teaching", "teacher-moves", "revoicing", "classroom-talk", "accountable-talk"]
---

# 对话式教学策略生成器（Dialogic Teaching Move Generator）

## 本技能的功能

接收课堂对话中学生的具体回答，生成高质量的教师跟进策略——即教师接下来可以说出的精确话语，用以深化思考、延伸推理、邀请其他声音或挑战假设。每个策略都标有类型标签（重述转译 revoicing、追问理由 pressing for reasoning、邀请参与 inviting participation、提出挑战 challenging、顺势建构 building on），并附有解释为何此时适合采用该策略的理由。AI 在此具有独特价值，因为专业的对话式教学要求教师在瞬间决定接下来该说什么——这种决策需要同时分析学生回答的质量、学习目标、课堂氛围以及高效话语策略库。即便经验丰富的教师也容易习惯性地只做评价（“回答得很好！”）或直接进入下一题，而未能将学生的回答转化为深化集体思维的跳板。

## 循证依据

Mercer（2000）提出了“协同思考”（interthinking）的概念——认为对话不仅是交流工具，更是共同思考的工具。他识别出三种课堂话语类型：争辩式话语（disputational，缺乏推理的反对）、累积式话语（cumulative，缺乏批判的附和）以及探究式话语（exploratory，基于证据与推理的批判性、建设性互动）。唯有探究式话语能持续带来学习增益。Alexander（2008, 2020）在此基础上构建了对话式教学框架，提出五项原则：集体性（collective，共同学习）、互惠性（reciprocal，倾听与分享）、支持性（supportive，无所畏惧地自由表达）、累积性（cumulative，在彼此贡献的基础上建构）以及目的性（purposeful，指向学习目标）。Michaels 等（2008）将对话式教学操作化为具体且可教授的“话语策略”（talk moves）——重述转译（“所以你的意思是……”）、追问理由（“是什么让你这么想？”）、邀请他人（“谁能补充她刚才说的？”）以及提出挑战（“有人不同意吗？”）。Resnick 等（2015）证明，系统性地运用这些“负责任的对话”（accountable talk）策略在阅读理解与数学推理方面带来了显著提升，对处境不利背景的学生尤为明显。Cazden（2001）指出了课堂话语的主导模式为 IRE（发起 Initiate-回应 Respond-评价 Evaluate），并证明打破这一模式——用跟进策略替代简单评价——能够彻底改变课堂思维的质量。

## 输入规范

教师必须提供：
- **学生回答：** 需要跟进的精确或转述的学生回答。*例如：“这个角色很自私，因为她没有分享食物” / “我觉得答案是 42，因为我把 6 乘以 7” / “光合作用就是植物吃阳光”*
- **学习目标：** 教师希望学生理解的内容。*例如：“学生应理解角色动机是复杂的且受情境影响” / “学生应能解释光合作用中光能与化学能之间的关系”*
- **学科情境：** 学科与主题。*例如：“9 年级英语——分析《人鼠之间》中的角色” / “7 年级科学——光合作用”*

可选（如情境引擎可用，将自动注入）：
- **学生水平：** 年龄/年级与口头表达自信度
- **学生档案：** 语言水平、讨论自信度、文化因素
- **回答质量：** 教师对该回答的评估（正确、部分正确、错误、不清晰或流于表面）
- **课堂情境：** 全班、小组或一对一

## Prompt

```
You are an expert in dialogic teaching and classroom discourse, with deep knowledge of Mercer's (2000) interthinking framework, Alexander's (2008, 2020) dialogic teaching principles, and Michaels et al.'s (2008) accountable talk moves. You understand that the teacher's response to a student's contribution is the single most important moment in classroom dialogue — it determines whether thinking deepens or dies.

Your task is to generate high-quality teacher follow-up moves for this situation:

**Student response:** {{student_response}}
**Learning goal:** {{learning_goal}}
**Subject context:** {{subject_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, generate moves appropriate for a secondary school student with moderate verbal confidence.
**Student profiles:** {{student_profiles}} — if not provided, assume a mixed class where some students are confident in discussion and others are reluctant to speak.
**Response quality:** {{response_quality}} — if not provided, analyse the student response yourself and determine whether it is correct, partially correct, incorrect, unclear, or superficial.
**Classroom context:** {{classroom_context}} — if not provided, assume whole-class dialogue.

Apply these evidence-based principles:

1. **Break the IRE pattern (Cazden, 2001):**
   - The default classroom pattern is Initiate (teacher asks) → Respond (student answers) → Evaluate (teacher says "Good" or "Not quite"). This pattern kills thinking because it tells students their job is to guess what the teacher wants, not to reason.
   - NEVER generate moves that simply evaluate ("Good answer!", "Not quite, try again"). Instead, generate moves that USE the student's response to push thinking forward.

2. **Use specific talk move types (Michaels et al., 2008):**
   - **Revoicing:** Restating the student's idea to check understanding and make it available to the class. "So you're saying that..." / "Let me see if I've got this — you think..."
   - **Pressing for reasoning:** Asking the student to explain WHY they think what they think. "What's your evidence for that?" / "What makes you say that?" / "Can you walk us through your thinking?"
   - **Inviting others:** Bringing other students into the dialogue. "Who agrees or disagrees with what Jamie said?" / "Can anyone build on that?" / "Does this connect to what Priya said earlier?"
   - **Challenging:** Introducing a counter-example, complication, or alternative perspective. "What if someone argued the opposite?" / "But what about [counter-example]?" / "How would you respond to someone who said...?"
   - **Building on:** Connecting the student's idea to the learning goal or to another concept. "That connects to something we looked at last week..." / "You've actually identified the key principle here..."

3. **Match the move to the response quality:**
   - If the response is CORRECT but SUPERFICIAL: press for reasoning or challenge to deepen.
   - If the response is PARTALLY CORRECT: revoice to clarify, then press for the missing element.
   - If the response is INCORRECT: do not evaluate negatively. Instead, revoice to make the claim visible, then challenge with a counter-example or invite others to respond.
   - If the response is UNCLEAR: revoice tentatively ("Are you saying...?") to give the student a chance to clarify.
   - If the response is EXCELLENT: build on it and invite others to engage with the idea.

4. **Promote exploratory talk (Mercer, 2000):**
   - The goal is not to get the "right answer" out of one student — it's to create a dialogue where the class thinks together.
   - Every move should aim to keep the dialogue going, not close it down.
   - Moves should model the norms of exploratory talk: giving reasons, considering alternatives, building on others' ideas.

5. **Maintain Alexander's (2008) five principles:**
   - Collective: moves should involve the whole class, not just the responding student.
   - Reciprocal: moves should position the teacher as genuinely listening, not just waiting for the right answer.
   - Supportive: moves should maintain psychological safety — a wrong answer should be treated as a valuable contribution to the dialogue.
   - Cumulative: moves should connect this response to previous contributions.
   - Purposeful: moves should steer toward the learning goal without being coercive.

Return your output in this exact format:

## Dialogic Teaching Moves: [Brief description of the situation]

**Student said:** [The student response]
**Learning goal:** [The learning goal]
**Response analysis:** [Your assessment: correct/partially correct/incorrect/unclear/superficial, with brief explanation]

### Recommended Moves

For each move (generate 4–5):
- **Move [N]: [Move type]**
  **Say:** "[The exact words the teacher could say]"
  **Why this move:** [Why this is appropriate here — what it does to the thinking in the room]
  **Likely student response:** [What the student or class is likely to say or do next]
  **Second-turn follow-up:** [What to say after the likely response]

### Move Selection Guide

[When to choose each move — e.g. "Use Move 1 if the class is quiet and you need to make the idea visible before discussing it. Use Move 3 if several students look like they want to respond."]

### Moves to Avoid Here

[1–2 specific moves that would be counterproductive in this situation, and why — e.g. "Avoid saying 'Good try' and moving on — this evaluates the response without deepening thinking and signals to the class that the answer was wrong."]

**Self-check before returning output:** Verify that (a) no move simply evaluates the response ("Good!", "Not quite"), (b) at least one move invites other students into the dialogue, (c) at least one move presses for reasoning, (d) the moves collectively steer toward the learning goal without being coercive, and (e) the exact wording sounds natural — like something a teacher would actually say in a classroom, not a textbook instruction.
```

## 示例输出

**场景：** *学生回答：“这个角色很自私，因为她没有把食物分给其他人” / 学习目标：“学生应理解《蝇王》中的角色动机是复杂的——受恐惧、生存本能以及社会规范崩塌的影响，而非单纯的性格特质” / 学科情境：“10 年级英语——分析《蝇王》第 9 章中的角色动机”*

---

## 对话式教学策略：《蝇王》中的角色动机

**学生说：** “这个角色很自私，因为她没有把食物分给其他人。”
**学习目标：** 学生应理解角色动机是复杂的——受恐惧、生存本能以及社会规范崩塌的影响，而非单纯的性格特质。
**回答分析：** 部分正确——学生识别出了相关行为（未分享食物）并做出了人物判断，但分析流于表面。“自私”是一个性格标签，而不是对动机的解释。该回答未考虑情境（生存处境、恐惧、群体动态），并将人物视为固定特质而非环境产物。这正是需要通过追问与挑战来向学习目标推进的典型回答。

### 推荐策略

**策略 1：重述转译 + 追问理由**
**话术：** “好的，所以你的意思是，不分享食物是一种自私的行为。这是一个很有意思的观点。你有什么证据说明这具体是出于‘自私’——而不是别的什么原因驱使了这种行为呢？”
**为何采用此策略：** 重述转译使该主张对全班可见，并肯定学生做出了有实质意义的贡献。追问（“而不是别的什么原因”）在不直接否定学生的前提下，为替代解释敞开了大门。它向学生传递了一个信号：教师非常重视这个想法，愿意认真加以探讨。
**可能的学生回应：** “因为她有足够的食物，但她选择不给别人分”——学生可能会用文本中的更多细节来为自己的主张辩护，但仍停留在表层。
**第二轮跟进：** “所以当时食物是够的，而她选择不分享。我想顺着‘选择’这个词再深挖一下——在小说进行到这一刻时，岛上的局势是什么样的？大家当时普遍是什么感受？”这样既没有抛弃学生的观察，又自然地把焦点引向了情境（恐惧、规范崩塌）。

**策略 2：用反例提出挑战**
**话术：** “有意思。我换一种读法给你听听：想象你就在那座岛上。你已经好几天没吃饱了。你不知道明天还会不会有食物。你也不信任周围的人。在那种情况下——不分享食物是自私，还是生存本能？这两者的界限在哪里？”
**为何采用此策略：** 这引入了学习目标所要求的情境因素（恐惧、匮乏、不信任）。它没有说学生错了——而是在不同条件下重新框定了同一个行为。“界限在哪里？”这个问题是真正开放的，邀请全班共同探讨道德复杂性。
**可能的学生回应：** 一些学生会坚持认为那仍是自私，另一些则会说是生存本能。这种分歧富有成效——它正是学习目标所指向的复杂性。
**第二轮跟进：** “看来我们有了两种解读——自私和生存本能。谁能在文本里找出一处细节，帮我们判断戈尔丁（Golding）真正想表达的是哪一种？”

**策略 3：邀请他人参与**
**话术：** “Alex 说这个角色很自私。谁有不同看法？对于那一刻，还有没有别的解读方式？”
**为何采用此策略：** 这是最简单却也最有力量的生成对话的策略。它将学生的回答定位为多种可能解读中的一种，无需教师亲自唱反调就能引发观点交锋，从而把思考分散到整个教室。
**可能的学生回应：** 另一名学生可能会提出替代观点（“我觉得她是害怕，不是自私”），或者表示赞同并补充证据。无论哪种回应都能延续对话。
**第二轮跟进：** 如果有学生提出替代观点：“那现在我们有两种解读——自私和害怕。Alex，你怎么看这个说法？‘自私’和‘害怕’之间有区别吗？”如果大家都赞同：“好，大家都觉得她自私。那我来挑战一下——如果她真心以为食物不够所有人分，你还会称之为自私吗？”

**策略 4：顺势建构 + 连接学习目标**
**话术：** “你抓住了很关键的一点——食物这一幕确实是个转折点。但我想让大家思考一下‘自私’这个词。在第二章里，同一个角色曾很乐意分享。现在她不分享了。究竟是什么变了——是她变成了另一个人，还是这座岛正在改变所有人的行为方式？”
**为何采用此策略：** 这在肯定学生观察（食物场景很重要）的基础上，把归因从性格解释转向了情境解释。“是她变了，还是岛改变了所有人？”直接扣住了学习目标——行为是由情境塑造的，而不仅仅是性格。
**可能的学生回应：** 学生可能会分成“她变了”和“岛改变了所有人”两派。两种回应都有助于推进讨论，通向学习目标所要求的复杂认知。
**第二轮跟进：** “如果说是这座岛改变了所有人的行为，那么戈尔丁想让我们对人性产生怎样的思考？自私是人天生的本性，还是环境催生的产物？”

**策略 5：追问文本证据**
**话术：** “自私是个很重的词。你能帮我指出文本里具体是哪一处——哪几行字——让你觉得是‘自私’，而不是比如‘惊恐’或‘绝望’吗？”
**为何采用此策略：** 这既追问了证据，又巧妙地引入了替代解读。它示范了文学学科的细读实践——对人物的判断必须立足于文本证据，而非笼统印象。同时也促使学生重新回到文本，而不是依赖大致感觉。
**可能的学生回应：** 学生要么能找到一段具体文本（全班可共同分析），要么意识到自己的判断基于笼统印象而非具体证据。
**第二轮跟进：** 如果他们找到了段落：“念出来吧，大家一起看看。这段话支持‘自私’的判断吗——还是我们可以做另一种解读？”如果找不到：“没关系——有时我们的第一印象确实只是种感觉。我们一起回到文本，看看戈尔丁实际写了什么。”

### 策略选择指南

- **将策略 1（重述转译 + 追问）** 作为默认首选——它最稳妥也最通用。它肯定了学生，使想法公开化，并为深度思考留出空间。适合学生比较自信、全班参与度较高的情况。
- **使用策略 2（提出挑战）** 如果班级习惯辩论且你希望加速推进至学习目标。它更直接，对自信心较弱的学生可能显得有些对抗性——请在课堂文化支持质疑挑战时使用。
- **使用策略 3（邀请他人）** 如果你看到其他学生跃跃欲试，或者当前发言的学生平时容易主导课堂。这是将师生一问一答转化为全班对话最快的方式。
- **使用策略 4（顺势建构）** 如果班级一直在表层打转，需要你把话题引回学习目标。这是引导性最强的策略——请在对话需要定向时使用，而不是在对话正顺畅推进时打断。
- **使用策略 5（追问证据）** 如果学生的主张缺乏支撑或过于模糊。这既教授了学科方法（基于证据的论证），又深化了文本分析。

### 此处应避免的策略

1. **避免说：“说得好，但其实这个角色并不自私——她是害怕。”** 这是伪装成对话的 IRE 模式。“但其实”直接否定了前面“说得好”的肯定，而且教师直接给出了标准答案，没有让全班自己推理出来。学生学到的是：他们的任务是猜测老师心里怎么想，而不是构建自己的解读。

2. **避免问：“还有谁想补充什么吗？”** 这过于笼统。它没有给其他学生提供任何具体的回应抓手，反而传递出教师正在“钓鱼”等待另一个标准答案的信号。对比策略 3 的“谁有不同看法？”——后者明确邀请分歧，并赋予学生质疑同伴解读的许可。

---

## 已知局限性

1. **输出质量完全取决于所提供学生回答的准确性。** 对学生原话进行转述或简化后输入的版本，所生成的策略会与原话输入有所不同。教师应尽量捕捉学生的真实原话——学生使用的具体词汇往往比教师的概括更能精准揭示其思维状态。

2. **对话式策略需要支持它们的课堂文化。** 如果学生不习惯被追问理由、被质疑或被要求回应同伴，这些策略可能会让他们感到受威胁或困惑。建设对话式课堂文化是一项长期工程——教师应循序渐进地引入这些策略，先从风险最低的“重述转译”开始，待学生适应后再逐步加入“追问”与“挑战”。本技能能生成策略，但无法替教师建设课堂文化。

3. **生成器无法“察言观色”。** 在真实的课堂对话中，教师选择哪种策略取决于肢体语言、语气语调、情绪状态、群体动态以及数十种无法通过文字描述捕捉的现场线索。此处提供的策略只是起点——教师必须运用专业判断来决定哪项策略契合当下时刻。同一策略在状态饱满、自信的班级里可能效果极佳，但在同一批学生疲惫或焦虑时却可能适得其反。
