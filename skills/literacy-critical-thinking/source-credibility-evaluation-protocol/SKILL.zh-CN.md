---
# AGENT SKILLS STANDARD FIELDS (v2)
name: source-credibility-evaluation-protocol
description: "运用横向阅读（lateral reading）与可信度核查设计数字信息源评估规程。适用于学生需要评估网站、在线信息源或社交媒体宣称时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "literacy-critical-thinking/source-credibility-evaluation-protocol"
skill_name: "信息源可信度评估规程"
domain: "literacy-critical-thinking"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Wineburg & McGrew (2017) — Lateral reading: reading less and learning more when evaluating digital information"
  - "Wineburg & McGrew (2019) — Lateral reading and the nature of expertise"
  - "Breakstone et al. (2021) — Students' civic online reasoning: a national portrait"
  - "Caulfield (2019) — SIFT: the four moves (Stop, Investigate, Find better coverage, Trace claims)"
  - "Hobbs (2010) — Digital and media literacy: a plan of action"
input_schema:
  required:
    - field: "source_type"
      type: "string"
      description: "学生正在评估的信息源类型——例如网站、新闻文章、社交媒体帖、维基百科条目、YouTube 视频、信息图"
    - field: "evaluation_context"
      type: "string"
      description: "学生评估该信息源的原因——任务或作业背景"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "specific_source"
      type: "string"
      description: "正在评估的实际信息源描述——主题、发布者、URL 类型"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：数字素养水平、先前的信息源评估经验"
    - field: "subject_area"
      type: "string"
      description: "学科语境——影响什么才算可信证据"
    - field: "common_mistakes"
      type: "array"
      description: "教师在本班观察到的信息源评估错误"
output_schema:
  type: "object"
  fields:
    - field: "evaluation_protocol"
      type: "object"
      description: "使用横向阅读评估该类型信息源的分步规程"
    - field: "teacher_modelling"
      type: "string"
      description: "展示教师结合具体示例示范该规程的脚本"
    - field: "red_flags_green_flags"
      type: "object"
      description: "针对该信息源类型的可靠与不可靠警示信号"
    - field: "student_checklist"
      type: "string"
      description: "学生可独立使用的简明核查清单"
chains_well_with:
  - "critical-thinking-task-designer"
  - "media-literacy-deconstruction-protocol"
  - "reading-comprehension-strategy-selector"
  - "socratic-questioning-sequence-generator"
  - "ai-hallucination-fact-check-protocol"
teacher_time: "3 分钟"
tags: ["source-evaluation", "lateral-reading", "SIFT", "digital-literacy", "critical-thinking"]
---

# 信息源可信度评估规程

## 本技能的作用

为评估特定类型的信息源生成结构化的横向阅读（lateral reading）规程——教导学生去核查“其他”信息源对当前信息源的评价，而不是孤立地死抠当前页面本身。这一方法直接遵循研究发现：专业事实核查员在评估信息源时之所以同时超越学生与大学教授，是因为他们采用横向阅读（立即打开新标签页核查谁在信息源背后），而非纵向阅读（停留在页面内更仔细地寻找可靠性“线索”）。输出包括分步规程、教师示范脚本、针对信息源类型的红旗/绿旗指标以及学生核查清单。AI 在此尤为有价值，因为有效的信息源评估既需要通用原则（横向阅读、主张溯源），也需要针对特定信息源类型的知识（新闻文章的可信标准不同于科学研究的标准）——没有领域专长很难将两者结合教授。

## 循证基础

