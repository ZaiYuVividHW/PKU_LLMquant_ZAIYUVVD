---
tags: [overview]
created: 2026-10-31
updated: 2026-10-31
---

# Overview — VeighNa 量化交易学习 wiki

## 目标
系统学习基于 VeighNa (vnpy) 的量化交易系统开发：框架架构、核心模块、策略开发、回测与实盘，并在此基础上开发自己的量化程序。用 LLM 驱动的方式建库与维护知识（见 [llm-wiki.md](../llm-wiki.md) 模式）。

## 当前状态
- **刚初始化**（2026-10-31）：目录结构与 schema（[AGENTS.md](../AGENTS.md)）就绪，wiki 页面为空，等待 ingest 第一份资料。
- 参考项目：`02/pku_demo` 是课程自带的成熟参考 wiki（同主题，已完成源码精读 + 3 个自研项目），仅作对照范例，**只读**。

## 主线问题（随学习推进更新）
1. vnpy 整体架构：事件驱动引擎如何组织各模块？
2. 网关层如何对接柜台（CTP 等）？
3. CTA 策略引擎：策略模板、数据流、下单流程？
4. 回测系统：数据加载、撮合模拟、绩效评估？
5. 如何在其上构建自己的交易系统？
6. 因子研究方法论：如何避免过拟合、做稳健的因子研究？

## 下一步
- [ ] 把第一份资料（vnpy 源码快照 / 官方文档）放入 `raw/`，开始 ingest
- [ ] 从 `02/pku_demo/raw/` 复制 vnpy / vnpy_ctp / vnpy_ctastrategy 源码到本项目 `raw/`（或从 Gitee 官方镜像下载）
- [ ] 参照 `02/pku_demo` 建库深度与页面格式，逐步填充 concepts / entities / sources
- [ ] `git init`（如需版本管理与协作）

## 相关页面
- [[index]] · [[log]]
