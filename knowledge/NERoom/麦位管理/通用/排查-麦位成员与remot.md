---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 麦位管理
platform: 通用
title: 麦位成员与remoteMembers数据不一致
root_cause: 网络恢复时数据同步机制问题
solution: 网络恢复后重新获取麦位信息和remoteMembers，避免数据不一致
customers: ["河南新秀金文化传媒"]
source: chat_history
tags: ["麦位", "remoteMembers", "数据同步", "网络恢复"]
created: 2025-02-19
updated: 2026-03-20
---

## 问题：通用 麦位成员与remoteMembers数据不一致

## 问题详情

**现象**：
用户上麦后，B看A不正常，B的members里没有A。

## 排查过程

1. 网络断开恢复后数据不同步
2. 需要重新拉取remoteMembers
3. 结合isInChatroom和isInRtc判定

## 问题原因

网络恢复时数据同步机制问题

## 解决方案

网络恢复后重新获取麦位信息和remoteMembers，避免数据不一致

## 其他触发场景
- [通用] 麦位成员与remoteMembers数据不一致，来源：['河南新秀金文化传媒']，2026-03-20
- [通用] 麦位成员与remoteMembers数据不一致，来源：['河南新秀金文化传媒']，2026-03-20

