---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息回调
platform: Server
title: modifyResponse修改ext字段偶现不生效
root_cause: 第三方回调响应超过2秒超时,云信未收到返回结果
solution: 优化回调接口响应时间,或在控制台调整回调超时时间(最大5秒)
customers: ["天津莱斯宝"]
source: chat_history
tags: ["消息回调", "modifyResponse", "超时", "TimeoutException", "ext"]
created: 2026-02-26
updated: 2026-03-15
---

## 问题：Server modifyResponse修改ext字段偶现不生效

## 问题详情

**现象**：
处理IM聊天消息回调时,通过modifyResponse字段更新ext中的数据,新增notificationTitle和notificationContent字段。大部分情况正常,但偶现客户端收到的消息中没有新增字段。后端日志显示字段已正常赋值。偶现。

**环境信息**：
- 产品：IM-SDK Server端消息回调

**相关日志**：
云信侧日志显示：response.error为java.util.concurrent.TimeoutException

## 排查过程

1. 检查后端回调日志 → 确认modifyResponse字段正常写入
2. 检查云信侧日志 → 发现response.error为java.util.concurrent.TimeoutException
3. 确认回调超时时间 → 默认2秒,最大可调整为5秒

**关键发现**：第三方回调超时,云信未收到服务器返回,导致ext未更改

## 问题原因

第三方回调响应超过2秒超时,云信未收到返回结果

## 解决方案

优化回调接口响应时间,或在控制台调整回调超时时间(最大5秒)

## 其他触发场景
