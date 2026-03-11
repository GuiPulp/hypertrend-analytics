---
name: hypertrend-analytics
description: HyperTrend 链上信用分析 + Hyperliquid 地址分析 + 自动跟单系统 + 榜单排名 + 地址监控 + 真实API集成。基于HyperTrend官方API，提供实时数据查询和交易操作。
version: 2.5.0
author: HyperTrend Team
homepage: https://www.hypertrend.top/
repository: https://github.com/GuiPulp/hypertrend-analytics
license: MIT
api_base_url: http://192.144.239.66/api
---

# HyperTrend Analytics

基于 Hyperliquid 的链上信用分析与智能交易工具。

## 🎯 功能特性

| 功能 | 描述 | 状态 |
|------|------|:----:|
| **🆕 真实API集成** | 基于HyperTrend官方API | ✅ v2.5.0 |
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
| **风险控制** | 多层风控保护本金 | ✅ |
| **收益追踪** | 实时统计跟单表现 | ✅ |

## 📦 安装

### 快速安装 (推荐)

```bash
curl -fsSL https://raw.githubusercontent.com/GuiPulp/hypertrend-analytics/main/scripts/install.sh | bash
```

### 手动安装

```bash
# 1. 克隆仓库
git clone https://github.com/GuiPulp/hypertrend-analytics.git

# 2. 移动到技能目录
mv hypertrend-analytics ~/.openclaw/skills/hypertrend-analytics

# 3. 完成！
```

## ⚠️ API 连接状态

### 当前状态

| 组件 | 状态 | 说明 |
|------|:----:|------|
| **API 文档** | ✅ 完整 | 所有接口已文档化 |
| **API 客户端** | ✅ 就绪 | Python + Shell 实现 |
| **API 服务** | ⚠️ 待确认 | `http://192.144.239.66/api` |

### 连接测试

如果 API 服务暂时不可用，技能会自动使用**模拟数据**演示功能。

**测试 API 连接：**
```bash
# 方法1: 使用测试脚本
cd ~/.openclaw/skills/hypertrend-analytics
./scripts/fetch_data.sh test

# 方法2: 直接 curl
curl -X POST http://192.144.239.66/api/apps/master \
  -H "Content-Type: application/json" \
  -d '{"page": 1, "page_size": 5, "type": "week"}'
```

**可能的问题：**
- 🔴 连接超时 - API 服务暂时不可用
- 🔴 连接重置 - 网络问题或防火墙
- 🟡 需要 VPN - 服务器在内网环境
- 🟡 服务迁移 - API 地址可能已更改

### 降级方案

当 API 不可用时，技能会：
1. 显示**模拟数据**（格式与真实数据一致）
2. 提示用户当前为演示模式
3. 继续展示功能流程

### 获取帮助

如果 API 连接有问题：
1. 联系 HyperTrend 官方确认 API 状态
2. 检查是否需要更新 API 地址
3. 确认网络环境和防火墙设置

---

### API 配置（必需）

```bash
# ~/.bashrc 或 ~/.zshrc

# HyperTrend API 基础URL
export HYPERTREND_API_URL="http://192.144.239.66/api"

# 认证Token（登录后获取）
export HYPERTREND_API_TOKEN="your_jwt_token"

# 或者使用钱包地址+签名（可选）
export HYPERTREND_WALLET_ADDRESS="0x..."
export HYPERTREND_API_SIGNATURE="0x..."
```

### 获取 API Token

1. **发送验证码**
   ```bash
   curl -X POST http://192.144.239.66/api/base/send/smscode \
     -H "Content-Type: application/json" \
     -d '{"contact": "your@email.com", "sms_type": "register"}'
   ```

2. **注册**
   ```bash
   curl -X POST http://192.144.239.66/api/base/register \
     -H "Content-Type: application/json" \
     -d '{
       "wallet_address": "0x...",
       "contact": "your@email.com",
       "sms_code": "123456",
       "invite_code": "xxx"
     }'
   ```

3. **获取 Nonce**
   ```bash
   curl -X POST http://192.144.239.66/api/base/usernonce \
     -H "Content-Type: application/json" \
     -d '{"wallet_address": "0x..."}'
   ```

4. **登录（使用钱包签名）**
   ```bash
   curl -X POST http://192.144.239.66/api/base/login \
     -H "Content-Type: application/json" \
     -d '{
       "wallet_address": "0x...",
       "signature": "0x...",
       "nonce": "123456"
     }'
   ```

5. **保存返回的 Token**
   ```bash
   export HYPERTREND_API_TOKEN="返回的jwt_token"
   ```

### 可选配置

```bash
# 跟单系统配置
export HYPERTREND_TRADING_ENABLED="true"

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

### 场景 2: 监控鲸鱼动态

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

### 场景 3: 🆕 地址实时监控

```
用户: 监控地址 0x7a3f...9d2e 的所有操作

AI输出:
🔍 地址监控已启动: 0x7a3f...9d2e

