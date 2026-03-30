---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-UIKit"
feature: "图片预览"
platform: "Android"
title: "Android长图在UIKit中预览模糊"
root_cause: "UIKit使用glide默认设置加载图片，长图会模糊"
solution: "在加载代码处添加.override(Target.SIZE_ORIGINAL, Target.SIZE_ORIGINAL)强行指定原图"
customers: ["北京爱和健康科技有限公司"]
source: "chat_history"
tags: ["UIKit", "Android", "图片预览", "模糊", "glide"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：Android Android长图在UIKit中预览模糊

## 问题详情

**现象**：
Android端长图在云信聊天中预览时同样模糊，需要解决。

## 排查过程

1. 技术分析 → UIKit中使用glide默认设置加载，长图会模糊
2. 提供解决方案 → 需要强行指定原图
3. 提供代码 → 添加.override(Target.SIZE_ORIGINAL, Target.SIZE_ORIGINAL)

## 问题原因

UIKit使用glide默认设置加载图片，长图会模糊

## 解决方案

在加载代码处添加.override(Target.SIZE_ORIGINAL, Target.SIZE_ORIGINAL)强行指定原图

## 其他触发场景
