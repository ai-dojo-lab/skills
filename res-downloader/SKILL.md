---
name: res-downloader
version: 1.0.0
description: Use putyy/res-downloader (爱享素材下载器) to sniff and download online resources (video/audio/images/m3u8/live streams) by running a local proxy and capturing requests.
metadata:
  {
    "openclaw": {
      "emoji": "⬇️",
      "requires": { "gui": true, "network": true },
      "notes": "This is a GUI app that installs a certificate and uses a local system proxy (127.0.0.1:8899)."
    }
  }
---

# res-downloader（爱享素材下载器）

Repo: https://github.com/putyy/res-downloader
Docs: https://res.putyy.com/

## 适用场景
- 视频号/小程序/抖音/快手/小红书 等资源嗅探下载
- m3u8、直播流、音频、图片等

## 使用步骤（关键）
1. 安装软件（务必允许：安装证书文件 + 网络访问）
2. 打开软件 → 左上角点击「启动代理」
3. 选择要获取的资源类型（默认全部）
4. 在外部打开资源页面（浏览器/客户端）
5. 回到软件首页，资源列表会出现 → 选择并下载

## 代理/证书注意事项
- 系统代理：127.0.0.1:8899
- 如果关闭软件后无法上网：检查并手动关闭系统代理

## 交互策略（对 Jarvis）
- 当用户说“下载某个平台视频/资源”且不要求命令行：优先使用 res-downloader。
- 若用户要求命令行/自动化：改用 yt-dlp / aria2 / wget（视站点而定）。
