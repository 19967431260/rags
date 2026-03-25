---
track_type: 排查类
sub_type: 配置问题
product: 短信
feature: 短信签名
platform: 服务端
title: 短信签名需要ICP备案的App名称
root_cause: 短信签名需要与ICP备案的App名称一致
solution: 1. 短信签名需要有ICP备案的App名称，或使用企业简称；2. 对于较早创建的应用，建议新建一个应用使用短信功能，代码中修改appkey即可，不会影响已上架应用；3. 参考文档：https://doc.yunxin.163.com/sms/concept/Tk0MzA4NTQ?platform=server
customers: ["深圳自然生长"]
source: chat_history
tags: ["短信签名", "ICP备案", "验证码", "App名称"]
created: 2025-05-14
updated: 2025-03-23
---

## 问题：服务端 短信签名需要ICP备案的App名称

## 问题详情

**现象**：
手机接收不到验证码，返回错误与签名相关。使用的是之前App的名称，现在App改名了且暂时没有ICP备案。

**环境信息**：
- 平台：服务端

## 排查过程

**关键发现**：短信签名需要与ICP备案的App名称一致

## 问题原因

短信签名需要与ICP备案的App名称一致

## 解决方案

1. 短信签名需要有ICP备案的App名称，或使用企业简称
2. 对于较早创建的应用，建议新建一个应用使用短信功能，代码中修改appkey即可，不会影响已上架应用
3. 参考文档：https://doc.yunxin.163.com/sms/concept/Tk0MzA4NTQ?platform=server
