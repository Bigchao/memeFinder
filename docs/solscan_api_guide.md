# Solscan API 使用指南

## 1. API概述

### 1.1 基本信息
- **官方文档**: https://docs.solscan.io/
- **API基础URL**: https://public-api.solscan.io
- **认证方式**: 需要在请求头中添加 token
  ```
  headers: {
    'token': 'YOUR_API_KEY'
  }
  ```

## 2. 账户相关API

### 2.1 获取账户信息
```http
GET /account/{account}
```
- **参数说明**:
  * account: 账户地址
- **返回字段**:
  * lamports: 账户余额
  * type: 账户类型
  * executable: 是否可执行
  * rentEpoch: 租金时期

### 2.2 获取账户代币列表
```http
GET /account/tokens?account={account}
```
- **参数说明**:
  * account: 账户地址
- **返回字段**:
  * tokenAddress: 代币地址
  * balance: 持有数量
  * decimals: 小数位数
  * tokenAmount: 实际数量

## 3. 交易相关API

### 3.1 获取交易信息
```http
GET /transaction/{signature}
```
- **参数说明**:
  * signature: 交易签名
- **返回字段**:
  * blockTime: 区块时间
  * slot: 区块槽位
  * fee: 交易费用
  * status: 交易状态

### 3.2 获取账户交易历史
```http
GET /account/transactions?account={account}&limit={limit}&before={before}
```
- **参数说明**:
  * account: 账户地址
  * limit: 返回数量限制
  * before: 时间戳

## 4. 代币相关API

### 4.1 获取代币信息
```http
GET /token/meta?token={tokenAddress}
```
- **参数说明**:
  * tokenAddress: 代币合约地址
- **返回字段**:
  * symbol: 代币符号
  * decimals: 小数位数
  * supply: 总供应量
  * name: 代币名称

### 4.2 获取代币持有者
```http
GET /token/holders?token={tokenAddress}&limit={limit}&offset={offset}
```
- **参数说明**:
  * tokenAddress: 代币合约地址
  * limit: 返回数量限制
  * offset: 偏移量

## 5. 使用限制

### 5.1 免费版限制
- 每秒请求数: 2
- 每天请求数: 100,000
- 历史数据访问: 有限

### 5.2 付费版特权
- 更高的请求限制
- 完整的历史数据访问
- 优先技术支持
- WebSocket支持

## 6. 最佳实践

### 6.1 性能优化
1. **缓存策略**
   - 缓存不常变化的数据
   - 设置合理的缓存时间
   - 实现增量更新

2. **请求优化**
   - 批量获取数据
   - 避免重复请求
   - 合理使用分页

### 6.2 错误处理
1. **常见错误码**
   - 429: 请求过多
   - 401: 未授权
   - 400: 请求参数错误

2. **建议处理方式**
   - 实现请求重试
   - 错误日志记录
   - 监控告警机制

## 7. 安全建议

### 7.1 API密钥管理
- 定期更换API密钥
- 避免密钥泄露
- 监控API使用情况

### 7.2 数据验证
- 验证响应数据完整性
- 检查数据一致性
- 处理异常情况

## 8. 应用场景

### 8.1 账户监控
- 余额变动监控
- 代币转账追踪
- 交易历史分析

### 8.2 代币分析
- 代币信息查询
- 持有者分析
- 交易活动监控

### 8.3 交易追踪
- 实时交易监控
- 历史交易分析
- 异常交易检测 