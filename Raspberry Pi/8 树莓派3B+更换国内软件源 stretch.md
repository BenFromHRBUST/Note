# **树莓派3B+更换国内软件源**

树莓派官方软件源链接：https://www.raspbian.org/RaspbianMirrors

经之前的测试，树莓派3B+已经装不起Jessie版本的系统了，只能使用最新的stretch版本。所以对应更新软件源也要换为stretch版本。

以清华大学软件源为例：

打开sources.list文件[（Linux下nano编辑器的使用](https://blog.csdn.net/m0_37509650/article/details/86606593)）

```
sudo nano /etc/apt/sources.list
```

将内容替换如下

```
deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ stretch main contrib non-free rpi
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ stretch main contrib non-free rpi
```

然后更新升级一下就是了

```
sudo apt-get update    #如果出现错误，重复执行一次
sudo apt-get upgrade   #这一步不是必须的，且比较耗时，可以选择跳过
```

如果想用其他源，将代码中的网址更换一下就好了，截下国内官方源的图：

![https://www.raspbian.org/RaspbianMirrors](https://img-blog.csdnimg.cn/20181230184625910.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3NTA5NjUw,size_16,color_FFFFFF,t_70)

 