<!-- keywords: andriod 视频点播上传 sdk，andriod 上传 sdk,视频断点续传，视频上传接口-->
<!-- description: Android-SDK 是用于服务器端点播上传的软件开发工具包，提供简单、便捷的方法，方便用户开发上传视频或图片文件的功能。-->
Android SDK 是网易云信点播提供的用于服务器端点播上传的软件开发工具包，提供简单、便捷的方法，方便您开发上传视频或图片文件的功能。支持以下功能：

- 文件上传
- 获取进度
- 断点续传
- 查询视频

## <span id="下载地址">下载地址</span>

请访问 GitHub 获取 [Android SDK 的源码](https://github.com/vcloud163/andriod-sdk.git "android SDK 的源码地址")。

## <span id="开发准备">开发准备</span>

### <span id="环境准备">环境准备</span>

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) > 账户信息获取 AppKey。通过移动端上传支持接口获取 Accid、Token。
- 如果安装了 git 命令行，执行 `git clone https://github.com/vcloud163/andriod-sdk.git` 或者直接在 github 下载 zip 包。
- 参照 API 说明和 SDK 中提供的 demo，开发代码。

### <span id="HTTPS 支持">HTTPS 支持</span>

支持 HTTP 和 HTTPS 的上传，分别对应 `putFileByHttp` 和 `putFileByHttps`。
如果使用 HTTPS 上传失败，内部会退化为 HTTP 上传，无需外部干涉，对用户透明。

## <span id="使用说明">使用说明</span>

### <span id="初始化">初始化</span>

接入网易云信视频点播，需要拥有一对有效的 AppKey 和 Accid，Token 进行签名认证，可通过如下步骤获得：

开通网易云信视频点播服务。

登录网易云信视频开发者平台，通过管理控制台->账户信息获取 AppKey。通过移动端上传支持接口获取 Accid、Token。

在获取到 AppKey 和 Accid，Token 之后，可按照如下方式进行初始化：

```Java
NosUpload nosUpload = NosUpload.getInstance(context);
NOSUpload.Config config = new NOSUpload.Config();
config.appKey = "...";
config.accid = "...";
config.token = "...";
nosUpload.setConfig(config);
```

### <span id="文件上传">文件上传</span>

网易云信视频点播在全国各地覆盖大量上传节点，会选择适合用户的最优节点进行文件上传，并根据用户传入的参数做不同处理，具体请参考点播服务端 API 文档。

以下是使用示例：

```Java
//从本地的持久化数据中获取该文件对应的上传上下文(根据这个上下文，服务端知道该从哪个 offset 开始上传)
String uploadContext = nosUpload.getUploadContext(mFile);
NOSUpload.UploadExecutor executor = nosUpload.putFileByHttp(
                                    mFile,                //    文件
                                    uploadContext,         //    用于断点续传的上传上下文
                                    mBucket,            //    上传到云存储的 bucket
                                    mObject,             //    上传到云存储的 object name
                                    mNosToken,             //    上传需要的 token, 由 uploadInit 返回

    new NOSUploadHandler.UploadCallback() {
        @Override
        public void onUploadContextCreate(String oldUploadContext, String newUploadContext) {
        /**
         * 将新的 uploadcontext 保存起来
        */
            nosUpload.setUploadContext(mFile, newUploadContext);
        }

        //    上传进度的回调函数
        @Override
        public void onProcess(long current, long total) {
        }

        @Override
        public void onSuccess(CallResult ret) {
            executor = null;
            /**
             * 上传成功后，清除该文件对应的 uploadcontext
             */
            nosUpload.setUploadContext(mFile, "");
        }

        @Override
        public void onFailure(CallResult ret) {
        }

        @Override
        public void onCanceled(CallResult ret) {

        }
    }
);
```

:::note note
具体使用示例请参考 SDK 包中 `MainActivity.java` 文件。
:::

### <span id="查询进度">查询进度</span>

网易云信视频点播文件上传采用分片处理，可通过以下方法查询上传完成的文件进度。SDK 提供回调函数接收文件上传进度。

以下是使用示例：

```Java
nosUpload.putFileByHttp(
    mFile,                //    文件
    uploadContext,         //    用于断点续传的上传上下文
    mBucket,            //    上传到云存储的 bucket
    mObject,             //    上传到云存储的 object name
    mNosToken,             //    上传需要的 token

            new NOSUploadHandler.UploadCallback() {
        //    上传进度的回调函数
        @Override
        public void onProcess(long current, long total) {
        }
    }
```

:::note note
具体使用示例请参考 SDK 包中 `MainActivity.java` 文件。
:::

### <span id="断点续传">断点续传</span>

在上传文件中，网易云信视频点播通过唯一标识 `uploadContext` 标识正在上传的文件，可通过此标识获取到已经上传网易云信视频的文件字节数。通过此方法可实现文件的断点续传。

为防止服务中止造成文件上传信息丢失，可通过在本地存储文件信息来记录断点信息，当服务重新启动，可根据文件继续上传文件。临时文件会在上传完成后删除记录。

使用示例如 4.2 所示。

### <span id="查询视频">查询视频</span>

视频上传成功后，可通过主动查询的方式获取到视频唯一标识，支持批量查询。

以下是使用示例：

```Java
nosUpload.videoQuery(list, new NOSUploadHandler.VideoQueryCallback() {

    //    请求返回的 QueryResItem 列表
    @Override
    public void onSuccess(List<QueryResItem> list) {
    }
    //    请求失败的回调函数, 返回错误码和错误字符串
    @Override
    public void onFail(int code, String msg) {

    }
});
```

:::note note
具体使用示例请参考 SDK 包中 `MainActivity.java` 文件。
:::

## <span id="版本更新记录">版本更新记录</span>

**v1.0.0**

Android SDK 的初始版本，提供点播上传的基本功能。包括：文件上传、获取进度、断点续传、查询视频。