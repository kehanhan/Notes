# JS语法

## 什么是表达式和语句
- 1+2表达式的值是3
- add(1,2)表达式的值是函数的返回值
- console.log(3)的值是undefined

>js大小写敏感 

## 空格
- 大部分空格都没有实际含义
- 加回车大部分也没有实际影响
- 只有一个地方不能加回车，那就是return后面, 否则会返回undefiend

## 标识符的规则
- 第一个字符，可以是任意Unicode字母或_$或中文
- 后面的字符除了上面所说的,还可以有数字

## if else语句

### 语法
```javascript
if (表达式) {
    语句
} else if (表达式) {
    语句
} else {
    语句
}
```

### 问号冒号表达式
    表达式1?表达式2:表达式3

### 短路逻辑

#### &&
**A && B && C && D 取第一个假值或D,不会取true/false** 
```javascript
a&&b
//等价于
if (a) {
	b
}
```

#### ||
**A || B || C || D 取第一个真值或D,不会取true/false**  
```javascript
a||b
//等价于
if(!a) {
  b
}
```
可以用来给a设定默认值
```javascript
a = a || 100
//如果a存在就a=a, 如果a不存在, a=100
//等价于
if (a) {
 a = a
} else {
 a = 100
}
```

## while for语句
### while
```javascript
let a = 0.1;
while (a !== 1) {
    console.log(a)
    a = a + 0.1
}
```
由于浮点数的计算时不精确的，所以以上代码会死循环

### for
```javascript
for (var i = 0; i < 5; i++) {
    console.log(i)
}
//请问这里打印出的i是多少？
console.log(i)
```
答案是5， 因为当i == 4, i = i + 1 = 5, 然后退出循环
```javascript
setTimeout就是过一段时间执行
for (var i = 0; i < 5; i++) {
    setTimeout(()=>{
        console.log(i)
    }, 0)
}
```
会打印出5次5
当把var 换成 let, 就会打印出 0, 1, 2, 3, 4

## break continue
- break 退出所有循环
- continue 退出当前循环

## label
语法:
```javascript
{
    a:1
}
```
这是一个label, a: 1 表示这个标签是a, a的值是1
对象:
```javascript
var a = {
    a:1
}
```

