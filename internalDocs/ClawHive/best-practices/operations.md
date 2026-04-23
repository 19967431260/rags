# 运维操作最佳实践

## 概述

本文档整理了 skill-market 平台的运维操作最佳实践，包括服务管理、数据库维护、日志管理、监控告警等方面。

---

## 1. 服务管理

### 1.1 服务启停

#### 开发环境

```bash
# 启动后端
cd backend
npm run start:dev

# 启动前端
cd frontend
npm run dev

# 启动 Agent Manager Core
cd agent-manager-core
make run-server
```

#### 生产环境

```bash
# 使用 PM2 管理
pm2 start ecosystem.config.js

# 查看服务状态
pm2 status

# 重启服务
pm2 restart skill-market-backend

# 查看日志
pm2 logs skill-market-backend

# 使用 Docker Compose
docker-compose up -d
docker-compose restart backend
docker-compose logs -f backend
```

### 1.2 服务健康检查

```bash
# 后端健康检查
curl http://localhost:3001/api/health

# 期望响应
{
  "status": "ok",
  "timestamp": "2024-01-15T10:30:00Z",
  "services": {
    "database": "ok",
    "redis": "ok"
  }
}

# Agent Manager Core 健康检查
curl http://localhost:8080/health
```

### 1.3 优雅重启

```bash
# PM2 优雅重启（等待现有请求完成）
pm2 reload skill-market-backend

# Docker 优雅停止（设置超时）
docker-compose stop -t 30 backend
```

---

## 2. 数据库维护

### 2.1 迁移执行

```bash
# 查看待执行迁移
cd backend
npm run migration:show

# 执行迁移
npm run migration:run

# 回滚迁移（谨慎操作）
npm run migration:revert

# 生成迁移
npm run migration:generate -- -n MigrationName
```

### 2.2 迁移最佳实践

1. **先在测试环境验证**：任何迁移先在测试环境完整执行一遍
2. **备份数据库**：执行迁移前备份数据库
3. **小步迁移**：大变更拆分为多个小迁移
4. **可回滚设计**：确保每个迁移有对应的回滚逻辑

### 2.3 数据库备份

```bash
# MySQL 备份
mysqldump -h localhost -u root -p skill_market > backup_$(date +%Y%m%d).sql

# 压缩备份
mysqldump -h localhost -u root -p skill_market | gzip > backup_$(date +%Y%m%d).sql.gz

# 恢复备份
mysql -h localhost -u root -p skill_market < backup_20240115.sql
```

### 2.4 常用维护 SQL

```sql
-- 查看数据库大小
SELECT 
  table_schema AS 'Database',
  ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS 'Size (MB)'
FROM information_schema.tables
GROUP BY table_schema;

-- 查看表大小
SELECT 
  table_name AS 'Table',
  ROUND(data_length / 1024 / 1024, 2) AS 'Data (MB)',
  ROUND(index_length / 1024 / 1024, 2) AS 'Index (MB)'
FROM information_schema.tables
WHERE table_schema = 'skill_market'
ORDER BY data_length DESC;

-- 查看慢查询
SELECT * FROM mysql.slow_log 
ORDER BY start_time DESC 
LIMIT 20;

-- 查看当前连接
SHOW PROCESSLIST;

-- 清理过期会话
-- 清理 7 天前的安全事件（由定时任务自动执行）
DELETE FROM security_events 
WHERE created_at < DATE_SUB(NOW(), INTERVAL 180 DAY);
```

---

## 3. 日志管理

### 3.1 日志位置汇总

| 服务 | 位置 | 说明 |
|-----|------|------|
| 后端 | `backend/logs/` 或 `/var/log/skill-market/` | NestJS 应用日志 |
| 前端 | 浏览器控制台 / Vercel 日志 | Next.js 应用日志 |
| Agent Manager | `agent-manager-core/logs/` | Go 服务日志 |
| ClawHive | `~/Library/Logs/ClawHive/` (macOS) | Electron 客户端日志 |
| WEClawHelper | `~/Library/Application Support/WEClawHelper/logs/` | Agent 日志 |

### 3.2 日志级别配置

```bash
# 后端（通过环境变量）
LOG_LEVEL=debug npm run start:dev

# 日志级别：error, warn, info, debug, verbose

# Agent（通过配置文件）
# 编辑 config.json
{
  "log_level": "debug"
}
```

### 3.3 日志轮转

