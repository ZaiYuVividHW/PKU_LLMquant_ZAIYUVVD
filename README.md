# 2610PKU_quantllm — LLM 驱动量化交易学习 wiki

基于 [llm-wiki.md](llm-wiki.md) 模式构建的**个人知识库**：主题是 **基于 VeighNa (vnpy) 的量化交易系统开发**。由 LLM 增量地阅读资料、写摘要页、维护交叉引用与综合结论；你负责找资料、提问、判断方向。

> 参考项目：`02/pku_demo/` 是课程自带的**成熟参考 wiki**（同主题，已完成源码精读 + 3 个自研项目），只读、勿改动，可当建库深度与格式的范例。

## 快速开始
1. 先读 [AGENTS.md](AGENTS.md)——它是本仓库的 schema，规定了目录、约定与工作流（任何 LLM 会话动手前都先读它）。
2. 把第一份资料放进 `raw/`（可从 `02/pku_demo/raw/` 复制 vnpy 源码快照，或从 Gitee 下载），然后对 LLM 说「ingest 这份资料」。
3. 用 [Obsidian](https://obsidian.md) 打开本目录浏览：`[[wiki/...]]` 双向链接、graph view 看知识结构。
4. 需要时 `git init` 纳管版本（wiki 就是一堆 markdown，天然适合 git）。

## 目录结构
```
.
├── AGENTS.md          # schema：LLM 的工作规范
├── llm-wiki.md        # 原始理念文档（只读）
├── raw/               # 原始资料层（只读，source of truth）
├── wiki/              # LLM 生成并维护的知识页面
│   ├── overview.md    # 总览：状态 / 主线问题 / 下一步
│   ├── index.md       # 内容索引
│   ├── log.md         # 时间日志（append-only）
│   ├── sources/       # 每份资料的摘要页
│   ├── concepts/      # 概念页
│   ├── entities/      # 模块 / 类实体页
│   └── code/          # 自研程序的设计笔记
└── projects/          # 自研量化程序（代码）
```

## 工作流（详见 AGENTS.md）
- **Ingest**：资料入 `raw/` → LLM 读资料、写摘要页、更新 concepts/entities、刷新 index/overview、追加 log。
- **Query**：提问 → LLM 先读 index 定位、再综合回答并引用页面；有价值的结论写回 wiki。
- **Lint**：定期健康检查（矛盾、过时、孤儿页、缺页、缺交叉引用）。
- **Dev**：在 `projects/` 写程序，设计笔记入 `wiki/code/`。

## 工具建议
- **Obsidian**：把本目录作为 vault 打开；装 Marp（幻灯片）、Dataview（按 frontmatter 查询）。
- **git**：`git init` 后获得版本历史、分支与协作。
