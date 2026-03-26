---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: 在线消息通知栏点击获取extra参数
root_cause: 在线通知点击的extra参数key值不是固定的，取决于初始化时的通知配置类型。使用错误的key无法获取到参数。
solution: 根据配置选择对应的key：1. 如果是普通在线消息提醒，使用NimIntent.EXTRA_NOTIFY_CONTENT；2. 如果配置为会话类型通知，使用EXTRA_NOTIFY_SESSION_CONTENT。参考文档：https://doc.yunxin.163.com/messaging2/guide/zkxOTU3Mjc?platform=client#单击在线通知的通知栏传递的-extra-类型
customers: ["OCEAN BLUE"]
source: chat_history
tags: ["EXTRA_NOTIFY_CONTENT", "EXTRA_NOTIFY_SESSION_CONTENT", "通知栏", "extra", "Android"]
created: 2025-08-11
updated: 2025-08-11
---

## 问题：Android 在线消息通知栏点击获取extra参数

## 问题详情

**现象**：
客户点击通知栏跳转到指定Activity，需要获取extra参数，但不确认使用哪个key。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户使用NimIntent.EXTRA_NOTIFY_CONTENT获取不到 → 确认获取方式
2. 客服拉取日志确认客户初始化配置 → 检查配置类型
3. 根因：根据通知配置类型不同，key值不同 → 定位根因

**关键发现**：不同通知配置使用不同的extra key

## 问题原因

在线通知点击的extra参数key值不是固定的，取决于初始化时的通知配置类型。使用错误的key无法获取到参数。

## 解决方案

根据配置选择对应的key：
1. 如果是普通在线消息提醒，使用NimIntent.EXTRA_NOTIFY_CONTENT
2. 如果配置为会话类型通知，使用EXTRA_NOTIFY_SESSION_CONTENT
参考文档：https://doc.yunxin.163.com/messaging2/guide/zkxOTU3Mjc?platform=client#单击在线通知的通知栏传递的-extra-类型

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
