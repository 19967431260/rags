---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话
platform: Web
title: IM聊天报错会话id传null
root_cause: 代码传参错误，会话id传了null给群id
solution: 检查代码传参，确保会话id正确传递，不要传null给群id
customers: ["杭州美联数字医疗科技有限公司"]
source: chat_history
tags: ["会话id", "null", "传参错误", "Web"]
created: 2025-05-09
updated: 2025-03-20
---

## 问题：Web IM聊天报错会话id传null

## 问题详情

**现象**：
客户反馈IM聊天报错，之前都是好的。5台电脑都报同样的错误，不是同一网络。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Web

## 排查过程

1. 客户反馈IM聊天报错，截图显示错误信息\n2. 技术支持建议切换网络重新登录\n3. 客户反馈5台电脑都报错，不是同一网络\n4. 技术支持访问客户提供的线上页面进行排查\n**关键发现**：客户代码传参有问题，会话id传了一个null给群id\n5. 客户找前端咨询处理

## 问题原因

代码传参错误，会话id传了null给群id

## 解决方案

检查代码传参，确保会话id正确传递，不要传null给群id

## 其他触发场景

