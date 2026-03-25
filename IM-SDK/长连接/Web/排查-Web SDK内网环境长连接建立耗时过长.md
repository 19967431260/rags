---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 长连接
platform: Web
title: Web SDK内网环境长连接建立耗时过长
root_cause: 内网环境tcp连接建立缓慢
solution: 内网部署方式下，建议将内网地址代理成外网相同域名优化，或让网络同事协助排查tcp耗时问题。
customers: ["和仁"]
source: chat_history
tags: ["IM", "Web", "长连接", "内网", "TCP"]
created: 2025-05-14
updated: 2025-03-20
---

## 问题：Web Web SDK内网环境长连接建立耗时过长

## 问题详情

**现象**：
Web SDK 7.5.0版本，建立长连接到触发onconnect耗时3-8秒，内网环境部署。

## 排查过程

**关键发现**：内网环境tcp连接建立缓慢

## 问题原因

内网环境tcp连接建立缓慢

## 解决方案

内网部署方式下，建议将内网地址代理成外网相同域名优化，或让网络同事协助排查tcp耗时问题。
