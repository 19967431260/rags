---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 域名解析
platform: iOS
title: RTC iOS getaddrinfo卡死导致崩溃
root_cause: getaddrinfo返回慢导致域名解析耗时长，老版本4.6.x下发的是域名而非IP。
solution: 可通过服务端修改下发配置，将域名改为下发IP。对现有功能没有影响，修改前会提前测试。
customers: ["知聊"]
source: chat_history
tags: ["RTC", "getaddrinfo", "卡死", "域名解析", "iOS"]
created: 2025-02-10
updated: 2025-03-20
---

## 问题：iOS RTC iOS getaddrinfo卡死导致崩溃

## 问题详情

**现象**：
iOS端RTC出现卡死崩溃，分析判断是getaddrinfo返回慢导致域名解析耗时长。

**环境信息**：
- 平台：iOS
- SDK版本：4.6.x

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析崩溃记录和埋点数据
2. 确认用户退出应用时发生
3. 分析日志发现getaddrinfo耗时
4. 确认服务端配置下发方式

**关键发现**：getaddrinfo返回慢导致域名解析耗时长

## 问题原因

getaddrinfo返回慢导致域名解析耗时长，老版本4.6.x下发的是域名而非IP。

## 解决方案

可通过服务端修改下发配置，将域名改为下发IP。对现有功能没有影响，修改前会提前测试。

## 其他触发场景
