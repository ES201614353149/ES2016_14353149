## 1.修改example1，使其输出3次方数

* 改完的example1 运行结果如下图所示
![](http://i.imgur.com/ufI8eB4.png)
generator 产生0-19的整数（length为20，初始值为0），
square 对输入进行三次方操作，
consumer 输出结果。


* 修改square.c如下图，把平方![公式名](http://latex.codecogs.com/png.latex?i=i*i)改为三次方![公式名](http://latex.codecogs.com/png.latex?i=i*i*i)

![](http://i.imgur.com/cLOtP5R.png)
## 2.修改example2，让3个square模块变成2个

* 改完的example2 运行结果如下图所示
![](http://i.imgur.com/hWXGw43.png)
generator 产生0-19的整数（length为20，初始值为0），
square 对输入进行四次方操作，
consumer 输出结果。


* 修改xml的iterator如下图，把value="3"改为value="2"
![](http://i.imgur.com/wPtep5C.png)
##3.实验感想
　　这次的实验挺简单的，TA上课的时候讲的很详细，实验文档内容也很完整，通过这次实验，分析DOL实例，对Distributed Operation Layer有了更深的认识，也了解了Example中各文件的含义：   
　　src文件夹：各进程（生产者，消费者，处理模块等）的功能定义，文件夹内包含2种文件：.c, 与对应的.h，就是实现的模块，就是.dot的框框的功能描述   
　　Example1.xml：系统架构即模块连接方式定义，里面定义了模块与模块之间是怎么连接的

　
