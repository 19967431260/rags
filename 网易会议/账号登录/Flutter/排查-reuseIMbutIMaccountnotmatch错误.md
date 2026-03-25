---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 账号登录
platform: Flutter
title: reuse IM but IM account not match错误
root_cause: 复用IM登录时，会议账号需要与IM账号保持一致，需先创建IM账号再创建会议账号
solution: 先创建IM账号，然后创建会议账号时填入IM账号和token，参考服务端API文档
customers: ["海南温蒂科技有限公司"]
source: chat_history
tags: ["网易会议", "IM复用", "账号不匹配", "Flutter", "RTC"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：reuse IM but IM account not match错误

## 问题详情

**现象**：
客户Android应用使用RTC callkit已有IM登录，集成Flutter会议后去掉会议登录逻辑，出现IM账号不匹配错误。

**环境信息**：
- 平台：Flutter

## 排查过程

1. 分析错误原因 → 会议账号和IM登录账号不一致
2. 确认账号关系 → IM账号和会议账号需要关联
3. 提供解决方案 → 先创建IM账号，会议账号创建时填入IM账号和token

## 根因分析

复用IM登录时，会议账号需要与IM账号保持一致，需先创建IM账号再创建会议账号

## 解决方案

先创建IM账号，然后创建会议账号时填入IM账号和token，参考服务端API文档

## 其他触发场景

（无）
