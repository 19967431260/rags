
## <span id="指南介绍">指南介绍</span>  
1. 本指南主要介绍在 Windows 操作系统下使用 OBS 采集视频并实现上行 RTMP 推流。
2. OBS 是一款第三方开源免费的直播软件，目前支持 OS X、Windows、Linux 操作系统。
3. [OBS 官网](https://obsproject.com/download?spm=a2c4g.11186623.2.15.6aac1445JPlKR8)可以下载到适合您操作系统的版本，下载完成后，请按照引导进行安装。

## <span id="使用步骤">使用步骤</span>

### <span id="获取推流地址">获取推流地址</span>

1. 登录云信控制台，选择创建的应用，在【功能管理】的直播产品中，点击进入【直播管理】
2. 您可以在【直播管理】频道列表中点击【地址】查看推流地址，如下所示：

![1](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/get_push_url.png)

### <span id="设置直播参数">设置直播参数</span>

1. 打开OBS，点击主界面右下方【控件】-【设置】，进入设置界面

![2](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_setting.png)

2. 点击左侧功能栏的【推流】选项，进入推流服务设置页面

![3](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_push_setting.png)
    
    说明：
    服务：选项中选择自定义；
    服务器：填写推流地址，即：​rtmp://xxxxxx.live.126.net/live/​​；
    串流密钥：填写推流名称，即：​频道ID？wsSecret=xxxxxx&wsTime=xxxxxx​；

3. 点击【应用】保存设置信息

### <span id="选择直播来源">选择直播来源</span>
1. 在主界面下方【来源】区域单击右键添加，选择直播流来源

![4](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_live_source.png)

    说明：
    媒体流：表示本地媒体文件；
    显示器捕获：表示显示器的显示桌面；  
    窗口捕获：表示打开的程序窗口；
    视频捕获设备：表示摄像头；

### <span id="启动直播推流">启动直播推流</span>
1. 单击“开始推流”，开始直播推流，底部出现**绿灯**，表示推流成功

![5](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/Lark20200917-162048.png)

## <span id="其他设置">其他设置</span>

### <span id="编码器">编码器</span>
* 【设置】窗口中选择左侧功能栏的【输出】选项，如下图：

![6](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_coder.png)

* 【输出】设置页面中编码器包含**x264软件编码**和**QuickSync H.264硬件编码**
    * 软件编码：CPU负载重，性能较硬编码低，低码率下质量高于硬编码；
    * 硬件编码：节省CPU消耗，性能较好，低码率下质量低于软编码器；

### <span id="视频相关">视频相关</span>
**码率**
* 指【输出】设置页面中视频比特率，如下图：

![7](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_bitrate.png)

> 注意：<br/>码率越大，视频的画面越清晰，但同时对带宽的要求也越高。<br/>因此，需要根据自己的网络和设备适当调整分辨率和码率

**分辨率**
* 指【视频】设置页面中输出分辨率，如下图：

![8](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_resolution.png)

> 注意：<br/>分辨率越大，视频画面尺寸越大，若此时码率不变，则视频的画面会变差。<br/>因此，分辨率越大，码率也要设置越大

* 常用分辨率码率参照表：

| 分辨率| 建议码率 |
| --------- | ---------------- |
| 320 x 240 | 250kbps |
| 480 x 360 | 400kbps |
| 640 x 480 | 600kbps |
| 960 x 720 | 1000kbps |
| 640 x 360 | 550kbps |
| 960 x 540 | 850kbps |
| 1280 x 720 | 1200kbps |

**帧率**
* 指【视频】设置页面中FPS，如下图：

![9](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_framerate.png)

> 注意：<br/>
> 帧率越大，画面越流畅；帧率越小，画面越有卡顿感。帧率越高，每秒钟传输的视频画面越多，需要的码率也越高。<br/>
> 若低于 10 FPS，画面会出现较明显的卡顿；若高于 30 FPS，人眼无法识别出画面效果，反而增加带宽成本。<br/>
> 因此，**推荐设置帧率为 15 FPS**。

**关键帧间隔**
* 【输出】设置页面中选择“输出模式”的“高级”选项，可以设置“关键帧间隔”，如下图：


![POPO20220726-144248.jpg](https://yx-web-nosdn.netease.im/common/42ba9a74b0d3687cead529e1dbad87da/POPO20220726-144248.jpg)


> 注意：<br/>
> GOP（关键帧间隔） 越大，理论上同等压缩码率下画质越高，但同时延时会越大。<br/>
> 为了降低延时，通常会减少 GOP 帧的数量，从而减少播放器加载 GOP 帧所用的时间。<br/>
> 因此，直播一般**推荐设置GOP为 2**。

带有B帧的视频流会增加直播延时，所以在需要低延时直播时，建议推流时配置的Profile为不带B帧的baseline格式

### <span id="音频相关">音频相关</span>
**采样率**
* 【音频】设置页面中可以设置采样率，如下图：

![11](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_samplingrate.png)

* 采样率包括：44.1kHz和48kHz
    * 44.1kHz：CD音质，**超过该采样率，人耳很难分辨**；
    * 48kHz：DVD音质；

> 注意：采样率越高声音的还原就越真实越自然。

**声道**
* 【音频】设置页面中可以设置声道，如下图：

![12](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/obs_vocaltract.png)

* 声道包括：单声道、立体声、2.1、4.0、4.1、5.1 和 7.1
    * 单声道：只用1个音频通道记录声音
    * 立体声：双声道立体声，包含左声道和右声道，日常生活中最常听到的
    * 5.1：环绕立体声，包含5个全频段音频通道和1个低音声道，主要应用于电影行业

> 注意：<br/>多声道声音效果越好，但是如果播放器不支持，则无法正常播放。<br/>
> 因此，为了保证播放器能正常播放，**推荐设置最适用的双声道**