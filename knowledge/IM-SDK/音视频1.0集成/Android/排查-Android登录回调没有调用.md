---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 音视频1.0集成
platform: Android
updated: 2025-08-21
---

<!-- entry: platform=Android, created=2025-08-21, customers=["圆通"], source=chat_history, frequency=1, tags=["Android", "音视频", "回调", "登录", "类找不到"], troubleshooting="1. 客户反馈回调没有调用 → 2. 客服建议拿复现日志 → 3. 客服确认是否集成音视频1.0 SDK → 4. 客户使用5.8.20版本是2.0 → 5. 客服发现引入了avchat库但没引入rtc库导致类找不到异常 → 6. 客服建议把api 'com.netease.nimlib:avchat:10.9.30'注释掉或引入rtc库", root_cause="项目中引入了音视频1.0的avchat库但没有引入rtc库，导致报类找不到异常，进而影响登录回调", solution="方案1：把api 'com.netease.nimlib:avchat:10.9.30'注释掉；方案2：引入rtc的jar包（如nrtc）" -->
## Q: Android登录回调没有调用

**问题描述**：圆通Android端反馈音视频回调没有调用，也没有相关报错，日志量少只操作了一次

**排查过程**：
1. 客户反馈回调没有调用
2. 客服建议拿复现日志
3. 客服确认是否集成音视频1.0 SDK
4. 客户使用5.8.20版本是2.0
5. 客服发现引入了avchat库但没引入rtc库导致类找不到异常
6. 客服建议把api 'com.netease.nimlib:avchat:10.9.30'注释掉或引入rtc库

**根因**：项目中引入了音视频1.0的avchat库但没有引入rtc库，导致报类找不到异常，进而影响登录回调

**解决方案**：方案1：把api 'com.netease.nimlib:avchat:10.9.30'注释掉；方案2：引入rtc的jar包（如nrtc）