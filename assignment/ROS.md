##配置Ubuntu的软件库
![](http://i.imgur.com/FPSj1wc.png)![](http://i.imgur.com/OKwwJqN.png)
##添加软件源到sources.list
添加正确的软件源，使操作系统知道去哪里下载程序，并根据命令自动安装软件。
设置软件源的代码如下：

	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
##设置密钥

	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116
![](http://i.imgur.com/b0mL122.png)
##安装
1.首先确认Debian的软件包索引是最新的。Debian计划是一个致力于创建一个自由操作系统的合作组织。我们所创建的这个操作系统名为 Debian。Debian系统目前采用Linux内核或者FreeBSD内核。

	$ sudo apt-get update
![](http://i.imgur.com/02eaAh1.png)
ubuntu14.04不安装以下的 packages， 14.04会摧毁X服务器

	sudo apt-get install xserver-xorg-dev-lts-utopic mesa-common-dev-lts-utopic libxatracker-dev-lts-utopic libopenvg1-mesa-dev-lts-utopic libgles2-mesa-dev-lts-utopic libgles1-mesa-dev-lts-utopic libgl1-mesa-dev-lts-utopic libgbm-dev-lts-utopic libegl1-mesa-dev-lts-utopic
下载以下包解决依赖问题

	sudo apt-get install libgl1-mesa-dev-lts-utopic
2.安装选择完全安装Desktop-Full Install，完全安装时的工具包括ROS、rqt、可视化环境rviz、通用机器人库robot-generic libraries、2D（如stage）和3D（如Gazebo）仿真环境2D/3D simulators、导航功能包集navigation and 2D/3D（移动、定位、地图绘制、机械臂控制）、感知库perception（如视觉、激光雷达、RGB-D摄像头等）

	sudo apt-get install ros-jade-desktop-full
##初始化rosdep
rosdep不仅能够使方便的安装一些系统依赖程序包，而且ROS的一些主要部件的运行也需要rosdep。

	$ sudo rosdep init
	$ rosdep update
#设置环境
添加ROS的环境变量，这样，当你打开你新的shell时，你的bash会话中会自动添加环境变量。

	echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
以上使环境变量设置立即生效

	source ~/.bashrc
	
##安装rosinstall
rosinstall命令是一个使用的非常频繁的命令，使用这个命令可以轻松的下载许多ROS软件包。

	sudo apt-get install python-rosinstall
至此，ROS已经配置成功。
##获取ROS源码
使用apt-get source即可下载相应的package,如下

	$ apt-get source ros-jade-laser-pipeline
![](http://i.imgur.com/WQzZZj9.png)

通过下面的命令进行测试，看看是不是真的安装成功了，因为还没有跑cartographer所以可以通过以下方式验证

 #查看环境变量(ROS_PACKAGE_PATH)
	
xxx@...$ export | grep ROS
![](http://i.imgur.com/ebRIEv0.png)
