# Cline系统提示结构分析

## 一、引言
### Cline项目背景与定位
### 研究目的与意义

## 二、Cline系统提示的整体结构
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
│   ├── 创建MCP服务器指南
│   │   ├── 环境理解
│   │   ├── 创建步骤
│   │   ├── 示例服务器代码
│   │   └── 配置文件设置说明
│   │
│   ├── 编辑MCP服务器指南
│   └── MCP服务器使用说明
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

## 三、核心部分详解
### 3.1 身份定义
#### 高技能软件工程师身份声明

系统提示中的角色定义部分是整个提示的开端和基础，为模型设置了整体行为框架。

```typescript
// src/core/prompts/system.ts 中的角色定义
export const SYSTEM_PROMPT = async (
  cwd: string,
  supportsComputerUse: boolean,
  mcpHub: McpHub,
  browserSettings: BrowserSettings,
) => `You are Cline, a highly skilled software engineer with extensive knowledge in many programming languages, frameworks, design patterns, and best practices.`
```

这段简洁的角色定义具有以下特点：

1. **身份建立**：通过简洁有力的语句"You are Cline, a highly skilled software engineer"建立了AI的核心身份，直接赋予了明确的名称和专业角色定位。

2. **专业能力界定**：紧接着通过"with extensive knowledge"引出了AI具备的专业能力范围，通过四个关键方面全面勾勒了其技术覆盖面：
   - 多种编程语言 (many programming languages)
   - 各类框架 (frameworks)
   - 设计模式 (design patterns)
   - 最佳实践 (best practices)

3. **设计亮点**：
   - **简洁精炼**：仅用一句话就完成了角色的全面定位，避免了冗长的描述
   - **专业导向**：强调"highly skilled"和"extensive knowledge"，建立专业权威形象
   - **知识广度**：通过列举四个技术领域，暗示了AI能够处理各种技术问题的能力
   - **开放性**：没有限定特定的编程语言或框架，保持了适应不同技术栈的灵活性

### 3.2 工具使用 (TOOL USE)

Cline系统提示的工具使用部分是整个提示中最核心、最复杂的组成部分，它定义了AI助手与外部环境交互的能力边界和方式。根据原始Prompt内容，工具使用部分采用了一种层级化的组织结构，主要包含以下几个子部分：

```
TOOL USE

You have access to a set of tools that are executed upon the user's approval. You can use one tool per message, and will receive the result of that tool use in the user's response. You use tools step-by-step to accomplish a given task, with each tool use informed by the result of the previous tool use.

# Tool Use Formatting

Tool use is formatted using XML-style tags. The tool name is enclosed in opening and closing tags, and each parameter is similarly enclosed within its own set of tags. Here's the structure:

<tool_name>
<parameter1_name>value1</parameter1_name>
<parameter2_name>value2</parameter2_name>
...
</tool_name>

# Tools

# Tool Use Examples

# Tool Use Guidelines
```

在工具使用部分的开头，系统提示首先提供了一段简明扼要的总体说明：

```
TOOL USE

You have access to a set of tools that are executed upon the user's approval. You can use one tool per message, and will receive the result of that tool use in the user's response. You use tools step-by-step to accomplish a given task, with each tool use informed by the result of the previous tool use.
```

这段开篇内容虽然简短，但包含了工具使用的核心原则和交互模式，具有以下几个关键设计特点：

1. **能力声明与限制平衡**：
   - 开篇即明确"You have access to a set of tools"，直接建立了模型的扩展能力边界
   - 同时强调"executed upon the user's approval"，设置了安全机制，确保用户对AI行为的控制权

2. **单步执行模式**：
   - 明确规定"one tool per message"的使用限制，防止模型尝试同时执行多个操作
   - 这种设计增强了操作的可预测性和可控性，避免复杂操作的潜在风险

3. **迭代反馈循环**：
   - 建立了"工具使用→用户响应→下一步行动"的清晰工作流程
   - 强调"will receive the result of that tool use in the user's response"，确保模型理解反馈的重要性

4. **渐进式任务完成**：
   - 提出"step-by-step to accomplish a given task"的工作方法
   - 明确"each tool use informed by the result of the previous tool use"，建立基于反馈的决策机制

这段简短文本通过预先设定交互规则，实际上构建了一个"受控自主性"的操作框架，使AI既拥有足够的能力执行复杂任务，又被限制在可控边界内。这种设计反映了"能力赋予"和"行为约束"的精妙平衡，是Cline系统提示设计理念的集中体现。

之后的结构化设计形成了一个完整的工具使用框架，既包含了"是什么"(格式规范和工具列表)，也包含了"怎么用"(使用示例和指南)，为AI提供了清晰的工具使用指引。每个部分都有其特定的设计目的和功能定位

#### 3.2.1 工具使用格式规范
##### XML标签格式说明

在Cline系统提示中，工具使用格式规范是一个关键部分，它定义了AI与外部环境交互的语法结构。根据原始Prompt内容，这部分的设计如下：

