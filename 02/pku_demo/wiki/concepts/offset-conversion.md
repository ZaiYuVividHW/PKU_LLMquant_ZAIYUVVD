---
tags: [concept, futures, order]
created: 2026-09-16
updated: 2026-09-16
sources: [raw/vnpy/vnpy/trader/converter.py]
---

# 概念：开平仓转换（平今/平昨/锁仓）

中国期货特有问题：上期所/能源中心（SHFE/INE）平今仓手续费不同且必须显式区分平今（CLOSETODAY）平昨（CLOSEYESTERDAY）；其他交易所用统一 CLOSE。vnpy 用 `OffsetConverter` + `PositionHolding` 在 OMS 层自动拆单（`raw/vnpy/vnpy/trader/converter.py`）。

## PositionHolding（仓位簿记）
每个 vt_symbol 维护 long/short 的 `pos / td(今仓) / yd(昨仓)` 及对应 frozen，由 position/order/trade 事件增量更新：
- `update_trade`：按 offset 增减 td/yd；CLOSE 在 SHFE/INE 优先减昨仓，其他交易所优先减今仓、不足回补昨仓
- `calculate_frozen`：遍历活动委托，把挂单量冻结到对应 td/yd

## 三种转换模式（`convert_order_request(req, lock, net)`）
1. **默认**：仅 SHFE/INE 交易所，把 CLOSE 按 td/yd 可用量拆成 CLOSETODAY + CLOSEYESTERDAY 两笔（`convert_order_request_shfe`）
2. **lock 锁仓转换**：有今仓时不再平仓而是直接反向开仓（避免平今费用）；无今仓则先平昨再开新（`convert_order_request_lock`）
3. **net 净持仓转换**：把策略目标仓位差转成"先平后开"组合（`convert_order_request_net`）

## 触发链路
CTA 策略 `buy/sell/short/cover` 的 `lock`/`net` 参数 → `CtaEngine.send_order` → `MainEngine.convert_order_request`（转发给 OmsEngine 的 converter）→ 拆成多笔 OrderRequest 逐笔发出。注意：**转换只对非净持仓模式的合约生效**（`is_convert_required` 检查 `contract.net_position`）。

相关：[[oms-engine]] · [[cta-engine]] · [[ctp-gateway]]
