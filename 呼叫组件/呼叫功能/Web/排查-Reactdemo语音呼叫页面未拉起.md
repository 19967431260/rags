---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 呼叫功能
platform: Web
title: React demo语音呼叫页面未拉起
root_cause: 403错误是本地反垃圾功能未开通，与呼叫页面未拉起无关，需进一步排查业务逻辑
solution: 403错误可忽略，如需排查呼叫问题需开启debug日志分析，确认呼叫逻辑执行
customers: ["海南温蒂科技有限公司"]
source: chat_history
tags: ["呼叫组件", "React", "403", "语音呼叫", "Web"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：React demo语音呼叫页面未拉起

## 问题详情

**现象**：
客户使用Web React demo，登录成功后自动发起语音呼叫，但呼叫页面未拉起，控制台有403错误。

**环境信息**：
- 平台：Web

## 排查过程

1. 分析403错误 → 本地反垃圾功能未开通，可忽略
2. 检查部署环境 → 确认是localhost
3. 开启debug日志 → 设置debugLevel为debug
4. 分析日志 → 客户自行发现问题原因

## 问题原因

403错误是本地反垃圾功能未开通，与呼叫页面未拉起无关，需进一步排查业务逻辑

## 解决方案

403错误可忽略，如需排查呼叫问题需开启debug日志分析，确认呼叫逻辑执行

## 其他触发场景

（无）
