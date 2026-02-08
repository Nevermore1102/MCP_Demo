# AGENTS.md - 项目专属指令

## CRITICAL: 关键工作流 (永不删除)

> **⚠️ 此部分绝不能被移除或修改 - 包含项目的核心工作流**

### Git分支策略
```
main (生产/稳定版本)
  ↑
develop (开发/集成分支)
  ↑
feature/* (功能分支)
fix/* (修复分支)
```

| 规则 | 强制性 |
|------|---------|
| **所有PR → develop** | 必须指向develop分支 |
| **禁止PR → main** | 指向main的PR会被CI自动拒绝 |
| **Conventional Commits** | 必须遵循提交规范 |

### Conventional Commits规范

提交信息格式：
```
<type>(<scope>): <subject>

<body>
```

**类型：**
- `feat`: 新功能
- `fix`: Bug修复
- `docs`: 文档更新
- `style`: 代码格式（不影响代码运行）
- `refactor`: 重构
- `test`: 测试相关
- `chore`: 构建/工具相关

**示例：**
```
feat(auth): add OAuth2 login support
fix(api): resolve token expiration issue
docs(readme): update quick start guide
```

---

## 项目配置

### 开发命令
- **启动开发服务器**: `npm run dev`
- **构建项目**: `npm run build`
- **测试**: `npm test`
- **代码检查**: `npm run lint`
- **类型检查**: `npm run typecheck`

### 代码规范
- 使用 2 个空格缩进
- 函数名使用驼峰命名
- 文件名使用 kebab-case
- 组件使用 PascalCase

## 工作流程

### 新功能开发
1. 创建功能分支
2. 开发新功能
3. 运行测试确保通过
4. 代码审查
5. 合并到主分支

### 修复 bug
1. 确认问题复现
2. 创建修复分支
3. 编写测试用例
4. 应用修复
5. 验证修复
6. 代码审查

## 自定义指令

### 搜索文档
- 使用 `grep` 搜索代码中的特定模式
- 使用 `glob` 按文件名查找文件
- 优先查看现有代码结构

### 添加新依赖
1. 检查 package.json 中是否已存在
2. 运行 `npm install <package>`
3. 更新相关配置文件
4. 验证功能正常工作

### 代码修改
- 首先阅读现有代码理解结构
- 遵循现有的命名和编码规范
- 添加必要的注释和文档

## 常用工具

### 文件操作
- `read` - 读取文件内容
- `edit` - 编辑文件（替换字符串）
- `write` - 写入新文件
- `glob` - 按模式搜索文件
- `grep` - 按内容搜索文件

### 代码管理
- `bash` - 执行终端命令
- `todowrite` - 创建和管理任务列表
- `task` - 启动复杂任务代理

## 项目特定信息

### 技术栈
根据项目类型填写实际技术栈：
- 前端框架: [React/Vue/Angular/Next.js等]
- 后端框架: [Node.js/Express/FastAPI等，如适用]
- 构建工具: [Vite/Webpack/Next.js内置等]
- 测试框架: [Jest/Vitest/Cypress等]
- 其他依赖: [填写重要的库和工具]

### 开发环境
- Node.js 版本: [填写当前使用的版本，如18.17.0]
- 包管理器: npm/yarn/pnpm/bun
- 操作系统: [Windows/macOS/Linux]

### Git 配置
- 用户名: Nevermore1102
- 邮箱: 1535332051@qq.com
- 远程仓库: https://github.com/Nevermore1102/OpenCode_template.git
- 代理设置: socks5://127.0.0.1:10808 (通过v2ray)
- 主分支: main

**多电脑同步说明：**
1. Clone仓库到新电脑：`git clone <repo-url>`
2. 配置Git用户信息（如不同）：`git config --global user.name "Your Name"`
3. 配置GitHub代理（如在国内）：
   ```bash
   git config --global http.https://github.com.proxy socks5://127.0.0.1:10808
   git config --global https.proxy socks5://127.0.0.1:10808
   ```
4. 启动OpenCode即可

### OpenCode 配置

**项目配置：** `.opencode/opencode.json`
```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "model": "zhipuai-coding-plan/glm-4.7",
  "permission": {
    "skill": { "*": "allow" }
  }
}
```

