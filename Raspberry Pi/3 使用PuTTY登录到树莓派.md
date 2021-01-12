# **使用PuTTY登录到树莓派**

装有Linux的树莓派，和普通计算机一样。所有操作都可以通过电脑的远程登录完成。通过VNC可以登录到树莓派的桌面环境，而通过SSH可以操作树莓派的命令行。

**开启SSH**
事实上最新的Raspbian 2012-10-28已经默认启动了SSH支持，无需特意开启。（[2016.11起新系统需要通过这个方法开启SSH服务](https://shumeipai.nxez.com/2017/02/27/raspbian-ssh-connection-refused.html)）
如果因为各种原因，系统没开启SSH服务（从旧系统升级，曾经特意关掉等），可通过sudo raspi-config启用或禁止SSH。

**登录SSH**
登录SSH的唯一推荐工具是PuTTY。（Tunnelier (Bitvise SSH Client)也是好工具，但无奈中文乱码无法解决而不建议）
PuTTY 下载：[putty.zip](http://pan.baidu.com/share/link?shareid=2217335081&uk=605377859)

打开PuTTY，输入树莓派的IP地址即可登录。
![20130907142345250](https://shumeipai.nxez.com/wp-content/uploads/2013/09/20130907142345250.png)
首次登录会和您确认连接密钥，请按“是”确认。只有首次登录会出现这个提示。
![20130907142345398](https://shumeipai.nxez.com/wp-content/uploads/2013/09/20130907142345398.png)
登录后会提示输入用户名和密码，输入之后即可登录树莓派的命令行。
（提示：Raspbian默认的用户名密码是pi/raspberry）
![20130907142345287](https://shumeipai.nxez.com/wp-content/uploads/2013/09/20130907142345287.png)

**推荐PuTTY中文版的原因**
就算您阅读英文毫无压力，我也推荐使用中文版的PuTTY。两点理由：
一、默认字体是更大字号、更容易看清的12px（小四）新宋体。
二、与英文原版不同，汉化版做了更改，默认即采用UTF-8编码进行通信。
这样无需任何设置，即可避免Linux命令行显示中文的乱码（变问号、变方块等）问题。

\* 如果您使用英文版PuTTY，碰到命令行的中文乱码，请调整连接选项的：
Window -> Translation，Remote character set改为“UTF-8”。
![20130907142345175](https://shumeipai.nxez.com/wp-content/uploads/2013/09/20130907142345175.png)

**树莓派的无显示器操作**
其实想要无显示器操作树莓派，只需要SD卡烧好系统之后，插卡开机，SSH登录即可。
如果不知道树莓派开机之后的IP地址请查看这篇文章：[没有显示器且IP未知的情况下登录树莓派](https://shumeipai.nxez.com/2013/09/07/no-screen-unknow-ip-login-pi.html)

另外提醒：新装系统SSH首次登录，不会出现第一次开机的[raspi-config设置](https://shumeipai.nxez.com/2013/09/07/raspi-config-configuration-raspberry-pie.html)程序。请用sudo raspi-config命令手工启动。

另外在PuTTY的第一个屏幕，可以使用“保存”按钮，把编辑好各种选项的连接，存成列表框里的一个条目。
下次连接时直接双击即可。