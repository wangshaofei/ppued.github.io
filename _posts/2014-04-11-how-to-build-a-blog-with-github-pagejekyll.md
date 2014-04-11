---
layout: post
title: "how to build a blog with github page&jekyll"
description: ""
category: 
tags: []
---
{% include JB/setup %}
# �����github pages��jekyll�����


���������⼸��ʹ��github��jekyll������͵ļ�¼���ĵ�,���ݱȽϻ�������������·�����в���Ҳ���æָ����

github��Ŀǰ���ܻ�ӭ�ķֲ�ʽ�汾����ϵͳ��jekyll�ǻ���liquidģ�������markdown����textile����Ϊ����������ԣ��ľ�̬��վ������,ʹ��github��jekyll������������ص�:

1. ����github�İ汾�������
2. ��ѣ���������
3. �Զ�������
4. ����̬��վ���ʺϼ���վ
	
##һ.github pages

github��һ�����linuxƽ̨�ķֲ�ʽϵͳ��ͬʱҲΪwindow��mac�û��ṩ����Ӧ�Ŀͻ���:

1. [github windows(ͼ�ν���)](http://windows.github.com/)
2. [github mac](http://mac.github.com/)
3. [Git for Windows (Git Bash)](http://msysgit.github.com/)

github���ṩ�ļ��йܷ���ģ�ֻ�ܿ����ļ�Դ�롣Ϊ�ˣ�github�����[github pages](https://pages.github.com/)���ܣ��������û�����ҳ��ʽ����ļ���github pages�ṩ����ҳģ�壬����ֱ��������ҳ��ͬʱҲ�������û��ȱ�д����ҳ���ϴ���github pages����֧��jekyll��Ҳ����ֱ���ϴ�����jekyll�淶���ļ���
	
### 1.����������ҳ
	
github Ϊÿһ���û�������һ����������usename.github.io��������github.io,github.com����֧���ˣ���������ʽ����:

1.��github�ϴ�������Ϊusername.github.io�İ汾��(ע��username��Ҫ�滻�����github�˺�����)��

![�����汾��](/assets/image/HowToCreateNewRepo.jpg)

2.���ð汾���¡�����ء�

	git clone https://github.com/username/username.github.io
	
3.�л���username.github.io,���ҽ����ļ�

	cd git username.github.io
	echo "Hello World!" > index.html
	
4.�ύ���ļ�
	
	git add .
	git commit -m "create home page!"

5.���͵�github

	git push

������֮�󣬷���http://username.github.io�Ϳ��Կ�����ҳ�ˡ�
		
### 2.������Ŀ��ҳ
github���ṩ������ҳ�����⣬������Ϊÿһ����Ŀ�ṩ��ҳ���ʹ��ܡ�������Ŀ��ҳ���ܼܺ򵥣�ֻ��ҪΪÿһ����Ŀ����һ������Ϊgh-pages�ķ�֧������������Ӿ�̬��ҳ���ɡ����һ����Ŀ������Ϊgh-pages��֧�Ļ������������Ŀ�ṩ�˾�̬��ҳ������ͨ����ַhttp://username.github.io/projectname/���ʵ���

������Ŀ��ҳ��ʽ����:

1.����Ŀ�Ҳ�ѡ��settings����
![������Ŀ��ҳ](/assets/image/HowToCreateProjectPage1.jpg)
	
2.ѡ��Automatic page generator��
![������Ŀ��ҳ](/assets/image/HowToCreateProjectPage2.jpg)

3.�༭��ҳ���ݣ�ѡ�����⣬��������

������֮�󣬷���http://username.github.io/projectname/�Ϳ��Կ�����Ŀ��ҳ�ˡ�

[Automatic page generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator)��github�ṩ��һ���򵥿�ݵ���ҳ�������������Կ������ɸ�����ҳ������Ŀ��ҳ�������ṩ�������⹩�û�ѡ���û�ֻ��Ҫ��ע���ݼ��ɡ����ݵĲ���[markdown](https://help.github.com/articles/github-flavored-markdown)����д��

### 3.�Զ�������
����ʹ��github.io�Ķ������������ʸ�����ҳ����Ŀ��ҳ�⣬������ʹ���Զ������������ʡ���������:
1.��username.github.io�汾�����½�����ΪCNAME���ı��ļ�������չ����,����Ϊ����

	echo "www.example.com" > CNAME
	
2.�����ļ��ύ��Զ�̰汾��

	git add CNAME
	git commit -m "create custom domain!"
	git push

3.�������ṩ�������޸��������ָ��ʹ��ָ��204.232.175.78

��������(�����������Чʱ�����)������ www.example.com���ԣ��Ϳ��Կ�����ҳ�ˡ�
		
		
##��.ʹ��jekyll
		
jekyll����github������֮һ��Tom Preston-Werner�����ľ�̬��վ��������֧��textile��markdown������������ԡ�jekyllʹ��rubyʵ�֣���Ҫ��װruby��gem��

### 1.ruby�İ�װ
������Ҫ���ز���װruby����װ��ַ��[����](https://www.ruby-lang.org/zh_cn/downloads/ "ruby��װ��ַ")��windowϵͳ����ֱ����RubyInstaller���汾Խ��Խ�ã��Ͱ汾������Ī����������⡣�������ֱ�Ӱ�װ���ɡ�ruby��װ��֮�󣬻��ṩCMD���ߡ������İ�װ����Ҫ������������С�

window�£�����Ҫ��װ[Development Kit]("https://github.com/oneclick/rubyinstaller/wiki/Development-Kit#quick-start" "Ruby Development Kit"),����RubyΪ����ʹ��C/C++��չ��һ�����ߡ����ص�ַ��[����](http://rubyinstaller.org/downloads/ "download Development Kit")���� [����](https://github.com/oneclick/rubyinstaller/downloads/ "download Development Kit")��������������²��谲װ:

1.��ȡ�ļ������ļ�����ȡ��һ��Ŀ¼�����磺 

	c://rubyDevKit
	
2.���а�װ�ű���

	cd c://rubyDevKit  //�ղŵ�Ŀ¼
	ruby dk.rb init    //���������ļ�
	ruby dk.rb install  //��װ
3.���԰����Ƿ�������

	ruby -rubygems -e "require 'json'; puts JSON.load('[42]').inspect"
   
���������Ļ���ruby�İ�װ������ɡ�

###2.jekyll�İ�װ

��ruby��CMD�����У�������������:

	gem install jekyll

���Զ���װ����jekyll�������Դ����װ��

��һЩʹ�ô���Ĺ�˾��������Ҫ��CMDʹ�ô����������ʹ����������,��������:

	set http_proxy=http://proxy.yourname.com:8080
	
���У�http://proxy.yourname.com�Ǵ���������ĵ�ַ��8080�Ƕ˿ںţ��������á�

###3.jekyll�Ľṹ
jekyll�ӱ�������˵��һ���ı�ת�����棬��ϵͳ�ڲ��Ĺ���ԭ���ǣ�������һЩ���Լ�ϲ���ı�����Ը�ʽ��д���ı���������Markdown��Textile�򴿴��HTML��������Щ�ı���Ϻ����һ����һ����ҳ�沼�ֵ��С������������У���������о������վ��URL��ģʽ���Լ���Щ���ݽ�����ʾ��ҳ���У��ȵȡ���һ�ж���ͨ���ϸ���ı��༭��ɣ������ɵ�Web�����������յĲ�Ʒ��

jekyll��װ���֮�󣬿���ʹ�����������ʼ��Ŀ¼:

	jekyll new blog  //����blogΪ���Ŀ¼����

��ʼ��֮�󣬻������Ŀ¼������һ�»�����Ŀ¼���ļ���jekyll�Ļ���Ŀ¼�ṹ����:

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
��վ�������ļ�
	
####_includes
����ɸ��õĹ���ģ�飬��header,footer��ʹ�÷�ʽΪ:{ % include footer.html % }

####_layouts
��վ��ģ�壬ʹ��HTML�﷨����д�����Ұ���[YAML Front Matter](http://jekyllcn.com/docs/frontmatter/)��ģ��ʹ��[liquid](http://liquidmarkup.org/)���棬֧��site,page,content����ȫ�ֱ�����

####_posts              
����Ҫ���������£��ļ�����������YEAR-MONTH-DATE-title.MARKUP����2014-04-09-ABC to HTML.md������title���ֲ��������ġ��ļ����ݲ���markdown����textile����д�����Ұ���[YAML Front Matter](http://jekyllcn.com/docs/frontmatter/)��֧��liquid�﷨(����ʹ��site,page��ȫ�ֱ���)������ֱ��ʹ��html����д��

####_site
����jekyll������ļ�����������Ŀ¼�У����Ŀ¼�������յ�webҳ�档


###jekyllģ��ȫ�ֱ���
jekyll����liquidģ������,�﷨��[����](http://liquidmarkup.org/),����ֱ����_layout�е�ģ���_post�е�������ʹ��site,page,content��ȫ�ֱ�����

####ȫ�ֱ���
<table><thead><tr><th style="text-align: left"><strong>����</strong></th><th style="text-align: left"><strong>����</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>site</code></td><td style="text-align: left">ȫվ����Ϣ+<code>_config.yml</code>�ļ��е�����ѡ��</td></tr><tr><td style="text-align: left"><code>page</code></td><td style="text-align: left">��������а���YAMLǰ������,���������������ı���ֵ:<code>url</code>��<code>content</code>��</td></tr><tr><td style="text-align: left"><code>content</code></td><td style="text-align: left">�ڲ���ģ���ļ��У��������������ҳ�������ͼ����������������Ⱦ������ݲ��뵽ģ���ļ��С�����������������º�ҳ���ļ���ʹ�á�</td></tr><tr><td style="text-align: left"><code>paginator</code></td><td style="text-align: left">һ��<code>paginate</code>����ѡ������ˣ�����������ܱ�ʹ�á�</td></tr></tbody></table>

####site����
<table><thead><tr><th style="text-align: left"><strong>����</strong></th><th style="text-align: left"><strong>����</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>site.time</code></td><td style="text-align: left">��ǰ��ʱ��(��������Jekyllʱ��ʱ��)</td></tr><tr><td style="text-align: left"><code>site.posts</code></td><td style="text-align: left">һ����ʱ������������б�</td></tr><tr><td style="text-align: left"><code>site.related_posts</code></td><td style="text-align: left">�����ǰ�������ҳ����һ�������ļ��������������һ�����������10ƪ������µ��б�Ĭ����˵����Щ��������ǵ������������ġ�Ϊ�˵õ����������������Ľ��������Jekyll����ʱ���Լ���<code>--lsi</code>ѡ�(Ǳ����������)</td></tr><tr><td style="text-align: left"><code>site.categories.CATEGORY</code></td><td style="text-align: left">������<code>CATEGORY</code>�����е������б�</td></tr><tr><td style="text-align: left"><code>site.tags.TAG</code></td><td style="text-align: left">����ӵ��<code>TAG</code>��ǩ�����µ��б�</td></tr><tr><td style="text-align: left"><code>site.[CONFIGURATION_DATA]</code></td><td style="text-align: left">��ֹ<strong>0.5.2</strong>�汾��������<code>_config.yml</code>�е����ݶ��ܹ�ͨ��<code>site</code>�������á�������˵���������һ��������ѡ������������ļ���:<code>url: http://higrid.net</code>���������º�ҳ���ļ��п�����������<code>{ { site.url } }</code>��Jekyll�������Զ������޸Ĺ���<code>_config.yml</code>�ļ�������Ҫ�����µ�����ѡ�����Ҫ����Jekyll</td></tr></tbody></table>

####page����
<table><thead><tr><th style="text-align: left"><strong>����</strong></th><th style="text-align: left"><strong>����</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>page.content</code></td><td style="text-align: left">ҳ����δ��Ⱦ������</td></tr><tr><td style="text-align: left"><code>page.title</code></td><td style="text-align: left">���µı���</td></tr><tr><td style="text-align: left"><code>page.url</code></td><td style="text-align: left">��ȥ���������URL������:<code>/2013/12/14/higrid-net.html</code></td></tr><tr><td style="text-align: left"><code>page.date</code></td><td style="text-align: left">ָ��ÿһƪ���µ�ʱ�䣬���ѡ���ܹ�����һƪ������ǰ���������õ�ʱ�䣬���ĸ�ʽ��������:<code>YYYY-MM-DD HH:MM:SS</code></td></tr><tr><td style="text-align: left"><code>page.id</code></td><td style="text-align: left">ÿһƪ���µ�Ψһ��ʾ��(��RSS�зǳ�����) ���ӣ�/2008/12/14/higrid-net</td></tr><tr><td style="text-align: left"><code>page.categories</code></td><td style="text-align: left">��ƪ���������ķ����һ���б�������ͨ����<code>_post</code>Ŀ¼�е�Ŀ¼�ṹ�Ƶ������ġ�������˵����·��<code>/work/code/_posts/2008-12-24-closures.textile</code>�µ��ļ����������������<code>[work,code]</code>���������Ҳ����YAMLǰ�������б�ָ����</td></tr><tr><td style="text-align: left"><code>page.tags</code></td><td style="text-align: left">��ƪ���µı�ǩ���б���Щ�����ܹ���YAMLǰ��������ָ��</td></tr><tr><td style="text-align: left"><code>page.next</code></td><td style="text-align: left">��ʱ�������һƪ����</td></tr><tr><td style="text-align: left"><code>page.content</code></td><td style="text-align: left">��ʱ�������һƪ����</td></tr></tbody></table>

####paginator����
<table><thead><tr><th style="text-align: left"><strong>����</strong></th><th style="text-align: left"><strong>����</strong></th></tr></thead><tbody><tr><td style="text-align: left"><code>paginator.per_page</code></td><td style="text-align: left">ÿһ��ҳ�������µ�����</td></tr><tr><td style="text-align: left"><code>paginator.posts</code></td><td style="text-align: left">��ǰҳ���Ͽ��õ�����</td></tr><tr><td style="text-align: left"><code>paginator.total_posts</code></td><td style="text-align: left">�������µ�����</td></tr><tr><td style="text-align: left"><code>paginator.total_pages</code></td><td style="text-align: left">����ҳ�������</td></tr><tr><td style="text-align: left"><code>paginator.page</code></td><td style="text-align: left">��ǰҳ�������</td></tr><tr><td style="text-align: left"><code>paginator.previous_page</code></td><td style="text-align: left">ǰ���ҳ�������</td></tr><tr><td style="text-align: left"><code>paginator.next_page</code></td><td style="text-align: left">�������ĵ�ҳ�������</td></tr></tbody></table>

###4.YAML�ļ�ͷ
�κ�ֻҪ���� YAML ͷ��Ϣ���ļ��� Jekyll �ж��ܱ�����һ��������ļ�������ͷ��Ϣ�������ļ��Ŀ�ʼ���֣�������Ҫ���� YAML �ĸ�ʽд������������֮�䣬��ʽ����:

	---
	layout: post
	title: Blogging Like a Hacker
	---

�������е�������֮�䣬���������һЩԤ������������Զ������������layout��ʾ������ʹ�õ�ģ�壬title��ʾ���µı��⡣���⻹�����µ�Ԥ���������

+ permalink ����Զ�ĳһƪ����ʹ��ͨ������֮�����������
+ published ���Ե�������ĳһƪ�����Ƿ���Ҫ����
+ category �������µķ���
+ tags �������µ�tag

�����YAML�ļ�ͷ��Ϣ��[����](http://jekyllcn.com/docs/frontmatter/)

###5.��������
�������ݿ���ʹ��markdown����textile����д������ֱ��ʹ��html��д��
������markdownΪ�����н��ܡ�

####1.����

������#��ͷ
	
	# ����1
	## ����2
	###### ����6
	
####2.���� 

����ǰ������һ�����ϵĿ��С�
	
####3.����

�����ֵ�ĩβʹ���������������ϵĿո�����ʾ���С�
	
####4.�б�
	
�����б�ʹ��*��+��-������Ͽո�����ʾ��
	
	* Item 1
	* Item 2
	* Item 3

	+ Item 1
	+ Item 2
	+ Item 3

	- Item 1
	- Item 2
	- Item 3
	
�����б�ʹ�����ּ�Ӣ�ľ�żӿո��ʾ��
	
	1. Item 1
	2. Item 2
	3. Item 3
	
####5.��������

���ڴ���ʹ�÷�����`��ʾ��
�������������ÿ������ǰ��4���ո����1����������ʾ��

	$ echo 'Something'
    $ echo -e '\tSomething\n'
	
####6.б��ͼӴ�

markdownʹ��*��_��ʾǿ����

	���Ǻ� = *б��*
	���»��� = _б��_
	˫�Ǻ� = **�Ӵ�**
	˫�»��� = __�Ӵ�__
	
####7.����
	
markdown֧�����ַ������ӣ�Inline��Reference��

Inline���������ű����ʾ�������ı������������С���Ű�Χ�����ӡ����������title���ԣ�����������ʹ�ÿո��"title����"��  
		
Reference��һ��Ӧ���ڶ����ͬλ��ʹ����ͬ���ӡ�ͨ����Ϊ�������֣����ò���Ϊ[�����ı�][ref]�����岿�ֿ��Գ������ı��е�����λ�ã���ʽΪ[ref]: http://some/link/address (��ѡ�ı���)��

	����һ��Inline[ʾ��](http://equation85.github.com "��ѡ��title")��
	����һ��Reference[ʾ��][ref]��
	[ref]: http://equation85.github.com
	
####8.ͼƬ
ͼƬ��ʹ�÷��������Ϻ��������ƣ�ֻ����������ǰ��̾�š�Markdown��������ͼƬ��С���������������Ӧʹ��HTML���<img>��

	Inlineʾ����![����ı�](/images/01.jpg "��ѡ��title")
	Referenceʾ����![����ı�][pic]
	[pic]: images/01.jpg "��ѡ��title"
	HTMLʾ����<img src="images/01.jpg" alt="����ı�" title="�����ı�" width="200" />
	
####9.ת��
�ѷ�б��\���������ַ�ǰ�棬�Ϳ��Խ���ת���ˡ�

������ǳ������﷨��������﷨��[����](http://wowubuntu.com/markdown/)��

###6.jekyll�ĵ��ԺͲ���

jekyll������һ������server�������ڱ��ص��ԣ����������֮�����ϴ�������֮ǰ����Ҫ����web �ļ���

	jekyll build  //��ǰ�ļ���������±����ɵ�_site/Ŀ¼
	jekyll build -source <source> -destination <destination>   //source�ļ���������±����ɵ�destinationĿ¼
	
webҳ������֮����������web server����Ԥ����

	jekyll serve
	
Ȼ�����http://localhost:4000 Ԥ�����ҳ�档

Ȼ��ҳ��push��github�ϣ��Ͷ�����ˡ�

	git add . 
	git commit -m "a new page"
	git push
	
	
##����
github page��Ȼ֧��jekyll,ǰ�߸����𣬺��߸������ݣ������Ǵ�������͵ĺô��

