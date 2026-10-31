# raw/ — 原始资料层（IMMUTABLE）

这里存放你精选的**原始来源**：源码快照、官方文档、文章、论文、数据文件、图片等。

- **只读**：LLM 从这里读取，但**永不修改**这一层。它是你的 source of truth。
- 放入新资料后，告诉 LLM「ingest 这份资料」，它会读资料、写摘要页、更新 wiki。
- 图片附件放到 `assets/`（可在 Obsidian 里设置为统一附件目录）。

## 第一份资料怎么来
- 快速起步：从参考项目复制源码快照 —
  `02/pku_demo/raw/vnpy`、`02/pku_demo/raw/vnpy_ctp`、`02/pku_demo/raw/vnpy_ctastrategy` → 本项目 `raw/`。
- 或从 Gitee 官方镜像下载 vnpy 各仓库最新分支快照（无 git 历史即可）。
- 官方文档：VeighNa 社区文档（社区版 / 精英版 / Fusion）。
