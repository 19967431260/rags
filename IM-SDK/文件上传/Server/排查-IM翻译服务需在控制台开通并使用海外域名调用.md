---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 文件上传
platform: Server
title: IM翻译服务需在控制台开通并使用海外域名调用
root_cause: 翻译API需要：1.使用海外域名调用；2.operator_account_id必须是在云信注册过的IM账号；3.需先在控制台开通翻译服务
solution: IM翻译服务使用步骤：1.在云信控制台（应用管理>全局功能>IM翻译服务）开通；2.调用海外域名API（https://open.yunxinapi.com/im/v2/translations）；3.operator_account_id填在云信注册的IM账号ID；参考：https://doc.yunxin.163.com/messaging2/server-apis/DYxNjA4NjY?platform=server
customers: ["数字传递"]
source: chat_history
tags: ["翻译API","海外域名","403","operator_account_id","IM翻译"]
created: 2025-08-28
updated: 2026-03-26
---

## 问题：Server IM翻译服务需在控制台开通并使用海外域名调用

## 问题详情

**现象**：
客户使用翻译API时遇到403错误和operator_account_id不存在错误。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供postman调用截图403错误 → 获取错误
2. 客服确认使用了国内域名 → 根因1
3. 指引使用海外域名 https://open.yunxinapi.com/im/v2/translations → 方案1
4. 客户报operator_account_id not exist → 错误2
5. 客服确认operator_account_id需填云信注册的账号ID → 根因2
6. 指引开通IM翻译服务（控制台 > 全局功能）→ 根因3 + 解决方案

**关键发现**：翻译API需要：1.使用海外域名调用；2.operator_account_id必须是在云信注册过的IM账号；3.需先在控制台开通翻译服务

## 问题原因

翻译API需要：1.使用海外域名调用；2.operator_account_id必须是在云信注册过的IM账号；3.需先在控制台开通翻译服务。

## 解决方案

IM翻译服务使用步骤：1.在云信控制台（应用管理>全局功能>IM翻译服务）开通；2.调用海外域名API（https://open.yunxinapi.com/im/v2/translations）；3.operator_account_id填在云信注册的IM账号ID；参考：https://doc.yunxin.163.com/messaging2/server-apis/DYxNjA4NjY?platform=server

## 其他触发场景

（合并时在此处追加）
