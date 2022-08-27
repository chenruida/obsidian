# WebFlux

异步非阻塞，在servlet3.1种才开始支持，核心基于Reactor的相关API实现。

- 异步和同步
  - 针对调用者
  - 调用者发送请求，如果等着对方回应之后才去做其他事情就是同步，如果发送请求之后不等对方回应就去做其他事情就是异步
- 阻塞和非阻塞
  - 针对被调用者
  - 被调用者收到请求折后，做完请走任务之后才给出反馈就是阻塞，受到请求之后马上给出反馈然后再去做事情就是非阻塞

![image-20211026212443920](https://raw.githubusercontent.com/chenruida/image/master/uPic/image-20211026212443920.png)



### 特点

1. 非阻塞性：在有限资源下，提高系统吞吐量和伸缩性，以Reactor为基础实现响应式编程
2. 函数式编程，使用Java8函数式编程方式实现路由请求

### 比较spring MVC

![image-20211026093021457](https://raw.githubusercontent.com/chenruida/image/master/uPic/image-20211026093021457.png)

1. 都可以使用注解方式，都运行在Tomcat容器中
2. 采用命令式编程，

## 响应式编程

### 1. 什么是响应式编程

是一种面向数据流和变化传播的编程范式。这意味着可以在编程语言中很方便的表达静态和动态的数据流，而相关的计算模型会自动的将变换的值通过数据流进行传播。

### 2.Reactor实现

1. 响应式编程操作中，Reactor是满足Reactive规范框架

2. Reactor有两个核心类，Mono和Flux,这两个类实现借口Publisher,提供丰富操作符。flux对象实现发布者，返回N个元素；MONO实现发布者，返回0或者1个元素。

3. Flux和Mono都是数据流的发布者，使用Flux和Mono都可以发出三种数据信号:元素值，错误信号，完成信号。错误信号和完成信号都代表终止信号，终止信号用于告诉订阅者数据流结束了。

4. - 错误信号和完成信号都是终止信号，不能共存。
   - 如果没有发送任何元素值，而是直接发送错误或者完成信号，表示空数据流
   - 如果没有错误信号，没有完成信号，表示无限数据流

5. 调用just或者其他方法只是声明数据流，数据流并没有发出，只有进行订阅之后才会触发数据流。

6. 操作符 ：对数据进行一道道操作，称为操作符，不如工厂流水线

   - map 元素映射为新元素

     ![image-20211026210130179](https://raw.githubusercontent.com/chenruida/image/master/uPic/image-20211026210130179.png)

   - flatMap 元素映射为流

     ![image-20211026210453284](https://raw.githubusercontent.com/chenruida/image/master/uPic/image-20211026210453284.png)

### 三种信号特点

1. 错误信号和完成信号都是终止信号，不能共存
2. 如果没有发送任何元素值，而是直接发送错误信号

## 执行流程和API

1. 执行过程和SpringMVC相似
   - 核心控制器DispathHandler,实现接口WebHandler
   - WebHandler 里面有方法handle
   - ![image-20211026213306243](https://raw.githubusercontent.com/chenruida/image/master/uPic/image-20211026213306243.png)

2. 核心控制器DispathHandler主要是负责请求的处理
   1. HandlerMapping 请求查询处理的方法
   2. HandlerAdapter 真正负责请求处理
   3. HandlerResultHandler 响应结果处理
3. 实现函数式编程，两个接口：RouterFunction (路由处理)和HandlerFunction（处理函数）

## 函数式编程模型

1. 使用函数式编程模型操作时，需要自己初始化服务器
2. 实现函数式编程，两个接口：RouterFunction (路由处理，请求转发给对应的handler)和HandlerFunction（处理请求生成的函数）。核心任务定义两个函数式接口的实现并且启动需要的服务器
3. 请求和响应不再是ServletRequest和ServletResponse，而是ServerRequest和ServerResponse
