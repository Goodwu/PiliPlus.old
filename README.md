# PiliPlus（每日自动同步的上游副本）

本仓库是 [bggRGjQaUbCoE/PiliPlus](https://github.com/bggRGjQaUbCoE/PiliPlus) 的自动同步副本。因 GitHub 单账号对同一仓库网络只能有一个 fork，故以此独立仓库 + 定时镜像方式维护。

- **看代码请切到 [`main`](https://github.com/Goodwu/PiliPlus/tree/main) 分支**；`dev`、`dom` 与全部 tag 一并同步。
- 当前分支 `ci/upstream-sync` 为仓库默认分支，仅承载同步 workflow（`.github/workflows/sync-upstream.yml`）。GitHub 的 `schedule` 触发只能来自默认分支，故本分支不参与同步、不会被覆盖。
- 每天 UTC 01:30（北京时间 09:30）自动运行，也可在 Actions 页面手动触发（workflow_dispatch）。
- 同步强制更新上游现有的同名分支；`main`、`dev`、`dom` 上的自有提交仍会被覆盖，自有开发请使用独立分支。本仓库独有的分支会保留，上游删除分支时也不再自动删除本仓库对应分支。全部 tag 继续按上游镜像更新与删除。
- `feature/ohos` 与 `ci/upstream-sync` 明确排除于分支推送之外，即使上游出现同名分支也不会被覆盖；同步期间这两个分支的新提交同样不会被回退。
- 同步推送使用仓库内置 `GITHUB_TOKEN`，按 GitHub 规则不会再触发本仓库内来自上游的其它 CI workflow。
