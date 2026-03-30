---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Web
title: 聊天室登录linkProvider参数格式
root_cause: link地址类型与客户端类型不匹配，web客户端获取到了小程序专用的link地址
solution: linkProvider是匿名函数，内部调用服务端API获取link后return返回；web客户端需要确认client_type参数，避免获取到小程序专用的link地址
customers: ['甘肃省农资化肥']
source: chat_history
tags: ['聊天室', 'linkProvider', '登录', 'Web', 'client_type']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：聊天室登录linkProvider参数格式

## 问题详情

**现象**：
客户使用Web客户端，询问聊天室登录时linkProvider参数应传什么格式，已通过服务端API获取到link地址。

## 排查过程

1. 客户询问聊天室登录时linkProvider参数格式\n2. 技术支持说明linkProvider是一个匿名函数，应在函数内调用服务端API获取link地址后return返回\n3. 客户按指导实现后出现错误\n4. 检查发现返回数据结构应为data.data.items\n5. 进一步发现link地址是小程序专用，web客户端需要确认client_type参数

## 问题原因

link地址类型与客户端类型不匹配，web客户端获取到了小程序专用的link地址

## 解决方案

linkProvider是匿名函数，内部调用服务端API获取link后return返回；web客户端需要确认client_type参数，避免获取到小程序专用的link地址

## 其他触发场景

（合并时在此处追加）
