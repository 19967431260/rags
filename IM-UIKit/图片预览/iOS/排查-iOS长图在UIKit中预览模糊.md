---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-UIKit"
feature: "图片预览"
platform: "iOS"
title: "iOS长图在UIKit中预览模糊"
root_cause: "UIKit默认预览的是缩略图而非原图"
solution: "修改源码使用url而非path预览原图，或替换为自己的图片浏览器控件"
customers: ["北京爱和健康科技有限公司"]
source: "chat_history"
tags: ["UIKit", "iOS", "图片预览", "模糊", "长图"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：iOS iOS长图在UIKit中预览模糊

## 问题详情

**现象**：
长图在云信聊天中预览时特别模糊，只能下载到相册才能看得清晰。

## 排查过程

1. 客户提供录屏 → 技术支持分析
2. iOS端分析 → 发现预览的是缩略图而非原图
3. 提供解决方案 → 修改源码去掉if else语句，只保留urlString
4. 客户测试反馈 → loading消失后再次点击又变成缩略图
5. 最终建议 → 使用自己的图片浏览器替换SDK的

## 问题原因

UIKit默认预览的是缩略图而非原图

## 解决方案

修改源码使用url而非path预览原图，或替换为自己的图片浏览器控件

## 其他触发场景
