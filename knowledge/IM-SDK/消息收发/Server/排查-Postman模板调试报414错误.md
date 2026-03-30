---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息收发
platform: Server
title: Postman模板调试报414错误
root_cause: Postman的Pre-request Script生成checknum逻辑未正确执行，可能是参数被覆盖或脚本未运行
solution: 本地计算好checknum后直接写死填入请求参数进行调试，或检查Postman的Pre-request Script配置
customers: ["优合集团有限公司"]
source: chat_history
tags: ["414", "Postman", "checknum", "调试"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Postman模板调试报414错误

## 问题详情

**现象**：
使用官方文档的Postman模板调试API时返回414错误，请求未自动带上checknum参数

**环境信息**：
- 平台：Server

## 排查过程

1. 检查header信息配置是否正确 → 发现配置无误\n2. 检查appkey和appsecret是否为最新 → 确认是从管理后台刚复制的\n3. 检查globals设置 → 发现已设置但未生效\n4. 建议本地算好checknum写死填入 → 验证通过

## 根因分析

Postman的Pre-request Script生成checknum逻辑未正确执行，可能是参数被覆盖或脚本未运行

## 解决方案

本地计算好checknum后直接写死填入请求参数进行调试，或检查Postman的Pre-request Script配置

## 其他触发场景

（无）
