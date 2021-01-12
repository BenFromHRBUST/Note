# 小程序核心开发

## “徒手”创建小程序

1. 创建项目目录。

2. 按照以下文件目录结构创建文件。

   ---index

   ​	|--index.js

   ​	|--index.json

   ​	|--index.wxml

   ​	|--index.wxss

   ---app.js

   ---app.json

   ---app.wxss

3. 打开app.json，写入以下代码：

   ```json
   {
   	"pages": [
   		"mypages/index/index"
   	]
   }
   ```

   指定默认启动页面地址。

4. 打开index.wxml，写入以下代码：

   ```html
   <view bindtap="countClick">我是index页面，你点击了{{count}}次</view>
   ```

5. 打开index.js，写入以下代码：

   ```js
   page({
   	data: {
   		count: 0
   	},
   	countClick:function() {
           this.setData({
               count: this.data.count + 1
           });
   	}
   });
   ```

   

## 框架主体文件

### app.json

- pages：设置页面路径，必填项
- window：设置默认页面的窗口表现
- tabBar：设置tab的表现
- networkTimeout：设置网路超时时间
- debug：设置是否开启debug模式，默认关闭。

app.json文件内容整体结构如下：

```json
{
	// 页面路径设置
	"pages" : [ /* 路径+文件名 */ ],
	// 默认页面的窗口设置
	"window" : {},
	// 底部tab设置
	tabBar : {},
	// 设置网路请求API的超时时间
	"networkTimeout" : {},
	// 是否为debug模式
	"debug" : false
}
```

[^注]: JSON规范的代码中不包含注释，以上代码中的注释只为方便理解所添加

### app.js

#### 注册小程序

- onLaunch：生命周期函数，监听小程序初始化。当小程序初始化完成时，就会触发onLaunch，onLaunch事件全局只会触发一次。
- onShow：生命周期函数，监听小程序显示。当小程序启动，或者从后台进入前台显示时都会触发onShow。
- onHide：生命周期函数，监听小程序隐藏。当小程序从前台进入后台会触发。
- 其他：开发者可以添加任意的函数或数据到Object参数中，这些属性会被注册到小程序对象中，其他逻辑文件可以通过getApp()函数获取已注册的小程序实例。

#### 获取小程序实例

注册小程序后，在其他逻辑文件中，可以通过全局函数getApp()获取小程序实例，例如：

```js
var app = getApp();
console.log(app.globalData);
```

### app.wxss

(暂无笔记)

## 框架页面结构

- .js：页面逻辑文件。必要项
- .wxml：页面结构文件。必要项。
- .wxss：页面样式文件。
- .json：页面配置文件。

### .json - 页面配置文件

由于页面的json只能配置window相关属性，编写时只需直接写出属性，不用写window这个键。

```json
{
	"navigationBarBackgroundColor": "#000000",
	"navigationBarTextStyle": "black",
	"navigationBarTitleText": "我的页面",
	"backgroundColor": "#efefef",
	"backgroundTextStyle": "light"
}
```

### .js - 页面逻辑文件

主要功能：设置初始化数据，注册当前页面生命周期函数，注册事件处理函数。

#### 注册页面

```js
// 获取app实例
var app = getApp();
Page( {
    data : {
        // 页面初始化数据
        count : 0
    },
    onLoad : function() {
        // 页面加载时执行
    },
    onShow : function() {
        // 页面打开时执行
        console.log(app.globalData);
    },
    onReady : function() {
        // 页面初次渲染完成时执行，一个页面只会调用一次
    },
    onHide : function() {
        // 页面隐藏时执行
    },
    onUnload() : function() {
    	// 页面卸载时执行
	},
    onPullDownRefresh() : function() {
      	// 下拉刷新时执行  
    },
	onReachBottom() : function() {
        // 下拉触底时执行
    },
    // 自定义函数
    countClick : function() {
        // 触发视图层重新渲染
        this.setData( {
            count : this.data.count + 1
        } );
    }，
    // 自定义数据
    customData : {
        name : '微信'
    }
} );
```

小程序框架以栈的形式维护了当前的所有页面。

- 小程序初始化：默认页面入栈，依次触发默认页面onLoad、onShow、onReady方法。

