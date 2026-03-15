---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息管理
platform: Android
title: UIKit删除消息提示无权限
root_cause: UIKit的deleteMessage方法会同时删除本地和云端消息,需要在控制台开启单向删除消息功能权限
solution: 在云信控制台开启单向删除消息功能权限,即可使用UIKit的deleteMessage方法
customers: ["云信-北京校企脉文化科技有限公司"]
source: chat_history
tags: ["UIKit", "deleteMessage", "权限", "单向删除", "控制台配置"]
created: 2026-02-27
updated: 2026-03-16
---

## 问题：Android UIKit删除消息提示无权限

## 问题详情

**现象**：
使用IM-UIKit的ChatViewModel中的deleteMessage方法删除消息时,提示没有权限。客户在UIKit的聊天界面添加了删除消息功能。

## 排查过程

1. 客户调用ChatViewModel的deleteMessage方法 → 提示无权限
2. 确认调用的是UIKit中的删除方法 → 发现UIKit的deleteMessage同时删除本地和云端消息

**关键发现**：UIKit的deleteMessage需要控制台开启单向删除消息功能权限

## 问题原因

UIKit的deleteMessage方法会同时删除本地和云端消息,需要在控制台开启单向删除消息功能权限

## 解决方案

在云信控制台开启单向删除消息功能权限,即可使用UIKit的deleteMessage方法

## 其他触发场景

