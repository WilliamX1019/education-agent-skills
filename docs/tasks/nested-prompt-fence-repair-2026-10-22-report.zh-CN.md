# 嵌套提示词围栏修复回执 — 2026 年 10 月 22 日

状态：候选方案已实施；聚焦提取检查与构建通过；独立只读审阅待定。Learning Target Authoring Guide 加载器提示词现已包含完整的原始方法，而非停在“Format:”处。未重写任何教育指令或元数据。生成产物集成、已安装客户端行为及发布仍在本工作代理职责范围之外。

检出路径：`/Users/garethmanning/Github/education-agent-skills`；分支：`codex/agent-skills-standards-quality-2026-10-22`；继承 HEAD：`6bbbce418f82e11044009c9f3b7373a354de5bd0` 加已验收的工作区编辑。已阅读 `AGENTS.md`、`CLAUDE.md`、`STATE.md`、有界修复简报以及组织报告和 ACCEPT 审阅。检查了相关 README/架构/排除约定。简报明确将生成产物集成与提交分配给协调器；本工作包的窄范围归属权取代了通用的仓库重新生成/提交工作流。

## 精确负责的变更

- `mcp-server/src/skill-loader.ts`：仅修改了 `extractPrompt` 中的围栏分支。它捕获起始反引号围栏长度，并仅在遇到具有完全相同围栏长度的完整闭合行（允许尾随水平空白与 LF/CRLF）时结束。行内反引号、更短/更长的围栏以及带有后缀文本的疑似闭合行均保留为提示词正文。既有的无围栏 h1/h2 回退代码未动。
- `skills/original-frameworks/learning-target-authoring-guide/SKILL.md`：仅将第 111 行与第 488 行的外层提示词分隔符从三个反引号改为四个反引号。第 207 行与第 237 行的内部三反引号围栏、完整模板、指令、参考资料、头部、示例与局限性保留精确字节。
- `mcp-server/tests/skill-loader.spec.ts`：通过导出的 `loadSkills` 与临时测试夹具新增九项提取回归测试。四个完整内容测试用例分别以 LF 和 CRLF 运行：常规围栏内容、嵌套三反引号模板、精确长度/整行闭合行为，以及在 EOF 处闭合。第九项断言实际指南提示词等于其整个外层围栏内的方法。既有的常规/System Prompt 与无围栏 h1/h2 测试保留。未导出任何生产辅助函数；过时的打包一致性断言保持未变。
- 本报告。

## 修改前即刻保留证据

编辑前，实际当前加载器加载并保存了全部 165 个技能（包括提示词以及原始解析的元数据/描述/工具名称）至 `/tmp/nested-prompt-fence-repair-20261022/before-loaded.json`。本工作代理还将全部 311 个 Git 可见工作文件的哈希清单保存至 `before-files.json`，并保存了三个现有负责文件的精确修改前副本。验证使用该已验收的脏树快照，而非 HEAD 或过时的生成包。

`/tmp/nested-prompt-fence-repair-20261022/check.mjs` 通过 `loadSkills` 加载修复后的源文件、比对所有记录，并断言修改后提示词等于原外层围栏之间去掉首尾空白的完整原始切片（原第 112–487 行）。这包含嵌套的指标模板、所有其余方法与输出规则以及最终检查清单。随后的顶层 `## Example Output` 与 `## Known Limitations` 章节被排除；提示词自身输出模板内的局限性指令保持包含。完整修改后源文件必须等于完整修改前源文件加上精确的两处指定分隔符替换。这些是完整字符串/字节断言，而非关键词存在性检查。

以下所有哈希均为 UTF-8 字节的 SHA-256。聚合运行时哈希使用按技能 ID 排序并经 `JSON.stringify` 与指定投影序列化的数组；同时也直接断言了相等性。

| 项目 | 修复前 | 修复后 |
|---|---|---|
| LT 提示词字符数（Unicode 码点；此处与 UTF-16 计数一致） | 9,498 | 23,993 |
| LT 提示词 UTF-8 字节数 | 10,556 | 26,001 |
| LT 提示词哈希 | `0cd4f6c0e36fb8277312c29144ed4614adbd24495eb1aac40c67fdc5f11aa582` | `0ba66d5fc85681152452f19f83bb617781b372119eb3ecaaabf7c23eb56c8f5b` |
| LT 完整源文件哈希 | `51b0eb995a87150cc9209cec07ac3c41e9f965159c77e483a395abcf8b477089` | `5be967515deace5c633f68d2c117bff90f7fc908fa0937d7aad938516763112e` |
| LT 原始 YAML 头部哈希 | `79912cb6b18588045945f91e51fabfa763f6df36dd0d069d2238d40aa8601259` | 完全一致 |
| 其余 164 条 `{skill_id, prompt}` 记录 | `6ad67b3da457375eb539d7920611dcf81301cf4a49e54ddc82c17d1d54887e6b` | 完全一致 |
| 全部 165 条 `{metadata, description, toolName}` 记录 | `05d568a1054005264b10cf6eec74d82687a2596bb4f3371017e24e713e8c26bc` | 完全一致 |

