---
track_type: 排查类
sub_type: 环境问题
product: IM
feature: 私有化部署
platform: 通用
title: "私有化环境登录报错192004 protocol timeout"
root_cause: "mix-link服务问题，老版本镜像存在bug，需要重启mix-link和protocolroute服务。"
solution: "在容器内执行：
1. supervisorctl restart protocolroute
2. supervisorctl restart mix-link
注：新版本镜像已修复此问题。"
customers: ["南京信息技术研究院"]
source: chat_history
tags: ["私有化", "192004", "protocol timeout", "mix-link", "服务重启"]
created: 2026-01-29
updated: 2026-03-15
---

## 问题：通用 私有化环境登录报错192004 protocol timeout

## 问题详情

**现象**：
客户在私有化环境配置后登录报错192004 protocol timeout。环境：关闭SSL，telnet 192.168.100.25 10180端口通，但登录失败。

## 排查过程

1. 检查网络连通性 → telnet端口正常
2. 检查asymmetricEncryptionKeyA配置 → 故意改错会报192004
3. 检查服务状态 → supervisorctl status显示都是running
4. 检查mix-link服务 → 重启protocolroute和mix-link后解决

## 问题原因

mix-link服务问题，老版本镜像存在bug，需要重启mix-link和protocolroute服务。

## 解决方案

在容器内执行：
1. supervisorctl restart protocolroute
2. supervisorctl restart mix-link
注：新版本镜像已修复此问题。

## 其他触发场景

（暂无）
