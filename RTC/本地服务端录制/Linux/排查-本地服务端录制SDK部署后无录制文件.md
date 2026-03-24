---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 本地服务端录制
platform: Linux
title: 本地服务端录制SDK部署后无录制文件
root_cause: 使用了错误的token类型。音视频的token和IM token不同，音视频token中普通用户和录制服务虚拟用户的token也不同。
solution: 1. 使用正确的音视频token（非IM token）
2. 确保房间内有普通用户进入（激活状态）才能获取录制服务token
3. 参考文档：https://doc.yunxin.163.com/nerecord/concept/Dc0NjcyMzA?platform=linux
customers: ["浙江惠瀜"]
source: chat_history
tags: ["本地录制", "Linux", "token", "checksum"]
created: 2025-02-13
updated: 2025-03-20
---

## 问题：Linux 本地服务端录制SDK部署后无录制文件

## 问题详情

**现象**：
按照官网文档部署本地服务端录制示例服务后，启动服务但在录制文件存储根目录下没有找到录制的文件。

**环境信息**：
- 平台：Linux
- 功能：本地服务端录制

**相关日志**：
checksum check fail

## 排查过程

1. 确认房间cid和房间名称
2. 检查Linux端是否加入房间 → 未进入
3. 查看SDK日志 → 发现checksum check fail错误
4. 确认token问题 → Linux端token有误
5. 获取正确的音视频token → 需要房间内有普通用户进入（激活状态）才能获取
6. 重新获取token后测试 → 录制成功

**关键发现**：token类型错误

## 问题原因

使用了错误的token类型。音视频的token和IM token不同，音视频token中普通用户和录制服务虚拟用户的token也不同。

## 解决方案

1. 使用正确的音视频token（非IM token）
2. 确保房间内有普通用户进入（激活状态）才能获取录制服务token
3. 参考文档：https://doc.yunxin.163.com/nerecord/concept/Dc0NjcyMzA?platform=linux

## 其他触发场景
