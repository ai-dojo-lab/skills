# OpenClaw Skills 备份

自动备份的 OpenClaw Skills 集合

## 备份说明

- **来源**：`~/.openclaw/skills/`
- **备份位置**：`/Users/pipixia/openclaw/backup/skills/`
- **备份频率**：每天 17:00 自动备份
- **自动提交**：备份后自动提交到 GitHub

---

## 已备份的 Skills

| 序号 | Skill 名称 | 功能说明 |
|------|-----------|----------|
| 1 | **6551-daily-news** | 每日新闻推送 - 自动推送热点新闻到 Telegram |
| 2 | **ai-en-teacher** | 🎓 雅思私教 AI - 为成人学习者提供雅思备考指导，目标 6.0-6.5 分 + 旅游工作英语 |
| 3 | **agent-playbook** | 📚 Agent 实战指南 - 包含实用的 AI Agent 提示词、技能和最佳实践 |
| 4 | **agent-reach** | 🌐 AI 互联网能力 - 让 AI 能读取 Twitter、Reddit、YouTube、B 站、小红书等网站内容 |
| 5 | **axton-obsidian-visual-skills** | 🎨 Obsidian 画图神器 - 用自然语言生成手绘风格图表（流程图/思维导图/时间线等） |
| 6 | **daily-news** | 📰 每日新闻 MCP - 自动获取和推送每日热点新闻 |
| 7 | **legal-research-skill** | ⚖️ 法律检索专家 - 中国法律全领域系统性检索，覆盖劳动争议/合同纠纷/侵权/婚姻/刑事等 |
| 8 | **lossless-claw** | 💾 无损记忆 - OpenClaw 作者推荐的长记忆方案，持久化存储对话历史 |
| 9 | **MoneyPrinterV2** | 🎬 自动化赚钱工具 - 自动制作 YouTube 短视频、自动发推、自动带货、自动发邮件 |
| 10 | **OpenMAIC** | 🎓 AI 多智能体课堂 - 将任何主题变成互动式 AI 课堂，支持幻灯片/测验/交互式模拟 |
| 11 | **opencli-skill** | 🌐 社交媒体 CLI - 通过 Chrome 登录会话访问 B 站/知乎/微博/YouTube/小红书/Reddit 等 |
| 12 | **openclaw-skills-security** | 🔒 安全中心 - Skill 安全审计工具，安装前验证技能安全性 |
| 13 | **trending-skills** | 🔥 热门技能集合 - 收录 ClawHub 上 trending 的热门 Skills |

---

## 自动化脚本

**备份脚本位置**：`/Users/pipixia/.openclaw/workspace/scripts/backup-skills.sh`

**手动执行**：
```bash
bash /Users/pipixia/.openclaw/workspace/scripts/backup-skills.sh
```

**功能**：
- ✅ 自动备份所有新 skills
- ✅ 重复的 skill 自动跳过
- ✅ 自动生成 README.md（包含功能说明）
- ✅ 自动提交到 GitHub
- ✅ 发送 Telegram 通知

---

## Cron 定时任务

```cron
0 17 * * * bash /Users/pipixia/.openclaw/workspace/scripts/backup-skills.sh
```

**任务名**：`backup:skills-daily-1700`
**执行时间**：每天下午 5 点（Asia/Shanghai）

---

## 分类索引

### 📚 学习类
- **ai-en-teacher** - 雅思私教
- **OpenMAIC** - AI 多智能体课堂

### 🛠️ 工具类
- **axton-obsidian-visual-skills** - Obsidian 画图
- **lossless-claw** - 长记忆存储
- **opencli-skill** - 社交媒体 CLI
- **agent-reach** - 互联网访问能力

### 📰 资讯类
- **6551-daily-news** - 每日新闻推送
- **daily-news** - 新闻 MCP
- **trending-skills** - 热门技能

### ⚖️ 专业类
- **legal-research-skill** - 法律检索

### 🔒 安全类
- **openclaw-skills-security** - 安全审计
- **agent-playbook** - 最佳实践指南

### 💰 自动化类
- **MoneyPrinterV2** - 自动化赚钱工具

---

## 使用方式

### 1. 从备份安装
```bash
cd /Users/pipixia/openclaw/backup/skills
cp -r <skill-name> ~/.openclaw/skills/
```

### 2. 重启 Gateway
```bash
openclaw gateway restart
```

### 3. 验证安装
```bash
openclaw skills list
```

---

## 相关链接

- **GitHub 仓库**：https://github.com/ai-dojo-lab/skills
- **OpenClaw 官方**：https://github.com/openclaw/openclaw
- **ClawHub**：https://clawhub.ai

---

*最后更新：2026-03-23 19:55:21*
*共备份 13 个 Skills*