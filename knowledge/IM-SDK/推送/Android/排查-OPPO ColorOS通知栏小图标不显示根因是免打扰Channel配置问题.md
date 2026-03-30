---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: OPPO ColorOS通知栏小图标不显示根因是免打扰Channel配置问题
root_cause: 老代码中本地保存的铃声和震动参数被写死为false，导致走免打扰通知Channel（IMPORTANCE_LOW），免打扰通道默认不显示小图标
solution: 检查代码中StatusBarNotificationConfig的铃声/震动参数是否被写死为false；确保notificationSmallIconId配置为非透明PNG图片（放在mipmap-xxhdpi目录）；Android 10+对通知图标有尺寸和透明度要求，需确保图标符合规范
customers: ["深圳市掌娱炫动"]
source: chat_history
tags: ["OPPO","通知图标","ColorOS","免打扰通道","IMPORTANCE_LOW","notificationSmallIconId"]
created: 2025-08-21
updated: 2026-03-26
---

## 问题：Android OPPO ColorOS通知栏小图标不显示根因是免打扰Channel配置问题

## 问题详情

**现象**：
APP在OPPO ColorOS设备上后台运行时收到通知栏消息没有小图标，换了图标图片和notificationSmallIconId配置都无效。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android，OPPO ColorOS设备
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反映换了多种图标仍然无小图标 → 更换图标无效
2. 客服排查发现走了免打扰消息通知通道（IMPORTANCE_LOW）→ 定位到Channel配置问题
3. 客户确认老代码中铃声震动参数被写死为false → 发现问题根因
4. 修改回true后走了消息通知通道，小图标正常显示 → 问题解决

**关键发现**：老代码中铃声震动参数被写死为false，导致走免打扰通知Channel（IMPORTANCE_LOW），免打扰通道默认不显示小图标

## 问题原因

老代码中本地保存的铃声和震动参数被写死为false，导致走免打扰通知Channel（IMPORTANCE_LOW），免打扰通道默认不显示小图标

## 解决方案

1. 检查代码中StatusBarNotificationConfig的铃声/震动参数是否被写死为false
2. 确保notificationSmallIconId配置为非透明PNG图片（放在mipmap-xxhdpi目录）
3. Android 10+对通知图标有尺寸和透明度要求，需确保图标符合规范

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
