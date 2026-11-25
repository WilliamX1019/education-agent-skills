# Education Skills Library — Agent Skills v2 升级规范

> 历史记录：下文中的计数、拟议布局及“v2/1.0”标准表述描述的是早期项目状态。关于当前的源文件/便携版契约及已验证边界，请以[开发者指南](AGENT_SKILLS.md)和[2026 年 10 月 22 日构建回执](audits/agent-skills-build-verification-2026-10-22.md)为准。本说明仅保留历史文本。

**致 Claude Code：在编写任何一行代码之前，请先通读本全文。**

---

## 概述

本规范将 Claude Education Skills Library 从一个自定义 MCP 服务的技能合集升级为完全符合 Agent Skills 开放标准的插件。预期成果：任何 Claude 用户均可通过一条命令安装全部 106 个技能；技能在相关场景下无需显式调用即可自动激活；并且本库可在任何兼容 Agent Skills 的 AI 工具中分发使用。

## 仓库路径

`~/Documents/Github/education-agent-skills`

请在 `feature/agent-skills-v2` 分支上工作。在人类审阅 `REVIEW.md`（于第 2 阶段生成）之前，请勿合并到 `main` 分支。

## 不可妥协的原则

- 零内容丢失。保留每个技能现有 YAML 与 Markdown 中的每一个词。
- 完全向后兼容。现有的 MCP 服务器继续正常运行，保持不变。
- 不得修改领域名称、技能名称、证据来源、输入/输出 schema 或 `chains_well_with` 元数据。
- `SKILL.md` 内容长度：每个文件尽量保持在 500 行以内。如果任何现有技能文件超出此限制，请在日志中记录，但不要截断。
- 在第 1 阶段期间从仓库中移除 `.DS_Store`，并将其添加到 `.gitignore`。

---

## 当前结构

```
education-agent-skills/
├── ai-learning-science/           ← 领域文件夹
│   └── skill-name.md              ← 扁平技能文件
├── curriculum-assessment/
│   └── skill-name.md
├── ... (共 14 个领域文件夹)
├── ARCHITECTURE.md
├── EVIDENCE.md
├── EXCLUSIONS.md
├── IMPLEMENTATIONS.md
├── README.md
└── llms.txt
```

## 目标结构

```
education-agent-skills/
├── skills/                                          ← 新增：插件技能根目录
│   ├── ai-learning-science/                         ← 保留领域作为子目录
│   │   └── adaptive-hint-sequence-designer/         ← 新增：技能文件夹
│   │       └── SKILL.md                             ← 从 domain/skill.md 迁移而来
│   ├── curriculum-assessment/
│   │   └── backwards-design-unit-planner/
│   │       └── SKILL.md
│   └── ... (全部 14 个领域，全部 106 个技能)
├── registry.json                                    ← 新增：机器可读技能索引
├── plugin.json                                      ← 新增：插件清单
├── ARCHITECTURE.md                                  ← 已更新
├── AGENT_SKILLS.md                                  ← 新增：开发者指南
├── EVIDENCE.md
├── EXCLUSIONS.md
├── IMPLEMENTATIONS.md
├── README.md                                        ← 已更新
├── llms.txt
└── .gitignore                                       ← 已更新，包含 .DS_Store
```

---

## 第 1 阶段 — 结构迁移

**目标：** 将全部 106 个技能文件从 `domain/skill-name.md` 迁移至 `skills/domain/skill-name/SKILL.md`，实现零内容变更。

### 步骤

1. **盘点当前状态。** 在改动任何内容前，在仓库根目录编写 `migration-log.md`，列出找到的每个技能文件、其路径及字符数。这是用于验证的基准事实。

2. **创建 `skills/` 目录结构。** 针对每个现有的 `domain-name/skill-name.md`：
   - 创建 `skills/domain-name/skill-name/` 目录
   - 将文件移动至 `skills/domain-name/skill-name/SKILL.md`
   - 技能短标识（slug）由文件名派生（去掉 `.md` 扩展名，保留连字符）

3. **验证零内容丢失。** 迁移完成后，针对 `migration-log.md` 中的每个文件确认：
   - 新路径下存在该文件
   - 字符数完全一致
   - YAML 前置元数据完整（检查 `---` 起始标记）

