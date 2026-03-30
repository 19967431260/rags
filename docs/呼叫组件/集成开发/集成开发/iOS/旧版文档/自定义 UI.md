本文介绍如何自定义呼叫组件 NERtcCallKit iOS 端的UI 界面。

## 自定义 UI 的操作步骤
1. 初始化 UI 组件。

    您可以通过如下两种方式初始化 UI 组件。
    
    - 只初始化UI组件（NERtcCallUIKit）

        ```objc
        NERtcCallUIConfig *config = [[NERtcCallUIConfig alloc] init];
        config.uiConfig.showCallingSwitchCallType = YES;
        config.uiConfig.enableVideoToAudio = YES;
        config.uiConfig.enableAudioToVideo = YES;
        [[NERtcCallUIKit sharedInstance] setupWithConfig:config];
        ```

    - 初始化 UI 组件同时初始化 API 组件。
    
        在 `NERtcCallUIConfig` 组件中透传 `appkey` 和 API 组件 `NERtcCallOptions` 初始化参数。

        ```objc
        NERtcCallUIConfig *config = [[NERtcCallUIConfig alloc] init];
        NERtcCallOptions *option = [NERtcCallOptions new];
        config.option = option;
        config.appKey = @"your app key";
        [[NERtcCallUIKit sharedInstance] setupWithConfig:config];
        ```

2. 调用 UI 状态机机制。

    为了方便开发者自定义 UI，呼叫组件 NERtcCallKit 根据不同的呼叫（如视频呼叫、音频呼叫等）和通话状态，提供了多个 Controller 类。请根据需要自定义的界面，继承对应的 Controller 类，并覆盖到呼叫组件内部。


    通过以下方法设置覆盖默认实现类：
    ```
    - (void)setCustomCallClass:(NSMutableDictionary<NSString *, Class> *)customDic
    ```
    
    NERtcCallUIKit 可用的状态键和默认类如下表所示。

    界面 | key | Class
    ---- | -------------- | ---------
    视频呼叫 |kVideoCalling |NEVideoCallingController
    音频呼叫 | kAudioCalling   | NEAudioCallingController 
    视频通话 | kVideoInCall     | NEVideoInCallController  
    音频通话 | kAudioInCall   | NEAudioInCallController  
    音频/视频被叫| kCalledState | NECalledViewController

    示例代码：

    ```objc
    // 初始化后注册自定义UI实现类
    NSMutableDictionary *cusstomDic = [[NSMutableDictionary alloc] init];
    [cusstomDic setObject:NEVideoCallingController.class forKey:kVideoCalling];
    [[NERtcCallUIKit sharedInstance] setCustomCallClass:cusstomDic];
    ```

3. 创建视频呼叫页面。

    继承组件内的视频呼叫 Controller 类来创建自定义视频呼叫页面。在自定义的 Controller 类中，您可以根据需求修改 UI 元素的颜色、位置、背景图片等。
    
    以下示例介绍视频呼叫页面，如何自定义取消呼叫的按钮。

    ```objc
    // 初始化后注册自定义UI实现类
    NSMutableDictionary *cusstomDic = [[NSMutableDictionary alloc] init];
    [cusstomDic setObject:CustomVideoCallingController.class forKey:kVideoCalling];
    [[NERtcCallUIKit sharedInstance] setCustomCallClass:cusstomDic];
    ```

    ```objc
    #import <NERtcCallUIKit/NERtcCallUIKit.h>
    @interface CustomVideoCallingController : NEVideoCallingController
    @end
    ```

    ```objc
    @interface CustomVideoCallingController ()
    @end
    @implementation CustomVideoCallingController
    - (void)viewDidLoad {
        [super viewDidLoad];
        // Do any additional setup after loading the view.
        // 隐藏主叫隐藏取消按钮示例(可以根据自己的需求修改颜色位置背景图片等)
        self.cancelBtn.hidden = YES;
    }
    @end
    ```

