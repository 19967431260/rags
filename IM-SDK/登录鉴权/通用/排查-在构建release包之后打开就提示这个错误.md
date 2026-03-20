---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: 通用
title: 在构建release包之后打开就提示这个错误
root_cause: ""
solution: "不可能吧，-keep class com.netease.yunxin.kit.** {*;}这个规则确认生效了吗"
customers: ["云信-太旗富鑫63fd92f3ee62d9a812ef8f3b834f7"]
source: chat_history
tags: ["云信", "SDK", "技术支持"]
created: 2025-01-22
updated: 2026-03-20
---

## 问题：通用 在构建release包之后打开就提示这个错误

## 问题详情

**现象**：
在构建release包之后打开就提示这个错误

## 排查过程

1. 检查会话日志与配置 → 不可能吧，-keep class com.netease.yunxin.kit.** {*;}这个规则确认生效了吗

## 问题原因

会话中未提供更细根因。

## 解决方案

不可能吧，-keep class com.netease.yunxin.kit.** {*;}这个规则确认生效了吗