Wineburg & McGrew (2017, 2019) 开展的里程碑式研究表明，专业事实核查员评估信息源的方式与学生乃至大学教授有着根本不同。事实核查员使用“横向阅读”——他们不停留在当前信息源上寻找可靠性线索，而是立即打开新标签页，查看其他信息源对该信息源的作者、发布机构和主张有何评价。相比之下，学生和教授使用“纵向阅读”——他们停留在页面内，寻找极易被伪造的表面可信度标记（专业排版、.org 域名、页面上列出的作者头衔）。横向阅读者平均仅用 93 秒就能得出正确评估；纵向阅读者耗时超过 5 分钟，且更容易出错。Breakstone 等 (2021) 发现，绝大多数美国高中生无法可靠地评估在线信息源——他们极易被专业的外观设计和页面上的头衔所欺骗。Caulfield (2019) 将研究操作化为 SIFT 方法：Stop（停下来，先别急着读）、Investigate the source（调查信息源背后是谁）、Find better coverage（寻找更好的报道：其他来源怎么说）、Trace claims（追踪主张到原始出处）。这一框架使横向阅读变得可教。Hobbs (2010) 确立了数字与媒体素养需要结构化教学——学生不会仅仅通过上网就自然发展出信息源评估技能。

## 输入模式

教师必须提供：
- **Source type（信息源类型）：** 哪种信息源。*例如："Website" / "News article" / "Social media post (Instagram infographic)" / "YouTube video" / "Wikipedia article" / "Scientific study abstract"*
- **Evaluation context（评估背景）：** 学生为什么要评估它。*例如："Students are researching climate change for a Geography essay and need to find reliable sources" / "A student shared a TikTok video claiming X and I want the class to evaluate it"*
- **Student level（学生水平）：** 年级。*例如："Year 9"*

可选（如上下文引擎可用则自动注入）：
- **Specific source（具体信息源）：** 正在评估的实际信息源描述
- **Student profiles（学生档案）：** 数字素养水平、先前经验
- **Subject area（学科领域）：** 学科语境
- **Common mistakes（常见错误）：** 教师观察到的信息源评估错误

## Prompt

