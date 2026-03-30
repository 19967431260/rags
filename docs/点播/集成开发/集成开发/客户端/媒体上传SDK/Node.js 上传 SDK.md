 ## <span id="简介">简介</span> 
Node.js-SDK是用于服务器端点播上传的软件开发工具包，提供简单、便捷的方法，方便用户开发上传视频或图片文件的功能。
## <span id="功能特性">功能特性</span>
- 文件上传
- 断点续传

## <span id="开发准备">开发准备</span>
### <span id="环境配置">环境配置</span>
1. 安装Node.js（0.11.x 以上版本）；
2. 执行`npm i vcloud-node-sdk --save`安装依赖包。

### <span id="模块引入">模块引入</span>
```js
let uploadSdk = require('vcloud-node-sdk');
```

### <span id="源码地址">源码地址</span>
[Node.js SDK 的源码地址](https://github.com/vcloud163/node-sdk.git "Node.js SDK 的源码地址")

## <span id="使用说明">使用说明</span>
### <span id="初始化">初始化</span>
接入网易云信视频点播，需要拥有一对有效的 AppKey 和 AppSecret 进行签名认证，可通过如下步骤获得：

- 开通网易云信视频点播服务；
- 登陆网易云信视频开发者平台，通过管理控制台->账户信息获取 AppKey 和 AppSecret。

在获取到 AppKey 和 AppSecret 之后，可按照如下方式进行初始化：

```js
uploadSdk.init({
    appKey: '[App Key]',
    appSecret: '[App Secret]',
    trunkSize: 4 * 1024 * 1024,
    logLevel: 'INFO'
});
```

**配置项说明：**

- appKey：AppKey
- appSecret：AppSecret
- trunkSize：分片大小，最大4MB
- logLevel：日志级别，支持：'ALL', 'TRACE', 'DEBUG', 'INFO', 'WARN', 'ERROR', 'FATAL', 'OFF'

### <span id="文件上传">文件上传</span>
调用upload接口，传入文件路径即可完成文件上传，路径支持相对路径（相对于index.js文件）或绝对路径（推荐）。

示例：

```js
uploadSdk.upload('E:/Hello.mp4');
```
### <span id="断点续传">断点续传</span>
upload接口同时支持断点续传，只需传入同一文件的路径再次调用upload接口即可，SDK会自动查询断点并进行续传。

示例：

```js
uploadSdk.upload('E:/Hello.mp4');
```
## <span id="版本更新记录">版本更新记录</span>
v1.0.3

1. Node-SDK初始版本，提供点播上传的基本功能，包括：文件上传、断点续传等。