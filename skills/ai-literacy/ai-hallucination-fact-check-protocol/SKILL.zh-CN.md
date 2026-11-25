---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ai-hallucination-fact-check-protocol
description: "设计针对 AI 生成文本的事实核查协议，在 SIFT 框架基础上扩展 AI 特有的幻觉检测步骤。适用于学生需要核实 AI 主张与引文时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-literacy/ai-hallucination-fact-check-protocol"
skill_name: "AI 幻觉事实核查协议"
domain: "ai-literacy"
version: "1.0"
contributor: "Gareth Manning"
evidence_strength: "moderate"
evidence_sources:
  - "Wineburg & McGrew (2017) — Lateral reading: reading less and learning more when evaluating digital information"
  - "Wineburg & McGrew (2019) — Lateral reading and the nature of expertise"
  - "Caulfield (2019) — SIFT: the four moves (Stop, Investigate, Find better coverage, Trace claims)"
  - "Breakstone et al. (2021) — Students' civic online reasoning: a national portrait"
  - "Ji et al. (2023) — Survey of hallucination in natural language generation"
input_schema:
  required:
    - field: "ai_output_context"
      type: "string"
      description: "学生正在进行事实核查的 AI 生成内容类型——例如‘ChatGPT 对法国大革命的解释（附带具名历史学家）’、‘包含青少年心理健康统计数据的 AI 研究摘要’"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及数字素养水平"
  optional:
    - field: "subject_area"
      type: "string"
      description: "学科领域——影响最常见的幻觉类型以及核查主张的方式"
    - field: "hallucination_risk"
      type: "string"
      description: "该情境下最可能出现的具体幻觉类型——捏造引文、编造统计数据、事件张冠李戴、虚假共识主张"
    - field: "verification_resources"
      type: "string"
      description: "学生可用的核查工具——图书馆数据库、Google Scholar、特定可信网站"
    - field: "ai_tool"
      type: "string"
      description: "学生正在核查哪款 AI 工具的输出"
output_schema:
  type: "object"
  fields:
    - field: "hallucination_taxonomy"
      type: "object"
      description: "该学科/情境下最可能出现的 AI 幻觉类型，附带每种类型的外观示例"
    - field: "ai_sift_protocol"
      type: "object"
      description: "针对 LLM 输出改造的 AI 版 SIFT 协议——将‘调查来源（Investigate the source）’替换为‘重构来源（Reconstruct the source）’"
    - field: "verification_moves"
      type: "array"
      description: "核查各类 AI 主张的分步动作——统计数据、引文、具名研究、事件主张、专家引语"
    - field: "hallucination_hunt_activity"
      type: "object"
      description: "结构化课堂活动（捉虫行动），包含操作说明、核查步骤与讨论协议"
    - field: "teacher_modelling_script"
      type: "string"
      description: "出声思考示范脚本，演示如何辨别真实引文与 AI 捏造引文"
chains_well_with:
  - "source-credibility-evaluation-protocol"
  - "ai-output-critical-audit-designer"
  - "media-literacy-deconstruction-protocol"
teacher_time: "4 分钟"
tags: ["AI-literacy", "hallucination", "fact-checking", "SIFT", "lateral-reading", "AI-citations", "verification"]
---

# AI 幻觉事实核查协议

## 本技能的作用

生成专门适配 AI 生成文本的事实核查协议——在 SIFT 框架（Caulfield, 2019）的基础上扩展 AI 特有的核查动作，以应对大语言模型（LLM）幻觉这一独特挑战。标准的横向阅读（lateral reading）假设信息来源拥有一个可以调查其资助背景与公信力的机构作者。这一假设在 AI 生成文本面前失效了：没有作者可查，没有机构资金可核，也没有“关于我们”页面可供审视。留存下来的是“追踪主张（Trace claims）”这一步——而这一步需要针对 AI 进行专门校准。AI 幻觉有多种形态：捏造引文（具名研究根本不存在，或从未发表）、编造统计数据（看似精确的数字却无任何可验证出处）、真实引文张冠李戴（真实论文被安在错误作者或期刊名下），以及虚假共识主张（“大多数科学家同意”但实际上并无此类共识）。每一种都需要不同的核查动作。输出包括针对该学科领域的幻觉类型分类法、AI 适配版 SIFT 协议、针对各类主张的具体核查动作、“猎捕幻觉（Hallucination Hunt）”课堂活动，以及展示真实引文与捏造引文查找差异的教师示范脚本。

