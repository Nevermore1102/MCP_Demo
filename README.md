# OpenCode 项目模板

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![OpenCode](https://img.shields.io/badge/OpenCode-1.1.53+-brightgreen.svg)](https://opencode.ai)
[![GitHub Stars](https://img.shields.io/github/stars/Nevermore1102/OpenCode_template?style=social)](https://github.com/Nevermore1102/OpenCode_template)
[![GitHub issues](https://img.shields.io/github/issues/Nevermore1102/OpenCode_template)](https://github.com/Nevermore1102/OpenCode_template/issues)

> 为 OpenCode 优化的项目模板，支持 GitHub 同步和多项目快速启动

## ✨ 特性

- 🚀 **即插即用**：Clone 后立即使用 OpenCode 开发
- 📚 **完整配置**：包含优化的 AGENTS.md 和 .opencode 配置
- 🔄 **GitHub 同步**：支持多台电脑间同步项目
- 🛠️ **自定义技能**：预置 5 个实用技能
- 📝 **Git 最佳实践**：内置 Conventional Commits 和分支策略
- 🧪 **CI/CD 就绪**：包含 GitHub Actions 工作流
- 🌍 **多项目支持**：通用配置，易于定制

## 🚀 快速开始

### 1. 克隆项目模板

**方法 1：GitHub Template（推荐）**

1. 访问 https://github.com/Nevermore1102/OpenCode_template
2. 点击 "Use this template" 按钮
3. 输入仓库名称
4. 克隆新仓库

**方法 2：Git Clone**

\`\`\`bash
git clone https://github.com/Nevermore1102/OpenCode_template.git my-project
cd my-project
\`\`\`

### 2. 配置项目

\`\`\`bash
# 修改项目名称
# 编辑 package.json 中的 name 字段

# 初始化 Git（如果是 clone）
git init
git remote add origin YOUR_REPO_URL
\`\`\`

### 3. 安装依赖

\`\`\`bash
npm install
\`\`\`

### 4. 配置 OpenCode

\`\`\`bash
# 启动 OpenCode
opencode

# 初始化项目
/init
\`\`\`

### 5. 开始开发

\`\`\`bash
# 启动开发服务器
npm run dev

# 运行测试
npm test
\`\`\`

## 📁 项目结构

\`\`\`
OpenCode_template/
├── .github/                  # GitHub 配置
│   ├── ISSUE_TEMPLATE/        # Issue 模板
│   ├── PULL_REQUEST_TEMPLATE.md # PR 模板
│   ├── workflows/             # CI/CD 工作流
│   └── CODEOWNERS            # 代码所有者
├── .opencode/               # OpenCode 配置
│   ├── opencode.json        # 项目配置
│   ├── README.md            # 配置说明
│   └── skills/             # 自定义技能
│       ├── error-diagnostic/
│       ├── github-explorer/
│       ├── ui-analyzer/
│       ├── visual-analyzer/
│       └── web-researcher/
├── src/                     # 源代码（根据项目创建）
├── tests/                   # 测试文件（根据项目创建）
├── AGENTS.md                # OpenCode 项目指导 ⭐
├── README.md                # 项目说明（本文件）
├── CONTRIBUTING.md          # 贡献指南
└── CODE_OF_CONDUCT.md        # 行为准则
\`\`\`

## ⚙️ 配置说明

### OpenCode 配置

**AGENTS.md** - 完整的项目指导文档：
- 项目特定信息（技术栈、Git 配置等）
- 开发命令和工作流程
- 代码规范和反模式
- OpenCode 配置说明
- Ultrawork 模式使用指南

**.opencode/README.md** - 配置参考文档：
- 详细的配置文件格式
- 技能添加方法
- MCP 服务器配置

### 预置技能

- \`error-diagnostic\` - 错误诊断和问题解决
- \`github-explorer\` - GitHub 仓库探索和代码研究
- \`ui-analyzer\` - UI 设计和转换
- \`visual-analyzer\` - 视觉内容分析
- \`web-researcher\` - 网络搜索和网页内容研究

更多技能详情和添加方法请查看 [AGENTS.md](AGENTS.md) 和 [.opencode/README.md](.opencode/README.md)。

## 💡 使用技巧

### Ultrawork 模式

在提示词中添加 \`ulw\` 或 \`ultrawork\` 激活最强模式：

\`\`\`bash
# 简单使用
帮我实现这个功能，ulw

# 明确指定
ultrawork 模式：帮我优化整个项目的代码结构

# 深度分析
ulw：深度分析这个模块的性能瓶颈
\`\`\`

更多详情请查看 [AGENTS.md](AGENTS.md)。

### 调用专业代理

\`\`\`bash
# 架构审查
让 @oracle 审查这个架构设计

# 文档查询
让 @librarian 查找相关的开源实现

# 代码库探索
让 @explore 找到所有认证相关的文件
\`\`\`

### 斜杠命令

\`\`\`bash
/init-deep    # 初始化层级 AGENTS.md
/ralph-loop   # 自循环开发
/ulw-loop     # Ultrawork 模式循环
/refactor     # 智能重构
/start-work   # 从 Prometheus 计划开始工作
\`\`\`

## 🤝 贡献

欢迎贡献！请查看 [CONTRIBUTING.md](CONTRIBUTING.md) 了解详情。

## 📄 许可证

MIT License - 详见 [LICENSE](LICENSE)

## 📚 相关资源

- [OpenCode 官方文档](https://opencode.ai/docs/)
- [Oh-My-OpenCode](https://github.com/code-yeongyu/oh-my-opencode)
- [AGENTS.md 最佳实践](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md/)
- [Conventional Commits](https://www.conventionalcommits.org/)

## 🌟 Star History

如果这个模板对你有帮助，请给它一个 ⭐️！

[![Star History Chart](https://api.star-history.com/svg?repos=Nevermore1102/OpenCode_template&type=Date)](https://star-history.com/#Nevermore1102/OpenCode_template&Date)
