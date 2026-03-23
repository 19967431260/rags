---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 服务端API
platform: Server
title: 拉人入群extension字段服务端历史消息不返回
root_cause: V10服务端历史消息接口对群通知extension字段支持存在问题
solution: 暂时服务器只能通过消息抄送来获取完整的通知消息内容。V9的attach字段对应V10的extension字段，对应消息对象的V2NIMMessageNotificationAttachment的serverExtension。
customers: ["一泓福瑞文化产业有限公司"]
source: chat_history
tags: ["extension","群通知","服务端API","抄送"]
created: 2025-06-16
updated: 2025-06-16
---

## 问题：Server 拉人入群extension字段服务端历史消息不返回

## 问题详情

**现象**：
客户使用V10接口拉人入群并设置extension字段，但服务端查询历史消息时attachment中没有extension信息。

**环境信息**：
- 平台：Server
- 涉及API：拉人入群接口

## 排查过程

1. 确认V9的attach对应V10的extension → 字段映射关系
2. 确认被邀请方是否同意入群 → 检查入群流程
3. 检查群组是否需要邀请确认 → 确认群组设置
4. 发现服务端接口确实存在问题，建议通过消息抄送获取完整通知内容 → 确定问题根因

**关键发现**：V10服务端历史消息接口对群通知extension字段支持存在问题

## 问题原因

V10服务端历史消息接口对群通知extension字段支持存在问题

## 解决方案

暂时服务器只能通过消息抄送来获取完整的通知消息内容。V9的attach字段对应V10的extension字段，对应消息对象的V2NIMMessageNotificationAttachment的serverExtension。

## 其他触发场景

