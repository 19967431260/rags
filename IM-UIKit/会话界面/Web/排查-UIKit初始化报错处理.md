---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话界面
platform: Web
title: UIKit初始化报错处理
root_cause: 云端会话未开启，且开通了AI功能导致初始化报错
solution: 1. 在管理后台开启云端会话功能；2. 初始化时配置aiVisible字段关闭AI显示
customers: ['北京破冰动力科技有限公司']
source: chat_history
tags: ['UIKit', '初始化', '云端会话', 'aiVisible']
created: 2025-02-21
updated: 2026-03-23
---

## 问题：Web UIKit初始化报错处理

## 问题详情

**现象**：
运行UIKit Demo时出现多个报错：云端会话未开启、AI配置相关错误。

**环境信息**：
- 平台：Web
- 产品：IM V10 UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 第一个报错 → 云端会话没有开启，需要在管理后台开启
2. 第二个报错 → 开通了AI导致，可以在初始化时配置aiVisible字段关闭
3. 关键发现：多个报错是连锁反应，解决前两个问题后其他报错会消失

## 问题原因

云端会话未开启，且开通了AI功能导致初始化报错

## 解决方案

1. 在管理后台开启云端会话功能；2. 初始化时配置aiVisible字段关闭AI显示

## 其他触发场景

（合并时在此处追加：`- [Web] UIKit初始化报错处理，来源：['北京破冰动力科技有限公司']，2026-03-23`）
