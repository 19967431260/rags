---
track_type: 排查类
sub_type: 推送失败
product: IM-SDK
feature: 离线推送
platform: Android
title: OPPO推送收不到消息
root_cause: OPPO推送SDK版本3.5.3不兼容，证书名称配置不一致
solution: 1. 将OPPO推送SDK版本从3.5.3降级到3.5.1；2. 确保证书名称配置一致，后台上传的证书名和代码中使用的证书名相同（如都使用oppo）。
customers: ["广州东晨网络科技有限公司"]
source: chat_history
tags: ["IM-SDK", "安卓", "离线推送", "OPPO推送", "证书配置"]
created: 2025-05-19
updated: 2025-03-23
---

## 问题：Android OPPO推送收不到消息

## 问题详情

**现象**：
使用OPPO推送时，用OPPO后台下发消息能收到，但用云信下发消息收不到。经排查发现两个问题：1. OPPO推送SDK版本3.5.3不兼容，需要降级到3.5.1；2. 证书名称配置不一致，后台上传的证书名是oppo，但代码中使用的是oppo-im。

**环境信息**：
- 平台：Android

## 排查过程

**关键发现**：OPPO推送SDK版本不兼容，证书名称配置不一致

## 问题原因

OPPO推送SDK版本3.5.3不兼容，证书名称配置不一致

## 解决方案

1. 将OPPO推送SDK版本从3.5.3降级到3.5.1；2. 确保证书名称配置一致，后台上传的证书名和代码中使用的证书名相同（如都使用oppo）。
