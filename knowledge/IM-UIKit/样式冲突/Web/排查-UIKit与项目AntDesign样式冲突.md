---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 样式冲突
platform: Web
title: UIKit与项目AntDesign样式冲突
root_cause: UIKit使用AntDesign组件，与项目原有AntDesign样式冲突。使用css引入方式时less配置未生效。
solution: 在main.js中全局配置ConfigProvider.config({ prefixCls: '自定义前缀' })，修改AntDesign组件前缀避免冲突。参考文档：https://doc.yunxin.163.com/messaging-uikit/faq/DMyNDMzNTQ?platform=client
customers: ["云南红岭云"]
source: chat_history
tags: ["UIKit", "样式冲突", "AntDesign", "vue3", "prefixCls"]
created: 2025-06-11
updated: 2026-03-23
---

## 问题：Web UIKit与项目AntDesign样式冲突

## 问题详情

**现象**：
vue3项目引入IM UIKit样式后，与原有AntDesign样式冲突，导致按钮圆角、message提示位置等被修改。

**环境信息**：
- 框架：vue3
- UI库：AntDesign

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认冲突现象：a-button圆角、message提示错位
2. 建议提高CSS选择器特异性覆盖
3. 建议修改前缀方案
4. 提供官方FAQ文档参考
5. 确认使用css引入方式导致less配置未生效
6. 提供修改prefixCls的解决方案

**关键发现**：UIKit使用AntDesign组件，与项目原有AntDesign样式冲突。使用css引入方式时less配置未生效。

## 问题原因

UIKit使用AntDesign组件，与项目原有AntDesign样式冲突。使用css引入方式时less配置未生效。

## 解决方案

在main.js中全局配置ConfigProvider.config({ prefixCls: '自定义前缀' })，修改AntDesign组件前缀避免冲突。参考文档：https://doc.yunxin.163.com/messaging-uikit/faq/DMyNDMzNTQ?platform=client

## 其他触发场景

