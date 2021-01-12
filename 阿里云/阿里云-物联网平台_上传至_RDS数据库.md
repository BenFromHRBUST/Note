# **阿里云物联网平台上传至RDS数据库**

[^笔记来源]: https://blog.csdn.net/qq_43251032/article/details/90445633

**准备条件：**
 1.已开通阿里云账户并开通了物联网平台。*账号的开通利用支付宝、手机号、淘宝号都行的，开通成功后为了不影响后续的使用，最好来个实名认证。*
 2.这次使用的将物联网数据平台上报到云端MySql上，所以前提要购买好RDS里的MySql产品,对于新用户，阿里云官网给了一个一个月的ECS服务器与MySql的免费试用，地址：https://free.aliyun.com/ntms/free/personal.html?handle=true。*当然要注意的是你是企业新用户，还是个人新用户。*
 下面就是相应的步骤，这不仅是为大家提供了的一点帮助，同时也是自己的一个笔记吧，怎么说都是耽误了自己的时间完成的，对吧。

##  **一、进入阿里云平台创建一个产品并添加一个设备**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522141914742.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
为了方便测试，我们在这里创建Alink  JSON格式的产品，名称自己定，其他默认。如果有需要用到透传格式的产品，遇到问题可以问我。进入产品详情页面根据箭头所指方向添加用来测试的属性，这里我们自定义添加，因为感觉系统自带属性的数据类型不人性化。。。下面是我先前创建好的
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/2019052214314013.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522143154370.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 上面步骤完成后，我们在去为产品添加一个设备，添加设备是一件很容易的事情，这里的产品选择刚刚创建好的产品。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522143742599.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)

##  **二、登录RDS控制台**

 如果已经购买好了，那么在RDS控制台就会多出一个购买后的实例，控制台链接：https://rdsnext.console.aliyun.com/
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019052214521150.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 进入管理页面，会看到它的一些信息，外网需要点击手动申请才会生成
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522145548565.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 在这里右侧导航栏是该产品的操作关键
 1.账号管理：为我们平时使用的数据库，创建最高权限用户root等。
 2.数据库管理：创建一个数据库，字符集设置成utf-8
 3.数据安全性：为数据库的白名单，只有在白名单里的ip才能访问这个数据库。这里默认为127.0.0.1指一切外网不可链接，0.0.0.0/0指所有网都可以链接。物联网平台链接的ip有（官网文档上有）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522150529354.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 4.其他导航暂不需了解
 以上步骤完成后我们，我们点击登录数据库
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522150736261.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 这里需要我们对其授权，那我们就根据提示对它授权便是了。
 授权成功后呈现出以下画面：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522151010275.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 或是这个画面：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522151327238.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 如果是这个界面那么上面的三个数据库，你只最上面的两个测试的。我们点击左侧导航栏RDS(Alink通用DB),进行授权后的数据库登录，进入到如下我们非常熟悉的页面：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522151711292.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 我们要打开刚刚创建好的数据库就行了。
 数据库的使用部分就先说到这，接下来我们又要回到物联网平台进行规则引擎的数据流转操作了。

##  **三、规则引擎**

 如果你懂点sql语句，那么你对规则引擎的句式编写也不会陌生的。进入规则引擎页面，点击创建一个规则引擎，一个规则引擎的组成分为以下三个部分:
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522152605908.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 第一部分：数据的来源
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019052215331556.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 字段的编写，可以根据Alink的数据流转进行编写，如下是阿里云的一张数据流转过程：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522153549207.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 数据的来源，我们选择系统自定义，设备属性的上报进行获取。可参考我的代码：

```mysql
SELECT deviceName() as deviceName,timestamp('yyyy-MM-dd HH:mm:ss') as timestamp,items.temperature.value as temperature,items.humidity.value as humidity FROM "/sys/a1jhwQkAWDQ/zh_demo01/thing/event/property/post"
```

第二部分：数据发往至哪里
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522153902552.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 注意：选择操作：选择RDS\RDS实例名填写正确，具体位置在你的RDS控制台中查看、数据库名表名字段名对应、键为数据库字段、值为上面定义的值并用’${}'括起来，这是格式，第三部分暂时没加进去，不影响。最后启动规则引擎。

##  **四、模拟数据、测试上报数据**

 1.进入物联网平台中监控运维中的在线调试
 2.选择对应的产品与设备，填写对应的模拟数据
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522155016893.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 3.进入日志服务，点击上行消息，观察有没有报错
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522155059765.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)
 4.如果没有报错，那么MDS的数据控制台中就把刚刚推送的数据上报了过来
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190522155210115.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUxMDMy,size_16,color_FFFFFF,t_70)