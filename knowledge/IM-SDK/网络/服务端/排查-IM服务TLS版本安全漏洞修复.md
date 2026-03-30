---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 网络
platform: 服务端
title: IM服务TLS版本安全漏洞修复
root_cause: TLS版本过低，存在安全风险
solution: 在nginx配置中强制指定高版本TLS：ssl_protocols TLSv1.2 TLSv1.3; ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256; ssl_prefer_server_ciphers on;
customers: ["科大国创", "辽宁移动"]
source: chat_history
tags: ["IM", "TLS", "SSL", "漏洞", "安全", "nginx"]
created: 2025-05-30
updated: 2025-03-20
---

## 问题：服务端 IM服务TLS版本安全漏洞修复

## 问题详情

**现象**：
IM服务存在中危漏洞，需要配置强制使用高版本TLS协议。

## 排查过程

**关键发现**：TLS版本过低，存在安全风险

## 问题原因

TLS版本过低，存在安全风险

## 解决方案

在nginx配置中强制指定高版本TLS：ssl_protocols TLSv1.2 TLSv1.3; ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256; ssl_prefer_server_ciphers on;
