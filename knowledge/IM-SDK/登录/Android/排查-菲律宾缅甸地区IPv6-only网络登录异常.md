---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 登录
platform: Android
title: 菲律宾缅甸地区IPv6 only网络登录异常
root_cause: 菲律宾地区和缅甸IPv6 only网络较多，部分SDK版本不兼容此类特殊网络
solution: 升级SDK版本到10.9.60版本，兼容IPv6 only特殊网络
customers: ["云信+乐次元"]
source: chat_history
tags: ["登录", "IPv6", "菲律宾", "缅甸", "SDK升级"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Android 菲律宾缅甸地区IPv6 only网络登录异常

## 问题详情

**现象**：
菲律宾地区和缅甸IPv6 only网络用户登录出现异常

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程



**关键发现**：

## 问题原因

菲律宾地区和缅甸IPv6 only网络较多，部分SDK版本不兼容此类特殊网络

## 解决方案

升级SDK版本到10.9.60版本，兼容IPv6 only特殊网络

## 其他触发场景

