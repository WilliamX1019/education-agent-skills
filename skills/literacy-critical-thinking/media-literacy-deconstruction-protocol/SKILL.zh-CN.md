---
# AGENT SKILLS STANDARD FIELDS (v2)
name: media-literacy-deconstruction-protocol
description: "设计媒体解构规程，分析媒体文本中的说服、偏见或表征。适用于教授学生批判性阅读广告、新闻或社交媒体内容时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "literacy-critical-thinking/media-literacy-deconstruction-protocol"
skill_name: "媒体素养解构规程"
domain: "literacy-critical-thinking"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Hobbs (2010) — Digital and Media Literacy: a plan of action"
  - "Buckingham (2003) — Media Education: literacy, learning and contemporary culture"
  - "Kellner & Share (2007) — Critical media literacy, democracy, and the reconstruction of education"
  - "Aufderheide (1993) — Media Literacy: a report of the national leadership conference on media literacy"
  - "Hobbs & Jensen (2009) — The past, present, and future of media literacy education"
input_schema:
  required:
    - field: "media_type"
      type: "string"
      description: "正在分析的媒体文本类型——例如广告、新闻文章、社交媒体帖、政治竞选材料、电影片段、信息图、播客"
    - field: "analysis_focus"
      type: "string"
      description: "教师希望学生注意的重点——例如说服技巧、表征、偏见、受众定位、信息省略"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "specific_text"
      type: "string"
      description: "正在分析的具体媒体文本描述"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：先前的媒体素养经验、文化背景"
    - field: "subject_area"
      type: "string"
      description: "课程学科语境——例如英语、PSHE、媒体研究、公民教育"
    - field: "learning_objectives"
      type: "string"
      description: "本次分析的具体学习目标"
output_schema:
  type: "object"
  fields:
    - field: "deconstruction_protocol"
      type: "object"
      description: "结构化分析框架，包含按分析类别组织的针对特定媒体类型的问题"
    - field: "teacher_modelling"
      type: "string"
      description: "展示教师结合具体示例示范分析的脚本"
    - field: "student_activity"
      type: "object"
      description: "学生使用该规程完成的结构化活动"
    - field: "extension_questions"
      type: "array"
      description: "面向完成基础规程学生的深层分析问题"
chains_well_with:
  - "source-credibility-evaluation-protocol"
  - "critical-thinking-task-designer"
  - "argument-structure-scaffold-generator"
  - "socratic-questioning-sequence-generator"
teacher_time: "3 分钟"
tags: ["media-literacy", "critical-thinking", "representation", "persuasion", "deconstruction"]
---

# 媒体素养解构规程

## 本技能的作用

为解构特定类型的媒体文本——广告、新闻文章、社交媒体帖、政治宣传、电影片段、信息图——生成结构化分析框架。该框架超越浅层观察（“用了什么颜色？”），教导学生分析媒体文本是如何被建构出来以定位受众、表征人物与观念并服务于特定目的的。输出包括按分析类别（生产、语言、表征、受众、省略）组织的针对特定媒体类型的解构规程、教师示范脚本以及结构化学生活动。AI 在此尤为有价值，因为媒体素养既需要通用分析原则，也需要针对特定媒体类型的知识——电视广告用来服人的技巧不同于新闻标题或社交媒体帖，有效的分析规程必须反映这些差异。

## 循证基础

Hobbs (2010) 确立了媒体素养所需的五项能力：获取（寻找与使用媒体）、分析（理解媒体信息如何被建构）、创作（生产媒体）、反思（审视自身的媒体消费）以及行动（在公民生活中负责任地使用媒体）。本技能聚焦于“分析”能力。Buckingham (2003) 提出了媒体分析的四大核心概念：生产（谁制作了它以及为什么？）、语言（使用了什么技巧？）、表征（人物、事件和观念是如何被描绘的？）以及受众（目标受众是谁、他们如何被定位？）。这些概念为媒体解构提供了分析框架。Kellner & Share (2007) 强调，批判性媒体素养必须超越技术分析，直面权力、意识形态与社会正义议题——不仅问“这是怎么做的？”，更问“这服务于谁的利益？”以及“谁的视角缺失了？”。Aufderheide (1993) 确立了所有媒体解构的基石原则：一切媒体信息都是“建构”的——它们是关于纳入什么、排除什么、强调什么和淡化什么的一系列选择的结果。Hobbs & Jensen (2009) 主张，媒体素养必须经过显性教学并搭建支架——学生不会仅仅通过日常接触媒体就自然发展出批判性分析能力。

## 输入模式