```bash
# 使用 logrotate（Linux）
# /etc/logrotate.d/skill-market
/var/log/skill-market/*.log {
    daily
    rotate 30
    compress
    delaycompress
    missingok
    notifempty
    create 0644 www-data www-data
    postrotate
        pm2 reloadLogs
    endscript
}

# 手动触发轮转
logrotate -f /etc/logrotate.d/skill-market
```

### 3.4 日志分析

```bash
# 错误统计
grep -c "ERROR" app.log

# 按小时统计请求
grep "Request" app.log | awk '{print $1, $2}' | cut -d: -f1-2 | uniq -c

# 响应时间分析
grep "Response time" app.log | awk '{print $NF}' | sort -n | tail -20

# 特定用户追踪
grep "user_id=abc123" app.log

# 特定请求追踪
grep "req_id=xyz789" app.log
```

---

## 4. 配置管理

### 4.1 环境变量

```bash
# 使用 use-env.sh 分发配置
./scripts/use-env.sh dev    # 开发环境
./scripts/use-env.sh staging # 预发环境
./scripts/use-env.sh prod   # 生产环境

# 验证环境变量
cd backend && npm run env:check
```

### 4.2 配置文件清单

| 文件 | 位置 | 说明 |
|-----|------|------|
| `.env` | `backend/.env` | 后端环境变量 |
| `.env.local` | `frontend/.env.local` | 前端环境变量 |
| `ormconfig.ts` | `backend/ormconfig.ts` | TypeORM 配置 |
| `config.json` | 各客户端数据目录 | 客户端配置 |

### 4.3 敏感配置保护

```bash
# 检查敏感信息泄露
grep -rn "password\|secret\|token\|key" --include="*.ts" --include="*.json" .

# 使用环境变量而非硬编码
# 不推荐
const apiKey = 'sk-xxxxx';

# 推荐
const apiKey = process.env.API_KEY;
```

---

## 5. 监控与告警

### 5.1 关键指标

| 指标 | 阈值 | 说明 |
|-----|------|------|
| API 响应时间 | < 500ms | P95 响应时间 |
| 错误率 | < 1% | 5xx 错误占比 |
| CPU 使用率 | < 80% | 服务器 CPU |
| 内存使用率 | < 80% | 服务器内存 |
| 数据库连接数 | < 80% max | 连接池使用率 |
| 磁盘使用率 | < 80% | 服务器磁盘 |

### 5.2 健康检查脚本

```bash
#!/bin/bash
# health-check.sh

# 后端健康检查
BACKEND_STATUS=$(curl -s -o /dev/null -w "%{http_code}" http://localhost:3001/api/health)
if [ "$BACKEND_STATUS" != "200" ]; then
  echo "ALERT: Backend health check failed with status $BACKEND_STATUS"
  # 发送告警通知
fi

# 数据库连接检查
mysql -h localhost -u root -p"$DB_PASSWORD" -e "SELECT 1" > /dev/null 2>&1
if [ $? -ne 0 ]; then
  echo "ALERT: Database connection failed"
fi

# Redis 检查
redis-cli ping > /dev/null 2>&1
if [ $? -ne 0 ]; then
  echo "ALERT: Redis connection failed"
fi
```

### 5.3 告警配置示例

```yaml
# Prometheus AlertManager 规则示例
groups:
  - name: skill-market
    rules:
      - alert: HighErrorRate
        expr: rate(http_requests_total{status=~"5.."}[5m]) / rate(http_requests_total[5m]) > 0.01
        for: 5m
        labels:
          severity: critical
        annotations:
          summary: "High error rate detected"
          
      - alert: SlowResponseTime
        expr: histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m])) > 0.5
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "Slow response time detected"
```

---

## 6. 故障处理流程

### 6.1 故障分级

| 级别 | 定义 | 响应时间 | 示例 |
|-----|------|---------|------|
| P0 | 核心功能完全不可用 | 15 分钟 | 服务宕机、数据丢失 |
| P1 | 核心功能部分不可用 | 30 分钟 | 登录失败、支付异常 |
| P2 | 非核心功能异常 | 2 小时 | 报表延迟、通知失败 |
| P3 | 体验问题 | 24 小时 | UI 问题、性能下降 |

### 6.2 故障处理检查清单

