---
track_type: 排查类
sub_type: 客户环境问题
product: 其他
feature: 基础功能
platform: iOS
title: iOS Framework证书上传报错
root_cause: YXAlog框架的bitcode配置问题
solution: 在Podfile中添加post_install脚本对YXAlog进行bitcode_strip处理，或升级到新版本
customers:
  - 时间在线
source: chat_history
tags:
  - 证书
created: 2025-06-04
updated: 2025-03-23
---

## 问题：iOS Framework证书上传报错

## 问题详情

**现象**：
iOS应用上传App Store时提示framework证书有问题，报错`Invalid bundle structure`，具体为YXAlog_iOS.framework的二进制文件不被允许。

**复现步骤**：
1. 构建iOS应用
2. 上传App Store
3. 提示证书/ bundle结构错误

**相关日志**：
```
Invalid bundle structure. The "BreathTrain.app/Frameworks/YXAlog_iOS.framework/YXAlog_ios" binary file is not permitted
```

## 排查过程

1. 确认问题 → 客户按照网上处理方式都试过仍报错
2. 分析报错 → 确定是YXAlog库的问题
3. 提供解决方案 → 添加bitcode_strip处理脚本

**关键发现**：YXAlog框架的bitcode配置问题导致上传失败

## 问题原因

YXAlog框架的bitcode配置与App Store上传要求不兼容。

## 解决方案

1. 临时方案：在Podfile中添加post_install脚本：
```ruby
post_install do |installer|
  installer.pods_project.targets.each do |target|
    if target.name == 'YXAlog'
      `xcrun -sdk iphoneos bitcode_strip -r Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS -o Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS`
    end
  end
end
```

2. 长期方案：升级到新版本，新版本已去掉YXAlog库。

## 其他触发场景
