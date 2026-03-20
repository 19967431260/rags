---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: RTC房间管理
platform: Flutter
title: Flutter NERoom与RTC SDK混用导致音频失效
root_cause: roomkit的roomuuid等于RTC层的channelname。如果单独加入RTC，同时加入roomkit房间，底层会创建一个和roomuuid一样的channel，加入之后导致上层紊乱，RTC成员就被踢掉了。
solution: 使用NERoom时，不要直接调用RTC SDK的joinChannel接口。应通过NERoom获取RTC实例后加入房间。参考文档：https://doc.yunxin.163.com/neroom/guide/TU5MzI2MzU?platform=flutter
customers: ["海南探寻未来科技有限责任公司"]
source: chat_history
tags: ["414", "joinChannel", "NERoom", "RTC", "Flutter", "音频失效"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：Flutter Flutter NERoom与RTC SDK混用导致音频失效

## 问题详情

**现象**：
客户在使用Flutter NERoom组件时，同时单独接入了RTC SDK。调用joinChannel和enableLocalAudio返回值为0，但双方无法听到声音，且发言者音量监测失效。onJoinChannel回调返回414错误。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查加入房间回调 → 发现onJoinChannel返回414错误
2. 确认channelName传递情况 → 客户未传递channelName
3. 建议传递channelName后测试 → onJoinChannel返回200，加入成功
4. 排查房间创建问题 → 客户反馈创建房间数不足
5. 分析加入流程 → 发现客户同时加入了chatroom和通过RTC SDK接口直接加入RTC channel
**关键发现**：客户同时使用了NERoom和单独RTC SDK加入房间，导致RTC成员被踢掉

**关键发现**：

## 问题原因

roomkit的roomuuid等于RTC层的channelname。如果单独加入RTC，同时加入roomkit房间，底层会创建一个和roomuuid一样的channel，加入之后导致上层紊乱，RTC成员就被踢掉了。

## 解决方案

使用NERoom时，不要直接调用RTC SDK的joinChannel接口。应通过NERoom获取RTC实例后加入房间。参考文档：https://doc.yunxin.163.com/neroom/guide/TU5MzI2MzU?platform=flutter

## 其他触发场景

