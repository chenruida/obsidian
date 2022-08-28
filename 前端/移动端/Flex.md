# 弹性布局
## 含义
1. 浏览器提倡的布局模型
2. 避免浮动托标
3. 更简单、灵活 
## 设置方式
父元素添加 `display：flex`,子元素可以自动的挤压或拉伸
## 组成部分
- 弹性容器
- 弹性盒子
![](https://raw.githubusercontent.com/chenruida/image/master/202207232057043.png)

## 对齐方式
### 水平
`justify-content:`
![](https://raw.githubusercontent.com/chenruida/image/master/202207232103843.png)
### 垂直
`align-items:`
![](https://raw.githubusercontent.com/chenruida/image/master/202207232112112.png)

`align-self:`添加到某个子级上，单独修改某个元素

### 弹性高度
1.stretch 容器高度
2.给宽 设定值
3.非stretch 内容高

## 伸缩比
修改盒子伸缩比
`flex:值`数值（整数）
只占用父盒子剩余尺寸
## 主轴方向
默认是水平方向，侧轴是垂直方向
`flex-direction:column`列，垂直
## 调整位置
1. 先判断主轴方向
2. 主轴方向一致：justify- content
3. 交叉轴方向一致:`align-self`
## 弹性盒子换行
`flex-warp:wrap`
### 行对齐方式
`align-content`取值和`justify-conten`基本一致


