# **最常用的树莓派 Linux 命令及说明**

对于 Linux 新手来说，使用 Raspbian 系统会遇到比较棘手的问题，其中之一就是对各种 Linux 命令的学习。下面树莓派实验室整理一份常用的 Linux 命令及说明，供初学者对照了解，后面我们也会逐步完善更新这个页面。

命令在哪里输入？
[通过 SSH 客户端登录你的树莓派](https://shumeipai.nxez.com/2013/09/07/using-putty-to-log-in-to-the-raspberry-pie.html)，或者进入树莓派的桌面运行终端程序，接下来就可以输入命令了。

什么是 sudo 命令？
在一行命令之前加上 sudo，表示以系统管理员身份执行这条命令。如果使用不当可能会造成事故，所以仅在特别需要使用管理员权限运行的时候添加。



#### **重启树莓派**

```
sudo reboot
```

重启树莓派，需要管理员权限才可以执行，因此添加 sudo。



#### **关机**

```
sudo poweroff
```

关机，需要管理员权限才可以执行。

```
sudo halt
```

关机。与 poweroff 不同的是，此命令会在关机前停止所有CPU功能。执行时，杀死应用进程、执行sync系统调用、文件系统写操作完成后就会停止内核。推荐使用这种方法关机。

```
sudo shutdown -h 03:14
```

定时关机，例如上面指令将设定关机时刻为凌晨3点14分。

```
sudo shutdown -h now
```

用定时关机命令立即关机。



#### **清除终端框内文字**

```
clear
```

清除终端上的文字。



#### **进入某目录**

```
cd /folder1/folder2
```

进入到目录 /folder1/folder2。



#### **进入当前用户主目录**

```
cd ~
```

进入到当前用户的主目录。



#### **列出当前位置的文件和目录**

```
ls -lha
```

列出当前位置的文件和目录，显示全部信息。如去掉后面的 -lha 则只列出文件名。



#### **查找文件**

```
sudo find / -name file.txt
```

查找文件名为 file.txt 的文件。

```
sudo find / -name file.txt -type f
```

查找文件名为 file.txt 的文件，仅查找文件。

```
sudo find / -name somedir -type d
```

查找文件名为 file.txt 的文件，仅查找目录。

```
sudo find / -name file.*
```

查找文件名为 file.* 的文件，星号为通配符。



#### **移动文件**

```
sudo mv ~/file /folder1/folder2/
```

将 ~/file 移动到 /folder1/folder2/。



#### **查看命令使用手册**

```
man command
```

查看命令的使用手册。command 替换成你想了解的任何命令。



#### **打开功能配置界面**

```
sudo raspi-config
```

打开树莓派功能配置界面。



#### **列出网络配置信息**

```
sudo ifconfig -a
```

列出树莓派的网络配置信息。



#### **ping**

```
ping 192.168.1.1
```

Ping 某个 IP。查看树莓派和这个 IP 的设备的连接状况。



#### **更新与升级软件**

```
sudo apt-get update
```

更新软件列表。

```
sudo apt-get upgrade
```

升级软件包。



#### **温度检测**

```
vcgencmd measure_temp
```

树莓派温度检测。

[^参考]: [http://shumeipai.nxez.com/2018/12/22/configure-raspberry-pi-audio-output-35mm-hdmi.html](https://links.jianshu.com/go?to=http%3A%2F%2Fshumeipai.nxez.com%2F2018%2F12%2F22%2Fconfigure-raspberry-pi-audio-output-35mm-hdmi.html)

