# HyperTrend API 文档

## 基础信息

- **Base URL**: `https://app.hypertrend.top/api`
- **协议**: HTTPS
- **数据格式**: JSON
- **编码**: UTF-8

## 接口分类

| 类别 | 接口路径 | 认证要求 |
|------|---------|---------|
| 🔓 公开接口 | `/open/*` | 无需认证 |
| 🔒 用户接口 | `/apps/*` | 需要 JWT Token |
| 🔒 账户接口 | `/account/*` | 需要 JWT Token |
| 🔒 跟单接口 | `/trade/*` | 需要 JWT Token |
| 🔒 基础接口 | `/base/*` | 部分需要 |

---

## 🔓 公开接口（无需认证）

### 1. 单量统计

```http
POST /open/billings
```

**请求参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| page | int | 否 | 页码，默认 1 |
| page_size | int | 否 | 每页数量，默认 10 |
| type | string | 否 | 统计类型: `day`/`week`/`month` |

**响应数据：**

```json
{
  "code": 200,
  "msg": "success",
  "data": {
    "list": [
      {
        "address": "0x3999...3336",
        "rankno": 1,
        "avalue": "8228620.05",
        "pnl": "41389.6",
        "roi": "0.01",
        "vlm": "480442266.42",
        "total": 15839,
        "spot": 1670,
        "perpetuals": 13501
      }
    ],
    "page": 1,
    "page_size": 10,
    "total": 10527
  }
}
```

**字段说明：**

| 字段 | 说明 |
|------|------|
| address | 钱包地址 |
| rankno | 排名 |
| avalue | 账户总资产 |
| pnl | 收益 |
| roi | 收益率 |
| vlm | 交易量 |
| total | 开单总数 |
| spot | 现货交易数 |
| perpetuals | 合约交易数 |

---

### 2. 交易量统计

```http
POST /open/vlm
```

**请求参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| page | int | 否 | 页码 |
| page_size | int | 否 | 每页数量 |
| type | string | 否 | `day`/`week`/`month`/`allTime` |

**响应数据：**

```json
{
  "code": 200,
  "msg": "success",
  "data": {
    "list": [
      {
        "name": "BTC",
        "maxLeverage": 50,
        "dayNtlVlm": "123456789",
        "oraclePx": "71234.56",
        "markPx": "71250.00"
      }
    ],
    "sum": "交易总量",
    "total": "活跃用户"
  }
}
```

---

### 3. 热点猎杀者榜单

```http
POST /open/hothunter
```

**请求参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| page | int | 否 | 页码 |
| page_size | int | 否 | 每页数量 |
| type | string | 否 | `day`/`week`/`month`/`allTime` |

**响应数据：**

```json
{
  "code": 200,
  "msg": "success",
  "data": {
    "list": [
      {
        "address": "0x7faf...",
        "rankno": 1,
        "Position": "热门项目",
        "pnl": "-7.72",
        "rio": "收益率",
        "cross_rate": "杠杆使用率",
        "vlm": "交易量",
        "avalue": "账户价值",
        "is_follow": false,
        "is_copy": false
      }
    ]
  }
}
```

---

### 4. 稳健大师榜单

```http
POST /open/master
```

**请求参数：** 同热点猎杀者

**响应数据：**

```json
{
  "list": [
    {
      "address": "0xa1e8...",
      "rankno": 1,
      "drawdown": "最大回撤",
      "pnl": "收益",
      "winrate": "胜率",
      "rio": "收益率",
      "cross_rate": "杠杆使用率",
      "avalue": "账户价值",
      "is_follow": false,
      "is_copy": false
    }
  ]
}
```

---

### 5. 量变先锋榜单

```http
POST /open/vertex
```

**响应数据：**

```json
{
  "list": [
    {
      "address": "0x...",
      "rankno": 1,
      "total": "开单数",
      "spot": "现货数",
      "perpetuals": "合约数",
      "vlm": "交易量",
      "pnl": "收益",
      "rio": "收益率",
      "avalue": "账户价值"
    }
  ]
}
```

---

### 6. 巅峰指数（六芒星）

```http
POST /open/hexagram
```

**响应数据：**

```json
{
  "list": [
    {
      "address": "0x...",
      "rankno": 1,
      "六芒星数据": {
        "收益质量": 85,
        "风险控制": 92,
        "市场相位": 78,
        "杠杆艺术": 88,
        "胜率矩阵": 90,
        "链上足迹": 82
      },
      "is_follow": false,
      "is_copy": false
    }
  ]
}
```

---

### 7. 名人名言

```http
GET /open/quotes
```

**响应数据：**

```json
{
  "code": 200,
  "msg": "success",
  "data": {
    "list": [
      {
        "Name": "人名",
        "image": "图片URL",
        "content": "名言内容"
      }
    ]
  }
}
```

---

## 🔒 需要认证的接口

### 认证流程

1. **获取 Nonce**
```http
POST /base/usernonce
{
  "wallet_address": "0x..."
}
```

2. **签名登录**
```http
POST /base/login
{
  "wallet_address": "0x...",
  "signature": "签名结果",
  "nonce": "上一步返回的nonce"
}
```

3. **使用 Token**
在请求头中添加：
```
Authorization: Bearer <token>
```

---

### 用户信息

```http
GET /account/preview
```

### 更新用户信息

```http
POST /account/edit
{
  "username": "用户名",
  "description": "简介",
  "avatar_id": 111,
  "achievement": [{"number": 1, "id": 1}]
}
```

---

### 跟单相关

#### 创建跟单
```http
POST /trade/create
{
  "copy_addr": "被跟单地址",
  "mode": "smart",  // fixed 或 smart
  "amount": 100,
  "stop_loss": 10
}
```

#### 获取跟单列表
```http
GET /trade/list
```

#### 停止跟单
```http
POST /trade/stop
{
  "id": 1
}
```

#### 跟单交易记录
```http
POST /trade/orders
{
  "id": 1
}
```

---

## 错误码

| 状态码 | 说明 |
|--------|------|
| 200 | 成功 |
| 400 | 请求参数错误 |
| 401 | 未授权/Token 过期 |
| 403 | 权限不足 |
| 404 | 接口不存在 |
| 500 | 服务器内部错误 |

---

## Python 示例代码

```python
import requests

BASE_URL = "https://app.hypertrend.top/api"

# 公开接口 - 无需认证
def get_leaderboard(leaderboard_type="master", period="day"):
    """获取榜单数据"""
    url = f"{BASE_URL}/open/{leaderboard_type}"
    response = requests.post(url, json={
        "page": 1,
        "page_size": 10,
        "type": period
    })
    return response.json()

# 使用示例
data = get_leaderboard("master", "day")
print(data)

# 需要认证的接口
def get_personal_info(token):
    """获取个人信息（需要 JWT）"""
    url = f"{BASE_URL}/apps/personal"
    headers = {"Authorization": f"Bearer {token}"}
    response = requests.get(url, headers=headers)
    return response.json()
```

---

## 版本记录

| 版本 | 日期 | 更新内容 |
|------|------|---------|
| v1.0 | 2026-03-16 | 初始文档，包含所有公开接口 |

---

**文档维护者**: HyperTrend Team  
**最后更新**: 2026-03-16
