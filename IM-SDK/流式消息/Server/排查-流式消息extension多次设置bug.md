---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 流式消息
platform: Server
title: 流式消息extension多次设置bug
root_cause: 服务端bug：流式消息尾次设置extension未能正确更新首次设置的值
solution: 已确认为bug，年后修复（当时处于封网期）。修复后首次设置extension，尾次再设置会把首次的ext字段更新掉。push推送设置：中间默认enabled=false，结束时改为enabled=true。
customers: ["智己汽车"]
source: chat_history
tags: ["流式消息","extension","bug","抄送","服务端"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Server 流式消息extension多次设置bug

## 问题详情

**现象**：
发送流式消息时，extension字段只在第一次抄送消息有，流式结束后的抄送没有extension字段。客户需要在最后一次设置extension来标记流式消息是正常结束还是异常结束。

## 排查过程

1. 确认文档描述 → 文档显示最后一次可以设置ext
2. 测试首次和尾次设置extension → 发现尾次设置未生效
3. 服务器核实消息抄送和最终值 → 确认存在bug

**关键发现**：首次设置extension后，尾次再设置应该更新但未生效

## 问题原因

服务端bug：流式消息尾次设置extension未能正确更新首次设置的值

## 解决方案

已确认为bug，年后修复（当时处于封网期）。修复后首次设置extension，尾次再设置会把首次的ext字段更新掉。push推送设置：中间默认enabled=false，结束时改为enabled=true。

## 其他触发场景

（暂无）
