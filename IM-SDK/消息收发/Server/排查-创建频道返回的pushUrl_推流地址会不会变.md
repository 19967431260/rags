---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Server
title: 创建频道返回的pushUrl 推流地址会不会变？ 
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 防盗链过期就变了，你们可以自己计算防盗链，也可以每次去调用接口获取完整地址。https://doc.yunxin.163.com/live-streaming/server-apis/DcwMzIyM
customers: ["VIP云信-惠州市脉链科技(蚂蚁报信)"]
source: chat_history
tags: ["云信", "技术支持", "历史会话"]
created: 2025-01-10
updated: 2026-03-20
---

## 问题：Server 创建频道返回的pushUrl 推流地址会不会变？ 

## 问题详情

创建频道返回的pushUrl 推流地址会不会变？  如果不是固定的什么情况会有变化？@云信技术支持-小易；@网易云信-王硕；防盗链过期就变了，你们可以自己计算防盗链，也可以每次去调用接口获取完整地址。https://doc.yunxin.163.com/live-streaming/server-apis/DcwMzIyMzI?platform=server；有没有NERoom 房间组件的源码Demo或最新直播Demo @网易云信-王硕  现在要对接直播需要；您这边的直播场景，是单人纯直播，还是有PK或者上麦的

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

防盗链过期就变了，你们可以自己计算防盗链，也可以每次去调用接口获取完整地址。https://doc.yunxin.163.com/live-streaming/server-apis/DcwMzIyM

## 其他触发场景
