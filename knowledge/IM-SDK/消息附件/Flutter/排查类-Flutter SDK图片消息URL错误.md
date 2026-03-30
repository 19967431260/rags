---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息附件
platform: Flutter
title: Flutter SDK图片消息URL错误
root_cause: Flutter SDK 1.8.0版本存在bug，导致接收到的图片消息URL解析错误。iOS端使用1.8.2版本发送的消息URL是正确的，但Android端使用1.8.0接收时解析出错。
solution: 统一升级到Flutter SDK 1.8.2版本（对应NIMSDK 9.19.3）可解决问题。
customers: ['武汉乐乐助推科技有限公司']
source: chat_history
tags: ['Flutter', '图片消息', 'URL错误', 'nim_core', '1.8.0', '1.8.2', 'iOS', 'Android']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Flutter SDK图片消息URL错误

## 问题详情

**现象**：
客户反馈使用Flutter SDK时，发送图片消息后接收方收到的图片地址host错乱（如MzE1MTI3MTg=-nosdn.netease.im），导致无法显示。

## 排查过程

1. 客户反馈Android和iOS互发图片消息无法显示
2. 技术支持查看日志发现底层拿到的URL是正确的
3. 怀疑Flutter层做了转换导致问题
4. 客户确认使用的是nim_core: 1.8.0
5. 排查发现发送方URL正确，接收方URL错误
6. 怀疑与第三方回调有关，关闭后问题仍存在
7. 发现发送方日志中有1.8.2版本的发送记录，但客户声称都用1.8.0
8. 最终确认iOS端使用的是1.8.2（NIMSDK 9.19.3），Android端使用1.8.0（NIMSDK 9.18.0）
9. 统一升级到1.8.2后问题解决

## 问题原因

Flutter SDK 1.8.0版本存在bug，导致接收到的图片消息URL解析错误。iOS端使用1.8.2版本发送的消息URL是正确的，但Android端使用1.8.0接收时解析出错。

## 解决方案

统一升级到Flutter SDK 1.8.2版本（对应NIMSDK 9.19.3）可解决问题。

## 其他触发场景

（合并时在此处追加）
