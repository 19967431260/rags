---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Server
title: 服务端发消息推送payload需传空json且需先配置推送证书
root_cause: 服务端推送系统通知栏有两个前提：1.配置推送证书；2.payload参数传空json（{}）而非不传
solution: 服务端推送消息到系统通知栏：1.先在云信后台配置推送证书（FCM/极光等）；2.调用接口时payload参数必须传空json对象{}；3.push=true表示开启推送，pushcontent为通知栏显示内容
customers: ["WooPlus&网易云信"]
source: chat_history
tags: ["push","payload","推送证书","服务端推送","FCM"]
created: 2025-07-31
updated: 2026-03-26
---

## 问题：Server 服务端发消息推送payload需传空json且需先配置推送证书

## 问题详情

**现象**：
服务端发消息设置了push=true和pushcontent但收不到系统通知栏推送。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Server
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供参数截图 → 确认配置
2. 客服建议payload传空json {} → 尝试
3. 仍无效 → 继续排查
4. 客服检查发现未配推送证书 → 定位到根因
5. 配置证书后问题解决 → 确认解决

**关键发现**：服务端推送系统通知栏有两个前提：配置推送证书 + payload传空json

## 问题原因

服务端推送系统通知栏有两个前提：1.配置推送证书；2.payload参数传空json（{}）而非不传

## 解决方案

服务端推送消息到系统通知栏：
1. 先在云信后台配置推送证书（FCM/极光等）
2. 调用接口时payload参数必须传空json对象{}
3. push=true表示开启推送，pushcontent为通知栏显示内容

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
