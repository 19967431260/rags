---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 服务端
title: V9删除消息API返回from accid not exists
root_cause: accid包含大写字母，导致删除API报错
solution: accid不能使用大写字母，建议换纯小写的字符串重新注册账号。
customers: ["南京芷间科技有限公司"]
source: chat_history
tags: ["accid", "大写字母", "删除API", "V9", "报错"]
created: 2025-05-28
updated: 2025-03-20
---

## 问题：服务端 V9删除消息API返回from accid not exists

## 问题详情

**现象**：
调用V9版本的删除API，返回提示from accid not exists，但使用相同accid可以成功发送消息。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：服务端

## 排查过程

1. 排查发现accid包含大写字母
2. 确认accid不能有大写，会引入未知问题

## 问题原因

accid包含大写字母，导致删除API报错

## 解决方案

accid不能使用大写字母，建议换纯小写的字符串重新注册账号。

## 其他触发场景