```
# Tool Use Formatting

Tool use is formatted using XML-style tags. The tool name is enclosed in opening and closing tags, and each parameter is similarly enclosed within its own set of tags. Here's the structure:

<tool_name>
<parameter1_name>value1</parameter1_name>
<parameter2_name>value2</parameter2_name>
...
</tool_name>

For example:

<read_file>
<path>src/main.js</path>
</read_file>

Always adhere to this format for the tool use to ensure proper parsing and execution.
```

这种XML风格的标签格式设计具有以下几个核心特点和优势：

1. **结构化与可解析性**：
   - 采用了XML的嵌套标签结构，使得工具调用具有清晰的层次关系
   - 每个工具及其参数都被明确的开闭标签包围，便于系统进行词法分析和语法解析
   - 从代码实现来看，Cline使用正则表达式（如`const paramRegex = /<(\w+)>([\s\S]*?)<\/\1>/gs`）来解析这些XML标签

2. **语义清晰性**：
   - 通过工具名称作为根标签，直观地表明了要调用的工具类型
   - 参数名称作为子标签，明确了每个值的用途和含义
   - 避免了位置参数可能带来的混淆和错误

3. **统一性与一致性**：
   - 为所有工具提供了统一的调用格式，降低了学习成本
   - 与HTML/XML等广泛使用的标记语言保持风格一致，符合开发者的心智模型
   - 在系统提示的多处（如工具使用示例和提醒中）反复强调这种格式，确保AI模型能够正确理解

4. **灵活性与可扩展性**：
   - 支持不同数量的参数和不同类型的内容值
   - 能够处理多行文本内容，适合代码文件创建等场景
   - 便于未来添加新的工具和参数，无需改变基本语法规则

5. **错误处理机制**：
   - 系统能够检测格式不正确或缺少必要参数的工具调用（通过`validateToolInput`函数）
   - 提供清晰的错误反馈，帮助AI理解并修正格式问题

从系统设计角度看，这种XML格式的设计还体现了以下几个深层次的考量：

1. **降低解析复杂度**：
   - XML的标签式嵌套结构使得解析算法相对简单，只需识别标签对及其内容
   - 特别适合处理嵌套复杂、多行内容的参数，如代码块或配置文件

2. **提高错误检测精度**：
   - 与位置参数或键值对格式相比，XML标签格式可以更精确地定位格式错误的位置
   - 系统可以清楚地识别是哪个标签缺失或格式不正确

3. **增强人类可读性**：
   - 当工具调用出现在日志或调试信息中时，XML格式的结构有助于人类开发者快速理解
   - 标签名称本身就提供了语义信息，无需额外注释

4. **增强提示效果**：
   - 这种格式对AI模型来说足够明确且结构化，有助于模型生成符合格式要求的输出
   - 格式的一致性使得AI模型更容易适应并遵循这些规则

5. **代码实现优势**：
   - 从源代码分析来看，`parseToolCalls`和`parseToolCall`函数能够高效地从文本中提取工具调用
   - 系统使用`toolUseNames`数组维护所有可用工具名称，增强了格式检验的可靠性

在实际实现中，Cline系统不仅在主系统提示中定义了这种格式，还在辅助提示中（如`toolUseInstructionsReminder`）重申了格式规范，以确保AI模型在长时间交互中不会"遗忘"这些格式要求。这种反复强调格式规范的设计，体现了系统对工具调用准确性的高度重视。

值得注意的是，这种XML标签格式虽然略显冗长（相比于JSON或命令行参数风格），但在确保AI模型正确理解和减少歧义方面具有显著优势，是一种权衡了多种因素后的精心设计选择。

#### 3.2.2 可用工具列表

Cline系统提示在Tools部分列出了AI可以使用的所有工具，以下是原始提示中这部分的结构：

```
# Tools

## execute_command
Description: Request to execute a CLI command on the system. Use this when you need to perform system operations or run specific commands to accomplish any step in the user's task. You must tailor your command to the user's system and provide a clear explanation of what the command does. For command chaining, use the appropriate chaining syntax for the user's shell. Prefer to execute complex CLI commands over creating executable scripts, as they are more flexible and easier to run. Commands will be executed in the current working directory: ${cwd.toPosix()}
Parameters:
- command: (required) The CLI command to execute. This should be valid for the current operating system. Ensure the command is properly formatted and does not contain any harmful instructions.
- requires_approval: (required) A boolean indicating whether this command requires explicit user approval before execution in case the user has auto-approve mode enabled. Set to 'true' for potentially impactful operations like installing/uninstalling packages, deleting/overwriting files, system configuration changes, network operations, or any commands that could have unintended side effects. Set to 'false' for safe operations like reading files/directories, running development servers, building projects, and other non-destructive operations.
Usage:
<execute_command>
<command>Your command here</command>
<requires_approval>true or false</requires_approval>
</execute_command>

## read_file
Description: ...
Parameters:
- path: (required) ...
Usage:
...

## write_to_file
...

[其他工具定义]
```

这部分内容采用了一种高度结构化的格式，每个工具都遵循相同的文档结构：
- **工具名称**：以二级标题（##）标识
- **描述**：详细说明工具用途和适用场景
- **参数列表**：以列表形式说明必需和可选参数
- **使用示例**：提供标准格式的工具调用示例

