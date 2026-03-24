---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 依赖管理
platform: Flutter
title: Flutter UIKit依赖的file_picker导致Google Play权限审核问题
root_cause: file_picker库用于发送文件类型消息，需要相关存储权限
solution: 若不需要发送文件消息，可将nim_chatkit_ui改为源码依赖，移除file_picker 8.1.7库。Flutter源码地址：https://github.com/netease-kit/nim-uikit-flutter/tree/release/9.7.3
customers: ['中科智感（湛江）科技发展有限公司']
source: chat_history
tags: ['Flutter', 'Google Play', '权限', 'file_picker', '审核']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：Flutter Flutter UIKit依赖的file_picker导致Google Play权限审核问题

## 问题详情

**现象**：
客户应用上传到Google Play时，因云信插件依赖的open_filex 4.6.0插件使用了READ_MEDIA_IMAGES、READ_MEDIA_VIDEO、READ_EXTERNAL_STORAGE权限，被Google Play要求说明权限用途。

## 排查过程

1. 客户反馈应用上传到Google Play出现权限审核问题
2. 技术支持检查依赖树，确认file_picker 8.1.7由nim_chatkit_ui引入
3. 提供两种解决方案：添加权限说明或移除依赖

## 问题原因

file_picker库用于发送文件类型消息，需要相关存储权限

## 解决方案

若不需要发送文件消息，可将nim_chatkit_ui改为源码依赖，移除file_picker 8.1.7库。Flutter源码地址：https://github.com/netease-kit/nim-uikit-flutter/tree/release/9.7.3

## 其他触发场景

（合并时在此处追加）
