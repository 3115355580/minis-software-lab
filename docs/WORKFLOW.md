# Minis Software Lab 工作流

这是用户在 Android 手机上通过 Minis + Claude Code + GitHub 进行软件开发的长期固化流程。

## 固定资产

- GitHub 仓库：`https://github.com/3115355580/minis-software-lab`
- Claude Code 隔离安装目录：`/var/minis/shared/tools/claude-code`
- Claude Code 原生命令：`/var/minis/shared/tools/bin/claude`
- 小任务非交互入口：`/var/minis/shared/tools/bin/claude-run`
- 大项目非交互入口：`/var/minis/shared/tools/bin/claude-project`

## 环境变量

敏感值不得写入文档或聊天。

已约定使用：

- `ANTHROPIC_API_KEY`：Claude Code 中转站 API Key
- `ANTHROPIC_BASE_URL`：Claude Code 中转站 Anthropic Base URL
- `ANTHROPIC_MODEL`：Claude Code 默认模型，例如 `claude-opus-4-6`
- `GITHUB_TOKEN`：GitHub Personal Access Token
- `GITHUB_USERNAME`：GitHub 用户名
- `GITHUB_EMAIL`：Git commit 邮箱
- `GITHUB_DEFAULT_REPO`：可选，默认仓库

## 默认开发策略

用户只需要在聊天里说需求，例如：

> 做一个记账 App

助手执行：

1. 在 `/var/minis/workspace/` 创建项目目录。
2. 写入 `SPEC.md`，固化需求和边界。
3. 使用 `claude-project` 分阶段生成架构和代码。
4. 使用 shell 工具构建、测试、检查。
5. 失败后把错误交给 `claude-project --continue` 修复。
6. 每个稳定阶段提交 Git commit。
7. 可用版本打 tag，例如 `v0.1.0`。
8. 需要发布时创建 GitHub Release 并上传 APK / zip / 文档。

## 项目目录规范

仓库建议结构：

```text
minis-software-lab/
├── apps/
│   ├── prompt-manager/
│   ├── accounting-app/
│   └── habit-tracker/
├── docs/
│   ├── WORKFLOW.md
│   ├── ideas.md
│   └── roadmap.md
└── README.md
```

每个项目建议结构：

```text
project-name/
├── SPEC.md
├── PLAN.md
├── TODO.md
├── CHANGELOG.md
├── README.md
├── src/
└── build/
```

## Git 提交规范

常用 commit 前缀：

- `init:` 初始化项目
- `spec:` 需求/计划变更
- `feat:` 新功能
- `fix:` 修复问题
- `refactor:` 重构
- `test:` 测试相关
- `docs:` 文档
- `build:` 构建/打包
- `release:` 发布版本

## 回滚与溯源

- 查看历史：`git log --oneline --graph --decorate --all`
- 查看改动：`git diff`
- 反向撤销某次提交：`git revert <commit>`
- 临时查看历史版本：`git checkout <commit>`
- 版本标签：`git tag v0.1.0`

原则：

- 每完成一个阶段就 commit。
- 每个可用版本就 tag。
- 重要交付物使用 GitHub Release。
- 不把 API Key、token、密码提交到仓库。

## Claude Code 调用方式

小任务：

```sh
/var/minis/shared/tools/bin/claude-run --dir /var/minis/workspace/project "任务"
```

大项目：

```sh
/var/minis/shared/tools/bin/claude-project --dir /var/minis/workspace/project "实现里程碑 1"
```

继续上次会话：

```sh
/var/minis/shared/tools/bin/claude-project --continue --dir /var/minis/workspace/project "继续实现里程碑 2"
```

## 安全边界

- 不在聊天、脚本、仓库里输出密钥。
- 检查环境变量只输出 set / not set。
- GitHub token 虽可全权限使用，但默认不执行删除仓库等破坏性操作，除非用户明确要求。
- 发布公开仓库前检查是否包含秘密文件。
