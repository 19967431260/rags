---
track_type: 排查类
sub_type: 接口调用
product: IM-SDK
feature: 服务端SDK
platform: 服务端
title: 创建聊天室报错accid is empty
root_cause: 请求版本不正确，V10 API需要使用V2版本请求
solution: 检查请求版本，V10 API需要使用V2版本请求。参考创建账号示例：https://github.com/netease-im/yunxin-im-server-sdk/blob/main/docs/quick_start_v2_raw.md
customers: ["北京小米移动软件有限公司"]
source: chat_history
tags: ["聊天室", "服务端SDK", "414", "accid", "V2"]
created: 2025-05-13
updated: 2025-03-23
---

## 问题：服务端 创建聊天室报错accid is empty

## 问题详情

**现象**：
使用服务端SDK创建聊天室报错{"code":414,"desc":"accid is empty"}

**环境信息**：
- 平台：服务端

## 排查过程

**关键发现**：请求版本不正确

## 问题原因

请求版本不正确，V10 API需要使用V2版本请求

## 解决方案

检查请求版本，V10 API需要使用V2版本请求。参考创建账号示例：https://github.com/netease-im/yunxin-im-server-sdk/blob/main/docs/quick_start_v2_raw.md
