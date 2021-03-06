# HTML中的JavaScript
## `<script>`元素
1. async：表示立即开始下载脚本，但不阻止其他页面动作，比如下载资源或等待其他脚本加载。只对外部脚本文件有效
2. charset：src属性指定的代码字符集。但是大多数浏览器都不在乎它的值
3. crossorigin:配置相关请求的CORS（跨源资源共享）设置。默认不使用CORS。crossorigin="anonymous"配置文件请求不必设置凭据标志。crossorigin="use-credentials"设置凭据标志，意味着出站请求会包含凭据。
4. defer：表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。
5. integrity：允许比对接收到的资源和指定的加密签名以验证子资源完整性（SRI，Subresource Integrity）。如果接收到的资源的签名与这个属性指定的签名不匹配，则页面会报错，脚本不会执行。这个属性可以用于确保内容分发网络（CDN，ContentDelivery Network）不会提供恶意内容。
6. type：代替language，表示代码块中脚本语言的内容类型（也称MIME类型）。惯例是"text/javascript"，实际是"application/x-javascript"不过给type属性这个值有可能导致脚本被忽略。
按照惯例，外部JavaScript文件的扩展名是.js。这不是必需的，因为浏览器不会检查所包含JavaScript文件的扩展名。这就为使用服务器端脚本语言动态生成JavaScript代码，或者在浏览器中
将JavaScript扩展语言（如TypeScript，或React的JSX）转译为JavaScript提供了可能性。不过要注意，服务器经常会根据文件扩展来确定响应的正确MIME类型。如果不打算使用.js扩展名，一定要确保服务器能返回正确的MIME类型。
### 标签占位符
- 放在`<head>`里，必须在所有JavaScript脚本执行完后再渲染页面。会导致延迟
- 放在`<body>`后，加快加载
### 推迟执行执行
- `defer` 属性会推迟执行
- 会在DOMContentLoaded事件之前执行
- 第一个脚本执行之后第二个脚本开始执行
### 异步执行
async属性与defer类似，但是不会保证执行的顺序。
### 动态加载脚本
在脚本中加载脚本
```js
let script = documnet.createElement('script');
script.src = 'test.js';
document.head.appendChild(script);
```
默认为异步加载
但是不要这样，会打乱执行的优先级，变得不可预测。
# 语法
### 声明提升
JavaScript 中，函数及变量的声明都将被提升到函数的最顶部。
JavaScript 中，变量可以在使用后声明，也就是变量可以先使用再声明。
JavaScript 只有声明的变量会提升，初始化的不会。
### 严格模式
ECMAScript 5增加了严格模式（strict mode）的概念。严格模式是一种不同的JavaScript解析和执行模型，ECMAScript 3的一些不规范写法在这种模式下会被处理，对于不安全的活动将抛出错误。
```js
"use strict"
```

### let和var的区别
1. let:块作用域，{}之内有效；var:函数作用域，函数之内有效
2. let 不允许冗余声明
3. let声明的变量不会在作用域中被提升，在let声明之前的执行瞬间被称为“暂时性死区”，在此阶段引用任何后面才声明的变量都会抛出ReferenceError
4. 全局声明：与var关键字不同，使用let在全局作用域中声明的变量不会成为window对象的属性（var声明的变量则会）
5. let 不能进行条件声明
6. for循环中，var会渗透到循环体外部，let不会
### 最佳实践
1. 不用var
2. const优先，var次之。只有知道会变化时才变化。
## 数据类型
Undefined、Null、Boolean、Number、String和Symbol
### typeof 
typeof是一个操作符而不是函数，所以不需要参数。
### undefined 类型
未初始化的变量会被自动赋予undefined值
### Null 类型
Null类型同样只有一个值，即特殊值null
### String
ECMAScript中的字符串是不可变的（immutable），意思是一旦创建，它们的值就不能变了。要修改某个变量中的字符串值，必须先销毁原始的字符串，然后将包含新值的另一个字符串保存到该变量。
### Symbol
符号是原始值，且符号实例是唯一、不可变的。符号的用途是确保对象属性使用唯一标识符，不会发生属性冲突的危险。
## 运算符
### 位操作符
```js
let num = -18
console.log(num.toString(2)) // "-10010"
```
1. 按位非：按位非操作符用波浪符（~）表示，它的作用是返回数值的一补数。按位非的最终效果是对数值取反并减1。
	```js
let num1 = 25; // 二进制00000000000000000000000000011001
let num2 = ~num1; // 二进制11111111111111111111111111100110
console.log(num2); // -26
```
2. 按位与。按位与操作符用和号（&）表示，有两个操作数。本质上，按位与就是将两个数的每一个位对齐，然后基于真值表中的规则，对每一位执行相应的与操作。
	![](https://raw.githubusercontent.com/chenruida/image/master/202207121050448.png)

3. 按位或操作符用管道符（|）表示，同样有两个操作数。按位或遵循如下真值表：
	![](https://raw.githubusercontent.com/chenruida/image/master/202207121051690.png)
4. 按位异或。按位异或用脱字符（^）表示，同样有两个操作数。
	![](https://raw.githubusercontent.com/chenruida/image/master/202207121051116.png)

5. 左移操作符用两个小于号（<<）表示，会按照指定的位数将数值的所有位向左移动。
6. 有符号右移由两个大于号（>>）表示，会将数值的所有32位都向右移，同时保留符号（正或负）。
7. 无符号右移用3个大于号表示（>>>），会将数值的所有32位都向右移。

### 等
ECMAScript中的等于操作符用两个等于号（`==`）表示，如果操作数相等，则会返回true。不等于操作符用叹号和等于号（`!=`）表示，如果两个操作数不相等，则会返回true。这两个操作符都会先进行类型转换（通常称为强制类型转换）再确定操作数是否相等。
全等和不全等操作符与相等和不相等操作符类似，只不过它们在比较相等时不转换操作数。全等操作符由3个等于号（`===`）表示，只有两个操作数在不转换的前提下相等才返回true
## 函数
# 变量、作用域与内存
- 上下文中的代码在执行的时候，会创建变量对象的一个作用域链
- 这个作用域链决定了各级上下文中的代码在访问变量和函数时的顺序。
- 代码正在执行的上下文的变量对象始终位于作用域链的最前端。
- 如果上下文是函数，则其活动对象（activation object）用作变量对象