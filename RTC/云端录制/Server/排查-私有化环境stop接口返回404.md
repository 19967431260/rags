---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 云端录制
platform: Server
title: 私有化环境云端录制stop接口返回404
root_cause: stop返回404可能是房间内人员已退完导致房间关闭；视频黑屏是因为使用了非正规的网络穿透技术访问外网
solution: 1. stop接口返回404属于正常情况，房间关闭后仍可通过queryMediaFileByChannelId查询视频；2. 录制文件应在内网下载，不要通过外网绕一圈访问；3. 正常流程是在内网下载视频后上传到OSS
customers: ["飞虎互动"]
source: chat_history
tags: ["云端录制", "私有化", "404", "stop", "queryMediaFileByChannelId", "网络穿透"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Server 私有化环境云端录制stop接口返回404

## 问题详情

**现象**：
私有化部署环境中，云端录制submit和updateLayout接口调用正常返回200，但调用stop接口时返回404错误"room not found"。queryMediaFileByChannelId查询返回null，录制视频为纯黑屏。

**环境信息**：
- 部署方式：私有化部署

## 排查过程

1. 检查录制流程 → submit和updateLayout都正常返回state:1
2. 调用stop接口 → 返回404 room not found
3. 查询录制文件 → queryMediaFileByChannelId返回null
4. 重新发起录制 → 生成了视频但内容为纯黑屏

**关键发现**：外网访问视频为黑屏，内网访问正常

## 问题原因

stop返回404可能是房间内人员已退完导致房间关闭；视频黑屏是因为使用了非正规的网络穿透技术访问外网

## 解决方案

1. stop接口返回404属于正常情况，房间关闭后仍可通过queryMediaFileByChannelId查询视频
2. 录制文件应在内网下载，不要通过外网绕一圈访问
3. 正常流程是在内网下载视频后上传到OSS

## 其他触发场景
