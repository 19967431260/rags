---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: iOS编译
platform: iOS
title: IM UIKit iOS 18兼容性问题及SnapKit版本冲突
root_cause: iOS 18系统兼容性问题以及SnapKit版本不匹配导致编译失败。
solution: 1. 对于iOS 18崩溃问题，升级呼叫组件到2.5.2版本
2. 对于SnapKit冲突，尝试指定pod 'SnapKit', '~> 4.2.0'版本
3. 移除RTC底层的libarclite相关文件
customers: ['临沂卓创网络科技有限公司']
source: chat_history
tags: ['iOS', 'UIKit', 'iOS 18', 'SnapKit', '编译错误', 'libarclite']
created: 2025-01-11
updated: 2026-03-23
---

## 问题：IM UIKit iOS 18兼容性问题及SnapKit版本冲突

## 问题详情

**现象**：
集成IM UIKit后编译出现文件无法打开错误，以及SnapKit版本冲突问题。

## 排查过程

1. 客户反馈编译报错文件无法打开 → 技术支持建议检查libarclite文件配置
2. 尝试指定SnapKit版本到4.2.0 → 出现新的权限相关错误
3. 建议升级呼叫组件到2.5.2版本以兼容iOS 18

## 问题原因

iOS 18系统兼容性问题以及SnapKit版本不匹配导致编译失败。

## 解决方案

1. 对于iOS 18崩溃问题，升级呼叫组件到2.5.2版本
2. 对于SnapKit冲突，尝试指定pod 'SnapKit', '~> 4.2.0'版本
3. 移除RTC底层的libarclite相关文件

## 其他触发场景

（合并时在此处追加）
