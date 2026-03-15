---
track_type: 排查类
sub_type: 系统限制
product: NERtcCallKit
feature: 系统来电
platform: iOS
title: iOS 17.4+ CallKit自定义铃声播放时长过短被打断
root_cause: 系统CallKit弹出LiveComm界面时会打断音频播放，这是iOS系统API行为，SDK无打断逻辑
solution: 这是iOS系统限制，建议：1. 测试高版本系统设备（iOS 18.2+）；2. 确认音频文件在app bundle中且格式正确；3. 如业务自行播放音频也被打断，则无其他解决方案
customers: ["VIP云信-深圳市天启航空科技有限公司"]
source: chat_history
tags: ["CallKit", "自定义铃声", "VoIP", "iOS 17.4", "reportIncomingCall"]
created: 2026-02-10
updated: 2026-03-15
---

## 问题：iOS iOS 17.4+ CallKit自定义铃声播放时长过短被打断

## 问题详情

**现象**：
使用NECallEngine的reportIncomingCallWithParam设置自定义铃声ringtone.caf，VoIP推送成功但铃声只播放1-2秒就被打断，之后只有震动。

## 排查过程



## 问题原因

系统CallKit弹出LiveComm界面时会打断音频播放，这是iOS系统API行为，SDK无打断逻辑

## 解决方案

这是iOS系统限制，建议：1. 测试高版本系统设备（iOS 18.2+）；2. 确认音频文件在app bundle中且格式正确；3. 如业务自行播放音频也被打断，则无其他解决方案
