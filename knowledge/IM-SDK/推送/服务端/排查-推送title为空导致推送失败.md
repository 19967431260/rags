---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: 服务端
title: 推送title为空导致推送失败
root_cause: 
solution: 
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 推送title为空导致推送失败

## 问题描述

消息推送有部分因未配置推送title导致失败，IM消息分发入口较多，需要定位title为空的msg对象

## 解答

云信提供title为空的消息内容示例供客户定位问题，如：OppoMessage{"title":"","app_message_id":"xxx","content":"xxx","notify_id":xxx}

## 标签

- 推送
- title
- OPPO
- 推送失败

## 客户

- 北京久幺幺

## 会话日期

2025-02-27
