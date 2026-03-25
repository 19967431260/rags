---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 圈组
platform: iOS
title: NECoreQChatKit与NIMSDK_LITE版本冲突
root_cause: NECoreQChatKit和NECoreIMKit依赖的NIMSDK_LITE版本不一致
solution: 使用NOS_Special版本指定依赖：pod 'NECoreQChatKit/NOS_Special', '9.6.5'。如果仍有冲突，删除Podfile.lock后重新install，并确保qchatUIKit也使用special版本。
customers: ["时间在线"]
source: chat_history
tags: ["iOS", "NECoreQChatKit", "NIMSDK_LITE", "pod冲突", "NOS_Special", "圈组"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：NECoreQChatKit与NIMSDK_LITE版本冲突

## 问题详情

**现象**：
iOS集成NECoreIMKit和NECoreQChatKit时，由于依赖的NIMSDK_LITE版本不同导致pod冲突。

**环境信息**：
- 平台：iOS

## 排查过程

1. NECoreIMKit 9.6.7依赖NIMSDK_LITE 9.14.2
2. NECoreQChatKit 9.6.5依赖NIMSDK_LITE 9.14.0
3. 尝试指定NIMSDK_LITE版本仍有冲突
4. 建议使用NOS_Special版本

## 根因分析

NECoreQChatKit和NECoreIMKit依赖的NIMSDK_LITE版本不一致

## 解决方案

使用NOS_Special版本指定依赖：pod 'NECoreQChatKit/NOS_Special', '9.6.5'。如果仍有冲突，删除Podfile.lock后重新install，并确保qchatUIKit也使用special版本。

## 其他触发场景

（无）
