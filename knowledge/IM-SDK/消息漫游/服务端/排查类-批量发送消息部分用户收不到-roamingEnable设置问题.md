---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息漫游
platform: 服务端
title: 批量发送消息部分用户收不到-roamingEnable设置问题
root_cause: 1. 消息设置了不允许漫游(roamingEnable=false)，导致当时不在线用户后续登录收不到
2. 应用后台漫游开关关闭
3. 用户切后台但保持在线状态，消息到达但客户端未正确处理展示
solution: 1. 登录云信后台开启漫游开关
2. 了解离线消息和漫游消息的区别：离线消息影响当前不在线用户，漫游消息影响跨设备收消息
3. 参考文档：https://faq.yunxin.163.com/#KB0014
customers: ['逗趣互动']
source: chat_history
tags: ['sendBatchMsg', 'roamingEnable', '消息漫游', '批量发送', '收不到消息']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：批量发送消息部分用户收不到-roamingEnable设置问题

## 问题详情

**现象**：
使用/msg/sendBatchMsg.action接口批量发送消息，同批次部分用户(5200102)未收到消息，但其他用户(5200103)正常收到。

## 排查过程

1. 检查消息日志发现消息设置了roamingEnable=false
2. 检查应用后台发现漫游开关是关闭状态
3. 分析发现该账号当时实际处于在线状态(切后台)
4. 日志确认消息已到达客户端但未展示

## 问题原因

1. 消息设置了不允许漫游(roamingEnable=false)，导致当时不在线用户后续登录收不到
2. 应用后台漫游开关关闭
3. 用户切后台但保持在线状态，消息到达但客户端未正确处理展示

## 解决方案

1. 登录云信后台开启漫游开关
2. 了解离线消息和漫游消息的区别：离线消息影响当前不在线用户，漫游消息影响跨设备收消息
3. 参考文档：https://faq.yunxin.163.com/#KB0014

## 其他触发场景

（合并时在此处追加）