4. 绑定自定义事件。

    在自定义的Controller类中，为自定义的 UI 元素绑定事件。您可以将默认事件转移到自定义的 UI 元素上，或根据需要创建新的事件。

    ```objc
    #import "CustomVideoCallingController.h"
    @interface CustomVideoCallingController ()

    @property(nonatomic, strong) UIButton *customButton;

    @end
    @implementation CustomVideoCallingController
    - (void)viewDidLoad {
        [super viewDidLoad];
        // Do any additional setup after loading the view.

        // 自定义UI绑定事件
        self.cancelBtn.hidden = YES;
        [self customAction];
    }

    - (void)customAction {

        // 自定义挂断按钮
        self.customButton = [UIButton buttonWithType:UIButtonTypeCustom];
        self.customButton.translatesAutoresizingMaskIntoConstraints = false;
        [self.view addSubview:self.customButton];
        [self.customButton setTitle:@"挂断" forState:UIControlStateNormal];
        [NSLayoutConstraint activateConstraints:@[
            [self.customButton.centerYAnchor constraintEqualToAnchor:self.view.centerYAnchor],
            [self.customButton.centerXAnchor constraintEqualToAnchor:self.view.centerXAnchor],
            [self.customButton.widthAnchor constraintEqualToConstant:80],
            [self.customButton.heightAnchor constraintEqualToConstant:40]
        ]];

        // 绑定事件转移
        NSArray<NSString *> *targets = [self.cancelBtn.maskBtn actionsForTarget:self.mainController forControlEvent:UIControlEventTouchUpInside];
        for (NSString *target in targets) {
        [self.customButton addTarget:self.mainController action:NSSelectorFromString(target) forControlEvents:UIControlEventTouchUpInside];
        }
    }


    @end
    ```

##  UI 元素


![自定义UI-iOS.png](https://yx-web-nosdn.netease.im/common/13fe3239e3a6ab6776e7741d09f9b5ef/自定义UI-iOS.png)


```
/// 视频小窗画布
@property(strong, nonatomic) NEVideoView *smallVideoView;
/// 视频大窗画布
@property(strong, nonatomic) NEVideoView *bigVideoView;
/// 远端用户头像(主叫界面)
@property(strong, nonatomic) UIImageView *remoteAvatorView;
/// 远端用户头像(被叫&音频通话模式下使用)
@property(strong, nonatomic) UIImageView *remoteBigAvatorView;
/// 主叫远端用户显示(正在呼叫xxxxx...)
@property(strong, nonatomic) UILabel *titleLabel;
/// 远端用户名显示(被叫界面)
@property(strong, nonatomic) UILabel *centerTitleLabel;
/// 远端操作状态标签(主叫界面)
@property(strong, nonatomic) UILabel *subTitleLabel;
/// 邀请通话类型&远端状态
@property(strong, nonatomic) UILabel *centerSubtitleLabel;
```
```objc
/// 取消呼叫
@property(strong, nonatomic) NECustomButton *cancelBtn;
/// 拒绝接听
@property(strong, nonatomic) NECustomButton *rejectBtn;
/// 接听
@property(strong, nonatomic) NECustomButton *acceptBtn;
/// 麦克风
@property(strong, nonatomic) NECustomButton *microphoneBtn;
/// 扬声器
@property(strong, nonatomic) NECustomButton *speakerBtn;
/// 通话中音视频操作工具栏
@property(strong, nonatomic) NEVideoOperationView *operationView;
```

`NEVideoOperationView`的 UI 元素如下：

```objc
/// 麦克风
@property(strong, nonatomic) UIButton *microPhone;
/// 开启/关闭视频
@property(strong, nonatomic) UIButton *cameraBtn;
/// 挂断
@property(strong, nonatomic) UIButton *hangupBtn;
/// 开启/关闭静音
@property(strong, nonatomic) UIButton *speakerBtn;
/// 通话中音视频通话类型切换
@property(strong, nonatomic) UIButton *mediaBtn;
```


