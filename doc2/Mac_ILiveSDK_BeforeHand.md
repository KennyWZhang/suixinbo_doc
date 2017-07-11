## 一 下载Demo
点击下载[Mac Demo](https://github.com/zhaoyang21cn/iLiveSDK_Mac_Suixinbo)的代码。演示了包含界面和后台交互的完整直播流程：<br/>

## 二 解压SDK压缩包

由于Github上有100MB文件上传限制，所以随心播工程中将QAVSDK压缩后再上传，要使随心播正常运行，请开发人员解压iLiveSDK_Mac_Suixinbo/SuixinboForMac/FrameworksMac/AVSDK.zip 到当前目录，解压后目录如下图所示:

![](http://mc.qcloudimg.com/static/img/e70b619d7c575b395680c4242f528f4f/image.png)

## 三 运行
编译运行工程。(最低支持MacOS 10.7)

* <div align=center>
<img src="http://mc.qcloudimg.com/static/img/259d05d27ffb3be35f2c739a9265397a/image.png"/>

* <div align=center>
<img src="http://mc.qcloudimg.com/static/img/a577ed2f15fb5fa3247f54c0c0ee301e/image.png"/>

## 四 集成到开发者自己的代码工程里
### 1 引入SDK并导入项目 

参照以上 第二步 

### 2 修改工程配置
将下载好的SDK复制到工程目录下，工程目录右键，Add Files to " you projectname",在demo中如下图所示：

1. Build Settings/Linking/Other Linker Flags，增加 -ObjC 配置，如下图所示：
![](http://mc.qcloudimg.com/static/img/9e48e62964428b6b12e11c262ff29178/image.png)

2.设置最低版本大于或等10.7,Build Settings -> macOS Deployment Target -> macOS 10.7,如下图所示：

![](http://mc.qcloudimg.com/static/img/592954bf985115b7089147800a3667c8/image.png)

若上述步骤均无误，则工程编译可以通过了。

### 3 修改后台地址
目前随心播后台主要用来维护直播房间列表。如果复用随心播客户端代码，需要修改随心播后台地址为业务方自己部署的服务器地址。 <br />     

| 请求类| 说明 | 修改文件 | 修改方法 |
|---------|---------|---------|---------|
| LiveAVRoomIDRequest | 获取自己分配的房间号 |LiveAVRoomIDRequest.m|- (NSString *)url |
| LiveStartRequest | 创建新房间 |LiveStartRequest.m|- (NSString *)url |
| LiveEndRequest | 退出房间 |LiveEndRequest.m|- (NSString *)url |
| LiveListRequest | 获取房间列表 |LiveListRequest.m| - (NSString *)url |
| LiveHostHeartBeatRequest | 房间心跳 |LiveHostHeartBeatRequest.m|- (NSString *)url |
| LiveImageSignRequest | 图片上传相关 |LiveImageSignRequest.m|- (NSString *)url |

### 4 添加系统库
添加以下系统库比较方便的方法是直接从随心播工程中，将SystemLibrarys组拖到自己的工程目录下

|  需要增加的系统库 |
|------------|
|QuartzCore.framework|
|CoreTelephony.framework|
|CoreWLAN.framework|
|Foundation.framework|
|SystemConfiguration.framework|
|libc++.tbd|
|libiconv.tbd|
|libresolv.9.tbd|
|libsqlite3.tbd|
|libstdc++.6.tbd|
|libz.tbd|

## 5 添加腾讯相关依赖库

|序号|名称|所在文件夹|说明|是否必须|
|--|--|--|
|1|QAVSDK.framework|FrameworksMac/AVSDK/|音视频SDK|必须|
|2|xplatform.framework|FrameworksMac/AVSDK/|音视频跨平台支持库|必须|
|3|IMCore.framework|FrameworksMac/IMSDK/|即时通讯核心库|必须|
|4|ImSDK.framework|FrameworksMac/IMSDK/|即时通讯Mac平台封装库|必须|
|5|QALSDK.framework|FrameworksMac/IMSDK/|即时通讯网络模块SDK|必须|
|6|TLSSDK.framework|FrameworksMac/IMSDK/|即时通讯登录服务SDK|必须|
|7|ILiveSDK.framework|FrameworksMac/|互动直播基础功能SDK|必须|
|8|TILFilterSDK.framework|FrameworksMac/|互动直播美颜依赖库|非必须|

