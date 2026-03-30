---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 录屏
platform: Windows
updated: 2025-08-07
---

<!-- entry: platform=Windows, created=2025-08-07, customers=["长沙银行"], source=chat_history, frequency=1, tags=["Windows", "RTC", "录屏", "黑屏", "桌面共享"], troubleshooting="客户反馈录屏黑屏问题 → 客服询问整个桌面是怎么实现录制的 → 客服确认是SDK直接采集Windows桌面 → 客服需要查看113205对应的SDK日志", root_cause="需要查看SDK日志确认具体原因", solution="需要提供113205对应SDK的日志（nrtclog名称的日志文件），查看采集和上行的日志情况" -->
## Q: Windows端录屏出现黑屏

**问题描述**：客户反馈生产环境每周有几笔录屏里面会有一小段黑屏，发生在坐席端Windows端，大概在10点50分17秒左右

**排查过程**：客户反馈录屏黑屏问题 → 客服询问整个桌面是怎么实现录制的 → 客服确认是SDK直接采集Windows桌面 → 客服需要查看113205对应的SDK日志

**根因**：需要查看SDK日志确认具体原因

**解决方案**：需要提供113205对应SDK的日志（nrtclog名称的日志文件），查看采集和上行的日志情况
