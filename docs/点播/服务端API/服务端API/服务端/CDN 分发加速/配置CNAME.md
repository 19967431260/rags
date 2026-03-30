配置加速域名后，您需要在域名解析服务商处，配置一条 CNAME 记录，将访问加速域名的请求指向 CNAME 域名。访问请求才能转发到 CDN 节点上，实现 CDN 加速。

## 背景信息

创建加速域名后，会给域名分配一个 **CNAME域名**，例如 `cdn.example.com`。

您需要在域名服务商处，配置一条 CNAME 记录，将访问加速域名的请求指向这个 `cdn.example.com`域名记录。

生效后，客户端访问加速域名时，DNS 解析会将请求指向网易云信 CDN，之后由 CDN 完成调度，使得该域名所有的请求都开始享有 CDN 加速效果。




## 操作步骤

假设您购买的一级域名为`example.com`。

1. 在网易云信控制台创建加速域名，例如您创建了自定义二级域名`cdn.example.com`。具体操作步骤请参见[添加加速域名](https://doc.yunxin.163.com/docs/jY3NDM4Nzc/DU1NDk4MTI?platformId=100066)。


    ![配置CNAME.png](https://yx-web-nosdn.netease.im/common/09a5cfd10650122bc76ca96ccdb00000/配置CNAME.png)


2. 在域名厂商后台添加解析记录时，您需要填写主机记录为加速域名对应的前缀，例如本示例中的前缀为**cdn** 。


::: note note
主机记录需要和加速前缀完全一致，请对应填写。
:::
  
常见域名类型的主机记录如下表所示。


创建的加速域名 | 域名类型 | 主机记录
---- | -------------- | ---------
example.com | 普通域名 | @
www.example.com | 普通域名|www|
cdn.example.com | 普通域名 |cdn |
video.cdn.example.com | 普通域名 | video.cdn |
.example.com | 泛域名 |*|
.cdn.example.com | 泛域名 | *.cdn |
 

::: note note
配置过程中如果 CNAME 记录与 A 记录冲突，您需要将 A 记录修改为 CNAME 记录
:::

## 验证CNAME解析是否正常

### Windows主机

在`cmd`命令提示符窗口中，选择如下命令中的任意一种方式，验证 CNAME 解析是否生效：

- `nslookup 域名`

- `nslookup -qt=CNAME CNAME`

- `nslookup -qt=CNAME CNAME域名`

如果返回的 Aliases 值为该加速域名在云信控制台对应的 CNAME 值，则说明 CNAME 解析正常。

![验证CNAME解析-Windows.png](https://yx-web-nosdn.netease.im/common/be560284e3b17f29362fe7f184e0cbdb/验证CNAME解析-Windows.png)

### Linux或mac主机

通过 Telnet 方式登录服务器，选择如下命令中的任意一种方式，验证 CNAME 解析是否生效：

- `dig 域名`

- `dig CNAME CNAME`

- `dig CNAME CNAME @域名`

如果返回的 CNAME 值为该加速域名在云信控制台对应的 CNAME 值，则说明 CNAME 解析正常。

![验证CNAME解析-Linux.png](https://yx-web-nosdn.netease.im/common/3e1c46f151b644771132aeaf89cc5615/验证CNAME解析-Linux.png)
