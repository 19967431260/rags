---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 服务端
title: 服务端API请求超时问题排查
root_cause: 暂时未收到其他客户类似反馈，服务器状态正常，可能是网络链路问题
solution: 添加判断脚本，出现超时后执行mtr、telnet、dig、ping等命令进行网络诊断
customers: ['FVIP云信-时间在线-gj']
source: chat_history
tags: ['服务端API', '超时', '法兰克福', '网络诊断', 'mtr', 'telnet']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：服务端 服务端API请求超时问题排查

## 问题详情

**现象**：
法兰克福服务器调用api.netease.im接口，每天晚上req api都会timeout，持续时间几分钟到1小时，涉及注册、添加关系等接口。

**环境信息**：
- 平台：服务端
- 产品：IM-SDK

## 排查过程

1. 确认服务器地域：法兰克福
2. 确认超时接口范围
3. 询问是否其他客户有类似反馈
4. 建议添加mtr/telnet/dig/ping等诊断脚本

## 问题原因

暂时未收到其他客户类似反馈，服务器状态正常，可能是网络链路问题

## 解决方案

添加判断脚本，出现超时后执行mtr、telnet、dig、ping等命令进行网络诊断

## 其他触发场景

（合并时在此处追加）
