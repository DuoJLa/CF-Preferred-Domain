<div align="center">

# 🌐 Cloudflare Domain 排名监控

<p>
  <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white" alt="GitHub Actions"/>
  <img src="https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"/>
</p>

**每天自动推送 Cloudflare 优选域名 TOP 5 到 您的Telegram Bot**

<p>
  <a href="#-功能特性">功能特性</a> •
  <a href="#-快速开始">快速开始</a> •
  <a href="#-效果预览">效果预览</a> •
  <a href="#-配置说明">配置说明</a>
</p>

---

</div>

## ✨ 功能特性

- 🤖 **全自动运行** - 基于 GitHub Actions，无需服务器
- ⏰ **定时推送** - 每天北京时间 8:00 准时推送
- 📊 **详细数据** - 包含综合评分、延迟、丢包率、三网表现
- 🚀 **高效稳定** - 轻量级 Python 脚本，运行快速
- 💰 **完全免费** - 零成本部署和运行
- 🔔 **即时通知** - Telegram 消息推送，随时随地查看

## 📱 效果预览

🌐 Cloudflare优选域名 TOP 5
📅 数据时间: 2026-01-13 00:00:00

━━━━━━━━━━━━━━━━━━━━

🥇 第1名
📍 域名: xxxxx.xxx
⭐ 综合评分: 100
⚡ 平均延迟: 45ms
📊 丢包率: 0.07%
📶 三网表现:

移动: 53ms

联通: 182ms

电信: 50ms

━━━━━━━━━━━━━━━━━━━━

... (共5条记录)

## 🚀 配置流程

### 1️⃣ 创建 Telegram Bot

1. 打开 Telegram，搜索 `@BotFather`
2. 发送 `/newbot` 创建新机器人
3. 按提示设置名称和用户名
4. **保存返回的 Token** (格式: `123456:ABCdefGHI...`)

### 2️⃣ 获取 Chat ID

**个人聊天：**
- 搜索 `@userinfobot` 或 `@RawDataBot`
- 点击 Start，获取你的 Chat ID

**群组聊天：**
1. 将 Bot 添加到群组
2. 访问：`https://api.telegram.org/bot你的TOKEN/getUpdates`
3. 找到 `"chat":{"id":-100...}` 的值

### 3️⃣ Fork 本仓库

点击右上角 ⭐ **Star** 后，再点击 **Fork** 按钮

### 4️⃣ 配置 Secrets

进入你 Fork 的仓库：

`Settings` → `Secrets and variables` → `Actions` → `New repository secret`

添加以下两个密钥：

| Name | Value | 说明 |
|------|-------|------|
| `TELEGRAM_BOT_TOKEN` | `123456:ABCdef...` | 你的 Bot Token |
| `TELEGRAM_CHAT_ID` | `123456789` 或 `-100123456` | 你的 Chat ID |

### 5️⃣ 启用 Actions

1. 进入 `Actions` 标签页
2. 点击绿色按钮启用 Workflows
3. 点击左侧 `CF IP Daily Monitor`
4. 点击 `Run workflow` → `Run workflow` 立即测试

### ✅ 完成！

现在每天早上 8:00 会自动推送数据到你的 Telegram 🎉

## ⚙️ 配置说明

### 修改推送时间

编辑 `.github/workflows/daily_push.yml` 文件：

```yaml
  # 北京时间 8:00 (UTC 0:00)
  - cron: '0 0 * * *'
  
  # 北京时间 12:00 (UTC 4:00)  
  # - cron: '0 4 * * *'
  
  # 每天两次：8:00 和 20:00
  # - cron: '0 0,12 * * *'
```
### 修改推送数量

编辑 scripts/notify.py 第 19 行：

```yaml
# 推送前 5 名
return data.get("data", {}).get("good", [])[:5]

# 改为推送前 10 名
return data.get("data", {}).get("good", [])[:10]

```

## ❓ 常见问题

<details> <summary><b>为什么收不到消息？</b></summary>
✅ 检查 Bot Token 和 Chat ID 是否正确

✅ 确认没有屏蔽 Bot

✅ 群组需要将 Bot 设为管理员（可选）

✅ 手动运行 workflow 测试

</details> <details> <summary><b>Actions 执行失败怎么办？</b></summary>
进入 Actions 标签查看日志

检查 Secrets 配置是否正确

确认仓库已启用 Actions

查看是否有 API 限流

</details> <details> <summary><b>可以推送到其他平台吗？</b></summary>
可以！修改 scripts/notify.py 中的推送逻辑：

微信：使用企业微信机器人或 Server酱

钉钉：使用钉钉机器人 Webhook

邮件：使用 SMTP 发送邮件

Discord：使用 Discord Webhook

</details> <details> <summary><b>数据来源是什么？</b></summary>
数据来自 vps789.com 提供的公开 API，包含：

Cloudflare CDN 节点测速数据

中国三大运营商（移动/联通/电信）实测

每日更新一次

</details> <details> <summary><b>评分指标</b></summary>

综合评分 (avgScore): 越低越好，综合考虑延迟和丢包率

平均延迟: 三网延迟的平均值 (毫秒)

丢包率: 数据包丢失百分比

三网表现: 移动/联通/电信各自的延迟数据
</details>


## 感谢vps789.com提供的公开数据，本项目调用接口返回数据

## ⭐ Star
如果这个项目对你有帮助，请点个 Star ⭐ 支持一下！








