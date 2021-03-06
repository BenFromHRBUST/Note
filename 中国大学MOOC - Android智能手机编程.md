# 一、概述和开发环境搭建

## 1.1 导学

### 1.1.1 学习目标

1. 简述Android智能手机操作系统的发展历程以及Android智能手机操作系统的现状。
2. 熟记Android智能手机操作系统的系统架构和Android应用框架的四个组件。
3. 独立搭建Android的开发环境和设置开发环境中环境变量。
4. 基于Android开发环境创建项目，将创建的项目部署到模拟器中。

### 1.1.2 本单元主要学习以下内容

![img](https://edu-image.nosdn.127.net/F8E6A9B08FF5B4F0C7CA4B5B7155DFD7.jpg?imageView&thumbnail=890x0&quality=100)

  本单元主要介绍目前市场上智能手机的状况，着重分析了智能手机的特点；分析Android出现的背景、Android平台的优势以及Android本身的架构，同时介绍如何搭建Android开发环境以及Android虚拟设备（AVD）的创建和管理。

## 1.2 Android概述

### 1.2.1 智能手机的演变及趋势

1.  第一代手机：大哥大。
2.  第二代手机：功能机，短信、电话、简单娱乐商务。
3.  第三代智能手机：个人电脑的强大功能，GPS导航、高清摄像头的影音分享、强大丰富的第三方应用市场。（代表：2007年苹果公司iPhone产品。）

### 1.2.2 智能手机的演变趋势

1. 价格：越来越便宜
2. 性能：越来越强大
3. 功能：结合功能手机和电脑、PDA,GPS等
4. 出门必备品（使用频率大于电脑）
5. 手机终端娱乐化和商务化

### 1.2.3 智能手机操作系统的现状

- 三国逐鹿时代：IOS, Android, Windows Phone
- iPhone（IOS）占据市场高端， Android占据市场过7成份额； Windows Phone迎头赶上
- 智能手机普及率急速提高

### 1.2.4 智能手机的特点

1. 独立操作系统，支持强大的多任务处理
2. 可简洁方便地访问互联网，访问速度大幅提升
3. 物理键盘消失，触摸操作方
4. GPS和移动互联网的结合（LBS）
5. 丰富强大的应用商

> 什么是LBS？
> LBS：基于地理位置的服务（Location Based Service, LBS）它是通过电信移动运营商的无线电通讯网络或外部定位方式（如GPS）获取移动终端用户的位置信息，在GIS平台的支持下，为用户提供相应服务的一种增值业务。

### 1.2.5 Android智能手机系统

​	由Google公司基于Linux的开源智能手机操作系统开发而成，自2008年发布第一个版本，至今已经发布了11个版本，是目前最流行和用户群最广的智能手机系统。

### 1.2.6 Android智能手机系统的优势

1.  开源，免费，允许其他厂商定制手机
2.  Google公司支持，升级频率快
3.  众多厂商参与，性价比高，新手机更新快
4.  拥有最大用户群体，满足不同人群需求
5.  基于Java开发语言，应用开发门槛低
6.  应用开发前景广阔

### 1.2.7 Android系统架构

1.  应用程序（Application）
2.  应用程序框架（Application Framework）
3.  本地框架类库（Libraries）和Java在Android上的运行环境
4.  Linux内核和驱动

Android系统架构-应用层

- 和用户交互的应用
- 如：桌面（Home）联系人（ Contacts）拨打电话（ Phone）浏览器（ Browsers）
- 应用开发者做的工作就在应用层

Android系统架构-应用框架层

- 开发者提供了调用 Android基本功能和手机硬件系统的应用程序接口（API），系统提供的开箱即用的应用界面组件

Android系统架构-本地框架和Java运行环境

- 基于 Linux内核开发的涉及底层的基础系统功能（活动管理器等）
- 运行 Android应用的Dalk虚拟运行环境

Android系统架构- Linux核心系统服务

- 涉及到硬件相关的底层服务，基于 -Linux内核的核心系统功能
- 安全性、内存管理、进程管理、网络堆栈、硬件驱动程序管理

### 1.2.8 Activity活动与 Service服务

Android的四大应用组件  

- Android的四大应用组件为Activity（活动）、Service（服务）、Broadcast Receiver（广播接收器）、Content Provider（内容提供者）。

#### Activity

1.  Activity展现为可视化用户界面，提供程序与用户交互的窗口
2.  一个Activity占据当前的窗口，响应所有窗口事件，具备控件、菜单等界面元素
3.  为保持各界面状态，Activity需要保存数据和调用系统功能、妥善管理生命周期和实现界面之间的跳转逻辑等
4.  对于开发者而言，一般创建Activity的子类，在其基础上定义界面布局、添加业务逻辑等

#### Service

1.  运行在后台的一个组件
2.  封装有完整的功能逻辑实现，像没有界面的Activity
3.  一般用于执行长时间运行的操作，且不需要提供用户界面的操作。如，后台下载，后台播放音乐等
4.  通过Intent与其他组件进行通信
5.  支持同步和异步的消息机制

### 1.2.9 Android广播机制

#### Broadcast Receiver-广播接收者

​	Broadcast Receiver是对发送出的广播进行过滤接收并响应的一类组件，通过它实现了组件之间异步的消息通信

#### Content Provider-内容提供器

1.  每个Android应用独立运行，通过它存储并检索数据并向其他应用程序提供访问数据的接口。
2.  Android系统提供诸多功能的Content Provider，比如：音频文件、视频、图片和私人通讯录等。

#### Intent-组件互相调用的相关信息

1.  负责在不同的组件之间传递消息，包含具体请求信息的对象
2.  系统中协助完成应用间的交互调用与通讯的一种机制

### 1.2.10Android面临的挑战

1. 不同厂商Android手机差异较大，缺乏统一用户体验和客户认知度
2. 频繁兼容升级带来的接口性问题
3. Android手机屏幕和硬件的配置繁杂，导致应用开发成本和测试成本偏高
4. Android自身版本的分裂（2.3 vs 4.x）