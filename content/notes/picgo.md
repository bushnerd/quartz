---
{"publish":true,"cssclasses":""}
---

[GitHub - Molunerfinn/PicGo: :rocket:A simple & beautiful tool for pictures uploading built by vue-cli-electron-builder](https://github.com/Molunerfinn/PicGo)
# 1. 图床
[关于图床的一些使用心得总结 - 掘金](https://juejin.cn/post/7084137919845236743)
[2020 年，我的微信公众号 Windows 平台流程化写作与发布心得 - 少数派](https://sspai.com/post/59652)
[图床搭配 PicGo：打造高效的图片处理工作流 - 少数派](https://sspai.com/post/65716)
## 1.1. sm.ms
[SM.MS](https://sm.ms/home/apitoken)
免费5GB，速度能接受，访问基本正常。
## 1.2. github
使用 `https://cdn.jsdelivr.net` 作为 CDN，不是很稳定。
在 picgo 那个自定义链接那里填上就可以了，还挺方便。
```js
https://cdn.jsdelivr.net/gh/bushnerd/blog_cdn
//目录要先建好，注意斜杠在后面
img/
```
## 1.3. 七牛云
付费
## 1.4. gitee
不用考虑了，迟早会被封
# 2. plugin
## 2.1. compression
上传图片之前进行压缩，默认配置即可；
## 2.2. gitHub-plus
在相册中删除图片可以同步到 github；
## 2.3. webp
上传前将图片转化成 .webp 格式；
# 3. 配置文件
```c
D:\Users\ryan\AppData\Roaming\picgo\data.json
```