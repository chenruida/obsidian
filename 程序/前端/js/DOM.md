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

# 节点操作

