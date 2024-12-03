# Birdeye API 使用指南

## 1. API概述

### 1.1 基本信息
- **官方文档**: https://docs.birdeye.so/
- **API基础URL**: https://public-api.birdeye.so
- **认证方式**: 需要在请求头中添加 API key
  ```
  headers: {
    'x-api-key': 'YOUR_API_KEY'
  }
  ```

## 2. Token API端点

### 2.1 获取代币信息
```http
GET /v1/token/metadata?address={token_address}
```

### 2.2 获取代币价格
```http
GET /v1/token/price?address={token_address}
```

### 2.3 获取代币持有者
```http
GET /v1/token/holders?address={token_address}&offset={offset}&limit={limit}
```

### 2.4 获取代币交易历史
```http
GET /v1/token/transactions?address={token_address}&offset={offset}&limit={limit}
```

### 2.5 获取代币市场数据
```http
GET /v1/token/market_data?address={token_address}
```

## 3. 市场数据端点

### 3.1 获取趋势代币
```http
GET /v1/token/trending
```

### 3.2 获取新代币
```http
GET /v1/token/new
```

### 3.3 获取代币排行
```http
GET /v1/token/ranking
```

## 4. DeFi API端点

### 4.1 DEX流动性
```http
GET /defi/pool_info
参数:
- address: 流动性池地址
```

### 4.2 DEX交易
```http
GET /defi/pool_tx_list
参数:
- address: 流动性池地址
- offset: 偏移量
- limit: 返回数量
```

## 5. 使用限制

### 5.1 API计划
- **Basic Plan**
  - 每分钟请求限制
  - 基础数据访问
  - 标准支持

- **Pro Plan**
  - 更高请求限制
  - 完整数据访问
  - 优先支持

### 5.2 请求限制
- 基于API key的请求限制
- 每个IP的请求限制
- 单个端点的调用频率限制

## 6. 最佳实践

### 6.1 错误处理
- 实现请求重试机制
- 处理常见错误码
- 实现错误日志记录

### 6.2 数据缓存
- 实现本地缓存
- 设置合理的缓存时间
- 定期更新机制

## 7. 响应格式

### 7.1 成功响应
```json
{
  "success": true,
  "data": {
    // 具体数据
  }
}
```

### 7.2 错误响应
```json
{
  "success": false,
  "error": {
    "message": "错误信息"
  }
}
```

## 8. 安全建议

### 8.1 API密钥管理
- 安全存储API密钥
- 定期更换API密钥
- 限制API密钥使用范围

### 8.2 请求安全
- 使用HTTPS
- 验证响应数据
- 实现请求超时