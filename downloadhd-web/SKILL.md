---
name: downloadhd-web
version: 1.0.0
description: Fallback web downloader: use https://downloadhd.net to parse & download videos/images/audio from many platforms when the primary downloader (res-downloader) can’t be used.
metadata:
  {
    "openclaw": {
      "emoji": "🌐",
      "requires": { "browser": true, "network": true },
      "notes": "Fallback only; prefer res-downloader skill first."
    }
  }
---

# DownloadHD（网页解析下载）

Site: https://downloadhd.net/

## 什么时候用
- 主下载器 `res-downloader` 不方便/不能用/抓不到
- 需要快速用网页方式解析下载

## 支持（来自推文）
抖音/快手/微博/小红书/YouTube/TikTok/Facebook/Telegram/Instagram 等 100+ 平台。

## 使用步骤
1. 打开 https://downloadhd.net/
2. 粘贴目标视频/图片/音频链接
3. 点击解析
4. 选择合适清晰度/格式下载

## 注意
- 网页解析站点可能会变更规则/限流/广告；尽量不要在上面输入任何账号密码。
- 对于需要登录才能看的内容：优先使用 `res-downloader` 代理抓包方式。
