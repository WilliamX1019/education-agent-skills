# 社交媒体贴文：托管 MCP 过渡说明

仅在自托管访问页面与修复后的托管 MCP 候选版本在生产域名上发布并验证后使用以下内容。

## LinkedIn

我构建了 Education Agent Skills Library，作为一套免费、开源的 165 个循证教学与课程设计技能，供各类 AI 工具使用。

它支持 Claude、Codex 以及任何能够读取 Agent Skills 风格 `SKILL.md` 文件的工具。初衷一直很简单：让高质量、有研究依据的教育设计变得更加触手可及。

有一点我起初低估了：公共 MCP 端点是实打实的基础设施。

我为了方便大家而搭建的托管 MCP 服务器开始产生可观的 Vercel 费用，主要来自匿名的长连接请求。技能库本身依然免费，GitHub 仓库依然开源，本地使用依然零成本。但托管 MCP 端点无法永远作为一个无限制的匿名公共服务运行下去。

因此，我在支持方式与说明上做了一点调整：

- 如果你可以从 GitHub 本地安装这些技能，请优先采用本地方式。
- Codex 用户可以使用本地插件，或将技能复制到 `~/.codex/skills/`。
- Claude Code 用户可以直接从 GitHub 安装插件。
- 任何人依然可以复制 `SKILL.md` 文件并粘贴到 Claude、ChatGPT、Codex 或其他助手中使用。
- 如果你的工作流确实依赖托管 MCP，自托管访问页面会签发带有效期的个人凭据并应用防滥用限制。

这并非给知识设置付费墙，而是围绕托管基础设施划定的一条务实边界。

仓库地址：https://github.com/GarethManning/education-agent-skills
托管 MCP 访问申请：https://mcp-server-sigma-sooty.vercel.app/request-access

如果你一直在使用托管 MCP 端点且本地方案无法满足你的需求，请告诉我。在做出永久性决定前，我更希望先了解真实的使用场景。

## X / Twitter 串文

1/ 我需要对 Education Agent Skills Library 做一项小小的可持续性调整。

技能库依然免费 + 开源：面向 Claude、Codex 及其他 AI 工具的 165 个循证教育技能。

仓库：https://github.com/GarethManning/education-agent-skills

2/ 问题出在托管 MCP 端点上。

我当初上线它是为了方便使用，但匿名的长连接 MCP 流量如今带来了实实在在的 Vercel 账单。

技能是免费的，服务器托管不是。

3/ 因此，现在推荐优先采用本地使用方式：

- Claude Code：从 GitHub 安装插件
- Codex：使用本地插件或将技能复制到 `~/.codex/skills/`
- 任何 AI：手动复制 `SKILL.md` 提示词

无需托管服务器。

4/ 如果你的工作流特别依赖托管 MCP，自托管访问页面会签发带防滥用限制的个人过期凭据。

托管 MCP 申请：https://mcp-server-sigma-sooty.vercel.app/request-access

5/ 我想避免那种常见的开源困境：

免费公共端点 → 意外天价账单 → 突然关停。

相反，我希望：保持技能库开放，把免费的本地选项讲清楚，并为托管基础设施设定合理的边界。

## 单条 X / Twitter 贴文

小更新：Education Agent Skills 依然保持免费 + 开源，但托管 MCP 端点存在实际的基础设施成本。

请尽量使用本地安装方式。

托管 MCP 申请：https://mcp-server-sigma-sooty.vercel.app/request-access

仓库：https://github.com/GarethManning/education-agent-skills

## Substack / 长文草稿

# 在保持 Education Agent Skills Library 免费的同时，让托管 MCP 可持续运行

当我发布 Education Agent Skills Library 时，我希望它能在尽可能多的 AI 环境中发挥作用。

如今，这个技能库已经包含 165 个循证教育技能：涵盖课程设计、评价、学习科学、福祉、历史思维、AI 素养、教师专业学习等。每个技能都是结构化的 `SKILL.md` 文件，扎根于具名研究，并专为 AI 代理使用而设计。

最重要的是：这个技能库是免费且开源的。

这一点不会改变。

改变的是托管 MCP 端点。

## 问题所在

我曾搭建了一个托管 MCP 服务器，让用户无需在本地安装任何东西就能将 Claude 等工具直接连接到技能库。

这确实很方便，但也带来了成本问题。匿名 MCP 流量会建立长连接。在 Vercel 上，即使这些连接只是静静挂着直到超时，也会持续产生费用。

结果是，一个为了图方便而设的免费端点开始变成一份真实的基础设施账单。

这就是开放 AI 基础设施中一个枯燥却关键的现实：分享提示词与技能文件几乎没有成本；但运行托管远程服务并不总是便宜的。

## 依然免费的部分

技能库本身依然免费且开放。

你完全可以不依赖托管 MCP 服务器来使用它：

- 在 Claude Code 中从 GitHub 安装插件。
- 使用本地 Codex 插件。
- 将单个技能复制到 `~/.codex/skills/`。
- 打开任意 `SKILL.md` 文件，粘贴到 Claude、ChatGPT、Codex、Gemini 或其他助手中。
- 克隆仓库并在本地运行你自己的工作流。

对大多数用户而言，本地安装是最佳选择：速度更快、隐私性更好，也不会给项目带来托管成本。

## 托管 MCP 的适用场景

托管 MCP 在某些工作流中依然很有价值：

- 无法安装本地文件的远程客户端；
- 程序化的技能发现；
- 需要共享端点的实验项目；
- 需要连接器而非本地插件的用户。

但托管 MCP 必须具备某种访问控制、速率限制或支持者模式。否则，整个项目就会变成依赖某一个人默默承担基础设施账单。

这是不可持续的。

## 接下来的做法

我正在清晰地记录所有免费的本地选项，并通过自托管页面签发个人托管 MCP 凭据。

访问申请页面刻意设计得非常简短。我不需要你的电话号码、收入、学校地址或学生数据。它仅要求提供一个电子邮箱用于投递凭据；姓名和使用的工具均为选填。选填的使用场景文本会在检查后丢弃，不会存入任何数据库。

如果本地方案适合你，请优先使用本地方案。

如果托管 MCP 对你的工作流不可或缺，请在此申请访问：

https://mcp-server-sigma-sooty.vercel.app/request-access

## 核心原则

我不想把技能库封闭起来，也不想假装公共基础设施是免费的。

可持续的版本应当是：

- 知识保持开放；
- 本地使用保持免费；
- 托管便利访问设有合理边界；
- 真正需要托管 MCP 的人有渠道提出申请。

这似乎才是恰当的平衡点。

仓库：https://github.com/GarethManning/education-agent-skills
