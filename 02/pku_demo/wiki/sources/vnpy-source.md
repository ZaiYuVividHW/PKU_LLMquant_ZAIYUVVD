---
tags: [source, vnpy, framework]
created: 2026-09-16
updated: 2026-09-16
sources: [raw/vnpy]
---

# 来源：vnpy 主框架源码

- 位置：`raw/vnpy`（Gitee main 分支快照）
- 结构：`vnpy/vnpy/` 下四个子包 —— `event`（事件引擎）、`trader`（交易核心）、`chart`（K线图表）、`rpc`（ZeroMQ RPC）、`alpha`（机器学习 Alpha 因子研究，较新模块）；另有 `examples/`、`docs/`、`tests/`
- 核心依赖：事件驱动全部解耦；技术指标依赖 `talib`；数据库/数据服务通过插件模块 `vnpy_<name>` 动态加载（`database.py`、`datafeed.py` 中 `import_module`）

## 关键结论
- vnpy 本体只是一个**骨架**：所有交易能力（网关 vnpy_ctp、应用 vnpy_ctastrategy、数据库 vnpy_sqlite、数据服务 vnpy_datayes 等）都是独立 pip 包，通过 `add_gateway` / `add_app` / `get_database` 动态装配
- `MainEngine` 是装配中心：持有 gateways / engines / apps 三个 dict，并把 OmsEngine 的 get_xxx 方法直接绑到自己身上（`raw/vnpy/vnpy/trader/engine.py#MainEngine.init_engines`）
- 配置与数据目录：优先当前目录的 `.vntrader/`，否则用户主目录（`utility.py#_get_trader_dir`）；`MainEngine.__init__` 会 `os.chdir(TRADER_DIR)`

## 已建相关页面
[[main-engine]] · [[event-engine]] · [[oms-engine]] · [[base-gateway]] · [[data-objects]] · [[bar-synthesis]]
