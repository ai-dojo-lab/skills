# OpenClaw Skills 备份

自动备份的 OpenClaw Skills 集合

## 备份说明

- **来源**：`~/.openclaw/skills/`
- **备份位置**：`/Users/pipixia/openclaw/backup/skills/`
- **备份频率**：每天 17:00 自动备份
- **自动提交**：备份后自动提交到 GitHub

## 已备份的 Skills

| 序号 | Skill 名称 | 备份时间 |
|------|-----------|----------|
| 1 | MoneyPrinterV2 | 2026-03-23 |
| 2 | OpenMAIC | 2026-03-19 |
| 3 | agent-playbook | 2026-03-19 |
| 4 | agent-reach | 2026-03-23 |
| 5 | agents | 2026-03-24 |
| 6 | ai-en-teacher | 2026-03-21 |
| 7 | anthropics-skills | 2026-03-23 |
| 8 | assets | 2026-03-24 |
| 9 | axton-obsidian-visual-skills | 2026-03-16 |
| 10 | blockbeats-skill | 2026-03-24 |
| 11 | daily-news | 2026-03-17 |
| 12 | evaluations | 2026-03-24 |
| 13 | examples | 2026-03-24 |
| 14 | legal-research-skill | 2026-03-18 |
| 15 | ljg-skills | 2026-03-23 |
| 16 | lossless-claw | 2026-03-19 |
| 17 | openai-skills | 2026-03-23 |
| 18 | openclaw-skills-security | 2026-03-19 |
| 19 | opencli-skill | 2026-03-19 |
| 20 | reference | 2026-03-24 |
| 21 | scripts | 2026-03-24 |
| 22 | themes | 2026-03-24 |
| 23 | trending-skills | 2026-03-19 |

## 自动化脚本

备份脚本位置：`/Users/pipixia/.openclaw/workspace/scripts/backup-skills.sh`

手动执行：
```bash
bash /Users/pipixia/.openclaw/workspace/scripts/backup-skills.sh
```

## Cron 任务

```cron
0 17 * * * bash /Users/pipixia/.openclaw/workspace/scripts/backup-skills.sh
```

---

*最后更新：2026-03-27 19:59:12*
