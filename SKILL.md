---
name: hypertrend-analytics
description: HyperTrend 链上信用分析 + Hyperliquid 地址分析 + 自动跟单系统 + 榜单排名 + 地址监控 + 智能风险偏好匹配。查询引力指数、六芒星评分、分析HL地址、监控鲸鱼、自动跟单、榜单追踪、实时监控、智能推荐。
version: 2.5.0
author: HyperTrend Team
homepage: https://www.hypertrend.top/
repository: https://github.com/hypertrend/hypertrend-analytics-skill
license: MIT
---

# HyperTrend Analytics

基于 Hyperliquid 的链上信用分析与智能交易工具。

## 🎯 功能特性

| 功能 | 描述 | 状态 |
|------|------|:----:|
| **引力指数查询** | HyperTrend六芒星信用评分 | ✅ |
| **HL地址分析** | 持仓、杠杆、盈亏分析 | ✅ |
| **鲸鱼监控** | >$500K大仓位追踪 | ✅ |
| **地址对比** | 多地址交易表现对比 | ✅ |
| **数据推文** | 基于真实数据生成内容 | ✅ |
| **自动跟单** | 智能筛选并自动跟随交易者 | ✅ |
| **榜单系统** | 引力/收益/胜率/带单榜单 | ✅ v2.2.0 |
| **变化追踪** | 榜单排名变化监控 | ✅ v2.2.0 |
| **平台跟单** | HyperTrend平台直接跟单交易 | ✅ v2.3.0 |
| **地址监控** | 实时追踪地址操作和资金 | ✅ v2.4.0 |
| **🆕 风险偏好匹配** | 根据用户风险偏好智能推荐交易者 | ✅ v2.5.0 |
| **风险控制** | 多层风控保护本金 | ✅ |
| **收益追踪** | 实时统计跟单表现 | ✅ |

## 🆕 v2.5.0 新特性：智能风险偏好匹配

根据用户的风险偏好，智能匹配并推荐最适合的交易者。

### 风险偏好类型

| 类型 | 英文名 | 描述 | 筛选条件 |
|------|--------|------|---------|
| **保守型** | conservative | 低风险，追求稳定，回撤<10% | 胜率>60%, 杠杆<5x |
| **稳健型** | moderate | 中等风险，平衡收益与风险 | 胜率>55%, 杠杆<10x |
| **进取型** | aggressive | 高风险高收益，追求超额回报 | 胜率>45%, 杠杆<20x |
| **量化型** | quantitative | 数据驱动，关注交易频率 | 胜率>50%, 最少交易次数 |

### 使用示例

```bash
# 命令行使用
python3 scripts/risk_match.py conservative    # 保守型推荐
python3 scripts/risk_match.py moderate        # 稳健型推荐
python3 scripts/risk_match.py aggressive      # 进取型推荐
python3 scripts/risk_match.py quantitative    # 量化型推荐
```

### OpenClaw 对话使用

```
用户: 我是稳健型投资者，帮我推荐几个合适的交易者跟单

AI: 
🎯 HyperTrend 智能跟单推荐
📊 风险偏好: 稳健型
📝 中等风险，平衡收益与风险，最大回撤控制在20%以内

【推荐 #1】匹配度: 93.26/100
├─ 地址: 0xe117d3d94b30f7e7aa...
├─ 榜单排名: #24
├─ 日收益: $7156.40
├─ 胜率: 100.0%
├─ 最大回撤: 0.1%
├─ 预估杠杆: 1.0x
└─ 💡 推荐理由: 胜率高达 100.0%，稳定性优秀；最大回撤仅 0.1%，风控出色

💰 跟单操作:
  查看详情: openclaw hypertrend address <地址>
  开始跟单: openclaw hypertrend copytrade <地址> --amount <金额>
```

## 📦 安装

### 快速安装 (推荐)

```bash
curl -fsSL https://raw.githubusercontent.com/hypertrend/hypertrend-analytics-skill/main/scripts/install.sh | bash
```

### 手动安装

```bash
# 1. 克隆仓库
git clone https://github.com/hypertrend/hypertrend-analytics-skill.git

# 2. 移动到技能目录
mv hypertrend-analytics-skill ~/.openclaw/skills/hypertrend-analytics

# 3. 完成！
```

## ⚙️ 配置

### 环境变量 (可选)

```bash
# ~/.bashrc 或 ~/.zshrc

# HyperTrend API Key (如需私有数据)
export HYPERTREND_API_KEY="your_key"

# 跟单系统配置 (如需自动跟单)
export HYPERTREND_TRADING_ENABLED="true"
export HYPERTREND_PRIVATE_KEY="your_wallet_private_key"

# 通知设置
export HYPERTREND_ALERT_TELEGRAM="chat_id"
export HYPERTREND_ALERT_DISCORD="webhook_url"

# 监控阈值
export HYPERTREND_WHALE_THRESHOLD="500000"
export HYPERTREND_LIQUIDATION_ALERT="5"
```

## 🚀 使用方法

### 场景 1: 分析交易者信用

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

### 场景 2: 🆕 智能风险偏好匹配

详见上方 v2.5.0 新特性章节。

### 场景 3: 监控鲸鱼动态

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

## 📚 API 文档

详见 [API_DOCUMENTATION.md](./API_DOCUMENTATION.md)

## 🔧 开发计划

- [x] v2.0.0: 基础跟单功能
- [x] v2.1.0: 鲸鱼监控系统
- [x] v2.2.0: 榜单系统 + 变化追踪
- [x] v2.3.0: 平台跟单功能
- [x] v2.4.0: 地址实时监控
- [x] **v2.5.0: 智能风险偏好匹配** 🆕
- [ ] v2.6.0: AI 策略分析
- [ ] v2.7.0: 社交交易功能

## 🤝 贡献

欢迎提交 PR 和 Issue！

## 📄 许可证

MIT License