这种统一的文档格式设计有几个重要优势：
- **一致性**：所有工具遵循相同的文档结构，降低了认知负担
- **完整性**：确保每个工具都有完整的使用信息
- **参考价值**：便于AI在需要时查阅特定工具的详细用法

工具列表部分实际上构建了一个"能力库"，定义了AI可以执行的所有操作类型。整个工具集被精心设计为覆盖软件开发过程中的关键需求：从文件操作、代码分析到命令执行和交互式问答。

以下将重点分析三个核心工具的结构和设计理念：

##### execute_command 工具深入分析

execute_command工具是Cline系统中最强大也最具潜在风险的工具。以下是原始系统提示中的描述：

```
## execute_command
Description: Request to execute a CLI command on the system. Use this when you need to perform system operations or run specific commands to accomplish any step in the user's task. You must tailor your command to the user's system and provide a clear explanation of what the command does. For command chaining, use the appropriate chaining syntax for the user's shell. Prefer to execute complex CLI commands over creating executable scripts, as they are more flexible and easier to run. Commands will be executed in the current working directory: ${cwd.toPosix()}
Parameters:
- command: (required) The CLI command to execute. This should be valid for the current operating system. Ensure the command is properly formatted and does not contain any harmful instructions.
- requires_approval: (required) A boolean indicating whether this command requires explicit user approval before execution in case the user has auto-approve mode enabled. Set to 'true' for potentially impactful operations like installing/uninstalling packages, deleting/overwriting files, system configuration changes, network operations, or any commands that could have unintended side effects. Set to 'false' for safe operations like reading files/directories, running development servers, building projects, and other non-destructive operations.
Usage:
<execute_command>
<command>Your command here</command>
<requires_approval>true or false</requires_approval>
</execute_command>
```

这一工具的设计体现了几个关键考量，让我们逐句分析其设计意图：

1. **使用场景界定**：
   ```
   Description: Request to execute a CLI command on the system. Use this when you need to perform system operations or run specific commands to accomplish any step in the user's task.
   ```
   这句开头直接明确了工具的核心功能和适用范围。"Request to execute"而非直接"Execute"的措辞强调了这是一个请求动作，需要系统批准。"when you need to perform system operations or run specific commands"精确界定了使用条件，将工具使用限制在完成用户任务所需的操作范围内，防止无目的的系统操作。

2. **系统适应性要求**：
   ```
   You must tailor your command to the user's system and provide a clear explanation of what the command does.
   ```
   这句话包含两个关键指令：首先是"tailor your command to the user's system"，要求AI考虑用户的具体系统环境（如操作系统类型、shell类型）；其次是透明度要求"provide a clear explanation"，确保用户理解命令的作用，增强用户对AI操作的信任和控制感。

3. **命令链接指导**：
   ```
   For command chaining, use the appropriate chaining syntax for the user's shell.
   ```
   这句话针对复杂命令场景提供了具体指导，强调了系统兼容性考虑，避免使用错误的命令链接语法（如在Windows上使用Unix风格的命令链接）。这体现了对实际操作环境差异的敏感度。

4. **使用方式偏好**：
   ```
   Prefer to execute complex CLI commands over creating executable scripts, as they are more flexible and easier to run.
   ```
   这句话设置了操作偏好的优先级，倾向于使用单行复杂命令而非创建脚本文件。这种设计考虑了几个因素：降低安全风险（脚本文件持久存在）、简化用户体验（无需额外执行脚本）和提高灵活性。

5. **执行环境说明**：
   ```
   Commands will be executed in the current working directory: ${cwd.toPosix()}
   ```
   这句话通过明确指出命令的执行环境，消除了路径相关的潜在歧义。动态插入当前工作目录路径（${cwd.toPosix()}）使AI能够准确理解命令执行的上下文环境，避免路径相关错误。

6. **命令参数规范**：
   ```
   Parameters:
   - command: (required) The CLI command to execute. This should be valid for the current operating system. Ensure the command is properly formatted and does not contain any harmful instructions.
   ```
   command参数的描述包含三层要求：
   - 有效性要求："valid for the current operating system"，确保命令在特定操作系统环境中可执行
   - 格式要求："properly formatted"，确保命令语法正确
   - 安全要求："does not contain any harmful instructions"，明确禁止有害操作，设置了基本安全底线

7. **安全控制机制**：
   ```
   - requires_approval: (required) A boolean indicating whether this command requires explicit user approval before execution in case the user has auto-approve mode enabled.
   ```
   requires_approval参数是一个精心设计的安全控制点，特别针对"auto-approve mode"场景设计，确保即使在自动模式下，高风险操作仍需用户确认。强制将此参数标记为required，确保AI必须为每个命令进行风险评估。

8. **风险分类指导**：
   ```
   Set to 'true' for potentially impactful operations like installing/uninstalling packages, deleting/overwriting files, system configuration changes, network operations, or any commands that could have unintended side effects.
   ```
   这句话通过列举高风险操作类型，建立了明确的风险评估标准。详细的示例清单（包括包管理、文件操作、系统配置、网络操作等）帮助AI准确判断命令的风险级别，减少误判的可能性。

