---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 旁路推流
platform: Server
title: 创建旁路推流任务报错layout不能为空
root_cause: layout参数为必填字段，不能传空值
solution: 参考文档示例填写layout参数，文档地址：https://doc.yunxin.163.com/nertc/server-apis/zI4MTk5NTU?platform=server
customers: ["顶呱呱科技股份有限公司"]
source: chat_history
tags: ["旁路推流","layout","参数校验"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Server 创建旁路推流任务报错layout不能为空

## 问题详情

**现象**：
客户调用创建旁路推流任务接口时报错，提示layout参数不能传空。

## 问题原因

layout参数为必填字段，不能传空值

## 解决方案

参考文档示例填写layout参数，文档地址：https://doc.yunxin.163.com/nertc/server-apis/zI4MTk5NTU?platform=server

## 其他触发场景

