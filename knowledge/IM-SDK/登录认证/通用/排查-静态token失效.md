---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录认证
platform: 通用
title: 静态token登录提示无效
root_cause: 静态token被服务端接口调用刷新了
solution: 静态token永久有效，除非被刷新。检查服务端是否调用了刷新token接口（https://doc.yunxin.163.com/messaging2/server-apis/DUwODIwMTg?platform=server），重新刷新token即可。
customers: ["绿瘦集团"]
source: chat_history
tags: ["静态token", "登录", "token失效", "刷新"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：通用 静态token登录提示无效

## 问题详情

**现象**：
客户配置了静态token，但SDK登录时仍然返回无效token错误。

## 问题原因

静态token被服务端接口调用刷新了

## 解决方案

静态token永久有效，除非被刷新。检查服务端是否调用了刷新token接口（https://doc.yunxin.163.com/messaging2/server-apis/DUwODIwMTg?platform=server），重新刷新token即可。

## 其他触发场景

