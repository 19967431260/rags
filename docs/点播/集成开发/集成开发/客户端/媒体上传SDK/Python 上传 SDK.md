Python SDK 是用于服务器端点播上传的软件开发工具包，提供简单、便捷的方法，方便用户开发上传视频或图片文件的功能。

## <span id="功能特性">功能特性</span>

- 文件上传
- 获取进度
- 断点续传
- 查询视频
- 设置回调

## <span id="开发准备">开发准备</span>

### <span id="下载地址">下载地址</span>

[Python SDK 的源码地址](https://github.com/vcloud163/python-sdk.git "Python SDK 的源码地址")。

### <span id="环境准备">环境准备</span>

- 适用于 Python2 和 Python 3 版本。
- 登录 [网易云信控制台](https://app.yunxin.163.com/global/home) 在账户信息获取 AppKey 和 AppSecret。
- 下载 Python SDK，如果安装了 git 命令行，执行以下 Git 命令或者直接在 GitHub 下载 zip 包。您也可以通过执行 `python setup.py install` 安装。

    ```
    git clone https://github.com/vcloud163/python-sdk.git
    ```
- 参照 API 说明和 SDK 中提供的 demo，开发代码。

:::note note
SDK 依赖 requests 包，需自行安装。
:::

### <span id="HTTPS 支持">HTTPS 支持</span>

默认使用 https 协议，如需修改为 http 协议，请在 SDK 包中 config 目录修改。

## <span id="使用说明">使用说明</span>

### <span id="初始化">初始化</span>

接入网易云信视频点播，需要拥有一对有效的 AppKey 和 AppSecret 进行签名认证，可通过如下步骤获得：

- 开通网易云信视频点播服务。
- 登录 [网易云信控制台](https://app.yunxin.163.com/global/home) 在账户信息获取 AppKey 和 AppSecret。

在获取到 AppKey 和 AppSecret 之后，可按照如下方式进行初始化：

```Python
from vcloud import Client
client = Client(AppKey, AppSecret)
```

### <span id="文件上传">文件上传</span>

网易云信视频点播在全国各地覆盖大量上传节点，会选择适合用户的最优节点进行文件上传，并根据用户传入的参数做不同处理，具体请参考点播服务端 API 文档。

以下是使用示例：

```Python
from vcloud import Client
client = Client(appKey, secretKey)

#上传初始化的请求包体参数
body = {"originFileName":"beauty.mp4"}

#要上传文件的本地路径
localfile = '/Users/Royen/Documents/video/beauty.mp4'

res = client.upload_file(body, localfile)
```

:::note note
具体使用示例请参考 SDK 包中 examples 目录下的 upload.py 文件。
:::

### <span id="查询进度">查询进度</span>

网易云信视频点播文件上传采用分片处理，可通过以下方法查询上传完成的文件进度。SDK 提供回调函数接收文件上传进度。

以下是使用示例：

```Python
#负责接收进度的回调函数
def upload_progress(offset, size):
    if size == 0:
        print "upload process ... {0}".format("%5.1f%%" % (100 * 0))
    else:
        ratio = float(offset) / size
        print "upload process ... {0}".format("%5.1f%%" % (100 * ratio))

from vcloud import Client
client = Client(appKey, secretKey)

#上传初始化的请求包体参数
body = {"originFileName":"beauty.mp4"}

#要上传文件的本地路径
localfile = '/Users/Royen/Documents/video/beauty.mp4'

res = client.upload_file(body, localfile, upload_progress)
```

:::note note
具体使用示例请参考 SDK 包中 examples 目录下的 upload.py 文件。
:::

### <span id="断点续传">断点续传</span>

在上传文件中，网易云信视频点播通过唯一标识 context 标识正在上传的文件，可通过此标识获取到已经上传网易云信视频的文件字节数。通过此方法可实现文件的断点续传。

为防止服务中止造成文件上传信息丢失，可通过在本地存储文件信息来记录断点信息，当服务重新启动，可根据文件继续上传文件。临时文件会在上传完成后删除记录。记录断点的临时文件在配置文件 config.py 中配置。

使用示例如 4.2 所示。

### <span id="查询视频">查询视频</span>

视频上传成功后，可通过主动查询的方式获取到视频唯一标识，支持批量查询。

以下是使用示例：

```Python
from vcloud import Client
client = Client(appKey, secretKey)
#查询视频的请求包体参数
body = {"objectNames":["sdfs.mp4"]}

res = client.query_id(body)
if res != None:
    print "client.query_id res : {0}".format(vars(res))
else:
    print "query video error!"
```

:::note note
具体使用示例请参考 SDK 包中 examples 目录下的 upload_query.py 文件。
:::

### <span id="设置回调">设置回调</span>

如果设置回调，视频上传成功后会发送相关视频信息给回调接口。

以下是使用示例：

```Python
from vcloud import Client
client = Client(appKey, secretKey)

#设置回调地址的请求包体参数
body = {"callbackUrl":"http://1.111.11.1"}

res = client.set_callback(body)
if res != None:
    print "client.set_callback res : {0}".format(res)
else:
    print "set callback error!"
```

:::note note
具体使用示例请参考 SDK 包中 examples 目录下的 upload_set_callback.py 文件。
:::

## <span id="版本更新记录">版本更新记录</span>

1.0.0 (2021-07-22)

1. Python SDK 的初始版本，提供点播上传的基本功能。包括：文件上传、获取进度、断点续传、查询视频、设置回调。