---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 账号系统
platform: Server
title: sendAttachMsg返回414 accid not register
root_cause: 账号刚注册后立即发送消息，可能存在数据同步延迟
solution: 账号注册后建议等待片刻再发送消息，如问题持续需提供请求的checksum进一步排查
customers: ["海南悠蓝网络科技有限公司"]
source: chat_history
tags: ["414", "accid not register", "自定义系统通知", "服务端"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：sendAttachMsg返回414 accid not register

## 问题详情

**现象**：
客户调用发送自定义系统通知接口返回错误{code:414,desc:accid not register}，账号为56199964109。

**环境信息**：
- 平台：服务端

## 排查过程

1. 检查账号注册状态 → 查询账号创建时间
2. 检查请求日志 → 服务端返回200，但客户收到414
3. 分析可能原因 → 账号注册与发送请求时间差导致同步延迟

## 根因分析

账号刚注册后立即发送消息，可能存在数据同步延迟

## 解决方案

账号注册后建议等待片刻再发送消息，如问题持续需提供请求的checksum进一步排查

## 其他触发场景

（无）
