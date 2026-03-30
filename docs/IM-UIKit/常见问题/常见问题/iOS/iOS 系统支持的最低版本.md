本文主要介绍 iOS 系统支持的最低版本。

当项目所支持的 iOS 最低版本高于 iOS 13 时，请在 Podfile 尾部添加：

```
post_install do |installer|
installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
    config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
    config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '13.0'
    end
end
end
```