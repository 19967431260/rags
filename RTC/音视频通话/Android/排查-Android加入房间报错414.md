---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Android
updated: 2025-08-19
---

<!-- entry: platform=Android, created=2025-08-19, customers=["圆通"], source=chat_history, frequency=1, tags=["Android", "RTC", "414", "数据库超时", "长连接"], troubleshooting="1. 客户反馈加入房间报414 → 2. 客服查看日志确认是数据库超时 → 3. 客服确认端口15050 → 4. 客服分析可能是中间代理将长连接掐断", root_cause="数据库连接超时15050，中间代理的长连接时长限制导致RTC长连接维持不住", solution="检查数据库连接配置，确认中间代理的超时时间设置，默认心跳是1分钟，中间代理的长连接时长需要超过1分钟" -->
## Q: Android加入房间报错414 concurrent join

**问题描述**：圆通Android端反馈加入房间时报错414 concurrent join try again，查看日志发现是数据库连接超时导致

**排查过程**：
1. 客户反馈加入房间报414
2. 客服查看日志确认是数据库超时
3. 客服确认端口15050
4. 客服分析可能是中间代理将长连接掐断

**根因**：数据库连接超时15050，中间代理的长连接时长限制导致RTC长连接维持不住

**解决方案**：检查数据库连接配置，确认中间代理的超时时间设置，默认心跳是1分钟，中间代理的长连接时长需要超过1分钟