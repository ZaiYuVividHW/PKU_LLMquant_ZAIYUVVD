---
tags: [overview]
created: 2026-09-16
updated: 2026-09-19
---

# Overview — VeighNa 量化交易学习 wiki

## 目标
系统学习基于 VeighNa (vnpy) 的量化交易系统开发：框架架构、核心模块、策略开发、回测与实盘，并在此基础上开发自己的量化程序。

## 当前状态
- **源码精读完成**（2026-09-16）：3 来源页、7 概念页、9 实体页（见 [[index]]）
- 已精读：event 引擎、trader 核心（engine/gateway/object/converter/utility/database/datafeed）、ctp_gateway.py、ctastrategy 全部核心（base/template/engine/backtesting）
- 尚未精读（按需 ingest 候选）：vnpy/ui（GUI）、vnpy/chart、vnpy/rpc、vnpy_ctastrategy/ui、vnpy_ctp/api 生成层；vnpy/alpha 已在实战中使用（见下）
- **自研程序 3 个**（`projects/`，详见 [[index]] Code 节）：
  - `ctp_demo` / `ctp_breakout_demo`：纯底层 CTP API 的连接/订阅与突破下单闭环，SimNow 实测跑通
  - `alpha_mining_demo`：LLM 驱动因子挖掘，**四方向实测完成**（量价共振、反转、动量证伪、跳空），防过拟合纪律逐方向升级（平台扫描、噪声锚点、试验台账、lockbox）
- 注意：当前工作区是 D 盘原始工作区（git 仓库）的副本，缺 `.git`、`raw/alpha_researcher`（因子数据）与 `raw/assets`；详见 [[wiki/sources/alpha-researcher]] 的位置说明

## 主线问题（随学习推进更新）
1. ✅ vnpy 整体架构：事件驱动引擎如何组织各模块？→ [[event-driven-architecture]]、[[main-engine]]
2. ✅ 网关层如何对接柜台？→ [[base-gateway]]、[[ctp-gateway]]（CTP 实现已精读 + 底层 API 直连实测）
3. ✅ CTA 策略引擎：策略模板、数据流、下单流程 → [[cta-engine]]、[[cta-template]]
4. ✅ 回测系统：数据加载、撮合模拟、绩效评估 → [[backtesting-engine]]、[[backtesting-model]]
5. 🔶 如何在其上构建自己的交易系统？已走通两条路径：底层 API 直连（CTP demo ×2）与因子研究闭环（alpha 挖掘）；**尚未做**：基于 CtaTemplate/CtaEngine 写一个正式 CTA 策略并回测
6. 🔶 因子研究方法论：选择偏差防治框架已成型（[[factor-overfitting]]），待落地项见其"剩余盲点"节（成本口径、point-in-time 池、滚动监控）

## 下一步
- [ ] 在 projects/ 写第一个 CtaTemplate 策略 + BacktestingEngine 回测（主线问题 5 收尾）
- [ ] D 盘原工作区收尾 git（gap 方向产物未提交、final_rev 等旧产物的删除未提交），并决定 C/D 两副本的主从关系
- [ ] alpha 方向可选增强：行业/市值中性化、扣费后组合回测、近三年滚动 RankIC 监控
- [ ] 精读 ui / chart 等未覆盖模块（按需）

## 相关页面
- [[index]] · [[log]]
