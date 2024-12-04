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

### 2.1 代币基础信息
```http
GET /v1/token/metadata?address={token_address}
```
- **返回字段**:
  * name: 代币名称
  * symbol: 代币符号
  * decimals: 小数位数
  * totalSupply: 总供应量
  * owner: 所有者地址

### 2.2 代币价格信息
```http
GET /v1/token/price?address={token_address}
```
- **返回字段**:
  * price: 当前价格
  * priceChange24h: 24小时价格变化
  * volume24h: 24小时交易量
  * marketCap: 市值

### 2.3 代币持有者分析
```http
GET /v1/token/holders?address={token_address}&offset={offset}&limit={limit}
```
- **返回字段**:
  * holderAddress: 持有者地址
  * balance: 持有数量
  * percentage: 持有比例
  * value: 持有价值

### 2.4 代币交易历史
```http
GET /v1/token/transactions?address={token_address}&offset={offset}&limit={limit}
```
- **返回字段**:
  * txHash: 交易哈希
  * timestamp: 交易时间
  * type: 交易类型
  * amount: 交易数量
  * price: 交易价格

### 2.5 代币市场深度
```http
GET /v1/token/orderbook?address={token_address}
```
- **返回字段**:
  * bids: 买单列表
  * asks: 卖单列表
  * spread: 买卖差价
  * depth: 深度数据

## 3. 市场分析端点

### 3.1 热门代币分析
```http
GET /v1/token/trending?timeframe={timeframe}
```
- **参数说明**:
  * timeframe: 1h, 24h, 7d
- **返回字段**:
  * tokens: 代币列表
  * priceChange: 价格变化
  * volumeChange: 交易量变化

### 3.2 新代币发现
```http
GET /v1/token/new?minLiquidity={minLiquidity}
```
- **参数说明**:
  * minLiquidity: 最小流动性要求
- **返回字段**:
  * launchTime: 发布时间
  * initialPrice: 初始价格
  * currentPrice: 当前价格
  * liquidityUSD: 流动性（USD）

### 3.3 大额交易监控
```http
GET /v1/token/large_transactions?address={token_address}&minAmount={minAmount}
```
- **参数说明**:
  * minAmount: 最小交易金额
- **返回字段**:
  * txHash: 交易哈希
  * amount: 交易金额
  * type: 买入/卖出
  * wallet: 钱包地址

## 4. 流动性分析

### 4.1 流动性池信息
```http
GET /v1/pool/info?address={pool_address}
```
- **返回字段**:
  * token0: 代币0信息
  * token1: 代币1信息
  * reserves: 储备量
  * totalLiquidity: 总流动性
  * apr: 年化收益率

### 4.2 流动性变化历史
```http
GET /v1/pool/liquidity_history?address={pool_address}
```
- **返回字段**:
  * timestamp: 时间戳
  * liquidityUSD: 流动性（USD）
  * change: 变化量
  * type: 添加/移除

## 5. 数据聚合分析

### 5.1 智能钱包追踪
```http
GET /v1/wallet/smart_money?timeframe={timeframe}
```
- **返回字段**:
  * walletAddress: 钱包地址
  * profitRate: 收益率
  * tradingVolume: 交易量
  * successRate: 成功率

### 5.2 代币关联分析
```http
GET /v1/token/related?address={token_address}
```
- **返回字段**:
  * relatedTokens: 相关代币列表
  * correlation: 相关性得分
  * commonHolders: 共同持有者数量

## 6. 使用限制与优化

### 6.1 请求限制
- **Basic Plan**
  * 60次/分钟
  * 基础数据访问
  * 标准响应时间

- **Pro Plan**
  * 300次/分钟
  * 完整数据访问
  * 优先响应时间

### 6.2 性能优化建议
1. **缓存策略**
   - 实现本地缓存
   - 设置合理的TTL
   - 定期更新机制

2. **请求优化**
   - 批量数据获取
   - 避免频繁请求
   - 实现请求队列

3. **错误处理**
   - 重试机制
   - 错误日志
   - 监控告警

## 7. 最佳实践

### 7.1 数据监控
1. **价格监控**
   - 设置价格预警
   - 监控异常波动
   - 跟踪价格趋势

2. **交易监控**
   - 大额交易追踪
   - 异常交易检测
   - 钱包行为分析

### 7.2 安全建议
1. **API密钥管理**
   - 定期轮换密钥
   - 权限最小化
   - 监控使用情况

2. **数据验证**
   - 验证响应数据
   - 检查数据一致性
   - 异常数据处理