---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 权限管理
platform: Android
title: 谷歌市场READ_MEDIA_IMAGES权限审核被拒
root_cause: 谷歌Play政策要求只有在核心场景才能使用READ_MEDIA_IMAGES等权限，需要提交声明或使用系统选择器
solution: 1. 提交谷歌权限声明说明聊天场景符合要求
2. 或将库复制出来改为本地依赖，移除权限请求代码
customers: ["VIP云信-重庆橙心物流网络"]
source: chat_history
tags: ["谷歌市场", "READ_MEDIA_IMAGES", "权限审核", "Flutter"]
created: 2025-10-31
updated: 2026-03-20
---

## 问题：Android 谷歌市场READ_MEDIA_IMAGES权限审核被拒

## 问题详情

**现象**：
使用IM UIKit Flutter版本，上传头像功能使用了READ_MEDIA_IMAGES和READ_MEDIA_VIDEO权限，导致谷歌市场上架被拒。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查权限使用 → 发现Android 33+使用READ_MEDIA_IMAGES/READ_MEDIA_VIDEO
2. 查看谷歌政策 → 要求使用系统图片选择器
3. 确认UIKit实现 → 图片选择使用系统选择器，但权限申请代码存在
**关键发现**：谷歌要求非核心场景不能使用媒体文件权限

**关键发现**：

## 问题原因

谷歌Play政策要求只有在核心场景才能使用READ_MEDIA_IMAGES等权限，需要提交声明或使用系统选择器

## 解决方案

1. 提交谷歌权限声明说明聊天场景符合要求
2. 或将库复制出来改为本地依赖，移除权限请求代码

## 其他触发场景

