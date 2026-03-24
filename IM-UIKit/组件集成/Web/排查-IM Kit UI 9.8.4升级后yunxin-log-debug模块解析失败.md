---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 组件集成
platform: Web
title: IM Kit UI 9.8.4升级后yunxin-log-debug模块解析失败
root_cause: UIKit 9.8.4版本依赖关系变化，@xkit-yx/utils缺少VisibilityObserver导出，且yunxin-log-debug模块无法解析
solution: 使用npm i --legacy-peer-deps安装依赖，或升级到9.8.7版本；也可主动添加yunxin-log-debug: ^1.1.6依赖
customers: ['VIP云信-云南国云药材国际交易有限公司']
source: chat_history
tags: ['UIKit', 'Web', 'yunxin-log-debug', 'VisibilityObserver', '依赖']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：Web IM Kit UI 9.8.4升级后yunxin-log-debug模块解析失败

## 问题详情

**现象**：
生产环境报错: Failed to resolve module specifier yunxin-log-debug，从9.8.2升级到9.8.4后出现

**环境信息**：
- 平台：Web
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查发现大量peer dependency警告，React版本不匹配
2. 报错显示@xkit-yx/utils缺少VisibilityObserver导出
**关键发现**：9.8.2版本被删除，依赖关系发生变化

## 问题原因

UIKit 9.8.4版本依赖关系变化，@xkit-yx/utils缺少VisibilityObserver导出，且yunxin-log-debug模块无法解析

## 解决方案

使用npm i --legacy-peer-deps安装依赖，或升级到9.8.7版本；也可主动添加yunxin-log-debug: ^1.1.6依赖

## 其他触发场景

（合并时在此处追加：`- [Web] IM Kit UI 9.8.4升级后yunxin-log-debug模块解析失败，来源：['VIP云信-云南国云药材国际交易有限公司']，2026-03-23`）
