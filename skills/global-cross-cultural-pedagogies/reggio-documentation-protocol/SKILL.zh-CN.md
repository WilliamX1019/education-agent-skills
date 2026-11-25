---
# AGENT SKILLS STANDARD FIELDS (v2)
name: reggio-documentation-protocol
description: "设计教学记录（pedagogical documentation）规程，使儿童的学习过程可见且可分享。适用于记录学习历程、与家庭沟通或规划下一步教学时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/reggio-documentation-protocol"
skill_name: "瑞吉欧教学记录规程"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Rinaldi (2006) — In Dialogue with Reggio Emilia: listening, researching and learning"
  - "Malaguzzi (1993) — For an education based on relationships"
  - "Krechevsky, Mardell, Rivard & Wilson (2013) — Visible Learners: promoting Reggio-inspired approaches in all schools"
  - "Edwards, Gandini & Forman (2012) — The Hundred Languages of Children: the Reggio Emilia experience in transformation (3rd edition)"
  - "Giudici, Rinaldi & Krechevsky (2001) — Making Learning Visible: children as individual and group learners"
input_schema:
  required:
    - field: "learning_experience"
      type: "string"
      description: "需要记录的学习活动、项目或调查——儿童正在做什么和探索什么"
    - field: "documentation_purpose"
      type: "string"
      description: "创建记录的目的——使学习可见、为下一步教学提供依据、与家庭沟通、专业反思"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄组——学前、小学或调适应用于中学"
    - field: "documentation_format"
      type: "string"
      description: "记录将如何呈现——墙面展板、学习日志、电子档案袋、班级画册"
    - field: "subject_area"
      type: "string"
      description: "如适用，所属课程领域"
    - field: "team_context"
      type: "string"
      description: "教师是独立记录还是作为团队成员协作记录"
    - field: "available_tools"
      type: "string"
      description: "可用的记录工具——相机、摄像机、录音笔、iPad、纸笔"
output_schema:
  type: "object"
  fields:
    - field: "documentation_protocol"
      type: "object"
      description: "完整规程——观察什么、如何记录、如何解读、如何分享"
    - field: "observation_focus"
      type: "object"
      description: "观察和倾听的重点——儿童思维、理论建构和意义建构的具体方面"
    - field: "recording_strategies"
      type: "array"
      description: "如何采集证据——照片、对话转录、视频、儿童作品样本"
    - field: "interpretation_framework"
      type: "object"
      description: "如何解读所记录的内容——证据揭示了儿童思维与学习的哪些方面"
    - field: "sharing_plan"
      type: "object"
      description: "如何分享记录——与儿童分享（重温并延展学习）、与家庭分享、与同事分享"
chains_well_with:
  - "emergent-project-design-scaffold"
  - "awe-wonder-experience-designer"
  - "reflective-practice-prompt-generator"
  - "lesson-observation-protocol-designer"
teacher_time: "3 分钟"
tags: ["Reggio-Emilia", "documentation", "Rinaldi", "Malaguzzi", "visible-learning-processes", "early-years", "primary", "observation"]
---

# 瑞吉欧教学记录规程

## 本技能的作用

遵循瑞吉欧·艾米利亚（Reggio Emilia）取向设计一份教学记录规程——这是一套系统性地观察、记录、解读并分享儿童“学习过程”而非仅仅“最终作品”的实践。在瑞吉欧传统中，记录（documentation）不是评估、不是墙面美化展示，也不是行政留档——它是一种研究工具。作为研究者的教师观察儿童的思维、捕捉他们的理论与问题，并利用这些证据理解儿童“正在试图理解什么”，进而规划下一步提供什么支持。来自 Rinaldi 的核心原则是：记录让学习“可见”——不是作为静止的结果，而是作为充满生命力的探究、假设、修正与理解深化的过程。输出包括观察重点规程、记录方法（照片、儿童对话转录、作品样本）、证据解读框架（它揭示了儿童思维的什么？），以及分享计划（与儿童分享以重温学习、与家庭分享以建立联结、与同事分享以开展专业对话）。AI 在此尤为有价值，因为设计有效的记录规程需要将瑞吉欧的哲学原则（将儿童视为有能力的个体、一百种语言、作为研究的学习）转化为教师在繁忙课堂中切实可行的观察策略。

