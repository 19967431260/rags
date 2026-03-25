---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: APP后台挂1天后重连失败，动态Token鉴权问题
root_cause: 动态Token登录时未正确实现tokenProvider回调，导致鉴权失败
solution: 动态Token登录：1.token字段不用赋值；2.实现tokenProvider，在getToken中返回从业务服务器拿到的动态Token。loginExtensionProvider用于第三方回调登录鉴权。
customers: ["南京芷间科技有限公司"]
source: chat_history
tags: ["动态Token", "tokenProvider", "登录", "重连", "鉴权"]
created: 2025-05-06
updated: 2025-03-20
---

## 问题：iOS APP后台挂1天后重连失败，动态Token鉴权问题

## 问题详情

**现象**：
APP在后台挂了1天多之后再打开，云信SDK没有重连上。使用动态Token登录。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程

1. 确认登录后进程在都是无限重连的
2. 排查发现是动态Token鉴权问题
3. 客户混淆了tokenProvider和loginExtensionProvider的用法
4. 确认需要实现tokenProvider回调返回有效的动态Token

## 问题原因

动态Token登录时未正确实现tokenProvider回调，导致鉴权失败

## 解决方案

动态Token登录：1.token字段不用赋值；2.实现tokenProvider，在getToken中返回从业务服务器拿到的动态Token。loginExtensionProvider用于第三方回调登录鉴权。

## 其他触发场景

