# DOM
document object model 文档模型
W3C
## DOM树
文档：一个页面就是一个文档，用document来表示
元素：所有的标签都是元素，用element来表示 
节点：所有的内容（标签、属性、文字）都可以用节点表示，DOM中使用node表示
DOM可以把以上内容都可以看成对象

# 获取元素
1. `document.getElementById("ID名")` 大小写敏感，结果为元素对象
2. `document.getElementsByTag("")` `element.getElementsByTag("")`
## h5 新增
4.  `document.getElementsByClassName("")` 类名,h5新增
5. `document.querySelector("选择器")`  根据指定选择返回第一个对象，css符号,h5新增
6.  `document.querySelectorAll("选择器")`指定选择器的所有对象,h5新增
## 特殊标签
body:`doucment.body`
html:`document.documentElement`

# 事件基础
事件由三部分组成：
1. 事件源 ：事件触发对象 谁 按钮
2. 事件类型：绑带时间
3. 事件处理程序：函数赋值

# 操作元素
## 修改内容
`element.innerText`从起始位置到终止位置，去除html标签，同时空格和换行也会去掉
`element.innerHtml`从起始位置到终止位置，包含html标签，同时保留空格和换行
## 修改属性

# 排他算法
同一组元素，某一元素实现某种样式，需要用到循环的排他思想
1. 所有元素全部清除样式（干掉其他人）
2. 设置当前元算的样式（留下自己）

# 获取，设置属性值
1. `element.属性` 获取属性值 (元素本身的属性)
2. `element.getAttribute('属性')` （获取自定义的属性）
3. 同理设置属性值也一样

# 自定义属性
保存并使用某些数据
H5 规定自定义属性data-开头作为属性名并且赋值
dataset 是一个集合存放了所有以data开头的自定义属性
如果自定义属性里面有多个-链接的单词，我们获取采用==驼峰命名法==
H5 新增element.dataset.index

# 节点操作
| DOM                       | 节点                       |
| ------------------------- | -------------------------- |
| document.getElementById() | 利用父子兄节点关系获取元素 |
| 逻辑性不强、繁琐          | 逻辑性强、但兼容性差       | 
## 概述
一般来说，节点至少拥有nodeType(节点类型)、nodeName(节点名称)和nodeValue（节点值）这三个基本属性
| 种类     | nodeType |
| -------- | -------- |
| 元素节点 | 1        |
| 属性节点 | 2        |
| 文本节点 | 3        | 
实际开发主要操作标签节点
## 层次关系
父子兄层级关系
1. 父节点 parentNode 离元素最近的父节点
2. 子节点 chideNodes / children()![](https://raw.githubusercontent.com/chenruida/image/master/202208012021312.png)
3. firstElementChild 返回第一子元素节点
4. nextSibling 下一个兄弟节点，元素节点和文本节点
5. previousSibling 上一个兄弟节点
6. nextElementSibling 下一个兄弟节点
## 创建节点
动态创建元素节点
`document.createElement('li')`
添加节点
`node.appendChild(child)`将一个节点添加到指定父节点的子节点列表的末尾
`node.insertBefore(child,指定元素）`
## 删除节点
`node.removeChild(child)`
## 复制节点
`node.cloneNode()` 括号为空或者为false 浅拷贝 只复制标签 为true 深拷贝
## 三种动态创建元素区别
![](https://raw.githubusercontent.com/chenruida/image/master/202208012108733.png)

# 高级事件
[[高级事件]]


# DOM案例
## 全选
![](https://raw.githubusercontent.com/chenruida/image/master/202208011944680.png)
![](https://raw.githubusercontent.com/chenruida/image/master/202208011947196.png)