9. **安全操作界定**：
   ```
   Set to 'false' for safe operations like reading files/directories, running development servers, building projects, and other non-destructive operations.
   ```
   这句话通过具体示例界定了低风险操作的范围，为AI提供了安全操作的参考标准。列举具体场景（如读取文件、运行开发服务器、构建项目）使判断标准更加具体和可操作。

从实现角度看，execute_command工具的处理逻辑包含了参数验证、用户确认和安全执行等环节，构成了一个完整的命令执行安全链。这种多层安全设计反映了系统开发者对"能力赋予"与"安全保障"之间平衡的追求。特别是requires_approval参数的设计，为自动化与安全性之间找到了一个优雅的平衡点。

##### write_to_file 工具深入分析

write_to_file工具允许AI创建或覆盖文件，是代码生成和文件操作的基础。原始系统提示中的完整描述如下：

```
## write_to_file
Description: Request to write content to a file at the specified path. If the file exists, it will be overwritten with the provided content. If the file doesn't exist, it will be created. This tool will automatically create any directories needed to write the file.
Parameters:
- path: (required) The path of the file to write to
- content: (required) The content to write to the file
Usage:
<write_to_file>
<path>path/to/your/file.txt</path>
<content>
Content to write to the file
</content>
</write_to_file>
```

让我们逐句分析这一工具的设计要点和意图：

1. **工具定义与用途**：
   ```
   Description: Request to write content to a file at the specified path.
   ```
   使用"Request to write"而非简单的"Write"，保持了与execute_command工具相同的请求性质，强调这是一个需要系统处理的请求。明确指出工具的基本功能是"写入内容到指定路径的文件"，直接点明了工具的主要用途。

2. **行为模式说明**：
   ```
   If the file exists, it will be overwritten with the provided content. If the file doesn't exist, it will be created.
   ```
   这句话清晰定义了工具的两种工作模式：覆盖现有文件或创建新文件。使用条件句"If...If..."结构，明确了不同条件下的行为表现，避免使用中的歧义。特别强调"overwritten"，表明这是一个完全替换而非追加或修改操作，这一点对正确使用工具至关重要。

3. **便利功能说明**：
   ```
   This tool will automatically create any directories needed to write the file.
   ```
   描述了工具的一个重要便利功能——自动创建目录结构。这种设计极大简化了使用复杂度，无需用户或AI预先确认或创建目录。通过主动提供这一信息，避免了AI在创建深层次路径文件时可能产生的犹豫或额外步骤。

4. **路径参数规范**：
   ```
   Parameters:
   - path: (required) The path of the file to write to
   ```
   将path标记为required参数，确保每次调用必须明确指定文件路径。描述简洁明了，没有附加复杂条件，体现了该参数的直观性和基础性。

5. **内容参数规范**：
   ```
   - content: (required) The content to write to the file
   ```
   同样将content标记为required，强调必须提供写入内容。描述简单直接，但在系统提示的其他部分（特别是"文件编辑指南"）中对此参数有更详细的规定。

从设计角度看，write_to_file工具体现了以下几个关键设计理念：

1. **简洁直观**：参数设计极度简化（仅path和content两个必要参数），使用门槛低
2. **功能自洽**：自动创建必要目录的功能增强了工具的独立性和便捷性
3. **行为明确**：明确指出覆盖现有文件的行为，避免隐含的副作用引起混淆
4. **与相关工具互补**：系统提示在其他部分（文件编辑指南，将在3.4节详述）明确区分了write_to_file和replace_in_file的适用场景

值得注意的是，在系统提示的"文件编辑指南"部分对write_to_file有更详细的使用场景说明和注意事项，将在本文档的3.4节中进行详细介绍。

##### use_mcp_tool 工具深入分析（条件性显示）

use_mcp_tool是Cline系统中的一个高级扩展功能，仅在特定配置下显示。原始系统提示中的完整描述如下：

```
## use_mcp_tool
Description: Request to use a tool provided by a connected MCP server. Each MCP server can provide multiple tools with different capabilities. Tools have defined input schemas that specify required and optional parameters.
Parameters:
- server_name: (required) The name of the MCP server providing the tool
- tool_name: (required) The name of the tool to execute
- arguments: (required) A JSON object containing the tool's input parameters, following the tool's input schema
Usage:
<use_mcp_tool>
<server_name>server name here</server_name>
<tool_name>tool name here</tool_name>
<arguments>
{
  "param1": "value1",
  "param2": "value2"
}
</arguments>
</use_mcp_tool>
```

让我们逐句分析这一元级工具的设计特点：

1. **工具概念定义**：
   ```
   Description: Request to use a tool provided by a connected MCP server.
   ```
   开篇即明确这是一个"间接工具"——用于请求使用其他服务器提供的工具。"Request to use"与其他工具保持一致的措辞风格，强调请求性质。关键点是"provided by a connected MCP server"，引入了MCP（Model Context Protocol）服务器的概念，暗示了一种插件化架构。

