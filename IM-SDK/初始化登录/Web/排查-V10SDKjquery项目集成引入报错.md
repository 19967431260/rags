---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化登录
platform: Web
title: V10 SDK jquery项目集成引入报错
root_cause: V10 SDK架构改变，不再支持直接下载JS文件引入，需通过npm安装
solution: V10 SDK需使用npm安装引入，如需纯JS文件可在本地npm安装后构建输出
customers: ["河南潮生网络科技有限公司"]
source: chat_history
tags: ["V10", "jquery", "npm", "SDK引入", "Web"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：V10 SDK jquery项目集成引入报错

## 问题详情

**现象**：
客户使用jquery/html项目集成V10 SDK，通过script标签引入时发生报错，无法正确初始化SDK实例。

**环境信息**：
- 平台：Web

## 排查过程

1. 检查引入方式 → 客户使用V9方式直接下载JS文件引入
2. 确认V10引入方式 → V10需使用npm引入
3. 提供解决方案 → 如需JS文件需先npm安装后本地构建输出

## 根因分析

V10 SDK架构改变，不再支持直接下载JS文件引入，需通过npm安装

## 解决方案

V10 SDK需使用npm安装引入，如需纯JS文件可在本地npm安装后构建输出

## 其他触发场景

（无）
