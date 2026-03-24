---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: Android私聊推送标题自定义配置
root_cause: Android端退后台且未被限网时触发SDK在线提醒，离线或杀死进程时触发厂商推送，两种推送的配置方式不同。
solution: 在线提醒自定义内容参考文档：https://doc.yunxin.163.com/messaging/guide/Tg1MDY4MTU?platform=android，需要端侧处理。厂商推送通过服务端pushPayload配置。
customers: ['好未来']
source: chat_history
tags: ['推送标题', 'Android', '在线提醒', '厂商推送', 'pushPayload']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android Android私聊推送标题自定义配置

## 问题详情

**现象**：
客户反馈私聊推送消息标题显示为企业邮箱（昵称），希望自定义推送标题显示效果，且要求前后台展示效果一致。

## 排查过程

1. 确认推送场景：应用退后台触发SDK在线提醒 vs 离线/杀死进程触发厂商推送
2. 检查服务端pushPayload配置
3. 确认Android端在线提醒自定义配置方式

## 问题原因

Android端退后台且未被限网时触发SDK在线提醒，离线或杀死进程时触发厂商推送，两种推送的配置方式不同。

## 解决方案

在线提醒自定义内容参考文档：https://doc.yunxin.163.com/messaging/guide/Tg1MDY4MTU?platform=android，需要端侧处理。厂商推送通过服务端pushPayload配置。

## 其他触发场景

（合并时在此处追加）
