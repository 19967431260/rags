---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 组件集成
platform: iOS
title: 会议组件与UIKit IM依赖冲突解决
root_cause: 会议组件和UIKit组件存在IM依赖重复
solution: 修改netease_meeting_kit.podspec使用NERoomKit/Base_FCS_Special版本去除组件内IM依赖，主项目Podfile新增Pod.const_set(:SPECIAL_VERSION, true)
customers: ['深圳市森愈网络科技有限公司']
source: chat_history
tags: ['依赖冲突', 'iOS', '会议组件', 'UIKit', 'podspec']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：iOS 会议组件与UIKit IM依赖冲突解决

## 问题详情

**现象**：
iOS运行时报错，经排查是会议组件和UIKit组件存在IM依赖重复

## 排查过程

1. iOS运行报错 → 建议选带rosetta后缀的模拟器
2. 客户无此选项 → 建议重新pod install
3. 真机也报错 → 排查依赖冲突
4. 发现会议组件和uikit组件有IM依赖重复
5. 建议修改podspec使用Special_All版本去除组件内IM依赖

## 问题原因

会议组件和UIKit组件存在IM依赖重复

## 解决方案

修改netease_meeting_kit.podspec使用NERoomKit/Base_FCS_Special版本去除组件内IM依赖，主项目Podfile新增Pod.const_set(:SPECIAL_VERSION, true)

## 其他触发场景

（合并时在此处追加）
