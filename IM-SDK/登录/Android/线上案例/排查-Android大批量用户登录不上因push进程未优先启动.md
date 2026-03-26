---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 登录
platform: Android
title: Android大批量用户登录不上（push进程未优先启动）
root_cause: Xiaomi手机系统策略导致push进程未第一时间启动，login方法未执行；部分账号因频繁刷新token或accid/token不匹配导致302
solution: SDK层面无法干预；客户端需要：1）在手机系统设置中将APP加白名单；2）开启自启动权限；3）电池策略设置为无限制（不同系统版本效果不同）；日志路径参考：https://faq.yunxin.163.com/#KB0179
customers: ["广州触海网络科技"]
source: chat_history
tags: ["302","登录失败","push进程","Xiaomi","加白名单"]
created: 2025-08-18
updated: 2025-08-18
---

## 问题：Android Android大批量用户登录不上（push进程未优先启动）

## 问题详情

**现象**：
Android端大批量用户登录不上，返回302（账号密码错误）。appKey: 7371d729710cd6ce3a50163b956b5eb6，日志显示部分账号302之前刷新过2次token，时间间隔很近。另有账号登录后服务器未收到login请求，客户端无响应。

**复现步骤**：
（无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Xiaomi手机
- 其他：appKey: 7371d729710cd6ce3a50163b956b5eb6

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服查询日志发现部分账号有重复登录-退出-再登录操作，302前刷新过2次token
2. 另有账号服务器端未收到登录请求 → 要求客户提供SDK日志
3. 分析日志发现push进程没有第一时间起来，导致login没有执行
**关键发现**：Xiaomi手机系统策略：app频繁开关或低电量时，push进程不会优先启动

## 问题原因

Xiaomi手机系统策略导致push进程未第一时间启动，login方法未执行；部分账号因频繁刷新token或accid/token不匹配导致302。

## 解决方案

SDK层面无法干预；客户端需要：
1）在手机系统设置中将APP加白名单
2）开启自启动权限
3）电池策略设置为无限制（不同系统版本效果不同）
日志路径参考：https://faq.yunxin.163.com/#KB0179

## 其他触发场景

（合并时在此处追加）
