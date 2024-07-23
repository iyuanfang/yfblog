title: 开始用gitbook写在线书
author: 元芳
date: 2024-07-20 13:55:45
tags:
---
用hexo搭了博客，再用gitbook搭一个在线书。这样就可以方便的分享知识了。

# gitbook
gitbook很早就有了，但我一直没用，它开始是开源软件，可以将Markdown文件生成为网站、pdf、epub等格式。但后面转向商业，搞了 [专业网站](https://www.gitbook.com/)。

# 搭建
程序员出身，我还是希望自己搭建而不是在它的网站上写和发布。但搭建过程中碰到蛮多问题，说明真的好久没维护了，好多问题都没有修复。

先用npm安装

```
npm i gitbook-cli -g
```

然后创建一个目录，我是yfbook，用
```
gitbook init
```
然后报错，网上搜索照做解决。

![](/images/pasted-25.png)

说是因为官方js代码有问题，要找到这个js文件，然后把中间3行注释掉。

![](/images/pasted-26.png)

问题解决，目录下生成了README.md和SUMMARY.md。

然后编辑这两个Markdown文件（我用vs code）。


![](/images/pasted-27.png)

这里就是书的目录，我先验证gitbook，后续完善目录。

里面每一个.md文件就是一个章节，在里面填充内容。

然后运行'gitbook serve'看效果。

![](/images/pasted-28.png)


![](/images/pasted-29.png)

挺方便的，按照md的格式和内容就生成了网页。

然后试下生成pdf文件。用命令：

```
gitbook pdf
```
结果又报错，"Error during ebook generation: 'ebook-convert' 加一堆乱码"。

再搜索是没有安装calibre。原来gitbook要调用calibre才能生成pdf和epub。

安装calibre后，再执行命令，成功生成book.pdf。

至此gitbook本地跑通，写Markdown文件，可以生成网页和pdf电子书。

# 部署
最后就要把生成的网页和hexo一起部署在github上。

我的方法是使用
```
gitbook build
```
生成静态页面，然后把这些内容copy到hexo生成的public目录下，然后用
```
hexo d
```
部署到github pages上。

目录结构如下：

![](/images/pasted-30.png)
等github启动部署后，访问 [book](https://iyuanfang.github.io/book/)

就可以看到在线电子书了。

![](/images/pasted-31.png)

# 整合到hexo
如果每次都要手工copy生成的文件到hexo，那也比较麻烦。

而且我想把yfblog和yfbook放到一个github仓库中，方便写文章和书。

有什么好的办法吗？

我就想把yfbook放到yfblog文件夹下，然后生成到pulbic目录下，这样就整合到一起了。目录结构如下：


![](/images/pasted-32.png)

然后在yfblog目录命令中使用gitbook，通过参数指定运行和生成的output文件夹。

```
C:\Users\yuanfang\yfblog>gitbook serve ./yfbook ./public/book

C:\Users\yuanfang\yfblog>gitbook build ./yfbook ./public/book
```
这两个命令参数都一样，第一个是gitbook 的Markdown文件所在，第二个是运行和生成的文件夹。

最后 hexo g -d 部署到github pages上。搞定！







