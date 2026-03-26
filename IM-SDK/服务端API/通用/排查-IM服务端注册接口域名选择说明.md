---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 通用
title: IM服务端注册接口域名选择说明
root_cause: 客户不确定应该调用哪个服务端注册接口
solution: IM服务端注册接口地址：https://api.yunxinapi.com/nimserver/account/create.action；不同的服务端接口对应不同的API服务器地址，需根据具体接口选择对应域名。
customers: ["厦门硕服特科技有限公司"]
source: chat_history
tags: ["注册接口", "服务端API", "域名", "account"]
created: 2025-08-07
updated: 2026-03-26
---

## 问题：通用 IM服务端注册接口域名选择说明

## 问题详情

**现象**：
客户不确定应该调用哪个服务端注册接口。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：服务端
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：客户不确定应该调用哪个服务端注册接口

## 问题原因

客户不确定应该调用哪个服务端注册接口

## 解决方案

IM服务端注册接口地址：https://api.yunxinapi.com/nimserver/account/create.action；不同的服务端接口对应不同的API服务器地址，需根据具体接口选择对应域名。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