```markdown
## 故障发现
- [ ] 记录故障发现时间
- [ ] 初步判断影响范围
- [ ] 确定故障级别
- [ ] 通知相关人员

## 故障定位
- [ ] 检查服务状态
- [ ] 检查错误日志
- [ ] 检查监控指标
- [ ] 检查最近变更

## 故障恢复
- [ ] 执行恢复措施
- [ ] 验证服务恢复
- [ ] 通知利益相关方

## 故障复盘
- [ ] 编写故障报告
- [ ] 分析根本原因
- [ ] 制定改进措施
- [ ] 跟踪改进落地
```

### 6.3 快速恢复操作

```bash
# 服务重启
pm2 restart skill-market-backend

# 数据库连接重置
# 1. 检查连接数
mysql -e "SHOW STATUS LIKE 'Threads_connected';"
# 2. 杀死空闲连接
mysql -e "SELECT CONCAT('KILL ', id, ';') FROM information_schema.processlist WHERE command = 'Sleep' AND time > 300;"

# 清理磁盘空间
# 1. 查看磁盘使用
df -h
# 2. 清理日志
find /var/log/skill-market -name "*.log" -mtime +30 -delete
# 3. 清理临时文件
rm -rf /tmp/skill-market-*

# 回滚部署
# 使用 Docker
docker-compose down
docker pull skill-market-backend:previous
docker-compose up -d

# 使用 PM2
pm2 deploy production revert 1
```

---

## 7. 定时任务

### 7.1 定时任务清单

| 任务 | 周期 | 说明 |
|-----|------|------|
| 数据库备份 | 每日 02:00 | 全量备份 |
| 日志轮转 | 每日 00:00 | 压缩归档旧日志 |
| 安全事件清理 | 每日 03:00 | 清理 180 天前的数据 |
| 统计数据刷新 | 每小时 | 更新租户统计 |
| 健康检查 | 每 5 分钟 | 服务可用性检查 |

### 7.2 Crontab 示例

```bash
# 数据库备份
0 2 * * * /opt/scripts/backup-db.sh >> /var/log/backup.log 2>&1

# 日志轮转
0 0 * * * /usr/sbin/logrotate -f /etc/logrotate.d/skill-market

# 健康检查
*/5 * * * * /opt/scripts/health-check.sh

# 清理临时文件
0 4 * * * find /tmp -name "skill-market-*" -mtime +1 -delete
```

---

## 8. 安全运维

### 8.1 访问控制

```bash
# SSH 密钥管理
# 只允许密钥登录
vim /etc/ssh/sshd_config
# PasswordAuthentication no
# PubkeyAuthentication yes

# 防火墙配置
ufw allow 22/tcp
ufw allow 80/tcp
ufw allow 443/tcp
ufw enable
```

### 8.2 证书管理

```bash
# Let's Encrypt 证书续期
certbot renew --dry-run  # 测试
certbot renew            # 实际续期

# 检查证书过期时间
openssl x509 -in /etc/ssl/certs/skill-market.crt -noout -dates
```

### 8.3 安全审计

```bash
# 检查登录记录
last -n 20

# 检查失败登录
grep "Failed password" /var/log/auth.log | tail -20

# 检查 sudo 使用记录
grep "sudo" /var/log/auth.log | tail -20
```

---

## 9. 容量规划

### 9.1 资源估算

| 组件 | 最小配置 | 推荐配置 | 说明 |
|-----|---------|---------|------|
| 后端服务 | 2 核 4GB | 4 核 8GB | Node.js 应用 |
| 数据库 | 2 核 4GB | 4 核 16GB | MySQL |
| Redis | 1 核 2GB | 2 核 4GB | 缓存 |
| 存储 | 50GB | 200GB+ | 日志 + 文件存储 |

### 9.2 扩容检查清单

```markdown
## 扩容前
- [ ] 确认当前资源使用率
- [ ] 评估预期增长
- [ ] 准备扩容方案
- [ ] 安排维护窗口

## 扩容中
- [ ] 备份当前配置
- [ ] 执行扩容操作
- [ ] 更新配置文件
- [ ] 重启相关服务

## 扩容后
- [ ] 验证服务正常
- [ ] 检查监控指标
- [ ] 更新文档
```

---

## 相关文档

- [服务架构说明](/docs/guides/dev-architecture.md)
- [数据库迁移指南](/docs/guides/database-migrations.md)
- [后端排障手册](/internalDocs/playbooks/backend/common-issues-triage.md)
- [日志路径汇总](/docs/guides/client-log-paths.md)
