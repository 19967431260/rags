---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 私有化部署
platform: Web
title: Electron环境私有化证书信任配置
root_cause: Electron默认不信任自签名证书，需要特殊配置。
solution: 在Electron主进程中添加：app.commandLine.appendSwitch('ignore-certificate-errors'); app.commandLine.appendSwitch('allow-insecure-localhost'); 并在webPreferences中配置nodeIntegration: true。
customers: ['云信-宏信动力(北京)科技有限公司']
source: chat_history
tags: ['Electron', '私有化', '证书', 'Web', 'ignore-certificate-errors']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：Web Electron环境私有化证书信任配置

## 问题详情

**现象**：
Electron环境中私有化部署需要处理证书信任问题。

**环境信息**：
- 平台：Web
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. Electron中访问私有化环境报错证书错误
2. 尝试使用app.commandLine.appendSwitch('ignore-certificate-errors')未生效
3. 需要配置Electron信任本地证书

## 问题原因

Electron默认不信任自签名证书，需要特殊配置。

## 解决方案

在Electron主进程中添加：app.commandLine.appendSwitch('ignore-certificate-errors'); app.commandLine.appendSwitch('allow-insecure-localhost'); 并在webPreferences中配置nodeIntegration: true。

## 其他触发场景

（合并时在此处追加：`- [Web] Electron环境私有化证书信任配置，来源：['云信-宏信动力(北京)科技有限公司']，2026-03-23`）
