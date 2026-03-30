---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 登录连接
platform: Android
updated: 2025-08-20
---

<!-- entry: platform=Android, created=2025-08-20, customers=["伊对/米连科技"], source=chat_history, frequency=1, tags=["海外", "登录失败", "DNS", "websocket"], troubleshooting="1. 排查用户网络和日志\n2. 发现用户网络会解析到一个连不上的ip地址\n3. 分配的不同域名解析到同一个IP\n4. 调整连接配置为websocket", root_cause="用户网络连不上云信分配的某个地址，DNS解析到了无法连接的IP" -->
## Q: 海外用户IM登录失败

**问题描述**：Android海外用户（菲律宾）打开App或进入直播间，IM登录一直失败

**排查过程**：
1. 排查用户网络和日志
2. 发现用户网络会解析到一个连不上的ip地址
3. 分配的不同域名解析到同一个IP
4. 调整连接配置为websocket

**根因**：用户网络连不上云信分配的某个地址，DNS解析到了无法连接的IP

**解决方案**：调整连接配置为websocket。下发调整后用户可以正常登录。建议升级到9.19.14版本以支持新的连接配置