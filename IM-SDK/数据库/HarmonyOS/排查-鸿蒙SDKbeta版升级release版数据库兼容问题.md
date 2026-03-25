---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 数据库
platform: HarmonyOS
title: 鸿蒙SDK beta版升级release版数据库兼容问题
root_cause: SDK从beta版升级release版本可能存在数据库兼容问题。
solution: 1. 建议客户卸载重装；2. 或先发一个基于10.7.0的版本作为过渡，测试确认1.4.0 beta升级到10.7.0是正常的。
customers: ["智联招聘"]
source: chat_history
tags: ["鸿蒙", "HarmonyOS", "数据库", "升级", "兼容", "beta"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：鸿蒙SDK beta版升级release版数据库兼容问题

## 问题详情

**现象**：
用户从1.4.0-beta直接升级到10.8.10后，出现消息会话拉不到的问题。错误：queryMessagesByOperationExclude。

**环境信息**：
- 平台：HarmonyOS

## 排查过程

1. 查询服务器记录，只有两条成功记录
2. 分析是客户端本地数据库异常
3. 确认用户是从1.4.0-beta直接升级到10.8.10
4. 开发反馈SDK从beta版升级release版本可能存在数据库兼容问题

## 根因分析

SDK从beta版升级release版本可能存在数据库兼容问题。

## 解决方案

1. 建议客户卸载重装；2. 或先发一个基于10.7.0的版本作为过渡，测试确认1.4.0 beta升级到10.7.0是正常的。

## 其他触发场景

（无）
