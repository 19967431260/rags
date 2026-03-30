---
track_type: "排查类"
sub_type: "使用问题"
product: "RTC"
feature: "音频Dump"
platform: "Android"
title: "RTC音频Dump文件路径问题"
root_cause: "音频dump文件保存路径与init中设置的SDK日志路径不一致"
solution: "音频dump文件保存在SDK日志目录下，但可能与init设置的路径不同。可通过打印日志确认实际保存路径。"
customers: ["中讯邮电咨询设计院"]
source: "chat_history"
tags: ["RTC", "音频Dump", "startAudioDumpWithType", "日志路径"]
created: "2025-09-09"
updated: "2026-03-20"
---

## 问题：Android RTC音频Dump文件路径问题

## 问题详情

**现象**：
客户按照文档添加代码后，在手机上没有找到相关的音频dump日志文件。

## 排查过程

1. 客户反馈添加startAudioDumpWithType后找不到dump文件
2. 确认调用时机：onJoinChannel中start，leaveChannel前stop
3. 客户发现日志路径与init设置的路径不一致
**关键发现**：音频dump文件保存路径与SDK日志路径不同，客户在其他路径找到

## 问题原因

音频dump文件保存路径与init中设置的SDK日志路径不一致

## 解决方案

音频dump文件保存在SDK日志目录下，但可能与init设置的路径不同。可通过打印日志确认实际保存路径。

## 其他触发场景
