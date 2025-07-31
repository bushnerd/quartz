---
{"publish":true,"cssclasses":""}
---

测试修改。
虽然有很多数据集，但是在日常使用中手机 APP 需要有 Map API 才能去正确下载瓦片数据。
[Map APIs](https://everydeveloper.com/apis/maps/) 此处列举了几种提供Map API的地方
# 1. Arcgis
```c
https://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{$z}/{$y}/{$x}
256
1-19
wgs84
```
![[../notes/attachments/20241008_114211.png]]
# 2. AnyGIS
在线地图合集
[AnyGIS | Online maps pack](https://anygis.ru/Web/Html/DownloadPage_en)
# 3. 是否带$$
`$s` 表i示服务器，在 xml 文件中的格式为 `servers=[01,02,03,04]`
```js
android, 带`$`
http://k.mv0.cc/vt/lyrs=y&hl=zh-CN&gl=cn&scale=2&x={$x}&y={$y}&z={$z}
IOS
http://k.mv0.cc/vt/lyrs=y&hl=zh-CN&gl=cn&scale=2&x={x}&y={y}&z={z}
```
# 4. Google
## 4.1. g
![[../notes/attachments/20241008_114235.png]]
## 4.2. ga
![[../notes/attachments/20241008_114259.png]]
## 4.3. flavor 原版
```js
google
256
1
23
gcj02

android
http://mt0.google.com/vt/lyrs=y&hl=zh-CN&gl=cn&x={$x}&y={$y}&z={$z}
ios
http://mt0.google.com/vt/lyrs=s&hl=zh-CN&gl=cn&x={x}&y={y}&z={z}

osmand
http://mts0.googleapis.com/vt/lyrs=s&x={1}&y={2}&z={0}
Zoom: 1-18
Expiry: 259200 (0.5 year)
其他的API都不行

备注：
$s:为下载服务器(servers)号，上表示Google有mt0,mt1, mt2,mt3四台下载服务器。
Lyrs:表示图层，可以组合，比如lyrs=s,m
Lyrs=y表示含标注的卫星图层，单独使用
Lyrs=s表示仅卫星图层，与其他标注图层配合使用

Lyrs=m表示为标准层
Lyrs=r表示为街道层
uhLyrs=p表示含标注的地形层
Lyrs=t表示仅地形层
Lyrs=h表示仅标签层
hl:为地图标注语言：zh-CN表示简体中文gl:为坐标系：cn表示中国国测局坐标
scale:为放大倍数，原有的谷歌的瓦片大小为256，两部路的最小瓦片大小为512，因此放大倍数为2。
x:为横向瓦片索引，最左边为0，向右步进为+1。两部路用参数$x传递该数值。
y:为纵向瓦片索引，最上边为0，向下步进为+1。两部路用参数$y传递该数值
z:为地图级别，数字范围为0-22。两部路用参数$z传递该数值。
```
## 4.4. 六只脚自带
```python
256
1
23
gcj02

http://k.mv0.cc/vt/lyrs=y&hl=zh-CN&gl=cn&scale=2&x={x}&y={y}&z={z}
```
## 4.5. googlecnapps
```python
256
1
23
gcj02

https://gac-geo.googlecnapps.cn/maps/vt?lyrs=y&gl=CN&x={x}&y={y}&z={z}&src=app&scale=2&from=app

https://gac-geo.googlecnapps.cn/maps/vt?lyrs=s&gl=CN&x={x}&y={y}&z={z}&src=app&scale=2&from=app
http://webst01.is.autonavi.com/appmaptile?x={$x}&y={$y}&z={$z}&lang=zh_cn&size=1&scale=1&style=8

```
# 5. Maxar
# 6. OpenCycleMap
[[notes/OpenCycleMap]]
精度为 10m，但是没有找到仅仅只是等高线的图层，如果可以的话，可以和别的卫星图层等一起来组合使用，那就好了。
OCM 也需要翻墙了？
```python
wgs84
https://tile.thunderforest.com/cycle/{$z}/{$x}/{$y}.png
地形
https://tile.thunderforest.com/landscape/{$z}/{$x}/{$y}.png
<host></host>
<minzoom>2</minzoom>
<maxzoom>19</maxzoom>
<tileSize>512</tileSize>
```
## 6.1. mapnik
主要地图
## 6.2. Thunderforest_outdoor
户外
## 6.3. Landscape
景观
## 6.4. Transport
交通
## 6.5. PublicTransport
公共交通
## 6.6. GPSTraces
用户上传的 GPS 轨迹
# 7. Amap 高德
```js
高德地标，仅包含地标
512
3
17
gcj02
https://wprd{$s}.is.autonavi.com/appmaptile?lang=zh_cn&size=1&style=8&x={$x}&y={$y}&z={$z}&scl=1&ltype=4
https://wprd{s}.is.autonavi.com/appmaptile?lang=zh_cn&size=1&style=8&x={x}&y={y}&z={z}&scl=1&ltype=4
servers=[01,02,03,04]
https://wprd03.is.autonavi.com/appmaptile?lang=zh_cn&size=1&style=8&x={x}&y={y}&z={z}&scl=1&ltype=4

高德道路，包含地标和道路，且不会覆盖底图
512
3
18
gcj02
http://webst{$s}.is.autonavi.com/appmaptile?x={$x}&y={$y}&z={$z}&lang=zh_cn&size=1&scale=1&style=8
servers=[01,02,03,04]
http://webst01.is.autonavi.com/appmaptile?x={$x}&y={$y}&z={$z}&lang=zh_cn&size=1&scale=1&style=8

高德道路详图，会覆盖地图，也不能用
512
3
18
gcj02
http://webrd01.is.autonavi.com/appmaptile?x={$x}&y={$y}&z={$z}&lang=zh_cn&size=1&scale=1&style=8
http://webrd01.is.autonavi.com/appmaptile?x={x}&y={y}&z={z}&lang=zh_cn&size=1&scale=1&style=8
http://webrd{$s}.is.autonavi.com/appmaptile?x={$x}&y={$y}&z={$z}&lang=zh_cn&size=1&scale=1&style=8

高德卫星，用处不大，并不清晰
512
3
17
gcj02
https://webst{$s}.is.autonavi.com/appmaptile?x={$x}&y={$y}&z={$z}&style=6
servers=[01,02,03,04]
```
# 8. Mapbox
```python
https://a.tiles.mapbox.com/v4/mapbox.satellite/{$z}/{$x}/{$y}.png?access_token=
256
1-21
GPS
```
# 9. MapQuest
[Static Map v4 API](https://developer.mapquest.com/documentation/static-map-api/v4/map/get/)
# 10. Here
[Hybrid Map Tile](https://developer.here.com/documentation/map-tile/dev_guide/topics/example-hybrid-map.html)
# 11. 透明图
ASTER 全球10m 等高线，但是现在已经失效
