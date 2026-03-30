---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "消息删除"
platform: "iOS"
title: "deleteMessageFromServer返回403权限错误"
root_cause: "deleteMessageFromServer是单向删除消息的接口，需要先在管理后台开启对应的功能权限才能使用。"
solution: "单向删除消息功能需要在管理后台先开启对应的权限开关。如果只是删除本地消息，可以直接使用deleteMessage接口，该接口不需要额外权限。"
customers: ["FVIP-深圳秀蛋"]
source: "chat_history"
tags: ["deleteMessageFromServer", "403", "权限", "单向删除", "iOS"]
created: "2025-09-26"
updated: "2026-03-20"
---

## 问题：iOS deleteMessageFromServer返回403权限错误

## 问题详情

**现象**：
客户调用deleteMessageFromServer接口删除消息时返回403错误，提示"非法操作或没有权限"。

## 问题原因

deleteMessageFromServer是单向删除消息的接口，需要先在管理后台开启对应的功能权限才能使用。

## 解决方案

单向删除消息功能需要在管理后台先开启对应的权限开关。如果只是删除本地消息，可以直接使用deleteMessage接口，该接口不需要额外权限。

## 其他触发场景
