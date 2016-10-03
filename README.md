#Description
##DOL 框架描述
&#160; &#160; &#160; &#160;分布式操作层（DOL）是一个程序的并行应用软件开发框架。DOL提供了基于XML规范的格式来描述一个多处理器系统上的并行应用程序的实现，包括结合和映射。基本上由三个部分构成： <br />
1.DOL 应用程序接口：<br />&#160; &#160; &#160; &#160;DOL定义了一组计算和通信的程序，启用分布式、并行应用程序的形状平台的编程。使用这些程序，应用程序程序员可以不必对底层的架构有详细的了解就编写程序。 <br />
2.DOL 功能仿真：<br />&#160; &#160; &#160; &#160;为了给程序员提供测试他们的应用程序的可能性，开发了一个功能仿真框架。除了应用程序的功能验证，该框架还用来获得应用程序级的性能参数。 <br />
3.DOL 映射优化：<br />&#160; &#160; &#160; &#160;DOL映射优化的目标是计算一组应用程序的最佳映射到图形架构平台。<br />

![Distributed Operation Layer](http://i.imgur.com/TLhE6BF.png)

#How to install
##DOL 安装笔记
###在虚拟机中打开terminal，输入以下指令：
#####1.安装一些必要的环境(我的操作系统是ubuntu）

    $  sudo apt-get update
	$  sudo apt-get install ant
	$  sudo apt-get installopenjdk-7-jdk
	$  sudo apt-get install unzip

#####2.直接用命令行下载文件到虚拟机中
 
	$  sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
	$  sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip

#####3.解压文件

	$  mkdir dol                       //新建dol的文件夹
	$  unzipdol_ethz.zip -d dol        //将dolethz.zip解压到 dol文件夹中
	$  tar -zxvf systemc-2.3.1.tgz     //解压systemc

#####4.编译systemc

	$  cdsystemc-2.3.1                //解压后进入systemc-2.3.1的目录下
	$  mkdir objdir                   //新建一个临时文件夹objdir
	$  cdobjdir                       //进入该文件夹objdir
	$  ../configure CXX=g++--disable-async-updates    //运行configure

由于没有装好gcc,出现以下错误

	checking build system type... i686-pc-Linux-gnu
	checking host system type... i686-pc-linux-gnu
	checking for gcc... gcc
	checking for C compiler default output file name...
	configure: error: C compiler cannot create executables
	See `config.log' for more details.

后来用<code>sudo apt-get install build-essential</code>又一直装不上，卡在一个地方然后失败，到晚上的时候用了<code>sudo apt-get install build-essential</code>就好了，应该是网络不好的原因，上午装不好。
运行<code>configure</code>之后的截图如下 

![OF0IXx6](http://i.imgur.com/OF0IXx6.png)


编译
<pre>$ sudo make install</pre>
编译完后文件目录如下
<pre>$ cd .. </pre>       
<pre>$ ls</pre>

![bzjFMxG](http://i.imgur.com/bzjFMxG.png)

记录当前的工作路径
<br />
![SBcOoDw](http://i.imgur.com/SBcOoDw.png)

这里表示我当前的工作路径为/home/lwx/systemc-2.3.1<br />
#####5.编译dol
进入刚刚dol的文件夹
<pre>$ cd ../dol</pre>
修改build_zip.xml文件<br />
&#160; &#160; &#160; &#160;property name="systemc.inc" value="YYY/include"<br />
&#160; &#160; &#160; &#160;property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/<br />
把YYY改成上页pwd的结果,即改为<br />
&#160; &#160; &#160; &#160;property name="systemc.inc" value="/home/lwx/systemc-2.3.1/include"<br />
&#160; &#160; &#160; &#160;property name="systemc.lib" value="/home/lwx/systemc-2.3.1/lib-linux/libsystemc.a"/<br />

然后是编译
<pre>$ ant -f build_zip.xml all</pre>
若成功会显示build successful

![oRWw8he](http://i.imgur.com/oRWw8he.png)

接着可以试试运行第一个例子
进入build/bin/mian路径下
<pre>$ cd build/bin/main</pre>
然后运行第一个例子
<pre>$ ant -f runexample.xml -Dnumber=1</pre>

成功结果如图

![WZH0VOS](http://i.imgur.com/WZH0VOS.png)
#Experimental experience
##实验感想、实验心得
&#160; &#160; &#160; &#160;上次的DOL配置只要跟着实验文档就能比较顺利地完成，主要是在于理解以及体会过程，整个过程算是比较顺利的，除了在运行运行configure的时候除了点问题，然后在版本控制实验安装 Git的时候一直出错，后来才发现是ubuntu没有连到网，然后一直连不上才想起我360关了vmware的一些功能（好气哦），最波折的就是用Markdown写实验文档了。Markdown语法并不复杂，很快就能上手，但比较麻烦，特别在添加图片的时候，我开始用Droplr来上传图片获取 URL 地址，然后不知道是怎么回事，没有图片标题也没有图片生成，就一个框框,然后我搜索网址：[Cloud](http://d.pr/i/M054)发现不能访问，就改了用百度网盘生成URL，可还是一样的效果，不过网址搜索是可以的。然后就想到可能是这个软件一些网站的同步效果不是很好，这里显示不出来吧，Git应该就可以了，后来用了Droplr生成图片网址：[Droplr](https://drops.azureedge.net/drops/previews/M054.preview_small.png?rscd=&rsct=binary&se=2016-10-03T02%3A55%3A30Z&sig=FKrSVAzPqNnjEgaOQbEPinPgkf2KASqFtY8sscB4qjI%3D&sp=r&sr=b&st=2016-10-03T01%3A55%3A30Z&sv=2013-08-15),在markdown上预览有图了，但传到Git后打不开，后来才发现我的markdown编辑器自带图片转网址功能，注册码网上很多，在工具栏点Image就可以生成了。


