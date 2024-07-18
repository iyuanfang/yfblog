title: 给Hexo加上访问计数和评论
author: 元芳
tags:
  - hexo
categories:
  - 原创
date: 2024-07-18 18:35:00
---
Hexo原理是用Markdown文件生成html静态文件，不用依赖于数据库。但的确还是有些需要用数据库做存储的，比如访问计数和评论。

# 技术发展
技术最早前端和后端访问数据库的代码写在一起的，比如jsp早期，但这样可维护性太差。后来把业务逻辑从页面脱离，单独写到后端代码中。

再后来做前后端分离，前端页面通过AJAX技术调用后端的rest接口，前后端可以分开部署。

现在又出了云函数，就是后端服务器也不用管了，就是运行在互联网上的一段代码，你可以前端直接调用。也算是更彻底的前后端分离。

# 使用Leancloud
那么hexo虽然生成的是前端代码，但也可以调用云函数这类。

所以做计数和评论，也不用像原来那样自己搞一套服务器，然后搞数据库，写代码，部署这一整套。只要调用Leancloud的API就可以了。

fluid主题可以直接配置使用Leancloud。

![](/images/pasted-19.png)

![](/images/pasted-18.png) 

修改config.yml配置文件，打开评论comments为true，配置使用valine，然后填入Leancloud上的appid和appKey,重启hexo，评论就展示出来了。Leancloud注册和获取key，可以搜索，很简单。

我试着评论一下。

![](/images/pasted-20.png)

然后打开Leancloud控制台，可以看到创建了一张Comment表，插入了一行评论记录。展示的评论就是从这里读取。

![](/images/pasted-21.png)

计数也同样使用Leancloud，配置统计为true，并将下面的Leancloud配置写入同样的appid和appKey。

![](/images/pasted-22.png)

重启后，计数功能也有了。

![](/images/pasted-23.png)

Leancloud有开发板，也是免费的，只是每天流量有限制，个人玩玩没问题的。

