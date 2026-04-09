# wechat-multi

macOS 微信多开工具（小绿书）。

## 安装

```bash
npx skills add joeseesun/wechat-multi
```

# WeChat Multi-Instance (小绿书)

## 命令映射

| 用户说 | 执行命令 |
|--------|----------|
| "打开两个微信" / "微信双开" | `sudo ~/bin/wechat-multi.sh auto --force` |
| "打开N个微信" / "微信多开N个" | `sudo ~/bin/wechat-multi.sh multi N --force` |
| "再开一个微信" | `open -n /Applications/小绿书.app` |
| "微信更新后重建" / "修复微信多开" | `sudo ~/bin/wechat-multi.sh rebuild --force` |
| "关闭所有微信" | `sudo ~/bin/wechat-multi.sh kill` |

## 注意事项

- 脚本需要 `sudo`，已在 sudoers 配置免密码，直接执行无需确认
- 微信更新后副本会失效，运行 `rebuild` 重建
- 副本名为 `小绿书.app`（双开）或 `小绿书1.app`、`小绿书2.app`...（多开）
- 如果提示签名错误，也用 `rebuild` 修复

## License

MIT

## 📱 关注作者

如果这个项目对你有帮助，欢迎关注我获取更多技术分享：

- **X (Twitter)**: [@vista8](https://x.com/vista8)
- **微信公众号「向阳乔木推荐看」**:

<p align="center">
  <img src="https://github.com/joeseesun/terminal-boost/raw/main/assets/wechat-qr.jpg?raw=true" alt="向阳乔木推荐看公众号二维码" width="300">
</p>
