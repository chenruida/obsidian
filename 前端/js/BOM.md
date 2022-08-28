# 概述
browser object model 浏览器交互模型，与浏览器窗口进行交互
- 核心对象是 widow
- 缺乏标准
- 比DOM更大，包含DOM
![](https://raw.githubusercontent.com/chenruida/image/master/202208032047433.png)

# Window 对象
浏览器的顶级对象，具有双重角色
- JS访问浏览器窗口的一个接口
- 全局对象。定义在全局作用域中的变量、函数都会变成window对象的属性和方法
## 常见事件
### 窗口加载事件
`window.onload = function(){}`
`window.addEventListener("load",function(){})`
1. 传统注册方式只能写一次，如果有多个，会以最后一个window.onload为准
``window.addEventListener("DOMContentLoad",function(){})``
仅当DOM加载完毕，不包括样式表、图片、flash
### 调整窗口大小
`window.onresize = function(){}`
`window.addEventListener("resize",function(){})`
只要窗口大小发生像素变化,就会触发事件
# 定时器
### setTimeout()
`window.setTimeout(调用函数,[延迟的毫秒数])`
定时器很多时，经常给定时器加标识符
回调函数，需要等待才调用
### setInterval()
`window.setInterval() `
### 停止定时器
`setTimeOut(function(){},5000)`

# this 指向
1. 全局函数或者普通函数中this指向 window
2. 定时器里的this指向Window
3. 方法调用中，谁调用指向谁
4. 构造函数中，this指向构造函数实例
# JS执行队列
单线程语言，同时只能做一件事
异步同步，在同一流水线执行顺序不同
## 执行顺序
1. 先执行同步队列栈中的同步任务
2. 异步任务（回调函数）放到任务队列中
3. 一旦同步队列栈中的任务执行完成后，系统按次序读取异步任务队列中的任务，被读取的异步任务结束等待状态，进入队列栈，开始执行
![](https://raw.githubusercontent.com/chenruida/image/master/202208071004911.png)
 ## 同步任务
同步任务在主线程的==执行栈==中
## 异步任务
异步任务通过回掉函数实现
有三类：
1. 普通事件，click、resize等
2. 资源加载，如load、error等
3. 定时器，setTimeout、setInterval
# location对象
window下的对象，设置获取解析url
![](https://raw.githubusercontent.com/chenruida/image/master/202208071011212.png)
# navigator 对象
navigator 包含浏览器的信息，使用userAgent 判断是什么终端
# history 对象
![](https://raw.githubusercontent.com/chenruida/image/master/202208071444464.png)

