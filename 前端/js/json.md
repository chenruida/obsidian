# 对象结构
key 必须是双引号包裹起来的字符串
value可以是数字、字符串、布尔值、null、数组、对象六种类型
 字符串类型的值也必须用双引号
 不能写注释
 # 与js对象的关系
 是js对象的字符串表示法，使用文本来表示一个对象，本质是字符串
 ```js
 var obj = {a:"hello",b:"world"}
 var json = '{"a":"hello","b":"world"}'
var obj = JSON.parse(json)
var json = JSON.stringify()
```