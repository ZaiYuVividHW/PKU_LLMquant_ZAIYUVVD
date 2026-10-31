---
tags: [index]
created: 2026-09-16
updated: 2026-09-19
---

# Index — wiki 目录

## Sources（资料摘要）
- [[vnpy-source]] — vnpy 主框架源码概览：本体是骨架，能力靠插件装配（2026-09-16）
- [[vnpy-ctp-source]] — vnpy_ctp 网关源码概览：双 API 结构、CTP 6.7.11（2026-09-16）
- [[vnpy-ctastrategy-source]] — vnpy_ctastrategy 源码概览：模板/引擎/回测三件套（2026-09-16）
- [[alpha-researcher]] — alpha_researcher 参考项目存根页：vnag+LLM 流水线、csi300 数据源位置说明（2026-09-19）

## Concepts（概念）
- [[event-driven-architecture]] — 事件驱动架构与事件类型设计（含合约级专属事件）
- [[vt-symbol-naming]] — vt_ 前缀统一命名体系（跨网关唯一 ID）
- [[offset-conversion]] — 开平仓转换：平今/平昨拆单、锁仓、净持仓三种模式
- [[bar-synthesis]] — BarGenerator K线合成与 ArrayManager 指标计算
- [[stop-order]] — 本地停止单：实盘触发逻辑与回测差异
- [[backtesting-model]] — 回测撮合与绩效模型（成本、逐日盯市、Sharpe/EWM/RGR）
- [[factor-overfitting]] — 因子挖掘过拟合：选择偏差实证、四阶段防治与样本消耗审计（2026-09-18）

## Entities（模块 / 类）
- [[event-engine]] — EventEngine 事件总线（vnpy.event）
- [[main-engine]] — MainEngine 装配中心与门面
- [[oms-engine]] — OmsEngine 订单管理与内存缓存
- [[base-gateway]] — BaseGateway 网关抽象契约
- [[data-objects]] — 核心数据对象与常量枚举（object.py / constant.py）
- [[ctp-gateway]] — CtpGateway：Md/Td 双 API、状态机、查询轮转
- [[cta-engine]] — CtaEngine 实盘引擎：三张映射表与事件链
- [[cta-template]] — CtaTemplate / TargetPosTemplate 策略模板
- [[backtesting-engine]] — BacktestingEngine 回测引擎与实盘差异对照

## Code（自研程序设计笔记）
- [[ctp-demo-notes]] — ctp_demo：最小化 CTP 底层 API DEMO，SimNow 实测跑通（含踩坑记录）
- [[ctp-breakout-demo-notes]] — ctp_breakout_demo：突破触发下单闭环，SimNow 实测成交
- [[alpha-mining-demo-notes]] — alpha_mining_demo：LLM 驱动因子挖掘，vnpy.alpha 评估闭环跑通（四方向实测，含 lockbox 纪律）

## Meta
- [[overview]] — 全局总览与计划
- [[log]] — 时间日志
