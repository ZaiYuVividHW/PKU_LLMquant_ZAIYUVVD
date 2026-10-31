---
tags: [source, gateway, ctp, futures]
created: 2026-09-16
updated: 2026-09-16
sources: [raw/vnpy_ctp]
---

# 来源：vnpy_ctp 网关源码

- 位置：`raw/vnpy_ctp`（Gitee main 分支快照，版本 6.7.11.4，对应 CTP API 6.7.11）
- 结构：`gateway/ctp_gateway.py`（~900 行，纯 Python 封装层）；`api/` 为脚本生成的 ctypes 封装（`ctp_struct.py` ~7000 行、`ctp_constant.py`、`ctp_typedef.py`、`vnctpmd/vnctptd` C++ 扩展）；`script/` 是生成脚本
- 仓库 70MB 主要来自预编译的各平台 `.whl` / `.dll` / `.so`

## 关键结论
- 网关拆成两条连接：`CtpMdApi`（行情，仅订阅+登录）与 `CtpTdApi`（交易：认证→登录→确认结算单→查合约→推单），见 [[ctp-gateway]]
- CTP 回报全部是 dict（data/error），由映射表（`STATUS_CTP2VT` 等）翻译成 vnpy 统一对象
- 定时查询：注册 EVENT_TIMER，每 2 秒轮流查资金/持仓（`ctp_gateway.py#CtpGateway.process_timer_event`）

## 已建相关页面
[[ctp-gateway]] · [[base-gateway]] · [[data-objects]]
