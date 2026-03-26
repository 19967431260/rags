---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送配置
platform: iOS
title: iOS推送token未上报导致收不到推送的排查方法
root_cause: iOS推送收不到的根因：登录时未调用updateApnsToken方法上报推送token，即使证书已配置但服务端未收到token因此无法推送
solution: iOS推送排查步骤：1.确认option.apnsCername配置了证书名称；2.确认AppDelegate或相应位置正确调用了[[NIMSDK sharedSDK] updateApnsToken:deviceToken]上报token；3.确认打包环境（TestFlight/AdHoc）与证书类型匹配
customers: ["数字传递"]
source: chat_history
tags: ["iOS推送","apnsToken","updateApnsToken","推送证书","TestFlight"]
created: 2025-08-20
updated: 2026-03-26
---

## 问题：iOS iOS推送token未上报导致收不到推送的排查方法

## 问题详情

**现象**：
客户App提交AppStore后收不到推送，但之前测试正常，怀疑是TestFlight打包问题或证书配置问题。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：TestFlight打包

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供包名com.aoyou.xinbo和证书名xlxb_push → 获取环境信息
2. 客服查服务端日志确认推送token未上报 → 根因定位
3. 确认是登录时未调用 updateApnsToken 上报token → 根因确认
4. 客服确认证书配置了但登录协议中无token和证书名称 → 确认
5. 检查代码是否正确调用[[NIMSDK sharedSDK] updateApnsToken:deviceToken] → 解决方案

**关键发现**：iOS推送收不到的根因：登录时未调用updateApnsToken方法上报推送token，即使证书已配置但服务端未收到token因此无法推送

## 问题原因

iOS推送收不到的根因：登录时未调用updateApnsToken方法上报推送token，即使证书已配置但服务端未收到token因此无法推送。

## 解决方案

iOS推送排查步骤：1.确认option.apnsCername配置了证书名称；2.确认AppDelegate或相应位置正确调用了[[NIMSDK sharedSDK] updateApnsToken:deviceToken]上报token；3.确认打包环境（TestFlight/AdHoc）与证书类型匹配。

## 其他触发场景

（合并时在此处追加）
