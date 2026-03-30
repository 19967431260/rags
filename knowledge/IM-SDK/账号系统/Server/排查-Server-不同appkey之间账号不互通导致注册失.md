---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 账号系统
platform: Server
title: 不同appkey之间账号不互通导致注册失败
root_cause: 不同appkey的账号不互通，且新应用配置的服务端域名有误
solution: 1. 新应用需要重新注册账号
2. 检查并修正服务端请求域名配置
3. 建议将注册接口调用迁移到后端，避免客户端暴露密钥
customers: ["一汽奔腾汽车股份有限公司"]
source: chat_history
tags: ["appkey", "账号注册", "account", "域名配置"]
created: 2025-11-07
updated: 2026-03-20
---

## 问题：Server 不同appkey之间账号不互通导致注册失败

## 问题详情

**现象**：
客户创建新测试应用后，使用相同accid登录报错。新应用与老应用使用不同appkey。

**排查过程**：
1. 确认appkey之间account不互通
2. 检查新应用注册接口调用
3. 发现请求未到达云信服务端
4. 排查发现请求域名配置错误（多了'ivi'后缀）

## 问题原因

不同appkey的账号不互通，且新应用配置的服务端域名有误

## 解决方案

1. 新应用需要重新注册账号
2. 检查并修正服务端请求域名配置
3. 建议将注册接口调用迁移到后端，避免客户端暴露密钥
