# 1.视觉组介绍前言

# 2.视觉组必备技能

# 3.Opencv

# 4.搜索方式及提问

## 1.视觉组介绍前言：

视觉组主要负责机器人所搭载计算机系统的开发，使机器人具备感知功能。具体任务包括图像处理、神经网络、SLAM、基于ROS系统的开发等。

AI组最主要负责的是机器人的视觉，简单来说，就是用摄像头代替人眼，通过计算机的多种图像处理技术来实现识别和定位，从而对现实世界进行测量和判断，机器人拥有视觉的意义在于让机器人能够全方位观察身边的整个世界，脱离只能靠光感传感器获取信息的半瞎子状态，实现更多的高级功能。

## 2.视觉组必备技能：

**No.1视觉组程序语言一般使用C++**

大部分理工专业都会必修这门课程，相对应发放的课本已经足够带没有基础的朋友入门。如果课本还没有发，或者有想要跨专业的同学，那么推荐同样供入门和理清概念的《C++ Primer》和经典《C++程序设计语言》；如果已经有一点点基础，但是需要复习和进一步提升，那么推荐供提升的《（more）Effective C++》及《C++编程规范》等，**最后跟着暑假c++作业做！！！**

**No.2 Opencv（一个开源计算机视觉库）**

里面有大量的可以供我们调用的数字图像处理函数、机器学习函数等。到2018年，Opencv已经18岁了，开源、跨平台和效率高使它即适合于钻研算法的研究党，也适用于的实际应用的工程党。我们的主要工作就是使用Opencv搞事情——给机器人一双洞察世界的慧眼。

**No.3 数学基础**

这个东西没有上限，没有止境，是图像处理和机器学习的基石。在敲代码和看文献的过程中会起很大作用。代数（线性代数、高等代数）和微积分（高等数学，数学分析）都是需要的，这两门也是每个学校都会开设的课程。

**No.4视觉编程的开发环境——Ubuntu。**

Ubuntu是一个基于Linux开源（开源、开源，重要的事情说三遍）的操作系统，工作室使用的版本推荐16.04.LTS。这是一个真正属于你的操作系统，你对它享有绝对的权限，他也是广大程序员钟爱的操作系统。我们的程序也是要在这个操作系统上运行的。它是一个忠实的朋友，你只需要知道相应的命令，它可以为你做任何他会做的事情（包括删除自己）。

**No.5串口通信**

这是计算机和单片机沟通最常用和最简单的方式之一。通过串口，我们可以给单片机提供必要的数据，相当于把眼睛看到的东西告诉大脑。

**No.6 Git**

Git是一个开源的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理，和linux操作系统同宗，是帮助大家团队协作、共同开发的利器。

**No.7 Cmake**

Cmake常用来make一些C/C++项目，它的主要工作的把程序员写的文本代码提供给编译器。编译过后，我们的代码就变成了有实际功能的可执行文件。

## 3.Opencv

**前提：已经配置好了VSstudio并且已经配好环境的，请看下一步学习，如果还没有配置好，请回去看配置环境那一部分培训内容，配置好了再回来继续学习！！！！**

1-----图像处理与分析的简要过程：

STEP1：摄像头获取图像

STEP2：对图像进行滤波

STEP3：对图像进行二值化

STEP4：图像形态学操作

STEP5：图像进行轮廓/特殊形状/边缘检测（霍夫变换-直线检测）

STEP6：提取检测结果所蕴含的信息

**STEP 1：获取图像**

1-1数字图像处理基础

**先问一下自己什么是图像**，**好了在心中自己下个定义，等5秒，1......5，**

**到了，想到了没有，没有想到也没关系，想到了那么你就很聪明。**

**图像定义：**

灰度图像由一个二维灰度（或亮度）的函数f(x,y)组成。在定义为f(x,y)的二维函数中，x,y是空间坐标，f(x,y)是点（x,y）的幅值。

彩色图像由三个（如RGB,HSV）二维灰度（或亮度）函数f(x,y)组成。![](C:\Users\25212\Desktop\WeChat Image_20190726144746.jpg)



