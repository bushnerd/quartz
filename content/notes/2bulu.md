# 1. 图源
[[图源]]
## 1.1. gcn_amap
![20240229_104847](https://s2.loli.net/2024/04/13/bstjYnlVPyNDBAx.png)
## 1.2. gcn
![20240229_104857](https://s2.loli.net/2024/04/13/KaZbEpLeYN3Dkin.png)
## 1.3. google
![20240229_104908](https://s2.loli.net/2024/04/13/jTBhkS9iaqlt5ZQ.png)
## 1.4. kmv
![20240229_104918](https://s2.loli.net/2024/04/13/6pDyNTm58VrHwBI.png)
## 1.5. 图源瓦片大小
数值越小越清晰
android 版本瓦片大小无法设置为 256
## 1.6. 分享方式
![[两步路图源20240229104539 1.xms]]
### 1.6.1. xms 文件分享
6.8 版本支持
[两步路图源文件技术说明与制作教程-地图轨迹-技术交流-两步路社区](https://app.2bulu.com/community/gotohuatinfo.htm?id=YddfawiegZM6sT%2F6RvJvBQ%3D%3D)
### 1.6.2. 二维码分享
6.8 版本不支持，应该是在 7.0 以后
## 1.7. android 与 IOS 链接格式
新版本已经无所谓是否带`$`
新版本已支持组合图层
~~IOS 不支持组合图层~~
~~`$s` 表示服务器，在 xml 文件中的格式为 `servers=[01,02,03,04]`~~
```js
android, 带`$`
http://k.mv0.cc/vt/lyrs=y&hl=zh-CN&gl=cn&scale=2&x={$x}&y={$y}&z={$z}
IOS
http://k.mv0.cc/vt/lyrs=y&hl=zh-CN&gl=cn&scale=2&x={x}&y={y}&z={z}
```
# 2. 轨迹路网
## 2.1. 路网数据下载
为 2405 个区块，总大小为 4.75G
下载下来的数据存放在 `/storage/emulated/0/lolaage/TbuluTools/map/net/2/china/12345678.zip` 中，为 2405 个 zip 压缩包
导入时，先把原数据文件夹清空，再拷贝
这里提到 20230701 更新的，百度网盘中存储的路网数据，只有 2378 个文件
### 2.1.1. 分省
Android 支持分省下载，路径为`/storage/emulated/0/lolaage/TbubuTools/map/net/2/北京/12345678.zip`
### 2.1.2. 不分省
IOS 只能不分省
## 2.2. 路网数据分析
其中主要的数据为一个 shapefile(.shp 文件)，可以利用 Arcgis-ArcMap-ArcToolbox 转成 KMZ 文件，然后显示在 Google earth pro 中。
### 2.2.1. IOS
路网解压后的文件存放路径
`/var/mobile/Containers/Data/Application/577BBFD2-3F56-47F0-8585-0E13D5321CA8/Documents/roadNetworkFiles/road_54523318`
路网 zip 文件存放路径
`/var/mobile/Containers/Data/Application/577BBFD2-3F56-47F0-8585-0E13D5321CA8/Documents/roadNetworkFiles/`
### 2.2.2. Android
2405 个 zip 压缩包下载存放 `/storage/emulated/0/lolaage/TbuluTools/map/net/2/china`
解压缩并存放在 `/storage/emulated/0/lolaage/TbuluTools/cache/TrackNetwork/`
### 2.2.3. 路网文件与地图的实际对应关系
[roadnet-grid.surge.sh](https://roadnet-grid.surge.sh/)
## 2.3. 路网分类
原路网是 18 年以前的矢量格式
18-至今，为图片格式，把路网与地图合并成图片
以前-至今，和上面那个一样，但是看字面意思应该是全部的
![Pasted image 20230823111203](https://s2.loli.net/2024/04/13/2hxjmuMWETg7GkL.png)
## 2.4. 模拟路网服务器
[模拟路网服务器-以山之名](https://mp.weixin.qq.com/s?__biz=MzUxNjE2Nzc2Mg==&mid=2247495966&idx=2&sn=a8466ee9d218a0b9b8979a593c8d268e&chksm=f9a93023cedeb93593896d8c0400db74d9e597d5eb54880c5be15c8ee2905c3e27fcbf10d91e&scene=21#wechat_redirect)
# 3. 去广告，禁止升级
使用 MyAndroidToolsPro 可以禁用一些窗口和进程
# 4. 位置图片
虽然在界面上依然可以找到位置图片的功能菜单，但是即使是打开了也不会有图片显示。但是在 6.8.0 中又开始增加了类似于位置图片的功能，改名叫周边图片搜索功能。
与之前抓包分析下来的情况一致，可以得到周边图片的经纬度，描述等信息，但是依然会把图片下载链接进行加密。
# 5. Version_history
## 5.1. IOS
[[两步路_IOS]]
[[两步路_IOS_Version_history]]
[关于两步路户外助手部分服务下架的通知](https://app.2bulu.com/community/gotohuatinfo.htm?id=vYu%2BCDlpVRPRYpxh95ouYA%3D%3D)
2023 年 5 月底，两步路彻底取消了两步路的路网功能，旧版（ 6.7 以下）的手机 APP 也无法下载路网数据，但已有数据仍可继续使用。
## 5.2. 探索版
时隔两年多又开始了更新
而且还支持原来的路网
### 5.2.1. 版本: 7.4.1
版本更新日期
2023-04-10
### 5.2.2. 版本: 6.9.1
版本更新日期
2021-11-25
## 5.3. android
Android 的更新历史在 QQ 群公告里有
版本更新记录与 IOS 应该是一样的
## 5.4. 推荐版本
### 5.4.1. IOS6.6.5
相比 6.6.7 少了几个 VIP 才支持的路网，比较简洁
### 5.4.2. Android6.6.6
# 6. Mod
[[oa_overlay_for_ge]]
# 7. Ref
[以山之名](https://mp.weixin.qq.com/s/qdosm08hcDhLeXTb37NvYQ)公众号中有很多关于两步路研究的成果
[Site Unreachable](https://www.youtube.com/watch?v=IrsozYiiarE)
[找回两步路的路网功能 - 阅微堂](https://zhiqiang.org/outdoor/get-back-2bulu-roads.html)
