---
track_type: 排查类
sub_type: 线上事故
product: RTC
feature: 私有化部署
platform: 服务端
title: RTC私有化录制文件丢失问题
root_cause: 磁盘满导致录制转码失败，数据无法恢复
solution: 已修复自动清理脚本，建议配置告警通知（短信：18172899526，邮箱：liujianwen@corp.netease.com）
customers: ['河北八方浩达']
source: chat_history
tags: ['私有化部署', '录制失败', '磁盘满', '告警配置']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：服务端 RTC私有化录制文件丢失问题

## 问题详情

**现象**：
1月9号和10号的视频没有录制上，磁盘满了导致录制失败。

## 排查过程

1. 检查发现9号10号录制服务器磁盘满
2. 导致转码写盘失败
3. 已解决自动清理备份问题

## 问题原因

磁盘满导致录制转码失败，数据无法恢复

## 解决方案

已修复自动清理脚本，建议配置告警通知（短信：18172899526，邮箱：liujianwen@corp.netease.com）

## 其他触发场景

（合并时在此处追加）
