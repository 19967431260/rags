---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 音频引擎
platform: iOS
title: NEPitchUIKit集成报错Library not loaded
root_cause: NEPitchUIKit依赖的Masonry、BlocksKit、YYText等库未正确链接为动态框架
solution: 在Podfile的pre_install脚本中将所有缺失的库添加到dynamic_frameworks数组：
customers: ['通通派对']
source: chat_history
tags: ['NEPitchUIKit', 'Library not loaded', 'Masonry', 'BlocksKit', 'YYText', 'K歌']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：NEPitchUIKit集成报错Library not loaded

## 问题详情

**现象**：
引用NEPitchUIKit后运行报错，提示Library not loaded: @rpath/Masonry.framework/Masonry等依赖库找不到。

## 排查过程

1. 检查错误日志发现缺少Masonry、BlocksKit、YYText等依赖
2. 确认是use_frameworks!问题导致
3. 建议将缺失的库添加到dynamic_frameworks列表

## 问题原因

NEPitchUIKit依赖的Masonry、BlocksKit、YYText等库未正确链接为动态框架

## 解决方案

在Podfile的pre_install脚本中将所有缺失的库添加到dynamic_frameworks数组：
$dynamic_frameworks = ['libextobjc', 'Masonry', 'BlocksKit', 'YYText']

## 其他触发场景

（合并时在此处追加）
