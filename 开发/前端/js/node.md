# node

## Node.js 是什么

- Node.js 不是一种语言

- Node.js 不是库、不是框架

- Node.js是一个JavaScript 运行时的环境

- 简单点来讲就是 Node.js可以解析和执行Javascript 代码

  ## 浏览器中JavaScript

  - Ecmascript
    - 基本语法
    - if
    - var
    - function
    - objec
    - array
  - BOM
  - DOM

- Node 中的JavaScript ==没有BOM和DOM==

- 服务器级别的操作API

  - 文件读写
  - 网络服务的构建
  - 网络通信
  - http通信

# 模块化
## 分类
1. 内置模块
2. 自定义模块
3. 第三方模块
## 加载模块
```js
const fs = require('fs')
const custom = require('./custom.js')
const moment = require('moment')
```
## 模块作用域
在自定义模块中定义的变量、方法等成员，只能在当前模块中被访问，这种模块级别的访问限制，叫做模块作用域
### 好处
1. 防止全局变量污染
## 向外共享模块作用域中的成员
### module对象
存储当前模块的有关信息
![](https://raw.githubusercontent.com/chenruida/image/master/20220827212149.png)
### module.exports对象
共享成员
外界使用require()方法得到就是module.exports所指向的对象

### 注意点
使用require()导入模块时，导入结果，==永远以module.exports指向的对象为准==，和exports对象冲突时

### exports对象
默认情况下，exports和module.exports所指向的对象为同一个
![](https://raw.githubusercontent.com/chenruida/image/master/20220827213037.png)

## 模块化规范
1. 每个模块内部，module变量代表当前模块
2. module变量是一个对象，他的exports属性是对外的接口
3. 加载某个模块时，其实加载该模块的module.exports属性。require（）方法用于加载模块
## 加载机制
1. 模块第一次加载会被缓存
2. 内置模块加载级别最高
3. 自定义模块必须制定以`./`或者`../`开头的路径标识符
4. 如果省略了文件扩展名
	1. 确切的文件名
	2. .js扩展名加载
	3. .json扩展名加载
	4. .node扩展名加载
5. 如果没找到相应的第三方模块，则移动到再上一层父目录加载，直到文件系统的根目录
6. ![](https://raw.githubusercontent.com/chenruida/image/master/202208272232147.png)



# 包
## 规范
1. 必须单独的目录存在
2. 包的顶级目录下必须包含package.json这个包管理配置文件
3. package.json必须包含name，version，main这三个属性代表包的名称、版本号、包的入口
4. 