## 实证基础

Wineburg & McGrew（2017, 2019）通过实证研究确立：专业事实核查员在信息源评估上优于学生和教授，因为他们采用横向阅读——立即打开新标签页查看外部来源对该信息源的评价——而非纵向阅读（仅分析信息源页面本身的可信度线索）。这项研究正是 SIFT 框架的基石。然而，横向阅读是为具有可调查机构身份的信息源设计的。当“信息源”是 LLM 时，SIFT 的“调查（Investigate）”步骤需要改造：没有机构身份、没有资金链、没有编辑委员会。横向阅读中真正适用的是“追踪主张”这一步——核实被引用的证据是否存在，以及它是否真的说了 AI 所声称的内容。Caulfield（2019）对 SIFT 的操作化界定提供了此处扩展的结构框架。Breakstone 等人（2021）发现，学生普遍缺乏评估网络信息源的能力，过度依赖表面可信度标记——而流畅且听起来权威的 AI 输出会急剧放大这一脆弱性。Ji 等人（2023）对自然语言生成中的幻觉进行了系统综述，记录了 LLM 中幻觉的普遍性与类型：内在幻觉（与源材料矛盾）、外在幻觉（添加无法验证或捏造的信息）以及事实不一致。他们的分类法直接支撑了本协议中的幻觉类别。

## 输入规范

教师必须提供：
- **AI 输出情境（AI output context）：** 正在核查的 AI 内容类型。*例如：“ChatGPT 对近期心理学研究的总结，附带具名研究引文” / “AI 对一战起因的解释，列举了具体历史学家及其论点” / “聊天机器人关于营养学的回答，包含青少年饮食模式的统计数据”*
- **学生水平（Student level）：** 年级与数字素养水平。*例如：“十一年级，熟悉 Google 搜索但未接受过正式的信息源评估训练” / “九年级，具备基础网络素养”*

可选项（如可用则由上下文引擎注入）：
- **学科领域（Subject area）：** 学科情境——不同学科的幻觉模式各异
- **幻觉风险（Hallucination risk）：** 该情境下最可能出现的幻觉类型
- **核查资源（Verification resources）：** 学生可以使用的工具
- **AI 工具（AI tool）：** 生成该输出的 AI 系统

## 提示词（Prompt）

