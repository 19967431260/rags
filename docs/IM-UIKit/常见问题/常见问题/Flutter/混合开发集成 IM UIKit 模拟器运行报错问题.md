
## 问题现象

混合开发集成 IM Flutter UIKit 模拟器运行报错。

## 问题原因

Google 兼容性问题，XCode 14 以上版本会出现该问题。

## 解决方案

修改本地缓存文件。

在 **FlutterPluginRegistrant.podspec** 文件中添加以下内容进行模拟器支持配置：

```
s.pod_target_xcconfig = {
    'DEFINES_MODULE' => 'YES',
    'EXCLUDED_ARCHS[sdk=iphonesimulator*]' => 'i386 arm64'
}
```

::: note notice
由于上述修改的是本地缓存文件，因此，若您重新 `pod install`，需要重新修改本地的缓存文件。
:::