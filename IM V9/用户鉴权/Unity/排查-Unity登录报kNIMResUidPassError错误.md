---
track_type: 排查类
sub_type: 客户开发能力
product: IM V9
feature: 用户鉴权
platform: Unity
title: Unity登录报kNIMResUidPassError错误
root_cause: 客户端传入的appkey、accid、token三者不一致，导致鉴权失败
solution: 检查appkey、accid、token三者是否一致。云信服务器日志为了脱敏不打印token，需要客户自行校对入参。Token本身没有期限，除非主动更新否则不会失效。
customers: ["北京久幺幺"]
source: chat_history
tags: ["Unity", "kNIMResUidPassError", "token", "鉴权失败", "登录"]
created: 2026-01-13
updated: 2026-03-15
---

## 问题：Unity Unity登录报kNIMResUidPassError错误

## 问题详情

**现象**：
客户使用Unity接入云信，登录时返回kNIMResUidPassError错误码。AppKey=8f22e4b416b382987a5112f815e7748a，account=177，token=84ubG1whKyJcU9a。客户调用了update.action接口刷新token，但仍然报错。

## 排查过程

1. 确认报错是token问题 2. 检查是否调用了刷新token接口 3. 建议打印入参对比appkey、accid、token三者是否一致

## 问题原因

客户端传入的appkey、accid、token三者不一致，导致鉴权失败

## 解决方案

检查appkey、accid、token三者是否一致。云信服务器日志为了脱敏不打印token，需要客户自行校对入参。Token本身没有期限，除非主动更新否则不会失效。

## 其他触发场景

（合并时在此处追加）
