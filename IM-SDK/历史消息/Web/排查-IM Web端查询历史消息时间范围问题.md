---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史消息
platform: Web
title: IM Web端查询历史消息时间范围问题
root_cause: 业务层封装导致时间戳计算错误。列表返回时+1，入参又+1，导致查询范围错乱。另外SDK版本较老（9.2.0）
solution: 1. 升级SDK到最新版本（9.19.10）
2. 检查上层封装逻辑，确保beginTime使用消息的实际time字段
3. 不要对时间戳进行+1操作后再作为查询参数
4. 新建空工程验证纯API接口调用
customers: ['VIP云信-鼎捷软件']
source: chat_history
tags: ['getHistoryMsgs', '历史消息', 'reverse', 'beginTime', 'Web']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Web IM Web端查询历史消息时间范围问题

## 问题详情

**现象**：
使用getHistoryMsgs查询历史消息时，设置reverse=true和beginTime，但查出了小于beginTime的消息

## 排查过程

1. 确认SDK版本 → 9.2.0（较老版本）
2. 检查参数设置 → reverse=true，传了beginTime和endTime
3. 分析时间戳差异 → 发现传入的beginTime与消息实际time字段不一致
4. 确认上层封装问题 → 业务层对返回数据做了封装处理
5. 发现时间戳计算问题 → 业务层在消息时间戳上+1后作为下次查询参数

## 问题原因

业务层封装导致时间戳计算错误。列表返回时+1，入参又+1，导致查询范围错乱。另外SDK版本较老（9.2.0）

## 解决方案

1. 升级SDK到最新版本（9.19.10）
2. 检查上层封装逻辑，确保beginTime使用消息的实际time字段
3. 不要对时间戳进行+1操作后再作为查询参数
4. 新建空工程验证纯API接口调用

## 其他触发场景

（合并时在此处追加）
