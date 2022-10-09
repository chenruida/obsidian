 # SPA
 - 后端渲染存在性能问题
 - Ajax前端渲染不支持浏览器的前进后退操作
 - SPA：单页面程序，整个网站是一个页面，内容的变化通过Ajax局部更新实现、同时支持浏览器地址栏的前进后退
 - 实现原理：基于URL的hash
 - hash的变化会导致浏览器记录访问历史的变换、但是hash的变换不会触发新的URL请求

# 前端路由
根据不同的==用户事件==，显示不同的页面内容
本质是==用户事件==与==事件处理函数==之间的关系
![](https://raw.githubusercontent.com/chenruida/image/master/20221005103744.png)
# Vue Router
 ## 使用
 1. 引入库文件
 2. 添加路由链接
 3. 添加路由填充位
 4. 定义路由组件
 5. 配置路由规则并创建路由实例
 6. 把路由挂载到Vue根实例中
## 嵌套路由
子集路由链接
子级路由展示位
## 动态匹配路由
```JS
:id 
```
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005153737.png)
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005153954.png)
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005154305.png)
## 命名路由
 给路由规则起一个别名，即为“命名路由”，方便跳转
 ![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005154651.png)
# 导航方式
## 命名式导航
```html
<a></a>
<router-link></router-link>
```
## 编程式导航
```js
this.$touter.push('hash地址')
this.$router.go(n) //前进，后退
```
### push
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005155310.png)