监控类型:
[✓] 仓位变化
[✓] 交易操作
[✓] 资金变动
[✓] 盈利变化
[✓] 风险预警

检查间隔: 30秒
通知方式: Telegram + 本对话

当前状态:
├─ 总仓位: $45,230
├─ 未实现盈亏: +$2,340 (+5.4%)
├─ 保证金余额: $12,450
└─ 爆仓风险: 🟢 安全

---

🚨 [实时监控] 15:32:18
📍 0x7a3f...9d2e | 开仓
币种: BTC-PERP | 方向: Long
数量: 0.5 BTC @ $68,450
杠杆: 10x | 仓位价值: $34,225

---

🚨 [实时监控] 16:15:42
📍 0x7a3f...9d2e | 平仓 (止盈)
币种: ETH-PERP | 盈利: +$1,350 (+7.0%) 🎉

---

⚠️ [风险预警] 18:45:23
📍 0x7a3f...9d2e | 爆仓风险
币种: SOL-PERP | 爆仓距离: 3.3% 🔴
建议: 减仓或追加保证金
```

### 场景 4: 榜单查询

```
用户: 查看引力指数榜 top10

AI输出:
🏆 HyperTrend 引力指数榜 (实时)

🥇 1. 0x7a3f...9d2e
   引力指数: 982/1000 (大师级⭐⭐⭐⭐⭐)
   六芒星: 风控182 | 胜率190 | 杠杆142
   24h变化: +3位 ↑

🥈 2. 0x9c1b...4f8a
   引力指数: 965/1000 (大师级)
   24h变化: -1位 ↓

🥉 3. 0x3d2e...8b5c
   引力指数: 958/1000 (大师级)
   24h变化: 新晋榜单 🆕

📈 榜单动态: 新晋3个 | 跌出3个
```

### 场景 5: 平台跟单交易

```
用户: 连接我的 HyperTrend 账户

AI输出:
🔗 HyperTrend 账户绑定 (钱包签名)

Step 1: 访问 https://www.hypertrend.top/
Step 2: 连接钱包并生成签名
Step 3: 输入钱包地址和签名

✅ 账户绑定成功！
钱包: 0x7a3f...9d2e
余额: $12,450.00
签名有效期: 7天

开始跟单?
├─ 🥇 交易宗师 (引力982, +156%)
├─ 🥈 稳健大师 (引力921, 回撤5%)
└─ 🥉 波段高手 (引力876)

确认开始? (y/n)
```

### 场景 6: 自动跟单系统

```
用户: 启动自动跟单，使用稳健策略

AI输出:
🤖 HyperTrend 自动跟单系统启动

策略: 稳健收益 (Conservative)
筛选条件:
├─ 引力指数 ≥ 800
├─ 胜率 ≥ 70%
└─ 最大杠杆 ≤ 8x

