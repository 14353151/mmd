### lab 3 DOL实例分析

##### 一、example2修改，让3个square模块变成2个。

##### 1、修改方法：

​	在example2.xml中把 variable value = 3 name="N" 变为 variable value = 2 name = "N"

##### 2、dot图

 ![example2dot](C:\Users\davidli\Desktop\example2dot.png)

##### 3、实验结果

  ![example2](C:\Users\davidli\Desktop\example2.png)

分析：这题要求我们修改迭代次数，根据TA的提示，我去分析了example2.xml的代码，然后发现iterator的部分为迭代部分，这部分的开头为：

`<iterator variable="i" range="N + 1">`

经过观察为range=“N + 1” 应当表述迭代次数，所以我要修改N的值，而该是在前面定义的，所以我将相应代码修改为：

`<variable value="2" name="N"/>`

这样就可以了。

##### 二、example1修改，让其输出3次方。

###### 1、修改方法：

​	在square.c文件中修改i=i* i 为i=i* i * i，然后重新运行example即可。

##### 2、dot图

 ![example1dot](C:\Users\davidli\Desktop\example1dot.png)

###### 3、修改结果截图：

 ![example1](C:\Users\davidli\Desktop\example1.png)



分析：这题要求我们改变输出，从i的平方变成i的立方，这样显然就要从square.c上入手，然后我们分析该文件的代码：

`DOL_read((void*)PORT_IN, &i, sizeof(float), p);`

 `i = i*i;`

`DOL_write((void*)PORT_OUT, &i, sizeof(float), p);`

显然前一段是读入i，后一段是输出i，所以 i= i* i 就代表输出值i，所以我们只需要改变这里的代码为i= i * i *i就可以了。

#### 三、实验感想

​	本次实验我对dol系统的相应的example有了初步的了解，知道了这些example的运行机理，相信对今后的学习会有很大的帮助。