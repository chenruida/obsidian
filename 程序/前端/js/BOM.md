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

# JS执行机制
# location对象
# navigator 对象
# history 对象
