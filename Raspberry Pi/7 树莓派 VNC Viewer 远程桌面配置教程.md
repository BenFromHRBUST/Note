# **树莓派 VNC Viewer 远程桌面配置教程**

在开始之前，你需要已经登录树莓派，进入到树莓派命令窗口，通过接上显示器和键鼠直接操作或[通过 SSH 登录](https://shumeipai.nxez.com/2013/09/07/using-putty-to-log-in-to-the-raspberry-pie.html)都可以。



### 启用树莓派 VNC 服务

在终端输入以下命令进入配置界面。

```
sudo raspi-config
```

![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054318-0.jpg)
 依次操作：Interfacing Options -> VNC -> Yes。之后系统会提示你是否要安装 VNC 服务，输入 y 之后回车，等待系统自动下载安装完成，一切顺利的话 VNC 服务就启动了！

![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054946-0.jpg)
 ![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054665-0.jpg)
 ![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054276-0.jpg)
 ![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054799-0.jpg)
 ![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054860-0.jpg)

### 安装 VNC 客户端

下面去 RealVNC 官网下载 [RealVNC Viewer](https://www.realvnc.com/en/connect/download/viewer/)，它是 RealVNC 的客户端，跨平台。下载你需要的平台的客户端版本即可。

https://www.realvnc.com/en/connect/download/viewer/

![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163236655-0.jpg)

### 登录远程桌面

运行 RealVNC Viewer 之后输入树莓派的 IP 地址，通过 ifconfig 命令可以查看。选择连接之后输入树莓派的登录用户名密码，初始用户名 pi，密码为 raspberry。确认之后即可进入树莓派的远程桌面！

![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054701-0.jpg)

![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054473-0.jpg)

![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054227-0.jpg)

![img](https://shumeipai.nxez.com/wp-content/uploads/2018/08/20180831163054488-0.jpg)

如果要修改树莓派的分辨率，[可以在终端运行 sudo raspi-config 进入设置界面设置操作](https://shumeipai.nxez.com/2019/07/08/set-the-resolution-of-the-raspberry-pi-vnc.html)。