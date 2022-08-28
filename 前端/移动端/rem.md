# rem
- 相对单位
- 相对于HTML标签的字号计算结果
- 1rem = 1HTML字号大小
# 媒体查询
根据不同的视口宽度，设置不同的根字号
```css
@media (媒体特性){
	选择器{
		css属性
	}
}
```
```css
@media (width:320px){
	html{
		font-size: 32px
	}
}
```
目前rem布局方案中，将网页等分为10份，HTML标签的字号为视口宽度的1/10
例如width:320px font-size:32px

### max-width;min-width
小于等于：max-width
大于等于：min-width
书写顺序：
min-width:从小到大
max-width:从大到小
# flexible.js
配合rem实现在不同设备中，网页元素尺寸缩放的效果
