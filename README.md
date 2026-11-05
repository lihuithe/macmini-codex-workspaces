# macmini-codex-workspaces

Mac mini 上的 Codex 操作工作空间集合。

## 这是什么

这个仓库用来集中管理在 Mac mini 上运行 Codex（AI 编码代理）时的**工作空间**：

- 每个任务/项目一个独立子目录,互不干扰
- 存放任务说明、脚本、配置和运行产物
- 便于在远程登录 Mac mini 时快速切换上下文、复用同类任务的做法

## 设计目标

| 目标 | 说明 |
| --- | --- |
| 隔离 | 不同任务的代码与产物分目录存放,避免互相污染 |
| 可复现 | 任务输入、执行脚本、输出都留在仓库里,事后可回溯 |
| 可迁移 | 换机器或重建环境时,拉下仓库即可继续 |
| 轻量 | 只保留必要的工作空间骨架,不塞入大文件或敏感信息 |

## 目录约定

```
macmini-codex-workspaces/
├── README.md
└── workspaces/          # 每个工作空间一个子目录（按需创建）
    └── <task-name>/
        ├── README.md    # 任务目标与执行说明
        └── ...          # 脚本、配置、产物
```

## 使用方式

```bash
git clone git@github.com:lihuithe/macmini-codex-workspaces.git
cd macmini-codex-workspaces

# 新建一个工作空间
mkdir -p workspaces/my-task
```

在 Mac mini 上让 Codex 执行任务时,把该任务的工作目录指向 `workspaces/<task-name>`,执行过程与结果都会留在这个目录里。

## 注意事项

- 不要提交密钥、Token、证书等敏感凭据
- 大体积产物（模型权重、数据集、构建缓存）不入库,改用外部存储并在任务 README 中注明位置
- 本仓库为公开仓库,提交前请自行确认内容可公开

## 环境

- 主机：Mac mini（Apple Silicon）
- 代理工具：Codex CLI / Codex 应用
- 版本管理：Git + GitHub
