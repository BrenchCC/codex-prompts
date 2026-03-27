# codex-prompt

一个面向多代理协作场景的角色 Prompt 集合仓库。

仓库中的每个 `.md` 文件定义一个独立角色，例如需求分析、规划、执行、架构评审、代码审查、测试、文档编写与安全审查。它们适合用于：

- 为 AI 编码代理提供稳定的角色边界
- 将复杂任务拆分给不同职责的子代理
- 统一团队内的 Prompt 风格、输出格式与协作协议
- 复用一套可维护的角色模板，而不是为每次任务重复写系统提示词

## 仓库结构

当前仓库以角色文件为核心，未包含运行时代码：

- `analyst.md`：需求澄清与前置分析
- `planner.md`：工作计划生成与确认
- `architect.md`：只读架构分析与根因诊断
- `executor.md`：端到端实现与验证
- `critic.md`：计划审查与风险质疑
- `code-reviewer.md`：代码评审
- `build-fixer.md`：构建或编译错误修复
- `debugger.md`：问题定位与回归分析
- `test-engineer.md`：测试策略与测试补强
- `qa-tester.md`：交互式验证
- `writer.md`：README、注释与技术文档编写

此外还包含产品、设计、性能、安全、API、信息架构、UX、视觉分析、Git 等方向的专用角色文件。

## 角色分工

这些 Prompt 的核心思路不是“一个代理做所有事”，而是把职责边界写清楚。

典型协作链路如下：

1. `analyst` 先识别目标、约束和缺失信息
2. `planner` 生成 3 到 6 步的可执行计划
3. `critic` 对计划做挑战，提前暴露风险
4. `executor` 按最小可行改动实现需求
5. `architect` 或 `code-reviewer` 做只读复核
6. `verifier`、`qa-tester`、`test-engineer` 补足验证证据
7. `writer` 整理 README、迁移说明或交付文档

这种拆分方式尤其适合以下场景：

- 中大型仓库改动
- 需要严格验证和留痕的任务
- 希望减少“既规划又实现又审查”导致的角色混叠
- 希望把 Prompt 模板沉淀为团队资产

## 文件特点

多数角色文件包含以下内容：

- 角色定义：明确该角色该做什么、不该做什么
- 成功标准：约束产出质量
- 调查协议：先看代码还是先问用户、如何收集证据
- 工具使用建议：什么时候用搜索、诊断、测试、Git 等工具
- 输出格式：统一最终回复结构，便于集成
- Failure Modes：列出常见失误，降低代理跑偏概率

这使得每个角色既像“人格”，也像“执行 SOP”。

## 使用方式

你可以把这些文件直接当作代理的系统提示词、角色提示词，或者作为你现有代理框架中的模板库。

常见使用方式包括：

### 1. 直接复制

将某个角色文件内容复制到你的 Agent/System Prompt 中，例如：

```text
Use the prompt from `executor.md` as the worker's system instruction.
```

### 2. 作为多代理模板库

根据任务类型动态选择角色，例如：

- 需求不清时使用 `analyst.md`
- 用户明确要求“先出方案”时使用 `planner.md`
- 用户要求“直接修”时使用 `executor.md`
- 实现结束后再调用 `code-reviewer.md` 或 `verifier.md`

### 3. 作为团队 Prompt 规范

如果你在维护一套内部 Agent 工作流，可以把本仓库作为统一提示词来源，避免不同代理的行为风格不一致。

## 推荐工作流

对于非简单任务，推荐使用下面的顺序：

```text
analyst -> planner -> critic -> executor -> verifier -> writer
```

对于调试问题，推荐：

```text
debugger -> architect -> executor -> qa-tester
```

对于上线前检查，推荐：

```text
code-reviewer -> security-reviewer -> quality-strategist -> verifier
```

## 适用对象

这个仓库适合：

- 使用 Codex、Claude Code、Cursor、OpenAI Agents 或自建代理系统的开发者
- 想把 AI 协作过程模块化、可复用、可审计的团队
- 希望沉淀“角色级 Prompt 资产”而不是零散临时提示词的项目维护者

## 后续可扩展方向

如果你打算继续演进这个仓库，比较自然的方向包括：

- 增加 `examples/` 展示每个角色的输入输出示例
- 增加 `workflows/` 沉淀常见编排方案
- 增加版本记录，说明角色 Prompt 的变更历史
- 补充与具体平台的集成示例，例如 Codex、Claude Code 或自定义 orchestrator

## License

如果你准备公开分发，建议补充许可证文件，例如 `MIT` 或 `Apache-2.0`。
