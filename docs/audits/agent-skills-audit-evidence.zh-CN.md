# Agent Skills 审计 — 证据与可复现性

2026-10-22。目标：`/Users/garethmanning/Github/education-agent-skills`，`main` 分支 `6bbbce418f82e11044009c9f3b7373a354de5bd0`。除四份请求的报告外均为只读审计。临时工具与构建位于 `/tmp/education-skills-audit-20261022/`；未在该处创建 Git 仓库。未更改任何已安装的插件设置、已提交源码、凭据、线上端点、邮件、包发布、推送或部署。

## 1. 权威来源与固定版本源码

| 来源 | 检查的标识/用途 |
|---|---|
| [Agent Skills 概览](https://agentskills.io) | 当前格式概览/发现/激活机制 |
| [官方规范](https://agentskills.io/specification) | 当前要求/建议/可选字段 |
| [上游仓库](https://github.com/agentskills/agentskills) | GitHub API main 提交 `69ef37e9424c0a7ea9dd2293b559e43ec8176379` |
| [固定版本规范](https://github.com/agentskills/agentskills/blob/69ef37e9424c0a7ea9dd2293b559e43ec8176379/docs/specification.mdx) | 前置元数据第 19–32 行、命名规则第 60–65 行；文件后半部分的渐进式披露/资源指南 |
| [固定版本校验器](https://github.com/agentskills/agentskills/blob/69ef37e9424c0a7ea9dd2293b559e43ec8176379/skills-ref/src/skills_ref/validator.py) | 允许列表第 15–22 行；额外键检查第 103–115 行；name/description 校验 |
| [固定版本解析器](https://github.com/agentskills/agentskills/blob/69ef37e9424c0a7ea9dd2293b559e43ec8176379/skills-ref/src/skills_ref/parser.py) | strictyaml 第 52–56 行；元数据字符串化第 61–62 行 |
| [参考 README](https://github.com/agentskills/agentskills/blob/69ef37e9424c0a7ea9dd2293b559e43ec8176379/skills-ref/README.md) | 明确的仅作演示免责声明；API/CLI 用法 |
| [官方客户端指南](https://agentskills.io/client-implementation/adding-skills-support) | 扫描位置属于约定；宽松校验属于客户端可选项；信任边界 |
| [Claude 清单文档](https://code.claude.com/docs/en/plugins-reference) | 清单路径、skills 数组、被忽略的键、CLI 校验 |
| [Codex 技能文档](https://learn.chatgpt.com/docs/build-skills) | `~/.agents/skills`；位于 `agents/openai.yaml` 的策略 |
| [Codex 插件文档](https://learn.chatgpt.com/docs/plugins) | 市场/安装及新会话行为 |
| [Codex 解析器源码](https://github.com/openai/codex/blob/a3d93e1e692f1144cf8685175a5d1f6bf7294f57/codex-rs/core-plugins/src/marketplace.rs#L677-L719) | 相对于根目录的路径规则；拒绝 ParentDir；固定于当前上游，未断言与本地二进制完全同构 |
| [Codex 清单源码](https://github.com/openai/codex/blob/a3d93e1e692f1144cf8685175a5d1f6bf7294f57/codex-rs/core-plugins/src/manifest.rs#L135-L140) | 清单 `skills` 接受字符串或数组 |
| [Codex 技能解析器](https://github.com/openai/codex/blob/a3d93e1e692f1144cf8685175a5d1f6bf7294f57/codex-rs/skills/src/parser.rs#L7-L20) | name/description/metadata 子集；不映射 Claude 调用标志 |
| [Codex 元数据源码](https://github.com/openai/codex/blob/a3d93e1e692f1144cf8685175a5d1f6bf7294f57/codex-rs/skills/src/metadata.rs#L35-L56) | 附属文件 `policy.allow_implicit_invocation` |

Web 工具打开了四个请求的 Agent Skills URL。GitHub `skills-ref` 目录树网页渲染失败；直接通过 GitHub API/raw 请求成功获取了固定提交处的完整参考包。部分 Claude Markdown 端点返回 403；渲染后的官方文档与原生 CLI 依然可用。一个猜测的 OpenAI 清单 URL 返回 404，未用作证据。当前 OpenAI 页面重定向至 `learn.chatgpt.com`。除固定提交外，未断言任何规范语义版本；参考包报告版本为 `0.1.0`。

## 2. 命令与结果

命令均已脱敏显示。写入派生状态的命令仅在临时目录中运行。项目脚本在执行前均已阅读。

| 命令 / 范围 | 结果 |
|---|---|
| `git status --short --branch`; `git remote -v`; `git rev-parse HEAD`; `git ls-remote origin refs/heads/main` | 干净的 main 分支；origin 正确；本地/远程均为 `6bbbce4…` |
| `git ls-files` 加文件系统 `SKILL.md` 搜索（排除 `.git`/`node_modules`） | 241 个受追踪文件；165 个技能；20 个领域；无未注册技能 |
| 阅读 AGENTS、CLAUDE、README、STATE、AUDIT、CONTRIBUTING、更新日志、docs 与清单 | 区分当前指令与历史材料；未将过时审计视为权威 |
| 通过 GitHub API/raw 下载固定版本参考包；安装前检查 pyproject/parser/validator/CLI | 已检查源码；仅在临时虚拟环境中安装；包 0.1.0 以可编辑模式安装 |
| 在虚拟环境中执行 `python -m pip install -e <scratch>/standard/skills-ref pyyaml pytest` | 成功；校验器解释器 3.13.2；strictyaml 1.7.3；PyYAML 6.0.3 |
| 对每个实际技能调用参考 `validate(path.parent)` API | 0 通过 / 165 失败：160 个流式序列解析失败；5 个非预期键失败 |
| `skills-ref validate skills/professional-learning/panel-review` | 退出码 1；14 个非预期顶层字段；完整示例见下文 |
| 仅对允许字段执行隔离 `validate_metadata` | 165 通过；仅作诊断，**不代表**原始文件通过校验 |
| 在临时同名目录中将完整元数据重新序列化为块状 YAML，然后运行官方校验 | 165 个非预期字段失败；不再出现解析失败 |
| 参考包测试 `pytest -q -p no:cacheprovider <scratch>/standard/skills-ref/tests` | 40 项通过 |
| 虚拟环境 Python 运行 `scripts/validate-skills.py` | 退出码 0；165 通过；4 条长度警告 |
| 虚拟环境 Python 运行 `scripts/validate-registry.py` | 退出码 0；165 技能 / 20 领域 |
| 在根目录执行 `env -u HOSTED_MCP_BASE_URL npm test -- --output=<scratch>/root-test-results` | 21 项通过；1 项托管冒烟测试刻意跳过；共 22 项 |
| 在内存中对 `tracked_skill_paths` 应用生成器 `parse_skill` 并与注册表技能对比 | 165 条目精确匹配；165 个唯一名称；未重新生成时间戳 |
| 在临时追踪快照中执行 `env -u SKILLS_FILTER npm run bundle-skills`，然后与规范 `src/skills.json` 执行 `cmp` | 退出码 0；快照按字节完全一致 |
| 在原始 `mcp-server` 中运行 `./node_modules/.bin/tsc --noEmit` | 退出码 0；源码类型检查通过；无产物输出；当前配置排除了 `api/` |
| 针对现有被忽略的 `dist` 运行初始 `npm test -- --output=<scratch>/mcp-test-results` | 39 通过 / 3 失败：工具计数、缺失时间回退、标量类型；溯源为过时的被忽略本地输出 |
| 将 241 个受追踪文件复制到不含 `.git` 的临时目录；符号链接现有 `node_modules`；先 `npm run build` 再 `npm test -- --output=<scratch>/fresh-mcp-test-results` | 构建成功；42/42 项测试通过；未向线上服务器发起请求 |
| 通过 SDK stdio 客户端连接编译后的 `dist/cli.js`；列出工具/提示词；获取 `spaced-practice` 提示词 | 157 个工具；165 个提示词；选定提示词非空；客户端已关闭 |
| 使用伪造请求/模拟 Resend 运行独立的认证/处理程序专项测试 | 29/29 通过；未联系任何邮件或 HTTP 端点 |
| 根目录 `npm audit --json --package-lock-only` | 退出码 0；零安全通告 |
| MCP `npm audit --json --package-lock-only` | 退出码 1；10 条包记录：1 严重、2 高危、7 中危 |
| `claude --version`; `claude plugin validate . --json` | 2.1.307；退出码 0 伴随警告，精确摘要见下文 |
| `codex --version`; plugin/help 子命令; 在仓库运行 `codex plugin list --json --available --marketplace education-agent-skills` | 0.163.0-alpha.11.1；退出码 0，`installed[]`/`available[]` 均为空；未执行安装 |
| `hermes skills --help`; 检查 inspect 实现; 运行 `hermes skills inspect GarethManning/education-agent-skills/skills/original-frameworks/learning-target-authoring-guide` | 退出码 0；成功获取 name/description/metadata/SKILL 预览；报告来源为 `skills.sh`/社区；未安装 |
| 无害的合成解析器与替换探针 | JS 标记被执行；字面量输入被篡改；精确代码见下文 |

环境：Node 22.23.4，macOS arm64。系统 Python 报告为 3.15.0，临时虚拟环境实际为 3.13.2；请勿混淆。复用了现有依赖树；未声称执行过全新的 `npm ci`。基线根目录测试输出已在会话中捕获；临时目录中全新 MCP 日志为 `fresh-mcp-tests.log`。原始审计 JSON 与校验清单保存在临时目录，而完整的官方逐技能错误已持久化收录于 CSV 中。

审计环境搭建失误记录：一条临时构建命令在缺少 `package.json` 的临时父目录中运行并返回 ENOENT；在复制后的 `mcp-server` 目录重跑成功。一条编排表达式存在 JS 语法错误而未执行任何操作。导入注册表生成器时曾短暂生成 `scripts/__pycache__/generate-registry.cpython-313.pyc`；仅移除了该审计产生的字节码及其空目录，原始文件保持未动。后续 Python 调用均抑制了字节码生成。这些属于审计工具操作问题，而非仓库缺陷。

### 参考校验复现方法

```bash
# 在一次性存储中操作；安装前请固定至上述源码修订版本。
python -m venv /tmp/agent-skills-reference-venv
/tmp/agent-skills-reference-venv/bin/pip install -e /path/to/pinned/skills-ref
/tmp/agent-skills-reference-venv/bin/skills-ref validate /path/to/skill
```

批处理 API 使用的是官方 CLI 调用的同一公共函数：

```python
from pathlib import Path
from skills_ref import validate
repo = Path('/Users/garethmanning/Github/education-agent-skills')
results = {str(p.relative_to(repo)): validate(p.parent)
           for p in sorted(repo.glob('skills/**/SKILL.md'))}
print(sum(not errors for errors in results.values()), len(results))
# 0 165
```

代表性实际诊断输出：

```text
Validation failed for skills/professional-learning/panel-review:
Unexpected fields in frontmatter: chains_well_with, disable-model-invocation,
domain, effort, evidence_sources, evidence_strength, input_schema,
output_schema, skill_id, skill_name, tags, teacher_time, user-invocable, version.
Only ['allowed-tools', 'compatibility', 'description', 'license', 'metadata', 'name'] are allowed.
```

另外 160 个原始文件则在 `tags: [...]` 处因 strictyaml 报错 `Found ugly disallowed JSONesque flow mapping` 而失败。这是参考解析器的报错措辞；在 PyYAML/JS 解析器中数组属于合法 YAML。五个可解析的文件是：`coverage-audit`、`curriculum-crosswalk`、`developmental-band-translator`、`kud-chart-author`、`panel-review`。块状规范化仅作为**诊断性临时探针**，并非源文件编辑，也不证明仅靠规范化就能解决合规问题。

### 无害的安全/正确性探针

由独立检查员在 `mcp-server` 目录下执行，未修改任何技能文件：

```javascript
import matter from './node_modules/gray-matter/index.js';
import { assemblePrompt } from './src/tool-handler.ts';
globalThis.auditMarker = false;
const parsed = matter('---js\n(globalThis.auditMarker = true, { skill_id: "synthetic/probe" })\n---\n## Prompt\nSynthetic text');
console.log(JSON.stringify({javascriptExecuted: globalThis.auditMarker, parsedId: parsed.data.skill_id}));
const assembled = assemblePrompt({prompt:'Before {{topic}} After'}, {topic:'literal-$&'});
console.log(JSON.stringify({inputPreservedInTemplate:assembled.startsWith('Before literal-$& After'),actualTemplateLine:assembled.split('\n')[0]}));
```

使用 `node --import tsx --input-type=module` 运行，输出：

```json
{"javascriptExecuted":true,"parsedId":"synthetic/probe"}
{"inputPreservedInTemplate":false,"actualTemplateLine":"Before literal-[not provided] After"}
```

未尝试任何破坏性载荷、密钥读取、网络操作、内存耗尽测试或针对已部署服务的漏洞利用。

### 原生客户端观察结果

Claude 校验器成功并不等同于运行时激活测试。警告包括：忽略 `display_name`（应使用 `displayName`）、根目录 `CLAUDE.md` 未作为插件项目上下文加载；以及针对市场安装命令行的建议。目录配置文件警告包括缺少列表图标以及忽略本地 `.DS_Store` 文件。这些文件未被 Git 追踪；不声称它们随 GitHub 源码分发。原生校验器在此主要校验了市场/清单结构，而非 165 项教学法激活。

Codex 当前上游 `resolve_local_plugin_source_path` 在第 688 行将 `./` 特例处理为根目录；在第 706–714 行拒绝非规范路径组件。因此本地 `./../..` 在这些规则下无法解析。现有清单的 20 个领域根目录本身枚举了 165 个目录。上游同时具备递归与直接子目录发现模式；切勿将仓库旧有的单层断言当成开放标准要求。

Hermes inspect 通过 `skills.sh` 返回了 `learning-target-authoring-guide`、预期的 132+ 字符描述、标签与前置元数据预览。这验证了该运行时对该标识符的检索能力，但未验证已安装技能的激活或 tap 索引完整性。

## 3. 发现与源码映射表

以下所有仓库引用均相对于被审计修订版本。除非标明复现结果，否则均属于静态观察。

| 发现 | 文件/行号证据 |
|---|---|
| 扩展 schema 与官方允许列表对比 | 代表性文件 `skills/memory-learning-science/spaced-practice-scheduler/SKILL.md:1–67`；全部 CSV 行；项目 `scripts/validate-skills.py:84–104` |
| 源文件保留规则 | `AGENTS.md:7–15`；基础设施审计未编辑技能文件 |
| 过度宽泛的合规与厂商无关保证 | `README.md:3`；`docs/ARCHITECTURE.md:88–96`；`docs/AGENT_SKILLS_V2_SPEC.md:118–145`；`CHANGELOG.md:15–23` |
| 注册表生成/受追踪源码约定 | `scripts/generate-registry.py:82–98`；`registry.json`；内存一致性比对 |
| 正确的当前清单领域数组 | `.claude-plugin/plugin.json:12–33`；`.codex-plugin/plugin.json:7–28`；根目录测试第 224–247 行 |
| Codex 市场失败 | `.agents/plugins/marketplace.json:6–8`；固定上游解析器第 677–719 行；本地空列表 |
| Codex 安装文档缺口 | `docs/CODEX.md:20–54`；`README.md:49–57`；本地 CLI `add` 与 `marketplace-add` 帮助信息 |
| 仅显式调用控制 | 全部 12 个带标志行；`mcp-server/src/server.ts:90–92`；缺少附属文件；固定 Codex 策略解析器 |
| YAML 代码执行 | `mcp-server/src/skill-loader.ts:134`；锁定 `gray-matter` `mcp-server/package-lock.json:1131–1140`；已安装 `gray-matter/lib/engines.js:36–43`；无害标记探针 |
| 并行打包校验边界 | `.github/workflows/validate.yml:38–50` 独立的打包同步作业 |
| 字面量输入损坏 | `mcp-server/src/tool-handler.ts:5–16`；无害替换探针 |
| SDK 之前的 HTTP 认证 | `mcp-server/api/mcp.ts:32–55`；应用字节限制 `mcp-server/src/request-body.ts:4–7` |
| 无上限的数组元素计数 | `mcp-server/src/server.ts:22–25,46–49`；SDK 锁定于 `package-lock.json` 第 480+ 行 |
| 不受支持的元数据文档客户端通告 | `mcp-server/src/oauth.ts:110–121,143–150,169–179` |
| 凭据家族吊销局限 | `mcp-server/api/oauth/token.ts:54–63`；`src/http-auth.ts:22–25`；`src/oauth.ts:275–289` |
| 被忽略的过时 dist 与干净源码对比 | `mcp-server/.gitignore:2`；`package.json:15–22`；测试 `mcp-server.spec.ts:11–20`；39/3 与 42/0 对比 |
| API 类型检查缺口 | `mcp-server/tsconfig.json:15` 仅包含 `src`；处理程序运行时测试依然存在 |
| Dist 贡献者文档矛盾 | `CONTRIBUTING.md:84–90`；被忽略的 `dist` |
| MCP 语义 | `mcp-server/src/server.ts:51–86,90–112`；`src/tool-handler.ts:5–29`；返回指令，无模型/服务商调用 |
| 隐私/持久化输入边界 | 全部 13 个学生文件；`weekly-agency-review/SKILL.md:237`；`fading-manager/SKILL.md:254`；技能中无后端代码 |
| 良好的证据/能动性边界 | `README.md:185–192`；`docs/ARCHITECTURE.md:59–61`；五个原创框架编排器的证据空间/组件/综合/适用章节 |
| 许可意图 | 根目录 `LICENSE:5–8`；`mcp-server/LICENSE`；单个文件夹仅包含 `SKILL.md` |

## 4. 依赖证据与实际适用性

`npm audit --package-lock-only` 查询的是当前的公共安全通告，并非可利用性或已部署版本的证明。其十条受影响的**包记录**可能包含传递性扩散影响；它们并非十个独立的暴露端点。

| 包 / 严重程度 | 范围 / 锁定版本证据 | 评估 |
|---|---|---|
| `@modelcontextprotocol/sdk` / 高危 | 锁定 1.30.0；[GHSA-46jr-4wx8-v453](https://github.com/advisories/GHSA-46jr-4wx8-v453)，1.32.0 通过可选上限修复 | 与已认证 HTTP 校验风险相关；未证实在 1 MiB 下会发生崩溃 |
| `proxy-addr` / 严重 | 锁定 2.0.7；[GHSA-jqcg-44mw-7w3h](https://github.com/advisories/GHSA-jqcg-44mw-7w3h)，2.0.8 修复 | 需要存在畸形可信代理子网及代理身份使用；此处不存在 |
| `fast-uri` / 高危 | 锁定 3.1.6；[GHSA-qw65-cvwx-89v3](https://github.com/advisories/GHSA-qw65-cvwx-89v3)、[GHSA-58mr-gqgx-xq4g](https://github.com/advisories/GHSA-58mr-gqgx-xq4g)、[GHSA-hrr3-gc8f-f4qj](https://github.com/advisories/GHSA-hrr3-gc8f-f4qj) | 未表现出不可信 URI 目标/SSRF 用法；建议升级至 >=3.1.8 |
| `hono`、`qs`、`ip-address` / 中危 | 审计 JSON | 标记的 JSX/静态/代理辅助路径未被当前应用使用 |
| `gray-matter`、`js-yaml`、`argparse`、`sprintf-js` / 中危 | 审计 JSON；[sprintf 通告](https://github.com/advisories/GHSA-hp3w-g68c-fv3c) | 审计严重性为传递所致；解析器执行问题已单独复现且更直接 |

其他 SDK 通告涉及其客户端 OAuth/重定向路径、实验性任务以及 SDK Bearer 校验，而当前托管实现均未使用这些功能。项目自身的受众/资源范围属于另一问题，不能作为其自定义 Bearer 校验器存在该 SDK 缺陷的证据。请保留此区分。官方通告指出仅升级 SDK 仍会保持 `maxToolInputElements` 禁用；必须显式配置该参数。

## 5. 教育证据与抽样一手核查

| 观察项 | 仓库证据 | 一手来源 / 限定说明 |
|---|---|---|
| Cepeda 研究计数与排程主张 | `spaced-practice-scheduler:18,78,113,206` | [作者存档综述](https://escholarship.org/uc/item/3rr6q10c)：317 项实验 / 184 篇文章；未确立精确课堂时间表 |
| LLM 自我解释持久性/迁移夸大 | `explain-first-interrogator:23,67` | [预印本 v2](https://arxiv.org/html/2604.00142v2)：一项 60 分钟研究；子集上的解释质量结果；未证明长期持久性 |
| 将 CAST 2018 描述为最新版 | `differentiation-adapter:78` | [CAST 指南](https://udlguidelines.cast.org/)：3.0 版已于 2024 年发布；允许保留 2018 版作为具名历史依据 |
| Woloshyn 年份/页码有误 | `docs/EVIDENCE.md:39` | [ERIC 记录](https://eric.ed.gov/?id=EJ443903)：1992, 84(1), 115–124；[出版商 DOI](https://doi.org/10.1037/0022-0663.84.1.115) 屏蔽爬虫 |
| 2025 年元分析缺少可追溯性 | `srl-session-wrapper:23,73` | [可能的一手 Frontiers 论文](https://www.frontiersin.org/journals/education/articles/10.3389/feduc.2025.1738751/full)；识别与主张匹配需要明确作者/标题，未称之为捏造 |
| 安全保护（Safeguarding）路由缺口 | `trauma-informed-practice-designer:200,284–293` | 文件中无紧急分支；建议专家/本地政策审阅。[官方示例指南](https://enough.campaign.gov.uk/campaign-resources/guidance-and-resources-teachers-and-school-staff/safeguarding-children/local)将安全保护与常规关怀跟进区分开；未采纳为普适司法管辖标准 |
| 撤架（Fading）矛盾 | `fading-manager:101,111–117,195–203`; `retrieve-first-gate:148–155` | 内部状态/示例不匹配；阈值本身在 `fading:256` 处诚实标注为启发式规则 |
| 转换器矛盾中止 | `developmental-band-translator:25–41,126,148–152` | 内部静态矛盾，包括遗漏覆盖分支 |
| 上游 KUD 路由 | `kud-chart-author:129,141` 对比 `translator:83–85,101–106` | 元数据标注器需要已完成拆解的输入 |
| 未使用的已接收字段 | `srl-session-wrapper:33–35,78–84`; `teach-back-evaluator:33–35` | 孤立调用缺口；同对话上下文可能已提供相关信息 |
| 迁移目标/示例不匹配 | `transfer-bridge:177–236` | 市场价格目标对比分配算术；属于内部任务对齐观察，而非新的经济学研究 |
| 评级支撑/适用范围 | `academic-language-sentence-frame-generator:15–21`; `backwards-design-unit-planner:15–21`; `cross-cultural-task-validity-checker:15–21`; `panel-review:3,70,618`; `band-system-designer:79–85` | 这些条目未充分支撑已发布的 Strong 门槛；需要范围/措辞精细化，而非否定其教学法 |

完整教育内容检查覆盖了全部描述、元数据、局限性章节存在性、每个学生技能的重点内容以及代表性的被标记教育者工作流。检查未逐行通读全部 46,181 行，也未独立核实全部 872 条引用。未使用任何学生数据或教育干预试验。

## 6. 完整的可选串联/评级警告

| 文件:行号 | 提示信息 |
|---|---|
| `skills/ai-learning-science/erroneous-example-designer/SKILL.md:65` | 建议串联目标不在 165 个技能库中：`diagnostic-question-generator` |
| `skills/ai-learning-science/individual-spacing-algorithm-explainer/SKILL.md:64` | 建议串联目标不在 165 个技能库中：`retrieval-practice-designer` |
| `skills/ai-learning-science/learning-analytics-interpretation-guide/SKILL.md:61` | 建议串联目标不在 165 个技能库中：`retrieval-practice-designer` |
| `skills/ai-learning-science/learning-analytics-interpretation-guide/SKILL.md:62` | 建议串联目标不在 165 个技能库中：`diagnostic-question-generator` |
| `skills/ai-literacy/prompt-literacy-sequence-designer/SKILL.md:16` | 证据评级超出已发布的四值量表：`low-moderate` |
| `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md:75` | 建议串联目标不在 165 个技能库中：`competency-framework-mapper` |
| `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md:77` | 建议串联目标不在 165 个技能库中：`d2r-project-cycle-designer` |
| `skills/curriculum-assessment/formative-assessment-technique-selector/SKILL.md:64` | 建议串联目标不在 165 个技能库中：`exit-ticket-designer` |
| `skills/global-cross-cultural-pedagogies/cpa-sequence-designer/SKILL.md:65` | 建议串联目标不在 165 个技能库中：`diagnostic-question-generator` |
| `skills/global-cross-cultural-pedagogies/variation-theory-task-designer/SKILL.md:62` | 建议串联目标不在 165 个技能库中：`diagnostic-question-generator` |
| `skills/montessori-alternative-approaches/mixed-age-learning-task-designer/SKILL.md:65` | 建议串联目标不在 165 个技能库中：`peer-tutoring-protocol-designer` |
| `skills/montessori-alternative-approaches/three-part-lesson-designer/SKILL.md:65` | 建议串联目标不在 165 个技能库中：`retrieval-practice-designer` |
| `skills/montessori-alternative-approaches/uninterrupted-work-cycle-designer/SKILL.md:65` | 建议串联目标不在 165 个技能库中：`self-regulated-learning-designer` |
| `skills/original-frameworks/self-determined-project-design-protocol/SKILL.md:75` | 建议串联目标不在 165 个技能库中：`self-regulated-learning-designer` |
| `skills/professional-learning/panel-review/SKILL.md:11` | 证据评级超出已发布的四值量表：`medium` |
| `skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md:64` | 建议串联目标不在 165 个技能库中：`self-regulated-learning-strategy-selector` |
| `skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md:65` | 建议串联目标不在 165 个技能库中：`metacognitive-prompt-generator` |
| `skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md:64` | 建议串联目标不在 165 个技能库中：`self-regulated-learning-strategy-selector` |
| `skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md:65` | 建议串联目标不在 165 个技能库中：`metacognitive-prompt-generator` |

这些均为可选的建议串联；缺失目标并非被导入的可执行文件，不构成硬性依赖失败。两项评级标签虽被代码接受，但超出了已发布的四值描述范围。

### 渐进式披露超长异常项

| 技能路径 | 物理行数 | 正文空白分隔词数（非 token 数） |
|---|---:|---:|
| `skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md` | 594 | 6702 |
| `skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md` | 641 | 9999 |
| `skills/original-frameworks/learning-target-authoring-guide/SKILL.md` | 775 | 8416 |
| `skills/professional-learning/panel-review/SKILL.md` | 624 | 7542 |

共有 16 个正文超过 4000 词；5k-token 指导值不能仅靠统计词数或物理行数来验证。拆分前应先测量实际的客户端分词器开销。技能正文中未发现 Markdown 链接，也未打包脚本/资源；未观察到损坏的 Markdown 资源路径。文本层面的测试工具/会话数据要求依然重要。

## 7. 清单完整性与收尾

下表每一行均独立来自文件系统中的技能文件，并与注册表路径成员资格匹配。哈希标识被审计的字节；完整诊断与建议见 CSV。该附录也使得在 `main` 后续变更时仍可追溯恢复本次有界审计修订。

| 技能路径 | SHA-256 |
|---|---|
| `skills/ai-learning-science/adaptive-hint-sequence-designer/SKILL.md` | `4f59e3a5e681dbeb72db4c703a96f1dc53c44c4c9ec18df534071fcd7972882a` |
| `skills/ai-learning-science/ai-facilitated-collaborative-learning-designer/SKILL.md` | `06bf3fb287deb38eebbf0d5c46a392adcb876e03325e272af147046b1bee8b18` |
| `skills/ai-learning-science/ai-feedback-design-principles/SKILL.md` | `7a5306d9a9e72846b9816d79ce1fbb81a0ef579db72ad9f0c0f3b0bef532d585` |
| `skills/ai-learning-science/cognitive-tutoring-architecture-designer/SKILL.md` | `84616a953bed8ee536fe0c596cd1d3fa2f88337b56e0e009fd88dfe58fa7c019` |
| `skills/ai-learning-science/digital-worked-example-sequence/SKILL.md` | `2bae9a7d85bf2e5795eb89a8b117ce2076dd33a9c169adcccfaa9d1d9c38640a` |
| `skills/ai-learning-science/erroneous-example-designer/SKILL.md` | `36691fc700df204168c7e1a8c99e35460d12eda45aa5af2471acd4cbaeb80d3c` |
| `skills/ai-learning-science/formative-assessment-loop-designer/SKILL.md` | `f98a439600f9e8c8796113d24f195496e55d6f7013515fbe24d6d94f37d8b133` |
| `skills/ai-learning-science/individual-spacing-algorithm-explainer/SKILL.md` | `0fb15298648e560d9f9f444c9f1330c83c24245bb10222db6539821ed852575c` |
| `skills/ai-learning-science/intelligent-tutoring-dialogue-designer/SKILL.md` | `421294c1311588bdd0ed8b6a4a944835cee5df023883f39e399c9f692c0d6ee8` |
| `skills/ai-learning-science/learning-analytics-interpretation-guide/SKILL.md` | `4c5e8a351fcb017a2ae350ac0efc0f66bc69e6e9bba6c57467a4e55cbaa4ae73` |
| `skills/ai-learning-science/metacognitive-monitoring-ai-contexts/SKILL.md` | `3dcd03b8b6ce52d5e7156d7f39a5cb6940676db303cb0d357aa2d27351ed1f03` |
| `skills/ai-learning-science/productive-failure-desirable-difficulty-designer/SKILL.md` | `a2ba0f2b73c437dfe417c2f005734866efc6b829d03d0691d6b9105f50ca23a1` |
| `skills/ai-learning-science/self-explanation-prompt-designer/SKILL.md` | `d0e4c730e64be5e5a3718647f942ea99f3a5f201ff9ad20269884dec67126e32` |
| `skills/ai-learning-science/worked-example-to-problem-solving-transition-designer/SKILL.md` | `1d9474717c3aa505328368a2e76cf49e09ffd94f767f141c955b09543852a4a6` |
| `skills/ai-literacy/ai-expertise-interrogation-designer/SKILL.md` | `15eb41bdcfeb6157a9c7aeff89b82f1466418ef7175324d074e0623ea91db1d4` |
| `skills/ai-literacy/ai-hallucination-fact-check-protocol/SKILL.md` | `00a6622564fd94ded79bf9ee1c468a30eeac29a40b4628d8347425475a1dc1c9` |
| `skills/ai-literacy/ai-learning-boundary-mapper/SKILL.md` | `06c952800aa5430c50624f8127d8768647561c84d0711b1c776ff52ba3ba4796` |
| `skills/ai-literacy/ai-output-critical-audit-designer/SKILL.md` | `ff4f9b4fcadf61292fbd816a3869c8e692edf5b18a808e932893149a4177e21c` |
| `skills/ai-literacy/ai-socratic-dialogue-designer/SKILL.md` | `25983f25bbad2febf317b7056ca90fbb62b07e06647f48a320658349de61132b` |
| `skills/ai-literacy/disciplinary-ai-literacy-sequence-designer/SKILL.md` | `9539708990fdabd1659a691786ee7d7e5e983f4b0a6739fbdd7a787f1a163b39` |
| `skills/ai-literacy/prompt-literacy-sequence-designer/SKILL.md` | `7f30f154dd4d5350ee10a0269b91053f57cd6dfc2686f9abddba494a631cea6d` |
| `skills/curriculum-alignment/coverage-audit/SKILL.md` | `464d31856c3b441ee8b5f307b4b1903c50f299eac0eb363f2cf3a1adc3101c72` |
| `skills/curriculum-alignment/curriculum-crosswalk/SKILL.md` | `c1cba6e18242ca768b5c88f5463a390710ad3331b0461e8bf073e76ff9f0a821` |
| `skills/curriculum-alignment/developmental-band-translator/SKILL.md` | `b1879a0422ba0c9e68ddd74752466709d7e2327ccdedab29bd0b6599d2bd2f5e` |
| `skills/curriculum-alignment/kud-chart-author/SKILL.md` | `f597606246661031163dce8adb8abed9a7ddcd9be2daba3d6e1a8b826494bbcc` |
| `skills/curriculum-assessment/assessment-validity-checker/SKILL.md` | `7cd36cbcd1f57d5216931d1c231b3e8774e4b5c9fec42e9ee1cb689e457bf33f` |
| `skills/curriculum-assessment/backwards-design-unit-planner/SKILL.md` | `1436d874e706d5cb7ed01df8755af87ad221322baf853ca4306c964882ef686f` |
| `skills/curriculum-assessment/competency-unpacker/SKILL.md` | `f7491dd4e9c38cf707067f8e4b1818069c501f39963d3628852f65bdd7031b46` |
| `skills/curriculum-assessment/criterion-referenced-rubric-generator/SKILL.md` | `b8f404c14ad9e33b275be384e390dce7946268436dc1cefc9620317c2b0cbc70` |
| `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md` | `e3c6ea6c5c0786ee96bf1d81ee5d33d0d98e969bc73ac657cbeced6587571a18` |
| `skills/curriculum-assessment/differentiation-adapter/SKILL.md` | `6545b55ca01e6eea998b9c1c808f6327a3dee87c91a4c313c4c7e6e163c35c5f` |
| `skills/curriculum-assessment/discipline-specific-critical-thinking-task-designer/SKILL.md` | `0ff6183639481ed85168569c8369ac2212e55057f91737fd291149e3822c67eb` |
| `skills/curriculum-assessment/formative-assessment-technique-selector/SKILL.md` | `a8a824d8e4b0f067561e54af496c8b04ac4b1a386da0b2fb6775e7e8320fd41a` |
| `skills/curriculum-assessment/gap-analysis-from-student-work/SKILL.md` | `27428b49667ccbfed30ae854ad5fed2ca3fc5a0f4cf2f44701f5ba296fc71be6` |
| `skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md` | `8cd13e8b3ba6829d235aca41a2f3ff7966ab13f57d63a8fbdab1b54b368b6479` |
| `skills/curriculum-assessment/learning-progression-builder/SKILL.md` | `17e59b772ef0e249b7a392865c68c113d38d8cbf0c2c59fba0ce76c34d96bcd7` |
| `skills/curriculum-assessment/project-brief-designer/SKILL.md` | `14f314ee2575140998e26edf22d5e1818172353d9e150431be91e722c40a5345` |
| `skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md` | `20630a379803fb5023608904748531e3e03b3d9dad7d554901f0885ed5a9d9de` |
| `skills/eal-language-development/academic-language-sentence-frame-generator/SKILL.md` | `152ee91b124a9ba3d8076cbce0dc4129dd368b20e598713fdbf97e038bf51019` |
| `skills/eal-language-development/language-demand-analyser/SKILL.md` | `c273657a5ea300492ff59ea2feeb126b7b750d228336f1c1ad46a6e235282533` |
| `skills/eal-language-development/scaffolded-task-modifier/SKILL.md` | `0a10c9639107dc33408ee6edbb941200e777ef53af3578c3837cf70be8314ced` |
| `skills/eal-language-development/sheltered-instruction-lesson-modifier/SKILL.md` | `24fbd5379b52aa1bb097ecdd3fca2c9140a141bc589fbbaa4c5875151949a056` |
| `skills/eal-language-development/vocabulary-tiering-tool/SKILL.md` | `2211f0938d8933334414e61e603072566bba30337fd520069ebde977c40f7315` |
| `skills/environmental-experiential-learning/biophilic-learning-environment-designer/SKILL.md` | `eb6bdcc5d963e221bf895ccebef691c0c03c56bd9436ff4ee45f486e946bd9f1` |
| `skills/environmental-experiential-learning/ecological-inquiry-anchor-designer/SKILL.md` | `ed7ec7f699a4eb077319a00ec1e51431946beb925e2b78682d59bc633b4bc970` |
| `skills/environmental-experiential-learning/experiential-learning-cycle-designer/SKILL.md` | `7c294a08c999984058840b8ac0e7f31da273ffe5044dc1b35db69c6a3ab74c25` |
| `skills/environmental-experiential-learning/interdisciplinary-real-world-connection-mapper/SKILL.md` | `983baacf84cb824c632259b51ca4b90143e77c7418974e1d8f77a701391a466f` |
| `skills/environmental-experiential-learning/outdoor-learning-sequence-designer/SKILL.md` | `12b0d293777020f77995a77fbe3662ae33ee46c7fc57a5b4a99c2ae4c25c4bf1` |
| `skills/environmental-experiential-learning/service-learning-project-designer/SKILL.md` | `129563ace2290a594d5572026b1e48e7ec142e14c6b084219edcce5d71646c8b` |
| `skills/explicit-instruction/checking-for-understanding-protocol-designer/SKILL.md` | `a6a3f5452edece0c826458e3a399ae3ced849b5035899b16d5debb192e011ffc` |
| `skills/explicit-instruction/explicit-instruction-sequence-builder/SKILL.md` | `ddaa316c3d41822032b42c6b8a436d1200c86c9da7ae0c4aa25dc4fb1d1e7f58` |
| `skills/explicit-instruction/lesson-opening-designer/SKILL.md` | `fd00e8c5f8220e5935bb12511e6682a9d4e4a7fcfa2d6c726c18f97d56863b6e` |
| `skills/explicit-instruction/practice-problem-sequence-designer/SKILL.md` | `3bcf66d76461040cf92e325f4466aef34d4c675eae4d2d4c61950e6dc79654e2` |
| `skills/explicit-instruction/think-aloud-script-generator/SKILL.md` | `74475c4835796cdff710bb3937e5a9dfd326c7089e35e2e620b09f4ad43fd1bd` |
| `skills/global-cross-cultural-pedagogies/cpa-sequence-designer/SKILL.md` | `a941c9c7d8c8d91b3bcdca4d45e75d84154b6503d05ca35026b1da308c8b4899` |
| `skills/global-cross-cultural-pedagogies/cross-cultural-task-validity-checker/SKILL.md` | `dee9dae43391d773e3859d275619da68dbd21f78313e99ae5cd3ef333c70a146` |
| `skills/global-cross-cultural-pedagogies/culturally-responsive-teaching-designer/SKILL.md` | `abf5069c378c3f4bc6e8946cad7d301c8070b82a14ba169f7aa7858609ed2adb` |
| `skills/global-cross-cultural-pedagogies/emergent-project-design-scaffold/SKILL.md` | `4e9abec96bbaad5bd68809b55b7146ef1b878684f36b9119e572e8e947e9729f` |
| `skills/global-cross-cultural-pedagogies/phenomenon-based-unit-anchor/SKILL.md` | `5dd8e05c56eacab51f54d4a9b1bbc9f15734d81da92df89f8fd168ac6d87c64d` |
| `skills/global-cross-cultural-pedagogies/place-based-inquiry-anchor/SKILL.md` | `935958ee6bcc5da410d45c6d7a1b3ea19d6961f07732eef2b7f824f41ee27cbb` |
| `skills/global-cross-cultural-pedagogies/reggio-documentation-protocol/SKILL.md` | `eb521689446e97c1a96b1b54b9e810f96e68d057c4db32683b6c387ae325861c` |
| `skills/global-cross-cultural-pedagogies/ubuntu-collective-knowledge-task-designer/SKILL.md` | `a9fdcacbbbc8915587a64cef8f6230a1afc08e760ca57fe03ab484f4d4f2f60a` |
| `skills/global-cross-cultural-pedagogies/variation-theory-task-designer/SKILL.md` | `f94f85e202278f54c6e56fcdc5385e22e7434082d7f42da286413108627a24d2` |
| `skills/historical-thinking/central-historical-question-evaluator/SKILL.md` | `a76c23ec6d7b894d29a3e5abf977402af38387ad6e4938221f0c233cbd434516` |
| `skills/historical-thinking/close-reading-skill-builder/SKILL.md` | `c1179e338bf45d1e8c5001278fc88a47c780bd2e6eacd2ab645e2ce2ebb197de` |
| `skills/historical-thinking/contextualisation-skill-builder/SKILL.md` | `2a97ca02b7bc14c846528b90e52432002d4d47128866c35e075a6755afcfb8a9` |
| `skills/historical-thinking/corroboration-skill-builder/SKILL.md` | `622a3578533bca6168474b8d9b2c9a0f778abb6c6e57a72498765f7f63494be5` |
| `skills/historical-thinking/document-based-lesson-designer/SKILL.md` | `3f4a2d1fcfe6c3939cb4de8176f916259ca87afb9d60644d70fbc9e4993f1792` |
| `skills/historical-thinking/historical-document-set-curator/SKILL.md` | `9cdcb821b2efa3905670e3eb1d898730af01ddbbb92a77d07e58bfe9717921f0` |
| `skills/historical-thinking/historical-source-adapter/SKILL.md` | `2f9ae1e36ecf08e5152fdfd97ae51d53a99f9984d63a83461c371f3942420e0d` |
| `skills/historical-thinking/historical-thinking-assessment-designer/SKILL.md` | `c986ed186ed8cb87158dfcbfdc3ca085b0d24d6d3c31c32dd93124244be5c564` |
| `skills/historical-thinking/historical-thinking-strategy-modelling-guide/SKILL.md` | `02ea30f406b632ccf4b8697b84e2a6e7daccb09db065ab86541cb139c0331a30` |
| `skills/historical-thinking/sourcing-skill-builder/SKILL.md` | `9c0d9fa57eb7cc247371d68ce4810a8aa581f85394e5d1cd513e6ccc392d33ee` |
| `skills/inclusive-design/udl-barrier-anticipator/SKILL.md` | `3b0883954fd5226de817c6a5d08cabb350b617c9d65b97b10279d8d2aa4de75f` |
| `skills/inclusive-design/udl-lesson-auditor/SKILL.md` | `08b15370a936cf573597afb5d67d5a792f5fa664935c623c5c1f0d9dd6042f29` |
| `skills/inclusive-design/udl-options-designer/SKILL.md` | `e6d7a582beb8c5ad5bd380901ad6c653fdca4feb6264aeeb877128a6c3b4c547` |
| `skills/literacy-critical-thinking/argument-structure-scaffold-generator/SKILL.md` | `01592cf7e32883f5f2ac1fdac62ff75d2b86b34246002264bd6a4a07bbb5e3f1` |
| `skills/literacy-critical-thinking/critical-thinking-task-designer/SKILL.md` | `d38ab41c685ef352246463aab8c53d1b774826dfc88031b43772c8e3b2910350` |
| `skills/literacy-critical-thinking/disciplinary-writing-scaffold/SKILL.md` | `bd48435ee210fe286ab74bfe73e4ceac613ba173f68ee754f7a55ab61490b846` |
| `skills/literacy-critical-thinking/media-literacy-deconstruction-protocol/SKILL.md` | `97671629913401df0e117600394aaad0662d4196d797ddd3a5601c94bd1fb9d0` |
| `skills/literacy-critical-thinking/reading-comprehension-strategy-selector/SKILL.md` | `73444b90e9d2e00ac1fa3300f44dc382884f7d8cee209c94c65ca5284d987341` |
| `skills/literacy-critical-thinking/source-credibility-evaluation-protocol/SKILL.md` | `cdf5a4d859aadb3785dddc10312e6b6706b4089b3aa3ff386349fa0f8eda65a7` |
| `skills/literacy-critical-thinking/text-complexity-analyser/SKILL.md` | `2fa015b1fe82bd2f0ecfd3052e7176ae61c4c46cd2a55cd412aa0d4c647b4081` |
| `skills/memory-learning-science/cognitive-load-analyser/SKILL.md` | `6368ddea1a5f1562f9c2b4ac070d489cbf1645ef312cb5d0eeb0c9dc40761b1c` |
| `skills/memory-learning-science/dual-coding-designer/SKILL.md` | `358ccdd979e57715d6a33460de746d09ccc6f96909fceb885c167501c5a8856f` |
| `skills/memory-learning-science/elaborative-interrogation-generator/SKILL.md` | `8b96a7a3a9cbeef9c63c92885a2b9267615ced74a8171f38146360880da5a02d` |
| `skills/memory-learning-science/feedback-quality-analyser/SKILL.md` | `1cf11373442d2a199137df4ea742870c0a4d4257c9512c484fc877284d4e3d2a` |
| `skills/memory-learning-science/interleaving-unit-planner/SKILL.md` | `e00d936d86dd777b57e20e27a5cde88381a8c80649be6e65666914a0fa0cca5b` |
| `skills/memory-learning-science/retrieval-practice-generator/SKILL.md` | `01182f519b7dfc6a5a204b3e49b26282f879f8b59d233fcaf1daafc3d7e43516` |
| `skills/memory-learning-science/spaced-practice-scheduler/SKILL.md` | `2718ed5b78cf3c4457a12aa5bfe53a9894f55c69d4a655049eee3f8413899bff` |
| `skills/memory-learning-science/worked-example-fading-designer/SKILL.md` | `4a1a18c559f1dcdb7b7d73b1ddc6031478a0deb30966b13aaeacb3c9186616c3` |
| `skills/montessori-alternative-approaches/mixed-age-learning-task-designer/SKILL.md` | `e8217eb6db39778ebf9f89fac0553ca47df2177bb76a58348a39ed51c0937feb` |
| `skills/montessori-alternative-approaches/prepared-environment-designer/SKILL.md` | `cc723ee79acc66d3d1ae66e35c0f149bfed9706ccf3db171417f98cc5b0d2f24` |
| `skills/montessori-alternative-approaches/three-part-lesson-designer/SKILL.md` | `605962b79b3a4efed95d5b99bfa277cf7ee15f79d2029a7a7b2b21c4d2804189` |
| `skills/montessori-alternative-approaches/uninterrupted-work-cycle-designer/SKILL.md` | `6f28dcb1e5a4088ab5de459d7caad81ae9bdea35220e65fc7a51c40c019e241b` |
| `skills/original-frameworks/assessment-design-orchestrator/SKILL.md` | `5434b12011c02ee249c4dcf64e55d2c09eea3d68912a9fe94ccf147c814db2d6` |
| `skills/original-frameworks/coherent-rubric-logic-builder/SKILL.md` | `a34dca38c15a7ef696c824e6d838fef06ba6616797f21bbe2f7660453e55a09f` |
| `skills/original-frameworks/compassionate-systems-awareness-orchestrator/SKILL.md` | `2d63a3558faf7a02cba60d7368591f0045bf955c2b01db30328a0453e788f654` |
| `skills/original-frameworks/developmental-band-system-designer/SKILL.md` | `6820236c419bd6f35a6a2e3461fe6c9ababe9e888f9dc0caaa08443254f52704` |
| `skills/original-frameworks/developmental-progression-synthesis/SKILL.md` | `fed3325d0e6e41792092ab53ad6f978a47ce4eda3591849af4e602c93c8bd06b` |
| `skills/original-frameworks/dilemma-navigation-for-education-design/SKILL.md` | `e0b42bbb0375bc308beba564518435cf53ce8d9be2cc38c0449e0b211aca1699` |
| `skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md` | `06748a891782204684b63fc81352af58bee8759fd4e40e02b9b056887d5ce76b` |
| `skills/original-frameworks/inclusive-design-orchestrator/SKILL.md` | `97e42e33c1ba372589561b67c185bfd4ffe60efc1000a837fe5943eec14ef19e` |
| `skills/original-frameworks/learning-target-authoring-guide/SKILL.md` | `18e3f6f69e3ee62a83b16340fa0301883add3db700e19821490b00866761eff1` |
| `skills/original-frameworks/multi-perspective-decision-wheel/SKILL.md` | `535c732396db8e1f77c0d1fc09fc5b50121c378072bcd470057b45dd56bcb3d0` |
| `skills/original-frameworks/place-based-curriculum-orchestrator/SKILL.md` | `46a89ffcb22e54dbf1fd434533a9ac4008fa9759d437bab9eee95e26d6bbde64` |
| `skills/original-frameworks/regenerative-project-design-orchestrator/SKILL.md` | `6353a953680276fa03cdea6758661f739168776849af817733adf3c9742ced72` |
| `skills/original-frameworks/scoping-for-transformative-learning-inquiry/SKILL.md` | `80e12a21f58394481f79dac179e9134d34796890a835efe1c8577fa9c1f064c4` |
| `skills/original-frameworks/seeds-regenerative-inquiry-cycle/SKILL.md` | `e5c63e581305f3aa5ed001934a4b287295755acb3983b6b44cf32730aa85009f` |
| `skills/original-frameworks/self-determined-project-design-protocol/SKILL.md` | `737567aa4d736febec637a767d68ca0ab72470308d9ec34beea35beacf16a16c` |
| `skills/original-frameworks/single-point-rubric-designer/SKILL.md` | `59d2d82803c308f04ac7756bc714fb981e2762b4446457fcca6739febb980200` |
| `skills/original-frameworks/three-horizons-learning-transition-mapper/SKILL.md` | `8fc937d164b8bf05fea3d382cae240e7f370bcb8f07b9651258b6ee4e9e7c76a` |
| `skills/professional-learning/competency-framework-translator/SKILL.md` | `9fd6bf1a6b1fd385789c70a6cdd9ef7646d558ca78273293d2a5d0978b5efbee` |
| `skills/professional-learning/instructional-coaching-conversation-guide/SKILL.md` | `824b7267290e6cc5174d0d9e6fa1af911e4369a55a8e09cba1c6f68f35553526` |
| `skills/professional-learning/lesson-observation-protocol-designer/SKILL.md` | `e203071fc7bca908012287dcd72ef06427ad89ad4bc9296d4b3db730399bc5ea` |
| `skills/professional-learning/lesson-study-cycle-designer/SKILL.md` | `b11d4b47ccf72d7a85d86a96b28c653828792ffcc4f732e229b46143a560ce68` |
| `skills/professional-learning/panel-review/SKILL.md` | `2eb97761fb0845075715819f695fc154a57e9a90cd82e80f55383b6304323255` |
| `skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md` | `f8a431f23538c5fda43b6eba12ea790e389646049dc24234d86ce5ba180808b5` |
| `skills/professional-learning/professional-development-session-designer/SKILL.md` | `d4b54ce8544e9728cf32b46d34ea1a80fcdde9aa5868b881a1fa848ac3fedf5b` |
| `skills/professional-learning/reflective-practice-prompt-generator/SKILL.md` | `cf27d702a91dbc1a3c3f022c13aa9ab04668ab380f6922700dba9d7d5624bbd4` |
| `skills/professional-learning/teacher-inquiry-cycle-designer/SKILL.md` | `5327cccaf7c05772d872abac30679aa8caf984b76a2e137570e858bea81568c7` |
| `skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md` | `bba497e20abdd748a52f32c7b4b18c4c8ba1ba212db8531fddac20c5f73558f1` |
| `skills/questioning-discussion/dialogic-teaching-move-generator/SKILL.md` | `dc395fb2be1efb11403ac65a21c496787cddfaf8483e4ec5745113146188936e` |
| `skills/questioning-discussion/discussion-protocol-selector/SKILL.md` | `e254c6d5178c0a036240b7a650204299949e00067f39da8a0c12b04fb24195ee` |
| `skills/questioning-discussion/hinge-question-designer/SKILL.md` | `a3d862c13b6d86065bebc8f1266d643e127c736a2e071107e35b3389da662fc6` |
| `skills/questioning-discussion/perspective-taking-designer/SKILL.md` | `1120fcc8a1d6e2973ce091aeadad82979f2450c60fc680f84b598676315fa470` |
| `skills/questioning-discussion/socratic-questioning-sequence-generator/SKILL.md` | `e7988cfff9a39d777a44fbc5c38f6d0684ae0a5d8a02c5037dbda3bdbd50a6dc` |
| `skills/self-regulated-learning/error-analysis-protocol/SKILL.md` | `c58a67e286c73a607ec7d24b86c6ec4a855829d43c5d32d094c387e46d2647b7` |
| `skills/self-regulated-learning/goal-setting-protocol-designer/SKILL.md` | `ab1e1523e63de50c7640705638dd183f4b16c6f8db883de7f3c552cd0eb2bedc` |
| `skills/self-regulated-learning/metacognitive-prompt-library/SKILL.md` | `1f3af35c0178ff4f1156a5ddf8fc7ce76622f9e3be08f0eff67ad7b74486e403` |
| `skills/self-regulated-learning/self-regulation-scaffold-generator/SKILL.md` | `8192adbc918764dc9f53ee30f67cf95a6056d3eaee6ef798ba9674e0233b6f5d` |
| `skills/self-regulated-learning/study-strategy-selector/SKILL.md` | `38f452e4c1c2c330816261e6fbff12aeffa9fabfda1fcd15676b0978de033491` |
| `skills/student-learning/ai-claim-checker/SKILL.md` | `03209658ad2be7c9b7ae5f5252ecda8be996afa5124a6fb895bf852c6c2dc0f9` |
| `skills/student-learning/confidence-calibration-check/SKILL.md` | `6df4825de26d60df14ef5566f8b35e17b58031d156996551fa34ffedf6e96db5` |
| `skills/student-learning/explain-first-interrogator/SKILL.md` | `aba08e222d596ede68b759d7adf2285d747eb37a2ccddcc573c28a0ef807b63f` |
| `skills/student-learning/fading-manager/SKILL.md` | `83681b24f6746e727480efdf657299f47fad1da9d858932bac2e3217a482b1d2` |
| `skills/student-learning/productive-failure-protocol/SKILL.md` | `981c2fbd183617787b40b094bbec3e76dc4630e9a73bc8797f51fb5c06b97c9f` |
| `skills/student-learning/progressive-hint-ladder/SKILL.md` | `5178e50cb0e4fd48e10dd6a0d16d1d884b805a2be0935989409030fb56274b55` |
| `skills/student-learning/retrieve-first-gate/SKILL.md` | `04bde0cc2ec1911ad45bcb3375763b977a7b92d87d760ed4886e5c8fe0ddae3c` |
| `skills/student-learning/srl-session-wrapper/SKILL.md` | `dd0dd6fecec960929755becfbe59a032f3d97cdc3868903f812adf2a4a524b4c` |
| `skills/student-learning/stuck-and-error-diagnosis-coach/SKILL.md` | `fb9f958472a5e8a712dd64653cb331dce737ac468a6e32868eabb340cb097473` |
| `skills/student-learning/teach-back-evaluator/SKILL.md` | `09c4d8639ccd8502c061fbf4a98a26203b60381de9da5054d50759dbe5bc87ee` |
| `skills/student-learning/transfer-bridge/SKILL.md` | `87b536419939a82c2f4bdef058a3250bc27643d2c4fa0c07bfe8ec871869b2f2` |
| `skills/student-learning/unassisted-evidence-checkpoint/SKILL.md` | `460a4d6d32b618859b5bc9de8fb148c97b5106d0b0139d6ecb6167536b808465` |
| `skills/student-learning/weekly-agency-review/SKILL.md` | `08082d91b2873907dbbce27c33fd5def5d928fa029c1425583aae03649b9cc65` |
| `skills/systems-thinking/agency-circles-for-systems-action/SKILL.md` | `96cf12fc8f23f924156feb73e1624edd7dccf1e50a3eaa16dec5184fb52f12dc` |
| `skills/systems-thinking/aspirational-systems-iceberg/SKILL.md` | `cd430b7410f250810a77c46fc192f6a0132023dcdbb442fdf09b39e787012b56` |
| `skills/systems-thinking/hexagon-complexity-mapper/SKILL.md` | `6b5524333b7c918accb93a417abd4ae25e39aa60bd4588ec55bb2c77b8d89e13` |
| `skills/systems-thinking/ladder-of-inference-reflection/SKILL.md` | `15068c44ce81c6868eaac7704fc0d925fe13a32affaf8018f3caeb272d5394ae` |
| `skills/systems-thinking/leverage-and-response-design/SKILL.md` | `e57be810949c12b97bab54e4cf4ff5457c4a0c4bbac38bdbf40d4add7a5dde5f` |
| `skills/systems-thinking/mental-model-mapper/SKILL.md` | `6b0234c7866f8ee0464c0c1bb2e84766d05cbff39e14f131ae484f8a0b24a63f` |
| `skills/systems-thinking/systems-awareness-iceberg/SKILL.md` | `4f1104d3f5f531d529e23eca26cc054065862a87e5906429dbd7f26b5b1c1f72` |
| `skills/systems-thinking/systems-wellbeing-impact-mapper/SKILL.md` | `58a5a777b15db43df3c39aa5830f6e3c8112513ce3d853b042faf31744693e83` |
| `skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md` | `3803c8bc63a828c42f7d5cd0429a3b8ebf8b29b6c424435005d47f06294fd2af` |
| `skills/wellbeing-motivation-agency/awe-wonder-experience-designer/SKILL.md` | `3249cc1879007f460f2ad52f078c9975a61c5450168b5fa1a5479036913d635e` |
| `skills/wellbeing-motivation-agency/belonging-classroom-culture-designer/SKILL.md` | `5d4c825c85b67b2e76a7300700141a34b72c36c2953b49810f9f9b582ae6c8fb` |
| `skills/wellbeing-motivation-agency/flow-state-condition-designer/SKILL.md` | `94714b077d4cce82fa4e1075ca4f532b79c1a9ffeba3728cfa2211e4ebe252e1` |
| `skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md` | `83819dfb83c3aeb253eab35292ca386e699a0363fced214cd2925adde51ee92d` |
| `skills/wellbeing-motivation-agency/motivation-diagnostic-task-redesign/SKILL.md` | `1b4717de6826f4cf803ef32f63cd4e854d3629165a28fc0e192aad38d358528e` |
| `skills/wellbeing-motivation-agency/perma-based-lesson-designer/SKILL.md` | `4fd5066f923dfafcbbad20561a5a6ec4572912ec05685b6c3fd9817a7f52c982` |
| `skills/wellbeing-motivation-agency/restorative-practice-protocol-designer/SKILL.md` | `7ec90a91b85fdd63fec0199ad624d7b7c4cb2e8829ee38d28c0bb051c7ff1fe9` |
| `skills/wellbeing-motivation-agency/ruler-emotional-literacy-sequence/SKILL.md` | `c6a079ba16320268ee52493686cbcd6dd9077ab72d88aaa850a47d5f92d36257` |
| `skills/wellbeing-motivation-agency/self-efficacy-builder-sequence/SKILL.md` | `3b66bdaef032d90bd840043301ba6454105e90d5c5de711a7a8310d031405a9c` |
| `skills/wellbeing-motivation-agency/trauma-informed-practice-designer/SKILL.md` | `26fc50ed988804a27fc34e01f3de8897b7ebed4e815f5c4299c7317919a6b71e` |
| `skills/wellbeing-motivation-agency/wellbeing-learning-connection-mapper/SKILL.md` | `ee8065c41aa3bb174ef457fc19d576a21115b94ef8352bf6db1822369e36da19` |

`docs/audits` 下仅四份请求的文件为交付物。源文件/正文/schema 迁移仍处于提案阶段。最终审计文件自检确认了 165 条唯一 CSV 路径、全部 165 条 `spec_valid=false`、可解析的 JSON 诊断数组、报告链接/文件引用以及无受追踪源文件差异。测试创建的 stdio 子进程均已关闭；未启动任何长期运行的服务；未发生任何部署活动。
