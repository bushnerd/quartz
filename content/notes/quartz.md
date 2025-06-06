#blog
# 1. Repo
已设为私有
[bushnerd/quartz](https://github.com/bushnerd/quartz)
https://bushnerd.github.io/quartz
https://bushnerd.github.io/
# 2. Content
```c
//笔记目录
D:\TXD\obsidian\notes_obsidian\notes\
//待发布目录
D:\github\quartz\content\notes\
```
pub_note
# 3. Command
```c
//初次安装
git clone https://github.com/jackyzha0/quartz.git
cd quartz
npm i
npx quartz create

//本地预览
npx quartz build --serve

//上传Github
//自动发布到Github pages
npx quartz sync
```
# 4. Issue
## 4.1. 图片大小
设定最大宽度，最大高度，由程序自动排版。
## 4.2. 白名单过滤发布的页面
几种方法，如果要安全性，就不能使用标签方式。
### 4.2.1. 软链接
最为保险，文件名更改了的话，则需要重新修改
### 4.2.2. ignorePatterns
需要仓库可以设为私有，如果名字更改了的话，则需要重新修改
```c
import { QuartzConfig } from './quartz/cfg' // 确保导入 QuartzConfig 类型

const config: QuartzConfig = {
  // ... 其他配置
  configuration: {
    pageData: {
      // ... 其他 pageData 配置
    },
    // 注意：这里的 plugins 数组可能会在你的 quartz.layout.ts 中
    // 或者其他地方，具体取决于你的 Quartz setup
    // 确保这里的 plugins 配置是你实际使用的
    plugins: [
      // ... 其他插件
    ],
    ignorePatterns: [
      "**/*", // 排除所有文件和文件夹
      "!my-first-blog-post.md", // 重新包含 'my-first-blog-post.md'
      "!another-article.md",    // 重新包含 'another-article.md'
      "!folder-of-published-notes/**/*.md", // 重新包含特定文件夹下的所有 .md 文件
      // 注意：如果您想包含某个文件夹本身，还需要：
      // "!folder-of-published-notes", // 重新包含文件夹本身（让Quartz能看到它）
      // 如果有子文件夹，可能需要 !folder-of-published-notes/**
      // 复杂的组合需要仔细测试
    ],
    // ... 其他 configuration 配置
  },
}

export default config
```
### 4.2.3. ~~3.1.3. Filter Plugins~~
> 不可用，所有非 Markdown 文件都会被输出并在最终构建中公开可用。这包括图像、音频录制、PDF 等文件。
#### 4.2.3.1. ExplicitPublish
白名单
#### 4.2.3.2. RemoveDrafts
黑名单
## 4.3. 不支持名字以中文开头的文件
以中文开头的文件会忽略，但是后来又可以了
中文名字会提示文字较长，后来有好了
## 4.4. 编辑/删除文件没有同步
## 4.5. ~~2.3. 在obsidian中不喜欢markdown中换行之间的空行，在obsidian中渲染没问题，但是到了别的场景下会因为没有空行导致无法换行~~
### 4.5.1. 解决
这个问题在quartz中已经没有了
### 4.5.2. 分析
段落之间的换行为2个换行符
段落内换行为2个空格
还是第一次知道markdown的语法
使用easy typing的customize convert rule可以实现
![[20241022_174057.png]]
并且在vim模式下o插入新行也可以。
但是如果又想连接两个空行，却会留下两个空格，能否用linter来帮忙去掉？
### 4.5.3. linter
使用obsidian的插件针对.md文件
添加一个自定义规则
不管在什么情况下，保证在内容与换行符之间有2个空格
```c
//成功
name: two-spaces-before-newline
description: Replaces any number of spaces (0, 1, or 3+) before a newline with exactly two spaces.
regex: ([^\s])\s*\n
replacement: $1  \n
gm: true

//不成功
name: remove-spaces-between-cjk-characters-single-line
description: Removes spaces between Chinese, Japanese, and Korean characters within a single line, preserving newlines.
regex: (?<=[\u4E00-\u9FFF\u3040-\u30FF\uAC00-\uD7AF])\s+(?=[\u4E00-\u9FFF\u3040-\u30FF\uAC00-\uD7AF])
replacement: 
gm: false
```
[关于obsidian内的换行问题 - 疑问解答 - Obsidian 中文论坛](https://forum-zh.obsidian.md/t/topic/9242/19)