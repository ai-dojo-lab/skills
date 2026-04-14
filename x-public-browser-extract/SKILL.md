---
name: x-public-browser-extract
description: Read public X/Twitter posts without X API keys by using OpenClaw browser tools first, then fallback to r.jina.ai. Use when the user provides an x.com/twitter.com status URL and wants正文 text, links, tx hashes, wallet addresses, images, or on-chain clues extracted.
version: 1.0.0
user_invocable: true
---

# x-public-browser-extract

用于公开 X/Twitter 链接的无 API 提取。

核心原则：
- 不依赖 `X_API_KEY`
- 优先走浏览器
- 先拿正文文本，再拿图片列表
- 文本不够时再用截图/图片分析或 `r.jina.ai`
- 提取出 `tx hash`、地址、外链后，继续打开 explorer 跟进

## 什么时候用

- 用户给了 `x.com/.../status/...` 或 `twitter.com/.../status/...`
- 用户要你读取正文、链接、图片、地址、交易哈希
- 用户要你分析推文里的链上事件
- 用户没有给 X API key，但你仍然需要读公开内容

## 默认流程

1. 先确认 URL 是公开推文链接。
2. 用浏览器打开原始链接。
3. 立即在页面里取：
   - 页面正文文本
   - 页面图片列表
   - 页面里的链接
4. 从文本和链接里提取：
   - URL
   - EVM 地址
   - 64 hex 交易哈希
   - 代币数量和时间
5. 如果文本不完整：
   - 继续看 `document.images`
   - 需要时做页面截图并走图片分析
   - 仍不够时，用 `r.jina.ai` 读正文
6. 如果拿到了 `etherscan` / `address` / `tx` 链接，继续打开并跟进分析。

## 浏览器优先做法

### 1. 打开推文

优先：

```text
browser_navigate("https://x.com/<user>/status/<id>")
```

### 2. 抽正文文本

优先用页面执行 JS，目标是接近 Hermes 那种 `document.body.innerText` 效果：

```js
() => document.body ? document.body.innerText : ""
```

如果你在当前工具面里用的是 Playwright 风格包装，也可以：

```js
async (page) => {
  return {
    url: page.url(),
    title: await page.title(),
    text: await page.locator("body").innerText()
  };
}
```

### 3. 抽图片和链接

```js
() => ({
  images: [...document.images].map(img => ({
    src: img.src,
    alt: img.alt || ""
  })),
  links: [...document.querySelectorAll("a")].map(a => ({
    text: (a.innerText || "").trim(),
    href: a.href
  }))
})
```

### 4. 关键判断

- 如果正文里已经出现了 `etherscan.io/tx/...`，直接提取并继续
- 如果链接列表没有 `etherscan`，但正文里有被换行拆开的 URL，也要人工拼接理解
- 如果图片是关键信息载体，继续对图片或截图做分析

## `r.jina.ai` 回退

满足任一情况就回退：

- X 页面只有登录墙/壳
- 浏览器正文太少
- 页面动态内容抽不出来

用法：

```text
https://r.jina.ai/http://x.com/<user>/status/<id>
https://r.jina.ai/https://x.com/<user>/status/<id>
```

目标仍然是：
- 先拿正文
- 再抽 URL / tx / address / amount / time

## 提取目标

至少留意这些模式：

- 交易哈希：`0x` + 64 hex
- EVM 地址：`0x` + 40 hex
- Explorer 链接：
  - `etherscan.io/tx/...`
  - `etherscan.io/address/...`
  - 其他链浏览器同类链接
- 媒体图片 URL：`pbs.twimg.com/media/...`

## 分析输出建议

返回结果尽量结构化：

- 原始推文链接
- 正文摘录
- 提取出的外链
- 提取出的交易哈希
- 提取出的地址
- 提取出的图片 URL
- 你对事件链路的简短判断
- 哪些信息是直接确认的，哪些只是推断

## 注意

- 不要把“看不到链接列表”误判成“推文没有链接”，正文可能把链接拆行显示
- X 页面上的 DOM 链接不一定包含正文里出现的完整外链
- 对链上安全事件，优先区分：
  - 正文直接确认
  - 图片 OCR/视觉确认
  - 你自己的推断
