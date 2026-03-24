---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 私有化部署
platform: Web
title: V10 Web端私有化SSL证书要求
root_cause: V10 Web端长链接使用wss协议，私有化环境需要配置SSL证书才能正常连接。
solution: 私有化环境需要申请域名及对应的SSL证书，配置到服务器上。如临时测试，可使用自签名证书并在浏览器中设置允许不安全内容。
customers: ['云信-宏信动力(北京)科技有限公司']
source: chat_history
tags: ['私有化', 'Web', 'SSL', '证书', 'wss', 'V10']
created: 2025-02-07
updated: 2026-03-23
---

## 问题：Web V10 Web端私有化SSL证书要求

## 问题详情

**现象**：
V10 Web端私有化部署时，长链接使用wss协议，需要SSL证书支持。

**环境信息**：
- 平台：Web
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 配置私有化参数后连接失败，报错ERR_SSL_PROTOCOL_ERROR
2. 检查配置发现使用https和wss连接
3. 确认V10 Web端必须使用SSL证书

## 问题原因

V10 Web端长链接使用wss协议，私有化环境需要配置SSL证书才能正常连接。

## 解决方案

私有化环境需要申请域名及对应的SSL证书，配置到服务器上。如临时测试，可使用自签名证书并在浏览器中设置允许不安全内容。

## 其他触发场景

（合并时在此处追加：`- [Web] V10 Web端私有化SSL证书要求，来源：['云信-宏信动力(北京)科技有限公司']，2026-03-23`）
