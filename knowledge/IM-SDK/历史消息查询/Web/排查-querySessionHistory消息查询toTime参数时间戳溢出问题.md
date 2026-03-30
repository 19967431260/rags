---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 历史消息查询
platform: Web
title: querySessionHistory消息查询toTime参数时间戳溢出问题
root_cause: 客户计算时间戳时发生溢出，导致参数错误
solution: 检查时间戳计算逻辑，避免整数溢出问题
customers: ['ISV云信-和仁']
source: chat_history
tags: ['querySessionHistory', '414', '时间戳溢出', '历史消息']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Web querySessionHistory消息查询toTime参数时间戳溢出问题

## 问题详情

**现象**：
客户调用querySessionHistory接口查询历史消息时，传入30天前的时间戳报414参数错误，传入20天则正常。排查发现是客户计算时间戳时发生溢出。

## 排查过程

1. 客户反馈传30天日期报414错误，传20天正常
2. 技术支持确认接口本身没有时间范围限制，与套餐历史消息可查询范围有关
3. 建议客户检查其他参数
4. 客户自查发现是计算时间戳时溢出问题

## 问题原因

客户计算时间戳时发生溢出，导致参数错误

## 解决方案

检查时间戳计算逻辑，避免整数溢出问题

## 其他触发场景

（合并时在此处追加）
