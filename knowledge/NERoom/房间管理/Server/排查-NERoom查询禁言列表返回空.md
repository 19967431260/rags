---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间管理
platform: Server
title: NERoom查询禁言列表返回空
root_cause: 查询禁言列表时传入了chat、video、audio多个参数，接口进行精准匹配导致查不到
solution: 查询禁言列表时只传chat=true即可，不需要传video和audio参数
customers: ['河南新秀金文化传媒']
source: chat_history
tags: ['禁言列表', '查询', '参数', 'mute_list', 'NERoom']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Server NERoom查询禁言列表返回空

## 问题详情

**现象**：
调用禁言接口成功后，查询禁言列表返回为空。

## 排查过程

1. 确认禁言参数
2. 检查查询参数
3. 核对参数匹配

## 问题原因

查询禁言列表时传入了chat、video、audio多个参数，接口进行精准匹配导致查不到

## 解决方案

查询禁言列表时只传chat=true即可，不需要传video和audio参数

## 其他触发场景

（合并时在此处追加）
