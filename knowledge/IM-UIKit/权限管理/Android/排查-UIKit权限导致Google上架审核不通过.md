---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 权限管理
platform: Android
title: UIKit权限导致Google上架审核不通过
root_cause: 使用的是早期开源UIKit版本（已停止维护），该版本包含的权限声明不符合Google Play当前审核要求
solution: 自行添加权限使用说明，或尝试移除这些权限（非SDK必需），或升级到维护中的UIKit版本
customers: ["上海超旺信息科技有限公司"]
source: chat_history
tags: ["Android", "UIKit", "权限审核", "Google Play", "READ_MEDIA_IMAGES", "READ_MEDIA_VIDEO"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Android UIKit权限导致Google上架审核不通过

## 问题详情

**现象**：
使用Android UIKit 4.8.2版本上架Google Play时，提示READ_MEDIA_IMAGES/READ_MEDIA_VIDEO权限不符合使用要求。

## 问题原因

使用的是早期开源UIKit版本（已停止维护），该版本包含的权限声明不符合Google Play当前审核要求

## 解决方案

自行添加权限使用说明，或尝试移除这些权限（非SDK必需），或升级到维护中的UIKit版本

## 其他触发场景

（暂无）