```
You are an expert in digital literacy and source evaluation pedagogy, with deep knowledge of Wineburg & McGrew's (2017, 2019) research on lateral reading, Caulfield's (2019) SIFT method, and Breakstone et al.'s (2021) findings on students' civic online reasoning. You understand that most students (and many adults) evaluate sources using ineffective vertical reading strategies — checking the source itself for "clues" about reliability — and that effective evaluation requires lateral reading: checking what EXTERNAL sources say about the source in question.

Your task is to generate a source evaluation protocol for:

**Source type:** {{source_type}}
**Evaluation context:** {{evaluation_context}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Specific source:** {{specific_source}} — if not provided, create a plausible example source of this type for the modelling script.
**Student profiles:** {{student_profiles}} — if not provided, assume students have limited formal training in source evaluation and tend to judge credibility by appearance (professional design = trustworthy).
**Subject area:** {{subject_area}} — if not provided, infer from the evaluation context.
**Common mistakes:** {{common_mistakes}} — if not provided, include the most common source evaluation errors for this age group: trusting professional-looking design, confusing .org with automatic credibility, accepting information because it confirms what they already believe.

Apply these evidence-based principles:

1. **Lateral reading over vertical reading (Wineburg & McGrew, 2017, 2019):**
   - The protocol must teach students to LEAVE the source and check external references — not to scrutinise the source itself for credibility cues.
   - Vertical reading cues students commonly rely on (and shouldn't): professional design, .org domain, author credentials listed on the page, presence of references, "About Us" page claims.
   - Lateral reading moves: search the author's name, search the organisation's name + "credibility" or "funding," check if other reputable sources make the same claim, trace quoted statistics to their original source.

2. **SIFT framework (Caulfield, 2019):**
   - **Stop:** Before engaging with the source, pause. Don't start reading, sharing, or citing until you've evaluated it.
   - **Investigate the source:** Who is behind this? What do OTHER sources say about this author/organisation? (Not what the author/organisation says about themselves.)
   - **Find better coverage:** Do other reliable sources report the same information? If only one source makes this claim, be cautious.
   - **Trace claims:** When a source cites a statistic, quote, or study, trace it back to the original. Does the original say what the source claims it says?

3. **Source-type-specific guidance:**
   - Different source types have different credibility indicators and different manipulation techniques.
   - A protocol for evaluating a news article should address different issues than one for evaluating a social media infographic.
   - Adapt the SIFT steps to the specific source type.

4. **Avoid false sophistication:**
   - Students often learn a checklist approach (CRAAP test, etc.) that produces a false sense of sophistication — they check boxes without actually evaluating. The protocol should teach THINKING, not box-ticking.
   - The most important question is always: "What do INDEPENDENT, KNOWLEDGEABLE sources say about this?" — not "Does this source LOOK reliable?"

5. **Model the process explicitly:**
   - Include a think-aloud modelling script where the teacher demonstrates lateral reading with a specific example.
   - Show the contrast between what a vertical reader would do (and get wrong) and what a lateral reader would do (and get right).

Return your output in this exact format:

## Source Evaluation Protocol: [Source Type]

**For:** [Student level]
**Context:** [Why students are evaluating this source]
**Method:** Lateral reading (SIFT framework)

### The Protocol

[Step-by-step protocol adapted for this source type — each step should explain WHAT to do, WHY it matters, and WHAT TO LOOK FOR]

### Teacher Modelling Script

[A think-aloud script showing the teacher evaluating a specific example of this source type, demonstrating lateral reading. Show the contrast with what a vertical reader might do wrong.]

### Red Flags and Green Flags

**Red flags (reasons to be cautious):**
[Source-type-specific indicators of unreliability]

**Green flags (reasons to be more confident):**
[Source-type-specific indicators of reliability]

**Important: green flags are not proof.** [Brief note that even reliable-looking sources can be wrong — green flags increase confidence but don't guarantee accuracy]

### Student Checklist

[A concise, printable checklist students can use independently when evaluating sources of this type]

**Self-check before returning output:** Verify that (a) the protocol prioritises lateral reading over vertical reading, (b) each step teaches thinking, not box-ticking, (c) the modelling script demonstrates the actual process of checking external sources, (d) red and green flags are specific to this source type, (e) the protocol is age-appropriate, and (f) the student checklist is concise enough to be practically usable.
```

## 示例输出

**场景：** *Source type: "Website" / Evaluation context: "Year 9 students are researching the health effects of energy drinks for a Science project. Several students have found websites claiming energy drinks are safe or even beneficial, and the teacher wants to teach them how to evaluate these sources before including them in their projects." / Student level: "Year 9"*

---

## 信息源评估规程：网站

**适用对象：** 九年级科学
**背景：** 在调研能量饮料对健康影响的项目期间评估所查找到的网站
**方法：** 横向阅读（SIFT 框架）

### 评估规程

**第 1 步：STOP（停下来）——先别急着读（30 秒）**

在读文章一个字之前，先停下来。你是通过搜索引擎找到这个网站的——但出现在搜索结果中“并不”意味着信息源可靠。Google 按流行度与搜索词相关性排序网页，而不是按准确性。

*怎么做：* 记下网址（URL）和网站/机构名称。此时“不要”开始读正文。

*为何重要：* 一旦开始读，你的大脑就会开始吸收并接受信息。吸收完主张之后再去批判性评估会困难得多。先评估，再阅读。

**第 2 步：INVESTIGATE THE SOURCE（调查信息源）——网站背后是谁？（2–3 分钟）**

这是最关键的一步。“不要”去看网站自己的“关于我们（About Us）”页面——任何机构都可以给自己写满赞美之词。相反，请“打开一个新标签页”从外部搜索。

*怎么做：*
1. 搜索："[机构名称]" —— 阅读维基百科条目（如有）和前 3–4 条结果。他们是谁？独立来源对他们作何评价？
2. 搜索："[机构名称] funding" 或 "[机构名称] backed by" —— 谁资助这个机构？如果一个谈论能量饮料安全性的网站是由能量饮料公司资助的，这就是关键信息。
3. 搜索："[作者姓名] credentials" —— 此人是该领域受过训练的专家吗？医生写医学文章不同于普通博主写医学文章。

