# Windows

## 1、在官网下载opencv

链接：http://opencv.org/，下载后点击，如下：

​      ![img](https://img-blog.csdn.net/20180414113802908?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

​      随后弹出一个提示框，可不用管它，等一段时间，会解压出一个OpenCV文件夹，其中有如下几个文件：

​       ![img](https://img-blog.csdn.net/20180414114217764?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 2、环境配置

  依次点击，计算机  ->（右键）属性 -> 高级系统设置  -> 高级（标签） ->  环境变量 -> 在【系统变量】中找到“PATH”，然后双击，如图：

（1）

​       ![img](https://img-blog.csdn.net/20180414115410712?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

（2）

​         ![img](https://img-blog.csdn.net/20180414115538620?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

（3）

​           ![img](https://img-blog.csdn.net/20180414115728204?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

（4）添加路径：

​           ![img](https://img-blog.csdn.net/20180414120014737?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**32位系统添加：**

​             ........opencv\build\x86\vc11\bin （省略部分为你opencv文件夹所在路径）

​             ........opencv\build\x86\vc12\bin （省略部分为你opencv文件夹所在路径）

比如： D:\下载（软件，链接）\OPenCV\opencv\build\x86\vc12\bin

**64位系统添加：**

​            ........opencv\build\x64\vc11\bin （省略部分为你opencv文件夹所在路径）

​            ........opencv\build\x64\vc12\bin （省略部分为你opencv文件夹所在路径）

​             ........opencv\build\x86\vc11\bin （省略部分为你opencv文件夹所在路径）

​            ........opencv\build\x86\vc12\bin （省略部分为你opencv文件夹所在路径）

​            也就是说，x86和x64都可以添加上。

比如： D:\下载（软件，链接）\OPenCV\opencv\build\x64\vc12\bin

 **注：vc10对应vs2010，vc11对应vs2012 , vc12对应vs2013，要相对应才不会出错哦。**



## 3、VS包含目录设置

（1）打开VS，新建一个空项目，添加cpp文件（这一步省略哈，大家都会的~）

（2）依次点击【视图】->【属性管理器】，然后进行如图操作：

​        ![img](https://img-blog.csdn.net/20180414122324879?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

（3）  添加包含目录：

​         路径为：D:\下载（软件，链接）\OPenCV \opencv\build\include;

​                       D:\下载（软件，链接）\OPenCV\opencv\build\include\opencv;

​                       D:\下载（软件，链接）\OPenCV\opencv\build\include\opencv2; 

![img](https://img-blog.csdn.net/20180414122457902?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 ![img](https://img-blog.csdn.net/20180414152115644?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  4、 VS添加库目录：

​      接着上一步，点击【库目录】，如图：

![img](https://img-blog.csdn.net/20180414152412946?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
 添加路径为：  ............\opencv\build\x86\vc11\lib（省略部分为你opencv文件夹所在路径）

​                        .............\opencv\build\x86\vc12\lib（省略部分为你opencv文件夹所在路径

![img](https://img-blog.csdn.net/20180414152608597?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  5、 VS链接库配置：

 （1）依次点击【视图】->【属性管理器】->【连接器】->【输入】->【添加依赖项】，然后进行如图操作：

​        注，划重点：依赖项lib在  ...............opencv\build\x64\vc11\lib 、,,,,,,,,,,opencv\build\x64\vc11\lib文件夹下

​         ![img](https://img-blog.csdn.net/2018041415373369?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)


![img](https://img-blog.csdn.net/20180414154344202?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

   大家会发现有4个压缩包，他们的区别在于：300.lib 和 300d.lib。 将 带有 d 的添加在debug中，不带d的添加在Release中，如图：

​                ![img](https://img-blog.csdn.net/20180414154459209?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)


   至此全部的安装配置就完成了。

##  6、 最终测试：

（1）随便放一张图片在你刚刚新建的VS工程目录下（若不添加，会报错，中断......等等）。

（2）测试程序：

```cpp
#include<iostream>  
#include <opencv/cxcore.hpp>  
#include <opencv2/highgui/highgui.hpp>  

using namespace cv;  

int main()  

{  
    // 读入一张图片  
    Mat img=imread("PIC.jpg");  

    // 创建一个名为 唯美原画"窗口  
     namedWindow("唯美原画");  

    // 在窗口中显示唯美原画  
    imshow("唯美原画",img);  

     waitKey();//若无此语句，则不能正常显示图像

	 return 0;
}  
```

（3）点击运行，会显示图像：

![img](https://img-blog.csdn.net/20180414155853522?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDY0NzgxOQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)