---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话界面
platform: Uniapp
title: Uniapp多开应用页面导致UIKit报错
root_cause: 多开了一个应用页面导致UIKit组件异常
solution: 关闭重复的应用页面即可恢复正常，不支持同时多开多个应用页面
customers: ["云信-七七星球技术对接群", "云信-上海一诺源核网络科技有限公司", "云信-上海威尔默教育科技有限公司"]
source: chat_history
tags: ["Vue2", "UIKit", "Uniapp", "多开"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Uniapp Uniapp多开应用页面导致UIKit报错

## 问题详情

**现象**：
Web端使用uniapp+Vue2集成UIKit组件时，H5经常出现报错，需要点击屏幕刷新才能恢复。偶现。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Web端uniapp+Vue2
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
H5经常出现报错

## 排查过程

1. 客服排查是否为Vue3版本导致报错 → 客户确认使用的是Vue2版本
2. 客服确认是否为UIKit版本问题 → 客户提供文档链接确认是Vue2版本
3. 客户自查 → 发现是多开了一个应用页面导致的问题

**关键发现**：多开了一个应用页面导致UIKit组件异常

## 问题原因

多开了一个应用页面导致UIKit组件异常

## 解决方案

关闭重复的应用页面即可恢复正常，不支持同时多开多个应用页面

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
