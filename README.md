# 14353151 李学思

### 一、Description *DOL框架描述*

​	DOL是一个在多进程系统下的、基于systemc 开发运行软件的框架。基本上分为如下3个方面：

##### 1、DOL编程应用接口：

​	DOL定义了一系列的计算和联通方式，这些方式可以让并行应用程序可以应用到SHAPE平台上

##### 2、DOL仿真功能：

​	为编程者提供一种可以测试自己应用程序的方式，并可以通过这种方式获得相应测试参数。

##### 3、DOL映射优化：

​	是把一个应用程序以一系列优化方式映射到SHAPE构筑平台

### 二、installation *DOL安装笔记*

#### 1、配置必要环境

``sudo apt-get update``

``sudo apt-get install ant``

``sudo apt-get install openjdk-7-jdk``

``sudo apt-get install unzip``

总结：这几步其实并不难，不过下载时间会很长

#### 2、解压文件

``mkdir dol`` 新建dol的文件夹

``unzip dol_ethz.zip -d dol``

``tar -zxvf systemc-2.3.1.tgz`` 解压systemc

总结：没什么特别的需要注意。

#### 3、编译systemc

解压``cd systemc-2.3.1`` 

新建临时文件夹``mkdir objdir`` 

``cd objdir``

运行configure``  ../configure CXX=g++ --disable-async-updates``

``sudo make install``

``pwd``  做完这一步之后记录当前路径

总结：修改路径这一步一定要小心，不要打错了。

#### 4、编译dol

``cd ../dol``

修改build_zip.xml文件中对应的路径，修改为刚才记录的路径。

``ant -f build_zip.xml all``

``cd build/bin/main``

``ant-f runexample.xml -Dnumber=1``

总结：这几步没有特别需要注意的地方，只是注意指令不要打错就好。

















