---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Web
title: Web端用户听不到其他人声音
root_cause: 系统退到后台后mic权限被回收或被其他应用占用，导致音频上行无声
solution: 监听SDK的local-track-state事件，提示用户进行相应处理，参考文档：https://doc.yunxin.163.com/nertc/guide/DM3NzExMzg?platform=web
customers: ["江苏华招网信息技术有限公司"]
source: chat_history
tags: ["RTC", "音频", "mic权限", "后台", "local-track-state"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web端用户听不到其他人声音

## 问题详情

**现象**：
客户反馈特定用户在会议中听不到其他人声音，但其他人可以听到他说话。关闭麦克风后重新开启可以恢复正常。

**环境信息**：
- 平台：Web

## 排查过程

1. 查看日志分析音频流状态 → 发现说话者上行音频异常
2. 怀疑mic权限被回收 → 建议监听local-track-state事件
3. 提供处理方案 → 参考文档处理后台权限回收问题

## 根因分析

系统退到后台后mic权限被回收或被其他应用占用，导致音频上行无声

## 解决方案

监听SDK的local-track-state事件，提示用户进行相应处理，参考文档：https://doc.yunxin.163.com/nertc/guide/DM3NzExMzg?platform=web

## 其他触发场景

（无）
