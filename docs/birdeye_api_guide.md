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

### 1.2 主要功能类别
1. **Token API**
   - 代币基本信息
   - 代币价格数据
   - 代币交易数据
   - 代币持有者信息

2. **DeFi API**
   - DEX交易数据
   - 流动性池信息
   - 收益率数据

3. **NFT API**
   - NFT集合数据
   - NFT交易数据
   - NFT持有者信息

## 2. Token API端点

### 2.1 代币信息
```http
GET /defi/token_info
参数:
- address: 代币地址
```

### 2.2 代币价格
```http
GET /defi/token_price
参数:
- address: 代币地址
```

### 2.3 代币持有者
```http
GET /defi/token_holder_list
参数:
- address: 代币地址
- offset: 偏移量
- limit: 返回数量
```

### 2.4 代币交易
```http
GET /defi/token_tx_list
参数:
- address: 代币地址
- offset: 偏移量
- limit: 返回数量
```

## 3. DeFi API端点

### 3.1 DEX流动性
```http
GET /defi/pool_info
参数:
- address: 流动性池地址
```

### 3.2 DEX交易
```http
GET /defi/pool_tx_list
参数:
- address: 流动性池地址
- offset: 偏移量
- limit: 返回数量
```

## 4. 使用限制

### 4.1 API计划
- **Basic Plan**
  - 每分钟请求限制
  - 基础数据访问
  - 标准支持

- **Pro Plan**
  - 更高请求限制
  - 完整数据访问
  - 优先支持

### 4.2 请求限制
- 基于API key的请求限制
- 每个IP的请求限制
- 单个端点的调用频率限制

## 5. 最佳实践

### 5.1 错误处理
- 实现请求重试机制
- 处理常见错误码
- 实现错误日志记录

### 5.2 数据缓存
- 实现本地缓存
- 设置合理的缓存时间
- 定期更新机制

## 6. 响应格式

### 6.1 成功响应
```json
{
  "success": true,
  "data": {
    // 具体数据
  }
}
```

### 6.2 错误响应
```json
{
  "success": false,
  "error": {
    "message": "错误信息"
  }
}
```

## 7. 安全建议

### 7.1 API密钥管理
- 安全存储API密钥
- 定期更换API密钥
- 限制API密钥使用范围

### 7.2 请求安全
- 使用HTTPS
- 验证响应数据
- 实现请求超时