---
name: tvclaw
description: TradingView-Claw（本地封装版）：用于查询 TradingView 热门标的、搜索 symbol、查看 OHLCV/技术指标（终端表格展示）。默认仅启用看盘/指标，不做下单。
---

# tvclaw（TradingView-Claw 本地封装）

> 说明：上游仓库 `helenigtxu/TradingView-Claw` 的代码结构与其 SKILL.md 声明不一致（import 路径问题），我已在本机修复为可运行版本。

## 本机安装位置
- Repo：`/Users/bruce/.openclaw/workspace/TradingView-Claw`
- Python venv（uv + Python 3.12）：`/Users/bruce/.openclaw/workspace/TradingView-Claw/.venv`

## 环境变量（可选）
- `TRADINGVIEW_SESSION`：可选。不设置也能跑 trending/search/部分 chart（使用公开 scanner）。
- **不要配置** `BROKER_API_KEY/SECRET`（默认不启用真实交易）。

## 命令（只读/看盘）
在 repo 目录下运行：

```bash
cd /Users/bruce/.openclaw/workspace/TradingView-Claw
source .venv/bin/activate
python tvclaw.py charts trending -l 10
python tvclaw.py charts search "BTC"
python tvclaw.py chart "BINANCE:BTCUSDT"
```

## 语义触发建议
- 用户说「看看热门标的」→ `tvclaw charts trending`
- 用户说「搜索 TradingView 的 xxx」→ `tvclaw charts search xxx`
- 用户说「画/看 K 线 xxx」→ `tvclaw chart <symbol>`

## 安全边界
- 本 skill 默认只做“数据/指标展示”。
- 如果用户要求交易（buy/sell），必须二次确认，并优先使用模拟盘/测试环境。