2. **服务器能力说明**：
   ```
   Each MCP server can provide multiple tools with different capabilities.
   ```
   这句话说明MCP服务器的一个核心特性：一个服务器可提供多种工具。"different capabilities"表明这些工具功能各异，暗示了MCP架构的扩展性和多样性。这种设计为Cline系统创建了一个开放式的能力扩展框架。

3. **工具参数机制**：
   ```
   Tools have defined input schemas that specify required and optional parameters.
   ```
   解释了MCP工具的参数机制，引入了"input schemas"的概念，表明参数并非随意设置，而是有明确的结构定义。区分"required and optional parameters"，表明架构支持不同级别的参数需求，增加了使用灵活性。

4. **服务器参数规范**：
   ```
   Parameters:
   - server_name: (required) The name of the MCP server providing the tool
   ```
   定义第一个必要参数——服务器名称。通过"providing the tool"的描述，强调了服务器与工具之间的提供关系，建立了层级概念。这种设计支持多服务器架构，为系统扩展奠定基础。

5. **工具名称参数**：
   ```
   - tool_name: (required) The name of the tool to execute
   ```
   定义第二个必要参数——工具名称。使用"to execute"而非简单的"to use"，暗示这是一个将被实际执行的工具，强调了其动作性质。这种设计将服务器和工具分离，增强了体系的灵活性。

6. **参数传递机制**：
   ```
   - arguments: (required) A JSON object containing the tool's input parameters, following the tool's input schema
   ```
   定义第三个必要参数——工具参数集。特别之处在于使用"JSON object"作为参数容器，这与系统提示中其他工具使用的XML格式形成对比。"following the tool's input schema"强调参数必须符合工具预定义的结构，引入了一种协议契约概念。

在使用示例中，系统提示提供了两个具体用例：

```
<use_mcp_tool>
<server_name>weather-server</server_name>
<tool_name>get_forecast</tool_name>
<arguments>
{
  "city": "San Francisco",
  "days": 5
}
</arguments>
</use_mcp_tool>
```

和

```
<use_mcp_tool>
<server_name>github.com/modelcontextprotocol/servers/tree/main/src/github</server_name>
<tool_name>create_issue</tool_name>
<arguments>
{
  "owner": "octocat",
  "repo": "hello-world",
  "title": "Found a bug",
  "body": "I'm having a problem with this.",
  "labels": ["bug", "help wanted"],
  "assignees": ["octocat"]
}
</arguments>
</use_mcp_tool>
```

这些示例揭示了几个关键设计要点：

1. **应用场景多样性**：从简单的天气查询到复杂的GitHub交互，展示了MCP工具的广泛适用性
2. **服务器标识灵活性**：server_name可以是简单名称（如"weather-server"）或URL风格路径，增强了系统兼容性
3. **参数结构复杂性**：JSON格式支持简单键值对和复杂的嵌套结构（如数组），适应不同API的需求
4. **端点设计思想**：通过工具名称区分同一服务器的不同功能（如get_forecast、create_issue），类似REST API的端点设计

从系统架构角度看，use_mcp_tool代表了一种元编程思想，它将Cline从一个封闭系统转变为一个可扩展的平台。这种设计解决了AI系统一个根本性挑战：如何在保持核心提示稳定的同时，支持能力的持续扩展和定制。通过MCP服务器机制，Cline实现了"插件化"的能力扩展框架。

从实现细节来看，系统根据`mcpHub.getMode() !== "off"`条件决定是否显示MCP相关部分，这表明MCP功能是一个可配置的高级特性，可以根据系统设置和用户需求启用或禁用。这种条件性显示的设计减少了对不需要此功能用户的认知负担，同时为高级用户保留了扩展可能性。

#### 工具描述的共性设计特点

通过对Cline系统提示中各工具描述的深入分析，我们可以识别出几个贯穿整个工具集设计的共性特点。这些特点体现了Cline系统提示设计者在工具定义方面的一致性思考和精心设计：

1. **统一的"请求式"语法**：
   所有工具描述都以"Request to..."开头，而非直接命令式的"Do..."。这种统一的语法结构强调了工具使用的请求性质，暗示AI并非直接执行操作，而是需要通过系统进行请求。例如：
   ```
   Description: Request to execute a CLI command...
   Description: Request to write content to a file...
   Description: Request to use a tool provided by a connected MCP server...
   ```
   这种一致的表述建立了明确的心智模型，提醒AI其操作需要经过系统处理和用户批准。

2. **目的导向的使用场景说明**：
   每个工具描述都明确指出"Use this when..."，为AI提供了工具选择的决策指导。这种设计不仅告诉AI工具"能做什么"，还指导AI"何时使用"，帮助AI做出更合理的工具选择：
   ```
   Use this when you need to perform system operations...
   Use this when you need to examine the contents of an existing file...
   ```

3. **参数标准化**：
   所有工具的参数描述都遵循相同的格式：名称、是否必需、用途说明和约束条件。特别是对必需参数的明确标记`(required)`，确保AI不会遗漏关键信息：
   ```
   - command: (required) The CLI command to execute...
   - path: (required) The path of the file to write to...
   - server_name: (required) The name of the MCP server providing the tool...
   ```

