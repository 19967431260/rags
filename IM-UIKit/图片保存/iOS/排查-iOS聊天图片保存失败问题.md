---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 图片保存
platform: iOS
title: iOS聊天图片保存失败问题
root_cause: 老版本UIKit开源demo中图片保存回调逻辑问题，系统层面可能有限制
solution: 自行修改开源demo代码逻辑，老版本UIKit已停止维护，建议升级到新版
customers: ['重庆橙心物流网络']
source: chat_history
tags: ['iOS', '图片保存', 'UIKit', 'NIM 9.6', '开源demo', 'image nil']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：iOS iOS聊天图片保存失败问题

## 问题详情

**现象**：
iOS端保存聊天图片失败，提示报错但实际保存成功。使用NIM 9.6老版本UIKit，在iOS 15-18系统上均复现。排查发现image为nil导致回调报错。

**环境信息**：
- 平台：iOS
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认问题必现，获取图片URL → URL浏览器访问正常
2. 确认使用NIM 9.6老版本UIKit开源demo
3. 排查发现image:(UIImage *)image didFinishSavingWithError方法中image为nil
4. 老版本UIKit已停止维护

## 问题原因

老版本UIKit开源demo中图片保存回调逻辑问题，系统层面可能有限制

## 解决方案

自行修改开源demo代码逻辑，老版本UIKit已停止维护，建议升级到新版

## 其他触发场景

（合并时在此处追加：`- [iOS] iOS聊天图片保存失败问题，来源：['重庆橙心物流网络']，2026-03-23`）
