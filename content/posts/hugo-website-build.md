---
author: liyiyuan
date: 2017-04-29 10:30:16+00:00
title: 基于hugo的静态博客建立及部署在GitHub上
---
### **开始之前：**


（这是一个非程序猿版本的hugo静态博客建立过程记录，我会尽量把每个步骤都认认真真记录下来）。

作为个人博客网站，为什么选择用静态博客呢？以及为什么选择hugo作为静态博客生成器呢？可以参考如下文章：

[11个最流行的静态(博客)网站生成工具](http://topspeedsnail.com/static-website-generators_or_tools/)

[开源静态博客生成器——jekyll、hexo、hugo怎么选？](https://www.simongong.net/xuan-ze-kun-nan-zheng/)

简单概括起来就是：1. 静态博客访问速度快，可以完全托管在GitHub上，不用另外花钱买主机；2. hugo生成静态博客速度非常之快，又比Jekyll构建简单许多（对于我们这些非程序猿们）。


### **过程记录：**


敲定hugo之后，接下来就是如何用hugo建立博客的问题了：

1. 首先简单环境介绍：  
windows 10    
hugo_0.20.6_windows-64bit.zip

2. git的一些简单操作命令的含义见： [Git远程操作详解](http://www.ruanyifeng.com/blog/2014/06/git_remote.html)

3. 安装hugo，下载地址：[https://github.com/spf13/hugo/releases](https://github.com/spf13/hugo/releases)    
在本地磁盘上建立文件目录（路径随意，例如）:`F:\github\hugo\bin`
把下载下来的hugo.exe二进制程序放进建立的bin文件夹中。
设置系统环境变量："我的电脑右键——属性——高级系统设置——高级——环境变量", 
选中PATH变量，"编辑——新建——F:\github\hugo\bin——确定". 这样PATH环境变量就设置好
了。然后"win+R"，输入cmd回车，进入command prompt，输入
    ```hugo
    hugo version
    ```
如果有版本提示，即表示安装成功。

4. 接下来hugo官方网站上有非常详细的步骤及视频教学：
[Hugo Quickstart Guide](https://gohugo.io/overview/quickstart/)。 
照着一步一步操作。或者另外两个hugo website建立的介绍：   
http://lucumt.info/posts/create-website-with-hugo/    
https://kknews.cc/tech/859ebkq.html

### **一些补充和自己的理解:**    
1. 修改baseURL可以直接在cmd命令行中实施，输入     	

	```
    hugo --theme=hyde --baseUrl="http://yiyuanli.github.io/blog"    
    ```  	
2. 我在实施的过程中发现一个问题，就是在最后面regenerate site的时候，cd ..
此时应该在blog根目录下：`F:\github\hugo\blog.` 接着在cmd中输入      	
	```
    hugo --theme=hugo_theme_robust
    ```
来重新生成静态网页。但接下来应该进入到`f:\github\hugo\blog\public`目录下
    ```git
    git add --all
    git commit -m "some changes"
    git push origin gh-pages 
    ```
(-f表示 -force，见[Git远程操作详解](http://www.ruanyifeng.com/blog/2014/06/git_remote.html)）
3. 如果部署在GitHub上建立的repository并不是http://yiyuanli.github.io, 例如我建立了一个repository http://yiyuanli.github.io/blog/, 则需要将所有的public push到gh-pages branch（分支）里， 而不能push到master branch中。
至此，就搭建好了一个基于hugo并部署在GitHub上的静态网站，并且可以手动更新。自动更新部分及个性域名设置后补。



### **时间分隔线：**

个性域名设置，参考： [利用Github Pages和基于Go的Hugo搭建个人博客](http://lucumt.info/posts/create-website-with-hugo/)

一些补充和自己的理解：

1. GitHub的主机IP地址为：    
192.30.252.153    
192.30.252.154    
故只需设置域名的A解析即可，其中point to填写上面两个ip地址，不用ping自己的网址
ip，参见[github官网方法](https://help.github.com/articles/setting-up-an-apex-domain/)。
