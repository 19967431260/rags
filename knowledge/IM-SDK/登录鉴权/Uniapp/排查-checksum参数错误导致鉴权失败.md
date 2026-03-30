---
track_type: 排查类
sub_type: 鉴权问题
product: IM-SDK
feature: Token鉴权
platform: Uniapp
title: checksum参数错误导致鉴权失败
root_cause: 误将appkey作为checksum的第一个参数传入
solution: checksum计算的第一个参数应该是appsecret，而不是appkey。正确的checksum计算方式：使用appsecret作为密钥，对拼接的字符串进行计算。请检查代码中checksum的生成逻辑，确保传入的第一个参数是appsecret。
customers: ["杭州软阁科技有限公司"]
source: chat_history
tags: ["Uniapp", "checksum", "鉴权", "appsecret", "appkey", "Token"]
created: 2025-05-13
updated: 2025-03-23
---

## 问题：Uniapp checksum参数错误导致鉴权失败

## 问题详情

**现象**：
在调用云信接口时，checksum参数传入错误导致鉴权失败。客户误将appkey作为checksum的第一个参数传入。

**环境信息**：
- 平台：Uniapp

## 排查过程

**关键发现**：误将appkey作为checksum的第一个参数传入

## 问题原因

误将appkey作为checksum的第一个参数传入

## 解决方案

checksum计算的第一个参数应该是appsecret，而不是appkey。正确的checksum计算方式：使用appsecret作为密钥，对拼接的字符串进行计算。请检查代码中checksum的生成逻辑，确保传入的第一个参数是appsecret。
