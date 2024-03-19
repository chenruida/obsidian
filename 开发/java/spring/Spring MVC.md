# Spring MVC

![image-20210219105044457](https://cdn.jsdelivr.net/gh/chenruida/image@master/uPic/image-202102191050444571pcLSZ.png)

## 前端控制器

- 处理servlet的共有行为
- 由框架充当

## 开发步骤

1. 导入Spring MVC  jar 包
2. 配置servlet,代表所有请求都要通过mvc 的控制器
3. 编写java bean (控制器 controller)
4. 将controller使用注解配置到Spring容器中（@Controller)，配置业务方法的映射地址
5. 配置组件扫描（Spring会自动发现应用上下文中所创建的bean。）
6. 执行访问测试

## SpringMVC执行流程

![截屏2021-02-19 13.46.35](https://cdn.jsdelivr.net/gh/chenruida/image@master/uPic/%E6%88%AA%E5%B1%8F2021-02-19%2013.46.35T3j6bX.png)

1. 客户端发送请求至前端控制器DispatcherServlet。
2. DispatcherServlet收到请求调用HandlerMapping处理器映射器。
3. 处理器映射器找到具体的处理器（可根据XML配置，注解进行查找），生成处理器对象及处理器拦截器（如果有则生成）一并返回给DispatcherServlet
4. DispatcherServlet调用HandlerAdapter处理器适配器
5. HandlerAdapter经过适配调用具体的处理器（Controller，也叫后端控制器）。
6. Controller执行完成返回ModelAndView。
7. HandlerMapping将返回的ModelAndView返回给DispatcherServlet
8. DispatcherServlet将ModelAndView传给ViewResolver
9. ViewResolver解析后返回View对象给DispatcherServlet
10. DispatcherServlet渲染试图

## 注解解析

- @RequestMapping 
  - 用于建立请求URL
  - value 访问路径
  - method RequestMethod  get或者post
  - params 指定限制请求参数。支持简单表达式

## 响应方式

### 1. 页面跳转

#### - 直接返回字符串

将返回的字符串与视图解析器的前后缀拼接后跳转

#### - 通过ModelAndView对象返回

### 2. 回写数据

#### -直接返回字符串

- 使用@ResponseBody，同时代表不进行页面跳转

#### -返回对象或集合

mvc的注解驱动

``<mvc:annotation-driver>``默认底层就会集成Jackson进行对象或集合的json格式字符串的转换

```java
    //  回写数据-返回对象或集合
    @RequestMapping(value = "/test", produces = "application/json")
    @ResponseBody
    public User test6() {
        User user = new User();
        user.setUserId(1);
        user.setUsername("admin");
        user.setPassword("admin");
        System.out.println("test success...");
        return user;
    }
```



## 注解驱动

在SpringMVC的各组件中，处理器映射器、处理器适配器、视图解析器成为SpringMVC的三大组件。使用``<mvc:annotation-driver>``自动加载RequestMappingHandlerMapping(处理映射器)和处理适配器，可在xml配置文件中使用代替注解处理器和适配的配置。

## 获取请求数据

### 1. 基本类型参数

Controller中业务方法的参数名称要与请求参数的name一致，参数值就会自动映射匹配

### 2. POJO类型

Controller中业务方法的POJO参数的属性名与请求参数的name一致，参数值会自动映射匹配

### 3. 数组类型

Controller中业务方法的POJO参数的属性名与请求参数的name一致，参数值会自动映射匹配

### 4. 集合类型参数

1. 获得集合参数时，要将集合参数包装到一个POJO中（ValueObject）



2. 当使用Ajax提交时，可以指定contentType为jsonx形式，那么在方法参数位置使用@RequestBody可以直接接受集合数据而无需使用POJO进行包装

json 格式

```json
[{
		"userId": 1,
		"username": "1",
		"password": "1",
		"submissionDate": "1",
		"userAuthority": 1
	},
	{
		"userId": 2,
		"username": "2",
		"password": "2",
		"submissionDate": "2",
		"userAuthority": 2
	}
]
```

## 请求数据乱码

![2023](https://raw.githubusercontent.com/chenruida/image/master/img/2023.png)

![20210221200119752](https://raw.githubusercontent.com/chenruida/image/master/img/20210221200119752.png)

## 参数绑定注解

@RequestParam

- value 与请求参数名称
- required 此在指定的请求参数是否必须包括，默认为true,提交时没有此参数数则报错
- defaultValue 当没有指定请求参数时，则使用默认值赋值

## RESTful风格

![image-20210221211016969](https://raw.githubusercontent.com/chenruida/image/master/img/image-20210221211016969.png)

![image-20210221211111410](https://raw.githubusercontent.com/chenruida/image/master/img/image-20210221211111410.png)

## 自定义类型转换器

内置了常用转换器，但是有些内置转不了，需要自定义，例如日期类型的数据

### 开发步骤

1. 定义转换器类实现Converter接口
2. 在配置文件中声明转换器
3. 在<annotation-driven> 中引用转换器

![image-20210221213437717](https://raw.githubusercontent.com/chenruida/image/master/img/image-20210221213437717.png)

![image-20210221213515661](https://raw.githubusercontent.com/chenruida/image/master/img/image-20210221213515661.png)

## 获取请求头

@RequestHeader

获取请求头的值

- value:请求头的名称
- required：是否必须携带此请求头

@CookieValue

直接获得Cookie的值

- value:cookie的名称
- required：是否必须携带此cookie

## 文件上传

### 客户端三要素

- 表单项type=“file”
- 提交方式是post
- enctype属性是多部分表单形式，即enctype = “multipart/form-data”

### 上传原理

- 当form表单修改为多部分表单时，request.getParamater()将失效
- enctype = “application/x-www-form-urlencoded”时，form表单的正文内容格式是：key=values&key=value&key=value
- 当form表单的enctype取值为multipart/form-data，请求正文内容变成多部分形式：

![截屏2021-02-22 10.16.31](https://cdn.jsdelivr.net/gh/chenruida/image@master/uPic/%E6%88%AA%E5%B1%8F2021-02-22%2010.16.31YEHBgy.png)



### 单文件上传步骤

1. 导入fileupload和io坐标

2. 配置文件上传解析器

   ![截屏2021-02-22 10.46.17](https://cdn.jsdelivr.net/gh/chenruida/image@master/uPic/%E6%88%AA%E5%B1%8F2021-02-22%2010.46.17cSkv6Q.png)

3. 编写代码

   ![截屏2021-02-22 11.17.28](/Users/admin/Library/Application%20Support/typora-user-images/%E6%88%AA%E5%B1%8F2021-02-22%2011.17.28.png)

## 拦截器（interceptor)

拦截器类似于Servlet中的过滤器Filter，用于对处理器进行预处理和后处理。

将拦截器按一定的顺序结成一条链，这条链称为拦截器链。在访问被拦截的方法或字段时，拦截器链中的拦截器就会按照定义的顺序被调用。拦截器也是**AOP思想**的具体实现。

### 拦截器和过滤器的区别

![截屏2021-02-22 11.26.23](https://cdn.jsdelivr.net/gh/chenruida/image@master/uPic/%E6%88%AA%E5%B1%8F2021-02-22%2011.26.23tf6ovg.png)

### 用法

1. 创建拦截器类实现HandlerInterceptor接口
2. 配置拦截器<img src="/Users/admin/Library/Application%20Support/typora-user-images/%E6%88%AA%E5%B1%8F2021-02-22%2013.42.25.png" alt="截屏2021-02-22 13.42.25"  />
3. 测试拦截器效果

### 接口方法

``````java
    //方法执行之前
    @Override
    public boolean preHandle(HttpServletRequest request,
                             @NotNull HttpServletResponse response,
                             @NotNull Object handler)
            throws Exception {
				...
        return true; //true 代表放行， false代表不放行
    }

    //方法执行之后  视图对象返回之前执行
    @Override
    public void postHandle(HttpServletRequest request,
                           @NotNull HttpServletResponse response,
                           @NotNull Object handler,
                           ModelAndView modelAndView)
            throws Exception {
				...
    }

    //在流程都执行完毕后 执行
    @Override
    public void afterCompletion(HttpServletRequest request,
                                @NotNull HttpServletResponse response,
                                @NotNull Object handler,
                                Exception exception)
            throws Exception {
				...
    }
``````

## 异常处理的思路

系统的异常包括两类：预期异常和运行时异常RuntimeException,前者可以通过捕获异常从而获取异常信息，后者主要通过规范代码开发、测试等手段减少运行时异常的发生。

系统的Dao、Service、Controller出现都通过throwsException向上抛出，最后又SpringMVC前端控制器交由异常处理器进行异常处理

![image-20210222213258743](https://raw.githubusercontent.com/chenruida/image/master/img/image-20210222213258743.png)

### 异常处理的两种方式

- 使用Spring MVC提供的简单异常处理器SimpleMappingExceptionResolver
- 使用Spring的异常处理器接口HandleExceptionResolver自定义自己的异常处理器

### SimpleMappingExceptionResolver

在使用时可以根据项目情况进行相应异常与识图的映射配置

![image-20210222213858490](https://raw.githubusercontent.com/chenruida/image/master/img/image-20210222213858490.png)

### 自定义异常处理

1. 创建异常处理器类实现HandlerExceptionResolver
2. 配置异常处理器
3. 编写异常页面
4. 测试异常跳转

## 注释

### POJO和JavaBean含义

一般这俩是一个东西

如果读写方法符合以下这种命名规范：

```
// 读方法:
public Type getXyz()
// 写方法:
public void setXyz(Type value)
```

那么这种`class`被称为`JavaBean`

**作用**

JavaBean主要用来传递数据，即把一组数据组合成一个JavaBean便于传输。此外，JavaBean可以方便地被IDE工具分析，生成读写属性的代码，主要用在图形界面的可视化设计中。





