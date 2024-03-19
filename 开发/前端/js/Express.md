# 托管静态资源
express.static()
![](https://raw.githubusercontent.com/chenruida/image/master/202208280921014.png)

# nodemon
自动重启项目
# 路由
请求方式、请求路径、处理函数

# 中间件
业务流程中间处理环节
必须包含next()函数，表示把流转关系转交给下一个中间件或路由
按照中间件的先后顺序进行判断
## 作用
多个中间件之间，共享同一份res和req
统一为req或者res对象添加自定义的属性和方法，供下游的中间件或路由使用
## 局部生效
不使用app.use在 
```js
app.get('/',mw1,mw2,(req,res) => {...})
app.get('/',[mw1,mw2],(req,res) => {...})
```
## 注意事项
1. 在路由之前定义中间件
2. 执行完中间件业务代码之后不要忘记使用next（）
3. 防止代码逻辑混乱，在next（）之后不要使用其他的
4. 可以连续调用多个中间件
5. 多个中间件，共享req和res对象
## 分类
1. 应用级别中间件：绑定到app实例中
2. 路由级别中间件：绑定到router上，和应用级别基本没区别
3. 错误级别中间件
4. 内置中间件
5. 第三方中间件
### 错误级别中间件
必须包含4个形参，分别是（err,req,res,next)
### 内置中间件
![](https://raw.githubusercontent.com/chenruida/image/master/202208281635420.png)
### 第三方中间件
## 自定应中间件