4. **清理。** 从仓库中移除 `.DS_Store`。若 `.gitignore` 尚未包含它则添加进去。移除根目录下的空领域文件夹（迁移后它们应当均为空）。

5. **编写验证报告。** 追加至 `migration-log.md`：已迁移文件总数、任何失败项、任何跳过的文件。

### 测试

```bash
# 迁移前统计技能数（迁移前运行）
find . -name "*.md" -path "./*-*/*.md" | grep -v "skills/" | wc -l

# 迁移后统计技能数（必须一致）
find skills/ -name "SKILL.md" | wc -l

# 检查旧位置没有遗留的孤立 .md 文件
find . -name "*.md" -not -path "./skills/*" -not -name "README.md" \
  -not -name "ARCHITECTURE.md" -not -name "EVIDENCE.md" \
  -not -name "EXCLUSIONS.md" -not -name "IMPLEMENTATIONS.md" \
  -not -name "migration-log.md" -not -name "AGENT_SKILLS.md"
# 预期结果：仅根目录文档，无 domain/skill 文件
```

### 停止条件

在此停止并汇报结果。在确认技能数量匹配且零内容丢失之前，请勿进入第 2 阶段。输出："Phase 1 complete. N skills migrated. Zero content loss confirmed." 或具体的错误报告。

---

## 第 2 阶段 — 渐进式披露前置元数据

**目标：** 为每个 `SKILL.md` 添加 Agent Skills 标准前置元数据。将全部 106 条描述生成到一个 `REVIEW.md` 文件中供人工审阅。在人类审阅并批准 `REVIEW.md` 之前，切勿将描述合并进 `SKILL.md` 文件。

### 需添加的精确前置元数据字段

这些字段添加在每个 `SKILL.md` 现有 YAML 前置元数据区块的**顶部**。现有的 YAML（`skill_id`、`skill_name`、`domain`、`version`、`evidence_strength`、`evidence_sources`、`input_schema`、`output_schema`、`chains_well_with`、`tags`、`teacher_time`）完整保留在这些新字段下方。

```yaml
---
# AGENT SKILLS STANDARD FIELDS (new in v2)
name: skill-name-slug                    # 小写，仅限连字符，最多 64 字符 — 由目录名派生
description: "..."                       # 见下方描述规则 — 最多 250 字符
disable-model-invocation: false          # 见下方调用规则
user-invocable: true                     # 默认 true；仅对纯背景知识设为 false
effort: medium                           # 所有教育技能的默认值

# EXISTING FIELDS (preserved exactly as-is)
skill_id: "..."
skill_name: "..."
# ... 其余现有 YAML 保持不变
---
```

### 描述规则（关键——请仔细阅读）

**格式：** `[Active verb] [what it produces] for [context]. Use when [specific trigger scenario].`

**硬性约束：**
- 最多 250 个字符——平台会强制执行此限制，超出将被截断
- 将触发关键词前置——平台可能从末尾截断，绝不会从开头截断
- 使用教师日常语言，而非学术晦涩语言
- 必须足够具体，使得误激活时让人感觉“不对劲”，而不仅仅是“不相关”

**质量测试：** 通读描述并自问：*如果一位教师输入此内容作为搜索查询，这个技能会是正确的结果吗？如果在对话中途因为出现了这些词而激活了该技能，它会让人觉得有帮助还是突兀打扰？*

**优质描述示例：**
- `"Design a spaced retrieval schedule for any topic list and timeline. Use when planning units, term sequences, or revision programmes."`
- `"Generate a cascading hint sequence for a problem type, revealing progressively without giving answers. Use when designing tutoring dialogues or scaffolded worksheets."`
- `"Analyse the language demands of a classroom task for EAL/D students. Use when adapting tasks, planning support, or assessing accessibility."`

**劣质描述示例：**
- `"Facilitates the application of distributed practice principles to instructional scheduling."` — 过于学术化，未将触发词前置
- `"Spaced practice."` — 过短，无动作动词，无触发场景
- `"Help teachers design better lessons using evidence-based approaches."` — 过于宽泛，几乎会在所有场景下误触发

### 调用规则

对于以下类型的技能，设置 `disable-model-invocation: true`：
- 需要大量特定于学生的数据，而这些数据在大多数对话中不会出现（例如：`individual-spacing-algorithm-explainer` 需要过往学习表现数据）
- 属于第 14 领域（原创框架）——这些技能具有高度情境特异性，自动激活容易误触发
- 触发词过于宽泛，会导致频繁误激活（例如：`formative-assessment-technique-selector`）

