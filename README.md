# HPC-FinalProject
## Title: 一维传热方程的迭代求解
## Information
autior：苏梓鑫;

Data:   2022/06/06;

Notification: 最终版本是在TAIYI 上跑的，所以CMakeLists.txt 是TAIYI版本的，这里提供了本地版本的在local文件夹里
## 使用说明

ls 查看是否有build文件夹，如果有，

`rm -rf build`

`mkdir build`

`cd build`

`cmake ../src`

`make`

即可生成可执行文件，implicitMethod 和 explicitMethod

## 文件夹解释

report 存放着latex文件，部分图片还没弄进来。 gplot.py 是绘图部分

local 存放一些杂乱文件

result 存放着跑出来的结果，TAIYI文件夹中才有

src  源代码文件以及 Makefile 和 CMakeList.txt 其中需要修改路径




## Log
### 2022.6.1
简单写完了显式的迭代，测试结果是一个大概在$[0,\pi]$的正弦函数形状。
### 2022.6.3
前面写完的显式迭代，结果并行有问题，因为取j+1的时候会涉及到processor通信，导致越界。所以改写成矩阵的乘法形式，重写了显式迭代。
### 2022.6.5
把main.c 变成demo，两种方法分开写，然后测试了显式的结果是正确的，并且可以正确的并行。等全部写完再一起测试结果。
### 2022.6.6
增加注释以及添加计时模块
### 2022.6.7
完成HDF5重启功能，完成了包括误差对比等工作。
### 2022.6.8
完成CMakeLists.txt 的书写, Makefile没有舍弃依旧保存着。
构建方法，`cd build`; `cmake ../src`; `make`; 就可以构建完成
本地装的是最新版，可以用`PetscCall`, TAIYI上装的是3.16.6 所以把PetscCall换回ierr
### 2022.6.9 
完成所有任务，提交最终版。