- 打开新页面：新页面入栈，依次触发新页面onLoad、onShow、onReady方法。

- 页面重定向：当前页面出栈并卸载，触发当前页面onUnload方法。

  ​					  新页面入栈。触发新页面onLoad、onShow、onReady方法。

- 页面返回：页面不断出栈并卸载，触发当前弹出页面onUnload方法，直到返回目标页面。

  ​				  新页面入栈，触发新页面onShow方法。

- Tab切换：当前页面出栈但不卸载，仅触发onHide方法。

  ​				新页面入栈，如果当前页面是新加载的，触发onLoad、onShow、onReady方法，如果当前页面已加载过，仅触发onShow方法。

- 程序从前台到后台：触发当前页面的onHide方法，触发App onHide方法。

- 程序从后台到前台：触发小程序onShow方法，触发页面onShow方法。

#### 获取当前页面栈

```js
// 获取页面栈
var pages = getCurrentPages();
// 获取当前页面对象
var currentPage = pages[pages.length - 1];
```

#### 事件处理函数

.wxml代码

```html
<view bindtap="myevent">点击执行逻辑层事件</view>
```

.js代码

```js
page( {
	myevent : function() {
		console.log('点击了view');
	}
} );
```

#### 触发视图层渲染

.wxml代码

```html
<view>{{text}}</view>
<button bindtap="changeText">修改普通数据</button>

<view>{{object,subObject.objectText}}</view>
<button bindtap="changeObjectText">修改对象数据</button>

<view>{{array[0].arrayText}}</view>
<button bindtap="changeArrayText">修改数组数据</button>

<view>{{newField.newFieldText}}</view>
<button bindtap="addNewData">增加新字段</button>
```

.js代码

```js
page( {
    data : {
        text : 'normal data',
        object : {
            subObject : {
                objectText : 'object data'
            }
        },
        array : [
            { arrayText : 'array data'}
        ]
    },
    changeText : function() {
        this.setData( {
            // 普通索引
            text : 'new normal data'
        } );
    },
    changeObjectText : function() {
      	this.setData( {
            // 按路径索引
            'object.subObject.objectText' : 'new object data'
        } );  
    },
    changeArrayText : function() {
      	this.setData( {
            // 按路径索引
            'array[0].arrarText' : 'new array data'
        } );  
    },
    addNewData : function() {
        this.setData( {
            // 修改一个已绑定，但未在data中定义的数据
            'newField.newFieldText' : 'add new data'
        } );
    }
} );
```

### .wxml - 页面结构文件

#### 数据绑定

小程序的数据绑定使用Mustache语法（双大括号）将变量或简单的运算规则包起来。

##### 简单绑定

.wxml代码：

```html
<!--作为内容-->
<view>{{content}}</view>

<!--作为组件属性-->
<view id="item-{{id}}" style="border:{{border}}">作为属性渲染</view>

<!--作为控制属性-->
<view wx:if="{{showContent}}">"作为属性渲染"</view>

<!--关键字-->
<view>{{2}}</view>
<checkbox checked="{{false}}"></checkbox>
```

.js代码：

```js
Page({
  data : {
    border : 'solid 1px #000',
    id : 1,
    content : '内容',
    showContent : false
  }
})
```

运行如下：

![image-20201130002701367](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20201130002701367.png)

##### 运算

.wxml代码

```html
<!--算数运算符-->
<view>{{ num1 + num2 }} + 1 + {{num3}} = ? </view>

<!--字符串运算-->
<view>{{ "name : " + name }}</view>

<!--逻辑判断-->
<view>{{ num3 > 0}}</view>

<!--数据路径运算-->
<view>{{ myObject.age }} {{myArray[1]}}</view>
```

.js代码

```json
Page({
  data : {
    showContent : false,
    num1 : 1,
    num2 : 2,
    num3 : 3,
    name : 'weixin',
    myObject : {
      age : 12
    },
    myArray : ['arr1', 'arr2']
  }
})
```

运行如下：

![image-20201224224806047](C:\Users\13714\AppData\Roaming\Typora\typora-user-images\image-20201224224806047.png)

##### 组合

