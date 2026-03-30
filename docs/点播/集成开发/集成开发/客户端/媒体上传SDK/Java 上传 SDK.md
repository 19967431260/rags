Java-SDK 是用于服务器端点播上传的软件开发工具包，提供简单、便捷的方法，方便用户开发上传视频或图片文件的功能。

## <span id="功能特性">功能特性</span>

- 文件上传
- 获取进度
- 断点续传
- 查询视频
- 设置回调

## <span id="开发准备">开发准备</span>

### <span id="下载地址">下载地址</span>

- Java SDK 的下载地址：[vcloud-sdk-java.jar](https://nos.netease.com/vod163/vcloud-sdk-java.jar "Java SDK 的下载地址")

Java SDK 的源码地址：[java-sdk.git](https://github.com/vcloud163/java-sdk.git "Java SDK 的源码地址")

### <span id="环境准备">环境准备</span>

- 推荐使用 1.7 及以上版本的 jdk 开发。
- 登录 [网易云信控制台](https://app.yunxin.163.com/global/home) 在账户信息获取 AppKey 和 AppSecret。
- 下载 Java SDK，如果安装了 git 命令行，执行以下命令或者直接在 GitHub 下载 zip 包。

    ```
    git clone https://github.com/vcloud163/java-sdk.git
    ```
- 参照 API 说明和 SDK 中提供的 demo，开发代码。

### <span id="SDK 依赖包">SDK 依赖包</span>

- httpclient5-cache（5.0-alpha1）
- fastjson（1.2.7）
- httpmime（4.5.2）
- fluent-h（4.5.2）
- commons-logging（1.1.1）

### <span id="HTTPS 支持">HTTPS 支持</span>

默认使用 https 协议，如需修改为 http 协议，请在 SDK 包中 config 目录修改。

## <span id="使用说明">使用说明</span>

### <span id="初始化">初始化</span>

接入网易云信视频点播，需要拥有一对有效的 AppKey 和 AppSecret 进行签名认证，可通过如下步骤获得：

- 开通网易云信视频点播服务。
- 登录 [网易云信控制台](https://app.yunxin.163.com/global/home) 在账户信息获取 AppKey 和 AppSecret。

在获取到 AppKey 和 AppSecret 之后，可按照如下方式进行初始化：

```Java
Credentials credentials = new BasicCredentials(appKey, appSecret);
VcloudClient vclient = new VcloudClient(credentials);
```

### <span id="文件上传">文件上传</span>

网易云信视频点播在全国各地覆盖大量上传节点，会选择适合用户的最优节点进行文件上传，并根据用户传入的参数做不同处理，具体请参考点播服务端 API 文档。

以下是使用示例：

```Java
Credentials credentials = new BasicCredentials(appKey, appSecret);
VcloudClient vclient = new VcloudClient(credentials);

/*请输入上传文件路径*/
String filePath = "e:\\您好.mp4";

Map<String, Object> initParamMap = new HashMap<String, Object>();
/*输入上传文件的相关信息 */
/* 上传文件的原始名称（包含后缀名） 此参数必填*/
initParamMap.put("originFileName", FileUtil.getFileName(filePath));

QueryVideoIDorWatermarkIDParam queryVideoIDParam = vclient.uploadVideo(filePath, initParamMap);
```

:::note note
具体使用示例请参考 SDK 包中 upload/demo 目录下的 UploadVideoDemo 类文件。
:::

### <span id="查询进度">查询进度</span>

网易云信视频点播文件上传采用分片处理，可通过以下方法查询上传完成的文件进度。

以下是使用示例：

```Java
in = FileUtil.getFileInputStream(filePath);
Long fileSize = FileUtil.getFileLength(filePath);

/*上传文件剩余大小*/
Long remainderSize = fileSize;
/*分片上传视频*/
while (remainderSize > 0) {
    UploadVideoFragmentParam uploadVideoParam = vclient.uploadVideoFragment(initUploadVideoParam,
        getUploadHostParam, offset, context, in, remainderSize);
    context = uploadVideoParam.getContext();

    QueryOffsetParam queryOffsetParam = vclient.getPartOffset(getUploadHostParam.getUpload().get(0),
        initUploadVideoParam.getRet().getBucket(), initUploadVideoParam.getRet().getObject(), context,
        initUploadVideoParam.getRet().getxNosToken());

    // 使用断点续传查询 offset，文件全部上传之后，再通过 getPartOffset()是无法查询到 offset 的，即无法通过 remainderSize = FileUtil.getFileLength(filePath) - offset 将 remainderSize 设置为 0

    offset = queryOffsetParam.getOffset();
    if (null != offset) {
        remainderSize = fileSize - offset;
    } else {
        remainderSize = 0L;
    }
}
```

:::note note
具体使用示例请参考 SDK 包中 upload/demo 目录下的 Upload_RecoderDemo 类文件。
:::

### <span id="断点续传">断点续传</span>

在上传文件中，网易云信视频点播通过唯一标识 context 标识正在上传的文件，可通过此标识获取到已经上传网易云信视频的文件字节数。通过此方法可实现文件的断点续传。

为防止服务中止造成文件上传信息丢失，可通过在本地存储文件信息来记录断点信息，当服务重新启动，可根据文件继续上传文件。临时文件会在上传完成后删除记录。

以下是使用示例：

```Java
Credentials credentials = new BasicCredentials(appKey, appSecret);
VcloudClient vclient = new VcloudClient(credentials);

/*请输入上传文件路径*/
String filePath = "e:\\3.mp4";

Map<String, Object> initParamMap = new HashMap<String, Object>();
/*输入上传文件的相关信息 */
/* 上传文件的原始名称（包含后缀名） 此参数必填*/
initParamMap.put("originFileName", FileUtil.getFileName(filePath));
/* 本地用于存放上传进度相关信息的文件 */
String recorderFilePath = "e:\\1\\2.docx";

Recorder recorder = new UploadRecorder(recorderFilePath);

vclient.uploadVideoWithRecorder(filePath, initParamMap, recorder);
```

:::note note
具体使用示例请参考 SDK 包中 upload/demo 目录下的 Upload_RecoderDemo 类文件。
:::

### <span id="查询视频">查询视频</span>

视频上传成功后，可通过主动查询的方式获取到视频唯一标识，支持批量查询。

以下是使用示例：

```Java
Credentials credentials = new BasicCredentials(appKey, appSecret);
VcloudClient vclient = new VcloudClient(credentials);

/* 请输入 查询文件的对象名,参数必填*/
List<String> objectNamesList = new ArrayList<String>();
objectNamesList.add("33cf71b1-86ac-4555-a071-d70db07b9685.mp4");
objectNamesList.add("14e36114-13f8-48f4-b7a2-90b1b76c531c.mp4");

/*上传完成后查询视频主 ID 返回结果的封装类*/
QueryVideoIDorWatermarkIDParam queryVideoIDParam = vclient.queryVideoID(objectNamesList);
```

:::note note
具体使用示例请参考 SDK 包中 upload/demo 目录下的 QueryVideoIDDemo 类文件。
:::

### <span id="设置回调">设置回调</span>

如果设置回调，视频上传成功后会发送相关视频信息给回调接口。

以下是使用示例：

```Java
Credentials credentials = new BasicCredentials(appKey, appSecret);
VcloudClient vclient = new VcloudClient(credentials);

/* 上传成功后回调客户端的 URL 地址    参数必填*/
String callbackUrl = "http://127.0.0.1/client/callback";

/*设置上传回调地址接口输出参数的封装类*/
SetCallbackParam setCallbackParam = vclient.setCallback(callbackUrl);
```

:::note note
具体使用示例请参考 SDK 包中 upload/demo 目录下的 SetCallbackDemo 类文件。
:::

## <span id="版本更新记录">版本更新记录</span>

1.0.0 (2021-07-22)

Java SDK 的初始版本，提供点播上传的基本功能。包括：文件上传、获取进度、断点续传、查询视频、设置回调。