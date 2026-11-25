# 安全 MCP 运行时 — 本地构建者报告

日期：2026-10-22。检出路径：`/Users/garethmanning/Github/education-agent-skills`。
分支：`codex/agent-skills-standards-quality-2026-10-22`。
基线/HEAD：`6bbbce418f82e11044009c9f3b7373a354de5bd0`。

## 结果

实施了有界的运行时/包修复并通过了本地检查。无提交、推送、发布、部署、托管调用、模型调用、学习者数据、数据库操作或子代理。协调器负责独立审阅/集成。本工作包未修改源技能、注册表、打包技能内容、根目录测试、根目录文档与插件清单。保留了并发未追踪的审计/任务文档。

## 变更内容

- `mcp-server/src/skill-loader.ts`：用直接引入的 `yaml` 2.9.1 替换 `gray-matter`。要求普通的起始/闭合 `---` 行，在无可执行引擎的情况下解析 YAML 核心数据，拒绝解析器警告/错误、自定义标签、别名/循环引用、复杂/非字符串映射键与非有限数字。失败时保留源文件路径。保留现有的提示词提取与运行时元数据校验。
- `mcp-server/src/tool-handler.ts`：对原始占位符 token 进行单遍回调替换，采用字面量大小写不敏感的参数键。传入值中的替换字符串、美元符号模式与 token 不会被二次解释；保留可选缺失 token 与现有的 Teacher Input 摘要。
- `mcp-server/src/server.ts`：SDK `maxToolInputElements` 显式设为 10,000。包含 1,000 条记录/每条 8 字段的虚构测试集连同根键共占用 9,004 个元素，留有 996 个元素的余量。独立的 1 MiB HTTP 请求上限保持不变。测试通过数组与嵌套对象两种形式验证恰好 10,000 个元素可接受、10,001 个元素被拒绝，随后确认服务器仍可正常响应。
- `mcp-server/src/oauth.ts`：移除了不受支持的 `client_id_metadata_document_supported` 通告；保留固定客户端 OAuth 行为。
- `docs/HOSTED_MCP_ACCESS.md`：澄清了精确令牌吊销与家族吊销、单实例/重启受限的重放状态、固定客户端支持以及参数/字节限制。
- `mcp-server/package.json` 与锁文件：将兼容 SDK 升级至 1.32.1，移除 `gray-matter` 及其旧 YAML 依赖链，添加 `yaml`，刷新受影响的兼容传递依赖，并添加 `prepack: npm run build`。
- 测试：新增 `skill-loader.spec.ts`、`tool-handler.spec.ts`、`packed-cli.spec.ts`；扩展 `mcp-server.spec.ts` 与 `oauth-handlers.spec.ts`。
- `mcp-server/LICENSE` 已存在。保留其原始条款与字节；打包冒烟测试验证了包含性与相等性。无许可决策或重新授权。

## 依赖证据与安装控制

