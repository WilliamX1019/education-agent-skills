# Education Agent Skills Library

[![Skills](https://img.shields.io/badge/skills-165-blue)](https://github.com/GarethManning/education-agent-skills)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Last Commit](https://img.shields.io/github/last-commit/GarethManning/education-agent-skills)](https://github.com/GarethManning/education-agent-skills/commits/main)

一个独立开源的教育技能库，包含**跨 20 个领域的 165 个教育技能**：为 AI 代理提供实用指令，辅助备课规划、评价设计、课程设计与学习支持。它将具名研究与清晰标注的实践者原创框架融入可复用的工作流，并内置局限性说明与教育者专业判断空间。第 1–19 领域服务于教师与课程设计者；第 20 领域包含 **13 个面向学生的技能**，用于实时学习互动。

本库采用 [Agent Skills](https://agentskills.io/home) 开放格式——该格式最初由 Anthropic 开发，现已在开放生态中广泛采用。每个技能都是一个文件夹，内含带名称和描述的 `SKILL.md`、指令文本以及可选的支持资源。现有的 Claude/插件和 MCP 集成使用富格式源文件；另有一个生成的便携版本可通过官方格式校验器检查。具体检查范围见[标准与验证](#agent-skills-格式与验证)，教育内容审阅方法见[技能质量](docs/SKILL_QUALITY.md)。格式兼容性并不代表对教学有效性的认证。

**2026 年 10 月 22 日 — v3.1.0：** 本库现已提供经官方 Agent Skills 参考工具校验的便携版本、37 项针对性教育内容修订，以及 8 份重组了可选示例的指南。技能 ID 与接口保持稳定。[阅读本次更新及其局限性](docs/releases/v3.1.0.md)。

由本库运营的公共 MCP 服务已随本次发布退役；不再提供公开注册。请使用下方的[便携版下载](https://github.com/GarethManning/education-agent-skills/releases/download/v3.1.0/education-agent-skills-portable-v3.1.0.zip)、源码插件、手动提示词或本地/自托管 MCP。现有仅使用远程服务的客户端需要改用受支持的本地路径或自行运营的端点；迁移不会自动完成。

---

## 快速开始

从 [v3.1.0 GitHub 发布页](https://github.com/GarethManning/education-agent-skills/releases/tag/v3.1.0)开始，为 Claude、Codex 或 Hermes 选择一种本地集成方式，或者将便携版本复制到其他兼容客户端中。不同客户端版本及激活行为存在差异；[验证回执](docs/audits/agent-skills-build-verification-2026-10-22.md)记录了已测试的边界。

本地技能文件无需依赖本库运营的在线服务。MCP 用户可以[通过 stdio 在本地运行，或自行运营托管端点](mcp-server/README.md)。

### Claude

**CoWork** — 用于插件导入的仓库 URL 为：

```
https://github.com/GarethManning/education-agent-skills
```

**Claude Code** — 对于 2.1.275 及以上版本，请使用经 2.1.307 校验器推荐的命令：

```text
/plugin install education-agent-skills --marketplace GarethManning/education-agent-skills
```

Claude 2.1.307 通过了本地清单校验（带有提示性警告）；安装与会话激活尚未测试。对于不支持此语法的旧版客户端，请使用下方的手动复制提示词方式，或遵循该客户端的本地插件说明；本项检查未验证通过仓库 URL 的 CLI 安装方式。

**Claude Desktop（本地 MCP）** — 请按照[本地 stdio 配置](mcp-server/README.md#run-locally-stdio)进行设置。对于仅接受远程 MCP 的客户端，请参考[自托管指南](mcp-server/README.md#self-hosted-http)运营你自己的已认证端点。原公共连接器与注册服务已不再受支持；其凭据不会自动迁移到你的自托管端点。

### OpenAI Codex

Codex **不需要**托管 MCP 服务器。推荐的本地配置方式：

```bash
git clone https://github.com/GarethManning/education-agent-skills.git
cd education-agent-skills
codex plugin marketplace add "$PWD"
codex plugin add education-agent-skills@education-agent-skills
codex plugin list --marketplace education-agent-skills --json
```

清单文件列出了全部 20 个领域目录。注册与安装是两个独立步骤。Codex CLI 0.163.0-alpha.11.1 在隔离环境中通过了 165 个源技能及其资源的注册、安装和列表检查；实际模型激活与桌面端刷新尚未测试。安装后请开启新会话；刷新与缓存更新方式请参见完整指南。

若只需一两个独立技能，可将其复制到你的全局 Codex 技能目录：

```bash
mkdir -p ~/.codex/skills
cp -r skills/<domain>/<skill-name> ~/.codex/skills/
```

示例：

```bash
cp -r skills/memory-learning-science/spaced-practice-scheduler ~/.codex/skills/
```

完整 Codex 指南：[docs/CODEX.md](docs/CODEX.md)。

### Hermes Agent

Hermes 用户应保留本仓库作为规范源，然后仅在本地安装实际需要的技能。

```bash
hermes skills tap add GarethManning/education-agent-skills
hermes skills install \
  GarethManning/education-agent-skills/skills/original-frameworks/learning-target-authoring-guide \
  --category education --yes
```

推荐起步方式：选择性安装所需技能或小型入门包，而不是一次性安装全部 165 个技能。这样能让你的本地 Hermes 索引保持精简实用，避免冗余干扰。

Hermes v0.18.0 (2026.7.1) 在隔离的本地配置文件中列出了全部 165 个便携版技能，并读取了选定的主文件、元数据及移动后的示例。该检查中未测试 Hub 安装、更新与模型调用。

如果你希望获得智能技能发现与推荐能力，而非本地/离线安装，请运行本地/自托管 MCP 并使用其 `find_skills` 和 `suggest_skills` 工具。MCP 路径与 Hermes tap 服务于不同类型的采用者；目前没有计划单独推出 Hermes 插件。

完整 Hermes 指南：[docs/HERMES.md](docs/HERMES.md)。

### 任何兼容 Agent Skills 的工具

下载[便携版 ZIP](https://github.com/GarethManning/education-agent-skills/releases/download/v3.1.0/education-agent-skills-portable-v3.1.0.zip)并解压：`agent-skills/` 目录包含 165 个技能文件夹及一份安装说明。对于要求严格标准前置元数据的客户端，请从 `agent-skills/<skill-name>/` 复制。维护者也可使用[隔离 Python 环境](docs/AGENT_SKILLS.md#generate-the-portable-edition)在 `dist/agent-skills/` 生成相同配置。将选定的完整文件夹复制到客户端的技能目录中，保留其中的 `references/`、`agents/` 及其他随附文件。使用已复制的技能不需要 Python 或 Node 构建。请检查客户端的发现路径与调用控制；通用客户端可能会忽略特定厂商的策略文件。

### 手动使用（无需安装）

1. 打开仓库中的任意技能文件（位于 `skills/` 下）
2. 复制提示词代码块
3. 粘贴到任意 AI 中，并根据你的班级或教学情境填写相应字段

---

## 反馈与贡献

非常欢迎你的想法与反馈。如果你有建议、发现问题或希望参与贡献：

- 邮箱：gareth.manning@gmail.com
- X：https://x.com/worldteacherman
- LinkedIn：https://www.linkedin.com/in/gareth-manning-a404b387/
- 在 GitHub 上提交 Pull Request 或 Issue

---

**我是教育者 — [从这里开始](#立即试用)**
无需配置。使用插件、本地技能安装或手动复制粘贴，即可开始教学设计。

**我是开发者或 AI 构建者 — [从这里开始](#系统架构)**
YAML schema、类型化输入与输出、串联元数据、[本地/自托管 MCP](#mcp-服务器)。

---

## 适用人群

- **一线教师**：希望无需花费数小时查阅文献，即可完成循证的教案与评价设计
- **大学讲师与教授**：未受过或较少接受过教师培训，希望获得实用、有研究依据的教学支持
- **课程设计师与教学主管**：构建教学项目、单元计划与评价体系
- **创新与另类教育学校领导者**——国际学校、蒙特梭利、项目式学习、民主学校及自然教育学校
- **教育创新者**——构建新型学校模式、替代性项目与下一代学习环境的探索者。循证约束不会限制教育的创造性重塑，反而会使其更加深厚。
- **教育科技开发者与 AI 构建者**：需要一个结构化、可编程访问的教育知识层
- **教育研究者**：关注研究证据如何转化为 AI 介导的教学实践

---

## 为何建立本项目

AI 正迅速进入教育领域。它究竟是会提升学习成效，还是仅仅将平庸的教学实践规模化复制，几乎完全取决于它建立在什么基础之上。

大多数 AI 教育工具建立在惯例、习惯与假设之上——即教育者“一直以来都在做的事”，而非研究证明“真正有效的事”。学习风格论、僵化的教案结构、与学习理论脱节的福祉项目。随着 AI 在教育中不断扩展，将低效实践规模化的风险也在同步放大。

建立本技能库正是为了打造不同的东西：为教育中的 AI 奠定可信、严谨的基础。它锚定于具名研究，坦诚说明自身局限，并专为站在前沿的教育者而设计——致力于构建下一代学校，而非仅仅优化现有模式。

其中的潜力是真实的：以前所未有的规模提供个性化、循证的学习支持。但前提是驱动它的必须是真正的证据。

其价值不仅在于个性化学习，更在于教学质量与教师工作负荷。原本需要花费数小时检索、设计与反复推敲的教育者，如今可在几分钟内获得结构化、有研究依据的支持——从而把更多时间留给只有人类教师才能完成的育人工作。

这只是其中一种用法。同一个技能库还可以驱动全校范围的课程审计、教师个性化专业发展路径，或编排期末评价复盘。技能是基础，下方的架构描述了实现这一切的各层设计。

---

## 立即试用

### 通过运行时安装（推荐）

在 Claude、Codex 或 Hermes 中安装技能，然后用自然语言告诉代理你的需求。系统可以自动选择相关技能，或在本地进行检索。

**示例：** 对代理说 *“我正在规划一个九年级科学‘细胞’单元——共 6 周，每周 3 节课。”*

代理可以组合使用**逆向设计单元规划器（Backwards Design Unit Planner）**、**间隔练习调度器（Spaced Practice Scheduler）**和**提取练习生成器（Retrieval Practice Generator）**，起草包含间隔提取与形成性评价活动的教学计划，供教育者审阅。这是一个示例工作流，并非经过实测的多代理运行或 90 秒性能保证。

### 不使用插件（手动方式）

无需 API 密钥，无需技术配置，无需安装依赖。

1. 打开仓库中的任意技能文件（位于 `skills/` 下）
2. 复制提示词代码块
3. 粘贴到任意 AI 中，并根据你的班级或教学情境填写字段

**示例：** 打开 `skills/memory-learning-science/spaced-practice-scheduler/SKILL.md` 并提供：

- 主题：细胞结构、物质运输、细胞分裂、酶、生物大分子
- 时间周期：8 周学期，2 月 3 日开始
- 每周课时：3 节

Claude 将返回一份完整的逐周计划，展示何时教授新内容、何时以递增间隔重温先前主题——并为每个复习时段提供具体的提取练习活动。递增间隔是一种受间隔效应研究（包括 Cepeda 等人，2006）启发的实用排程启发式方法，而非该元分析针对本班得出的精确最优解。复习时机应根据记忆保持目标与学习者证据动态调整；当复习暴露出知识缺口时，该技能也会提供应对指导。

---

## 核心差异化特点

**以证据作为过滤器——包括明确知道该排除什么。**
研究驱动的技能会引用具名作者、研究与发现；实践者原创框架则会明确区分自身方法与所借鉴的研究。缺乏实证支撑的框架——包括学习风格、VAK 以及其他流传广泛但证据薄弱的做法——均不予收录。本库在 [EXCLUSIONS.md](docs/EXCLUSIONS.md) 中详细记录了被排除的内容及原因。对于任何试图区分证据与惯例的学校或教研组而言，这份文档本身就值得一读。

**透明的证据强度评级。**

| 评级 | 含义 |
|------|------|
| **Strong（强）** | 多项元分析或系统综述得出一致结论 |
| **Moderate（中等）** | 具备扎实实验证据，但存在一定情境差异 |
| **Emerging（新兴）** | 具有前景的研究基础，但重复验证或实践转化有限 |
| **Original（原创）** | 实践者框架；清晰标注，不冒充有研究验证 |

原创框架集中在第 15 领域并如实标注。现有元数据中还保留了实践型（practitioner）与历史遗留的证据标签；这些标签未被静默映射为新评级。提示词本身尚未作为 AI 干预措施经过实证检验。[质量指南](docs/SKILL_QUALITY.md)说明了评审标准与尚存的研究局限。

**由拥有 20 年国际学校经验的教育者构建。**
每条提示词、每种输出结构以及每项已知局限中所蕴含的教学判断，均源自真实的课堂与课程设计实践——而非单纯的文献阅读。

**从第一天起即为编排而设计。**
YAML schema 头部、类型化输入输出字段、串联元数据与可组合输出内置于每个技能中。这并非事后强加元数据的提示词合集，而是专为程序化调用而工程化打造的技能库。

---

## 20 个领域

> **关于第 20 领域的说明：** 第 1–19 领域面向教师与课程设计者——用于生成教案、量规、支架与评价工具。第 20 领域则不同：这些技能在学生学习会话期间实时运行，塑造 AI 如何实时回应学习者。所有 20 个领域遵循相同的核心原则——以证据为基础——但使用者、输出形态与调用模式截然不同。详见[第 20 领域技能](skills/student-learning/)。

| # | 领域 | 技能数 | 核心聚焦 |
|---|------|--------|----------|
| 1 | **记忆与学习科学（Memory & Learning Science）** | 8 | 提取练习、间隔效应、交错练习、认知负荷、双重编码、精细加工提问、反馈 |
| 2 | **自我调节学习与元认知（Self-Regulated Learning & Metacognition）** | 5 | 自我调节支架、元认知提示、目标设定、学习策略选择、错误分析 |
| 3 | **明确教学与直接教学（Explicit & Direct Instruction）** | 5 | 渐进式放手序列、理解检查、课堂导入、出声思考示范、练习设计 |
| 4 | **提问、讨论与对话（Questioning, Discussion & Dialogue）** | 5 | 苏格拉底式提问、讨论规范、对话式教学动作、诊断性关键问题 |
| 5 | **读写、写作与批判性思维（Literacy, Writing & Critical Thinking）** | 7 | 论证结构、学科写作、阅读理解、来源评估、文本复杂度、媒体素养、批判性思维 |
| 6 | **EAL/D 与语言发展（EAL/D & Language Development）** | 5 | 语言需求分析、词汇分层、支架式任务调整、句型框架、庇护式教学 |
| 7 | **课程设计与评价（Curriculum Design & Assessment）** | 13 | 逆向设计、能力拆解、量规生成、评价效度、形成性评价、差异化教学、差距分析、学习进阶、项目式学习、门槛概念转化 |
| 8 | **福祉、动机与学生能动性（Wellbeing, Motivation & Student Agency）** | 12 | 动机诊断、自我效能感、福祉与学习联结、能动性支架、归属感及相关实践 |
| 9 | **专业学习与教师发展（Professional Learning & Teacher Development）** | 10 | 课堂观察、反思性实践、专业发展活动设计、数据解读及相关实践 |
| 10 | **全球与跨文化教学法（Global & Cross-Cultural Pedagogies）** | 9 | 变易理论、CPA 序列、现象式学习、文化回应式教学、Ubuntu、地方本位探究、瑞吉欧记录、生成性项目、跨文化效度 |
| 11 | **环境与体验式学习（Environmental & Experiential Learning）** | 6 | 户外学习、亲生命设计、生态探究、体验式学习循环、跨学科联结、服务学习 |
| 12 | **AI 学习科学（AI Learning Science）** | 14 | 自适应提示、错误示例、数字例题、间隔算法、AI 反馈、辅导对话、学习分析、协作学习、认知辅导、自我解释、元认知监控、建设性失败、例题向解题过渡、形成性评价循环 |
| 13 | **AI 素养（AI Literacy）** | 7 | AI 输出审计、幻觉事实核查、提示词素养、专业质询、学习边界映射、AI 苏格拉底对话、学科 AI 可靠性 |
| 14 | **蒙特梭利与替代性循证教学路径（Montessori & Alternative Evidence-Based Approaches）** | 4 | 三阶段课程、预备环境设计、混龄学习、不间断工作周期 |
| 15 | **原创框架（Original Frameworks）** | 17 | SEEDS 再生型探究、H3Uni 系统方法（界定范围、三地平线、困境导航、多视角决策轮）、发展阶段体系、学习目标撰写、量规逻辑、自主项目设计、倾向性评价、单点量规；复合编排器（评价设计、包容性设计、地方本位课程、再生型项目设计、慈悲系统意识） |
| 16 | **课程对齐（Curriculum Alignment）** | 4 | 覆盖度审计、KUD 图表编写、发展阶段转化、范围与序列 |
| 17 | **历史思维（Historical Thinking）** | 10 | 溯源、细读、语境化、互证、文献探究课设计、史料集策展、史料改编、策略示范、评价设计、核心历史问题评估 |
| 18 | **系统思维（Systems Thinking）** | 8 | 系统意识冰山、愿景冰山、六边形复杂度映射、杠杆与应对设计、心智模型映射、系统行动能动性圈、推理阶梯、系统福祉影响 |
| 19 | **包容性设计（Inclusive Design）** | 3 | UDL 课程审计、围绕参与/表征/行动的选项设计、授课前主动障碍预判 |
| 20 | **面向学生的学习技能（Student-Facing Learning Skills）** *（新增）* | 13 | 提取优先门控、先解释后追问、渐进提示阶梯、信心校准检查、卡点与错误诊断教练、AI 声明核查器、迁移桥梁、费曼回教评估、建设性失败协议、SRL 学习包装器、无辅助证据检查点、每周能动性复盘、支架撤除管理器 |

---

## Agent Skills 格式与验证

两套视图分别服务于不同客户端：

- **规范源文件（Canonical source）：** `skills/<domain>/<skill-name>/` 保留了类型化教育 schema、证据元数据及厂商选项，供现有插件和 MCP 适配器使用。其扩展前置元数据不声称通过严格的官方校验器。
- **便携版本（Portable edition）：** `dist/agent-skills/<skill-name>/` 采用标准前置元数据，保留源文件正文，并将完整的原始元数据存储在 `references/education.json` 中。完整文件夹包含许可证与本地资源/策略文件。

[2026 年 10 月 22 日本地验证](docs/audits/agent-skills-build-verification-2026-10-22.md)记录显示：**165/165 个便携版技能全部通过 `skills-ref` 0.1.0 校验**，且全部 165 个技能均被其提示词生成器收录（固定至上游提交 `69ef37e9424c0a7ea9dd2293b559e43ec8176379`）。这证明了在特定时间点与[官方规范](https://agentskills.io/specification)的兼容性，而非基金会官方认证、名为“1.0”或“v2”的规范版本，也非模型遵循度或学习者成效的证明。这些本地检查不代表任何托管环境更新。

面向开发者：[格式、导出与版本详情](docs/AGENT_SKILLS.md)。面向教育者与贡献者：[质量标准与局限性](docs/SKILL_QUALITY.md)。

---

## 系统架构

本仓库实现了技能库与 MCP 适配器。上下文引擎（第 2 层）与编排器（第 3 层）为架构提案，并未在此实现为实际服务。设计详情见 [ARCHITECTURE.md](docs/ARCHITECTURE.md)。

### 面向开发者：YAML schema

每个技能均以机器可读的 YAML 头部开头，包含技能 ID、领域、证据强度、证据来源、类型化输入/输出 schema、串联元数据及标签。完整格式可查看 `skills/` 下的任意技能文件，或参阅 [ARCHITECTURE.md](docs/ARCHITECTURE.md) 中的 schema 参考。

### MCP 服务器

MCP 源码支持本地 stdio 与自托管 Streamable HTTP。由本库运营的公共端点随 v3.1.0 退役，不再提供公开访问注册。参见[迁移选项](docs/HOSTED_MCP_ACCESS.md)。

对于本地 MCP，请从源码检出构建并配置你的客户端通过 stdio 启动它。无需配置 Vercel、访问令牌或邮件服务商。仅支持远程连接器的客户端需要由你自行运营的端点，并配置你自己的源站与认证机制。[安装说明](mcp-server/README.md)涵盖了这两种路径。

该服务器暴露：
- **157 个工具**（153 个可由模型调用的技能 + 4 个发现工具：`list_skills`、`find_skills`、`suggest_skills`、`get_skill_details`）
- **165 个提示词**（所有技能——包括 12 个标记为 `disable-model-invocation: true` 的技能——均可作为显式提示词使用）

源码、本地配置与开发说明：[`mcp-server/`](mcp-server/)

---

## 参与贡献

纳入标准请见 [CONTRIBUTING.md](CONTRIBUTING.md)。本库刻意保持高标准——每个技能都必须以具名证据为基础、如实评级并具有实用价值。本库的价值取决于其严谨性。

### 新增或修订技能的工作流

编辑规范技能及其资源，然后重新生成 `registry.json` 与 `mcp-server/src/skills.json`。单独生成并校验便携版本；生成的分发目录保持被 Git 忽略。[贡献者指南](CONTRIBUTING.md#validation-before-a-pull-request)提供了依赖安装、精确检查命令及需要提交的文件清单。更新本地克隆并不一定会刷新已安装的插件缓存或复制过去的技能；请按照对应客户端的更新说明操作。本地重新构建的 MCP 快照不等于托管环境发布。

---

## 致谢

由 [Gareth Manning](https://substack.com/@garethmanning) 构建——教育者、课程设计师与学习系统设计师，拥有横跨 27 个国家的 20 年国际教育经验。

## 许可证

本仓库中的教育技能、文档、示例及课程材料采用 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) 许可协议。开放、可分叉、相同方式共享。仓库级声明与完整法律条款请参见 [LICENSE](LICENSE) 文件。