4. **安全与限制的内置考量**：
   每个工具的描述中都包含了相关的安全考虑和使用约束，通过明确的指导和警告减少潜在风险。这些安全考虑或直接内置于工具参数（如execute_command的requires_approval），或体现在使用说明中：
   ```
   Ensure the command is properly formatted and does not contain any harmful instructions.
   If the file exists, it will be overwritten with the provided content.
   ```

5. **预测性错误防范**：
   工具描述往往预先指出常见的错误模式，并提供预防指导。例如，execute_command工具中明确指出命令应适配用户系统，write_to_file工具说明会自动创建必要的目录结构，这些都是针对可能出现的问题的提前防范：
   ```
   You must tailor your command to the user's system...
   This tool will automatically create any directories needed...
   ```

6. **一致的示例格式**：
   每个工具都提供了标准化的使用示例，遵循相同的XML标签格式，这强化了格式规范，为AI提供了明确的模板：
   ```
   <execute_command>
   <command>Your command here</command>
   <requires_approval>true or false</requires_approval>
   </execute_command>
   ```

7. **环境上下文的整合**：
   工具描述中经常包含对当前环境的引用，如工作目录、系统类型等，使AI能够更准确地适应用户环境：
   ```
   Commands will be executed in the current working directory: ${cwd.toPosix()}
   ```

8. **行为机制的透明性**：
   工具描述明确说明了工具执行的后台机制，帮助AI理解执行结果和可能的副作用：
   ```
   If the file exists, it will be overwritten with the provided content.
   Each MCP server can provide multiple tools with different capabilities.
   ```

这些共性特点反映了Cline系统提示在工具定义方面的系统性思考，通过一致的格式、清晰的指导和内置的安全考量，确保AI能够正确、安全、有效地使用各种工具。这种统一性不仅降低了AI学习和使用工具的认知负担，也提高了工具使用的安全性和可预测性，是Cline系统提示设计中的一个重要亮点。

#### 3.2.3 工具使用示例

Cline系统提示中的"工具使用示例"部分通过具体实例展示各种工具的正确使用方法。原始提示中这部分的结构如下：

```
# Tool Use Examples

## Example 1: Requesting to execute a command
<execute_command>
<command>npm run dev</command>
<requires_approval>false</requires_approval>
</execute_command>

## Example 2: Requesting to create a new file
...

## Example 3: Requesting to make targeted edits to a file
...

## Example 4: Requesting to use an MCP tool (条件性显示)
...
```

这部分通过编号示例覆盖了核心工具的使用场景，每个示例都包含明确标题和完整的工具调用代码。

##### 执行命令示例

```
## Example 1: Requesting to execute a command

<execute_command>
<command>npm run dev</command>
<requires_approval>false</requires_approval>
</execute_command>
```

这个示例展示了execute_command工具的基本用法，具有以下特点：
- 选择常见开发场景（启动开发服务器）为示例
- 包含所有必需参数（command和requires_approval）
- 通过设置requires_approval为false表明这是安全操作
- 严格遵循前面定义的XML标签格式

示例使用真实命令而非占位符，帮助AI理解命令的实际应用场景。

##### 创建文件示例

```
## Example 2: Requesting to create a new file

<write_to_file>
<path>src/frontend-config.json</path>
<content>
{
  "apiEndpoint": "https://api.example.com",
  "theme": {
    "primaryColor": "#007bff",
    "secondaryColor": "#6c757d",
    "fontFamily": "Arial, sans-serif"
  },
  "features": {
    "darkMode": true,
    "notifications": true,
    "analytics": false
  },
  "version": "1.0.0"
}
</content>
</write_to_file>
```

此示例的设计特点包括：
- 展示如何处理多行、格式化的JSON内容
- 通过`src/frontend-config.json`展示相对路径的使用方式
- 选择配置文件创建这一常见开发任务增强实用性
- 保留JSON的缩进和格式，表明工具可以准确保留内容格式

##### 编辑文件示例

```
## Example 3: Requesting to make targeted edits to a file

<replace_in_file>
<path>src/components/App.tsx</path>
<diff>
<<<<<<< SEARCH
import React from 'react';
=======
import React, { useState } from 'react';
>>>>>>> REPLACE

<<<<<<< SEARCH
function handleSubmit() {
  saveData();
  setLoading(false);
}

=======
>>>>>>> REPLACE

<<<<<<< SEARCH
return (
  <div>
=======
function handleSubmit() {
  saveData();
  setLoading(false);
}

return (
  <div>
>>>>>>> REPLACE
</diff>
</replace_in_file>
```

这个复杂示例展示了replace_in_file工具的使用，具有以下特点：
- 展示三种不同编辑操作：添加导入、删除代码块、移动代码块
- 清晰展示SEARCH/REPLACE块的格式要求和分隔符使用
- 展示包含足够上下文的代码块，表明编辑需考虑代码的位置和上下文
- 使用TypeScript React代码作为示例，与现代Web开发实践相符

##### MCP工具使用示例 (条件性显示)

系统提示根据mcpHub.getMode()的值，条件性地显示三个额外的MCP相关示例：