```
You are an expert in digital literacy and AI verification pedagogy, with deep knowledge of Wineburg & McGrew's (2017, 2019) lateral reading research, Caulfield's (2019) SIFT framework, Breakstone et al.'s (2021) work on students' online reasoning, and Ji et al.'s (2023) taxonomy of hallucination types in natural language generation. You understand the critical limitation of standard lateral reading when applied to AI-generated content: SIFT's "Investigate the source" step assumes an institutional author whose funding and credibility can be checked externally. LLMs have no institutional author. The adaptation required is to replace "Investigate the source" with "Reconstruct the source" — verifying that cited sources exist and say what the AI claims, and that un-cited statistics have traceable origins.

CRITICAL PRINCIPLES FOR AI FACT-CHECKING:
- **AI hallucinations are qualitatively different from human misinformation.** A biased human source has a motive you can investigate. AI fabricates because of statistical patterns in training data — it produces plausible-sounding text. There is no motive to find; there is a verification deficit to expose.
- **The most dangerous hallucinations are the ones that look most real.** A citation to a non-existent study is dangerous precisely because it includes a real-sounding author name, a real-sounding journal title, and a plausible-sounding year. Students who have learned "check the source" may feel they have verified the citation when they have not.
- **Verification requires SOURCE RECONSTRUCTION, not source investigation.** The fact-checker's move with AI is: (1) Does this source exist? (2) Does it say what the AI claims? This is different from asking "Is this source credible?" — it is asking "Does this source exist at all?"
- **Not all hallucinations are dramatic.** The most common AI hallucinations are subtle: a real study presented with the wrong year, a real statistic from a different context, a real author attributed with a paper they didn't write. Students need protocols for subtle errors, not just obvious fabrications.
- **Absence of citation is not hallucination.** AI often omits citations entirely. This is an accuracy problem (Ennis standard) but not hallucination. The specific concern is when AI PROVIDES citations or statistics — that is when verification moves are needed.

Your task is to generate an AI hallucination fact-check protocol for:

**AI output context:** {{ai_output_context}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the context and adapt hallucination types accordingly.
**Hallucination risk:** {{hallucination_risk}} — if not provided, identify the 2-3 most likely hallucination types for this subject and output type.
**Verification resources:** {{verification_resources}} — if not provided, design for Google + Google Scholar + Wikipedia as the baseline verification toolkit.
**AI tool:** {{ai_tool}} — if not provided, assume a general-purpose LLM chatbot.

Return your output in this exact format:

## AI Hallucination Fact-Check Protocol: [Context]

**For:** [Student level]
**Output type:** [Type of AI content]
**Highest-risk hallucination types:** [The 2-3 most likely for this context]

### Hallucination Taxonomy

[For each relevant hallucination type:]

**[Type name]**
- **What it looks like:** [Specific example appropriate to this context]
- **Why it's dangerous:** [Why students are likely to miss it]
- **How to verify:** [The specific verification move]

### AI-Adapted SIFT Protocol

**S — Stop**
[Pause-and-check instruction adapted for AI context]

**I — Identify the claim type**
[For AI, "Investigate the source" becomes "Identify what kind of claim this is." Guide students to classify claims before attempting verification — statistics need one move, citations need another, expert quotes need another.]

**F — Find the original**
[Source reconstruction: find whether cited sources exist, then find whether they say what the AI claims]

**T — Trace unattributed claims**
[What to do with statistics and claims that have no citation — lateral reading for the underlying data]

### Verification Moves

[For each claim type — statistics, citations, named studies, expert quotes, event claims — provide:]

**Verifying [claim type]:**
- **Step 1:** [What to search/check first]
- **Step 2:** [How to confirm existence vs. content]
- **Red flags:** [Signs that the claim may be hallucinated]
- **Example:** [A specific walkthrough]

### Hallucination Hunt Activity

**Setup:** [How to prepare the activity — what AI output to use, what students receive]

**Round 1 — Identify verification targets (X minutes):** [Instructions]

**Round 2 — Verify (X minutes):** [Instructions with specific verification steps]

**Round 3 — Report and discuss (X minutes):** [Class debrief protocol]

**Discussion questions:** [Questions that draw out the pedagogical insight — what did finding/not finding a hallucination teach about AI reliability?]

### Teacher Modelling Script

[Think-aloud script — 200-300 words — demonstrating the difference between finding a real citation and finding a fabricated one, walking through the verification moves explicitly]

**Self-check before returning output:** Verify that (a) the hallucination taxonomy is specific to this subject and output type, (b) the SIFT adaptation explicitly replaces "Investigate the source" with something workable for AI, (c) verification moves are specific enough to follow, (d) the activity creates genuine discovery moments rather than just confirming what students already suspect, and (e) the modelling script shows both a successful verification AND a hallucination discovery.
```

## 示例输出

**情景：** *AI 输出情境：“十一年级心理学学生使用 ChatGPT 获取关于社交媒体与青少年心理健康研究的摘要。AI 生成了一段 200 词的回复，其中写道：‘根据 Twenge 等人 2021 年发表在《JAMA Psychiatry》上的研究，每天使用社交媒体超过 3 小时使青少年患抑郁症的风险增加 47%。’” / 学生水平：“十一年级，具备基础网络素养，未接受过正式信息源评估训练” / 学科领域：“心理学” / 核查资源：“Google、Google Scholar、学校图书馆数据库”*

---

## AI 幻觉事实核查协议：心理学研究引文

**适用对象：** 十一年级，具备基础网络素养
**输出类型：** 附带具名引文的 AI 生成研究摘要
**最高风险幻觉类型：** 引文捏造（真实作者、错误研究）、统计数据编造（看似合理的数字、无真实出处）、去语境误用（真实研究、错误人群或语境）

### 幻觉分类法

**引文捏造：真实作者，错误研究**
- **外观示例：** “Twenge 等人（2021）发表于《JAMA Psychiatry》”——Jean Twenge 确实是研究社交媒体与心理健康的真实学者，《JAMA Psychiatry》也是真实期刊。但这篇特定的 2021 年研究真的存在吗？AI 利用真实人名和真实期刊拼凑出一条听起来天衣无缝、却可能从未存在过的引文。
- **为何危险：** 学生搜索“Twenge social media mental health”会搜到一大堆真实的 Twenge 论文——于是可能误以为引文已核实，其实他们只核实了作者存在，而非这篇特定研究存在。
- **核查方法：** 在 Google Scholar 中搜索“Twenge JAMA Psychiatry 2021”——检查是否出现符合该描述的论文。随后阅读摘要，核实它是否真的说了 AI 所声称的内容。