*关注什么：*
- 该机构是独立的，还是在该议题上有经济利益？
- 作者是相关领域的合格专家吗？
- 独立来源将该机构描述为可信的，还是有偏见/有争议的？

**第 3 步：FIND BETTER COVERAGE（寻找更好的报道）——其他可靠来源也这么说吗？（2–3 分钟）**

如果该网站提出具体宣称（"Energy drinks have no negative health effects on teenagers"），核查权威独立来源是否认同。

*怎么做：*
1. 搜索具体宣称："energy drinks health effects teenagers"
2. 寻找没有经济利益牵涉的机构来源：NHS（英国国家医疗服务体系）、WHO（世界卫生组织）、大学研究摘要、同行评审期刊
3. 对比：该网站的宣称是否与这些独立来源一致？

*关注什么：*
- 如果只有这一个网站提出该宣称，而没有任何权威来源附议，务必高度警惕。
- 如果权威来源的说法恰好相反，那么无论该网站外观多么专业，其宣称很可能不可靠。
- 如果多个独立来源证实了该宣称，你的信心可以提升。

**第 4 步：TRACE CLAIMS（追踪主张）——统计数字从哪里来？（2–3 分钟）**

如果网站引用了数字、研究或专家引语，将其追踪回原始出处。

*怎么做：*
1. 找出一项带数字的具体宣称："A study found that 95% of energy drink consumers experience no side effects."
2. 搜索原始研究。它真的存在吗？它真的说了网站宣称的内容吗？
3. 核查：谁开展了这项研究？谁资助的？发表在权威期刊上吗？

*关注什么：*
- 含糊引用（"studies show"、"research proves"）却无具体出处——这是红旗警示。
- 无法追踪到原始出处的统计数据——又一个红旗警示。
- 研究确实存在但结论与网站所说不同——该网站正在歪曲证据。

### 教师示范脚本

"I'm going to show you how I'd evaluate a website I found while searching for information on energy drinks. I've found a website called 'EnergyDrinkFacts.org' — it looks professional, has a clean design, and has an article titled 'The Truth About Energy Drinks and Teen Health.' Let me show you what most people do — and then what I do differently.

**大多数人怎么做（纵向阅读——这是错误做法）：**
Most people would start reading the article. They'd see the .org domain and think 'this must be legitimate.' They'd see that the article cites some studies and think 'this is evidence-based.' They'd see the professional design and think 'this looks trustworthy.' They might check the About Us page and read 'We are an independent research organisation dedicated to providing factual information about energy beverages.' Sounds good, right? This is vertical reading — staying on the website and looking for clues. And it's exactly how misinformation works. ANYONE can register a .org domain. ANYONE can make a professional-looking website. ANYONE can write a nice About Us page.

**我怎么做（横向阅读——这是正确做法）：**
I'm going to LEAVE this website immediately and open a new tab.

[打开新标签页] I search: 'EnergyDrinkFacts.org' — and I find... interesting. The Wikipedia article says this organisation was founded and funded by the American Beverage Association — the trade body that represents energy drink manufacturers. So the 'independent research organisation' is actually funded by the companies that sell energy drinks. That's not automatically disqualifying, but it's ESSENTIAL context that I would never have found by reading the website itself.

Now I search: 'energy drinks health effects teenagers NHS' — and the NHS page says caffeine in energy drinks can cause anxiety, sleep disruption, and heart palpitations in teenagers, and advises against regular consumption. The WHO says the same. So the claim on EnergyDrinkFacts.org that energy drinks are safe for teens CONTRADICTS what the NHS and WHO say.

