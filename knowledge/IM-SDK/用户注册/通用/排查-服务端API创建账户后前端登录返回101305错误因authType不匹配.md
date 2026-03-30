---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 用户注册
platform: 通用
title: 服务端API创建账户后前端登录返回101305错误
root_cause: 服务端创建账户时填写的authType与前端登录时使用的authType不匹配
solution: 登录时调整authType参数值（客户原使用0，中间修改过导致不匹配）；刷新并重新获取正确的token即可正常登录
customers: ["广州纪元互动"]
source: chat_history
tags: ["101305","服务端创建账户","authType","登录失败"]
created: 2025-08-29
updated: 2025-08-29
---

## 问题：通用 服务端API创建账户后前端登录返回101305错误

## 问题详情

**现象**：
通过服务端API创建的IM账户，在前端使用id和password登录时返回错误码101305；使用IM后台手动创建的测试账号可以正常登录。appKey: bf58e7c995a44946264f7245e250c2bc

**复现步骤**：
（无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：appKey: bf58e7c995a44946264f7245e250c2bc

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服要求提供appKey排查
2. 后续客户反馈问题已解决

**关键发现**：服务端创建账户时填写的authType与前端登录时使用的authType不匹配。

## 问题原因

服务端创建账户时填写的authType与前端登录时使用的authType不匹配。

## 解决方案

登录时调整authType参数值（客户原使用0，中间修改过导致不匹配）；刷新并重新获取正确的token即可正常登录。

## 其他触发场景

（合并时在此处追加）
