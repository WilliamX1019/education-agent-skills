# Agent Skills 开发者指南

本文档面向希望以程序化方式消费、编排或扩展 Education Agent Skills Library 的开发者与 AI 构建者。

---

## 源文件、标准与便携版本

[Agent Skills](https://agentskills.io/home) 是最初由 Anthropic 开发的开放文件夹格式。[规范](https://agentskills.io/specification)定义了一个包含必需 `name` 与 `description` 字段的 `SKILL.md`、Markdown 指令及可选资源。本独立技能库参与该开放生态；格式兼容并不意味着厂商背书或官方认证。

位于 `skills/<domain>/<skill-name>/` 的规范源文件保留了丰富的项目/厂商前置元数据：证据、类型化输入与输出、串联提示及调用标志。现有的源码插件与 MCP 使用这些扩展文件。**源文件校验属于项目级检查，而非严格的官方格式校验。**

生成的 `dist/agent-skills/<skill-name>/` 版本仅包含标准前置元数据字段：`name`、`description`、`license` 以及带有 `education.*` 键的字符串值 `metadata`。完整的原始元数据连同来源溯源信息一并保存在 `references/education.json` 的 `metadata` 下。原始 Markdown 正文紧随一条元数据指引之后，保持原样不变。每个文件夹均包含 `LICENSE` 以及存在时的本地 `references/`、`scripts/`、`assets/` 和 `agents/` 文件。复制时请复制整个文件夹，而不仅仅是 `SKILL.md`。

[集成验证回执](audits/agent-skills-build-verification-2026-10-22.md)记录了 **165/165 个便携版技能全部通过 `skills-ref` 0.1.0 校验**，且 165/165 个均被官方 `to_prompt` 收录。该工具/源码固定于 [agentskills/agentskills 提交 69ef37e9424c0a7ea9dd2293b559e43ec8176379](https://github.com/agentskills/agentskills/tree/69ef37e9424c0a7ea9dd2293b559e43ec8176379/skills-ref)。其经评估的源文件/资源/许可证 SHA256 为 `a2e71fa05cde2ea2ebccd875023ebb0368c11379beb1fe165c1e0debd12938dc`；回执标识的是工作区实际内容，而不仅仅是 Git HEAD。后续对源文件的任何编辑都需要重新导出并校验。

### 下载便携版本

[v3.1.0 发布页](https://github.com/GarethManning/education-agent-skills/releases/tag/v3.1.0)提供了 [education-agent-skills-portable-v3.1.0.zip](https://github.com/GarethManning/education-agent-skills/releases/download/v3.1.0/education-agent-skills-portable-v3.1.0.zip)。解压后可找到包含 165 个技能文件夹的 `agent-skills/` 目录及一份随附的安装说明。将每个选定的完整 `agent-skills/<skill-name>/` 文件夹复制到客户端文档指定的技能目录中；保留其中的元数据、许可证、参考资料与策略文件。切勿将外层容器作为单个技能复制，也不要盲目覆盖合并到已有的本地编辑文件夹上。使用方无需导出器或其 Python 依赖。

### 生成便携版本

在仓库根目录（需具备 Python 3.11+ 和 Git），运行脚本前请先创建隔离环境。当系统 Python 缺少 PyYAML 时此方法同样适用：

```bash
python3 -m venv .venv-standard
.venv-standard/bin/python -m pip install -r requirements/standard-validation.txt
.venv-standard/bin/python scripts/export-standard-skills.py
.venv-standard/bin/python scripts/validate-standard-skills.py
```

依赖项包含固定版本的上游参考工具及其运行时依赖。首次安装需要联网。导出及使用已复制的技能不会调用模型；使用已复制的文件夹不需要 Python 或 Node 构建。

默认生成并校验 `dist/agent-skills/`。若需指定其他输出目录：

```bash
.venv-standard/bin/python scripts/export-standard-skills.py --output /absolute/path/to/new-profile
.venv-standard/bin/python scripts/validate-standard-skills.py /absolute/path/to/new-profile
```

导出器会拒绝重复名称/ID、无效元数据、不安全路径、冲突及符号链接。它仅会替换自己生成的未修改输出（通过 `.education-agent-skills-export.json` 校验）；替换已安装副本前请先保留有意的本地修改。切勿将生成的文件夹当作第二套源码库来维护修改。详见[贡献者检查](../CONTRIBUTING.md#validation-before-a-pull-request)。

### 现有集成方式

经测试的 Claude Code 2.1.307 校验器为 2.1.275+ 推荐的命令：

```text
/plugin install education-agent-skills --marketplace GarethManning/education-agent-skills
```

对于 Codex，请注册检出目录**并安装**其插件：

```bash
codex plugin marketplace add "$PWD"
codex plugin add education-agent-skills@education-agent-skills
codex plugin list --marketplace education-agent-skills --json
```

请在仓库根目录运行上述命令。`.claude-plugin/plugin.json` 和 `.codex-plugin/plugin.json` 列出了 20 个领域目录；`.agents/plugins/marketplace.json` 提供 Codex 市场配置。根目录下不存在 `plugin.json`。详见 [Codex 配置与缓存更新](CODEX.md)、[Hermes 配置](HERMES.md)与 [MCP 退役与迁移](HOSTED_MCP_ACCESS.md)。

回执区分了 Codex 0.163.0-alpha.11.1 隔离安装/列表检查、Claude 2.1.307 带提示性警告的清单校验，以及 Hermes v0.18.0 (2026.7.1) 隔离便携版列表/资源读取。实际模型激活、真实客户端设置与托管更新均尚未测试。更新本地克隆的源码并不证明已安装的缓存或复制的文件夹已同步刷新。

### 调用控制与版本边界

十二个源文件使用了 Claude 的 `disable-model-invocation: true`；对应的 Codex `agents/openai.yaml` 附属文件设置了 `allow_implicit_invocation: false`。MCP 将这些技能暴露为显式提示词，并将其排除在模型可调用工具之外。便携版导出保留了元数据与策略文件，但该标准并没有全局统一的仅显式调用控制机制：其他客户端可能会忽略它们。符合条件的技能只是可被选择的候选者，并不保证会被自动激活。

本项目**250 个字符的描述长度限制**比规范中 1,024 个字符的上限更为严格。正文长度指导旨在支持选择性披露，而非一条普适的“越短越好”规则或 5,000 个 token 的硬性失败阈值。请保留核心方法、边界与自检项；仅在可被发现且可用时才将可选示例移出。MCP 返回的是提取出的活跃提示词，不会自动返回整个文件或其链接的示例。

`registry.json` schema 中的 `version: "2.0"` 与历史遗留的 `standard: "agent-skills-1.0"` 属于项目元数据，而非上游规范版本或官方认证。GitHub 发布版本 v3.1.0、插件版本 2.2.0、根目录 npm 包版本 1.0.0、MCP 包版本 0.1.0 以及便携版配置文件 `education-agent-skills-portable-1` 分别标识不同的产物。切勿强行让它们保持一致或虚构上游语义化版本号。许可范围仍以 [LICENSE](../LICENSE) 中所述为准；本配置文件不对软件或第三方源码重新授权。

---

## registry.json

注册表是本技能库最主要的程序化接口。它由 `scripts/generate-registry.py` 根据 `SKILL.md` 前置元数据生成。

### 结构

```json
{
  "version": "2.0",
  "generated": "<ISO timestamp>",
  "standard": "agent-skills-1.0",
  "total_skills": 165,
  "domains": [
    { "id": "memory-learning-science", "label": "Memory & Learning Science", "skill_count": 8 }
  ],
  "skills": [
    {
      "id": "memory-learning-science/spaced-practice-scheduler",
      "name": "spaced-practice-scheduler",
      "display_name": "Spaced Practice Schedule Builder",
      "domain": "memory-learning-science",
      "description": "<project description, at most 250 characters>",
      "disable_model_invocation": false,
      "evidence_strength": "strong",
      "tags": ["spacing", "memory", "planning"],
      "teacher_time": "5 minutes",
      "chains_with": ["retrieval-practice-generator", "interleaving-unit-planner"],
      "chain_edges": {
        "receives_from": [],
        "feeds_into": [],
        "output_field": null,
        "input_field": null
      },
      "path": "skills/memory-learning-science/spaced-practice-scheduler/SKILL.md"
    }
  ]
}
```

### 消费注册表

```python
import json

with open('registry.json') as f:
    registry = json.load(f)

# 按领域查找技能
science_skills = [s for s in registry['skills'] if s['domain'] == 'memory-learning-science']

# 按标签查找技能
spacing_skills = [s for s in registry['skills'] if 'spacing' in s['tags']]

# 查找可与给定技能串联的技能
chains = [s for s in registry['skills'] if 'spaced-practice-scheduler' in s['chains_with']]

# 根据源文件标志筛选允许隐式调用的候选技能
auto_skills = [s for s in registry['skills'] if not s['disable_model_invocation']]
```

### 保持注册表同步

```bash
python3 scripts/generate-registry.py
```

CI 会在每次推送和 PR 时校验 `registry.json` 是否与当前的 `SKILL.md` 文件保持一致。

---

## 构建编排器

本技能库被设计为三层架构中的第 1 层：

### 第 1 层 — 技能（本仓库）

涵盖 20 个领域的 165 个技能，其中包括 13 个面向学生的工作流。源文件与 MCP 适配器已在此实现；实践者原创方法保留其原有标签与证据限制。技能本身不提供持久化学习者存储。

### 第 2 层 — 上下文引擎（架构提案，此处未实现）

拟议中的服务将位于编排器与技能之间，用于保存相关的班级与课程上下文。它可以在调用技能时自动填充可选输入；本仓库未实现该存储层或其隐私控制机制。

### 第 3 层 — 编排器（架构提案，此处未实现）

未来的编排器将接收一个高层次的教育者目标（例如：“为八年级设计一个为期 6 周的气候变化单元”），并执行：

1. 向上下文引擎查询相关的学生与课程数据
2. 利用注册表选择并排序适当的技能
3. 将技能输出串联为连贯的计划
4. 呈现结果供教育者审阅与批准

每个注册表条目中的 `chains_with` 数组提供了显式的串联提示。编排器还可以通过匹配库中各技能的输出 schema 与输入 schema 来发现新的串联组合。

---

## 串联图谱（Chaining Graph）

每个技能条目中的 `chain_edges` 对象是类型化串联边的占位符：

- `receives_from`：输出可流入本技能输入的技能列表
- `feeds_into`：消费本技能输出的技能列表
- `output_field`：向下游传递的具体输出字段
- `input_field`：接收上游数据的具体输入字段

目前 `receives_from` 和 `feeds_into` 均为空列表；`output_field` 和 `input_field` 均为 `null`。类型化图谱构建仍是未来工作。`chains_with` 包含无类型建议（包括历史遗留的未解析建议），不保证 schema 一定兼容或构成可执行链路。

---

## 上下文与技能

客户端可以在选定技能的同时提供课程文档、班级背景与学校政策。使用前请确认必需输入、尽量减少可识别的学习者信息，并对输出进行审阅。无论是开放格式还是本注册表，都不会自动提供上下文引擎、解决相互冲突的政策，或保证模型必然会选择正确的技能。[质量指南](SKILL_QUALITY.md)描述了格式测试无法确立的教育维度检查。