Now I trace a specific claim. The website says 'A 2018 study found no significant health risks from moderate energy drink consumption.' I search for this study... and I find it was funded by Red Bull and published in a journal with a low impact factor. The larger, independent studies published in mainstream medical journals found the opposite.

My conclusion: this website LOOKS professional and credible, but lateral reading reveals it's industry-funded and its claims contradict the independent evidence. I would NOT use this as a source in my project.

That whole process took me about 3 minutes. And I barely read the article itself — because the article isn't where the truth is. The truth is in what INDEPENDENT sources say."

### 红旗警示与绿旗指标

**红旗警示（需要保持警惕的理由）：**
- 网站在该议题上存在经济利益（例如食品公司的营养网站、化石燃料公司的气候变化网站）
- “关于我们”页面用含糊正面的语言自我吹嘘，却不点名具体人员、资助方或机构隶属关系
- 网站笼统声称“研究表明”，却不给出链接或具体名称
- 没有其他权威、独立来源做出相同宣称
- 网址刻意营造权威感但实为私人机构（.org 并不等于非营利或可信——任何人都可以注册 .org）
- 网站攻击主流科学或主流机构（"What the NHS doesn't want you to know..."）

**绿旗指标（更有信心的理由）：**
- 网站由公认机构发布（大学、政府卫生部门、具备编辑规范的成熟新闻机构）
- 独立来源证实了相同信息
- 具体宣称可追踪到具名、经过同行评审的研究
- 网站承认不确定性与复杂性，而非发表绝对化论断
- 作者资质可从外部独立核实
- 内容与通过横向阅读查到的信息一致

**重要提示：绿旗指标不是绝对证明。** 即使是成熟机构也可能发表错误，看起来可靠的信息源在具体宣称上也可能出错。绿旗提升信心，但不能保证绝对准确。始终要对照其他来源核查具体宣称。

### 学生核查清单

**SIFT 核查——在为项目评估任何网站时使用**

| 步骤 | 行动 | ✓ |
|------|--------|---|
| **STOP（停）** | 我尚未开始读正文。我会先做评估。 | |
| **INVESTIGATE（查）** | 我在新标签页搜索了机构名称，知道网站背后是谁。 | |
| **INVESTIGATE（查）** | 我搜索了 "[机构] funding" 或 "backed by"，知道是谁资助他们。 | |
| **INVESTIGATE（查）** | 该机构在该议题上 有 / 没有 经济利益。 | |
| **FIND（找）** | 我在新标签页搜索了主要宣称。其他权威来源 同意 / 不同意 / 找不到任何其他来源做出此宣称。 | |
| **TRACE（溯）** | 我找出了一个具体统计数据或宣称并追踪到原始出处。原始出处 支持 / 不支持 网站所说的内容。 | |
| **我的判断** | 基于横向阅读，我对该信息源的评级为：可靠 / 谨慎使用 / 不予采用 | |
| **我的理由** | 我得出这一判断是因为：_________________________________ | |

---

## 已知局限性

1. **横向阅读需要互联网接入与时间。** SIFT 流程每份信息源耗时 3–5 分钟，这对于研究项目来说是可行的，但对于学生在网上遇到的每一条信息并不现实。本技能教授的是最适合学术研究任务的深度评估流程——学生在日常数字生活中还需要更快速的启发法（例如“转发前先查出处”），这不在本规程覆盖范围内。

2. **本规程教授的是单个信息源的评估，而非跨信息源的综合。** 能够评估单个网站的学生，在综合多个来源、权衡相互冲突的证据或认识到连可信来源也可能意见相左时，仍可能遇到困难。信息源评估是研究能力的必要条件，但非充分条件。

3. **某些类型的信息源比其他类型更难横向评估。** 网站与新闻文章相对容易核查——机构与作者都可以被搜索到。社交媒体帖、匿名论坛发言以及没有署名就被病毒式传播的内容则更难追踪。本规程对具有可识别作者与发布者的信息源最为有效。