## 循证基础

Rinaldi (2006) 将记录阐述为“可见的倾听（visible listening）”——即细心关注儿童的话语、行动与表征，并通过系统记录与展示使这种倾听变得可见。瑞吉欧取向中的记录发挥四大功能：使儿童的学习过程对儿童自己可见（支持重温与深化）、对教师可见（指引教学决策）、对家庭可见（传达儿童学了什么以及如何学习），以及对学校共同体可见（积累集体专业知识）。Malaguzzi (1993) 描述了儿童的“一百种语言”——儿童通过绘画、雕塑、律动、戏剧游戏、建构、写作与交谈表达理解的多种方式。记录必须关注所有这些语言，而不仅仅是口头或书面表达。Krechevsky 等 (2013) 将瑞吉欧记录原则从幼儿阶段延伸至小学和中学语境，证明在任何年龄段，“让学习可见”都能提升学生的元认知、教师的响应力以及学校文化。Edwards, Gandini & Forman (2012) 全面记录了瑞吉欧·艾米利亚取向，强调记录与课程密不可分——教师记录什么，塑造了他们注意到什么，进而塑造了他们下一步规划什么。Giudici, Rinaldi & Krechevsky (2001) 展示了记录展板（结合照片、儿童原话、教师解读与儿童作品的墙面展示）如何作为“集体记忆”发挥作用——使儿童与教师能够重温、反思并延展他们的调查。

## 输入模式

教师必须提供：
- **Learning experience（学习体验）：** 儿童正在做什么。*例如："Reception children are investigating shadows — they've noticed that shadows change during the day and are full of questions about why" / "Year 2 students are building structures from recycled materials — exploring balance, strength, and design" / "Year 5 students are conducting a science investigation into plant growth — but their conversations reveal they're also developing theories about what plants 'need' and 'want'"*
- **Documentation purpose（记录目的）：** 为什么要记录。*例如："I want to capture the children's evolving theories about shadows so I can plan the next provocation" / "I need to share children's learning with families at the end of the project" / "I want to use the documentation in a team meeting to discuss what the children are understanding"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年龄组
- **Documentation format（记录格式）：** 墙面展板、日志、电子档案
- **Subject area（学科领域）：** 课程领域
- **Team context（团队背景）：** 个人记录还是团队记录
- **Available tools（可用工具）：** 相机、摄像等

## Prompt

