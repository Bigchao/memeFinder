# Birdeye API 使用指南

## 1. API概述

### 1.1 基本信息
- **官方文档**: https://docs.birdeye.so/
- **API基础URL**: https://public-api.birdeye.so
- **API版本**: v1
- **认证方式**: API Key (需要在header中添加 'x-api-key')

### 1.2 主要功能
1. **代币信息**
   - 代币基本数据
   - 价格信息
   - 市值数据
   - 持仓分布

2. **交易数据**
   - 实时交易
   - 历史交易记录
   - 交易量分析
   - 大额交易追踪

3. **市场数据**
   - 流动性信息
   - 买卖盘深度
   - 价格走势
   - 市场情绪

## 2. API端点详解

### 2.1 代币相关
1. **获取代币信息**
```http
GET /public/token_list/solana
GET /public/token/{token_address}
```

2. **代币价格**
```http
GET /public/price?address={token_address}
```

3. **代币持仓**
```http
GET /public/token_holders?address={token_address}
```

### 2.2 交易相关
1. **最新交易**
```http
GET /public/latest_transactions?address={token_address}
```

2. **历史交易**
```http
GET /public/historical_transactions?address={token_address}
```

3. **大额交易**
```http
GET /public/whale_transactions?address={token_address}
```

### 2.3 市场数据
1. **市场深度**
```http
GET /public/market_depth?address={token_address}
```

2. **价格图表数据**
```http
GET /public/price_chart?address={token_address}
```

## 3. 使用限制

### 3.1 API计划
1. **免费版**
   - 速率限制: 30次/分钟
   - 基础数据访问
   - 有限的历史数据

2. **专业版**
   - 速率限制: 100次/分钟
   - 完整数据访问
   - 更多历史数据
   - 优先支持

3. **企业版**
   - 自定义速率限制
   - 完整数据访问
   - 专属支持
   - 定制化服务

### 3.2 使用限制
- 请求频率限制
- 数据范围限制
- IP限制
- 并发连接限制

## 4. 最佳实践

### 4.1 性能优化
1. **缓存策略**
   - 本地缓存实现
   - 缓存时间设置
   - 定期更新机制

2. **批量请求**
   - 合并多个请求
   - 避免频繁调用
   - 使用批量API

### 4.2 错误处理
1. **错误码**
   - 429: 请求过多
   - 401: 未授权
   - 400: 请求错误
   - 500: 服务器错误

2. **重试策略**
   - 指数退避
   - 错误重试
   - 超时处理

## 5. 示例应用场景

### 5.1 代币监控
1. **价格监控**
   - 实时价格追踪
   - 价格预警设置
   - 波动分析

2. **交易监���**
   - 大额交易追踪
   - 异常交易检测
   - 交易模式分析

### 5.2 市场分析
1. **流动性分析**
   - 流动性深度
   - 买卖压力
   - 市场情绪

2. **趋势分析**
   - 价格趋势
   - 交易量趋势
   - 持仓变化

## 6. 安全建议

### 6.1 API密钥管理
- 安全存储密钥
- 定期轮换密钥
- 访问权限控制
- 监控异常使用

### 6.2 请求安全
- 使用HTTPS
- 验证响应数据
- 实现请求签名
- 防止信息泄露

## 7. 故障排除

### 7.1 常见问题
1. **连接问题**
   - 网络超时
   - API限流
   - 认证失败

2. **数据问题**
   - 数据不完整
   - 数据延迟
   - 数据不一致

### 7.2 解决方案
1. **连接优化**
   - 使用CDN
   - 实现重试机制
   - 负载均衡

2. **数据验证**
   - 数据完整性检查
   - 交叉验证
   - 异常检测 