# vue组件之间数据共享方式
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005170843.png)
# 概念
实现组件全局状态（数据）管理的一种机制，可以方便的实现组件之间数据的共享
共享的数据存储在vuex中；私有的存储组件自身
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005171007.png)
1. 集中管理，方便开发
2. 实现组件之间的数据共享，提高效率
3. 存储在vuex中的数据都是响应式的，能够保持数据与页面的同步
# State
提供唯一的公共数据源，所有的数据都要统一放到Store的state中进行存储
```js
const store = new Vuex.Store({
	state:{ count: 0}
})//添加
//----------用法一----------//
this.$store.state.全局数据名称 
//----------用法二----------//
import {mapState} from 'Vuex'

computed:{
	...mapState(['count'])
}
```
## Mutation
修改数据
 1. 只能使用Mutation修改该数据，不能直接操作数据
 2. 可以集中监控数据的变化
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005172432.png)
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005172606.png)
# Action
处理异步数据
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005172808.png)
# Getter
1. 对Store中已有的数据加工处理之后形成新的数据，类似Vue的计算属性
2. Store中数据发生变化，Getter的数据也会跟着变化
3. 不会修改Store里的数据
![](https://raw.githubusercontent.com/chenruida/image/master/picgo/20221005173113.png)