**数字图像定义**

像素组成的二维排列，可以用矩阵表示。

对于单色（灰度）图像而言，每个像素的亮度用一个数值来表示，通常数值范围在0到255之间，0表示黑、255表示白，其它值表示处于黑白之间的灰度。

彩色图像可以用红、绿、蓝三元组的二维矩阵来表示。

![](C:\Users\25212\Desktop\WeChat Image_20190726144903.jpg)

1-2数字图像质量

**图像采样**

空间坐标(x,y)的数字化被称为图像采样。采样即确定水平和垂直方向上的像素个数N、M。![](C:\Users\25212\Desktop\WeChat Image_20190726145142.jpg)

**图像量化**

函数取值的数字化被称为图像的量化，如量化到256个灰度级。

![](C:\Users\25212\Desktop\WeChat Image_20190726145250.jpg)

**图像的质量：层次**

灰度级：表示像素明暗程度的整数量。

例如：像素的取值范围为0-255，就称该图像为256个灰度级的图像。

层次：表示图像实际拥有的灰度级的数量。

例如：具有32种不同取值的图像，可称该图像具有32个层次。

图像数据的实际层次越多，视觉效果就越好。

![](C:\Users\25212\Desktop\WeChat Image_20190726145356.jpg)

**图像的质量：对比度**

对比度：是指一幅图像中灰度反差的大小。

对比度 = 最大亮度 / 最小亮度

![](C:\Users\25212\Desktop\WeChat Image_20190726145451.jpg)

图像的质量：清晰度

与清晰度相关的主要因素：亮度、对比度、颜色饱和度、尺寸大小、细微层次 

![](C:\Users\25212\Desktop\WeChat Image_20190726145536.jpg)

![](C:\Users\25212\Desktop\WeChat Image_20190726145543.jpg)

![](C:\Users\25212\Desktop\WeChat Image_20190726145551.jpg)

![](C:\Users\25212\Desktop\WeChat Image_20190726145559.jpg)

![](C:\Users\25212\Desktop\WeChat Image_20190726145606.jpg)

**STEP 2：滤波处理**

![](C:\Users\25212\Desktop\WeChat Image_20190726145740.jpg)

2-1均值滤波

**算术均值滤波**

![](C:\Users\25212\Desktop\WeChat Image_20190726145834.jpg)

Sxy表示中心在(x,y)，尺寸为m×n的矩形窗口平滑了一幅图像的局部变化，在模糊了结果的同时减少了噪声。

**几何均值滤波**



![](C:\Users\25212\Desktop\WeChat Image_20190726145942.jpg)

几何均值滤波器所达到的平滑度可以与算术均值滤波器相比，但几何均值滤波器在滤波过程中，与算术均值滤波器相比，会丢失更少的图像细节——相对锐化。

![](C:\Users\25212\Desktop\WeChat Image_20190726150014.jpg)

算术均值滤波器和几何均值滤波器适合于处理高斯或均匀等随机噪声，缺点是必须事先知道噪声是暗噪声还是亮噪声，以便于选择合适的Q符号。

**2-2中值滤波**

![](C:\Users\25212\Desktop\WeChat Image_20190726150058.jpg)

在相同尺寸下，比起均值滤波器引起的模糊少，对单极或双极脉冲噪声非常有效。

**2-3高斯滤波**

**高斯噪声**

了解高斯滤波之前，我们首先熟悉一下高斯噪声。



高斯噪声是指它的概率密度函数服从高斯分布（即正态分布）的一类噪声。如果一个噪声，它的幅度分布服从高斯分布，而它的功率谱密度又是均匀分布的，则称它为高斯白噪声。



对于图像来说，高斯滤波器是利用高斯核的一个2维的卷积算子，用于图像模糊化（去除细节和噪声）。

**高斯分布**

一维高斯分布

二维高斯分布

**高斯核**

理论上，高斯分布在所有定义域上都有非负值，这就需要一个无限大的卷积核。

实际上，仅需要取均值周围3倍标准差内的值，以外部份直接去掉即可。 

