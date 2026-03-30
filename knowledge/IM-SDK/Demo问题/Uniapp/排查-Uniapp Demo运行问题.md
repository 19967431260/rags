---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Demo问题
platform: Uniapp
title: Uniapp Demo运行问题
root_cause: Demo运行需要正确配置appkey、account和token。
solution: 1. 配置正确的appkey、account和token
2. 账号需要在云信后台注册
3. 后续账号需要走服务器API注册
4. 参考文档：https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server
customers: ['云信-安徽省刀锋网络科技有限公司']
source: chat_history
tags: ['Demo', 'Uniapp', 'token', '账号注册']
created: 2025-02-17
updated: 2026-03-23
---

## 问题：Uniapp Uniapp Demo运行问题

## 问题详情

**现象**：
客户反馈Uniapp Demo运行不正常。

**环境信息**：
- 平台：Uniapp
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供截图
2. 确认参数配置
3. 发现Token未配置

## 问题原因

Demo运行需要正确配置appkey、account和token。

## 解决方案

1. 配置正确的appkey、account和token
2. 账号需要在云信后台注册
3. 后续账号需要走服务器API注册
4. 参考文档：https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server

## 其他触发场景

（合并时在此处追加：`- [Uniapp] Uniapp Demo运行问题，来源：['云信-安徽省刀锋网络科技有限公司']，2026-03-23`）