对于所有其他技能，设置 `disable-model-invocation: false`（默认值）。

不确定时默认设为 `false`——人工审阅者会在 `REVIEW.md` 中排查过宽的触发器。

### 需生成的内容：REVIEW.md 格式

在仓库根目录编写单一的 `REVIEW.md` 文件，结构如下。这是供人类审阅的文件。暂勿将描述应用到 `SKILL.md` 文件中。

```markdown
# Skills Description Review — Agent Skills v2

**Instructions for reviewer:**
- Each entry shows the proposed description and invocation setting.
- Edit directly in this file if any description is wrong, too broad, too narrow, or violates the format rules.
- Delete the ❓ marker on any line you want to flag for discussion.
- When satisfied with all 106 entries, confirm and descriptions will be applied.

---

## Domain: memory-learning-science (8 skills)

### spaced-practice-scheduler
**Proposed description:**
"Design a spaced retrieval schedule for any topic list and timeline. Use when planning units, term sequences, or revision programmes."
**Character count:** 127 ✅
**disable-model-invocation:** false
**Rationale:** Triggers are specific (revision planning, spacing), unlikely to misfire.

---

### retrieval-practice-generator
...
```

每个条目必须包含：
- 拟议描述（加引号）
- 字符数及 ✅（≤250）或 ❌（>250）
- `disable-model-invocation` 值
- 关于调用设置的一行理由说明

按照与现有仓库相同的顺序按领域分组。涵盖全部 14 个领域。

### 如何生成优质描述

对于每个技能，使用以下输入生成描述：
1. `skill_name` 字段
2. `domain` 字段
3. `tags` 数组
4. `input_schema.required` 字段（教师需要提供什么？）
5. `chains_well_with` 列表（该技能属于什么工作流？）

描述应当概括：*技能产出什么* + *在何种具体情境下有用*。

### 第 2 阶段测试

```python
# 在人工审阅前运行此脚本以校验 REVIEW.md 中的所有描述
import re

with open('REVIEW.md') as f:
    content = f.read()

# 查找所有拟议描述
descriptions = re.findall(r'\*\*Proposed description:\*\*\n"([^"]+)"', content)
print(f"Found {len(descriptions)} descriptions")
assert len(descriptions) == 106, f"Expected 106, got {len(descriptions)}"

for i, desc in enumerate(descriptions):
    assert len(desc) <= 250, f"Description {i+1} exceeds 250 chars: {len(desc)} chars"
    assert desc[0].isupper(), f"Description {i+1} doesn't start with capital letter"

print("All 106 descriptions valid (length and format checks passed)")
```

### 停止条件

生成 `REVIEW.md` 并停止。输出："Phase 2 complete. REVIEW.md generated with 106 skill descriptions. Please review REVIEW.md and confirm before Phase 3 proceeds."

**未经明确的人工确认，切勿进入第 3 阶段。**

---

## 第 3 阶段 — 应用经批准的描述

**本阶段仅在人类审阅并确认 `REVIEW.md` 后运行。**

### 步骤

1. 从 `REVIEW.md` 解析经批准的描述（使用文件的最终状态，包含任何人工编辑）。

2. 针对每个技能，将新的前置元数据字段添加到 `SKILL.md` 现有 YAML 区块的顶部：
   - `name`：由目录名称派生
   - `description`：来自经批准的 `REVIEW.md`
   - `disable-model-invocation`：来自经批准的 `REVIEW.md`
   - `user-invocable: true`（全部默认）
   - `effort: medium`（全部默认）

3. 修改后验证每个文件中的 YAML 依然有效。

### 测试

```bash
# 验证所有 SKILL.md 文件中的 YAML 均可解析
python3 -c "
import yaml, glob, sys
errors = []
for f in glob.glob('skills/**/**/SKILL.md', recursive=True):
    with open(f) as fh:
        content = fh.read()
    # Extract frontmatter
    if content.startswith('---'):
        end = content.index('---', 3)
        fm = content[3:end]
        try:
            yaml.safe_load(fm)
        except Exception as e:
            errors.append(f'{f}: {e}')
if errors:
    for e in errors: print(e)
    sys.exit(1)
print(f'All SKILL.md files have valid YAML frontmatter')
"
```

