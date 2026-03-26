---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话列表
platform: Server
title: queryMySessionList返回403是V9服务端会话未开通
root_cause: 新应用在控制台只开通了V10云端会话，V9服务端会话（queryMySessionList对应功能）未开通；V9服务端会话和V10云端会话是独立的两个功能
solution: queryMySessionList 403解决方法：在云信控制台开通V9服务端会话功能（该功能需手动在后台开启）；V9和V10的会话功能独立，需分别开通；参考：https://faq.yunxin.163.com/#KB0572
customers: ["WooPlus&网易云信"]
source: chat_history
tags: ["queryMySessionList","403","服务端会话","V9","云端会话"]
created: 2025-08-22
updated: 2026-03-26
---

## 问题：Server queryMySessionList返回403是V9服务端会话未开通

## 问题详情

**现象**：
queryMySessionList接口返回403错误，新换的appkey无法使用该接口。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Server
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供接口返回403截图 → 确认问题
2. 客服检查发现新应用开通了V10云端会话但V9服务端会话未开 → 定位到开通状态问题
3. V9服务端会话和V10云端会话是不同功能 → 确认功能区分
4. 客服帮忙开通V9服务端会话后正常 → 确认解决方案

**关键发现**：新应用在控制台只开通了V10云端会话，V9服务端会话未开通

## 问题原因

新应用在控制台只开通了V10云端会话，V9服务端会话（queryMySessionList对应功能）未开通；V9服务端会话和V10云端会话是独立的两个功能

## 解决方案

queryMySessionList 403解决方法：在云信控制台开通V9服务端会话功能（该功能需手动在后台开启）；V9和V10的会话功能独立，需分别开通；参考：https://faq.yunxin.163.com/#KB0572

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
