---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 文档转码
platform: Web
title: PPT转码后JSON文件404问题
root_cause: PPT中某一页内容导致转码失败，影响整个文件
solution: 暂时移除导致问题的PPT页面。开发正在排查具体原因。
customers: ["海亮教育管理"]
source: chat_history
tags: ["互动白板", "PPT", "转码", "404", "JSON"]
created: 2025-02-21
updated: 2026-03-20
---

## 问题：Web PPT转码后JSON文件404问题

## 问题详情

**现象**：
客户反馈PPT转码后，转码出来的JSON文件访问404，且一个两三M的PPT好几分钟都没转好。

## 排查过程

1. 客户反馈转码后的JSON文件404
2. 技术支持排查发现转码文件地址无法访问
3. 客户测试发现去掉最后一页PPT后转码正常
4. 确认是特定PPT页面导致转码失败

## 问题原因

PPT中某一页内容导致转码失败，影响整个文件

## 解决方案

暂时移除导致问题的PPT页面。开发正在排查具体原因。

## 其他触发场景
- [Web] PPT转码后JSON文件404问题，来源：['海亮教育管理']，2026-03-20
- [Web] PPT转码后JSON文件404问题，来源：['海亮教育管理']，2026-03-20

