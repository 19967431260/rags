---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: 华为推送报错query token with exception：初始化不对
root_cause: 华为推送初始化顺序或配置不正确，导致token获取时对象为空
solution: 参考云信FAQ KB0494排查华为推送初始化问题；错误"must not refer to a null object"表明初始化时某配置对象为空，需检查华为推送初始化参数是否正确设置
customers: ["广州市巴图鲁信息科技"]
source: chat_history
tags: ["华为推送", "query token", "初始化", "KB0494"]
created: 2025-07-21
updated: 2025-07-25
---

## 问题：华为推送报错query token with exception：初始化不对

## 问题原因

华为推送初始化顺序或配置不正确，导致token获取时对象为空

## 解决方案

参考云信FAQ KB0494排查华为推送初始化问题；错误"must not refer to a null object"表明初始化时某配置对象为空，需检查华为推送初始化参数是否正确设置
