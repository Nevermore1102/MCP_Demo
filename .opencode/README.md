# .opencode 配置说明

本目录包含 OpenCode 的项目级配置和自定义技能。

## 配置文件

### opencode.json

项目级 OpenCode 配置文件。

**重要：** 不要将敏感信息（API 密钥）提交到 Git！

#### 配置模板

使用 \`opencode.json.template\` 作为模板，创建 \`opencode.json\`：

\`\`\`bash
# 复制模板
cp .opencode/opencode.json.template .opencode/opencode.json

# 编辑配置
# 根据项目需求修改模型、权限等设置
\`\`\`

#### 配置示例

\`\`\`jsonc
{
  "$schema": "https://opencode.ai/config.json",
  
  // 模型配置
  "model": "zhipuai-coding-plan/glm-4.7",
  "small_model": "zhipuai-coding-plan/glm-4.5-air",
  
  // 权限配置
  "permission": {
    "skill": { "*": "allow" }
  },
  
  // 外部指令文件（自动加载）
  "instructions": [
    "CONTRIBUTING.md",
    "README.md"
  ]
}
\`\`\`

#### 配置选项

| 配置项 | 说明 | 示例 |
|-------|------|------|
| \`model\` | 主模型 | \`zhipuai-coding-plan/glm-4.7\` |
| \`small_model\` | 小模型（快速任务） | \`zhipuai-coding-plan/glm-4.5-air\` |
| \`permission\` | 工具和技能权限 | \`{"skill": {"*": "allow"}}\` |
| \`instructions\` | 自动加载的文档 | \`["README.md", "CONTRIBUTING.md"]\` |

---

## 技能 (Skills)

项目包含以下自定义技能（\`.opencode/skills/\`）：

| 技能 | 描述 | 使用场景 |
|------|------|----------|
| **error-diagnostic** | 错误诊断和问题解决 | 遇到错误、异常时 |
| **github-explorer** | GitHub 仓库探索和代码研究 | 查找开源实现时 |
| **ui-analyzer** | UI 设计和转换 | UI 设计转代码时 |
| **visual-analyzer** | 视觉内容分析 | 分析图表、数据可视化时 |
| **web-researcher** | 网络搜索和网页内容研究 | 搜索信息时 |

### 添加新技能

1. 在 \`.opencode/skills/\` 下创建目录
2. 添加 \`SKILL.md\` 文件

**目录结构：**
\`\`\`
.opencode/skills/my-skill/
└── SKILL.md
\`\`\`

**SKILL.md 格式：**
\`\`\`markdown
---
name: my-skill
description: 技能描述
license: MIT
---

## 我做什么

[技能功能说明]

## 何时使用我

[使用场景说明]
\`\`\`

**技能命名规范：**
- 小写字母数字
- 单个连字符分隔符
- 不以 \`-\` 开头或结尾
- 正则：\`^[a-z0-9]+(-[a-z0-9]+)*$\`

**示例：**
- ✅ \`git-release\`
- ✅ \`code-review\`
- ✅ \`typescript-patterns\`
- ❌ \`Git-Release\` (大写)
- ❌ \`git--release\` (连续连字符)

---

## MCP 服务器配置

MCP 服务器在全局配置中设置（\`~/.config/opencode/opencode.json\`），不提交到 Git。

### 配置位置

**全局配置：** \`~/.config/opencode/opencode.json\`
**项目配置：** \`.opencode/opencode.json\`（不推荐存放 MCP）

### 添加新的 MCP 服务器

编辑全局配置：

\`\`\`jsonc
{
  "mcp": {
    "my-mcp": {
      "type": "remote",
      "url": "https://api.example.com/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
\`\`\`

**安全提示：** 不要将 API 密钥提交到 Git！

### MCP 服务器类型

| 类型 | 说明 | 配置示例 |
|------|------|------|
| \`remote\` | 远程服务器 | \`{"type": "remote", "url": "https://..."}\` |
| \`local\` | 本地命令 | \`{"type": "local", "command": ["npx", "my-mcp"]}\` |

---

## Oh-My-OpenCode 插件

插件安装在全局配置中（\`~/.config/opencode/opencode.json\`）。

### 插件配置

\`\`\`jsonc
{
  "plugin": ["oh-my-opencode"]
}
\`\`\`

### 插件详细配置

**配置文件：** \`~/.config/opencode/oh-my-opencode.json\`

详细配置请参考项目根目录的 \`AGENTS.md\`。

---

## 配置优先级

OpenCode 按以下优先级加载配置（后覆盖前）：

1. **远程配置** (\`.well-known/opencode\`) - 组织默认值
2. **全局配置** (\`~/.config/opencode/opencode.json\`) - 用户偏好
3. **自定义配置** (\`OPENCODE_CONFIG\` env var) - 自定义覆盖
4. **项目配置** (\`.opencode/opencode.json\`) - 项目特定设置
5. **\`.opencode\` 目录** - 技能、命令、代理、插件

**重要：** 配置是合并而非替换！

---

## 故障排除

### 技能无法加载

**检查：**
1. SKILL.md 格式是否正确（YAML frontmatter + Markdown）
2. 技能目录结构是否正确（.opencode/skills/{name}/SKILL.md）
3. 技能命名是否符合规范（小写 + 连字符）
4. 权限配置是否正确（\`{"skill": {"*": "allow"}}\`）

### MCP 服务器无法连接

**检查：**
1. MCP 配置是否在正确的文件中（全局 vs 项目）
2. URL 和 API 密钥是否正确
3. 网络连接是否正常
4. 代理配置是否正确（如需访问国外 API）

### Oh-My-OpenCode 无法工作

**检查：**
1. 插件是否在全局配置中启用
2. 插件配置文件是否存在（\`~/.config/opencode/oh-my-opencode.json\`）
3. 模型名称是否正确
4. OpenCode 是否已重启

---

## 相关资源

- [OpenCode 官方文档](https://opencode.ai/docs/)
- [Oh-My-OpenCode 仓库](https://github.com/code-yeongyu/oh-my-opencode)
- [MCP 协议文档](https://modelcontextprotocol.io/)
