# Python for Data Analysis 相关笔记
## 统计学知识
### 协方差 （Covariance）
可以通俗的理解为：两个变量在变化过程中是同方向变化？还是反方向变化？同向或反向程度如何？你变大，同时我也变大，说明两个变量是同向变化的，这时协方差就是正的。你变大，同时我变小，说明两个变量是反向变化的，这时协方差就是负的。从数值来看，协方差的数值越大，两个变量同向程度也就越大。反之亦然。
> 百度百科定义：协方差表示的是两个变量的总体的误差，这与只表示一个变量误差的方差不同。 如果两个变量的变化趋势一致，也就是说如果其中一个大于自身的期望值，另外一个也大于自身的期望值，那么两个变量之间的协方差就是正值。 如果两个变量的变化趋势相反，即其中一个大于自身的期望值，另外一个却小于自身的期望值，那么两个变量之间的协方差就是负值。

期望值分别为E[X]与E[Y]的两个实随机变量X与Y之间的协方差Cov(X,Y)定义为：
$$Cov(X,Y) = E[(X - \mu_x)(Y - \mu_y)] $$
公式的简单解释：如果有两个变量X，Y，每个时刻的“X与其均值之差”乘以“Y与其均值之差”得到一个乘积，再对这每时刻的乘积求和并求出均值（其实是求“期望”）、

>参考链接 [如何通俗易懂地解释「协方差」与「相关系数」的概念](https://www.zhihu.com/question/20852004)

### 标准差 （Standard Deviation）
标准差（Standard Deviation） ，中文环境中又常称均方差，是离均差平方的算术平均数的平方根，用σ表示。在概率统计中最常使用作为统计分布程度上的测量。标准差是方差的算术平方根。标准差能反映一个数据集的离散程度。平均数相同的两组数据，标准差未必相同。
> 参考链接 [标准差](https://baike.baidu.com/item/%E6%A0%87%E5%87%86%E5%B7%AE)

$$
\sigma= \sqrt{\frac{1}{N}\sum_{i=1}^{N}{(x_i - \mu)}^2}
$$

> 其实标准差就是方差的算术平方根

###相关系数  
一般情况下，相关系数的公式为：
$$\rho = \frac{Cov(X,Y)} {\sigma_x \sigma_y}$$
就是用X、Y的协方差除以X的标准差和Y的标准差。相关系数也可以看成协方差：一种剔除了两个变量量纲影响、标准化后的特殊协方差。既然是一种特殊的协方差，那它的意义如下：、

* 也可以反映两个变量变化时是同向还是反向，如果同向变化就为正，反向变化就为负
* 由于它是标准化后的协方差，因此其重要性就体现出来了：它消除了两个变量变化幅度的影响，而只是单纯地反映两个变量每单位变化时的相似程度。
>参考链接 [如何通俗易懂地解释「协方差」与「相关系数」的概念](https://www.zhihu.com/question/20852004)

以上的相关系数是通常所说的**皮尔逊相关系数**,还有其它的几个相关系数，具体参见
[统计学习--三种常见的相关系数](https://zhuanlan.zhihu.com/p/34717666)

* Pearson相关系数是在原始数据的方差和协方差基础上计算得到，所以对离群值比较敏感，它度量的是线性相关。因此，即使pearson相关系数为0，也只能说明变量之间不存在线性相关，但仍有可能存在曲线相关。

* Spearman相关系数和kendall相关系数都是建立在秩和观测值的相对大小的基础上得到，是一种更为一般性的非参数方法，对离群值的敏感度较低，因而也更具有耐受性，度量的主要是变量之间的联系。

### 线性回归


## Python相关知识
### 一些小技巧 
* 在学习代码的过程中，经常看到一段代码`np.random.seed(12345)` ，特地查了一下这段代码的作用，原来每次运行代码时设置相同的seed，则每次生成的随机数也相同，如果不设置seed，则每次生成的随机数都会不一样。关于seed()的用法：  
  **seed()** 用于指定随机数生成时所用算法开始的整数值,  
  * 如果使用相同的seed( )值，则每次生成的随即数都相同；
  * 如果不设置这个值，则系统根据时间来自己选择这个值，此时每次生成的随机数因时间差异而不同
  * 设置的seed()值仅一次有效
  * 
  例如：  
  
  ```python 
   import numpy as np
   #不使用seed
   np.random.randn(3)
   [out] > array([ 0.1876, -0.3299, -1.1928])
   np.random.randn(3)
   [out] > array([-0.2049, -0.3588,  0.6035])
   
   #使用seed
   np.random.seed(3)
   np.random.randn(3)
   [out] > array([1.7886, 0.4365, 0.0965])
   # 再次调用
   np.random.seed(3)
   np.random.randn(3)
   [out] > array([1.7886, 0.4365, 0.0965])
  ```
  显示两次结果相同
  
* f

## Pandas和NumPy学习
### 资料地址：
* [NumPy教程](https://www.runoob.com/numpy/numpy-tutorial.html)  
* [Pandas中文网](https://www.pypandas.cn)
* [Python 3.7.6中文文档](https://docs.python.org/zh-cn/3.7/index.html)
* [Python Data Analysis with Pandas and Matplotlib](https://ourcodingclub.github.io/2018/04/18/pandas-python-intro.html)

## MatPlotLib和Seaborn学习
### 直方图(histogram)
直⽅图（histogram）是⼀种可以对值频率进⾏离散化显示的柱状图。数据点被拆分到离散的、间隔均 匀的⾯元中，绘制的是各⾯元中数据点的数量。直方图中非常重要的概念就是**bins**(X的值域被划分为不想交的连续子域，子域称作bucket或者bin，是X的数据分布的不相交的子集。bin的范围被称为宽度。通常，诸bins是等宽的).
如何确定合理的bins的值，可以利用 [Freedman-Diaconis rule](https://en.wikipedia.org/wiki/Freedman%E2%80%93Diaconis_rule) 进行计算:
$$ Bin \ width = 2\frac{IQR(x)}{\sqrt[3]{n}} $$
其中，IQR(x)是[interquartile range 数据的四分位](https://en.wikipedia.org/wiki/Interquartile_range)，n是观测样本x的数量。
> 其实就是bw <- 2 * IQR(x) / length(x)^(1/3)

### 密度图(density)
密度图，它是通过计算“可能会产⽣观测数据的连续概率分布的估计”⽽产⽣ 的。⼀般的过程是将该分布近似为⼀组核（即诸如正态分布之类的较为简单的分布）。因此，密度图 也被称作KDE（Kernel Density Estimate，核密度估计）图。
> 利用matplotlib绘制密度图例子：

```python
import pandas as pd
```