教师必须提供：
- **Media type（媒体类型）：** 媒体文本类型。*例如："Instagram advertisement" / "BBC News article" / "Political campaign poster" / "TikTok video" / "Newspaper front page" / "Documentary clip"*
- **Analysis focus（分析焦点）：** 需要关注的重点。*例如："Persuasive techniques targeting teenagers" / "How the article frames the issue as controversial" / "Representation of gender in the advertisement" / "What information is included and what is left out"*
- **Student level（学生水平）：** 年级。*例如："Year 10"*

可选（如上下文引擎可用则自动注入）：
- **Specific text（具体文本）：** 实际分析的媒体文本描述
- **Student profiles（学生档案）：** 先前媒体素养经验、文化背景
- **Subject area（学科领域）：** 课程学科
- **Learning objectives（学习目标）：** 本次分析的具体目标

## Prompt

```
You are an expert in media literacy education, with deep knowledge of Hobbs' (2010) media literacy competencies, Buckingham's (2003) four key concepts for media education (production, language, representation, audience), Kellner & Share's (2007) critical media literacy framework, and Aufderheide's (1993) principle that all media messages are constructed. You understand that effective media analysis requires both general critical thinking principles and media-type-specific knowledge of how particular media forms use specific techniques to construct meaning.

Your task is to generate a media deconstruction protocol for:

**Media type:** {{media_type}}
**Analysis focus:** {{analysis_focus}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Specific text:** {{specific_text}} — if not provided, create a plausible example of this media type for the modelling script.
**Student profiles:** {{student_profiles}} — if not provided, assume students have everyday experience consuming this type of media but have not been formally taught to analyse it critically.
**Subject area:** {{subject_area}} — if not provided, design for a general media literacy context.
**Learning objectives:** {{learning_objectives}} — if not provided, infer appropriate objectives from the media type and analysis focus.

Apply these evidence-based principles:

1. **All media messages are constructed (Aufderheide, 1993):**
   - The foundational principle: nothing in a media text is accidental. Every element — image, word, colour, angle, framing, sequence, what's included, what's excluded — is the result of a choice.
   - The protocol should train students to ask "Why was this choice made?" rather than just "What do I see?"

2. **Buckingham's (2003) four key concepts:**
   Structure the analysis around four categories:
   - **Production:** Who made this? Why? Who funded it? What are their interests?
   - **Language:** What specific techniques are used? (This is media-type-specific — an advertisement uses different techniques from a news article.) How do these techniques create meaning or emotion?
   - **Representation:** How are people, events, places, and ideas represented? What stereotypes or assumptions are present? Whose perspective is centred, and whose is marginalised or absent?
   - **Audience:** Who is the intended audience? How does the text try to position the audience (to feel, think, or do something)? How might different audiences respond differently?

3. **Add the "omission" question (Kellner & Share, 2007):**
   - What is NOT shown, said, or included? This is often the most powerful analytical question.
   - What alternative perspectives, evidence, or representations are missing?
   - Whose voice is not heard?

4. **Media-type-specific techniques:**
   - Adapt the "Language" analysis to the specific media type.
   - Advertisements: camera angles, lighting, colour, body language, music, slogans, celebrity endorsement, lifestyle association, emotional appeal
   - News articles: headline framing, source selection, quote placement, active/passive voice, image selection, story positioning
   - Social media: algorithm awareness, engagement techniques, parasocial relationships, filter effects, shareability design
   - Film/video: shot composition, editing, music, narrative structure, point of view
   - Political material: emotional appeal, us/them framing, statistics presentation, visual symbolism

5. **Model the analysis explicitly:**
   - Include a teacher modelling script that demonstrates the analytical thinking process — not just identifying techniques but explaining how they position the audience.

Return your output in this exact format:

## Media Deconstruction Protocol: [Media Type]

**For:** [Student level]
**Focus:** [Analysis focus]
**Key principle:** All media messages are constructed — every choice serves a purpose.

### The Protocol

**Category 1: Production — Who made this and why?**
[Questions specific to this media type]

**Category 2: Language — What techniques are used?**
[Media-type-specific technique analysis questions]

**Category 3: Representation — How are people and ideas portrayed?**
[Questions about representation, stereotypes, perspectives]

**Category 4: Audience — Who is this for and how does it position them?**
[Questions about target audience and audience positioning]

**Category 5: Omission — What's missing?**
[Questions about what's not shown, said, or included]

### Teacher Modelling Script

[Think-aloud script demonstrating the analysis of a specific example, working through the protocol categories]

### Student Activity

[Structured activity where students apply the protocol — format appropriate for the media type and student level]

### Extension Questions

[3–4 deeper analytical questions for students who complete the basic protocol]

**Self-check before returning output:** Verify that (a) the protocol is specific to the stated media type, not generic, (b) each category includes questions that teach critical thinking, not just observation, (c) the "omission" category is included, (d) the modelling script demonstrates analytical thinking (explaining WHY choices were made), not just identification of techniques, and (e) the student activity requires genuine analysis, not just description.
```

