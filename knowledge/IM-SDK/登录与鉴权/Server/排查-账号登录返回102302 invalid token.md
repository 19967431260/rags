---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录与鉴权
platform: Server
title: 账号登录返回102302 invalid token
root_cause: 测试环境和正式环境使用了同一个账号ID，导致token环境不一致；102302为鉴权失败错误码
solution: 确认测试/正式环境账号ID隔离；若token不匹配则重新调用refreshToken接口刷新token
customers: ["一智科技（成都）有限公司"]
source: chat_history
tags: ["102302","invalid token","token刷新","账号鉴权"]
created: 2025-07-31
updated: 2026-03-26
---

## 问题：Server 账号登录返回102302 invalid token

## 问题详情

**现象**：
客户账号 gensen_official_activity 登录时报102302 invalid token错误，token从服务端刷新token接口获取，认为token应永久有效。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：测试环境和正式环境共用同一账号ID

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认102302为账号密码错误 → 初步判断为鉴权问题
2. 客户提供accid和token → 获取客户信息
3. 客服检查无刷新token记录 → token未经过主动刷新
4. 客户确认token从创建用户时存储，未主动刷新 → token来源确认
5. 客服确认token默认永久有效 → token本身应有效
6. 客户发现测试环境和正式环境共用同一账号ID → 根因定位

**关键发现**：测试环境和正式环境使用了同一个账号ID，导致token环境不一致；102302为鉴权失败错误码

## 问题原因

测试环境和正式环境使用了同一个账号ID，导致token环境不一致；102302为鉴权失败错误码。

## 解决方案

确认测试/正式环境账号ID隔离；若token不匹配则重新调用refreshToken接口刷新token。

## 其他触发场景

（合并时在此处追加）
