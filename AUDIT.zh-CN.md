# Codex 兼容性审计

> 历史记录：下文中的计数、拟议布局及“v2/1.0”标准表述描述的是早期项目状态。关于当前的源文件/便携版契约及已验证边界，请以[开发者指南](docs/AGENT_SKILLS.md)和[2026 年 10 月 22 日构建回执](docs/audits/agent-skills-build-verification-2026-10-22.md)为准。本说明仅保留历史文本。

**日期：** 2026-05-10  
**范围：** 针对当前仓库结构与 OpenAI Codex / agentskills.io 要求的只读审计。  
**未修改任何文件。**

---

## 1. 当前结构

### 顶层文件与目录

```
education-agent-skills/
├── .claude-plugin/          # Claude Code 插件清单
│   ├── marketplace.json
│   └── plugin.json
├── .github/                 # GitHub Actions CI
│   └── workflows/
│       └── validate.yml
├── .gitignore
├── CLAUDE.md                # Claude Code 会话入口指南
├── README.md
├── education-agent-skills-skills-only.zip   # 预构建归档包（未追踪）
├── education-agent-skills.zip               # 预构建归档包（未追踪）
├── docs/                    # 支持文档
│   ├── AGENT_SKILLS_V2_SPEC.md
│   ├── AGENT_SKILLS.md
│   ├── ARCHITECTURE.md
│   ├── EVIDENCE.md
│   ├── EXCLUSIONS.md
│   ├── IMPLEMENTATIONS.md
│   ├── PRIVACY.md
│   ├── REVIEW.md
│   ├── brief.md
│   └── migration-log.md
├── llms.txt                 # 面向 LLM 的技能库概览
├── mcp-server/              # MCP 服务器（TypeScript，部署于 Vercel）
├── node_modules/            # Playwright 测试运行器依赖（根目录）
├── package-lock.json
├── package.json
├── playwright.config.ts
├── registry.json            # 机器可读技能索引（自动生成）
├── schemas/                 # （空目录）
├── scripts/                 # Python 构建与校验脚本
│   ├── generate-registry.py
│   ├── validate-registry.py
│   └── validate-skills.py
├── skills/                  # 全部 131 个 SKILL.md 文件
├── test-results/
└── tests/
    └── skills-library.spec.ts
```

### 技能的精确文件路径模式

来自不同领域的三个典型示例：

```
skills/ai-learning-science/formative-assessment-loop-designer/SKILL.md
skills/historical-thinking/sourcing-skill-builder/SKILL.md
skills/montessori-alternative-approaches/prepared-environment-designer/SKILL.md
```

模式：`skills/<domain>/<skill-slug>/SKILL.md`  
每个技能位于独立目录中。每个目录仅包含 `SKILL.md`（无其他文件）。

### 技能文件总数

```
131 SKILL.md files
```

已验证：`find skills/ -name "SKILL.md" | wc -l` → `131`

各领域技能数量：

| 领域 | 数量 |
|---|---|
| ai-learning-science | 14 |
| ai-literacy | 7 |
| curriculum-alignment | 4 |
| curriculum-assessment | 13 |
| eal-language-development | 5 |
| environmental-experiential-learning | 6 |
| explicit-instruction | 5 |
| global-cross-cultural-pedagogies | 9 |
| historical-thinking | 10 |
| literacy-critical-thinking | 7 |
| memory-learning-science | 8 |
| montessori-alternative-approaches | 4 |
| original-frameworks | 8 |
| professional-learning | 10 |
| questioning-discussion | 4 |
| self-regulated-learning | 5 |
| wellbeing-motivation-agency | 12 |
| **总计** | **131** |

### 混杂在技能目录中的非技能文件

`skills/` 内部四处位置存在 `.DS_Store` 文件：

```
skills/.DS_Store
skills/original-frameworks/.DS_Store
skills/curriculum-alignment/.DS_Store
skills/curriculum-assessment/.DS_Store
```

这些是 macOS 元数据文件。它们未被 Git 追踪（已通过 `git ls-files skills/ --others` 确认），仅存在于磁盘上。技能文件夹内不存在其他非 `SKILL.md` 文件。

---

## 2. 当前 YAML 前置元数据

