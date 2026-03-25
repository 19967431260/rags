---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话列表
platform: Web
title: Web端V10 SDK本地会话列表为空
root_cause: uniapp环境不支持本地数据库(indexedDB)，V10 SDK本地会话功能在uniapp中无法使用
solution: uniapp环境需使用云端会话功能，在初始化配置enableV2CloudConversation开启云端会话
customers: ["河南潮生网络科技有限公司"]
source: chat_history
tags: ["V10", "uniapp", "本地会话", "云端会话", "indexedDB"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web端V10 SDK本地会话列表为空

## 问题详情

**现象**：
客户使用Web端V10 SDK集成，调用getConversationList获取本地会话列表返回空数组。客户使用uniapp开发APP，在浏览器网页端测试。

**环境信息**：
- 平台：Web

## 排查过程

1. 检查SDK版本和初始化配置 → 确认使用V10 SDK
2. 检查浏览器环境 → 火狐浏览器
3. 检查本地会话依赖 → uniapp环境不支持indexedDB本地存储
4. 确认问题根因 → 本地会话依赖浏览器indexedDB，uniapp环境不支持

## 根因分析

uniapp环境不支持本地数据库(indexedDB)，V10 SDK本地会话功能在uniapp中无法使用

## 解决方案

uniapp环境需使用云端会话功能，在初始化配置enableV2CloudConversation开启云端会话

## 其他触发场景

（无）
