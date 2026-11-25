# Hermes Agent 配置指南

如果你使用 [Hermes Agent](https://hermes-agent.nousresearch.com/) 并希望在本地使用 Gareth Manning 的 **Education Agent Skills Library**，请参考本指南。

在 Hermes 中推荐的路径是**选择性本地安装**，而非插件模式。本仓库继续作为规范、可审查的唯一事实来源；Hermes 则从 GitHub 将选定的 `SKILL.md` 文件夹安装到你的本地运行时中。

## 应该选择哪种方式？

| 路径 | 最适合场景 | 权衡考量 |
| --- | --- | --- |
| Hermes 选择性安装 | 在 Hermes 内部本地、离线、无依赖使用 | 需要自行选择要安装的技能 |
| Hermes tap | 将本 GitHub 仓库注册为社区技能源 | 当前 Hermes tap 搜索最适用于扁平结构的技能仓库，因此单个安装时请使用下方的完整标识符 |
| 本地/自托管 MCP | 通过 `find_skills` / `suggest_skills` 进行发现 | 需在本地运行 stdio 或自行运营经认证的 HTTP 端点 |
| Claude/Codex 插件 | 已在这些运行时中工作的用户 | 特定于运行时的安装路径 |
| 手动复制粘贴 | 零配置试用单个技能 | 无自动发现或编排能力 |

## 可选步骤：添加 GitHub tap

```bash
hermes skills tap add GarethManning/education-agent-skills
```

此命令会将本仓库注册为 Hermes 社区源。由于本库保留了领域子目录结构（`skills/<domain>/<skill-name>/SKILL.md`），源码安装时请使用完整技能标识符。隔离验证检查了便携版发现与资源读取；Hub 安装与更新尚未测试。

## 安装单个技能

```bash
hermes skills install \
  GarethManning/education-agent-skills/skills/original-frameworks/learning-target-authoring-guide \
  --category education --yes
```

安装完成后，验证 Hermes 是否已识别该技能：

```bash
hermes skills list
```

## 推荐入门技能包

默认情况下请勿安装全部 165 个技能。本库刻意保持较广的覆盖面；较小的本地技能集合更易于检索，也更不容易造成代理行为的冗余干扰。

### 课程与评价入门包

```bash
hermes skills install GarethManning/education-agent-skills/skills/curriculum-assessment/competency-unpacker --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/original-frameworks/learning-target-authoring-guide --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/curriculum-assessment/kud-knowledge-type-mapper --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/curriculum-assessment/criterion-referenced-rubric-generator --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/curriculum-assessment/assessment-validity-checker --category education --yes
```

### 学习科学入门包

```bash
hermes skills install GarethManning/education-agent-skills/skills/memory-learning-science/retrieval-practice-generator --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/memory-learning-science/spaced-practice-scheduler --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/memory-learning-science/feedback-quality-analyser --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/self-regulated-learning/metacognitive-prompt-library --category education --yes
```

### 面向学生的 AI 学习入门包

```bash
hermes skills install GarethManning/education-agent-skills/skills/student-learning/retrieve-first-gate --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/student-learning/progressive-hint-ladder --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/student-learning/stuck-and-error-diagnosis-coach --category education --yes
hermes skills install GarethManning/education-agent-skills/skills/student-learning/teach-back-evaluator --category education --yes
```

## 完整便携版文件夹

如需便携版副本，请下载 [v3.1.0 ZIP](https://github.com/GarethManning/education-agent-skills/releases/download/v3.1.0/education-agent-skills-portable-v3.1.0.zip)。解压后的 `agent-skills/` 包含 165 个文件夹并附带一份安装说明。将选定的完整文件夹复制到你的 Hermes 配置文件所规定的技能目录中；请保留 `references/education.json`、`LICENSE`、示例及策略文件。使用前请通过 `hermes skills list` 检查并审阅相关资源。替换前请妥善保留已有的本地编辑版本。

仅下载单个原始 `SKILL.md` 会遗漏支持资源，不适合作为完整安装方式。若只想免安装试用，请手动复制提示词并在仓库中查阅其链接的示例资源。

## 智能技能选择

目前没有计划推出 Hermes 插件。MCP 源码已经暴露了发现层。

如果你希望系统根据教学需求推荐技能，请运行[本地/自托管 MCP](../mcp-server/README.md) 并使用：

- `find_skills` — 按关键词、领域、证据评级或任务搜索；
- `suggest_skills` — 描述教学/课程需求以获取推荐技能；
- `get_skill_details` — 获取完整的技能元数据与指导；
- `list_skills` — 浏览整个技能库。

当你需要本地/离线技能时，请使用 Hermes 选择性安装；当你需要通过本地进程或自建已认证端点进行技能发现时，请使用 MCP。由本库运营的公共服务随 v3.1.0 退役，不再提供公开注册。仅支持远程连接的客户端需要自建托管端点或改用其他受支持的安装路径；不存在自动迁移连接器的机制。

## 信任与许可

Hermes 社区源不同于默认的受信任 OpenAI/Anthropic 官方仓库。因此，本库的信任信号被刻意设计为公开且可审查的：

- 每个技能在 GitHub 上均以纯文本形式公开；
- 证据强度与文献来源在每份 `SKILL.md` 中清晰可见；
- 被排除的方法记录在 [`EXCLUSIONS.md`](EXCLUSIONS.md) 中；
- 架构与 schema 记录在 [`ARCHITECTURE.md`](ARCHITECTURE.md) 中；
- 许可协议为 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)。

## 本仓库之外的发现渠道

在 Hermes 路径验证完成后，下一步分发计划是提议将本库收录至 [`VoltAgent/awesome-agent-skills`](https://github.com/VoltAgent/awesome-agent-skills)，Hermes 会将其作为默认社区源进行扫描。对于尚未听说过本仓库的用户而言，这是真正的发现渠道。
