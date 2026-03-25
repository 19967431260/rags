---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 消息渲染
platform: Android
title: UIKit超链接文本颜色修改
root_cause: 老版UIKit超链接颜色通过主色调设置
solution: 在MsgViewHolderText类中修改超链接span颜色设置，老UIKit已开源建议本地引入修改
customers: ["河北家和康孕"]
source: chat_history
tags: ["UIKit", "超链接", "文本颜色", "Android", "MsgViewHolderText"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：UIKit超链接文本颜色修改

## 问题详情

**现象**：
客户使用老版UIKit，需要修改文本中超链接的颜色，目前显示为主色调而非蓝色。

**环境信息**：
- 平台：Android

## 排查过程

1. 确认使用老版开源UIKit
2. 定位MsgViewHolderText类
3. 通过span设置颜色

## 问题原因

老版UIKit超链接颜色通过主色调设置

## 解决方案

在MsgViewHolderText类中修改超链接span颜色设置，老UIKit已开源建议本地引入修改

## 其他触发场景

（无）
