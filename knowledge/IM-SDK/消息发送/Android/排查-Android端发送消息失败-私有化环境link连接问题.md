---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: Android端发送消息失败-私有化环境link连接问题
root_cause: 私有化环境link服务器地址配置格式错误，导致SDK无法正常连接link服务器。
solution: 正确配置link服务器地址格式：serverAddresses.link = Arrays.asList("域名:端口"); 例如：serverAddresses.link = Arrays.asList("link.example.com:8080"); 注意不要加协议前缀（http://或https://）。
customers: ["顺丰科技"]
source: chat_history
tags: ["Android", "消息发送", "408", "link配置", "私有化"]
created: 2026-01-06
updated: 2026-03-15
---

## 问题：Android Android端发送消息失败-私有化环境link连接问题

## 问题详情

**现象**：
Android端发送消息失败，报错code 408。私有化部署环境，已配置link服务器地址。

## 排查过程

1. 检查错误码 → 408表示客户端网络问题
2. 检查link配置 → 发现配置了link地址但格式可能有问题
3. 查看日志 → 需要进一步分析连接状态
**关键发现**：私有化环境link配置格式不正确。

## 问题原因

私有化环境link服务器地址配置格式错误，导致SDK无法正常连接link服务器。

## 解决方案

正确配置link服务器地址格式：serverAddresses.link = Arrays.asList("域名:端口"); 例如：serverAddresses.link = Arrays.asList("link.example.com:8080"); 注意不要加协议前缀（http://或https://）。

## 其他触发场景

（合并时在此处追加）
