---
track_type: 排查类
sub_type: 客户开发能力
product: 其他
feature: 基础功能
platform: Flutter
title: Flutter消息未读数不清理问题
root_cause: 未正确调用setChattingAccount接口设置当前会话
solution: 进入会话时调用setChattingAccount设置当前会话，退出时恢复
customers:
  - 时间在线
source: chat_history
tags:
  - MsgService
  - 未读
  - 消息
  - setChattingAccount
  - NIMClient
  - 会话
created: 2025-06-12
updated: 2025-03-23
---

## 问题：Flutter消息未读数不清理问题

## 问题详情

**现象**：
当用户点击列表进入聊天页面，然后杀掉APP，重新启动app，发现未读数还是一样的，没有清理。

**复现步骤**：
1. 进入聊天页面
2. 杀掉APP
3. 重新启动APP
4. 未读数未清理

## 排查过程

1. 确认现象 → 未读数确实没有清理
2. 检查日志 → 发现17:27确实没有调用清理未读数接口
3. 确认使用方式 → 客户只用了SDK没有用UI组件

**关键发现**：未正确调用setChattingAccount接口

## 问题原因

进入会话时没有调用setChattingAccount设置当前会话，导致未读数清理机制没有触发。

## 解决方案

1. 进入会话时调用接口设置当前会话：
```dart
NimCore.instance.messageService.setChattingAccount(
    sessionId: 'sessionId', 
    sessionType: NIMSessionType.p2p,
);
```

2. 退出聊天界面或离开最近联系人列表界面，需要恢复更新未读数：
```dart
NIMClient.getService(MsgService.class).setChattingAccount(
    MsgService.MSG_CHATTING_ACCOUNT_NONE, 
    SessionTypeEnum.None
)
```

该接口内部会调用清理未读，而且会马上清空未读数，新来的这个会话的消息也不会增加未读数。

## 其他触发场景