## 示例输出

**场景：** *Media type: "Instagram advertisement" / Analysis focus: "Persuasive techniques targeting teenagers — how the ad creates desire for the product through lifestyle association and social proof" / Student level: "Year 10" / Subject area: "English / Media Literacy"*

---

## 媒体解构规程：Instagram 广告

**适用对象：** 十年级英语 / 媒体素养
**焦点：** 针对青少年的说服技巧——生活方式联想与社会认同
**核心原则：** 所有媒体信息都是建构出来的——每一个选择都服务于特定目的。一则看起来随性又“真实”的 Instagram 广告，背后其实经过了数十次精心策划，旨在让你产生某种特定感受。

### 解构规程

**类别 1：生产（Production）——谁制作了它，为什么？**
- 品牌是谁？他们卖什么？他们希望你在看完这则广告后“做什么”？（购买、关注、转发、产生某种情绪？）
- 它是否清晰标明为广告，还是看起来像普通用户的原生内容？为什么品牌可能希望它看起来像原生内容？
- 如果有网红（influencer）出镜：他们收钱了吗？有没有 #ad 或 #sponsored 标签？（注：许多赞助帖并未清晰标注。）
- 商业模式是什么？品牌如何从你看到这则广告中赚钱？

**类别 2：语言（Language）——使用了哪些技巧？**
*视觉技巧：*
- 色彩基调是什么？暖色、冷色、低饱和还是鲜艳？营造了什么情绪？
- 场景是什么？它是否把产品与某种特定生活方式联系在一起（旅行、健身、奢华、友谊、创造力）？
- 人物是如何被拍摄的？抓拍还是摆拍？特写还是全身？直视镜头（建立联结）还是望向别处（营造向往感）？
- 画面看起来“真实”还是“精心策展”？你怎么看出来的？如果它看起来毫不费力地自然，想一想：为了做出这种“毫不费力”的效果，背后付出了多少刻意努力？

*文字与文案技巧：*
- 文案是什么语气？随性、幽默、励志还是紧迫？听起来像朋友聊天，而不像公司在推销吗？
- 文案是否包含行动号召？（"Shop now"、"Link in bio"、"Tag a friend who needs this"）
- 是否使用了社会认同（social proof）？（"Thousands of happy customers"、"As seen on..."、互动点赞数）
- 是否制造紧迫感或稀缺感？（"Limited edition"、"Only available today"、"Selling fast"）

*平台特定技巧：*
- 这则广告如何利用 Instagram 的特定功能？（Stories 竖屏形式、上滑跳转、轮播图、Reels 短视频、购物标签）
- 它是否被设计成便于分享或收藏？什么让它值得分享？
- 它如何与算法互动？（互动诱饵、评论引导、值得收藏的干货感）

**类别 3：表征（Representation）——人物与观念如何被描绘？**
- 广告中出现了谁？他们长什么样？（年龄、体型、族裔、性别、穿搭风格）
- 他们过着什么样的生活？这现实吗，还是理想化的版本？
- 产品被绑定了哪些“价值观”？（自由、美丽、自信、受欢迎、成功、叛逆、归属感）
- 是利用了刻板印象，还是挑战了刻板印象？如何实现的？
- “谁”没有出现？哪些体型、身份、生活方式或经历缺席了？

**类别 4：受众（Audience）——这是给谁看的，如何定位他们？**
- 目标受众是谁？你怎么知道的？（考虑：年龄、兴趣、生活方式、价值观、不安全感）
- 广告“希望”受众有什么感受？（受鼓舞、自惭形秽、兴奋、羡慕、被接纳、被赋权）
- 广告制造或激活了什么欲望？（想长得像那样、想过那样的生活、想加入那个群体）
- 隐含的信息是什么？"If you buy this product, you will..."（补全这句话——这就是广告底层的承诺。）
- 目标受众之外的人看到这则广告会有何不同反应？

**类别 5：省略（Omission）——缺失了什么？**
- 关于产品本身，“没有”展示什么？（价格、质量、道德生产、环境影响）
- 关于那种生活方式，“没有”展示什么？（“轻松自然”照片背后的付出、花费、特权或摆拍）
- 关于广告中的人物，“没有”展示什么？（修图、滤镜、专业打光、几十次重拍、他们与产品的真实关系）
- 关于产品的哪些替代视角缺席了？（差评、竞品、不想买或买不起的人）
- 如果是网红内容：关于品牌与网红之间的财务关系，“没有”披露什么？

