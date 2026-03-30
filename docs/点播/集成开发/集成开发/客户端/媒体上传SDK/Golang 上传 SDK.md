Golang-SDK 是用于服务器端点播上传的软件开发工具包，提供简单、便捷的方法，方便用户开发上传视频或图片文件的功能。

## <span id="功能特性">功能特性</span>

- 文件上传
- 获取进度
- 断点续传
- 查询视频
- 设置回调

## <span id="开发准备">开发准备</span>

### <span id="下载地址">下载地址</span>

[Golang SDK 的源码地址](https://github.com/vcloud163/golang-sdk.git "Golang SDK 的源码地址")。

### <span id="环境准备">环境准备</span>

- 适用于 go 1.7 及以上版本。
- 通过 [网易云信控制台](https://app.yunxin.163.com/global/home) 账户信息获取 AppKey 和 AppSecret。
- 下载 Golang SDK，如果安装了 git 命令行，执行以下命令或者直接在 GitHub 下载 `.zip` 包。
    ```
    git clone https://github.com/vcloud163/golang-sdk.git
    ```
- 参照 API 说明和 SDK 中提供的 demo，开发代码。

### <span id="HTTPS 支持">HTTPS 支持</span>

默认使用 https 协议，如需修改为 http 协议，请在 SDK 包中 `config/configuration.go` 中修改。

## <span id="使用说明">使用说明</span>

### <span id="初始化">初始化</span>

接入网易云信视频点播，需要拥有一对有效的 AppKey 和 AppSecret 进行签名认证，可通过如下步骤获得：

- 开通网易云信视频点播服务。
- 登录网易云信视频开发者平台，通过管理控制台->账户信息获取 AppKey 和 AppSecret。

在获取到 AppKey 和 AppSecret 之后，可按照如下方式进行初始化，AppKey 和 AppSecret 配置在 config/configuration.go 文件中：

```Go
    import (
    "golang-sdk/auth"
    "golang-sdk/config"
    "golang-sdk/vcloudutil"
    )
    key := auth.Key{config.AppKey, config.AppSecret}
    vutil := vcloudutil.NewVcloudUtil(key)
```

### <span id="文件上传">文件上传</span>

网易云信视频点播在全国各地覆盖大量上传节点，会选择适合用户的最优节点进行文件上传，并根据用户传入的参数做不同处理，具体请参考点播服务端 API 文档。

以下是使用示例：

```Go
key := auth.Key{"", ""}
vutil := vcloudutil.NewVcloudUtil(key)

initParams := vcloudutil.UploadInitParams{}
initParams.OriginFileName = util.GetFileName(filePath)
initParams.UploadCallbackUrl = "http://127.0.0.1/abc"
vutil.Upload = vcloudutil.NewUploadUtil(initParams)

/* 上传初始化，获取 xNosToken（上传 token）、bucket（存储对象的桶名）、object（生成的唯一对象名） */
responseDate := vutil.Upload.InitUpload(config.InitUploadVideoURL, key)
if responseDate.Code != 200 {
    fmt.Println("Failed to init upload! Error message: " + responseDate.Msg)
    return
}

/* 获取上传加速节点地址 */
uploadHost := vutil.Upload.GetUploadHost(config.GetUploadHostURL, responseDate.Ret.Bucket)
from vcloud import Client
client = Client(appKey, secretKey)

/* 简单文件上传 */
vutil.Upload.UploadVideo(responseDate, uploadHost, filePath)
```

:::note note
具体使用示例请参考 SDK 包中 demo.go 文件的 UploadDemos 函数。
:::

### <span id="查询进度">查询进度</span>

网易云信视频点播文件上传采用分片处理，上传进度保存在用户自定义的本地文件中，可通过调用函数 GetUploadProcess 查询上传进度。

以下是使用示例：

```Go
vutil := vcloudutil.NewVcloudUtilNoKey()
/* "D:\\recoder.txt"为记录上传进度的本地文件 */
offset := vutil.GetUploadProcess("D:\\recoder.txt")
```

:::note note
具体使用示例请参考 SDK 包中 demo.go 文件的 GetUploadProcessDemo 函数。
:::

### <span id="断点续传">断点续传</span>

在上传文件中，网易云信视频点播通过唯一标识 context 标识正在上传的文件，可通过此标识获取到已经上传网易云信视频的文件字节数。通过此方法可实现文件的断点续传。

为防止服务中止造成文件上传信息丢失，可通过在本地存储文件信息来记录断点信息，当服务重新启动，可根据文件继续上传文件。临时文件会在上传完成后删除记录。

以下是使用示例：

```Go
/* recordFilePath 为本地保存断点信息的文件路径 */
recoder := vcloudutil.NewRecoder(recordFilePath)
/* filePath 为上传文件路径 */
object := vutil.Upload.UploadVideoWithRecorder(filePath, recoder, key)
```

:::note note
具体使用示例请参考 SDK 包中 demo.go 文件的 UploadWithRecoderDemo 函数。
:::

### <span id="查询视频">查询视频</span>

视频上传成功后，可根据视频上传后的返回结果，主动查询视频唯一标识，支持批量查询。

以下是使用示例：

```Go
/* 上传完成后，根据 objectName 查询视频 ID */
var objectNames []string
objectNames = append(objectNames, responseDate.Ret.Object)
queryRslt := vutil.Upload.QueryVideoIDorWatermarkID(config.QueryVideoIDURL, key, objectNames)
```

:::note note
具体使用示例请参考 SDK 包中 demo.go 文件的 UploadDemos 函数或 UploadWithRecoderDemo 函数。
:::

### <span id="设置回调">设置回调</span>

如果设置回调，视频上传成功后会发送相关视频信息给回调接口。

以下是使用示例：

```Go
ret := vutil.SetUploadCallback(config.SetUploadCallback, callback)
fmt.Println(ret.Code)
if ret.Code != 200 {
    fmt.Println(ret.Msg)
}
```

:::note note
具体使用示例请参考 SDK 包中 demo.go 文件的 SetUploadCallbackDemo 函数。
:::

## <span id="版本更新记录">版本更新记录</span>

**v1.0.0** (2021-07-22)

1. Golang SDK 的初始版本，提供点播上传的基本功能。包括：文件上传、获取进度、断点续传、查询视频、设置回调。