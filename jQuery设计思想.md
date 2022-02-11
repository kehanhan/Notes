# jQuery 设计思想

## 获取元素
jQuery的基本设计思想和主要用法，就是"选择某个网页元素，然后对其进行某种操作"。
选择表达式可以是CSS选择器：
```javascript
　　$(document) //选择整个文档对象
　　$('#myId') //选择ID为myId的网页元素
　　$('div.myClass') // 选择class为myClass的div元素
　　$('input[name=first]') // 选择name属性等于first的input元素
```
也可以是jQuery特有的表达式：
```javascript
　　$('a:first') //选择网页中第一个a元素
　　$('tr:odd') //选择表格的奇数行
　　$('#myForm :input') // 选择表单中的input元素
　　$('div:visible') //选择可见的div元素
　　$('div:gt(2)') // 选择所有的div元素，除了前三个
　　$('div:animated') // 选择当前处于动画状态的div元素
```
## 链式操作
jQuery设计思想之三，就是最终选中网页元素以后，可以对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来，比如：
```javascript
　　$('div') //找到div元素
　　　.find('h3') //选择其中的h3元素
　　　.eq(2) //选择第3个h3元素
　　　.html('Hello'); //将它的内容改为Hello
// 找到所有的div元素，增加'red'类，并且替换文本内容
```

## 创建元素
把新元素传入jQuery的构造函数：
```javascript
　　$('<p>Hello</p>');
　　$('<li class="new">new list item</li>');
　　$('ul').append('<li>list item</li>');
```

## 移动元素
jQuery提供两组方法，来操作元素在网页中的位置移动。一组方法是直接移动该元素，另一组方法是移动其他元素，使得目标元素达到我们想要的位置。

- .insertAfter()和.after()：在现存元素的外部，从后面插入元素
- .insertBefore()和.before()：在现存元素的外部，从前面插入元素
- .appendTo()和.append()：在现存元素的内部，从后面插入元素
- .prependTo()和.prepend()：在现存元素的内部，从前面插入元素

## 修改元素属性
```javascript
　　.html() //取出或设置html内容
　　.text() //取出或设置text内容
　　.attr() //取出或设置某个属性的值
　　.width() //取出或设置某个元素的宽度
　　.height() //取出或设置某个元素的高度
　　.val() //取出某个表单元素的值
```

参考资料：
http://www.ruanyifeng.com/blog/2011/07/jquery_fundamentals.html