### 存在的字段（跨不同领域抽样 10 个技能）

检查的全部 10 个技能具有完全相同的字段结构。前置元数据在整个库中保持一致。字段分为两个区块，由注释分隔：

**区块 1 — Agent Skills v2 标准字段（在 v2 迁移期间添加）：**
- `name` — 小写短标识（slug），与父目录名称完全匹配
- `description` — ≤250 个字符，动作优先的触发描述
- `disable-model-invocation` — 布尔值
- `user-invocable` — 布尔值（所有检查的技能中均为 `true`）
- `effort` — 字符串（所有检查的技能中均为 `"medium"`）

**区块 2 — 既有技能库字段（原始 schema）：**
- `skill_id` — `"domain/slug"` 格式
- `skill_name` — 人类可读的显示名称
- `domain` — 领域短标识
- `version` — 语义化版本字符串（均为 `"1.0"`）
- `evidence_strength` — `"strong"`、`"moderate"`、`"emerging"` 或 `"original"`
- `evidence_sources` — 引用字符串数组
- `input_schema` — 包含 `required` 和 `optional` 数组的对象，每项包含 `{field, type, description}`
- `output_schema` — 包含 `type` 和 `fields` 数组的对象
- `chains_well_with` — 数组（大多数技能存在，部分可能缺失或为空）

**部分技能中存在的可选字段（非通用）：**
- `contributor` — 字符串（例如 `"Sean Hu"`、`"Gareth Manning"`）
- `tags` — 数组
- `teacher_time` — 字符串

### 差异与异常项

有两个技能具有不符合已定义枚举值（`"strong" | "moderate" | "emerging" | "original" | "practitioner"`）的非标准 `evidence_strength` 值：

- `ai-literacy/prompt-literacy-sequence-designer`: `evidence_strength: "low-moderate"`
- `professional-learning/panel-review`: `evidence_strength: medium`（未加引号，解析为字符串）

十二个技能设置了 `disable-model-invocation: true`：
```
ai-learning-science/cognitive-tutoring-architecture-designer
ai-learning-science/individual-spacing-algorithm-explainer
curriculum-assessment/formative-assessment-technique-selector
original-frameworks/coherent-rubric-logic-builder
original-frameworks/developmental-band-system-designer
original-frameworks/developmental-progression-synthesis
original-frameworks/dispositional-knowledge-assessment-designer
original-frameworks/learning-target-authoring-guide
original-frameworks/seeds-regenerative-inquiry-cycle
original-frameworks/self-determined-project-design-protocol
original-frameworks/single-point-rubric-designer
professional-learning/panel-review
```

### 一个完整的代表性前置元数据区块

摘自 `skills/memory-learning-science/spaced-practice-scheduler/SKILL.md`：

```yaml
---
# AGENT SKILLS STANDARD FIELDS (v2)
name: spaced-practice-scheduler
description: "Design a spaced retrieval schedule for any topic list and timeline. Use when planning units, term sequences, or revision programmes."
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/spaced-practice-scheduler"
skill_name: "Spaced Practice Schedule Builder"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Ebbinghaus (1885/1913) — The forgetting curve: exponential decay of memory without review"
  - "Cepeda et al. (2006) — Meta-analysis of 254 studies on distributed practice: optimal spacing depends on retention interval"
  - "Kornell & Bjork (2008) — Spacing and interleaving effects on learning"
  - "Carpenter et al. (2012) — Using spacing to enhance diverse forms of learning"
  - "Dunlosky et al. (2013) — Distributed practice rated high-utility learning strategy"
input_schema:
  required:
    - field: "topics"
      type: "array"
      description: "List of topics or concepts to be spaced across the schedule"
    - field: "timeline"
      type: "string"
      description: "Available teaching period (e.g. '6-week half-term' or 'Term 2: Jan 15 – Mar 28')"
    - field: "lessons_per_week"
      type: "integer"
      description: "Number of lessons per week for this subject"
  optional:
    - field: "assessment_date"
      ...
output_schema:
  type: "object"
  fields:
    - field: "schedule"
      type: "array"
      description: "Week-by-week schedule showing new teaching and spaced review slots"
    ...
---
```

### 技能是否包含 `name` 和 `description` 字段？