**统计数据编造**
- **外观示例：** “使抑郁症风险增加 47%”——一个具体、看似精确的数字。真实的心理学研究通常报告效应量、相关系数和置信区间，而不是像“47%”这样干净利落的百分比。
- **为何危险：** 具体感会被误读为精确性。像 50% 这样的整数或许会引起怀疑；47% 听起来却像是从真实统计分析中跑出来的。
- **核查方法：** 找到原始研究。它里面报告了“47%”这个数字吗？如果论文报告的是比值比（odds ratio）或相关系数，AI 可能错误地进行了换算——或者干脆凭空编造。

**去语境误用**
- **外观示例：** 一项真实研究的发现被报道成适用于全体青少年，而原研究实际上只调查了特定人群（例如仅限 10–14 岁美国女孩，或已存在心理健康问题的临床样本）。
- **为何危险：** 引文确实存在——研究是真的——但 AI 陈述的主张超出了证据支持的范围。
- **核查方法：** 找到论文后，阅读方法（Methods）部分：样本是谁？AI 的主张是否与研究的实际适用范围相符？

### AI 适配版 SIFT 协议

**S — Stop（停下来）**
在复制或引用 AI 回复中的任何内容之前，先停下来。AI 生成的研究摘要经常包含听起来像真的一样、但未经核实的引文。论文或项目中出现哪怕一条未经核实的 AI 引文都会成为硬伤。继续前先停下来核查。

**I — Identify the claim type（识别主张类型）**
面对 AI 文本，“调查来源”行不通——AI 就是来源，它本身没什么可调查的。相反，对文本中的每一条具体主张进行分类：
- **具名引文：** “根据 Smith（2022）……” → 需要存在性核查 + 内容核查
- **统计主张：** “X% 的……” → 需要来源重构
- **专家归因：** “【机构】的研究人员发现……” → 需要机构 + 研究核查
- **共识主张：** “大多数心理学家同意……” → 需要多方佐证核查

**F — Find the original（查找原始出处）**
针对每条具名引文：（1）在 Google Scholar 中搜索 作者 + 期刊 + 年份。（2）如果论文出现，点开并检查：它真的说了 AI 声称的内容吗？（3）如果论文**没有**出现，该引文很可能是捏造的。

针对无引文的统计数据：给具体短语加上引号搜索（"47% depression risk" social media teenagers）。如果没有结果能追溯到同行评审来源，该统计数据便无法验证——很可能是幻觉。

**T — Trace unattributed claims（追踪无归因主张）**
当 AI 说“研究表明”或“研究发现”却不点名具体出处时：搜索来自独立、具名来源的佐证。如果你找到一篇引用率很高的系统综述得出了相反结论，AI 的共识主张可能就是过度概括。

### 核查动作

**核查具名引文（例如“Twenge et al., 2021, JAMA Psychiatry”）：**
- **第 1 步：** 打开 Google Scholar。搜索：Twenge 2021 JAMA Psychiatry social media。查看前五条结果。
- **第 2 步：** 如果出现匹配论文：点进摘要。它是否报告了 AI 提出的特定主张（抑郁风险增加 47%）？
- **危险信号：** Scholar 中搜不到该论文。论文存在但研究的是不同人群（成年人、临床样本）。论文存在但报告的是不同统计指标（比值比而非百分比）。
- **演练示例：** 搜索 → 出现论文 → 摘要显示其研究的是美国青少年 2013–2018 年数据，报告的是相关系数而非百分比 → 具体的“47% 抑郁风险”数字并未出现 → AI 要么编造了，要么曲解了这一统计数据。

**核查具体统计数据：**
- **第 1 步：** 用英文双引号精确搜索短语："47% depression risk" social media teenagers。
- **第 2 步：** 如果出现结果，检查：它是同行评审期刊，还是转述某项未具名研究的新闻报道？
- **危险信号：** 只有社交媒体帖子或新闻文章引用了这个数字，找不到原始研究。找到的原始研究报告的是完全不同的指标。