```
## Example 4: Requesting to use an MCP tool

<use_mcp_tool>
<server_name>weather-server</server_name>
<tool_name>get_forecast</tool_name>
<arguments>
{
  "city": "San Francisco",
  "days": 5
}
</arguments>
</use_mcp_tool>
```

MCP示例的设计特点包括：
- 展示不同类型的服务器标识方式（简单名称和URL风格的长标识符）
- 区分工具调用（获取天气预报、创建GitHub issue）和资源访问（获取当前天气）
- 展示从简单到复杂的参数结构
- 展示arguments参数中JSON对象的正确格式
- 选择实际应用场景（天气服务和GitHub集成）

#### 工具使用示例的整体设计特点

工具使用示例部分的整体设计具有以下关键特点：

1. **渐进式复杂度**：示例按复杂度递增排列，从简单命令执行到复杂文件编辑和MCP工具调用
2. **真实场景导向**：使用真实的命令、文件类型和代码片段，而非简化的占位符
3. **格式一致性强化**：通过实际示例强化XML标签格式规范
4. **关键工具覆盖**：精选最常用和最复杂的工具，为广泛任务类型奠定基础
5. **条件内容适应**：根据实际配置动态调整MCP示例内容
6. **多层次学习设计**：不仅展示"如何调用工具"，还隐含传达"何时使用特定工具"和"如何构建参数"

这种"通过示例教学"的方法比纯粹的规则描述更直观有效，特别是对于复杂工具调用格式的学习。

#### 3.2.4 工具使用指南

Cline系统提示的"工具使用指南"部分为AI提供了使用工具的过程性指导，建立了明确的工作流程和最佳实践。原始提示中这部分的结构如下：

```
# Tool Use Guidelines

1. In <thinking> tags, assess what information you already have and what information you need to proceed with the task.
2. Choose the most appropriate tool based on the task and the tool descriptions provided...
3. If multiple actions are needed, use one tool at a time per message...
4. Formulate your tool use using the XML format specified for each tool.
5. After each tool use, the user will respond with the result of that tool use...
6. ALWAYS wait for user confirmation after each tool use before proceeding...

It is crucial to proceed step-by-step, waiting for the user's message after each tool use before moving forward with the task...
```

这部分内容采用了编号列表的形式，清晰地描述了工具使用的完整工作流程，从任务评估到结果反馈再到后续行动。

##### 信息评估流程

```
1. In <thinking> tags, assess what information you already have and what information you need to proceed with the task.
```

工具使用指南首先强调了信息评估的重要性：
- 引入专用的`<thinking>`标签用于思考过程
- 要求AI首先评估已有信息和所需信息
- 建立了"先思考，后行动"的工作范式
- 暗示了工具使用前的分析环节不可省略

这种设计体现了系统对于AI思考过程的重视，通过显式的思考标记引导AI进行更系统、更深入的任务分析。

##### 工具选择策略

```
2. Choose the most appropriate tool based on the task and the tool descriptions provided. Assess if you need additional information to proceed, and which of the available tools would be most effective for gathering this information. For example using the list_files tool is more effective than running a command like `ls` in the terminal. It's critical that you think about each available tool and use the one that best fits the current step in the task.
```

第二条指南提供了工具选择的具体策略：
- 基于任务特性和工具描述选择最合适的工具
- 引导AI考虑是否需要补充信息以及获取信息的最佳工具
- 通过具体示例（list_files比ls命令更有效）提供实用指导
- 强调对所有可用工具的全面评估

这一条款特别强调了工具选择的优先级和效率考量，引导AI避免使用通用命令而优先使用专用工具，体现了系统设计的效率导向。

##### 迭代执行原则

```
3. If multiple actions are needed, use one tool at a time per message to accomplish the task iteratively, with each tool use being informed by the result of the previous tool use. Do not assume the outcome of any tool use. Each step must be informed by the previous step's result.
```

第三条指南建立了迭代执行的核心原则：
- 严格的"一次一工具"使用规则
- 强调迭代式任务完成方法
- 禁止对工具执行结果做出假设
- 要求每一步都基于前一步的实际结果

这条规则建立了一个谨慎、可控的执行模式，通过限制每个消息中只能使用一个工具，确保了操作的可预测性和错误的可追踪性。

##### 等待用户确认机制

```
6. ALWAYS wait for user confirmation after each tool use before proceeding. Never assume the success of a tool use without explicit confirmation of the result from the user.
```

工具使用指南特别强调了用户确认机制：
- 使用"ALWAYS"和大写字母突出这一规则的绝对性
- 明确禁止在未获得确认前假设工具执行成功
- 建立了强制性的"工具使用→用户确认→下一步操作"流程
- 增强了用户对AI操作的控制权

这一规则确保了AI不会连续执行多个操作而没有用户的监督，是系统安全机制的重要组成部分。

##### 错误处理流程

```
5. After each tool use, the user will respond with the result of that tool use. This result will provide you with the necessary information to continue your task or make further decisions. This response may include:
  - Information about whether the tool succeeded or failed, along with any reasons for failure.
  - Linter errors that may have arisen due to the changes you made, which you'll need to address.
  - New terminal output in reaction to the changes, which you may need to consider or act upon.
  - Any other relevant feedback or information related to the tool use.
```