**是的。** 全部 131 个技能均包含这两个字段。它们是在 v2 迁移期间添加的（记录于 `docs/AGENT_SKILLS_V2_SPEC.md`）。这两个正是 Agent Skills 开放标准所必需的字段。

---

## 3. Codex 兼容性差距分析

### 标准要求

**agentskills.io 规范（开放标准）：**

必需前置元数据：仅需 `name`（≤64 个字符，小写字母/连字符/数字，必须与父目录名称匹配）和 `description`（≤1024 个字符）。所有其他字段均为可选，或置于 `metadata:` 映射下。

插件的预期目录布局：
```
plugin-root/
├── .codex-plugin/
│   └── plugin.json        ← Codex 插件打包必需文件
└── skills/
    └── <skill-name>/      ← 技能文件夹直接位于 skills/ 之下
        └── SKILL.md
```

`plugin.json` 最小必需字段：`name`（kebab-case 短横线命名）、`version`（语义化版本）、`description`、`skills`（指向技能目录的相对路径）。

**OpenAI Codex 插件文档**（developers.openai.com/codex/plugins/build）：

Codex 文档使用 `.codex-plugin/plugin.json` 作为插件清单位置，并确认为了兼容 Claude 风格，它们也会读取 `$REPO_ROOT/.claude-plugin/marketplace.json`。系统会扫描技能目录的直接子目录，要求每个直接子目录包含一个 `SKILL.md`。

### 所需的结构性变更

#### 问题 1：领域子目录（阻塞性问题）

**当前结构：** `skills/<domain>/<skill-name>/SKILL.md` — 两层深度  
**要求结构：** `skills/<skill-name>/SKILL.md` — 一层深度

`plugin.json` 指向 `skills/` 目录。agentskills.io 规范与 Codex 文档均表明技能扫描器会将技能根目录的每个直接子目录视为一个技能文件夹。在当前结构中，这些直接子目录是领域文件夹（如 `ai-learning-science/`、`curriculum-assessment/` 等）——其中没有一个包含 `SKILL.md`。因此 Codex 将找不到任何技能。

Codex 是否会递归扫描嵌套子目录尚未见于文档。规范的显式结构以及 `name` 必须匹配父目录的约束均假定了扁平布局。**这是最主要的结构不兼容问题。**

解决该问题有三种方案，各自存在不同权衡：

- **方案 A（扁平化）：** 将全部 131 个技能移至 `skills/<skill-name>/SKILL.md`。会在文件系统中丢失领域分组。需要更新 MCP 服务器、注册表生成器、CI、测试、README 以及所有路径引用。
- **方案 B（并行扁平目录）：** 创建 `.agents/skills/<skill-name>/SKILL.md` 作为符号链接或副本。保留现有结构，但增加维护负担（每个技能文件存在两份副本）。
- **方案 C（构建步骤）：** 添加脚本，从当前领域结构生成兼容 Codex 的扁平目录。面向 Codex 的副本为生成产物；唯一事实来源仍保留在 `skills/<domain>/`。

#### 问题 2：缺少 `.codex-plugin/plugin.json`

当前插件清单位于 `.claude-plugin/plugin.json`。Codex 查找的是 `.codex-plugin/plugin.json`。

现有的 `.claude-plugin/plugin.json` 内容：

```json
{
  "name": "education-agent-skills",
  "display_name": "Claude Education Skills Library",
  "version": "2.1.0",
  "description": "124 evidence-based pedagogical skills...",
  "author": { "name": "Gareth Manning", "url": "https://github.com/GarethManning" },
  "homepage": "https://github.com/GarethManning/education-agent-skills",
  "license": "CC BY-SA 4.0"
}
```

该文件**缺少 `skills` 字段**——即指向技能目录的路径。它也未严格按照要求使用语义化版本格式的 `version`。Codex 会读取该文件以兼容 Claude，但若没有 `skills` 字段则无法从中发现技能。

兼容 Codex 的 `.codex-plugin/plugin.json` 至少需要包含：

```json
{
  "name": "education-agent-skills",
  "version": "2.1.0",
  "description": "...",
  "skills": "./skills/"
}
```

#### 问题 3：技能短标识（slug）重复

