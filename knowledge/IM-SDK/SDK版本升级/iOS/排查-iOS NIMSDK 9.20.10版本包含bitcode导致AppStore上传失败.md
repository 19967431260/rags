---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: SDK版本升级
platform: iOS
title: iOS NIMSDK 9.20.10版本包含bitcode导致AppStore上传失败
root_cause: SDK中的YXAlog等库包含bitcode，与AppStore要求冲突
solution: |-
  在Podfile中添加post_install脚本，对需要去除bitcode的库执行bitcode_strip命令。示例：
  post_install do |installer|
    installer.pods_project.targets.each do |target|
      if target.name == 'YXAlog'
        `xcrun -sdk iphoneos bitcode_strip -r Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS -o Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS`
      end
    end
  end
  这样每次pod install都会自动去除，无需手动处理。
customers:
  - 淮南东东网络科技有限公司
source: chat_history
tags:
  - iOS
  - bitcode
  - AppStore
  - 上传失败
  - YXAlog
  - NIMSDK
created: '2025-06-23'
updated: '2025-03-23'
---

## 问题：iOS iOS NIMSDK 9.20.10版本包含bitcode导致AppStore上传失败

## 问题详情

**现象**：
使用iOS NIMSDK 9.20.10版本打包上传AppStore时，提示YXAlog、NIMSDK等库包含bitcode，导致上传失败。问题涉及YXAlog_iOS.framework、NIMSDK.framework等库。

**排查过程**：

1. 确认上传AppStore时报错，提示包含bitcode
2. 尝试使用NIMSDK_LITE版本，但lite版改动较大且后续可能需要搜索功能
3. 研发提供podfile脚本解决方案，在post_install中自动去除bitcode

**关键发现**：SDK中的YXAlog等库包含bitcode，与AppStore要求冲突

## 问题原因

SDK中的YXAlog等库包含bitcode，与AppStore要求冲突

## 解决方案

在Podfile中添加post_install脚本，对需要去除bitcode的库执行bitcode_strip命令。示例：
post_install do |installer|
  installer.pods_project.targets.each do |target|
    if target.name == 'YXAlog'
      `xcrun -sdk iphoneos bitcode_strip -r Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS -o Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS`
    end
  end
end
这样每次pod install都会自动去除，无需手动处理。
