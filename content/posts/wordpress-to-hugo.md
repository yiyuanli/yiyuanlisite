---
author: liyiyuan
date: 2017-10-15 10:30:16+00:00 
title: wordpress转hugo，并托管在GitHub上
---

在转之前我发现网上很少有介绍word press转hugo的中文文章，大多数都是
word press转hexokinase或者Jekyll。 但是由上篇文章总结来看hugo目前是
最适合静态网页生成器，故总结在此作为大家参考。

wordpress动态网页转hugo静态网页并托管在GitHub上一共可以分成三步： 
   
1. 在本地建立hugo site；    
2. 把wordpress内容转为markdown格式并放入本地hugo site中；    
3. 把已经放好转出内容的hugo site 部署到GitHub上。

每步之间几乎是相互独立，互不影响。每个步骤都可以单独完成，如果想把wordpress
转hexo或者Jekyll，或者要把hugo静态网页托管在GitHub上，都可以参考此篇文章。

### **下面开始正文：**

1. 在本地建立一个hugo site，参见上篇博客（基于hugo的静态博客建立及部署在GitHub上）
2. 这一步是花费了我最长时间的一部，因为有两个wordpress转出工具——wordpress-to-hugo-exporter和Exitwp，两个我都有尝试，但是中间都遇到了一些问题，最终我用Exitwp解决了wordpress转出问题，下面就是详细过程.       
    
	2.1. 导出word press文件：需要在wordpress/admin界面Tools-Export中把自己本来wordpress里的所有内容导出为xml文件。    
    
	2.2. 我们用[Exitwp](https://github.com/thomasf/exitwp)这个工具把xml文件转为markdown文件。下载[Exitwp](https://github.com/thomasf/exitwp.git)，然后把所有的xml文件都放在解压了的Exitwp文件夹里的word press-xml目录下；    
    
	2.3. 进行下部之前，我们需要安装五个software，分别是    
    * [python 2.7](https://www.python.org/)，记得安装完之后要在环境变量-path中添加python，只有添加path之后才可以在cmd中运行python命令，否则后面几步运行会报错；
    * [html2text](http://www.aaronsw.com/2002/html2text/): 把html文件转为markdown文件（python编写）。参照指示，点击download之后直接把code拷贝下来建在一个新txt文档里并命名为html2text.py就行，这里是我建好的.py文件；    
    * [PyYAML](http://pyyaml.org/wiki/PyYAML)：Reading configuration files and writing YAML headers（python编写）（这里是英文解释，有点难翻译，也不太懂什么意思）。下载安装包，然后直接在命令符中输入     
	    
		```
	    python setup.py install
	    ```
    * [beautiful soup](https://www.crummy.com/software/BeautifulSoup/)：运行和下载wordpress posts 中的图片（也是python编写），下载4.6.0版本，然后在cmd中输入    
		```
		pip install beautifulsoup4
		```
	运行，然后beautifulsoup4.6.0就安装在python27\lib\site-packages目录下了；
	* [xmllint](http://xmlsoft.org/downloads.html)：xmllint是一个处理及验证xml的工。Linux下只要安装libxml2就可以使用了，但是在Windows下就要麻烦很多。这一步也是很烦人的一部，因为官网上的指示一点都不清楚，可能针对linux系统比较详细吧，反正Windows系统非常不详细。所以我搜了很久才找到正确安装方法（可以参考[这篇文章](http://flowingmotion.jojordan.org/2011/10/08/3-steps-to-download-xmllint/)来安装xmllint.
	首先找到[xmllint windows下载包](http://xmlsoft.org/sources/win32/)，下载同一版本的libxml2，libxslt，iconv，zlib这四个zipfiles，解压，然后打开这四个文件bin目录，把四个bin文件里的东西全部复制到一个新的命名为bin的文件夹里，这个新的bin文件夹放在C盘下，然后将这个bin添加进环境变量path中。这样，xmllint就算是安装好了。    
    
	2.4.在安装好了所有上述东西之后，在cmd中就最终可以输入$ xmllint ...xml 命令了。我的xml文件是yiyuanli.wordpress.2017-10-04.xml,所以我就直接输入$ xmllint yiyuanli.wordpress.2017-10-04.xml,然后回车运行，（可能会提示有一些错误或者转化不完整，没关系，到时候可以在已经转好的markdown文件中修改），然后在exitwp/build/jekyll中就可以找到转出来的markdown文件们了，终于大功告成！xml文件成功转为markdown！
    
	2.5. 把转好的markdown文件复制到本地hugo site中的content目录下，然后在cmd中hugo site目录下运行 $ hugo server --theme=hugo-theme-crisp，然后网页输入localhost：1313就可以看到以前word press的post已经都移到hugo site中啦~~~
3. 在cmd中hugo site目录下运行
    ```
	hugo –-theme=hugo-theme-crisp –-baseUrl=“http://yiyuanli.github.io/site”
	```
然后将生成的public目录下的所有文件都复制到GitHub的新建的repository master 分支下就可以啦，如果想在cmd中直接用git命令也可以，不过如果你都会用git命令，那一定可以成功将public中的所有文件上传repository中。我用的是特别蠢的办法，适用大白小白非程序猿们，直接把public中的文件拖到master分支中，就完成啦，就可以在自己的github网页上看到生成的静态网页啦！（注意，不是需要把hugo stie下的所有文件都push到github repository中去，只要有public文件夹下的内容就足够了，不过可以新建另外一个repository储存其他文件夹，毕竟**存档**是很重要的一件事，不然后面哪里出了小错有可能就要把前面**所有步骤都重新来一遍了!!!**	   
	       
