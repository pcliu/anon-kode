# Active Context

## Current Focus

*   Populating the initial Memory Bank based on project files (`package.json`, `README.md`, `.clinerules`).

## Recent Changes

*   Initialized all core Memory Bank files (`projectbrief.md`, `productContext.md`, `activeContext.md`, `systemPatterns.md`, `techContext.md`, `progress.md`).
*   Read `package.json` and `README.md`.
*   Updated `projectbrief.md` and `productContext.md` with information derived from `package.json` and `README.md`.

## Next Steps

*   Update `systemPatterns.md` based on project structure and README.
*   Update `techContext.md` based on `package.json` and README.
*   Update `progress.md` based on `package.json` and README.
*   Potentially analyze source code in `src/` for deeper insights if required.

## Active Decisions & Considerations

*   Using `package.json` and `README.md` as the primary sources for initial Memory Bank population.
*   Following the Memory Bank structure defined in `.clinerules`.

## Important Patterns & Preferences

*   The project is a Node.js CLI application using TypeScript.
*   Uses `pnpm` for package management.
*   Uses `Ink` (React for CLIs) for the user interface.
*   Interacts with external AI models via OpenAI-style APIs.
*   Can function as both a standalone CLI and an MCP server.
*   Uses `commander` for command-line argument parsing.
*   Uses `prettier` for code formatting.

## Learnings & Project Insights

*   The project aims to integrate AI coding assistance directly into the developer's terminal workflow.
*   Emphasis on flexibility by supporting various OpenAI-compatible AI models.
*   Provides mechanisms for configuration (`/config`, `/model`).

## Agent Prompt 逻辑与工具调用策略

### Agent Prompt 设计

Anon Kode 使用一个结构化的 Agent Prompt 系统：

1. 主要 Agent Prompt 包含两部分：
   - 任务描述：简明直接的任务说明，避免冗长的引言和结论
   - 环境信息：包括工作目录、平台、日期和使用的模型等

2. 关键提示规范（在 `src/constants/prompts.ts` 中定义）:
   - 要求简洁直接的回答，适合命令行界面
   - 鼓励在需要时共享文件名和代码片段
   - 要求返回的文件路径必须是绝对路径
   - 避免不必要的解释或格式化

### 工具调用策略

Anon Kode 实现了高效的工具调用策略：

1. 工具可用性与限制（在 `src/tools/AgentTool/prompt.ts` 中实现）:
   - 通过 `getAgentTools` 函数确定可用工具集
   - 根据权限设置过滤可用工具（`dangerouslySkipPermissions` 参数）
   - 禁止递归代理调用（防止 Agent 调用另一个 Agent）
   - 当不跳过权限检查时，Agent 无法使用文件修改工具（如 BashTool、FileWriteTool、FileEditTool 等）

2. 工具调用执行方式（在 `src/query.ts` 中实现）:
   - 并行工具执行：当所有工具都是只读时，使用 `runToolsConcurrently` 并行执行，最多同时执行 10 个工具调用
   - 串行工具执行：当有非只读工具时，使用 `runToolsSerially` 按顺序执行
   - 工具执行前会进行输入验证和权限检查

3. 使用准则（在 Agent Prompt 中提供）:
   - 鼓励在可能时并发启动多个代理以提高性能 
   - 为搜索关键词或文件时使用 Agent 工具
   - 指导何时使用特定工具而非 Agent 工具（如读取特定文件时使用 FileReadTool）
   - 明确代理的无状态性质，强调详细任务描述的重要性

4. 输入规范化与权限检查:
   - 使用 `normalizeToolInput` 对特定工具输入进行标准化（如 BashTool 命令）
   - 在 `checkPermissionsAndCallTool` 中验证输入类型并检查权限

### 主要代码组件

1. `src/tools/AgentTool/AgentTool.tsx` - Agent 工具的核心实现
2. `src/tools/AgentTool/prompt.ts` - 定义 Agent 提示和工具可用性
3. `src/constants/prompts.ts` - 系统提示和 Agent 提示的定义
4. `src/query.ts` - 工具调用的执行逻辑
5. `src/tools.ts` - 所有可用工具的注册和管理

### 关键设计思想

- 简洁直接的交互风格，避免不必要的解释
- 根据任务类型智能选择工具执行方式（并行或串行）
- 严格的权限管理，确保只有授权工具可以修改文件
- 详细的工具使用指南，帮助 Agent 选择最适合的工具