**2-4双边滤波**

双边滤波（Bilateral filter）是一种非线性的滤波方法，是结合图像的空间邻近度和像素值相似度的一种折衷处理，同时考虑空域信息和灰度相似性，达到保边去噪的目的。

双边滤波器之所以能够做到在平滑去噪的同时还能够很好的保存边缘（Edge Preserve），是由于其滤波器的核由两个函数生成。一个函数由像素欧式距离决定滤波器模板的系数，另一个函数由像素的灰度差值决定滤波器的系数。

高斯滤波器只考虑像素间的欧式距离，其使用的模板系数随着和窗口中心的距离增大而减小；

α截尾均值滤波器只考虑了像素灰度值之间的差值，去掉α%的最小值和最大值后再计算均值；

双边滤波器使用二维高斯函数生成距离模板，使用一维高斯函数生成值域模板。

距离模板系数的生成公式如下：

![img](https://mmbiz.qpic.cn/mmbiz/XKibCyd3WnNN4QuPpXVI68l8qMnekiaATbsdhsfj9gLdCzaYERAlVP5pibL7LGMYib2T5ErIC7wLAjmQ6eiaU0AcQXA/640?wx_fmt=other&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

其中,(k,l)为模板窗口的中心坐标；(i,j)为模板窗口的其他系数的坐标；σ为高斯函数的标准差。使用该公式生成的滤波器模板和高斯滤波器使用的模板是没有区别的。

值域模板系数的生成公式如下：

![img](https://mmbiz.qpic.cn/mmbiz/XKibCyd3WnNN4QuPpXVI68l8qMnekiaATbDHCibtxW5ZIYvGjRs399Ud0eibOjYptuCcGvLliaf5pqeNpfJHGbNibibTA/640?wx_fmt=other&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

其中，函数f(x,y)表示要处理的图像，f(x,y)表示图像在点(x,y)处的像素值；(k,l)为模板窗口的中心坐标；(i,j)为模板窗口的其他系数的坐标；σr为高斯函数的标准差。

将上述两个模板相乘就得到了双边滤波器的模板：

![img](https://mmbiz.qpic.cn/mmbiz/XKibCyd3WnNN4QuPpXVI68l8qMnekiaATbB4wTlJefNK0SAszYeGIfdibNqzmyN9J2micQ3REElDfbgKPyWavtCdLg/640?wx_fmt=other&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**STEP 3：二值化处理**

**二值化处理的四种方法**

3-1**直接设定像素值**

该方法非常简单，对RGB彩色图像灰度化以后，扫描图像的每个像素值，值小于127的将像素值设为0(黑色)，值大于等于127的像素值设为255(白色)。

该方法的好处是计算量少速度快。缺点更多首先阈值为127没有任何理由可以解释，其次完全不考虑图像的像素分布情况与像素值特征。

**3-2计算像素的平均值K**

最常见的二值处理方法是计算像素的平均值K，扫描图像的每个像素值如像素值大于K像素值设为255(白色)，值小于等于K像素值设为0(黑色)。

该方法相比方法一，阈值的选取稍微有点提高，可以解释。但是使用平均值作为二值化阈值同样有个致命的缺点，可能导致部分对象像素或者背景像素丢失。二值化结果不能真实反映源图像信息。

**3-3直方图找二值化阈值**

使用直方图方法来寻找二值化阈值，直方图是图像的重要特质，直方图方法选择二值化阈值主要是发现图像的两个最高的峰，然后在阈值取值在两个峰之间的峰谷最低处。

该方法相对前面两种方法而言稍微精准一点点。结果也更让人可以接受。

![](C:\Users\25212\Desktop\WeChat Image_20190726150755.jpg)

**STEP 4形态学操作**

**4-1 概述**

形态学，即**数学形态学**（mathematical Morphology，也称“图像代数”），表示以形态为基础对图像进行分析的数学工具，是图像处理中应用最为广泛的技术之一。

形态学操作主要用于提取图像特征[1]，简化图像数据，保持它们基本的形状特性，并除去不相干的结构。从而使后续的识别工作能够抓住**目标对象最为本质[2]的形状特征**，如边界和连通区域等。

形态学图像处理的数学基础和所用语言是集合论，基本运算为：膨胀、腐蚀、开操作和闭操作。本文的介绍基本针对的是**二值图像**。

**4-2集合论逻辑运算**

![](C:\Users\25212\Desktop\WeChat Image_20190726151200.jpg)

从左到右，从上到下的运算为：补集运算、并集运算、交集运算、差集运算

**4-3腐蚀和膨胀**

**1）结构元素**

二维结构元素可以理解成一个二维矩阵，矩阵元素的值为0或者1。通常结构元素要小于待处理的图像。



**2）腐蚀**

腐蚀是一种**消除边界点，使边界向内部收缩**的过程。可以用来消除小且无意义的物体。

 

腐蚀的算法：扫描图像的每一个像素，用结构元素（一般为3×3）和该元素覆盖的二值图像做“与”操作。如果都为1，结果图像的该像素为1，否则为0。

结果：**使二值图像减小一圈**。

算法原理：把结构元素B平移a后得到Ba，若**Ba包含于X**，我们记下这个a点，**所有满足上述条件的a点组成的集合称做X被B腐蚀（Erosion）的结果**。

用公式表示为：![img](https://mmbiz.qpic.cn/mmbiz_jpg/XKibCyd3WnNN38JlYp1N5NOianKickChic8xLy5pVLCrAxTDowxyNmLSQCS9JoPbB5fyt1pKxEyFibBiaic99QDC6ccfw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

*应用于一般图像的腐蚀公式



![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNN38JlYp1N5NOianKickChic8x3a92yzQz6w77oVB6ic7kyMpJmLVSEj9ibFnN2jZezicbjiagNnBK23ibBAA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![](C:\Users\25212\Desktop\WeChat Image_20190726151518.jpg)

图中左边是被处理的图象X（二值图象，我们针对的是图中的**黑点**），中间是结构元素B，那个标有origin 的点是**中心点**，即当前处理元素的位置。

腐蚀的方法是，拿B的中心点和X上的点一个一个地对比，**当B的中心点和X范围内的某一点重合时，若此时B上的其他点也在X范围内，则X上的该点保留****，否则将该点去掉。**

 图中右边是腐蚀后的结果。可以看出，它仍在原来X的范围内，且比X包含的点要少，就像X被腐蚀掉了一圈。

![](C:\Users\25212\Desktop\WeChat Image_20190726151556.jpg)

**3）膨胀**

膨胀是将与物体接触的所有背景点合并到该物体中，**使边界向外部扩张**的过程。可以用来**填补物体中的空洞**。



膨胀的算法：扫描图像的每一个像素，用结构元素（一般为3×3）和该元素覆盖的二值图像做“或”操作。如果都为0，结果图像的该像素为0，否则为1。

结果：**使二值图像扩大一圈**。

 

膨胀(dilation)可以看做是**腐蚀的对偶运算**，其定义是：把结构元素B平移a后得到Ba，若**Ba击中（Ba上存在一点与X上的点重合）**，我们记下这个a点。所有满足上述条件的a点组成的集合称做X被B膨胀的结果。

用公式表示为：![img](https://mmbiz.qpic.cn/mmbiz_jpg/XKibCyd3WnNN38JlYp1N5NOianKickChic8xfYq2ic7L0LhLRTibvDZmib1gvicAD9Y1kNcrbQ1nlnrW97RCq53juliccibQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

上式表示B的反射进行平移，与A的交集不为空。

或表示为：![img](https://mmbiz.qpic.cn/mmbiz_jpg/XKibCyd3WnNN38JlYp1N5NOianKickChic8xp4YcnF0cLsmo8siaktwteoQibeUKr0gt7BsmwJNW7uib92zkxibr2pQRtg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

*应用于一般图像的膨胀公式



![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNN38JlYp1N5NOianKickChic8x6qU1ibmzGvB6CmS6ibtNgtjCqVAyw7loKzSVlfn9rAaknh1S9sLCOEjA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

上式表示B的反射进行平移，与A的交集是A的子集。

![](C:\Users\25212\Desktop\WeChat Image_20190726151646.jpg)

图中左边是被处理的图象X（二值图象，我们针对的是图中的**黑点**），中间是结构元素B，那个标有origin的点是中心点，即当前处理元素的位置。。

膨胀的方法是，拿B的中心点和X上的点及X周围的点一个一个地对比，**当B的中心点和所给范围内的某一点重合时，若此时B上有一个点落在X的范围内****，则与B的中心点重合的该点保留或变为黑点。**

图中右边是膨胀后的结果。可以看出，它包括X的所有范围，就象X膨胀了一圈。

![](C:\Users\25212\Desktop\WeChat Image_20190726151723.jpg)

膨胀的应用：**桥接文字裂缝**

优点：在一幅二值图像中直接得到结果。

**3）膨胀和腐蚀的优缺点**

优点：这两种运算**逻辑简单，容易实现**；膨胀运算可以使图像轮廓更加平滑；

缺点：运算中会有大量的访问操作和窗口操作，非常**耗时**，因此在视觉识别的过程中，即使图像存在噪声，一般也不会用腐蚀和膨胀去消除。

**4-4开运算&闭运算**

**1）开运算**

一般来说， 开运算能够**去除孤立的小物体****，去除毛刺和小桥(即连通两块区域的纤细小点)从而分离物体，以及平滑较大物体的边界，同时维持总的位置和形状不明显改变**。



先腐蚀后膨胀的过程称为开运算 (open)，即OPEN(X)=D(E(X))。

用公式表示为：![img](https://mmbiz.qpic.cn/mmbiz_jpg/XKibCyd3WnNN38JlYp1N5NOianKickChic8xNicTfDjZDxrYoqJk0ibWw5khrncicicaLYIooicibQc1e8icKboUwBeWWttyA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

上式含义：先用B对A腐蚀，然后用B对结果膨胀。

或表示为：![img](https://mmbiz.qpic.cn/mmbiz_jpg/XKibCyd3WnNN38JlYp1N5NOianKickChic8x6JiaXz6TMwFqOcq3AVZpDAsqX7ayVIstXyiaomRhTZ1WepN7mbmnNnmg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

 

让我们来看看实际上是如何进行开运算的。

![](C:\Users\25212\Desktop\WeChat Image_20190726151828.jpg)

 开运算

图中上面的两幅图中，左边是被处理的图象X（二值图象，我们针对的是黑点），右边是结构元素B；下面的两幅图中左边是腐蚀后的结果，右边是在此基础上膨胀的结果。可以看到，**原图经过开运算后，****一些孤立的小点被去掉了**。

下图是开运算的几何解释。左边灰色圆B对三角形A腐蚀，虚线为腐蚀过程中Ba的路径；中间黑色实线为膨胀过程Ba的路径；右边灰色区域为膨胀结果。

![](C:\Users\25212\Desktop\WeChat Image_20190726151901.jpg)

开运算实例：![](C:\Users\25212\Desktop\WeChat Image_20190726151936.jpg)

**2）闭运算**

与开运算相反，闭运算能够**填平小湖(即小孔)，弥合小裂缝（狭窄的间断和长细的鸿沟），以及填补轮廓线中的裂痕，同时维持总的位置和形状不发生明显变化**。

先膨胀后腐蚀称为闭（close），即CLOSE(X)=E(D(X))

用公式表示为：![img](https://mmbiz.qpic.cn/mmbiz_jpg/XKibCyd3WnNN38JlYp1N5NOianKickChic8xiboSSbHMqYPuIDbyJ4zIye4VS3IlG2meZYxv8ImNWBs1YV5pw8iaFB4Q/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

上式含义：先用B对A膨胀，然后用B对结果腐蚀。

![](C:\Users\25212\Desktop\WeChat Image_20190726152008.jpg)

图中上面的两幅图中，左边是被处理的图象X(二值图象，我们针对的是黑点)，右边是结构元素B；下面的两幅图中左边是膨胀后的结果，右边是在此基础上腐蚀的结果。可以看到，**原图经过闭运算后，断裂的地方被弥合了**。

 下面是闭运算的几何解释。左边灰色圆B对V形槽A膨胀；中间图的实线为膨胀过程中Ba的路径；右边灰色区域为腐蚀结果。

![](C:\Users\25212\Desktop\WeChat Image_20190726152046.jpg)

**3）开运算和闭运算的关系**

你大概已经猜到了，开和闭也是**对偶运算**，的确如此。

用公式表示为：(OPEN(X))c=CLOSE(Xc))，或者(CLOSE(X))c =OPEN((Xc))。

即：X开运算的补集等于X的补集的闭运算，或者X闭运算的补集等于X的补集的开运算。

这句话可以这样来理解：在两个小岛之间有一座小桥，我们把岛和桥看做是处理对象X，则X的补集为大海。如果涨潮时将小桥和岛的外围淹没（相当于用尺寸比桥宽大的结构元素对X进行开运算），那么**两个岛的分隔，相当于小桥两边海域的连通**（对Xc做闭运算）。

**4-5基于形态学基本运算的应用**

**1）细化运算**

一般指二值图像的**骨架化（ImageSkeletonization）** 的一种操作运算。所谓细化，就是**从原来的图中去掉一些点，但仍要保持原来的形状，实际上，是保持原图的骨架**。骨架，可以理解为图象的中轴。例如一个长方形的骨架是它的长方向上的中轴线，正方形的骨架是它的中心点，圆的骨架是它的圆心，直线的骨架是它自身，孤立点的骨架也是自身。

**2）边界提取与跟踪**

轮廓是对物体形状的有力描述，对图像分析和识别十分有用。通过边界提取算法可以**得到物体的边界轮廓**，而边界跟踪算法在提取边界的同时还能依次记录下边**界像素的位置信息**。

 **3）区域填充**

区域填充可视为**边界提取的反过程**， 它是在边界已知的情况下得到边界包围的整个区域的形态学技术。 

**4）噪声滤除**

对图像中的噪声进行滤除是图像预处理中不可缺少的操作。**将开启和闭合运算结合起来可构成形态学噪声滤除器。**

对于二值图像，噪声表现为目标周围的噪声块和目标内部的噪声孔。用结构元素B对集合A进行开启操作，就可以将目标周围的噪声块消除掉；用B对A进行闭合操作，则可以将目标内部的噪声孔消除掉。该方法中，对结构元素的选取相当重要，它应当比所有的噪声孔和噪声块都要大。

**step 5-1边缘检测**

梯度算子

● 图像f(x,y)在位置(x,y)的梯度定义为下列向量

![](C:\Users\25212\Desktop\WeChat Image_20190726152530.jpg)

霍夫变换-直线检测

\#Hough变换问题的提出

● 在找出边界点集之后，需要连接，形成完整的边界图形描述

![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJCBzOHRXWBttEWqseI2h6ggTgGEph1kcdNRrDhrqpf3Wemqqj0ATDMg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

\#Hough变换的基本思想

● 对于边界上的n个点的点集，找出共线的点集和直线方程。

● 对于任意两点的直线方程：y = ax +b，构造一个参数a，b的平面，从而有如下结论：

![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJUMOXREoRRVK9pZUzKia3UaZias1D5E01Pibl85XKsk1NgNX6N2uvuxMDg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

● xy平面上的任意一条直线y = ax +b ，对应在参数ab平面上都有一个点



![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJ5kG12pKUftZLFukQcHK8ISQy26WL8IjTSBvsX9EnPkafVtBFKRxLNQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



● 过xy平面一个点(x,y)的所有直线，构成参数ab平面上的一条直线

![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJMke72o9LicXUDCCNPoqCBYPTibINf1icL4l7wicKs54lfKVBeu10UHMJKQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

● 如果点(x1,y1)与点(x2,y2)共线，那么这两点在参数ab平面上的直线将有一个交点,具有相同的a和b



![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJmXbzjCKK1ny0PGpUKy6rGLAuNj2lDNTSoot7wTpTqv6PVicIwPOTeZw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

● 在参数ab平面上相交直线最多的点，对应的xy平面上的直线就是我们的解

![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJIofx6TSyBoUAF2COicibib4ue8hsxCacrh6dvqsibibsWRYhv8mtQsnI6Kg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJgKictxkhZXg8iaS2ewhcHGcySjsSQUF5T5h54oDquApL9aOaoCRIp4Qw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

\#Hough变换算法实现

● 由于垂直直线a为无穷大，我们改用极坐标形式：

![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJYNHjozjPWUQe5kq9Tb2icVKumNcAzupepmeYHdN2bYE5R2XD1ZGVQMw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

● 参数平面对应的不是直线而是正弦曲线

● 使用交点累加器，或交点统计直方图，找出相交线段最多的参数空间的点

● 然后找出该点对应的xy平面的直线线段

![img](https://mmbiz.qpic.cn/mmbiz_png/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJB8QUibVVxs0sjW61I3M4FZrfOdyFXwD2CibkaEGVK253Z384AfiaWbIUg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



● 问题一：为甚么不用高中直线公式 y=kx+b?

答：没有一种数据类型可以用来表示斜率，因为斜率会有无穷搭（不存在）的情况。



● 问题二：为什么用于统计投票的图像的正弦曲线交点多于直线数目：

答：跟取的theta范围有关，取0-2Pi的时候，会有两个交点，例如90度的直线和270的直线实际是同一条直线，但是theta会有90度和270度两个值。

 

\#Hough变换的扩展

● Hough变换不只对直线，也可以用于圆：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/XKibCyd3WnNMiaAzOoj3rKnqfr2fQ028dJzNt3VnvOQ02foVnPFcHf8cXaKgNT1MljfiaPaia3epWCwhhEOBDiblOhw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

● 这时需要三个参数的参数空间

--------------------------------------

**干货学习：**

**官方网站：官方二字透露着绝对权威、绝对全面的霸气。官方网站提供的技术支持是最全面的最有保证的，另外官网还会提供简练的概述，供大家更好的了解要学的知识。简单来说，不管要学什么，先看他的官网。比如Opencv的官网、Caffe2的官网、Git官网……**



**知乎：知乎是一个大神云集的社交网络平台，在上面经常有和胡歌、赵丽颖搭过戏的网友发言；经常有和王健林或者雷军一起共进晚餐的人士发言…… 以上是“逼乎”的由来。但对于我们来说，知乎上对于技术问题的解答往往十分透彻，更有Caffe的创始人贾杨清这样的大佬谈深度学习……**

**下面是一篇经典的傅里叶变换教程：（网称”傅里叶之掐死教程”）**

**https://zhuanlan.zhihu.com/p/32620793** 

**知乎上不乏这样幽默的讲解难题的大佬。**



**专业IT技术社区CSDN：曾经他还冠以全球最大，下面会介绍为何没了“全球最大”，尽管如此，CSDN博客上还是有质量很高的博文；CSDN下载里还是有值得学习的源代码。**



**Github: 我不确定是谁将CSDN推下全球最大的神坛，但里面一定有Github的功劳，Github的源代码质量比CSDN高，而且是完全免费的，而且来源是全世界的程序员，你经常可以Download到台湾省同胞或者国际友人的代码。**



**哔哩哔哩：我们不是死板的人，Bilibili上的教学视频的水平已经达到了一定的高度，范围不单单涵盖各种软件的使用，编程教学和神经网络，还有各大学科的教学视频，比如前面的线代、高数、理论力学、材料力学和概率统计…… 既能帮你学技术，又能帮你备考。**



**淘宝和闲鱼：往往有10个G卖9毛9教学资源。不咋推荐这个，因为容量太多了，**

**基本上买几块钱的，这辈子就看不完了23333。**

-----------------------------------------------------------------------------

2----------解算角度运算