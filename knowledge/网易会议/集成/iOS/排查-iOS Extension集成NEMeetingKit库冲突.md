---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 集成
platform: iOS
title: iOS Extension集成NEMeetingKit库冲突
root_cause: ""
solution: 删除冲突的库,Extension中直接使用 pod 'NEMeetingKit'
customers: ["安徽航峰信息科技有限公司"]
source: chat_history
tags: ["iOS", "Extension", "NEMeetingKit", "库冲突"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：iOS iOS Extension集成NEMeetingKit库冲突

## 问题详情

**现象**：
iOS项目Extension中集成会议SDK时出现库冲突错误

## 解决方案

删除冲突的库,Extension中直接使用 pod 'NEMeetingKit'

## 其他触发场景

（暂无）
