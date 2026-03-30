---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 订阅画布
platform: Uniapp
title: 订阅画布报错uid参数undefined
root_cause: 订阅画布操作时机错误，必须在进入房间后且对方开始视频推流后才能订阅；uid参数为undefined导致订阅失败
solution: 订阅画布必须在进入房间后并且对方开始视频推流后才进行，uid参数应该是数字串，在joinChannel时设置。通过NERtcCallback的onJoinChannel回调监听加入房间结果。测试阶段可在管理后台将鉴权模式改为调试模式，无需计算token
customers: ["广西南宁探夕网络科技有限责任公司"]
source: chat_history
tags: ["订阅画布", "uid", "undefined", "joinChannel", "时序错误"]
created: 2026-02-09
updated: 2026-03-16
---

## 问题：Uniapp 订阅画布报错uid参数undefined

## 问题详情

**现象**：
Uniapp集成音视频2.0，刚开始发起就报错，提示订阅画布时uid参数为undefined。尚未进入房间就调用了订阅画布操作。

## 排查过程

1. 检查是否进入房间 → 未进入房间
2. 检查uid参数 → 发现为undefined

**关键发现**：订阅画布在进入房间前就被调用，且uid参数未正确传入

## 问题原因

订阅画布操作时机错误，必须在进入房间后且对方开始视频推流后才能订阅；uid参数为undefined导致订阅失败

## 解决方案

订阅画布必须在进入房间后并且对方开始视频推流后才进行，uid参数应该是数字串，在joinChannel时设置。通过NERtcCallback的onJoinChannel回调监听加入房间结果。测试阶段可在管理后台将鉴权模式改为调试模式，无需计算token

## 其他触发场景

