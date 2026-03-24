---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 短信验证
platform: 通用
title: Demo中短信验证码无法接收
root_cause: 客户使用自己的appkey运行Demo，但该appkey未开通短信功能，导致无法接收验证码
solution: 修改Demo代码中的appkey为云信测试账号的appkey，或联系后台开通短信功能
customers: ['北京方辰网络科技有限公司']
source: chat_history
tags: ['短信验证码', 'Demo', 'appkey', '权限开通']
created: 2025-02-06
updated: 2026-03-23
---

## 问题：通用 Demo中短信验证码无法接收

## 问题详情

**现象**：
客户运行呼叫组件Demo时，使用自己的appkey无法接收短信验证码，因为该appkey未开通短信功能。

**环境信息**：
- 平台：通用
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查短信发送记录 → 未发现该号码的发送记录
2. 确认appkey配置 → 客户使用了自定义appkey
3. 关键发现：客户appkey未开通短信功能，Demo默认使用云信测试账号的短信功能

## 问题原因

客户使用自己的appkey运行Demo，但该appkey未开通短信功能，导致无法接收验证码

## 解决方案

修改Demo代码中的appkey为云信测试账号的appkey，或联系后台开通短信功能

## 其他触发场景

（合并时在此处追加：`- [通用] Demo中短信验证码无法接收，来源：['北京方辰网络科技有限公司']，2026-03-23`）