有一个短标识同时存在于两个领域中：

```
skills/curriculum-assessment/critical-thinking-task-designer/SKILL.md  →  name: critical-thinking-task-designer
skills/literacy-critical-thinking/critical-thinking-task-designer/SKILL.md  →  name: critical-thinking-task-designer
```

在当前的领域命名空间结构中，该问题由 MCP 服务器的 `buildToolName()` 函数处理（它会检测重复短标识并用领域名加以限定）。在扁平化的 Codex 技能目录中，两者都会使用 `name: critical-thinking-task-designer`，导致其中一个覆盖另一个或引发加载错误。**在进行任何扁平化处理前，必须解决此冲突。**

### 所需的前置元数据变更

**无需修改。** Agent Skills 开放标准强制要求的两个字段——`name` 和 `description`——已在全部 131 个技能中存在。

现有的额外字段（`skill_id`、`domain`、`evidence_strength`、`input_schema` 等）虽非标准字段，但不会造成危害。agentskills.io 规范会忽略未知的前置元数据字段；如果需要严格合规，可将结构化元数据放入可选的 `metadata:` 映射下，但这并非阻塞项。

当前 `description` 上限为 250 个字符。agentskills.io 标准允许最多 1024 个字符——不存在截断问题。

`disable-model-invocation` 是 Claude Code/agent-skills 的扩展字段。Codex 中没有等效字段；Codex 在每个技能中使用 `agents/openai.yaml` 来配置调用策略。两者属于不同机制——并非阻塞项。

### 所需的新增文件

**实现最小可行 Codex 加载：**

1. 包含 `name`、`version`、`description`、`skills` 字段的 `.codex-plugin/plugin.json`

**实现推荐的插件分发：**

1. `.codex-plugin/plugin.json`（同上，外加用于市场列表展示的完整 `interface` 区块）
2. 解决领域子目录问题（上述三种方案之一）
3. 解决 `critical-thinking-task-designer` 短标识冲突

**可选的 Codex 专属补充（非必需）：**
- 仓库根目录下的 `AGENTS.md` — Codex 会查找该文件以获取仓库级指令
- 每个技能下的 `agents/openai.yaml` — 用于单技能调用策略（相当于 Codex 版的 `disable-model-invocation`）

### 使技能可在 Codex 中加载的最小变更

1. 创建包含 `"skills": "./skills/"` 的 `.codex-plugin/plugin.json` — **1 个新文件**
2. 解决领域子目录问题 — 可能需要：
   - 添加构建步骤以生成扁平化的 `.agents/skills/` 目录（新增 1 个脚本 + 131 个生成文件），或者
   - 测试 Codex 是否支持递归扫描（未见文档说明；可能无需修改即可工作）
3. 重命名两个 `critical-thinking-task-designer` 短标识之一 — **修改 2 个 SKILL.md + 重建注册表/打包产物**

### 规范插件分发的推荐变更

包含上述全部内容，外加：
- 带有 `interface` 区块（显示名称、分类、描述、Logo）的完整 `.codex-plugin/plugin.json`
- 彻底解决领域嵌套问题（长期来看方案 A 或 C 比方案 B 更整洁）
- 更新重命名后的批判性思维技能中的 `name` 字段
- 更新 `.claude-plugin/plugin.json` 以补充缺失的 `skills` 字段（同时也修复 Claude 插件发现问题）

---

## 4. 风险评估

### 哪些现有功能可能会被破坏

#### MCP 服务器（若移动技能则存在高风险）

MCP 服务器（`mcp-server/`）部署在 Vercel 的 `mcp-server-sigma-sooty.vercel.app/mcp`。它是**本仓库**的一部分，提供打包在 `mcp-server/src/skills.json` 中的预构建快照。

`skill-loader.ts` 第 55–56 行：
```typescript
const skillsDir = join(resolvedRoot, "skills");
// v2 structure: skills/{domain}/{skill-name}/SKILL.md
```

如果移除领域子目录层（方案 A），必须更新 `skill-loader.ts`。如果使用并行目录（方案 B/C），`skill-loader.ts` 不受影响。

