# Code Agent Configuration

一个用于记录和维护我个人 AI code agent 配置的仓库。

这个仓库不再只是零散的角色 Prompt 集合，而是面向日常开发工作流的 agent 配置资产库。当前内容主要覆盖：

- `Codex` 的代理规则与行为约束
- `Claude` 的配置文件与偏好说明
- 一组可复用的角色 Prompt 模板

这些文件用于沉淀我在 AI 编码协作中的约定，而不是保存业务代码。

## 仓库结构

### `codex/`

存放 Codex 相关配置。

- `codex/AGENTS.md`：Codex 在本仓库中的行为规范、语言偏好、Python 编码约定、Conda 使用方式等

### `claude/`

存放 Claude Code 相关配置。

- `claude/CLAUDE.md`：Claude 的响应偏好与配置入口
- `claude/rules/preferences.md`：Claude 使用的代码风格与执行约定

### `prompts/`

存放按职责拆分的角色 Prompt 模板，用于多代理协作或按需切换角色。

当前包含的角色方向包括：

- 分析与规划：`analyst`、`planner`、`critic`
- 实现与修复：`executor`、`build-fixer`、`debugger`
- 审查与验证：`architect`、`code-reviewer`、`verifier`、`qa-tester`、`test-engineer`
- 产品与设计：`product-manager`、`product-analyst`、`designer`、`ux-researcher`
- 质量与专项能力：`security-reviewer`、`performance-reviewer`、`quality-reviewer`、`quality-strategist`
- 其他辅助角色：`writer`、`vision`、`researcher`、`git-master`、`style-reviewer`、`api-reviewer` 等

## 这个仓库记录什么

我会在这里维护与 AI code agent 协作有关的长期配置，例如：

- 响应语言、输出风格、个性化前缀
- Python 代码格式偏好
- Prompt 模板的职责边界
- 多代理协作时的角色拆分方式
- 不同 agent 的配置文件组织方式

它更接近一个个人 agent workspace profile，而不是通用 SDK 或应用项目。

## 使用方式

### 1. 作为个人配置仓库

把这里的文件同步到本地 agent 环境，用来统一 Codex、Claude Code 等工具的行为。

### 2. 作为 Prompt 模板库

按任务类型选择 `prompts/` 下的角色文件，作为 system prompt 或 worker prompt 的基础模板。

### 3. 作为可追踪的配置历史

通过 Git 记录各类 agent 配置的变更，方便回溯什么时候调整了规则、目录结构或协作方式。

## 适用场景

这个仓库适合我自己做以下事情：

- 统一不同 AI code agent 的行为习惯
- 维护稳定可复用的角色 Prompt
- 管理个人开发工作流中的 agent 配置
- 把临时经验沉淀成可版本化的配置资产

## 后续可以继续补充

- 增加不同 agent 的安装或同步说明
- 增加 `examples/` 展示 Prompt 实际用法
- 增加 `workflows/` 记录固定协作链路
- 增加变更日志，说明配置演进历史

## License

MIT License