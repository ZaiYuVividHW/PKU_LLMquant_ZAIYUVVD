---
tags: [source, cta, strategy, backtesting]
created: 2026-09-16
updated: 2026-09-16
sources: [raw/vnpy_ctastrategy]
---

# 来源：vnpy_ctastrategy 源码

- 位置：`raw/vnpy_ctastrategy`（Gitee main 快照，版本 1.4.1）
- 结构：`template.py`（策略模板基类）、`engine.py`（实盘引擎 CtaEngine，~970 行）、`backtesting.py`（回测引擎 BacktestingEngine，~1270 行）、`base.py`（常量/StopOrder）、`ui/`（PySide6 界面）、`strategies/`（示例策略）
- 作为 App 挂载：`CtaStrategyApp(BaseApp)` → `add_app` 后由 `CtaEngine` 提供全部功能

## 关键结论
- 实盘与回测共用同一套 `CtaTemplate` 接口：策略只调 `cta_engine` 的方法，两个引擎各自实现（鸭子类型而非继承），见 [[cta-template]]
- 实盘引擎核心映射三张表：`symbol_strategy_map`（行情→策略）、`orderid_strategy_map`（委托→策略）、`strategy_orderid_map`（策略→委托集合），见 [[cta-engine]]
- 回测撮合是简化模型：bar 模式下限价单用 bar 高低价穿越判断、以开盘价为最优成交价；全量成交、无部分成交；见 [[backtesting-engine]]
- 2026 版本新增了 EWM Sharpe 与 RGR Ratio（收益-风险-稳健综合指标）等绩效指标

## 已建相关页面
[[cta-engine]] · [[cta-template]] · [[backtesting-engine]] · [[stop-order]] · [[bar-synthesis]]
