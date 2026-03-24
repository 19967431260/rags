---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 好友系统
platform: Flutter
title: Flutter监听好友申请及离线通知接收
root_cause: 
solution: 通过onReceiveSystemMsg方法监听系统通知接收好友申请，好友申请的系统通知支持存离线，app下次打开时能收到。通知类型可参考系统通知文档。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['Flutter', '好友申请', '系统通知', 'onReceiveSystemMsg', '离线通知']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Flutter监听好友申请及离线通知接收

## 问题详情

**现象**：
客户咨询前端如何知道有新的好友申请过来，以及如果app没有打开，下次打开是否能收到该事件。

## 排查过程



## 问题原因



## 解决方案

通过onReceiveSystemMsg方法监听系统通知接收好友申请，好友申请的系统通知支持存离线，app下次打开时能收到。通知类型可参考系统通知文档。

## 其他触发场景

（合并时在此处追加）
