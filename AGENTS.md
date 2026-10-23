# Repository Instructions

- Use `main` as the base branch for this repository. Do not use `origin/master` for `unit-test-agent` work unless a user explicitly asks for it.
- Preserve unrelated local edits and generated reports when working in this repo; `.uta_reports` and `.uta_cache` are runtime artifacts, not application-source changes.
- Architecture invariant: different language backends must share the same abstraction layer. Core workflow, task, report, progress, and cost code should stay language-agnostic; Java/Python/other language behavior belongs behind language adapters or category packages such as `uta/batch/{language}`, `uta/language/{language}/parse`, `uta/language/{language}/verification`, and `uta/enforcement/{language}`.

## 五项目协作边界（2026-10-23）

跨项目职责、架构和问题路由以 `/Users/helloppx/GitHub/WFGameAI/docs/technical-docs/2026-10-23-五项目架构与协作说明.md` 为准。

- 本仓是独立的代码级单测生成与确定性门禁：Enforcement 负责测试执行、变更行覆盖率与 mutation evidence，Generation 生成/修复单测并必须服从该证据。
- 当前未找到 WFGameAI 运行时直接调用本仓；代码覆盖率/mutation 结果不能冒充游戏 UI 用例质量、FairyGUI/设备执行事实或业务 BUG 结论。
- 需要查业务测试点、Oracle、人工终审去 `/Users/helloppx/GitHub/WFGameAI`；查真实设备执行与 trace 去 `/Users/helloppx/GitHub/playbee-mcp`。
- 继续遵守语言适配器边界；新增 WFGameAI 接入前必须先固定跨仓契约、失败语义和在真实变更上的验证证据。