恰好只有一个已加载的提示词发生变更：`original-frameworks/learning-target-authoring-guide`。其修改后哈希同样等于原预期边界哈希。其余全部 164 个源 `SKILL.md` 文件与修改前即刻状态按字节完全一致；所有参考文件及非负责运行时/源文件保留其快照。对 `docs/tasks/library-introduction-2026-10-22.md` 的并发修改属于协调器（已在父级对话中确认）并予以保留。它被排除在本工作代理的增量之外，且由检查器明确披露。

组织报告依然作为历史记录保留。本回执仅取代其中“Learning Target 提取提示词一致性”的哈希/结果：此前未改动的截断提取为 `0cd4f6c…`，修正后的提取为 `0ba66d5f…`。其其余保留与组织发现保持完整。

## 命令与实测结果

除非另有说明，命令均在 `mcp-server/` 下运行。完整精确输出保留在 `/tmp/nested-prompt-fence-repair-20261022/`。

1. 编辑前，使用捕获脚本运行 `node --import tsx --input-type=module` 保存了全部 165 条已加载记录与工作文件清单。通过（PASS）；确认 LT 提示词确实止于“Format:”。
2. 基线 `npx playwright test tests/skill-loader.spec.ts --reporter=line`：17 项通过，1 项失败。既有失败项为 `all 165 metadata records and extracted prompts retain deep bundle parity`，因为已验收的源文件变更尚未集成到生成包中。日志：`baseline-tests.log`。
3. 编辑后，运行 `npx playwright test tests/skill-loader.spec.ts --grep-invert 'all 165 metadata records and extracted prompts retain deep bundle parity' --reporter=line`：26 项在 1.1 秒内通过。这保留了现有集成断言完整，仅剔除了已知的基线失败项。日志：`focused-tests.log`。
4. `npm run build`：通过（PASS）。现有脚本运行 TypeScript 编译并将现有源码包复制至被忽略的 `dist/skills.json`；未重新生成注册表/源码包/便携版导出。日志：`build.log`。
5. `node --import tsx /tmp/nested-prompt-fence-repair-20261022/check.mjs`：通过（PASS）。精确预期边界相等性、164 提示词字节一致性、165 元数据/描述/工具名称深度相等、原始头部相等、完整源文件仅双分隔符替换相等、其余 164 个源文件字节一致性以及范围内工作文件增量均通过。详细指标：`checks.json`；修改后加载记录：`after-loaded.json`。检查器首次运行时准确捕获了协调器并发编辑的引导简报；协调器确认归属权后，辅助脚本收窄范围以披露该已知非负责文件。未因聚焦测试或构建失败而需要实施修复。
6. 交接前已检查范围内空白字符检查与修改前即刻增量；结果附后。

## 局限与交接

未执行任何子代理、模型调用、托管请求、服务器/后台进程、真实客户端设置、注册表/导出重新生成、提交、推送、发布或部署。聚焦加载器测试仅运行了本地临时虚构夹具。不宣称任何学习收益、已安装客户端行为或线上修复。独立审阅待定；协调器随后负责已验收的生成产物集成与全套测试。本范围内审阅无需任何产品决策或新的创始人授权。

工作代理峰值：1；派生工作代理：0；继承历史例外：0；首次聚焦提取测试/构建：通过（PASS）；实施返工：无；Token/额度遥测：不可用。临时证据保留在仓库外部供协调器/审阅者使用。

最终空白字符检查结果：在仓库根目录运行 `git diff --check -- mcp-server/src/skill-loader.ts mcp-server/tests/skill-loader.spec.ts skills/original-frameworks/learning-target-authoring-guide/SKILL.md docs/tasks/nested-prompt-fence-repair-2026-10-22-report.md` 通过（PASS），新报告的尾随空白/末尾换行直接检查亦通过。修改前即刻 diff 检查确认加载器新增 4 行/删除 2 行、提取测试新增 28 行、LT 源文件新增 2 行/删除 2 行（仅限指定分隔符）。从修改前捕获到回执完成耗时约 164 秒（不含初始熟悉时间）。最初一条追加回执的命令误将 MCP 子目录作为工作目录而在写入前失败；改用绝对路径重试后完成。
