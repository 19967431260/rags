
## 问题现象

Flutter UIKit 的 iOS 端的相册和拍摄功能无法使用，不弹出获取权限弹框。

## 问题原因

permission_handler 兼容性问题。

## 解决方案

自行设置 permission_handler 的兼容性配置，具体可参考 [permission_handler 官网文档](https://pub.dev/packages/permission_handler)。

打开 ios/Podfile，在文件末尾新增如下权限代码。

```
post_install do |installer|
    installer.pods_project.targets.each do |target|
    flutter_additional_ios_build_settings(target)
    target.build_configurations.each do |config|        
            config.build_settings['EXCLUDED_ARCHS[sdk=iphonesimulator*]'] = 'arm64'               
            config.build_settings['ENABLE_BITCODE'] = 'NO'        
            config.build_settings["ONLY_ACTIVE_ARCH"] = "NO"    
        end
    target.build_configurations.each do |config|
            config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [
            '$(inherited)',
            'PERMISSION_MICROPHONE=1',
            'PERMISSION_CAMERA=1',
            'PERMISSION_PHOTOS=1',
            'PERMISSION_MEDIA_LIBRARY=1',
            ]
        end
    end
end
```