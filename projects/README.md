# projects/ — 自研量化程序

这里放你**自己开发的量化程序**（普通代码目录，各自独立、git 管理）。

## 约定
- 每个程序一个子目录，如 `projects/ctp_demo/`、`projects/alpha_mining_demo/`。
- 每个程序配一份自己的 `README.md`（怎么跑、依赖、配置）。
- 架构决策、设计笔记、踩坑记录写到 `wiki/code/`，并与 concepts / entities 互链。
- 程序运行产物（如 `runs/`、`cache/`、图表、中间数据）默认不入库（见根目录 `.gitignore`）。

## 参考范例
课程参考项目 `02/pku_demo/projects/` 下有 3 个已跑通的自研程序可对照：
- `ctp_demo` / `ctp_breakout_demo`：底层 CTP API 连接 / 下单闭环（SimNow 实测）
- `alpha_mining_demo`：LLM 驱动因子挖掘（vnpy.alpha 评估闭环）
