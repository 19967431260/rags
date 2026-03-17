---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: Token鉴权
platform: 通用
title: 移动端加入房间报错10119 checksum error
root_cause: token生成参数错误
solution: 检查生成token时传入的参数(uid、channelName、expireAt)是否正确,确保参数与实际使用场景匹配
customers: ["杭州帆特科技有限公司"]
source: chat_history
tags: ["10119","checksum error","token","移动端","鉴权"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：通用 移动端加入房间报错10119 checksum error

## 问题详情

**现象**：
PC端使用生成的token可以正常加入房间,但移动端使用不同uid生成的token加入时报错: join( check checksum error 10119。本地生成和服务端API生成的token都报同样错误

## 排查过程

1. uid=1的用户创建房间并生成token → PC端可以正常进入
2. uid=2的用户使用cid生成新token → 移动端报错10119
3. 尝试本地生成和服务端API生成 → 都报同样错误

**关键发现**: token校验失败

## 问题原因

token生成参数错误

## 解决方案

检查生成token时传入的参数(uid、channelName、expireAt)是否正确,确保参数与实际使用场景匹配

## 其他触发场景

