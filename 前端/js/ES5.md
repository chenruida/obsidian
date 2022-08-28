# 数组方法
1. ![](https://raw.githubusercontent.com/chenruida/image/master/202208211621148.png)
2. ![](https://raw.githubusercontent.com/chenruida/image/master/202208211621143.png)
3. ![](https://raw.githubusercontent.com/chenruida/image/master/202208211622466.png)
4. some和foreach区别：foreach不会结束迭代
5.  
# 字符串方法
![](https://raw.githubusercontent.com/chenruida/image/master/202208211627627.png)
 # 对象方法
 ![](https://raw.githubusercontent.com/chenruida/image/master/202208211629934.png)
![](https://raw.githubusercontent.com/chenruida/image/master/202208211633441.png)
# 函数
所有函数都是Function的实例（对象）
![](https://raw.githubusercontent.com/chenruida/image/master/202208211903058.png)
![](https://raw.githubusercontent.com/chenruida/image/master/202208211905799.png)
## 改变this的指向
1. call,主要用于继承
2. apply，操作数组![](https://raw.githubusercontent.com/chenruida/image/master/202208211940986.png)
3. bind,不会调用函数，但会改变函数的指向，返回的是改变this后的新函数。有的函数不想立即调用，但又想改变this的指向![](https://raw.githubusercontent.com/chenruida/image/master/202208211946485.png)
# 严格模式
## 作用
1. 变量必须先声明再使用，不能随意删除已声明好的变量
2. 全局作用域中函数的this指向是undefined，严格模式下构造函数不加new调用，this会报错
3. new实例化的构造函数指向创建的对象实例
4. 定时器的this还是指向window
5. 事件、对象还是指向调用者
6. 函数不能重名的参数
7. 不允许在非函数的代码块内声明函数（if,for内不允许声明函数）
# 高阶函数
对其他函数进行操作的函数，它接受函数作为参数或者将函数作为返回值输出
# 闭包
有权访问另一个函数作用域中的变量的函数
一个作用可以访问另一个函数内部的局部变量
 延伸了变量的作用范围
 ![](https://raw.githubusercontent.com/chenruida/image/master/202208212039335.png)

![](https://raw.githubusercontent.com/chenruida/image/master/202208212043056.png)