### 猎捕幻觉（Hallucination Hunt）活动

**准备：** 教师准备 3–4 段围绕课堂主题的简短 AI 生成研究摘要，每段混合包含真实引文、微调篡改的引文和完全捏造的引文。学生领取纸质版摘要。

**第一轮——标出核查目标（5 分钟）：** 学生阅读每段摘要，在所有具名引文、具体统计数据和共识主张下划线。两人一组，按类型对标出的要素进行分类。

**第二轮——核查（15 分钟）：** 每组使用 Google Scholar 和学校图书馆数据库核查 2–3 条主张。对每条主张记录：该来源是否存在？（是/否）它是否说了 AI 声称的内容？（是/否/被修改）。记下具体证据。

**第三轮——汇报与讨论（10 分钟）：** 各组汇报发现。教师揭晓哪些引文是真实的、哪些被篡改、哪些是捏造的。全班讨论：是什么让捏造的引文看起来那么可信？破绽在哪里？

**讨论问题：**
- “如果你不经核查就把这条引文放进论文里，会发生什么？”
- “AI 放进了一位真实作者（Twenge）。这让这条引文比完全编造一个假名字更可信还是更危险？为什么？”
- “核查这三条主张花了多长时间？这些时间花得值吗？”

### 教师示范脚本

“看我如何处理这条 AI 引文。它写着：‘根据 Twenge 等人 2021 年在《JAMA Psychiatry》发表的研究，每天使用社交媒体超过 3 小时使抑郁风险增加 47%。’听起来很让人信服，对吧？真实学者、真实期刊、精确百分比。让我向你们展示真正的事实核查是什么样的。

我打开 Google Scholar。搜索：Twenge 2021 JAMA Psychiatry。我得到好几条结果——能看出 Twenge 确实在相关领域发过很多论文。但我需要**这一篇**特定论文：2021 年，《JAMA Psychiatry》。我扫视结果……我看到一篇 2022 年发在《JAMA Pediatrics》的论文，一篇 2018 年发在《Emotion》的论文，但没有任何一篇精确匹配 2021 年《JAMA Psychiatry》。这就是一个危险信号。

让我试一个更宽泛的搜索：Twenge JAMA Psychiatry。现在我在找 Twenge 在该期刊发表过的任何论文。我看到一条 2020 年的结果——点开它。它是关于屏幕时间与幸福感的，用了不同方法。关键在于：它报告的是相关系数 r=0.05，而不是‘抑郁风险增加 47%’。统计语言完全不同。

我的结论：这条引文要么不存在，要么被严重曲解了。我**并没有**证明该主张本身一定是假的——也许还有另一篇我没搜到的 Twenge 2021 年论文。但在我核实它确实存在并且真的说了我需要引用的内容之前，我绝对不能在论文中使用这条引文。AI 给了我一个看起来像引文的东西，但它根本起不到引文的作用。”

---

## 已知局限

1. **核查需要时间与数据库权限。** 完整的核查协议——找到研究、查看摘要、核实主张——每条引文需要 3–5 分钟。在撰写论文的情境下，学生可以核查一两条关键主张，但无法核查 AI 的每一句话。本技能旨在培养核查习惯，而非要求穷尽式事实核查。

2. **有些幻觉确实极难察觉。** 一篇由真实作者撰写、发表在真实期刊上的真实论文，摘要总结基本正确，只是年份略旧或样本人群不同——这需要阅读方法部分，而不仅仅是确认论文存在。学术阅读能力有限的学生可能无法独立达到这一核查深度。

3. **LLM 幻觉率因模型和主题而异。** Ji 等人（2023）记录了多个模型的幻觉情况；发生率因任务类型与学科领域而异。在训练语料充分的领域（近期高关注度科学、主流政治史）幻觉较少，而在冷门主题、前沿研究和细分专业领域则更为常见。教师应据此校准预期。

4. **横向阅读在 AI 领域的具体应用缺乏直接实证检验。** 横向阅读 / SIFT 的实证基础（Wineburg & McGrew, 2017, 2019; Caulfield, 2019）在一般信息源评估方面十分坚实。本协议中针对 AI 的改造是该实证基础的原则性延伸，而非经过独立验证的干预措施。“来源重构”动作在逻辑上成立，但尚未在教育研究中接受正式测试。
