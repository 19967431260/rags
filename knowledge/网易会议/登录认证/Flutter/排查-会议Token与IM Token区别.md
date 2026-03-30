---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 登录认证
platform: Flutter
title: 会议Token与IM Token区别
root_cause: IM Token和会议Token不同，不能共用
solution: 会议账号和IM账号可以一样，但token不一样。创建会议账号时会返回会议专用token，需使用会议token进行会议登录
customers: ['深圳市森愈网络科技有限公司']
source: chat_history
tags: ['会议登录', 'Token', '401', 'Flutter', '认证失败']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Flutter 会议Token与IM Token区别

## 问题详情

**现象**：
客户误以为IM Token和会议Token可以共用，导致会议登录401错误

## 排查过程

1. 客户反馈加入会议返回401错误，token cannot be empty → 询问会议登录是否成功
2. 客户确认IM登录成功 → 说明会议账号和IM账号token不同
3. 客户找到会议token后问题解决

## 问题原因

IM Token和会议Token不同，不能共用

## 解决方案

会议账号和IM账号可以一样，但token不一样。创建会议账号时会返回会议专用token，需使用会议token进行会议登录

## 其他触发场景

（合并时在此处追加）