`bundle-skills` 脚本同样从 `skills/` 读取。任何结构变更都需要：
1. 更新 `mcp-server/src/skill-loader.ts`
2. 重新构建 `mcp-server/src/skills.json`
3. 重新部署至 Vercel

#### CI 校验（中风险）

`.github/workflows/validate.yml` 硬编码了检查：
```bash
[ "$COUNT" -eq 131 ] || (echo "Expected 131 skills, found $COUNT" && exit 1)
```

任何改变技能数量或将 `SKILL.md` 文件移出 `skills/` 目录树的重构都会破坏 CI，直到更新计数为止。

`validate-skills.py` 脚本扫描 `skills/**/SKILL.md` — 无法找到位于 `.agents/skills/` 的文件。

`generate-registry.py` 脚本使用 `git ls-files -- skills` — 无法拾取位于新路径下的未追踪文件。

#### Playwright 测试套件（中风险）

`tests/skills-library.spec.ts` 中包含已经过时的硬编码预期数量：

```typescript
test("finds exactly 107 SKILL.md files", () => {
  expect(paths.length).toBe(108);  // ← expects 108, repo has 131
});
test("skills span exactly 14 domains", () => {
  expect(domains.length).toBe(14); // ← expects 14, repo has 17
});
test("registry contains 107 skills", () => {
  expect(registry.total_skills).toBe(108); // ← wrong for current state
});
test("plugin.json is valid JSON", () => {
  expect(plugin.version).toBe("2.0.0"); // ← .claude-plugin/plugin.json has "2.1.0"
});
```

该测试还引用了 `plugin.skills`（第 205 行）：
```typescript
const skillsDir = path.join(__dirname, "..", plugin.skills);
```

但当前的 `.claude-plugin/plugin.json` 没有 `skills` 字段，因此 `plugin.skills` 为 `undefined`。即使不做任何 Codex 相关改动，该测试套件目前在多个断言上也处于失败状态。**在当前状态下，该测试套件不是可靠的门禁。**

#### registry.json

由 `scripts/generate-registry.py` 使用 `git ls-files -- skills` 生成。如果技能移动至 `.agents/skills/`，必须更新生成器以扫描新路径，否则下次重新生成时注册表将变为空。

#### README.md

直接引用了技能路径：
- 第 153 行：`"Example:** Open `skills/memory-learning-science/spaced-practice-scheduler/SKILL.md`"`
- 第 323 行：`"git add skills/<domain>/<skill-name>/SKILL.md registry.json mcp-server/src/skills.json"`
- 多个领域表格链接指向 GitHub 上的 `skills/domain/` 路径

#### llms.txt

引用了 v2 之前的旧路径（不带 `skills/` 前缀的领域根目录，例如 `memory-learning-science/` 而非 `skills/memory-learning-science/`）。相对于当前结构，该文件已经过时。

### 引用当前技能路径的文件

| 文件 | 引用类型 | 路径变更时的影响 |
|---|---|---|
| `mcp-server/src/skill-loader.ts` | 代码 — 扫描 `skills/{domain}/{slug}/SKILL.md` | **高** — 服务器中断 |
| `mcp-server/src/skills.json` | 生成的打包快照 | **高** — 必须重新构建 |
| `scripts/generate-registry.py` | 代码 — `git ls-files -- skills` | **高** — 注册表变空 |
| `scripts/validate-skills.py` | 代码 — `glob("skills/**/SKILL.md")` | 中 — 校验会跳过新路径 |
| `scripts/validate-registry.py` | 代码 — 校验路径是否以 `skills/` 开头 | 中 — 产生误报失败 |
| `tests/skills-library.spec.ts` | 代码 — `SKILLS_DIR = "../skills"` | 中 — 测试失败 |
| `.github/workflows/validate.yml` | CI — `find skills/ -name "SKILL.md"` | 中 — 数量检查失败 |
| `README.md` | 文档 — 多处路径示例 | 低 — 外观层面 |
| `llms.txt` | 文档 — 过时路径（本就已过时） | 低 |
| `registry.json` | 生成产物 — `path` 字段中的路径 | 自动重新生成，非手动编辑 |

### MCP 服务器位于本仓库内还是其他地方？

