# JS语法

## 什么是表达式和语句
- 1+2表达式的值是3
- add(1,2)表达式的值是函数的返回值
- console.log(3)的值是undefined

**js大小写敏感** 

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
*** A && B && C && D 取第一个假值或D,不会取true/false ***

#### ||
*** A || B || C || D 取第一个真值或D,不会取true/false ***

## while for语句

## break continue

## label