✅ 发现 3 个符合条件的交易者
总收益: +$170 (+7.08%)
```

## 🔌 核心工具

### 分析工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `analyze_address` | 分析单个HL地址 | `analyze_address("0x...")` |
| `compare_addresses` | 对比多个地址 | `compare_addresses(["0xA", "0xB"])` |
| `scan_whales` | 扫描鲸鱼仓位 | `scan_whales(500000)` |

### 🆕 地址监控工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `add_address_monitor` | 添加监控 | `add_address_monitor("0x...", options)` |
| `get_monitor_list` | 监控列表 | `get_monitor_list()` |
| `get_address_monitor_detail` | 监控详情 | `get_address_monitor_detail("0x...", "7d")` |
| `pause_address_monitor` | 暂停监控 | `pause_address_monitor("0x...")` |
| `resume_address_monitor` | 恢复监控 | `resume_address_monitor("0x...")` |
| `remove_address_monitor` | 移除监控 | `remove_address_monitor("0x...")` |
| `get_monitor_alerts` | 预警历史 | `get_monitor_alerts("0x...", "24h")` |
| `export_monitor_data` | 导出数据 | `export_monitor_data("0x...", "csv")` |

### 榜单工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `get_leaderboard` | 获取榜单 | `get_leaderboard("gravity", "all", 10)` |
| `get_leaderboard_changes` | 榜单变化 | `get_leaderboard_changes("gravity", "1d")` |
| `get_address_ranking` | 地址排名 | `get_address_ranking("0x...")` |

### 平台跟单工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `connect_hypertrend_wallet` | 连接钱包 | `connect_hypertrend_wallet("0x...", "sig")` |
| `get_platform_leaders` | 获取带单者 | `get_platform_leaders({min_gravity: 800})` |
| `start_platform_copytrading` | 开始跟单 | `start_platform_copytrading("0x...", 5000)` |
| `get_platform_copytrading_status` | 跟单状态 | `get_platform_copytrading_status()` |

### 跟单工具

| 工具 | 功能 | 示例 |
|------|------|------|
| `start_copytrading` | 启动自动跟单 | `start_copytrading("conservative")` |
| `stop_copytrading` | 暂停跟单 | `stop_copytrading()` |
| `emergency_stop` | 紧急止损 | `emergency_stop()` |
| `get_copytrading_status` | 跟单状态 | `get_copytrading_status()` |

## 🆕 监控类型

| 监控 | 说明 | 通知内容 |
|------|------|----------|
| **仓位变化** | 加仓、减仓、调杠杆 | 变动详情、保证金变化 |
| **交易操作** | 开仓、平仓、部分平仓 | 交易对、方向、盈亏 |
| **资金变动** | 充值、提现、盈亏结算 | 金额、余额、类型 |
| **盈利追踪** | 已实现/未实现盈亏 | 累计盈亏、日统计 |
| **风险预警** | 爆仓风险、大额变动 | 风险等级、建议操作 |

详细监控文档见 [ADDRESS_MONITORING.md](ADDRESS_MONITORING.md)

## 🆕 榜单类型

| 榜单 | 说明 | 周期 |
|------|------|------|
| **引力指数榜** | 六芒星综合评分排名 | 实时 |
| **收益榜** | 按收益率/金额排名 | 24h/7d/30d |
| **胜率榜** | 按交易胜率排名 | 7d/30d |
| **带单榜** | 按带单收益排名 | 7d/30d |
| **涨幅榜** | 按24h涨幅排名 | 实时 |
| **新贵榜** | 新晋优质交易者 | 7d |

详细榜单文档见 [LEADERBOARD.md](LEADERBOARD.md)

## 🆕 跟单策略

| 策略 | 引力指数 | 胜率 | 杠杆 | 风险等级 |
|------|:--------:|:----:|:----:|:--------:|
| **保守型** | ≥800 | ≥70% | ≤8x | 🟢 低 |
| **平衡型** | ≥650 | ≥60% | ≤12x | 🟡 中 |
| **激进型** | ≥500 | ≥55% | ≤20x | 🔴 高 |

详细跟单文档见 [COPYTRADING.md](COPYTRADING.md)

## 📊 六芒星信用模型

| 维度 | 权重 | 满分 | 指标 |
|------|:----:|:----:|------|
| 风控能力 | 20% | 200 | 回撤、止损、仓位 |
| 胜率矩阵 | 20% | 200 | 胜率、盈亏比、夏普 |
| 杠杆艺术 | 15% | 150 | 杠杆效率、爆仓风险 |
| 市场阶段 | 15% | 150 | 趋势判断、周期识别 |
| 链上足迹 | 15% | 150 | 交易频次、Gas效率 |
| 收益质量 | 15% | 150 | 收益稳定、资金来源 |

**引力指数等级:**
- ⭐⭐⭐⭐⭐ 950-1000: 大师级
- ⭐⭐⭐⭐ 800-950: 精英级
- ⭐⭐⭐ 600-800: 优秀级

## 🎨 品牌规范

- **六芒星**: 两个重叠等边三角形 (▲ + ▼)
- **主色**: `#00D4FF` (青色)
- **话题标签**: `#HyperTrend` `#OnChainCredit`

## 📁 文件结构

```
hypertrend-analytics/
├── SKILL.md                    # 本文件
├── README.md                   # 项目说明
├── COPYTRADING.md              # 自动跟单系统
├── LEADERBOARD.md              # 榜单系统
├── PLATFORM_COPYTRADING.md     # 平台跟单
├── ADDRESS_MONITORING.md       # 🆕 地址监控
├── CHANGELOG.md                # 版本日志
├── CONTRIBUTING.md             # 贡献指南
├── LICENSE                     # MIT许可证
├── package.json               # 包信息 (v2.4.0)
├── examples/                  # 使用示例
│   ├── address-analysis.md
│   └── whale-monitoring.md
└── scripts/
    └── install.sh
```

## 📝 更新日志

### v2.4.0 (2026-03-11)
- 🆕 新增地址实时监控系统
- 🆕 支持仓位/交易/资金/盈利/风险监控
- 🆕 支持自定义通知阈值
- 🆕 支持监控数据导出

### v2.3.0 (2026-03-11)
- 🆕 新增 HyperTrend 平台跟单
- 🆕 钱包签名认证

### v2.2.0 (2026-03-10)
- 🆕 新增榜单系统
- 🆕 新增榜单变化追踪

### v2.1.0 (2026-03-09)
- 🆕 新增自动跟单系统
- 🆕 新增风险控制

## 🤝 贡献

欢迎提交 PR 和 Issue！

## 📄 许可证

MIT License

## 🔗 链接

- 官网: https://www.hypertrend.top/
- Twitter: https://x.com/gohypertrend
- Telegram: https://t.me/HyperTrendHQ

---

**⚠️ 风险提示:** 加密货币交易存在高风险，请只用可承受损失的资金。

**Maintained by HyperTrend Team**
