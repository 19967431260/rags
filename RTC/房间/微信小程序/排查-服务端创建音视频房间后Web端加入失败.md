---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间
platform: 微信小程序
title: 服务端创建音视频房间后Web端加入失败
root_cause: 1.使用cid而不是cname进入房间；2.创建播放任务时playTs参数有问题
solution: 1.使用cname（房间名称）进入房间而不是cid；2.修正playTs参数后创建播放任务成功；3.不建议cname用中文
customers: ["VIP-云信-北京艺典"]
source: chat_history
tags: ["RTC","房间","cid","cname","播放任务","playTs"]
created: 2025-08-10
updated: 2026-03-26
---

## 问题：微信小程序 服务端创建音视频房间后Web端加入失败

## 问题详情

**现象**：
客户通过服务端API创建音视频通话2.0房间，云端播放任务也创建了，返回房间号是1349234119069629，在Web端demo中进入房间提示失败

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认返回的是cid，前端demo是输入cname进入的 → 混淆了cid和cname
2. demo有自己的appkey，服务器创建的用的是客户的appkey → appkey不匹配
3. 报错playTs参数有问题，修正后成功 → 参数错误

**关键发现**：使用cid而不是cname进入房间；创建播放任务时playTs参数有问题

## 问题原因

1. 使用cid而不是cname进入房间；2. 创建播放任务时playTs参数有问题

## 解决方案

1. 使用cname（房间名称）进入房间而不是cid；2. 修正playTs参数后创建播放任务成功；3. 不建议cname用中文

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
