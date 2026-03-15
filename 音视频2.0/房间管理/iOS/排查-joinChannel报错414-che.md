---
track_type: 排查类
sub_type: 使用问题
product: 音视频2.0
feature: 房间管理
platform: iOS
title: joinChannel报错414 check checksum error
root_cause: 使用了IM的refreshToken接口获取token，该接口与RTC无关。RTC需要使用专门的getToken接口或自行生成token
solution: 使用正确的RTC token获取方式：1. 调用RTC的getToken接口获取token 2. 或根据文档自行生成token。确认appsecret、nonce、curtime等参数的有效值，可使用在线工具验证：https://www.iamwawa.cn/jiami.html。参考文档：https://doc.yunxin.163.com/nertc/server-apis/TcxNDAxMTI?platform=server
customers: ["上海功途教育"]
source: chat_history
tags: ["音视频2.0", "joinChannel", "414", "checksum error", "token", "安全模式"]
created: 2026-01-13
updated: 2026-03-15
---

## 问题：iOS joinChannel报错414 check checksum error

## 问题详情

**现象**：
互动直播场景下，调用joinChannel加入房间时报错：Error Domain=NERtcRemoteErrorDomain Code=414 "check checksum error"

## 排查过程

1. 检查应用配置 → 应用为安全模式，需要传token
2. 检查token来源 → 客户使用IM的refreshToken接口获取token
3. 确认token生成方式 → 后端服务器生成rtcToken
**关键发现**：客户混淆了IM token和RTC token，使用了错误的接口获取token

## 问题原因

使用了IM的refreshToken接口获取token，该接口与RTC无关。RTC需要使用专门的getToken接口或自行生成token

## 解决方案

使用正确的RTC token获取方式：1. 调用RTC的getToken接口获取token 2. 或根据文档自行生成token。确认appsecret、nonce、curtime等参数的有效值，可使用在线工具验证：https://www.iamwawa.cn/jiami.html。参考文档：https://doc.yunxin.163.com/nertc/server-apis/TcxNDAxMTI?platform=server

## 其他触发场景

（合并时在此处追加）
