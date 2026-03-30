---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 搜索
platform: Flutter
title: IM UIKit搜索好友界面卡死问题
root_cause: nim_searchkit组件存在bug，在特定输入场景下导致界面卡死。
solution: 更新nim_searchkit依赖到9.7.3+1版本修复此问题。https://pub.dev/packages/nim_searchkit
customers: ['达济中道(沈阳)信息科技']
source: chat_history
tags: ['IM-UIKit', 'Flutter', '搜索', '卡死', 'nim_searchkit', '9.7.3']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Flutter IM UIKit搜索好友界面卡死问题

## 问题详情

**现象**：
IM UIKit搜索好友时，搜索accid到最后一位查询输入别的会出现卡死状态，控制台无错误。

## 排查过程

1. 确认复现流程 → 当前登录账号搜索好友，输入accid到最后一位后输入其他字符
2. 确认必现性 → 问题必现
3. 研发排查 → 确认是组件bug
4. 提供修复 → 更新依赖版本

## 问题原因

nim_searchkit组件存在bug，在特定输入场景下导致界面卡死。

## 解决方案

更新nim_searchkit依赖到9.7.3+1版本修复此问题。https://pub.dev/packages/nim_searchkit

## 其他触发场景

（合并时在此处追加）