```
You are an expert in Reggio Emilia documentation practices, with deep knowledge of Rinaldi's (2006) concept of documentation as visible listening, Malaguzzi's (1993) hundred languages of children, Krechevsky et al.'s (2013) adaptation for all ages, Edwards, Gandini & Forman's (2012) comprehensive account of the Reggio approach, and Giudici, Rinaldi & Krechevsky's (2001) documentation as group memory. You understand that Reggio documentation is NOT display (making the classroom look pretty), NOT assessment (measuring children against benchmarks), and NOT record-keeping (filing evidence for accountability). It is RESEARCH — the teacher systematically observes and records to understand children's thinking, theories, and meaning-making, and uses this understanding to plan responsive, emergent curriculum.

CRITICAL PRINCIPLES:
- **Document PROCESSES, not just products.** A photograph of a finished painting is display. A sequence of photographs showing a child mixing colours, pausing, trying again, mixing differently — accompanied by a transcription of what the child said while working — is documentation. The process reveals the THINKING; the product alone does not.
- **Listen before you interpret.** Rinaldi's "visible listening" means attending to what children actually say and do, not what the teacher expects or hopes they will say and do. Transcribe children's exact words. Photograph their actual actions. The evidence comes first; interpretation follows.
- **Children's theories are the focus.** Children are theory-builders — they observe the world and construct explanations. Documentation should capture their theories: "I think shadows happen because the sun is tired" is a theory about light. It's scientifically inaccurate but cognitively rich — it reveals that the child understands there is a causal relationship between the sun and shadows. The teacher's job is to capture this theory, not correct it, and then plan provocations that help the child refine it.
- **Documentation is a tool for planning.** The purpose of documentation is not to create a beautiful wall display (though it may result in one). The primary purpose is to help the teacher understand what children are CURRENTLY thinking so they can plan what to offer NEXT. Documentation feeds forward into curriculum.
- **Share with children for revisiting.** When documentation is shared with children ("Look at what you said last week about shadows..."), it enables them to revisit their thinking, notice how it has changed, and deepen their understanding. Documentation creates group memory that sustains long-term investigation.

Your task is to design a documentation protocol for:

**Learning experience:** {{learning_experience}}
**Documentation purpose:** {{documentation_purpose}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for early years or primary.
**Documentation format:** {{documentation_format}} — if not provided, design for a flexible format that could be a wall panel or digital portfolio.
**Subject area:** {{subject_area}} — if not provided, follow the learning experience wherever it leads.
**Team context:** {{team_context}} — if not provided, design for a solo practitioner with suggestions for team use.
**Available tools:** {{available_tools}} — if not provided, design for camera and notebook (minimum tools).

Return your output in this exact format:

## Documentation Protocol: [Learning Experience]

**Experience:** [What children are investigating]
**Purpose:** [Why this documentation is being created]
**Guiding question:** [What the teacher is trying to understand about children's learning through this documentation]

### What to Observe

[Specific aspects of children's learning to watch and listen for — their theories, questions, strategies, interactions, representations]

### How to Record

**Photographs:** [What to photograph and why — not "take nice pictures" but specific moments that reveal thinking]
**Transcription:** [What to write down — exact children's words, dialogue between children, key moments]
**Children's work:** [What to collect — drawings, constructions, writing — and how to annotate them]
**Teacher notes:** [What the teacher records about their own observations, questions, and hypotheses]

### How to Interpret

[A framework for making sense of the documentation — what the evidence reveals about children's thinking, where their understanding is developing, what they're ready for next]

### How to Share

**With children:** [How to use the documentation to help children revisit and extend their learning]
**With families:** [How to share in a way that communicates the depth of children's thinking]
**With colleagues:** [How to use the documentation for professional dialogue]

### Planning Forward

[How the documentation informs what the teacher offers next — provocations, materials, questions, experiences]

**Self-check before returning output:** Verify that (a) the protocol focuses on processes and thinking, not just products, (b) children's exact words are captured, (c) the interpretation framework honours children's theories, (d) the documentation feeds forward into planning, and (e) sharing includes revisiting with children, not just displaying for adults.
```

## 示例输出

**场景：** *Learning experience: "Reception children (ages 4–5) are investigating shadows. It started when a child noticed that their shadow was 'following' them in the playground. Several children are now fascinated — they've been drawing shadows, measuring them, and having conversations about where shadows come from. One child said 'the shadow is inside you and it comes out when the sun finds it.' Another said 'shadows are afraid of the dark so they only come out in the light.' The class wants to understand: why do we have shadows?" / Documentation purpose: "I want to capture the children's evolving theories about shadows so I can (a) understand what they currently think, (b) plan provocations that help them refine their theories, and (c) create a documentation panel for the classroom and a summary for families." / Available tools: "iPad for photos and video, notebook, children's drawings, large paper for group work"*

---

## 教学记录规程：影子调查——学前班（Reception）

**体验：** 学前班儿童调查影子——影子从哪里来、为什么会变化、是什么造就了影子
**目的：** 捕捉儿童不断演变的理论，以理解他们当前的思维、规划下一步激发物，并与家庭分享学习历程
**引导问题：** "What theories are the children constructing about HOW shadows work, and how are these theories changing as they encounter new evidence?"

### 观察重点

**儿童的理论（最核心的关注点）：**
倾听因果解释——任何时候儿童说出 "because"、"I think" 或 "maybe it's because"，这就是理论。请“逐字准确”写下来。已捕捉到的示例：
- "The shadow is inside you and it comes out when the sun finds it" —— 认为影子是人身体的一部分，被太阳激活后跑出来
- "Shadows are afraid of the dark so they only come out in the light" —— 将影子拟人化，并识别出影子出现的条件（光）

