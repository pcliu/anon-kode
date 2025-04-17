anon-kode/
├── src/                     # 源代码目录
│   ├── components/          # UI组件
│   │   ├── binary-feedback/ # 二进制反馈组件
│   │   ├── CustomSelect/    # 自定义选择组件
│   │   ├── messages/        # 消息相关组件
│   │   ├── permissions/     # 权限相关组件
│   │   ├── PromptInput.tsx  # 提示输入组件
│   │   ├── Message.tsx      # 消息显示组件
│   │   ├── ModelSelector.tsx # 模型选择器
│   │   └── ...              # 其他UI组件
│   ├── constants/           # 常量定义
│   ├── commands/            # 命令实现
│   ├── entrypoints/         # 应用入口点
│   │   ├── cli.tsx          # CLI入口点
│   │   └── mcp.ts           # MCP入口点
│   ├── hooks/               # React钩子
│   ├── screens/             # 应用屏幕/页面
│   ├── services/            # 服务实现
│   ├── tools/               # 工具实现
│   │   ├── AgentTool/       # 代理工具
│   │   ├── ArchitectTool/   # 架构工具
│   │   ├── BashTool/        # Bash工具
│   │   ├── FileEditTool/    # 文件编辑工具
│   │   ├── FileReadTool/    # 文件读取工具
│   │   ├── FileWriteTool/   # 文件写入工具
│   │   ├── GlobTool/        # 全局匹配工具
│   │   ├── GrepTool/        # 文本搜索工具
│   │   ├── MCPTool/         # MCP工具
│   │   └── ...              # 其他工具实现
│   ├── utils/               # 实用工具函数
│   ├── context.ts           # 上下文处理
│   ├── commands.ts          # 命令定义
│   ├── messages.ts          # 消息处理
│   ├── permissions.ts       # 权限管理
│   ├── query.ts             # 查询处理
│   └── tools.ts             # 工具定义
├── .github/                 # GitHub配置
├── .vscode/                 # VSCode配置
├── tsconfig.json            # TypeScript配置
├── package.json             # 项目依赖管理
├── pnpm-lock.yaml           # pnpm锁文件
├── README.md                # 项目说明文档
├── CHANGELOG.md             # 变更日志
└── LICENSE.md               # 许可证文件 