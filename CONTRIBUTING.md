# 贡献指南

感谢您考虑为项目贡献！

## 📋 如何贡献

1. **Fork** 本仓库
2. **创建特性分支** (`git checkout -b feature/AmazingFeature`)
3. **提交更改** (`git commit -m 'feat: add some AmazingFeature'`)
4. **推送到分支** (`git push origin feature/AmazingFeature`)
5. **开启 Pull Request**

## 🎯 开发流程

### 分支策略

```
main (生产/稳定版本)
  ↑
develop (开发/集成分支)
  ↑
feature/* (功能分支)
fix/* (修复分支)
```

- 所有 PR 必须指向 `develop` 分支
- 指向 `main` 的 PR 会被 CI 自动拒绝

### Conventional Commits

提交信息格式：
```
<type>(<scope>): <subject>

<body>
```

**类型：**
- `feat`: 新功能
- `fix`: Bug 修复
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

### 代码规范

- 遵循 AGENTS.md 中的代码规范
- 运行 `npm run lint` 检查代码风格
- 运行 `npm run typecheck` 检查类型
- 运行 `npm test` 确保测试通过

### 测试要求

- 为新功能添加测试
- 确保所有测试通过
- 测试覆盖率不低于 80%

### Pull Request 要求

- PR 标题遵循 Conventional Commits 规范
- 描述清楚更改内容和原因
- 关联相关 Issue（如适用）
- 通过所有 CI 检查
- 至少一个审查者批准

## 🐛 报告 Bug

使用 Issue 模板报告 bug，提供：

- 清晰的 bug 描述
- 复现步骤
- 期望行为 vs 实际行为
- 环境信息

## 💡 功能请求

使用 Issue 模板请求新功能，提供：

- 清晰的问题描述
- 建议的解决方案
- 替代方案（如有）

## 📧 开发命令

```bash
# 安装依赖
npm install

# 开发
npm run dev

# 构建
npm run build

# 测试
npm test

# Lint
npm run lint

# 类型检查
npm run typecheck
```

## 📚 相关资源

- [AGENTS.md](AGENTS.md) - OpenCode 项目配置
- [README.md](README.md) - 项目说明
- [OpenCode 官方文档](https://opencode.ai/docs/)
- [Oh-My-OpenCode](https://github.com/code-yeongyu/oh-my-opencode)

## 🤝 行为准则

请遵守 [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)。

---

感谢你的贡献！🎉
