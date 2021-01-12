

# SpringBoot入门

## 创建maven工程

1. 新建一个Module文件。![1585761100367](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\1585761100367.png)

2. 选择maven。![1585761141791](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\1585761141791.png)

3. 输入GroupId和ArtifactId。一般GroupId以"com."开始。![1585761320623](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\1585761320623.png)

4. 单击"Next"后自动生成Module name等，也可以自己修改。![1585761409782](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\1585761409782.png)

5. 创建完成。![1585761494787](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\1585761494787.png)

   

## 添加SpringBoot的起步依赖

1. SpringBoot要求，项目要继承SpringBoot的起步依赖spring-boot-starter-parent

   ```xml
   <parent>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-parent</artifactId>
       <!--SpringBoot版本号-->
       <version>2.0.1.RELEASE</version>
   </parent>
   ```

   

2. SpringBoot要集成SpringMVC进行Controller的开发，所以项目要导入web的起步依赖。

   ```xml
   <dependencies>
       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-web</artifactId>
       </dependency>
   </dependencies>
   ```

   

## 编写SpringBoot引导类

要通过SpringBoot提供的引导类起步的SpringBoot才可以进行访问。

1. 在\src\main\main\java目录下创建Java文件。![image-20200402195815523](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200402195815523.png)

2. 编写代码。

   ```java
   package com.test;
   
   import org.springframework.boot.SpringApplication;
   import org.springframework.boot.autoconfigure.SpringBootApplication;
   import org.springframework.web.bind.annotation.ResponseBody;
   
   @SpringBootApplication
   public class MySpringBootApplication {
   
       public static void main(String[] args) {
           SpringApplication.run(MySpringBootApplication.class);
       }
   }
   
   ```

3. 点击运行。![image-20200402221821744](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200402221821744.png)

4. 启动成功。![image-20200402221929343](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200402221929343.png)

5. 此时，在浏览器中输入localhost:8082，即可看到网页。（8082为端口号）![image-20200402222027598](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200402222027598.png)

## 注：更改端口号。

1. 在resources文件目录下，创建新File，命名为application.yml。![image-20200402222445972](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200402222445972.png)

2. 向文件中键入代码。

   ```html
   server:
     port: 8082
   ```

   8082为所使用的端口号。

## 编写Controller

在引导类MySpringBootApplication同级包或者子级包中创建QuickStartController。

1. 创建Java文件。![image-20200402223700363](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200402223700363.png)

2. 编写代码。

   ```java
   package com.test.controller;
   
   import org.springframework.boot.autoconfigure.SpringBootApplication;
   import org.springframework.stereotype.Controller;
   import org.springframework.web.bind.annotation.RequestMapping;
   import org.springframework.web.bind.annotation.ResponseBody;
   
   @Controller
   public class QuickController {
   
       @RequestMapping("/quick")
       @ResponseBody
       public String quick(){
           return "Hello World!";
       }
   }
   ```

3. 重启工程。

4. 在浏览器中访问localhost:8082/quick。![image-20200402224518284](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200402224518284.png)

## SpringBoot工程热部署

我们在开发中反复修改类、页面等资源，每次修改后都是需要重新启动才生效，这样每次启动都很麻烦，浪费了大量时间，所以我们可以在修改代码后不重启就能生效，在pom.xml中添加如下配置就可以实现这样的功能，我们称之为热部署。

在<dependencies>中添加代码：

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
</dependency>
```

## 注：IDEA热部署失败解决方案

出现这种情况，并不是热部署配置问题，其根本原因是因为Intellij IDEA默认情况下不会自动编译，需要对IDEA进行自动编译的设置。

1. 选择File -> Settings... ![image-20200404141604767](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404141604767.png)
2. 选择Build, Execution, Deployment -> Compiler，勾选Build project automatically。![image-20200404141822171](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404141822171.png)
3. 使用快捷键Shift+Ctrl+Alt+/，选择Registry...。![image-20200404142521085](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404142521085.png)
4. 勾选complier.automake.allow.app.running，单击Close。![image-20200404145138657](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404145138657.png)
5. 热部署完成。修改代码后只需Ctrl+F9刷新即可，无需重新启动。

## IDEA快速创建SpringBoot项目

1. 新建Module。![image-20200404145712373](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404145712373.png)
2. 选择Spring Initializr。![image-20200404145739751](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404145739751.png)
3. 设置Group和Artifact。![image-20200404150004023](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404150004023.png)
4. 勾选功能，自动生成坐标。（勾选Web -> Spring Web）![image-20200404150201149](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20200404150201149.png)
5. 设置名称及路径。创建完毕。