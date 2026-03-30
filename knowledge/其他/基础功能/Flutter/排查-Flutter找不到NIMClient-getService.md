---
track_type: 排查类
sub_type: 客户开发能力
product: 其他
feature: 基础功能
platform: Flutter
title: Flutter找不到NIMClient.getService
root_cause: 混淆了底层Android接口和Flutter封装接口
solution: 使用Flutter上层封装接口NimCore.instance.messageService.setChattingAccount
customers:
  - 时间在线
source: chat_history
tags:
  - setChattingAccount
  - NIMClient
created: 2025-06-12
updated: 2025-03-23
---

## 问题：Flutter找不到NIMClient.getService

## 问题详情

**现象**：
客户按照文档调用`NIMClient.getService()`时，报错找不到该方法。

## 问题原因

`NIMClient.getService()`是底层Android端的接口，Flutter有上层封装的接口。

## 解决方案

使用Flutter上层封装接口：
```dart
NimCore.instance.messageService.setChattingAccount(
    sessionId: 'sessionId', 
    sessionType: NIMSessionType.p2p,
);
```

## 其他触发场景
