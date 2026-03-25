---
track_type: 排查类
sub_type: 配置开通咨询
product: 短信
feature: 短信发送
platform: 服务端
title: 短信API返回成功但用户未收到短信
root_cause: 短信签名PartyPlay未完善实名报备信息，国内短信发送需要实名认证。
solution: 在网易云信控制台补充短信签名实名信息。参考文档：https://doc.yunxin.163.com/sms/concept/Tk0MzA4NTQ?platform=server ，完成签名实名报备后短信可正常发送。
customers: ["景群數位互動有限公司"]
source: chat_history
tags: ["短信发送", "实名报备", "签名", "sendtemplate", "200"]
created: 2025-05-06
updated: 2025-03-20
---

## 问题：服务端 短信API返回成功但用户未收到短信

## 问题详情

**现象**：
调用短信发送接口https://api.netease.im/sms/sendtemplate.action返回code:200和sendid，但接收方未收到短信。接收号码为15638698252，签名PartyPlay。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：服务端

## 排查过程

1. 客户反馈短信发送成功但未收到 → 技术支持要求提供接收号码
2. 客户提供号码15638698252 → 技术支持查询发现签名未完善实名信息
3. 确认国内短信需要实名报备，引导客户按文档补充实名信息

## 问题原因

短信签名PartyPlay未完善实名报备信息，国内短信发送需要实名认证。

## 解决方案

在网易云信控制台补充短信签名实名信息。参考文档：https://doc.yunxin.163.com/sms/concept/Tk0MzA4NTQ?platform=server ，完成签名实名报备后短信可正常发送。

## 其他触发场景

