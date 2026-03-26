---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: 服务端
title: IM登录失败code=191001：一般是authtype传的类型不对
root_cause: authtype参数传的类型枚举值不对，导致姿态签名验证失败
solution: 检查authtype传参的枚举类型是否正确，参考文档中的authtype枚举值说明进行修正。
customers: ["衢州雀之才科技"]
source: chat_history
tags: ["登录失败", "191001", "authtype", "姿态", "签名"]
created: 2025-07-06
updated: 2026-03-25
---

## 问题：IM登录失败code=191001：一般是authtype传的类型不对

## 问题原因

authtype参数传的类型枚举值不对，导致姿态签名验证失败

## 解决方案

检查authtype传参的枚举类型是否正确，参考文档中的authtype枚举值说明进行修正。