MCP 服务器位于**本仓库内部**的 `mcp-server/` 目录下。它单独部署至 Vercel，但其源码属于本仓库的一部分。Vercel 部署读取的是 `mcp-server/src/skills.json`（预构建快照），而非实时的 `skills/` 目录。任何技能内容的修改都必须执行 `cd mcp-server && npm run bundle-skills` 才能在已部署的服务器上生效。

---

## 5. 工作量评估

### 最小可行 Codex 兼容性（技能可被 Codex 加载）

**需要创建或编辑的文件：**

| 操作 | 文件 | 备注 |
|---|---|---|
| 创建 | `.codex-plugin/plugin.json` | 1 个新文件，约 10 行 |
| 编辑 | `skills/curriculum-assessment/critical-thinking-task-designer/SKILL.md` | 重命名短标识以解决冲突 |
| 编辑 | `skills/literacy-critical-thinking/critical-thinking-task-designer/SKILL.md` | 重命名短标识或修改 `name` 字段 |
| 重建 | `registry.json` | 运行 `python3 scripts/generate-registry.py` |
| 重建 | `mcp-server/src/skills.json` | 运行 `cd mcp-server && npm run bundle-skills` |
| 编辑 | `.github/workflows/validate.yml` | 更新技能数量（可选，否则 CI 会失败） |

**涉及文件总数：3 个新建/编辑的技能/清单文件 + 2 个生成产物。**

**未解决的阻塞项：** Codex 在扫描 `./skills/` 时是否会递归进入领域子目录。如果不支持递归，无论 `plugin.json` 如何配置，技能都无法加载。在宣称达到最小可行状态前，必须对此进行实测验证。

### 完整插件打包（在 Codex 市场上规范分发）

**在最小可行基础上额外涉及的文件：**

| 操作 | 文件 | 备注 |
|---|---|---|
| 决策 + 实施 | 领域子目录解决方案 | 方案 A/B/C — 见第 3 节。方案 A（扁平化）涉及 131 个 `SKILL.md` 路径。方案 C（构建步骤）增加 1 个脚本。 |
| 更新 | `mcp-server/src/skill-loader.ts` | 仅方案 A（扁平化）需要 |
| 更新 | `scripts/generate-registry.py` | 仅当技能移至新根目录时需要 |
| 更新 | `scripts/validate-skills.py` | 路径扫描更新 |
| 更新 | `scripts/validate-registry.py` | 路径校验更新 |
| 更新 | `.github/workflows/validate.yml` | 技能数量与路径 |
| 更新 | `tests/skills-library.spec.ts` | 修复过时计数 + 添加 Codex 清单测试 |
| 更新 | `.claude-plugin/plugin.json` | 添加缺失的 `skills` 字段 |
| 更新 | `README.md` | 更新路径示例 |
| 重建 | `mcp-server/src/skills.json` | 重新构建打包产物 |
| 重新部署 | Vercel | 在重新构建打包产物后执行 |

**若采用方案 A（扁平化），涉及文件总数：** 约 145 个文件（移动 131 个 `SKILL.md` + 删除 14 个目录 + 约 10 个支持文件）  
**若采用方案 C（构建步骤），涉及文件总数：** 约 15 个文件（1 个新脚本 + 约 14 个支持文件，无需修改技能内容）

### 需人工审阅与可安全自动化的工作

**需要人工审阅：**
- 在领域子目录解决的方案 A、B、C 之间做出选择——这是对仓库用户的使用体验有影响的架构决策
- 重命名 `critical-thinking-task-designer` 短标识冲突——需要决定哪个领域的版本保留该名称
- 决定是重命名/合并，还是仅为冲突项添加 `name` 别名

**可安全自动化（在人工批准上述决策后）：**
- 创建 `.codex-plugin/plugin.json` — 纯 JSON 文件生成
- 向 `.claude-plugin/plugin.json` 添加 `skills` 字段 — 简单编辑
- 更新 `validate.yml` 中的 CI 技能计数 — 简单的 sed 替换
- 运行注册表与打包产物重建脚本 — 已在 `CLAUDE.md` 工作流中记录
- 若采用方案 C：编写扁平化构建脚本 — 简单的文件复制/符号链接生成

---

*审计完成。未修改任何文件（0 个）。*
