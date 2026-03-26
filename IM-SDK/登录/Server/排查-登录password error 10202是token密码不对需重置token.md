---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Server
title: 登录password error 10202是token密码不对需重置token
root_cause: 客户端使用的token与云信服务端存储的token不匹配，导致鉴权失败返回10202 password error
solution: password error 10202解决方法：调用服务端API重置用户token（https://doc.yunxin.163.com/messaging/server-apis/DUxNDQ3NjA?platform=server）；token有效期过期或被修改后需要重新获取
customers: ["西安麦游网络科技有限公司"]
source: chat_history
tags: ["10202","password error","token重置","登录失败"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：Server 登录password error 10202是token密码不对需重置token

## 问题详情

**现象**：
客户端登录云信时报password error，客户询问原因。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Server
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供accid和token → 收集信息
2. 客服确认password error（10202）是密码/token不对 → 定位到鉴权问题
3. 指引调用服务端接口重置token → 确认解决方案

**关键发现**：客户端使用的token与云信服务端存储的token不匹配，导致鉴权失败返回10202

## 问题原因

客户端使用的token与云信服务端存储的token不匹配，导致鉴权失败返回10202 password error

## 解决方案

password error 10202解决方法：调用服务端API重置用户token（https://doc.yunxin.163.com/messaging/server-apis/DUxNDQ3NjA?platform=server）；token有效期过期或被修改后需要重新获取

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
