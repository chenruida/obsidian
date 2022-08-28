# Spring AOP

面向切片编程，是通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。

是OOP的延续，是函数式编程的一种衍生泛型。利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑和部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。

## 作用及其优势

- 作用：

  在程序运行期间，在不修改源码的情况下对方法进行功能增强

- 优势：

   减少重复代码，提高开发效率，并且便于维护

## 动态代理

### 1. JDK

### 2. cglib

## 相关概念

- Target(目标对象)：代理的目标对象
- Proxy(代理)：一个类被AOP织入增强后，就产生一个代理类
- Joinpoint(代理点)指那些被拦截的店。在spring中，这些点指的就是方法，因为spring只支持方法类型的连接点。==可以被增强的方法==
- **Pointcut(切入点)** ：所谓切入点是指我们要对哪些joinpoin进行拦截的定义。==真正被增强的方法==
- **Advice（通知/增强**）：所谓通知是指拦截到Joinpoint之后所要做的事情（方法）
- **Aspect(切面)**：切入点+通知
- **Weaving(织入)**：是指把增强应用到目标对象来创建新的代理对象的过程。 

## AOP开发明确的事项

### 1. 需要编写的内容

- 编写核心业务代码（目标类的目标方法）
- 编写切面类，切面类中有通知（增强功能方法）
- 在配置文件中，配置织入关系，即将哪些通知与哪些连接点进行结合

## 2. AOP技术实现的内容

Spring 框架监控切入点的执行。一旦监控到切入点方法被运行，使用代理机制，动态创建目标对象的代理对象，根据通知类别，在代理对象的对应位置，将通知对象的功能织入，完成完整的代码逻辑运行。

## 3.AOP底层使用哪种代理方式

自动判断

## 快速入门(XML)

1. 导入AOP相关坐标
2. 创建目标接口和目标类
3. 创建切面类（内部又增强方法）
4. 将目标类和切面类的对象创建权交给Spring
5. 在applicationContext.xml中配置织入关系

#### 切点表达式写法

execution([修饰符] 返回值类型 包名.类名.方法名(参数))

- 访问修饰符可以省略
- 返回值类型、报名、类名、方法名可以使用星号代表任意
- 包名与类名之间一个点. 代表当前包下的类，两个点.. 代表当前包及其子包下的类
- 参数列表可以使用两个点.. 表示任意个数 ，任意类型的参数列表

#### 通知种类

- 前置通知 \<aop:before>
- 后置通知 \<aop:after-returning>
- 环绕通知 \<aop:aroud>
- 异常抛出通知 \<aop:throwing>
- 最终通知 \<aop:after>

## 快速入门(注解)

1. 导入AOP相关坐标
2. 创建目标接口和目标类
3. 创建切面类（内部又增强方法）
4. 将目标类和切面类的对象创建权交给Spring
5. 在切面类使用注解配置织入关系
6. 在配置文件中开启组件扫描和AOP自动代理

#### 通知注解

@Before

@AfterReturning

@Around

@AfterThrowing

@After

### 切点表达式

随意定义一个方法(example)，在方法上写@Pointcut("表达式")

然后@around("example()")