---

## 第 4 阶段 — 注册表清单

**目标：** 生成 `registry.json`——实现渐进式披露的机器可读技能索引。

### registry.json Schema

```json
{
  "version": "2.0",
  "generated": "<ISO timestamp>",
  "standard": "agent-skills-1.0",
  "total_skills": 106,
  "domains": [
    {
      "id": "memory-learning-science",
      "label": "Memory & Learning Science",
      "skill_count": 8
    }
  ],
  "skills": [
    {
      "id": "memory-learning-science/spaced-practice-scheduler",
      "name": "spaced-practice-scheduler",
      "display_name": "Spaced Practice Schedule Builder",
      "domain": "memory-learning-science",
      "description": "<250-char description>",
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

**关于 `chain_edges` 的说明：** 在 v2 中，`output_field` 和 `input_field` 的值刻意保留为 `null`。这些是用于类型化串联边的占位符槽位，将在单独的串联设计会话中填充。切勿尝试推断这些值——请保留为 `null`。

### 生成方式

编写 Python 脚本 `scripts/generate-registry.py`，实现以下功能：
1. 遍历 `skills/` 目录
2. 读取每个 `SKILL.md` 的 YAML 前置元数据
3. 提取所需字段
4. 写入 `registry.json`

该脚本应可独立运行，并添加到 CI 中以保持注册表同步。

### 测试

```python
import json

with open('registry.json') as f:
    registry = json.load(f)

assert registry['total_skills'] == 106
assert len(registry['skills']) == 106
assert all(len(s['description']) <= 250 for s in registry['skills'])
assert all(s['path'].startswith('skills/') for s in registry['skills'])
print("registry.json valid")
```

---

## 第 5 阶段 — 插件清单

**目标：** 创建 `plugin.json`，使技能库可作为 Claude Code 插件安装。

### plugin.json Schema

```json
{
  "name": "education-agent-skills",
  "display_name": "Claude Education Skills Library",
  "version": "2.0.0",
  "description": "106 evidence-based pedagogical skills for educators. Curriculum design, assessment, learning science, wellbeing, professional learning, and more.",
  "author": "Gareth Manning",
  "homepage": "https://github.com/GarethManning/education-agent-skills",
  "license": "CC BY-SA 4.0",
  "skills": "skills/",
  "min_claude_version": "claude-sonnet-4-6"
}
```

### 测试

```bash
# 验证 plugin.json 为有效 JSON
python3 -c "import json; json.load(open('plugin.json')); print('plugin.json valid')"

# 确认 skills 目录引用正确
python3 -c "
import json, os
p = json.load(open('plugin.json'))
assert os.path.isdir(p['skills']), f\"Skills dir not found: {p['skills']}\"
print('Plugin skills directory exists')
"
```

---

## 第 6 阶段 — 文档更新

### README.md

在 README 顶部（现有内容之前）添加：

```markdown
## Install

