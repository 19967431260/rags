---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间信息
platform: iOS
updated: 2025-08-07
---

<!-- entry: platform=iOS, created=2025-08-07, customers=["飞虎互动"], source=chat_history, frequency=1, tags=["iOS", "channelId", "cname", "房间ID"], troubleshooting="1. 排查NECallInfo获取方式\n2. 发现老版本ios组件有问题\n3. 建议用cname做映射", root_cause="老版本iOS组件存在bug，获取的channelId不准确" -->
## Q: iOS端获取房间channelId不准确

**问题描述**：iOS端获取的房间channelId有重复，与实际房间ID不一致

**排查过程**：
1. 排查NECallInfo获取方式
2. 发现老版本ios组件有问题
3. 建议用cname做映射

**根因**：老版本iOS组件存在bug，获取的channelId不准确

**解决方案**：使用channelName（cname）做映射，后端用cname创建录制任务，抄送的录制信息里cname也有