### 教师示范脚本

"I'm going to show you how I analyse an Instagram ad. I'm looking at a post from a fitness clothing brand — it shows a young woman in workout clothes, stretching on a rooftop at sunrise, with a city skyline behind her. The caption says: 'Your only competition is yourself. Start your journey. 🌅 #NoBoundaries #FitnessGoals. Shop the collection — link in bio.'

Let me work through this.

**生产：** This is from a fitness clothing brand. They want me to buy their clothes. But notice — this doesn't LOOK like an ad. There's no 'BUY NOW' in big letters. It looks like something a real person posted about their morning workout. That's a deliberate choice — they want this to feel authentic, not commercial, because we trust authentic-looking content more than obvious advertising.

**语言：** Look at the visual choices. Sunrise — warm, golden light. A rooftop — elevated, aspirational. She's alone — this says 'independent, strong, self-motivated.' The city below her — she's literally above it all. None of this is accidental. Someone chose this location, this time of day, this angle, to create a feeling of calm, strength, and aspiration.

The caption is interesting: 'Your only competition is yourself.' It sounds like a motivational quote, not a sales pitch. It positions the brand as being about self-improvement, not consumerism. But it IS a sales pitch — it just doesn't want you to notice.

**表征：** The woman is young, slim, fit, and conventionally attractive. She represents an idealised version of the 'fitness lifestyle.' This is who the brand wants you to WANT TO BE. Ask yourself: how many people actually do yoga on rooftops at sunrise? This is a fantasy — but it's presented as an achievable reality, if you just buy the clothes and 'start your journey.'

**受众：** This targets young women who are interested in fitness and self-improvement. It WANTS me to feel inspired but also slightly inadequate — like I COULD be this calm, this fit, this together, if I just took that first step. And conveniently, that first step is... buying their clothes.

**省略：** What's NOT here? We don't see the photographer, the lighting rig, the twenty takes it took to get this shot. We don't see the price tag. We don't see the factory where the clothes were made. We don't see the model's actual morning (which probably started at 4am for a paid photoshoot, not a spontaneous rooftop workout). The 'real' feeling is completely manufactured — but that's the point."

### 学生活动

**第 1 步——个人分析（10 分钟）：**
每位学生选择一则 Instagram 广告（由教师提供或从自己的信息流中寻找）。按规程类别逐步分析，并记录在下表中：

| 类别 | 我注意到了什么 | 做出了什么选择，为什么 |
|----------|--------------|-------------------------------|
| 生产 | | |
| 语言（视觉） | | |
| 语言（文字） | | |
| 表征 | | |
| 受众 | | |
| 省略 | | |

**第 2 步——同伴对比（5 分钟）：**
与同伴交换广告并对比分析。聚焦问题："Did your partner notice something you missed? What did they see in the 'omission' category?"

**第 3 步——全班讨论（5 分钟）：**
"What was the most effective persuasive technique you found? Why is it effective? And — now that you can see how it works — does it still work on you? Can you be persuaded by a technique you can identify?"

### 拓展问题

1. "Find two ads for similar products (e.g., two fitness brands, two skincare brands). How do they differ in their representation and audience positioning? What does this tell you about how brands create identity through advertising?"

2. "Choose an ad that uses an influencer. Research the influencer: how much are they paid? How many similar brand deals do they have? Does knowing this change how you read their 'authentic' endorsement?"

3. "Redesign the ad from the perspective it omits. If the ad shows an idealised lifestyle, create a version showing the reality behind the image. What changes? What's lost?"

4. "Should Instagram require all ads to be clearly labelled? Should filters be disclosed? Argue your position using the analytical framework we've practised."

---

## 已知局限性

1. **媒体素养分析可能流于套路化。** 如果学生机械套用规程（"Colour: warm. Audience: teenagers. Technique: lifestyle association"）而不去追问这些选择“为什么”重要，分析就会沦为描述性练习而非批判性思考。教师应当追问“那又怎样？（So what?）”——不只是“用了什么技巧？”，而是“它们对你产生了什么影响？”。

2. **本规程主要反映了西方的媒体分析传统。** 媒体惯例、广告技巧和受众期待在不同文化间存在差异。来自不同文化背景的学生对同一媒体文本的解读可能不同——这些差异应当被视为丰富了分析，而非错误。分析非西方语境的媒体时，应对规程加以调适。

3. **批判性地分析媒体不等于全盘否定所有媒体。** 媒体素养教学的一个风险是学生变得愤世嫉俗而非具备批判性——一味怀疑一切，而不是具体评估。规程应当帮助学生区分正当说服（对其目的保持透明）与操纵（掩盖其目的），而不是教导他们所有媒体都在欺骗。
