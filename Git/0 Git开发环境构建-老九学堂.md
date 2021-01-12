# Git开发环境构建

## 主要内容

1. 安装Git客户端和界面操作工具
2. 配置Eclipse Git插件
3. 使用Git插件导入GitHub中的Java项目
4. 使用Git插件构建Git仓库，并发布到GitHub

## Git简介

Git是目前世界上最先进的分布式版本控制系统。

​	版本控制是指对软件开发过程中各种程序代码、配置文件及说明文档等文件变更的管理，是软件配置管理的核心思想之	一。

**Git的优点**

1. 适合分布式开发，每一个个体都可以作为服务器。每一次Clone就是从服务器上pull到了所有的内容，包括版本信息。
2. 公共服务器压力和数据量都不会太大。
3. 速度快、灵活，分支之间可以任意切换。
4. 任意两个开发者之间可以很容易的解决冲突，并且单机上就可以进行分支合并。
5. 离线工作，不影响本地代码编写，等有网络连接以后可以再上传代码，并且在本地可以根据不同的需要，本地新建自己的分支。

其他版本的控制系统

​	VSS作为 Microsoft visual studio的一名成员，它主要任务就是负责项目文件的管理。

​	Subversion是一个开放源代码的版本控制系统，相较于RCS、CVS，它采用了分支管理系统，它的设计目标就是取代	CvS3

Git的前世今生

​	一个只用2周时间完成的分布式版本控制系统。

![image-20200826141446621](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200826141446621.png)

## 安装Git客户端

```
Git客户端是我们操作Git核心，其他工具都需要依赖它执行相应的命令，所以要使用Git我们必须安装Git客户端，我们可以在Git官网下载最新的Git客户端。
```

