---
track_type: 排查类
sub_type: BUG问题
product: 易盾反垃圾
feature: 安全通回调
platform: Server
title: 安全通视频检测回调返回403 invalid signature
root_cause: 易盾生成的回调签名与云信侧校验不一致，导致签名校验失败返回403
solution: 需要易盾和云信双方联查签名生成和校验逻辑，确认签名算法一致性。易盾要求回调接口返回200才认为回调成功。
customers: ["技术｜VIP-易盾反垃圾｜杭州网易智企&深圳尚米"]
source: chat_history
tags: ["安全通", "回调失败", "403", "invalid signature", "视频检测"]
created: 2026-02-25
updated: 2026-03-15
---

## 问题：Server 安全通视频检测回调返回403 invalid signature

## 问题详情

**现象**：
安全通配置中视频消息检测开关已开启，但回调时返回403错误：invalid signature。部分taskId回调失败，部分成功。

## 排查过程

1. 确认业务配置中视频检测开关已开启
2. 检查回调日志发现返回403: invalid signature
3. 发现相同signature有时成功有时失败
4. 回调地址：http://internal-service.netease.im/nimserver/yidun/new/callback.action

## 问题原因

易盾生成的回调签名与云信侧校验不一致，导致签名校验失败返回403

## 解决方案

需要易盾和云信双方联查签名生成和校验逻辑，确认签名算法一致性。易盾要求回调接口返回200才认为回调成功。
