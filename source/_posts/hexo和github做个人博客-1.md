title: Hexo 和 Github 做个人博客
author: 元芳
tags:
  - 技术
  - hexo
categories:
  - 原创
date: 2024-07-12 10:07:00
---
前面一直用公众号写文章，但发现比较散，不利于自己做知识管理。所以想搞个免费博客，私域，技术，经济都可以写。后面再用 gitbook 搞个在线书。

就选了比较流行的 hexo，然后免费部署到 github pages 上。很快就搭起来了，可以通过 [元芳的博客](https://iyuanfang.github.io/)访问。

这里主要讲原理和相关命令。如 git，node 的安装和使用可以自行搜索。

# Hexo

Hexo 原理是通过 node 将 Markdown 文件最后打包生成 html 和 js/css 静态文件，然后将这些静态文件放到免费托管就可以网络访问了。

Hexo 使用见{% post_link 'Hexo 官方入门文档' %}

安装 Hexo，然后运行，就可以浏览器查看站点了。

![运行](/images/pasted-2.png)

## Hexo-admin

我使用了 Hexo-admin 插件，这样可以可视化创建和修改文章。
![编辑](/images/pasted-1.png)

Markdown 语法很简单，参考这里 [Markdown 语法](https://markdown.com.cn/)

这个后台支持直接拷贝图片进来，但生成的 Markdown 文字有些问题，要改成"/"才能够正常显示图片。

## 主题

比较了很多 hexo 主题，最后选择了 fluid 主题，比较好看，又能配置很多东西。

![效果](/images/pasted-3.png)

# Github Pages

github pages 是 github 提供的免费静态文件托管站点。我开始想用 vercel，但发现生成的网站国内无法访问，所以还是用 pages 了。

步骤就是先在 github 创建一个名为"iyuanfang.github.io"仓库(这里 iyuanfang 替换成你自己的 github 账号)，然后将 hexo 的文件直接通过"hexo d" 部署到这个仓库，然后 github 会检测到文件变化，自动部署站点。github pages 还支持其它很多 action，但比较复杂，以后再研究，先用最基础的"Deploy from a branch"。
![deploy](/images/pasted-0.png)

hexo 生成静态文件并部署到 github pages 上

```bash
hexo g && hexo d
```

然后等待 github pages 自动构建，就可以看到新发布或修改的文章了

# 总结

Hexo 启动，然后在 admin 后台用 Markdown 写文章，同时可以预览效果，最后生成静态文件并一键 deploy 到 github pages。挺简单的，你也试试吧！