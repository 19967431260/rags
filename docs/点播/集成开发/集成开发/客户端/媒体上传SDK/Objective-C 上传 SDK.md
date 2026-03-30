Objective-C SDK 是用于移动端点播上传的软件开发工具包，提供简单、便捷的方法，方便用户开发上传视频或图片文件的功能。

## <span id="功能特性">功能特性</span>

- 文件上传
- 获取进度
- 断点续传
- 查询视频

## <span id="开发准备">开发准备</span>

### <span id="下载地址">下载地址</span>

[Objective-C SDK 的源码地址](https://github.com/vcloud163/objc-sdk "Objective-C SDK 的源码地址")。

### <span id="环境准备">环境准备</span>

- 推荐使用 Xcode 7 及以上版本开发。
- 下载 Objective-C SDK，如果安装了 git 命令行，执行以下命令或者直接在 GitHub 下载。

    ```
    git clone https://github.com/vcloud163/objc-sdk
    ```
- 参照 API 说明和 SDK 中提供的 demo，开发代码。

### <span id="SDK 依赖包">SDK 依赖包</span>

- libz.tbd

### <span id="HTTPS 支持">HTTPS 支持</span>

默认使用 https 协议，如需修改在 Info.plist 中增加 NSAppTransportSecurity 中的 NSAllowsArbitraryLoads 为 true，支持 http。

## <span id="使用说明">使用说明</span>

### <span id="初始化">初始化</span>

接入网易云信视频点播，需要拥有一对有效的 AppKey 和 Accid，Token 进行签名认证，可通过如下步骤获得：

- 开通网易云信视频点播服务。
- 登录 [网易云信控制台](https://app.yunxin.163.com/global/home) 在账户信息获取 AppKey。通过移动端上传支持接口获取 Accid，Token。

在获取到 AppKey 和 Accid，Token 之后，可按照如下方式进行初始化：

```Objective-C
-(NSString *)NOSUploadAppKey{
    return kNOSTestAppKey;
}

-(NSString *)NOSVcloudAppAccid{
    return kNOSTestAccid;
}

-(NSString *)NOSVcloudAppToken{
    return kNOSTestToken;
}
```

### <span id="文件上传">文件上传</span>

网易云信视频点播在全国各地覆盖大量上传节点，会选择适合用户的最优节点进行文件上传，并根据用户传入的参数做不同处理。

以下是使用示例：

```Objective-C
//文件上传
if (isHttps) {
    [upManager putFileByHttps: localFileName bucket:bucket key:object
        token: token
        complete: ^(NOSResponseInfo *info, NSString *key, NSDictionary *resp) {
            NSLog(@"上传完成~~");
            NSLog(@"%@", info);
            NSLog(@"%@", resp);
        }
        option: option];
    } else {
    [upManager putFileByHttp: localFileName bucket:bucket key:object
        token: token
        complete: ^(NOSResponseInfo *info, NSString *key, NSDictionary *resp) {
            NSLog(@"上传完成~~");
            NSLog(@"%@", info);
            NSLog(@"%@", resp);
        }
        option: option];
    }
```

:::note note
具体使用示例请参考 SDK 包中 ViewController 类文件。
:::

### <span id="查询进度">查询进度</span>

网易云信视频点播文件上传采用分片处理，可通过以下方法查询上传完成的文件进度。

以下是使用示例：

```Objective-C
//可选参数集合:上传进度回调
NOSUploadOption *option = [[NOSUploadOption alloc] initWithMime: @"image/jpeg"
    progressHandler: ^(NSString *key, float percent) {
        NSLog(@"current progress:%f", percent);
    }
    metas: nil
    cancellationSignal: ^BOOL{
        return cancelUpload;
    }];
```

:::note note
具体使用示例请参考 SDK 包中 ViewController 类文件。
:::

### <span id="断点续传">断点续传</span>

在上传文件中，网易云信视频点播通过唯一标识 context 标识正在上传的文件，可通过此标识获取到已经上传网易云信视频的文件字节数。通过此方法可实现文件的断点续传。

为防止服务中止造成文件上传信息丢失，可通过在本地存储文件信息来记录断点信息，当服务重新启动，可根据文件继续上传文件。临时文件会在上传完成后删除记录。

以下是使用示例：

```Objective-C
//创建断点续传目录并记录
NOSFileRecorder *file = [NOSFileRecorder fileRecorderWithFolder:dir error:&error];
//配置基于位置服务的参数
NOSConfig *conf = [[NOSConfig alloc] initWithLbsHost: @"http://wanproxy.127.net"
                                        withSoTimeout: [_soTimeoutText.text intValue]
                    //withConnectionTimeout: [_connectTimeoutText.text intValue]
                                    withRefreshInterval: [_monitorInterval.text intValue]
                                        withChunkSize: [_chunkSizeText.text intValue] * 1024
                                    withMoniterInterval: [_monitorInterval.text intValue]
                                        withRetryCount: [_retryCountText.text intValue]];
//将其设置为全局变量
[NOSUploadManager setGlobalConf:conf];

if (error) {
    NSLog(@"%@", error);
}
//实例化上传管理类
upManager = [NOSUploadManager sharedInstanceWithRecorder: (id<NOSRecorderDelegate>)file
                                    recorderKeyGenerator: nil];
//设置上传管理类的 delegate
upManager.delegate = self;
```

:::note note
具体使用示例请参考 SDK 包中 ViewController 类文件。
:::

### <span id="查询视频">查询视频</span>

视频上传成功后，可通过主动查询的方式获取到视频唯一标识，支持批量查询。

以下是使用示例：

```Objective-C
//上传完成根据对象名查询视频或水印图片主 ID
[upManager videoQuery:[NSArray arrayWithObjects:upManager.objectName, nil] success:^(id responseObject) {
    NSLog(@"%@",responseObject);
} fail:^(NSError *error) {
    NSLog(@"%@",error);
}];
```

:::note note
具体使用示例请参考 SDK 包中 ViewController 类文件。
:::

## <span id="版本更新记录">版本更新记录</span>

1.0.0 (2021-07-22)

iOS SDK 的初始版本，提供点播上传的基本功能。包括：文件上传、获取进度、断点续传、查询视频。