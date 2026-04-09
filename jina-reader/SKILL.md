---
name: jina-reader
version: 1.0.0
description: Use r.jina.ai to fetch readable正文/正文 text from almost any web page (including X/Twitter) by prefixing the URL with https://r.jina.ai/http(s)://...
metadata:
  {
    "openclaw": {
      "emoji": "📄",
      "requires": { "network": true },
      "notes": "Great fallback when a site has a login wall or heavy JS."
    }
  }
---

# r.jina.ai (Jina Reader) — 网页正文抓取

## 什么时候用
- 网页太重/JS 太多
- 有登录墙（尤其 X/Twitter）
- 你只想要正文（可读文本）

## 用法
把原始 URL 前面加上 `https://r.jina.ai/`：

- 原始：`https://example.com/a/b`
- 读取正文：`https://r.jina.ai/https://example.com/a/b`

X/Twitter 示例：
- 原始：`https://x.com/<user>/status/<id>`
- 读取正文：`https://r.jina.ai/https://x.com/<user>/status/<id>`

## 常用命令（终端）
```bash
curl -L "https://r.jina.ai/https://x.com/USER/status/ID"
```

## 注意
- 返回的是可读正文，不保证包含所有互动/媒体资源。
- 如遇到 403/空内容，换用浏览器或 Agent-Reach/xreach。
