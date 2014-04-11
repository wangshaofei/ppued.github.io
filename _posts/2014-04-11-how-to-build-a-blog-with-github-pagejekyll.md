---
layout: post
title: "how to build a blog with github page&jekyll"
description: ""
category: 
tags: []
---
{% include JB/setup %}
# 如何用github pages和jekyll搭建博客


本文是我这几天使用github和jekyll搭建本博客的记录和心得,内容比较基础，高手请绕路，如有不对也请帮忙指正。

github是目前最受欢迎的分布式版本管理系统，jekyll是基于liquid模板引擎和markdown或者textile（均为轻量标记语言）的静态网站生成器,使用github和jekyll搭建博客有以下特点:

1. 享受github的版本管理便利
2. 免费，无限流量
3. 自定义域名
4. 纯静态网站，适合简单网站
	
##一.github pages

github是一个针对linux平台的分布式系统，同时也为window和mac用户提供了相应的客户端:

1. [github windows(图形界面)](http://windows.github.com/)
2. [github mac](http://mac.github.com/)
3. [Git for Windows (Git Bash)](http://msysgit.github.com/)

github是提供文件托管服务的，只能看到文件源码。为此，github设计了[github pages](https://pages.github.com/)功能，他能让用户以网页形式浏览文件。github pages提供了网页模板，允许直接生成网页，同时也可以让用户先编写好网页再上传。github pages内置支持jekyll，也可以直接上传符合jekyll规范的文件。
	
### 1.创建个人主页
	
github 为每一个用户分配了一个二级域名usename.github.io（必须是github.io,github.com不再支持了）。创建方式如下:

1.在github上创建名字为username.github.io的版本库(注意username需要替换成你的github账号名字)。

![创建版本库](/assets/image/HowToCreateNewRepo.jpg)

2.将该版本库克隆到本地。

	git clone https://github.com/username/username.github.io
	
3.切换到username.github.io,并且建新文件

	cd git username.github.io
	echo "Hello World!" > index.html
	
4.提交新文件
	
	git add .
	git commit -m "create home page!"

5.推送到github

	git push

几分钟之后，访问http://username.github.io就可以看到主页了。
		
### 2.创建项目主页
github除提供个人主页功能外，还可以为每一个项目提供主页访问功能。启用项目主页功能很简单，只需要为每一个项目创建一个名字为gh-pages的分支，并向其中添加静态网页即可。如果一个项目存在名为gh-pages分支的话，则表明该项目提供了静态网页，可以通过网址http://username.github.io/projectname/访问到。

创建项目主页方式如下:

1.在项目右侧选择“settings”，
![创建项目主页](/assets/image/HowToCreateProjectPage1.jpg)
	
2.选择“Automatic page generator”
![创建项目主页](/assets/image/HowToCreateProjectPage2.jpg)

3.编辑主页内容，选择主题，发布即可

几分钟之后，访问http://username.github.io/projectname/就可以看到项目主页了。

[Automatic page generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator)是github提供的一个简单快捷的网页生成器，他可以快速生成个人主页或者项目主页，并且提供几套主题供用户选择。用户只需要关注内容即可。内容的采用[markdown](https://help.github.com/articles/github-flavored-markdown)来编写。

### 3.自定义域名
除了使用github.io的二级域名来访问个人主页和项目主页外，还可以使用自定义域名来访问。方法如下:
1.在username.github.io版本库下新建名字为CNAME的文本文件（无扩展名）,内容为域名

	echo "www.example.com" > CNAME
	
2.将此文件提交到远程版本库

	git add CNAME
	git commit -m "create custom domain!"
	git push

3.在域名提供商那里修改你的域名指向，使其指向204.232.175.78

过几分钟(视你的域名生效时间而定)，访问 www.example.com试试，就可以看到主页了。
		
		
##二.使用jekyll
		
jekyll是由github创世人之一的Tom Preston-Werner开发的静态网站生成器，支持textile、markdown等轻量标记语言。jekyll使用ruby实现，需要安装ruby和gem。

### 1.ruby的安装
首先需要下载并安装ruby，安装地址见[这里](https://www.ruby-lang.org/zh_cn/downloads/ "ruby安装地址")。window系统建议直接用RubyInstaller，版本越高越好，低版本会碰到莫名其妙的问题。下载完后直接安装即可。ruby安装完之后，会提供CMD工具。后续的安装都需要在这个工具运行。

window下，还需要安装[Development Kit]("https://github.com/oneclick/rubyinstaller/wiki/Development-Kit#quick-start" "Ruby Development Kit"),他是Ruby为方便使用C/C++扩展的一个工具。下载地址见[这里](http://rubyinstaller.org/downloads/ "download Development Kit")或者 [这里](https://github.com/oneclick/rubyinstaller/downloads/ "download Development Kit")。下载完后按照以下步骤安装:

1.提取文件。将文件夹提取到一个目录，比如： 

	c://rubyDevKit
	
2.运行安装脚本。

	cd c://rubyDevKit  //刚才的目录
	ruby dk.rb init    //生成配置文件
	ruby dk.rb install  //安装
3.测试按照是否正常。

	ruby -rubygems -e "require 'json'; puts JSON.load('[42]').inspect"
   
测试正常的话，ruby的安装算是完成。

###2.jekyll的安装

在ruby的CMD工具中，运行如下命令:

	gem install jekyll

会自动安装下载jekyll及相关资源并安装。

在一些使用代理的公司内网，需要给CMD使用代理才能正常使用网络下载,命令如下:

	set http_proxy=http://proxy.yourname.com:8080
	
其中，http://proxy.yourname.com是代理服务器的地址，8080是端口号，有则设置。

###3.jekyll的结构
jekyll从本质上来说是一个文本转换引擎，该系统内部的工作原理是：你输入一些用自己喜爱的标记语言格式书写的文本，可以是Markdown、Textile或纯粹的HTML，它将这些文本混合后放入一个或一整套页面布局当中。在整个过程中，你可以自行决定你的站点URL的模式、以及哪些数据将被显示在页面中，等等。这一切都将通过严格的文本编辑完成，而生成的Web界面则是最终的产品。

jekyll安装完成之后，可以使用以下命令初始化目录:

	jekyll new blog  //其中blog为你的目录名称

初始化之后，会在你的目录下生成一下基本的目录和文件。jekyll的基本目录结构如下:

	|-- _config.yml
	|-- _includes
	|-- _layouts
	|   |-- default.html
	|   `-- post.html
	|-- _posts
	|   |-- 2007-10-29-why-every-programmer-should-play-nethack.textile
	|   `-- 2009-04-26-barcamp-boston-4-roundup.textile
	|-- _site
	-- index.html

####_config.yml
网站的配置文件
	
####_includes
保存可复用的公共模块，如header,footer。使用方式为:{ % include footer.html % }

####_layouts
网站的模板，使用HTML语法来编写，并且包含[YAML Front Matter](http://jekyllcn.com/docs/frontmatter/)。模板使用[liquid](http://liquidmarkup.org/)引擎，支持site,page,content三个全局变量。

####_posts              
作者要发布的文章，文件命名规则是YEAR-MONTH-DATE-title.MARKUP，如2014-04-09-ABC to HTML.md，其中title部分不能是中文。文件内容采用markdown或者textile来编写，并且包含[YAML Front Matter](http://jekyllcn.com/docs/frontmatter/)，支持liquid语法(可以使用site,page等全局变量)，或者直接使用html来编写。

####_site
经过jekyll处理的文件都会放在这个目录中，这个目录包含最终的web页面。


###jekyll模板全局变量
jekyll采用liquid模板引擎,语法见[这里](http://liquidmarkup.org/),可以直接在_layout中的模板和_post中的文章中使用site,page,content等全局变量。

####全局变量
<table><thead><tr><th style="text-align: left"><strong>变量</strong></th><th style="text-align: left"><strong>描述</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>site</code></td><td style="text-align: left">全站的信息+<code>_config.yml</code>文件中的配置选项</td></tr><tr><td style="text-align: left"><code>page</code></td><td style="text-align: left">这个变量中包含YAML前置数据,另外加上两个额外的变量值:<code>url</code>和<code>content</code>。</td></tr><tr><td style="text-align: left"><code>content</code></td><td style="text-align: left">在布局模板文件中，这里变量包含了页面的子视图。这个变量将会把渲染后的内容插入到模板文件中。这个变量不能在文章和页面文件中使用。</td></tr><tr><td style="text-align: left"><code>paginator</code></td><td style="text-align: left">一旦<code>paginate</code>配置选项被设置了，这个变量才能被使用。</td></tr></tbody></table>

####site变量
<table><thead><tr><th style="text-align: left"><strong>变量</strong></th><th style="text-align: left"><strong>描述</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>site.time</code></td><td style="text-align: left">当前的时间(当你运行Jekyll时的时间)</td></tr><tr><td style="text-align: left"><code>site.posts</code></td><td style="text-align: left">一个按时间逆序的文章列表。</td></tr><tr><td style="text-align: left"><code>site.related_posts</code></td><td style="text-align: left">如果当前被处理的页面是一个文章文件，那这个变量是一个包含了最多10篇相关文章的列表。默认来说，这些相关文章是低质量但计算快的。为了得到高质量但计算慢的结果，运行Jekyll命令时可以加上<code>--lsi</code>选项。(潜在语意索引)</td></tr><tr><td style="text-align: left"><code>site.categories.CATEGORY</code></td><td style="text-align: left">所有在<code>CATEGORY</code>分类中的文章列表</td></tr><tr><td style="text-align: left"><code>site.tags.TAG</code></td><td style="text-align: left">所有拥有<code>TAG</code>标签的文章的列表</td></tr><tr><td style="text-align: left"><code>site.[CONFIGURATION_DATA]</code></td><td style="text-align: left">截止<strong>0.5.2</strong>版本，所有在<code>_config.yml</code>中的数据都能够通过<code>site</code>变量调用。举例来说，如果你有一个这样的选项在你的配置文件中:<code>url: http://higrid.net</code>，那在文章和页面文件中可以这样调用<code>{ { site.url } }</code>。Jekyll并不会自动解析修改过的<code>_config.yml</code>文件，你想要启用新的设置选项，你需要重启Jekyll</td></tr></tbody></table>

####page变量
<table><thead><tr><th style="text-align: left"><strong>变量</strong></th><th style="text-align: left"><strong>描述</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>page.content</code></td><td style="text-align: left">页面中未渲染的内容</td></tr><tr><td style="text-align: left"><code>page.title</code></td><td style="text-align: left">文章的标题</td></tr><tr><td style="text-align: left"><code>page.url</code></td><td style="text-align: left">除去域名以外的URL，例子:<code>/2013/12/14/higrid-net.html</code></td></tr><tr><td style="text-align: left"><code>page.date</code></td><td style="text-align: left">指定每一篇文章的时间，这个选项能够覆盖一篇文章中前置数据设置的时间，它的格式是这样的:<code>YYYY-MM-DD HH:MM:SS</code></td></tr><tr><td style="text-align: left"><code>page.id</code></td><td style="text-align: left">每一篇文章的唯一标示符(在RSS中非常有用) 例子：/2008/12/14/higrid-net</td></tr><tr><td style="text-align: left"><code>page.categories</code></td><td style="text-align: left">这篇文章隶属的分类的一个列表，分类是通过在<code>_post</code>目录中的目录结构推导而来的。举例来说，在路径<code>/work/code/_posts/2008-12-24-closures.textile</code>下的文件，这个变量将会是<code>[work,code]</code>。这个变量也能在YAML前置数据中被指定。</td></tr><tr><td style="text-align: left"><code>page.tags</code></td><td style="text-align: left">这篇文章的标签的列表。这些数据能够在YAML前置数据中指定</td></tr><tr><td style="text-align: left"><code>page.next</code></td><td style="text-align: left">按时间序的下一篇文章</td></tr><tr><td style="text-align: left"><code>page.content</code></td><td style="text-align: left">按时间序的上一篇文章</td></tr></tbody></table>

####paginator变量
<table><thead><tr><th style="text-align: left"><strong>变量</strong></th><th style="text-align: left"><strong>描述</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>paginator.per_page</code></td><td style="text-align: left">每一个页面上文章的数量</td></tr><tr><td style="text-align: left"><code>paginator.posts</code></td><td style="text-align: left">当前页面上可用的文章</td></tr><tr><td style="text-align: left"><code>paginator.total_posts</code></td><td style="text-align: left">所有文章的数量</td></tr><tr><td style="text-align: left"><code>paginator.total_pages</code></td><td style="text-align: left">所有页面的数量</td></tr><tr><td style="text-align: left"><code>paginator.page</code></td><td style="text-align: left">当前页面的数量</td></tr><tr><td style="text-align: left"><code>paginator.previous_page</code></td><td style="text-align: left">前面的页面的数量</td></tr><tr><td style="text-align: left"><code>paginator.next_page</code></td><td style="text-align: left">接下来的的页面的数量</td></tr></tbody></table>

###4.YAML文件头
任何只要包含 YAML 头信息的文件在 Jekyll 中都能被当做一个特殊的文件来处理。头信息必须在文件的开始部分，并且需要按照 YAML 的格式写在两行三虚线之间，格式如下:

	---
	layout: post
	title: Blogging Like a Hacker
	---

在这两行的三虚线之间，你可以设置一些预定义变量或者自定义变量。其中layout表示文章所使用的模板，title表示文章的标题。另外还有如下的预定义变量：

+ permalink 你可以对某一篇文章使用通用设置之外的永久链接
+ published 可以单独设置某一篇文章是否需要发布
+ category 设置文章的分类
+ tags 设置文章的tag

更多的YAML文件头信息见[这里](http://jekyllcn.com/docs/frontmatter/)

###5.文章内容
文章内容可以使用markdown或者textile来编写，或者直接使用html编写。
下面以markdown为例进行介绍。

####1.标题

标题以#开头
	
	# 标题1
	## 标题2
	###### 标题6
	
####2.段落 

段落前后需有一个以上的空行。
	
####3.换行

在文字的末尾使用两个或两个以上的空格来表示换行。
	
####4.列表
	
无序列表使用*、+或-后面加上空格来表示。
	
	* Item 1
	* Item 2
	* Item 3

	+ Item 1
	+ Item 2
	+ Item 3

	- Item 1
	- Item 2
	- Item 3
	
有序列表使用数字加英文句号加空格表示。
	
	1. Item 1
	2. Item 2
	3. Item 3
	
####5.代码区域

行内代码使用反引号`表示。
代码段落则是在每行文字前加4个空格或者1个缩进符表示。

	$ echo 'Something'
    $ echo -e '\tSomething\n'
	
####6.斜体和加粗

markdown使用*或_表示强调。

	单星号 = *斜体*
	单下划线 = _斜体_
	双星号 = **加粗**
	双下划线 = __加粗__
	
####7.链接
	
markdown支持两种风格的链接：Inline和Reference。

Inline：以中括号标记显示的链接文本，后面紧跟用小括号包围的链接。如果链接有title属性，则在链接中使用空格加"title属性"。  
		
Reference：一般应用于多个不同位置使用相同链接。通常分为两个部分，调用部分为[链接文本][ref]；定义部分可以出现在文本中的其他位置，格式为[ref]: http://some/link/address (可选的标题)。

	这是一个Inline[示例](http://equation85.github.com "可选的title")。
	这是一个Reference[示例][ref]。
	[ref]: http://equation85.github.com
	
####8.图片
图片的使用方法基本上和链接类似，只是在中括号前加叹号。Markdown不能设置图片大小，如果必须设置则应使用HTML标记<img>。

	Inline示例：![替代文本](/images/01.jpg "可选的title")
	Reference示例：![替代文本][pic]
	[pic]: images/01.jpg "可选的title"
	HTML示例：<img src="images/01.jpg" alt="替代文本" title="标题文本" width="200" />
	
####9.转义
把反斜杠\放在特殊字符前面，就可以进行转义了。

上面的是常见的语法，更多的语法见[这里](http://wowubuntu.com/markdown/)。

###6.jekyll的调试和部署

jekyll内置了一个本地server，可以在本地调试，调试完成了之后再上传。调试之前，先要生产web 文件。

	jekyll build  //当前文件夹里的文章被生成到_site/目录
	jekyll build -source <source> -destination <destination>   //source文件夹里的文章被生成到destination目录
	
web页面生成之后，启动本地web server进行预览。

	jekyll serve
	
然后访问http://localhost:4000 预览你的页面。

然后将页面push到github上，就额可以了。

	git add . 
	git commit -m "a new page"
	git push
	
	
##结语
github page天然支持jekyll,前者负责部署，后者负责内容，二者是搭建轻量博客的好搭档。

