---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息
platform: Web
title: Web端用户频繁上下线排查
root_cause: 用户IP不断在ipv4和ipv6之间变化，ipv4可能有某种限制
solution: 建议客户检查VPN设置或网络配置
customers: ["VIP_云信-广州爱拍网络科技有限公司"]
source: chat_history
tags: ["Web","频繁上下线","ipv4","ipv6","VPN"]
created: 2025-08-27
updated: 2026-03-26
---

## 问题：Web Web端用户频繁上下线排查

## 问题详情

**现象**：
客户反馈Web版本用户频繁上下线

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服排查发现用户IP不断在ipv4和ipv6之间变化 → 换到ipv4就会登录后立马掉线
2. 询问客户是否有开VPN → 建议检查VPN设置或网络配置

**关键发现**：用户IP不断在ipv4和ipv6之间变化，ipv4可能有某种限制

## 问题原因

用户IP不断在ipv4和ipv6之间变化，ipv4可能有某种限制

## 解决方案

建议客户检查VPN设置或网络配置

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
