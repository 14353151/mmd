##### 14353151 李学思

### ROS和cartographer的配置笔记

#### 一、实验目的

体验安装配置ROS和cartographer的过程。

#### 二、配置ROS

根据TA的网址得到需要输入的代码：

其实只要跟着步骤走，就基本上不会有问题，在1.4的时候需要注意一下，如果输入了指令`sudo apt-get update` 的话，就不要输入1.4部分的其它代码了。这里我在几个关键的地方截图，来表示配置过程。

1、`sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`

2、`sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`

3、`sudo apt-get update`

4、`sudo rosdep init`

`    rosdep update`![sudo rosdep init](C:\Users\davidli\Desktop\sudo rosdep init.png)

5、`sudo apt-get install python-rosinstall` ![QQ截图20161110123320](C:\Users\davidli\Desktop\QQ截图20161110123320.png)

自此，ROS就已经配置完成了，整个过程没有遇到什么大问题。

#### 三、配置cartographer

根据TA提供的代码一步一步地输入指令：

1、`sudo apt-get update`

​     `sudo apt-get install -y python-wstool python-rosdep ninja-build`

 2、`mkdir catkin_ws``cd catkin_ws``wstool init src`

 ![c3](C:\Users\davidli\Desktop\c3.png)

3、`wstool merge -t src https:// raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall`

`wstool update -t src`

 ![c4](C:\Users\davidli\Desktop\c4.png)

4、`rosdep init` `rosdep update` `rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y`

到此为止我的配置没有遇到什么问题，但是在运行`catkin_make_isolated --install --use-ninja  ` 的步骤时就出错了，系统无法访问一个地址，用来配置cartographer的环境。所以我开始配置环境：

#### 四、从网站上找出相关地址，上面有相关的代码，顺着输入代码：

##### 1、配置librarise ：

`sudo apt-get update`

`sudo apt-get install -y cmake g++ git google-mock libboost-all-dev   libcairo2-dev libeigen3-dev libgflags-dev libgoogle-glog-dev  liblua5.2-dev   libprotobuf-dev libsuitesparse-dev libwebp-dev ninja-build  protobuf-compiler python-sphinx`

##### 2、配置 ceres:

`git clone https://ceres-solver.googlesource.com/ceres-solver`

`cd ceres-solver` `mkdir build` `cd build` `cmake .. -G Ninja` 

`ninja ` 这一步执行了很长时间，这里我截图了。

![ni2](C:\Users\davidli\Desktop\ni2.png)

`ninja test`

![ni3](C:\Users\davidli\Desktop\ni3.png)

`sudo ninja install`

##### 3、安装Cartographer

1 、 `cd cartographer` `mkdir build` `cd build`  `cmake .. -G Ninja` 

2、`ninja`

![ca1](C:\Users\davidli\Desktop\ca1.png)

3、`ninja test`

![ca2](C:\Users\davidli\Desktop\ca2.png)

4、`sudo ninja install` 

![ca3](C:\Users\davidli\Desktop\ca3.png)

自此，配置cartographer就完成了。

#### 5、实验感想

​	本次实验，我掌握许多Ubuntu 的指令，对如何配置ROS和cartographer有了深刻的了解，同时，这次配置实验中我遇到了许多问题，但是和舍友与百度的帮助下，我一一解决了这些问题。