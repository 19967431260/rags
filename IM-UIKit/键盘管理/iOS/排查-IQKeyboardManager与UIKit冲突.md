---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 键盘管理
platform: iOS
title: IQKeyboardManager与UIKit冲突
root_cause: IQKeyboardManager与云信UIKit的NEKeyboardManager键盘管理机制冲突
solution: 使用云信提供的NEKeyboardManager替代IQKeyboardManager，或源码依赖UIKit后在NEKeyboardManager处添加IQKeyboardManager对应代码
customers: ['VIP云信-沈阳捷影']
source: chat_history
tags: ['UIKit', '键盘', 'IQKeyboardManager', '冲突', 'iOS']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：iOS IQKeyboardManager与UIKit冲突

## 问题详情

**现象**：
客户升级到UIKit 10.5.3后，发现与IQKeyboardManager键盘插件存在冲突，导致输入框异常跳动。

## 排查过程

1. 客户升级到10.5.3后出现键盘跳动问题
2. 排查发现与IQKeyboardManager插件冲突
3. 客服建议改用云信提供的NEKeyboardManager
**关键发现**：IQKeyboardManager与UIKit的键盘管理存在冲突

## 问题原因

IQKeyboardManager与云信UIKit的NEKeyboardManager键盘管理机制冲突

## 解决方案

使用云信提供的NEKeyboardManager替代IQKeyboardManager，或源码依赖UIKit后在NEKeyboardManager处添加IQKeyboardManager对应代码

## 其他触发场景

（合并时在此处追加）