```
/plugin install GarethManning/education-agent-skills
```
Or browse the [Skills Directory](https://claude.ai) to install individual domain bundles.

[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-1.0-blue)](https://agentskills.io)
[![Skills](https://img.shields.io/badge/skills-106-blue)](https://github.com/GarethManning/education-agent-skills)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
```

### ARCHITECTURE.md

新增名为 "Agent Skills Compliance (v2)" 的章节，描述：
- 插件结构
- 渐进式披露机制（元数据优先加载）
- `registry.json` 及其赋能的能力
- 类型化串联边（v2 中为 null，待串联设计会话填充）
- 冲突解决规则：当多个技能自动激活时，以建议形式呈现，切勿同时自动触发多个

### AGENT_SKILLS.md（新文件）

为开发者/AI 构建者受众创建新文件，涵盖：
- 如何安装插件
- `registry.json` 的工作原理及如何以程序化方式消费它
- 如何在本库之上构建编排器
- 串联图谱结构（包括 null 占位符及其未来形态）
- 三层架构（技能 → 上下文引擎 → 编排器）
- Projects 与 Skills 如何协同工作（Projects 用于静态班级上下文，Skills 用于动态教学法激活）

---

## 第 7 阶段 — CI 与最终验证

### .github/workflows/validate.yml

创建在每次推送到 `main` 和每次 PR 时运行的 GitHub Actions 工作流：

```yaml
name: Validate Skills Library
on: [push, pull_request]
jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.11'
      - name: Install dependencies
        run: pip install pyyaml
      - name: Count skills
        run: |
          COUNT=$(find skills/ -name "SKILL.md" | wc -l)
          echo "Skills found: $COUNT"
          [ "$COUNT" -eq 106 ] || (echo "Expected 106 skills, found $COUNT" && exit 1)
      - name: Validate YAML frontmatter
        run: python3 scripts/validate-skills.py
      - name: Validate registry.json
        run: python3 scripts/validate-registry.py
      - name: Check registry is in sync
        run: |
          python3 scripts/generate-registry.py
          git diff --exit-code registry.json || (echo "registry.json is out of sync — run scripts/generate-registry.py" && exit 1)
```

### scripts/validate-skills.py

编写校验脚本，检查每个 `SKILL.md`：
- 有效的 YAML 前置元数据
- 存在 `name` 字段且有效（小写、连字符、最多 64 字符）
- 存在 `description` 字段且 ≤250 字符
- `disable-model-invocation` 为布尔值
- 现有必需字段仍存在：`skill_id`、`skill_name`、`domain`、`evidence_strength`
- 文件少于 500 行（发出警告，不失败）

### 最终手动测试集

所有阶段完成后，手动运行以下五项测试并汇报结果：

1. **安装测试：** 在全新的 Claude Code 会话中，运行 `/plugin install GarethManning/education-agent-skills`（或从本地路径安装）。确认技能出现在 `/` 菜单中。

2. **自动激活测试：** 输入 "I need to plan revision sessions for my Year 9 class over the next 6 weeks." 确认 `spaced-practice-scheduler` 激活或作为建议出现。

3. **直接调用测试：** 直接运行 `/backwards-design-unit-planner`。确认其运行并生成预期输出。

4. **注册表测试：** 确认 `registry.json` 是有效的 JSON，包含 106 个技能，且所有描述均 ≤250 字符。

5. **向后兼容性测试：** 使用 `list_skills` 向现有 MCP 服务器（`mcp-server-sigma-sooty.vercel.app/mcp`）发起测试调用。确认其仍能返回结果（MCP 服务器为独立仓库——此测试仅确认迁移未破坏 MCP 服务器对本仓库的预期结构）。

---

## 执行顺序摘要

```
Phase 1: Structural Migration         → STOP: confirm skill count + zero content loss
Phase 2: Generate descriptions        → STOP: human reviews REVIEW.md
Phase 3: Apply approved descriptions  → runs after human confirms REVIEW.md
Phase 4: Registry manifest            → automated
Phase 5: Plugin manifest              → automated  
Phase 6: Documentation                → automated
Phase 7: CI + final validation        → automated, then manual test battery
```

一旦第 2 阶段获得批准，第 3–7 阶段可连续运行。

---

## 本次会话超出范围的内容

- MCP 服务器更新（独立仓库 — `mcp-server-sigma-sooty.vercel.app/mcp` — 独立的 Claude Code 会话）
- 类型化串联边的值（仅保留 null 占位符——需要单独的串联设计会话）
- 新增技能或领域
- 测试工具模板（Harness templates）
- 第 2 层（上下文引擎）或第 3 层（编排器）开发工作

---

## 完成定义（Definition of Done）

当满足以下所有条件时，会话视为完成：
- [ ] 全部 106 个技能均位于 `skills/domain/skill-name/SKILL.md`
- [ ] 全部 106 个技能均具有包含经批准描述的有效 Agent Skills 前置元数据
- [ ] `registry.json` 已生成且有效
- [ ] `plugin.json` 已创建
- [ ] CI 工作流通过
- [ ] 全部 5 项手动测试通过
- [ ] `REVIEW.md` 经人工审阅且描述已应用
- [ ] 现有 MCP 服务器无回归问题（向后兼容性测试通过）
- [ ] 已编写 Playwright 测试套件，覆盖：技能发现、直接调用、注册表校验、插件清单校验
- [ ] 已在 `feature/agent-skills-v2` 分支发起 PR，准备合并审阅

---

*规范版本：1.0 — 2026 年 4 月*
*在通读本全文之前，请勿开始执行。*