这两个理论在科学上都不完整，但在认知上却很精巧——它们都识别出光是必要条件，并提出了一种机制。观察随着儿童接触新证据，这些理论如何演变。

**儿童的实验：**
留意儿童“检验”自己理论的时刻——刻意站在光下与阴凉处、用物体挡住光、试图“抓住”自己的影子。即使儿童不称之为实验，这些也是实验。记录他们做了什么以及得出了什么结论。

**儿童之间的对话：**
当儿童彼此讨论影子时，他们的思维最为可见。倾听分歧（"No, that's not why!"）、延展（"And ALSO, the shadow is flat because..."）以及修正（"Actually, I changed my idea..."）。尽可能逐字记录这些交流。

**多元表征：**
观察儿童如何表征自己的理解——画影子、涂鸦、身体动作（模仿影子）、建构（试图造出一个影子）。Malaguzzi 的“一百种语言”原则：儿童用多种形式表达理解。一幅影子的画作可能揭示出儿童尚无法用语言表达的理解。

### 记录方式

**照片（iPad）：**
- 拍摄儿童正在“调查中”的动作——蹲下来审视影子、把物体举向光线、在纸上描摹影子。构图应同时展现儿童的动作“以及”他们正在看的对象，而不仅仅是拍脸。
- 将影子本身与儿童的反应一起拍下来——他们的手指指向、惊讶的表情、试图操控影子的尝试。
- 拍摄序列照：同一个孩子连续多天进行调查。周一、周三、周五的三张照片展示其参与度的演变，比单张照片揭示得多得多。
- 拍摄儿童的画作，并“附带”记录儿童的口头解释。单独看画可能有歧义；儿童的话语赋予了它意义。

**文字转录（随身笔记本）：**
- 在户外游戏和调查时间随身携带笔记本。写下儿童的原话——而非概括总结。"The shadow is inside you and it comes out when the sun finds it" 是有效记录；"The child talked about shadows and the sun" 则是错失良机。
- 记录语境：孩子说这句话时正在做什么？是什么引发了这句话？在和谁说话？
- 记录儿童之间的对话："A said... B replied... A then said..." 这种往来揭示了思维如何通过社会互动发展。
- 现场使用速记，并在 24 小时内趁记忆尚未淡忘整理扩充。

**儿童作品：**
- 收集带有批注的影子画作。问孩子："Tell me about your drawing." 把他们的解释写在背面或贴在画上的便利贴上。画作加上解释才共同构成完整记录。
- 如果儿童描摹了影子（在固定于地面的纸上），保留描摹稿并拍下描摹过程。
- 如果儿童制作了与影子相关的立体建构，从多个角度拍照并记录儿童的解释。

**教师笔记：**
- 每次调查活动后，写一段简短反思笔记（2–3 句话）："What theories did I hear today? What surprised me? What do I think the children are ready to explore next?"
- 记录你自己的疑问："I'm not sure whether Aisha understands that the shadow is created by the object BLOCKING the light, or whether she still thinks the shadow is part of the object. How can I find out?"

### 解读方法

**跨时间追踪理论发展：**
按时间顺序摊开记录。从第 1 周到现在的儿童原话通读一遍。他们的理论如何变化了？有没有孩子从“影子在你身体里”转向“当你挡住光时就会出现影子”？有没有孩子的画作发生变化——从把影子画成一个独立小人，变成把影子与物体和光源连接起来？

**识别理解的“边缘”：**
儿童“差一点”就理解什么了？如果他们知道光有关，但尚未识别出“遮挡光线”这一机制，他们就正处于理解的边缘。下一个激发物应当创造一个让“遮挡机制”清晰可见的情境（例如在暗室里用手电筒照射物体制造影子——光束、物体、影子三者同时可见）。