**全局配置：** `~/.config/opencode/opencode.json`
- oh-my-opencode插件：已安装
- MCP服务器：配置在全局，不提交到Git

### 技能 (Skills)

**项目级技能：** `.opencode/skills/`

| 技能 | 描述 | 使用场景 |
|------|------|----------|
| error-diagnostic | 错误诊断和问题解决 | 遇到错误、异常时 |
| github-explorer | GitHub仓库探索和代码研究 | 查找开源实现时 |
| ui-analyzer | UI设计和转换 | UI设计转代码时 |
| visual-analyzer | 视觉内容分析 | 分析图表、数据可视化时 |
| web-researcher | 网络搜索和网页内容研究 | 搜索信息时 |

**使用方式：**
```bash
# 在OpenCode会话中
@agent 使用error-diagnostic技能分析这个错误
@agent 使用github-explorer探索相关项目
```

### 项目结构
```
project-name/
├── .github/                  # GitHub配置
│   ├── ISSUE_TEMPLATE/      # Issue模板
│   ├── workflows/           # CI/CD工作流
│   └── CODEOWNERS          # 代码所有者
├── .opencode/               # OpenCode配置
│   ├── opencode.json       # 项目级配置
│   └── skills/            # 自定义技能
│       ├── error-diagnostic/
│       ├── github-explorer/
│       ├── ui-analyzer/
│       ├── visual-analyzer/
│       └── web-researcher/
├── src/                     # 源代码
├── tests/                   # 测试文件
├── docs/                    # 文档
├── package.json             # 项目配置
├── AGENTS.md               # 项目指导（本文件）
├── README.md               # 项目说明
├── CONTRIBUTING.md         # 贡献指南
└── LICENSE                 # 许可证
```

## 注意事项

1. 修改代码前先理解现有结构
2. 运行测试确保功能正常
3. 遵循项目编码规范
4. 及时更新文档
5. 备份重要配置文件

## 快速开始

```bash
# 克隆项目
git clone [repository-url]

# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 运行测试
npm test
```

---

## 🚀 使用 Ultrawork 模式

**什么是Ultrawork？**

Ultrawork是Oh-My-OpenCode提供的超强工作模式。只需在提示词中添加`ulw`或`ultrawork`关键词，即可激活：

- 并行执行多个代理
- 后台任务处理
- 深度代码库探索
- 持续执行直到任务完成

**使用示例：**

```bash
# 简单使用
帮我实现这个功能，ulw

# 明确指定
ultrawork模式：帮我优化整个项目的代码结构

# 深度分析
ulw：深度分析这个模块的性能瓶颈
```

### 可用的专业代理

| 代理 | 用途 | 模型 |
|------|------|------|
| **Sisyphus** | 主协调器，复杂任务编排 | GLM-4.7 |
| **Hephaestus** | 自主深度工作者，目标导向执行 | GLM-4.7 |
| **Oracle** | 架构决策、代码审查、调试 | GLM-4.7 |
| **Prometheus** | 战略规划师，创建详细工作计划 | GLM-4.7 |
| **Librarian** | 文档搜索、开源实现、代码库探索 | GLM-4.7 |
| **Explore** | 快速代码库探索和上下文grep | GLM-4.7 |

**显式调用代理：**

```bash
# 架构审查
让 @oracle 审查这个架构设计

# 文档查询
让 @librarian 查找相关的开源实现

# 代码库探索
让 @explore 找到所有认证相关的文件
```

### 内置斜杠命令

| 命令 | 功能 |
|------|------|
| `/init-deep` | 初始化层级AGENTS.md知识库 |
| `/ralph-loop` | 自循环开发直到任务完成 |
| `/ulw-loop` | Ultrawork模式循环（最强） |
| `/cancel-ralph` | 取消活动Ralph循环 |
| `/refactor` | 智能重构（LSP+AST） |
| `/start-work` | 从Prometheus计划开始工作 |

**使用示例：**

```bash
# 初始化项目知识库
/init-deep

# 自循环开发
/ralph-loop "实现一个REST API"

# Ultrawork循环
/ulw-loop "优化整个前端性能"

# 智能重构
/refactor PaymentModule --scope=module

# 启动工作流程
/start-work
```