---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Server
updated: 2025-08-20
---

<!-- entry: platform=Server, created=2025-08-20, customers=["圆通"], source=chat_history, frequency=1, tags=["Server", "数据库", "连接超时", "私有化"], troubleshooting="1. 客户反馈数据库超时 → 2. 客服询问是否有代理的LB → 3. 客户说没有 → 4. 客户说写脚本测试", root_cause="可能是B机房数据库网络不稳定或连接超时配置问题", solution="可以尝试把B机房的数据库连接换成A机房的，或者检查数据库连接超时配置" -->
## Q: B机房数据库连接超时问题

**问题描述**：客户反馈B机房数据库连接超时，数据库域名解析已在hosts里指定不需要走DNS

**排查过程**：
1. 客户反馈数据库超时
2. 客服询问是否有代理的LB
3. 客户说没有
4. 客户说写脚本测试

**根因**：可能是B机房数据库网络不稳定或连接超时配置问题

**解决方案**：可以尝试把B机房的数据库连接换成A机房的，或者检查数据库连接超时配置