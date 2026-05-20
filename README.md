# minis-software-lab

Android 上的 Minis + Claude Code 软件实验室。

仓库用途：

- 保存通过 Minis / Claude Code 生成的软件项目源码；
- 记录需求、计划、变更和发布历史；
- 支持 GitHub 溯源、回滚、标签和 Release；
- 让聊天记录删除后，项目流程和资产仍然可恢复。

## 固化工作流

见：[`docs/WORKFLOW.md`](docs/WORKFLOW.md)

## 推荐目录

```text
apps/       # 各个软件项目
docs/       # 工作流、想法、路线图
releases/   # 交付说明或发布索引
```

## 原则

- 每个项目先写 `SPEC.md`。
- 大项目使用里程碑分阶段实现。
- 每完成稳定阶段就 commit。
- 可用版本打 tag。
- APK / zip / 文档可通过 GitHub Release 归档。
- 不提交 API Key、token、密码等秘密。
