---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: Asset validation failed I
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 刚才配置了ios的推送证书，测试版本和开发版本的证书都提交了
customers: ["VIP云信-临沂久讯网络科技有限公司"]
source: chat_history
tags: ["token", "消息", "推送", "证书"]
created: 2025-01-07
updated: 2026-03-20
---

## 问题：iOS Asset validation failed I

## 问题详情

Asset validation failed Invalid Executable. The executable 'app.app/Frameworks/YXAlog_iOS.framework/YXAlog_iOS' contains bitcode. (ID: b2cedf36-0539-4a5f-aef5-d07d0fbf45cb)；这个库 是咱nim带的吧？；是的，我发一个文档给你，稍等；https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client；参考这个文档去除一下 Bitcode

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

刚才配置了ios的推送证书，测试版本和开发版本的证书都提交了

## 其他触发场景
