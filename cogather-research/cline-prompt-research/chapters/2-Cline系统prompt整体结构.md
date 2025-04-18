# Cline系统提示结构分析

## 2 Cline系统提示的整体结构

Cline系统提示（System Prompt）采用了高度模块化的设计架构，将复杂的AI指令体系划分为多个功能明确的模块。这种结构化设计使得AI助手能够清晰理解自身角色、可用工具及操作规范，从而在命令行环境中高效执行各类开发任务。

Cline的系统提示结构主要包含以下几个核心模块：
1. **身份定义** - 确立AI作为高技能软件工程师的角色定位
2. **工具使用** - 详细定义各类工具的使用方法、参数及示例
3. **MCP服务器** - 提供扩展功能的服务器配置和使用说明
4. **文件编辑指南** - 规范化文件操作的方法和最佳实践
5. **运行模式** - 区分计划模式和执行模式的不同工作流程
6. **能力清单** - 明确AI可执行的各类操作范围
7. **规则与限制** - 设定操作边界和安全准则
8. **系统信息** - 提供环境上下文
9. **工作目标** - 指导任务分析和执行流程
10. **用户自定义指令** - 允许灵活定制AI行为

这种分层结构使得系统提示既有明确的指导性，又保持了足够的灵活性，能够适应不同的开发场景和用户需求。

### 树状结构图展示
```
CLINE SYSTEM PROMPT
├── 身份定义
│   └── 高技能软件工程师身份声明
│
├── 工具使用 (TOOL USE)
│   ├── 工具使用格式规范
│   │   └── XML标签格式说明
│   │
│   ├── 可用工具列表
│   │   ├── execute_command
│   │   │   ├── 描述
│   │   │   ├── 参数 (command, requires_approval)
│   │   │   └── 使用示例
│   │   │
│   │   ├── read_file
│   │   │   ├── 描述
│   │   │   ├── 参数 (path)
│   │   │   └── 使用示例
│   │   │
│   │   ├── write_to_file
│   │   │   ├── 描述
│   │   │   ├── 参数 (path, content)
│   │   │   └── 使用示例
│   │   │
│   │   ├── replace_in_file
│   │   │   ├── 描述
│   │   │   ├── 参数 (path, diff)
│   │   │   ├── SEARCH/REPLACE块格式规则
│   │   │   └── 使用示例
│   │   │
│   │   ├── search_files
│   │   │   ├── 描述
│   │   │   ├── 参数 (path, regex, file_pattern)
│   │   │   └── 使用示例
│   │   │
│   │   ├── list_files
│   │   │   ├── 描述
│   │   │   ├── 参数 (path, recursive)
│   │   │   └── 使用示例
│   │   │
│   │   ├── list_code_definition_names
│   │   │   ├── 描述
│   │   │   ├── 参数 (path)
│   │   │   └── 使用示例
│   │   │
│   │   ├── browser_action (条件性显示)
│   │   │   ├── 描述
│   │   │   ├── 参数 (action, url, coordinate, text)
│   │   │   └── 使用示例
│   │   │
│   │   ├── use_mcp_tool (条件性显示)
│   │   │   ├── 描述
│   │   │   ├── 参数 (server_name, tool_name, arguments)
│   │   │   └── 使用示例
│   │   │
│   │   ├── access_mcp_resource (条件性显示)
│   │   │   ├── 描述
│   │   │   ├── 参数 (server_name, uri)
│   │   │   └── 使用示例
│   │   │
│   │   ├── ask_followup_question
│   │   │   ├── 描述
│   │   │   ├── 参数 (question, options)
│   │   │   └── 使用示例
│   │   │
│   │   ├── attempt_completion
│   │   │   ├── 描述
│   │   │   ├── 参数 (result, command)
│   │   │   └── 使用示例
│   │   │
│   │   └── plan_mode_response
│   │       ├── 描述
│   │       ├── 参数 (response, options)
│   │       └── 使用示例
│   │
│   ├── 工具使用示例
│   │   ├── 执行命令示例
│   │   ├── 创建文件示例
│   │   ├── 编辑文件示例
│   │   └── MCP工具使用示例 (条件性显示)
│   │
│   └── 工具使用指南
│       ├── 信息评估流程
│       ├── 工具选择策略
│       ├── 迭代执行原则
│       ├── 等待用户确认机制
│       └── 错误处理流程
│
├── MCP服务器 (条件性显示)
│   ├── 已连接MCP服务器列表
│   │   ├── 创建MCP服务器指南
│   │   │   ├── 环境理解
│   │   │   ├── 创建步骤
│   │   │   ├── 示例服务器代码
│   │   │   └── 配置文件设置说明
│   │   │
│   │   └── 编辑MCP服务器指南
│   └── MCP服务器不总是必要的
│
├── 文件编辑指南
│   ├── write_to_file工具
│   │   ├── 用途
│   │   ├── 使用场景
│   │   └── 重要考虑因素
│   │
│   ├── replace_in_file工具
│   │   ├── 用途
│   │   ├── 使用场景
│   │   └── 优势
│   │
│   ├── 工具选择指南
│   ├── 自动格式化考虑因素
│   └── 工作流程提示
│
├── 运行模式对比
│   ├── ACT MODE
│   │   ├── 可用工具
│   │   └── 工作流程
│   │
│   ├── PLAN MODE
│   │   ├── 可用工具
│   │   └── 工作流程
│   │
│   └── PLAN MODE详解
│       ├── 用途
│       ├── 信息收集流程
│       ├── 方案设计流程
│       └── 模式切换建议
│
├── 能力清单
│   ├── 命令执行能力
│   ├── 文件操作能力
│   ├── 代码分析能力
│   ├── 浏览器交互能力 (条件性显示)
│   └── MCP服务器能力 (条件性显示)
│
├── 规则与限制
│   ├── 工作目录限制
│   ├── 命令执行规范
│   ├── 搜索规则
│   ├── 项目创建规范
│   ├── 代码修改规则
│   ├── 用户交互规范
│   ├── 文件编辑规范
│   └── 浏览器操作规则 (条件性显示)
│
├── 系统信息
│   ├── 操作系统
│   ├── 默认Shell
│   ├── 主目录
│   └── 当前工作目录
│
├── 工作目标
│   ├── 任务分析方法
│   ├── 目标分解策略
│   ├── 工具使用流程
│   ├── 结果展示要求
│   └── 反馈处理机制
│
└── 用户自定义指令 (动态添加)
    ├── 语言偏好设置 (可选)
    ├── 设置自定义指令 (可选)
    ├── cline规则文件指令 (可选)
    └── cline忽略指令 (可选)
``` 