---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Web
title: 登录报错appkey不正确
root_cause: 账号未在云信后台注册。
solution: 1. 在云信后台注册账号
2. 后续账号需要走服务器API注册
3. 使用正确的account和token组合登录。
customers: ['云信-安徽省刀锋网络科技有限公司']
source: chat_history
tags: ['登录', 'appkey', '账号不存在', 'Web']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：Web 登录报错appkey不正确

## 问题详情

**现象**：
加完token后登录报错，提示appkey不正确。

**环境信息**：
- 平台：Web
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户确认appkey正确
2. 提供具体参数
3. 技术支持测试发现返回account not exist
4. 检查账号注册状态

## 问题原因

账号未在云信后台注册。

## 解决方案

1. 在云信后台注册账号
2. 后续账号需要走服务器API注册
3. 使用正确的account和token组合登录。

## 其他触发场景

（合并时在此处追加：`- [Web] 登录报错appkey不正确，来源：['云信-安徽省刀锋网络科技有限公司']，2026-03-23`）
