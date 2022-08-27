# ES6

ECMAScript 6

## let

为什么新增let声明变量

1. var 可以重复声明，无法限制修改，==没有块级作用==
## 解构赋值
从数组中提取值，按照对应位置，对变量赋值。对象也可以实现解构。
```js
let [a,b,c] = [1,2,3]
let person = {name:'zhangsan',age:20}
let {name,age} = person
let {name:myName,age:myAge} = person
```
## 箭头函数

- 不需要参数或需要多个参数，就用圆括号代替
- 代码块部分多于一条语句，就用代码块括起来，并用return返回
- 箭头函数返回对象时，必须使用在对象外面加上括号
- 箭头函数使得表达更加简洁
- 箭头函数能够简化回调函数

### 用法

1. 如果没有参数，或有多个参数调试需要使用（）来定义参数列表
2. 如果有一个参数，可以不用（）
3. 如果函数体中只有一条语句，可以不用{},就不用return

### 细节

- 通常用于回调函数
- 箭头函数返回对象时，必须在对象外面加上（）

### this的指向问题

- 普通函数的this指向他的调用者
- 箭头函数没自己的this，
- 他的this是继承而来的
## 剩余参数
不定参数表示为一个数组
```js
let sum = (...args) =>{

}
let [a,...b] = [1,2,3]
```
## 扩展运算符
将数组或者对象转化为用逗号分隔的参数序列
```js
//数组合并1
let ary1 = [1,2,3]
let ary2 = [1,2,3]
let ary3 = [...ary1,...ary2]
//数组合并2
ary1.push(..ary2)
//伪数组遍历成真正的数组
let arrayLike = {'0':'zhangsan','1':'lisi','2':'wangwu','length':3}
let ary = Array.from(arrayLike,item => {})
```
## Array扩展方法
1. ![](https://raw.githubusercontent.com/chenruida/image/master/202208232006221.png)
2. ![](https://raw.githubusercontent.com/chenruida/image/master/202208232007020.png)
3. ![](https://raw.githubusercontent.com/chenruida/image/master/202208232007870.png)
4. ![](https://raw.githubusercontent.com/chenruida/image/master/202208232009209.png)

# String的扩展方法
![](https://raw.githubusercontent.com/chenruida/image/master/202208232009209.png)


 


