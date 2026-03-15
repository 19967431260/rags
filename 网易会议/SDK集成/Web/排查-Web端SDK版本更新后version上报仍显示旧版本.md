---
track_type: 排查类
sub_type: 使用问题
product: 网易会议
feature: SDK集成
platform: Web
title: Web端SDK版本更新后version上报仍显示旧版本
root_cause: 引入的js文件名未更新，仍使用旧文件名，导致浏览器缓存未刷新。
solution: 1. 确保引入的js文件名与实际文件名一致（如NEMeetingKit_v4.19.0.js）
2. 清除浏览器缓存
3. 重新发布应用
customers: ["VIP云信-四川辰海"]
source: chat_history
tags: ["版本更新", "缓存问题", "文件引入", "Web SDK"]
created: 2026-02-10
updated: 2026-03-15
---

## 问题：Web Web端SDK版本更新后version上报仍显示旧版本

## 问题详情

**现象**：
客户更新SDK文件到4.19.0后，上报的version仍显示4.14.1旧版本。

## 排查过程

1. 检查服务器资源文件 → 已更新为4.19.0
2. 检查引入的js文件名 → 仍引入NEMeetingKit.js而非NEMeetingKit_v4.19.0.js
3. 清除缓存重新发布 → 问题解决

## 问题原因

引入的js文件名未更新，仍使用旧文件名，导致浏览器缓存未刷新。

## 解决方案

1. 确保引入的js文件名与实际文件名一致（如NEMeetingKit_v4.19.0.js）
2. 清除浏览器缓存
3. 重新发布应用
