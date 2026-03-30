---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Uniapp
title: Uniapp推送监听需去掉click_action的action字段
root_cause: Uniapp推送的click_action配置与原生Android有差异
solution: 使用简化的payload格式：{"hwField":{"click_action":{"type":1,"intent":"intent:#Intent;action=com.netease.nimlib.uniapp.push.NotificationClickActivity;component=包名/com.netease.nimlib.uniapp.push.NotificationClickActivity;launchFlags=0x04000000;i.sessionType=1;S.sessionId=发送者ID;end"},"androidConfig":{"target_user_type":1}}}
customers: ["四川捷登科技有限公司"]
source: chat_history
tags: ["Uniapp", "click_action", "华为推送", "payload配置"]
created: 2026-01-08
updated: 2026-03-15
---

## 问题：Uniapp Uniapp推送监听需去掉click_action的action字段

## 问题详情

**现象**：
Uniapp项目中，服务器推送的消息可以接收，但点击消息进入APP后监听不到。使用了完整的click_action配置包含action字段。

## 排查过程

1. 检查监听代码 → 聊天消息可以监听到，说明代码正常
2. 检查payload配置 → 包含action字段
**关键发现**：Uniapp推送需要特殊的payload格式

## 问题原因

Uniapp推送的click_action配置与原生Android有差异

## 解决方案

使用简化的payload格式：{"hwField":{"click_action":{"type":1,"intent":"intent:#Intent;action=com.netease.nimlib.uniapp.push.NotificationClickActivity;component=包名/com.netease.nimlib.uniapp.push.NotificationClickActivity;launchFlags=0x04000000;i.sessionType=1;S.sessionId=发送者ID;end"},"androidConfig":{"target_user_type":1}}}
