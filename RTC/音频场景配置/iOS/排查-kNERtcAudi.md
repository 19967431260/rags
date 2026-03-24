---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频场景配置
platform: iOS
title: kNERtcAudioScenarioMusic模式下震动失效问题
root_cause: kNERtcAudioScenarioMusic音频场景模式与系统震动服务冲突
solution: 如不需要播放音乐，建议不设置kNERtcAudioScenarioMusic模式。如需使用music模式（媒体音量控制），可使用临时方案：在music模式下使用特定API触发震动。注意music模式音质更好但外放时回声概率大。
customers: ["邯郸市趣网传媒技术有限公司"]
source: chat_history
tags: ["kNERtcAudioScenarioMusic", "震动", "音频场景", "iOS", "语聊房"]
created: 2025-02-24
updated: 2026-03-20
---

## 问题：iOS kNERtcAudioScenarioMusic模式下震动失效问题

## 问题详情

**现象**：
iOS端进入音视频房间后，调用AudioServicesPlayAlertSound(kSystemSoundID_Vibrate)震动方法失效，退出房间后正常。使用kNERtcAudioScenarioMusic音频场景模式。

## 排查过程

1. 确认问题场景 → 剧本杀游戏场景，需要控制声音大小
2. 确认音频模式影响 → 设置kNERtcAudioScenarioMusic后影响震动
3. 本地验证 → 官方demo测试正常，确认是音频场景配置问题
4. 分析需求 → 客户需要音量键一键修改麦克风声音和收到的声音，且声音可归零
5. 提供解决方案 → music模式下使用特定代码触发震动

## 问题原因

kNERtcAudioScenarioMusic音频场景模式与系统震动服务冲突

## 解决方案

如不需要播放音乐，建议不设置kNERtcAudioScenarioMusic模式。如需使用music模式（媒体音量控制），可使用临时方案：在music模式下使用特定API触发震动。注意music模式音质更好但外放时回声概率大。

## 其他触发场景
- [iOS] kNERtcAudioScenarioMusic模式下震动失效问题，来源：['邯郸市趣网传媒技术有限公司']，2026-03-20
- [iOS] kNERtcAudioScenarioMusic模式下震动失效问题，来源：['邯郸市趣网传媒技术有限公司']，2026-03-20

