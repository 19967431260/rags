---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 登录问题
platform: Uniapp
title: Uniapp本地部署登录失败
root_cause: token不正确或已过期
solution: 使用正确的token登录，或通过服务端接口刷新token：https://doc.yunxin.163.com/messaging2/server-apis/DUwODIwMTg?platform=server
customers: ["吉林省大塘网络科技有限公司"]
source: chat_history
tags: ["Uniapp", "登录失败", "token", "UIKit"]
created: 2025-02-27
updated: 2026-03-20
---

## 问题：Uniapp Uniapp本地部署登录失败

## 问题详情

**现象**：
客户反馈Uniapp项目布置到本地后登录不上去。

## 排查过程

1. 查看控制台日志
2. 发现tokenInvalid错误
3. 确认是token不正确导致
4. 提供测试账号验证
5. 建议调用服务端接口刷新token

## 问题原因

token不正确或已过期

## 解决方案

使用正确的token登录，或通过服务端接口刷新token：https://doc.yunxin.163.com/messaging2/server-apis/DUwODIwMTg?platform=server

## 其他触发场景
- [Uniapp] Uniapp本地部署登录失败，来源：['吉林省大塘网络科技有限公司']，2026-03-20
- [Uniapp] Uniapp本地部署登录失败，来源：['吉林省大塘网络科技有限公司']，2026-03-20

