---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送集成AbstractMethodError错误
root_cause: OPPO推送SDK版本与NIM SDK版本不兼容，客户使用了3.5.2版本但NIM SDK暂不支持
solution: OPPO推送需使用3.5.1版本的heytap push，与NIM SDK版本对应。
customers: ['南通英可达']
source: chat_history
tags: ['OPPO推送', 'AbstractMethodError', 'heytap push', '版本兼容', 'Android']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：OPPO推送集成AbstractMethodError错误

## 问题详情

**现象**：
客户在OPPO手机上集成推送时出现java.lang.AbstractMethodError错误，与heytap push版本不兼容。

## 排查过程

1. 客户反馈配置了推送信息后报错
2. 询问是否使用demo运行
3. 确认是OPPO推送版本问题，需要与NIM SDK版本对应

## 问题原因

OPPO推送SDK版本与NIM SDK版本不兼容，客户使用了3.5.2版本但NIM SDK暂不支持

## 解决方案

OPPO推送需使用3.5.1版本的heytap push，与NIM SDK版本对应。

## 其他触发场景

（合并时在此处追加）
