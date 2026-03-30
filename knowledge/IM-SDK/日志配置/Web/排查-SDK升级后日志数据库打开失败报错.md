---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "日志配置"
platform: "Web"
title: "SDK升级后日志数据库打开失败报错"
root_cause: "旧版本初始化参数为db，新版本改为dbLog，参数名变更导致日志数据库打开失败"
solution: "初始化第一参数设置为dbLog: false，关闭日志数据库存储"
customers: ["深圳招银国际"]
source: "chat_history"
tags: ["IM-SDK", "日志", "dbLog", "数据库", "初始化"]
created: "2025-09-05"
updated: "2026-03-20"
---

## 问题：Web SDK升级后日志数据库打开失败报错

## 问题详情

**现象**：
客户升级SDK后成功连接，但一直触发日志数据库打开失败的报错。

## 排查过程

1. 确认与statistic域名无关
2. 发现是日志数据库打开失败
3. 旧版本使用db参数，新版本使用dbLog参数
**关键发现**：新版本初始化参数db改为dbLog

## 问题原因

旧版本初始化参数为db，新版本改为dbLog，参数名变更导致日志数据库打开失败

## 解决方案

初始化第一参数设置为dbLog: false，关闭日志数据库存储

## 其他触发场景
