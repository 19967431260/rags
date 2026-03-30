---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: Flutter
title: Flutter V10创建群邀请好友收不到验证消息
root_cause: V10 UIKit目前未实现群组申请展示功能，需要业务层自行监听onReceiveTeamJoinActionInfo回调并展示UI
solution: 监听NimCore.instance.teamService.onReceiveTeamJoinActionInfo回调，根据回调信息自行实现群组申请UI展示
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["Flutter", "V10", "群组邀请", "验证消息", "UIKit", "onReceiveTeamJoinActionInfo"]
created: 2025-05-06
updated: 2025-03-20
---

## 问题：Flutter Flutter V10创建群邀请好友收不到验证消息

## 问题详情

**现象**：
创建群后邀请好友入群，被邀请人收不到入群验证消息。客户使用Flutter V10 SDK，创建群时传入了inviteeAccountIds参数，但好友收不到同意入群的请求通知。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Flutter

## 排查过程

1. 检查系统通知监听 → 客户确认已调用监听接口
2. 检查建群参数 → 发现memberCount为1，说明成员未被成功拉入
3. 检查beInviteMode设置 → 建议设置为noAuth，但客户希望是验证模式
4. 联调测试 → 发现UIKit暂未实现群组申请展示功能

## 问题原因

V10 UIKit目前未实现群组申请展示功能，需要业务层自行监听onReceiveTeamJoinActionInfo回调并展示UI

## 解决方案

监听NimCore.instance.teamService.onReceiveTeamJoinActionInfo回调，根据回调信息自行实现群组申请UI展示

## 其他触发场景