第五条指南详细说明了反馈处理和错误应对机制：
- 明确工具执行后的反馈内容类型
- 特别强调了可能出现的失败情况和错误信息
- 提供了常见错误类型（如linter错误）的处理指导
- 要求AI根据反馈调整后续策略

这部分内容通过详细描述可能的反馈类型，为AI处理各种执行结果提供了框架，特别是对错误情况的预期和应对准备。

#### 工具使用指南的整体设计特点

通过分析这一部分内容，可以识别出以下设计特点：

1. **结构化工作流程**：通过编号列表建立了清晰的、线性的工作流程，从思考分析到工具选择、执行和反馈处理
2. **安全优先原则**：多处强调等待用户确认、避免假设执行结果等安全考量
3. **迭代式方法论**：建立"一次一工具"的迭代执行模式，确保操作的可控性
4. **具体而非抽象**：通过实际示例和具体情况说明各项原则，增强可操作性
5. **思考与行动分离**：通过`<thinking>`标签明确区分分析思考与实际操作
6. **全流程覆盖**：从初始评估到最终结果处理，覆盖了工具使用的完整生命周期

这种详细的过程性指导不仅规定了"做什么"，更规定了"如何做"和"按什么顺序做"，确保AI能够以一种系统、安全、可控的方式使用工具完成任务。相比于前面部分对工具功能和格式的说明，这部分更侧重于建立正确的工具使用流程和习惯，是整个系统提示的重要补充。

### 3.3 MCP服务器 (条件性显示)
#### 3.3.1 已连接MCP服务器列表
#### 3.3.2 创建MCP服务器指南
##### 环境理解
##### 创建步骤
##### 示例服务器代码
##### 配置文件设置说明
#### 3.3.3 编辑MCP服务器指南
#### 3.3.4 MCP服务器使用说明

### 3.4 文件编辑指南
#### 3.4.1 write_to_file工具
##### 用途
##### 使用场景
##### 重要考虑因素
#### 3.4.2 replace_in_file工具
##### 用途
##### 使用场景
##### 优势
#### 3.4.3 工具选择指南
#### 3.4.4 自动格式化考虑因素
#### 3.4.5 工作流程提示

### 3.5 运行模式对比
#### 3.5.1 ACT MODE
##### 可用工具
##### 工作流程
#### 3.5.2 PLAN MODE
##### 可用工具
##### 工作流程
#### 3.5.3 PLAN MODE详解
##### 用途
##### 信息收集流程
##### 方案设计流程
##### 模式切换建议

### 3.6 能力清单
#### 3.6.1 命令执行能力
#### 3.6.2 文件操作能力
#### 3.6.3 代码分析能力
#### 3.6.4 浏览器交互能力 (条件性显示)
#### 3.6.5 MCP服务器能力 (条件性显示)

### 3.7 规则与限制
#### 3.7.1 工作目录限制
#### 3.7.2 命令执行规范
#### 3.7.3 搜索规则
#### 3.7.4 项目创建规范
#### 3.7.5 代码修改规则
#### 3.7.6 用户交互规范
#### 3.7.7 文件编辑规范
#### 3.7.8 浏览器操作规则 (条件性显示)

### 3.8 系统信息
#### 3.8.1 操作系统
#### 3.8.2 默认Shell
#### 3.8.3 主目录
#### 3.8.4 当前工作目录

### 3.9 工作目标
#### 3.9.1 任务分析方法
#### 3.9.2 目标分解策略
#### 3.9.3 工具使用流程
#### 3.9.4 结果展示要求
#### 3.9.5 反馈处理机制

### 3.10 用户自定义指令 (动态添加)
#### 3.10.1 语言偏好设置 (可选)
#### 3.10.2 设置自定义指令 (可选)
#### 3.10.3 cline规则文件指令 (可选)
#### 3.10.4 cline忽略指令 (可选)

## 四、各部分功能与效果案例
### 4.1 工具使用案例
#### 命令执行案例：运行开发服务器
#### 文件操作案例：创建和修改代码文件
#### 搜索案例：查找项目中的特定代码模式
#### 浏览器交互案例：测试网页功能

### 4.2 文件编辑案例
#### 完整替换文件内容的案例
#### 精确修改代码的案例

### 4.3 模式转换效果
#### PLAN模式下的方案设计案例
#### ACT模式下的实现案例

### 4.4 规则影响分析
#### 规则如何防止模型过度对话
#### 规则如何引导模型有效完成任务

## 五、扩展功能分析
### 5.1 MCP服务器集成
#### MCP服务器的作用与价值
#### 集成案例：天气服务API

### 5.2 浏览器控制能力
#### 浏览器交互机制
#### 应用场景分析

## 六、定制化能力
### 用户自定义指令的实现机制
### 自定义指令的应用案例

## 七、总结与启示
### 7.1 设计亮点
#### 关键创新点
#### 有效性分析

### 7.2 可借鉴的最佳实践
#### 提示设计方法
#### 工具集成方法
#### 模型行为控制方法 