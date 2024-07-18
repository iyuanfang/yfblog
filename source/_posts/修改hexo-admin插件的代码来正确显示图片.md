title: 修改hexo-admin插件的代码来正确显示图片
author: 元芳
tags:
  - 技术
  - hexo
categories:
  - 原创
date: 2024-07-16 19:21:00
---
已经用hexo写了几篇文章了，[https://iyuanfang.github.io](https://iyuanfang.github.io/)

# 问题
但用hexo-admin上传图片发现一个小问题，就是当copy图片后，生成的Markdown文字不对，导致图片显示不出来。

生成的文字如下：
```
![upload successful](\\images\pasted-19.png\)
```
需要手工改成
```
![upload successful](/images/pasted-19.png)
```
这样图片才可以正常展示出来。

那么每上传一张图片后，都需要手工改这个生成的文字，还是挺烦的。我又是不喜欢做重复劳动的人，就想修改下插件的代码来修正这个问题，一劳永逸！

# 说干就干
插件的代码就在‘node_modules’文件夹里，找到hexo-admin文件夹，可以看到里面就是正常的js代码。
![](/images/pasted-15.png)

然后搜索'images' ，会发现在api.js里有这样的代码。


![](/images/pasted-16.png)

就是这里处理上传文件的！

往下一直找，找到了最后生成Markdown文字的地方。

![](/images/pasted-17.png)

这段代码写文件，并输出。

'src'就是输出的文字，它调用了path.join 方法，我懒得进去改，直接注释掉这句，然后用replace方法把反斜杠' \ '替换成' / '。

重启hexo服务，试着上传文件，这下生成的Markdown文字就正确了。

顺便我把图片的默认文字'upload successful' 在代码中也改成空，省的每次修改时要删除浪费时间。

这下省事了，上传图片无需修改文字，直接展示，搞定！

# 总结
很多东西其实没那么复杂，花了点时间改代码（js好久不用了，花了点时间捡起来），但后面就一劳永逸，不用做无用的重复劳动了。