[前往软件下载页面](https://git-scm.com/download/win)

![blob.jpg](https://i.loli.net/2019/07/11/5d26d16311b9033114.jpg)

下面我们来看一下它的安装步骤，首先双击安装包后，我们可以看到启动界面

![blob.jpg](https://i.loli.net/2019/07/11/5d26d9e9ba43d62155.jpg)

点击“Next”，进入选择安装路径界面

![blob.jpg](https://i.loli.net/2019/07/11/5d26da2b9472281613.jpg)

点击“Next”，进入选择组件界面，按照下图选择安装的组件

![blob.jpg](https://i.loli.net/2019/07/11/5d26da773b5b725336.jpg)

点击“Next”，进入设定开始菜单组界面，这个界面我们做任何调整

![blob.jpg](https://i.loli.net/2019/07/11/5d26db20dd62d45798.jpg)

点击“Next”，进入选择默认编辑器界面，这里我们使用Notepad++

![blob.jpg](https://i.loli.net/2019/07/11/5d26dbdff365d17693.jpg)

点击“Next”，进入环境变量设置界面，这里我们使用默认配置

![blob.jpg](https://i.loli.net/2019/07/11/5d26dd5a241b557990.jpg)

点击“Next”，进入传输协议选择界面，我们选择第一个选项

![blob.jpg](https://i.loli.net/2019/07/11/5d26ddb05450b17188.jpg)

点击“Next”，进入配置Git处理文件结尾的方式，我们使用默认设置

![blob.jpg](https://i.loli.net/2019/07/11/5d26deaada3db89778.jpg)

点击“Next”，进入配置终端使用的模拟器类型，我们使用Mintty

![blob.jpg](https://i.loli.net/2019/07/11/5d26df11c55cf46272.jpg)

点击“Next”，进入扩展项配置界面，我们使用默认配置即可

![blob.jpg](https://i.loli.net/2019/07/11/5d26df7102afe25090.jpg)

点击“Next”，进入安装过程界面，安装完成后，可以看到安装接收界面

![blob.jpg](https://i.loli.net/2019/07/11/5d26dfa5c446732016.jpg)

点击“Finish”,此时会打开一个Git终端，到此git客户端安装完成，喜欢使用命令行的小伙伴，可以在终端上完成Git相关操作了

## 安装TortoiseGit

```
如果完全使用命令行操作Git势必影响我们的操作效率，而且应对复杂的操作，比如解决冲突，非常困难，很幸运的是在互联网上提供了许多GUI工具，当然Git客户端也自带有UI工具，但是不怎么好用。在这里我们选择使用TortoiseGit这一款GUI工具，非常好用，而且使用过TortoiseSVN的小伙伴一定会钟情于它。
```

[前往软件下载页面](https://tortoisegit.org/download/)

下载这个工具，我们需要下载两个安装包，一个是工具基础包、一个语言包，当然如果你的英文OK，就可以不用在安装语言包了，下图显示了我们需要下载软件包

![blob.jpg](https://i.loli.net/2019/07/11/5d26f19590d3e40798.jpg)

下面是它的安装过程截图，我们的安装顺序是先安装核心软件包，再安装语言包

![blob.jpg](https://i.loli.net/2019/07/11/5d26f20171e7667482.jpg)

![blob.jpg](https://i.loli.net/2019/07/11/5d26f2993c64e47575.jpg)

![blob.jpg](https://i.loli.net/2019/07/11/5d26f220dfb2965496.jpg)

下面是语言包安装完成的截图

![blob.jpg](https://i.loli.net/2019/07/11/5d26f5d093cb741077.jpg)

## Fork

下面我们来演示一下如何从GitHub中clone一个git仓库（以JavaBase为例）

**1 登录GitHub,登录地址**

**2 搜索JavaBase这个项目**

![blob.jpg](https://i.loli.net/2019/07/11/5d26f88f181c013758.jpg)

或者直接定位到 https://github.com/ljxt-ExtremeAcademy/JavaBase

**3 fork JavaBase项目**

![blob.jpg](https://i.loli.net/2019/07/11/5d26f8aa1718c33027.jpg)

**4 获取clone地址**

![blob.jpg](https://i.loli.net/2019/07/11/5d26fb35ef94b53600.jpg)

**5 pull JavaBase项目到本地**

首先我们在本地磁盘中新建一个文件夹用于存放所有的git仓库文件，然后使用TortoiseGit工具clone远程仓库，操作方式如图所示

![blob.jpg](https://i.loli.net/2019/07/11/5d26fa65b736b50477.jpg)

在打开的clone窗口中，输入远程仓库的地址

![blob.jpg](https://i.loli.net/2019/07/11/5d26faee217a390638.jpg)

点击“确认”按钮，开始clone

![blob.jpg](https://i.loli.net/2019/07/11/5d26fc03a9e4325102.jpg)

等待clone完成后我们就可以进入目录查看相关内容了

## GitHub中创建自己的仓库

通过前面的步骤我们已经可以实现clone GitHub上的开源项目了，但是我们需要使用GitHub来搭建一个提供给自己团队开发的仓库，此时我们就需要在GitHub创建一个仓库了，下面是创建的步骤。
 首先在浏览器的窗口的右上角，我们可以找到创建仓库的入口

![blob.jpg](https://i.loli.net/2019/07/11/5d26fde0108d948277.jpg)

打开创建仓库页面，然后输入仓库名称，选中ReadMe选项

![blob.jpg](https://i.loli.net/2019/07/11/5d26fe3bbf9bd20804.jpg)

当然在这里我们使用的公有仓库，它是免费的，如果需要创建私有仓库，需要完成相应的付费操作。

## 推送

编写完代码后，我们需将代码推送至GitHub网站。

右键项目文件夹，单击“Git提交(C) -> "master"...”

![image-20200826211916487](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200826211916487.png)

填写日志信息，单击“提交”。

![image-20200826213202545](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200826213202545.png)

![image-20200826213227752](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200826213227752.png)

再单击“TortoiseGit(T)”，选择“推送(H)”。

![image-20200826212050117](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200826212050117.png)

登录后单击“确定”即可提交代码。

![image-20200826213407690](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200826213407690.png)

## 在Eclipse中导入本地仓库

首先讲解本地导入的步骤
 **1 首先使用TortoiseGit工具将刚才建立的空仓库clone到本地**

**2 打开Eclipse配置Git用户**
 打开Eclipse首选项菜单，然后找到git的配置节点，点击Add Entry，添加两个Key

![blob.jpg](https://i.loli.net/2019/07/11/5d2700664cbf645618.jpg)

![blob.jpg](https://i.loli.net/2019/07/11/5d2700914207614421.jpg)

添加完成后

![blob.jpg](https://i.loli.net/2019/07/11/5d2700a820e2413615.jpg)

**3 使用Eclipse向导初始化仓库**
 选择File->Improt打开导入向导界面，选择Git

![blob.jpg](https://i.loli.net/2019/07/11/5d270171c73a323737.jpg)

选择“Next”，进入资源类型选择页面，我们选择本地仓库

![blob.jpg](https://i.loli.net/2019/07/11/5d2701c269bb046704.jpg)

选择“Next”，选择刚才clone的仓库所在位置

![blob.jpg](https://i.loli.net/2019/07/11/5d27021c6973120114.jpg)

选择“Next”，进入项目向导选择界面，我们选择最后一个选项

![blob.jpg](https://i.loli.net/2019/07/11/5d2702637234799738.jpg)

导入完成后我们设置项目类型，将普通项目转换成Java项目

![blob.jpg](https://i.loli.net/2019/07/11/5d2702e46987a37233.jpg)

![blob.jpg](https://i.loli.net/2019/07/11/5d2702fc3a24966990.jpg)

转换完成后，我们可以看到当前项目的结构和Java项目结构已经一致了

![blob.jpg](https://i.loli.net/2019/07/11/5d270339ca99b69904.jpg)

**4 提交修改到GitHub中心仓库**
 在项目根目录中鼠标右键中选择->Team->Add to Index,这样就可以吧所有文件添加到待提交列表了

![blob.jpg](https://i.loli.net/2019/07/11/5d2704290ae0280572.jpg)

然后我们提交待提交列表到本地仓库，并push到中心仓库
 在项目根目录中鼠标右键选择->Team->Commit,打开提交信息界面。

![blob.jpg](https://i.loli.net/2019/07/11/5d2704af4773879233.jpg)

输入提交日志，然后点击“Commit and Push”按钮，完成提交，当然此时提交会提示我们输入GitHub的账号和密码

![blob.jpg](https://i.loli.net/2019/07/11/5d27051f0199935275.jpg)

提交完成后我们可以在GitHub查看刚提交的文件了

## 其他成员pull刚才提交的项目

**1 在Eclipse中设置用户信息**（当然刚才已经配置了，如果没有配置需要手动配置）
 **2 搜索组长创建的项目**（项目名称：Kenny-JiaoTou/GitTest）
 **3 在GitHub上fork该项目**
 **4 使用Eclipse导入这个项目**
 依次选择菜单：Import -> Git -> Projects from Git -> Clone URI,然后打开路径填写界面

![blob.jpg](https://i.loli.net/2019/07/11/5d2707b07d56e80229.jpg)

输入clone地址，然后输入github的账号和密码，点击“Next”,进入仓库文件保存路径设置界面

![blob.jpg](https://i.loli.net/2019/07/11/5d27081ab115795396.jpg)

点击“Next”，此时会自动clone仓库到本地,clone完成后，我们将其导入到Eclipse中

![blob.jpg](https://i.loli.net/2019/07/11/5d270874336c931972.jpg)

点击“Next”，按照默认向导执行操作，最后我们可以成功的导入项目

![blob.jpg](https://i.loli.net/2019/07/11/5d2708dcee8a481564.jpg)

导入成功后的项目，我们进行代码修改

![blob.jpg](https://i.loli.net/2019/07/11/5d2708fe596c385477.jpg)

**5 提交修改代码**
 我们可以使用Eclipse向导将项目提交到中心仓库

![blob.jpg](https://i.loli.net/2019/07/11/5d270940ad19c29971.jpg)

由于我们使用的组员账号，所以提交到GitHub上，并没有将代码合并到主项目中，因此需要组员发起push更新申请，在GitHub网站上找到“New pull request”选项，如下图所示：

![blob.jpg](https://i.loli.net/2019/07/11/5d271556055b298139.jpg)

点击“New pull request”按钮后，跳转到创建申请确认页面，此时只需点击“Create pull request”按钮，填写日志，然后提交就可以完成申请创建

![blob.jpg](https://i.loli.net/2019/07/11/5d2716471fd9180103.jpg)

申请创建完成后，我们可以发个邮件或发个QQ消息通知组长审核

## 组长审核pull更新申请

组员创建了更新申请，组长可以在GitHub中看到申请的数量，如下图所示

![blob.jpg](https://i.loli.net/2019/07/11/5d271a15001bd93369.jpg)

点击“Pull request”,组长可以处理更新申请，比如下面是老九君提交的申请

![blob.jpg](https://i.loli.net/2019/07/11/5d271b5891c0680655.jpg)

点击申请列表项，就会打开合并确认页面，如下图所示

![blob.jpg](https://i.loli.net/2019/07/11/5d27213deb15b59582.jpg)

点击“Merge pull request”按钮,然后书写日志，提交就可以完成合并处理，同时完成申请处理，然后我们在来观察项目，就会发现老九君修改的代码了

![blob.jpg](https://i.loli.net/2019/07/11/5d271f7c6e01d22671.jpg)

组长需要再次进入到本地仓库，执行拉取最新仓库修改操作，当然也可以在Eclipse执行pull操作，比如

![blob.jpg](https://i.loli.net/2019/07/11/5d27203ef1e8a22477.jpg)



[^注]: 本文部分内容来源于老九Wiki。