2026-10-22 的最新 npm 注册表元数据报告 SDK 最新版为 1.32.1、YAML 最新版为 2.9.1。SDK 内存校验安全通告 [GHSA-46jr-4wx8-v453](https://github.com/modelcontextprotocol/typescript-sdk/security/advisories/GHSA-46jr-4wx8-v453) 要求同时满足 SDK >=1.32.0 与显式元素上限；仅升级仍会保持该防护禁用。已对照[维护者文档](https://eemeli.org/yaml/)核查 YAML 解析选项。

| 包 | 修改前 | 修改后 |
| --- | --- | --- |
| @modelcontextprotocol/sdk | 1.30.0 | 1.32.1 |
| yaml | 无 | 2.9.1 |
| fast-uri | 3.1.6 | 3.1.9 |
| proxy-addr | 2.0.7 | 2.0.8 |
| hono | 4.13.5 | 4.13.13 |
| ip-address | 10.5.0 | 10.7.4 |
| qs | 6.15.3 | 6.16.1 |

无无关的大版本升级。`npm audit` 最初报告 10 条受影响包记录：1 严重、2 高危、7 中危。最终审计：**所有严重程度均为 0 漏洞**，无需任何例外。

安装前，在仅锁文件解析后检查了每个新增/变更包的注册表生命周期脚本。SDK 有一个源码构建 `prepack` 钩子；`ip-address` 有 `prepack` 以及设置 Git hooks 路径的 `prepare` 钩子；`qs` 有一个 `prepack` 钩子；其他变更包无相关安装/准备/打包钩子。现有未变更的含安装钩子包为 `esbuild` 与可选 `fsevents`。所有依赖安装均使用 `--ignore-scripts`；未执行任何依赖钩子。项目自有的 `prepack` 有意仅执行本地 TypeScript 构建与技能快照复制。

## 命令与结果

运行时：Node v22.23.4、npm 10.9.9。除非另有说明，以下命令均在 `mcp-server` 目录运行。

| 命令/检查 | 结果 |
| --- | --- |
| 基线 `npm run build` | 通过 |
| 基线 `npm test -- --reporter=dot` | 42 项通过，耗时 3.3 秒 |
| 基线加载器快照，随后对元数据/提示词/描述/工具名称执行最终 Node `deepStrictEqual` | 165/165 精确匹配 |
| `npm view @modelcontextprotocol/sdk version dist-tags --json`、SDK 1.32.0/1.32.1 与 YAML 脚本/引擎元数据 | 已检查最新注册表数据 |
| 基线 `npm audit --audit-level=high --json` | 失败基线：10 条受影响包记录；摘要如上 |
| `npm install --package-lock-only --ignore-scripts --no-audit` | 通过 |
| `npm update fast-uri proxy-addr hono ip-address qs --package-lock-only --ignore-scripts --no-audit` | 通过 |
| 检查每个变更/新增版本的注册表包清单脚本 | 安装前完成；钩子记录如上 |
| `npm install --ignore-scripts --no-audit` | 通过 |
| `npm ls @modelcontextprotocol/sdk yaml fast-uri proxy-addr hono ip-address qs` | 解析版本与上表一致 |
| 最终 `npm run build` | 通过 |
| 最终 `npm test -- --reporter=dot` | **66 项通过，耗时 5.5 秒** |
| 保留原 LICENSE 后最终聚焦 `npm test -- --reporter=dot tests/packed-cli.spec.ts` | 1 项通过，耗时 2.9 秒 |
| 最终 `npm audit --audit-level=high` | **通过，发现 0 个漏洞** |
| `git diff --check` | 通过 |
| `git diff --name-only -- skills registry.json mcp-server/src/skills.json README.md tests` | 为空：受保护内容未变 |

一致性快照 `/tmp/education-mcp-baseline-parity.json` SHA-256：`9409053fc77a3daf0ceceb51c47121ccfc14af23a793fe4f9a4d212a054ebc95`。持久化回归测试覆盖将全部 165 条元数据、提示词、描述与工具名称同未变更的签入打包产物进行对比，排除特定于机器的文件路径。

新的解析器测试覆盖包括普通/流式/块状 YAML、CRLF、全部四种受支持的提示词布局、`js`/`javascript` 分隔符、缺失/畸形分隔符、可执行/自定义标签、类型化集合、循环别名、非有限数字、复杂键与重复键。标记断言证明被拒绝的 JS 输入未执行。字面量替换覆盖包括 `$&`、其他美元符号模式、`{{literal}}`、嵌套传入 token、键中的正则字符、大小写匹配与数组。

完整套件保留 165 个提示词、157 个工具（153 个技能工具加 4 个发现工具），以及 12 个不在工具中但可作为提示词使用的仅显式调用技能。既有的严格标量 schema、未授权快速失败、OAuth/刷新/吊销以及全部五项 HTTP POST 字节限制/413 检查均通过。

打包冒烟测试运行 `npm pack --pack-destination <temp> --json`，验证 TypeScript `prepack` 执行，解压 tarball，使用 `npm ci --ignore-scripts --prefer-offline --omit=dev --no-audit --no-fund` 安装锁定的生产依赖，移除可选的源码快照与仅安装用锁文件，随后从无关空目录与 `dist/cli.js` 握手。它列出 157 个工具/165 个提示词并调用 `list_skills`，不依赖源码树路径。仅允许从 npm 注册表获取依赖；子 CLI 接收不含托管/服务商凭据的精简环境。`finally` 块关闭客户端/传输并移除临时包存储。

## 已解决的失败与剩余局限

- 初次解析器编译失败，因为在读取 `tag` 前尚未收窄 YAML 访问器值的类型；改用库的类型化 `isNode` 检查后编译通过。
- 首次完整打包冒烟测试在严格 `--offline` 下失败，因为本机 npm 缓存中缺少未变更的 `zod` tarball。将仅离线安装替换为 `--prefer-offline`；脚本依然禁用。随后的完整套件与聚焦冒烟测试均通过。冷缓存打包测试可能会下载锁定的公共依赖，需要注册表访问权限。
- 此为本地实施/测试证据，而非托管发布或独立验收。测试环境为 Node 22；未单独运行 Node 20。现有的历史凭据兼容性、仅精确令牌吊销、实例本地重放/速率映射以及缺乏持久化家族吊销等特性仍按文档所述保持不变。
- 拒绝非核心 YAML/别名是有意为之；当前全部 165 个技能保持精确一致。未更改任何教育内容或前置元数据字段。
- 测试清理会关闭 stdio 子进程，无已启动的服务器/进程继续运行。本工作包无需付费服务或 Gareth 决策。

## 回滚

协调器可仅丢弃/回退列出的受追踪运行时/文档/测试/包变更，并移除三个新增的聚焦测试与本报告，同时保留并发文档。若回退依赖，请恢复先前的锁文件并在禁用脚本的情况下重新安装。不涉及任何数据库、托管配置、部署或技能内容回滚。
