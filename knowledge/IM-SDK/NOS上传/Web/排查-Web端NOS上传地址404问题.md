---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: NOS上传
platform: Web
title: Web端NOS上传地址404问题
root_cause: 私有化配置被覆盖，导致上传地址错误
solution: 检查并修正nos_uploader_web等私有化配置，确保配置正确加载
customers: ["圆通"]
source: chat_history
tags: ["NOS上传", "404", "私有化配置", "Web"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web Web端NOS上传地址404问题

## 问题详情

**现象**：
NOS上传时构建的上传地址请求返回404。

**环境信息**：
- 平台：Web

## 排查过程

1. 检查上传链接拼接 → 确认拼接方式
2. 检查私有化配置 → 发现配置被覆盖
3. 修正配置 → 问题解决

**关键发现**：私有化配置被覆盖，导致上传地址错误

## 问题原因

私有化配置被覆盖，导致上传地址错误

## 解决方案

检查并修正nos_uploader_web等私有化配置，确保配置正确加载

## 其他触发场景

（无）
