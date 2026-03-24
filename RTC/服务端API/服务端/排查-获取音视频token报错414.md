---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 服务端API
platform: 服务端
title: 获取音视频token报错414
root_cause: 请求body格式应为表单提交(form-urlencoded)，而非JSON格式。
solution: 1. 确保使用application/x-www-form-urlencoded格式提交
2. 检查AppKey和AppSecret配置正确
3. uid为必传参数，使用Long类型纯数字
4. 参考官方Postman模板配置请求。
customers: ['云信-国信网安（上海）大数据科技']
source: chat_history
tags: ['RTC', 'token', '414', 'checksum', '服务端API']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：服务端 获取音视频token报错414

## 问题详情

**现象**：
调用/user/getToken.action接口返回code 414，desc为uid is empty或checksum错误。

**环境信息**：
- 平台：服务端
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认接口地址和传参方式
2. 检查AppKey和AppSecret配置
3. 对比Postman模板测试
4. 发现请求body格式错误

## 问题原因

请求body格式应为表单提交(form-urlencoded)，而非JSON格式。

## 解决方案

1. 确保使用application/x-www-form-urlencoded格式提交
2. 检查AppKey和AppSecret配置正确
3. uid为必传参数，使用Long类型纯数字
4. 参考官方Postman模板配置请求。

## 其他触发场景

（合并时在此处追加：`- [服务端] 获取音视频token报错414，来源：['云信-国信网安（上海）大数据科技']，2026-03-23`）