**尊重理论，而非否定：**
"The shadow is inside you and it comes out when the sun finds it" 不是“错的”——它是“发展中的”。它准确地识别出：(a) 人与影子之间存在联系，(b) 太阳是影子出现的必要条件，(c) 存在某种机制（“找到它”）。孩子需要的是帮助他们精炼机制的体验——从“太阳找到它”走向“太阳光被你的身体挡住了”。

**兼顾个体路径与群体知识：**
有些孩子可能走得比其他孩子更远。既要记录个体历程，也要记录群体的集体理解。当儿童彼此分享理论时，即使单个儿童处于不同阶段，群体的整体理解也会向前推进。

### 分享方式

**与儿童分享（重温——最重要的用途）：**
打印 4–5 张关键照片，张贴在儿童视线高度，下方用大号清晰字体写上他们自己的原话。在集体时间重温："Last week, Aisha said 'the shadow is inside you and it comes out when the sun finds it.' Do you still think that? Has anyone noticed anything new?"

这种重温发挥双重作用：帮助儿童记住并在早期思考的基础上继续建构，并营造一种“理论受到珍视且理应随时间演变”的文化。

**与家庭分享（沟通）：**
为班级通讯或数字平台制作一页“学习故事（Learning Story）”：
- 3–4 张展示调查过程的照片
- 2–3 句儿童原话引用（署真实姓名需经家长许可）
- 一段简短的教师点评："The children are investigating shadows. They are developing sophisticated theories about what causes shadows and how they work. We are supporting their investigation by providing opportunities to experiment with light and shadow both outdoors and in our 'shadow studio.' Here are some of their current theories..."
- 给家庭的延伸提示："You could extend this learning at home by exploring shadows together — notice how shadows change at different times of day!"

**与同事分享（专业对话）：**
将记录带到教研团队会议上。先不附加你自己的解读，直接分享儿童的理论。问同事："What do you think the children are understanding? What would you offer next?" 这将记录用作集体专业学习的工具——而不仅仅是个人反思。

### 向前规划

基于记录，教师规划“下一个”激发物（不是下一份传统教案——而是帮助儿童以新方式相遇该现象的下一次体验）：

**如果儿童识别出光很必要但尚未识别出遮挡：** 开辟一处暗化区域并配备手电筒。儿童可以实验："Can you make a shadow? What do you need? What happens if you move the torch? What happens if you move the object?"

**如果儿童将影子拟人化（"the shadow is afraid"）：** 这是一个值得探索而非直接纠正的理论。提问："Can you make your shadow do something? Can you make it dance? Can you make it disappear? What makes it disappear?" 发现自己可以通过控制光线让影子出现和消失的儿童，正在建立“是他们控制影子，而不是影子控制他们”的理解。

**如果儿童把影子画成与物体分离的东西：** 提供镜子、描图纸和强光源。发起挑战："Can you draw your shadow while it's there? Can you trace it?" 描摹的动作揭示了影子与物体和光线相连——它不是一个独立实体。

---

## 已知局限性

1. **瑞吉欧记录需要许多教师并不具备的时间。** 转录儿童话语、筛选并批注照片、制作记录展板以及利用记录规划教学都需要时间。在教师本就负荷沉重的学校里，在现有工作之上叠加记录可能不切实际。上述规程已尽量设计得易于操作（笔记本与 iPad、简短反思笔记），但即便如此仍需要受保护的专用时间。

2. **瑞吉欧取向是为幼儿与小学教育开发的。** 尽管 Krechevsky 等 (2013) 证明它可以调适应用于高年级学生，这里描述的记录实践最自然地契合幼儿与小学阶段——在那里儿童的学习更外显且较少受分科课表限制。调适应用于中学语境需要重新思考“儿童的理论”在分科学习中呈现为何种面貌。

3. **记录是一种教学法立场，而不仅仅是一种技术。** 本规程提供了实用指引，但瑞吉欧记录要求教师从根本上相信儿童是有能力、胜任的理论建构者。如果一位教师一边记录儿童的话语，私下却将其视为“可爱的错误”而一笑置之，那就完全错失了精髓。记录的力量取决于它对待儿童思维的尊重程度。
