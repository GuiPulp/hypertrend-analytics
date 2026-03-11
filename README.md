# 🎯 HyperTrend Analytics

[![OpenClaw](https://img.shields.io/badge/OpenClaw-Skill-blue)](https://openclaw.ai)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Version](https://img.shields.io/badge/Version-2.1.0-orange)](package.json)
[![CopyTrading](https://img.shields.io/badge/CopyTrading-✅-brightgreen)](COPYTRADING.md)

**Hyperliquid 链上信用分析 + 智能交易数据 + 自动跟单系统**

[快速开始](#-快速开始) • [功能特性](#-功能特性) • [安装指南](#-安装) • [使用示例](#-使用示例) • [🆕 自动跟单](#-自动跟单系统)

</div>

---

## 📖 简介

HyperTrend Analytics 是一个专为 **OpenClaw AI Agent** 设计的技能包，提供：

- 📊 **链上信用分析** - HyperTrend 引力指数和六芒星评分
- 🐋 **鲸鱼监控** - Hyperliquid 大仓位实时追踪
- 📝 **数据推文** - 基于真实数据生成营销内容
- 🤖 **🆕 自动跟单** - 智能筛选并自动跟随优质交易者

通过整合 **HyperTrend 引力指数** 和 **Hyperliquid 链上数据**，帮助用户发现聪明钱、分析交易行为、自动复制优质策略。

---

## ✨ 功能特性

| 功能 | 描述 | 状态 |
|------|------|:----:|
| **引力指数查询** | HyperTrend 六芒星信用评分 | ✅ |
| **HL 地址分析** | 持仓、杠杆、盈亏分析 | ✅ |
| **鲸鱼监控** | >$500K 大仓位追踪 | ✅ |
| **地址对比** | 多地址交易表现对比 | ✅ |
| **数据推文** | 基于真实数据生成内容 | ✅ |
| **🆕 自动跟单** | 智能筛选并自动跟随交易者 | ✅ v2.1.0 |
| **🆕 风险控制** | 多层风控保护本金 | ✅ v2.1.0 |
| **🆕 收益追踪** | 实时统计跟单表现 | ✅ v2.1.0 |

---

## 🚀 快速开始

### 一键安装 (推荐)

```bash
curl -fsSL https://raw.githubusercontent.com/your-username/hypertrend-analytics/main/scripts/install.sh | bash
```

### 手动安装

```bash
# 1. 克隆仓库
git clone https://github.com/your-username/hypertrend-analytics.git

# 2. 移动到技能目录
mv hypertrend-analytics ~/.openclaw/skills/hypertrend-analytics

# 3. 完成！
```

---

## ⚙️ 配置

### 基础配置

```bash
# ~/.bashrc 或 ~/.zshrc

# HyperTrend API Key (可选)
export HYPERTREND_API_KEY="your_api_key_here"

# 通知设置
export HYPERTREND_ALERT_TELEGRAM="your_chat_id"
export HYPERTREND_ALERT_DISCORD="your_webhook_url"
```

### 跟单系统配置 (如需自动跟单)

```bash
# 启用自动跟单
export HYPERTREND_TRADING_ENABLED="true"

# 钱包私钥 (用于执行交易)
export HYPERTREND_PRIVATE_KEY="your_wallet_private_key"

# 默认策略 (conservative/balanced/aggressive)
export HYPERTREND_DEFAULT_STRATEGY="balanced"
```

---

## 📖 使用示例

### 1️⃣ 分析交易者信用

```
用户: 分析这个HL地址: 0x7a3f...9d2e

AI输出:
📊 地址分析报告: 0x7a3f...9d2e

🎯 引力指数: 782/1000 (优秀级)
├─ 风控能力: 142/200 (优秀)
├─ 胜率矩阵: 168/200 (优秀)
├─ 杠杆艺术: 89/150 (良好)
├─ 市场阶段: 145/150 (卓越)
├─ 链上足迹: 128/150 (良好)
└─ 收益质量: 110/150 (良好)

📈 当前持仓:
├─ BTC-PERP: 2.5 BTC @ $67,200
│   杠杆: 10x | 爆仓价: $60,480
└─ ETH-PERP: 15 ETH @ $3,850

💡 评估: 风控优秀，适合作为带单参考
```

### 2️⃣ 监控鲸鱼动态

```
用户: 查看今日HL鲸鱼动态

AI输出:
🐋 Hyperliquid 鲸鱼监控 (3月9日)

新增鲸鱼 (24h): 3个
├─ 0x4e2b...8a10: $2.1M BTC Long
├─ 0x9c1d...4f8a: $890K ETH Short
└─ 0x3d2e...8b5c: $650K SOL Long

⚠️  liquidation 风险:
🔴 0x3e7b...9a4c: 距离爆仓 2.3%

市场情绪: 62% Long / 38% Short (偏多)
```

### 3️⃣ 生成数据推文

```
用户: 基于今日HL数据生成推文

AI输出:
📊 今日Hyperliquid数据洞察 (3月9日)

💥 24h爆仓: $750M
🐋 BTC >$1M仓位: +12个 (增持)
🎯 聪明钱信号: 引力指数>800的地址80%增持

当散户恐慌时，链上信用在买入。

#HyperTrend #OnChainCredit #BTC
```

---

## 🤖 自动跟单系统

### 🚀 启动跟单

```
用户: 启动自动跟单，使用稳健策略

AI输出:
🤖 HyperTrend 自动跟单系统启动

策略: 稳健收益 (Conservative)
筛选条件:
├─ 引力指数 ≥ 800
├─ 胜率 ≥ 70%
├─ 最大杠杆 ≤ 8x
└─ 最大回撤 ≤ 15%

✅ 发现 3 个符合条件的交易者:
├─ 0x7a3f...9d2e (引力 850, 胜率 78%)
├─ 0x9c1b...4f8a (引力 820, 胜率 72%)
└─ 0x3d2e...8b5c (引力 805, 胜率 75%)

初始资金: $10,000
单仓上限: $1,000 (10%)
最大持仓: 3 个

确认启动跟单? (y/n)
```

### 📊 查看状态

```
用户: 查看跟单状态

AI输出:
📊 HyperTrend 跟单状态报告

运行时间: 3天 4小时 32分钟
当前策略: 稳健收益

【跟随的交易者】
🥇 0x7a3f...9d2e
├─ 引力指数: 850 (精英级)
├─ 跟随资金: $1,000
├─ 未实现盈亏: +$125 (+12.5%)
└─ 状态: ✅ 优秀

🥈 0x9c1b...4f8a
├─ 引力指数: 820 (精英级)
├─ 跟随资金: $800
├─ 未实现盈亏: +$45 (+5.6%)
└─ 状态: ✅ 良好

【收益统计】
├─ 总投入: $2,400
├─ 当前净值: $2,570
├─ 总收益: +$170 (+7.08%)
└─ 风控状态: 🟢 正常
```

### 🛡️ 风险控制

```
用户: 执行紧急止损

AI输出:
🚨 紧急止损执行中...

正在平掉所有持仓:
├─ 平仓 BTC Long: 实现盈亏 +$118
├─ 平仓 ETH Long: 实现盈亏 -$15
└─ 平仓 SOL Long: 实现盈亏 +$42

总实现盈亏: +$145 (+6.0%)
资金已转回钱包: $10,145

跟单系统已停止。
```

### 📋 跟单策略

| 策略 | 引力指数 | 胜率 | 杠杆 | 风险等级 | 适合人群 |
|------|:--------:|:----:|:----:|:--------:|----------|
| **保守型** | ≥800 | ≥70% | ≤8x | 🟢 低 | 风险厌恶者 |
| **平衡型** | ≥650 | ≥60% | ≤12x | 🟡 中 | 大多数用户 |
| **激进型** | ≥500 | ≥55% | ≤20x | 🔴 高 | 高风险偏好 |

详细跟单文档见 [COPYTRADING.md](COPYTRADING.md)

---

## 🔌 核心工具

### 分析工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `analyze_address` | 分析单个HL地址 | `analyze_address("0x...")` |
| `compare_addresses` | 对比多个地址 | `compare_addresses(["0xA", "0xB"])` |
| `scan_whales` | 扫描鲸鱼仓位 | `scan_whales(500000)` |
| `get_leaderboard` | 带单排行榜 | `get_leaderboard("7d", "pnl")` |

### 跟单工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `start_copytrading` | 启动自动跟单 | `start_copytrading("conservative")` |
| `stop_copytrading` | 暂停跟单 | `stop_copytrading()` |
| `emergency_stop` | 紧急止损 | `emergency_stop()` |
| `get_copytrading_status` | 跟单状态 | `get_copytrading_status()` |
| `adjust_strategy` | 调整策略 | `adjust_strategy("aggressive")` |

### 内容工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `generate_tweet` | 生成推文 | `generate_tweet("market")` |

---

## 📊 六芒星信用模型

| 维度 | 权重 | 满分 | 评估指标 |
|------|:----:|:----:|----------|
| 风控能力 | 20% | 200 | 最大回撤、止损纪律、仓位管理 |
| 胜率矩阵 | 20% | 200 | 胜率、盈亏比、夏普比率 |
| 杠杆艺术 | 15% | 150 | 杠杆使用效率、爆仓风险控制 |
| 市场阶段 | 15% | 150 | 趋势判断、周期识别 |
| 链上足迹 | 15% | 150 | 交易频次、Gas效率、合约交互 |
| 收益质量 | 15% | 150 | 收益稳定性、资金来源合法性 |

**引力指数等级:**
- ⭐⭐⭐⭐⭐ 950-1000: 大师级
- ⭐⭐⭐⭐ 800-950: 精英级
- ⭐⭐⭐ 600-800: 优秀级
- ⭐⭐ 400-600: 良好级

---

## 🎨 品牌规范

### 六芒星图形
- 两个重叠的等边三角形 (▲ + ▼)
- 顺时针六个顶点：风控→胜率→杠杆→市场→足迹→收益

### 配色
| 用途 | 颜色 | 色值 |
|------|------|------|
| 主色 | 青色 | `#00D4FF` |
| 辅色 | 深蓝 | `#1A1A2E` |
| 警告 | 红色 | `#FF4757` |
| 成功 | 绿色 | `#2ED573` |

### 话题标签
- `#HyperTrend` (必带)
- `#OnChainCredit`
- `#DeFi`
- `#Hyperliquid`

---

## 📁 项目结构

```
hypertrend-analytics/
├── LICENSE                      # MIT 许可证
├── README.md                    # 项目说明 (本文件)
├── SKILL.md                     # OpenClaw 技能主文档
├── COPYTRADING.md               # 🆕 自动跟单系统文档
├── CHANGELOG.md                 # 版本更新日志
├── CONTRIBUTING.md              # 贡献指南
├── GITHUB_UPLOAD_GUIDE.md       # GitHub 上传指南
├── package.json                 # 包信息
├── .gitignore                   # Git 忽略文件
├── examples/                    # 使用示例
│   ├── address-analysis.md     # 地址分析示例
│   └── whale-monitoring.md     # 鲸鱼监控示例
├── scripts/                     # 辅助脚本
│   └── install.sh              # 一键安装脚本
└── .github/                     # GitHub 配置
    └── workflows/              # CI/CD 工作流
```

---

## 🤝 贡献

欢迎提交 PR 和 Issue！

### 提交规范
- `feat:` 新功能
- `fix:` Bug 修复
- `docs:` 文档更新
- `example:` 示例添加

---

## ⚠️ 风险提示

**自动跟单存在以下风险：**

1. **市场风险** - 加密货币价格波动大，可能损失全部本金
2. **策略风险** - 历史表现不代表未来，策略可能失效
3. **技术风险** - 系统故障、网络延迟可能影响交易
4. **流动性风险** - 极端行情可能无法成交

**请确保：**
- 只用可承受损失的闲置资金
- 了解所有风险后再使用
- 设置合理的风险控制参数
- 不要投入无法承受损失的资金

---

## 📄 许可证

[MIT](LICENSE) © HyperTrend Team

---

## 🔗 相关链接

- 🌐 官网: https://www.hypertrend.top/
- 🐦 Twitter: https://x.com/gohypertrend
- 💬 Telegram: https://t.me/HyperTrendHQ
- 🎮 Discord: https://discord.gg/MEFA8Rbq
- 📚 Hyperliquid API: https://hyperliquid.gitbook.io/

---

<div align="center">

**Built with ❤️ by HyperTrend Team**

[↑ Back to Top](#-hypertrend-analytics)

</div>
