---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频渲染
platform: Flutter
title: Flutter视频通话从浮窗返回后远端画面丢失
root_cause: 从Android浮窗返回Flutter后，远端视频渲染绑定丢失，需要重新绑定
solution: 返回Flutter页面时重新调用setupRemoteVideoRenderer，如不行则重新创建NERtcVideoView
customers: ['天津星如雨科技有限公司']
source: chat_history
tags: ['Flutter', 'RTC', '浮窗', '视频渲染', '远端画面']
created: 2025-02-26
updated: 2026-03-23
---

## 问题：Flutter Flutter视频通话从浮窗返回后远端画面丢失

## 问题详情

**现象**：
应用切换到桌面用安卓代码在浮窗播放视频，返回Flutter后只能预览本地视频，远程视频预览不到

**环境信息**：
- 平台：Flutter
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈从浮窗返回后远端画面丢失
2. 推流未断，本地视频正常
3. 浮窗使用Android端重新绑定了远端画面
4. 返回Flutter后需要重新绑定远端画面
5. 尝试didUpdateWidget方法但不行
6. 最终需要重新创建NERtcVideoView

## 问题原因

从Android浮窗返回Flutter后，远端视频渲染绑定丢失，需要重新绑定

## 解决方案

返回Flutter页面时重新调用setupRemoteVideoRenderer，如不行则重新创建NERtcVideoView

## 其他触发场景

（合并时在此处追加：`- [Flutter] Flutter视频通话从浮窗返回后远端画面丢失，来源：['天津星如雨科技有限公司']，2026-03-23`）
