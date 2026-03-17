---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 流式消息
platform: Server
title: 流式消息extension字段抄送问题
root_cause: 1. extension字段应与message对象同级，不应放在message对象内部；2. 管理后台未勾选对应的抄送事件类型
solution: 1. 修正参数结构：extension字段与message对象同级；2. 管理后台勾选消息更新抄送事件：单聊勾选89事件，群聊勾选群消息更新事件，配置立即生效
customers: ["智己汽车"]
source: chat_history
tags: ["流式消息","extension","抄送","kafka","服务端","参数配置"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Server 流式消息extension字段抄送问题

## 问题详情

**现象**：
服务端调用流式消息接口时传了extension字段，但kafka收到的消息没有这个字段。同时流式消息只收到第一次的抄送，流输出结束后没有收到消息。

## 排查过程

1. 检查extension字段传参位置 → 发现extension放在了message对象内部
2. 修正参数层级 → extension应与message对象同级
3. 检查抄送配置 → 需要在管理后台勾选消息更新抄送事件(89)和群消息更新抄送
4. 测试单聊和群聊场景 → 单聊勾选89事件，群聊勾选群消息更新事件

**关键发现**：extension字段层级错误，抄送配置未开启

## 问题原因

1. extension字段应与message对象同级，不应放在message对象内部
2. 管理后台未勾选对应的抄送事件类型

## 解决方案

1. 修正参数结构：extension字段与message对象同级
2. 管理后台勾选消息更新抄送事件：单聊勾选89事件，群聊勾选群消息更新事件，配置立即生效

## 其他触发场景

（暂无）
