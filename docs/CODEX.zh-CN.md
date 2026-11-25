# 在 OpenAI Codex 中使用 Education Agent Skills

本技能库可以直接从本地文件运行，无需依赖托管 MCP 服务器。你可以选择完整源码插件或仅复制选定的技能；安装文件无需进行付费模型调用。

## 完整源码插件

将[本仓库](https://github.com/GarethManning/education-agent-skills)克隆到你常用的仓库目录中，然后注册**并安装**它：

```bash
cd /absolute/path/to/education-agent-skills
codex plugin marketplace add "$PWD"
codex plugin add education-agent-skills@education-agent-skills
codex plugin list --marketplace education-agent-skills --json
```

注册操作使市场（marketplace）可用，`plugin add` 则安装其插件。该市场的本地 `source.path` 为 `./`（相对于仓库根目录）。`.codex-plugin/plugin.json` 保留了一个包含 **20 个领域目录**的数组，每个目录下存放具体技能文件夹；它并未指向单一扁平化的 `./skills/` 目录。

已于 2026 年 10 月 22 日使用 **codex-cli 0.163.0-alpha.11.1** 在全新隔离的 `CODEX_HOME` 及配置/缓存目录中完成测试（未复制凭据，也未运行模型）。注册、安装与列表查询均成功；列表输出显示 `installed: true` 且 `enabled: true`。安装后的缓存包含全部 **165 个技能文件**（与源文件完全一致）以及 **12 个策略附属文件**。这验证了本地打包与安装流程，但不代表模型选择或激活行为。

安装或更新后请开启新的 Codex 会话。如果你的桌面端仍保留旧的技能列表，请重载或重启客户端并开启新会话。隔离 CLI 检查未测试会话刷新与实际模型调用；客户端行为可能因版本而异。

## 选择性安装技能：扩展源文件或便携配置文件

规范源文件位于 `skills/<domain>/<skill-name>/`。其富格式前置元数据包含教育 schema、引用文献与厂商选项。插件使用的正是这一源文件配置。

对于要求遵循开放规范受限前置元数据的客户端，请下载 [v3.1.0 便携版 ZIP](https://github.com/GarethManning/education-agent-skills/releases/download/v3.1.0/education-agent-skills-portable-v3.1.0.zip)。解压后可在 `agent-skills/` 下找到 165 个文件夹及一份安装说明。复制所需的完整文件夹，例如：

```bash
mkdir -p ~/.codex/skills
cp -R agent-skills/spaced-practice-scheduler ~/.codex/skills/
```

复制前请先处理已存在的同名目标目录；切勿直接覆盖合并到已编辑的技能上，也不要多嵌套一层文件夹。使用下载包无需 Python 构建。维护者也可以按以下方式生成增量式便携配置文件：

```bash
python3 -m venv /tmp/education-standard-venv
/tmp/education-standard-venv/bin/python -m pip install -r requirements/standard-validation.txt
/tmp/education-standard-venv/bin/python scripts/export-standard-skills.py
/tmp/education-standard-venv/bin/python scripts/validate-standard-skills.py
```

`dist/agent-skills/<skill-name>/` 为自动生成目录且被 Git 忽略。便携配置文件 `education-agent-skills-portable-1` 是一个项目格式标签，独立于源文件 schema 与上游规范版本。其前置元数据包含 `name`、`description`、`license` 以及字符串值的 `education.*` 元数据。完整的原始元数据保存在 `references/education.json` 中；正文顶部有一条指向该文件的指令，随后按字节原样保留全部原始正文。每个导出的技能均包含仓库的 `LICENSE`，以及存在时的本地 `references/`、`scripts/`、`assets/` 和 `agents/` 资源。复制技能时请保留整个文件夹。

便携版安装示例（请替换为你需要的技能）：

```bash
mkdir -p ~/.codex/skills
cp -R dist/agent-skills/spaced-practice-scheduler ~/.codex/skills/
```

或者将 `skills/memory-learning-science/spaced-practice-scheduler` 作为扩展源文件复制。无论哪种方式，最终路径都应为 `~/.codex/skills/spaced-practice-scheduler/SKILL.md`；避免在其中嵌套领域文件夹。复制前请先清理或确认目标目录，以免命令静默创建出多余的嵌套文件夹。

导出器会拒绝重复的名称/ID、格式错误元数据、路径穿越名称、资源冲突以及符号链接（包括内部符号链接）。它会包含未追踪的新资源。它仅会替换自己生成的未修改输出（通过文件哈希回执识别）；若目标为任意目录或包含用户手动编辑的导出目录，则会拒绝覆盖。如果你需要保留经过编辑的导出结果，请使用 `--output /path/to/new-profile` 重新生成到新路径。回执记录的是输入文件哈希（包括工作区编辑和资源），而非宣称仅凭 Git HEAD 就能标识被评估的内容。

独立的项目校验器负责检查扩展源文件。官方参考门禁**仅检查便携版导出产物**，使用的是[固定于上游提交 69ef37e9424c0a7ea9dd2293b559e43ec8176379 的 skills-ref 0.1.0](https://github.com/agentskills/agentskills/tree/69ef37e9424c0a7ea9dd2293b559e43ec8176379/skills-ref)。其解析器接受的 YAML 子集比通用 YAML 更窄。通过该参考工具检查仅证明格式兼容性，不代表教育认证或模型行为表现。

## 仅显式调用（Explicit-only invocation）

共有恰好 12 个源技能设置了 `disable-model-invocation: true`。它们各自配有 `agents/openai.yaml`，内容为：

```yaml
policy:
  allow_implicit_invocation: false
```

这些附属文件告知 Codex 保留这些技能供显式调用，同时禁止隐式自动调用。其余 153 个技能没有此项限制。当你需要运行仅显式调用的工作流时，请使用显式技能请求（例如 `$panel-review`）。导出器会复制这些策略文件，并在富元数据中保留原始标志。

开放的 Agent Skills 格式**没有全局统一的仅显式调用控制机制**。其他客户端可能会忽略 Codex 附属文件及保留的厂商标志。切勿假定通过便携版校验就意味着所有客户端都会强制执行调用策略；在将仅显式调用的工作流安装到其他客户端前，请先确认该客户端的控制机制。隔离测试仅验证了策略文件与数量，未测试模型主动选择或拒绝技能的行为。

## 更新与故障排查

v3.1.0 版本中的源码插件版本号为 2.2.0。本地插件会被安装到缓存中。仅更新本地仓库检出目录并不能保证缓存已刷新。在有意识地更新本地克隆后，请移除并重新安装插件，随后检查其列表状态并开启新会话：

```bash
cd /absolute/path/to/education-agent-skills
git pull
codex plugin remove education-agent-skills@education-agent-skills
codex plugin add education-agent-skills@education-agent-skills
codex plugin list --marketplace education-agent-skills --json
```

对于基于 Git 的市场，`codex plugin marketplace upgrade` 可刷新市场快照；但仍建议核查已安装的插件并刷新会话。对于选择性复制的便携版副本，请下载当前发布版本或重新生成配置文件，并完整替换每个已安装的文件夹（替换前请先在其他位置保存你有意做的本地修改）。对于源文件副本，请从更新后的源文件完整替换每个文件夹。切勿将生成的导出产物当作第二套源码树直接手动编辑。

如果发现技能未被识别，请检查插件是否已安装并启用、每个配置的领域目录是否存在于安装缓存中，以及选择性复制的文件夹内是否直接包含 `SKILL.md`。存在时请保留 `references/education.json` 和 `agents/openai.yaml`。仅凭有效清单或成功的列表输出，不足以证明运行中的模型已经加载了某个技能。
