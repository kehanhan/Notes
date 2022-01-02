# JavaScript 的历史

## 背景

> 1994 年，网景公司（Netscape）发布了 Navigator 浏览器 0.9 版。这是历史上第一个比较成熟的网络浏览器，轰动一时。但是，这个版本的浏览器只能用来浏览，不具备与访问者互动的能力。...... 网景公司急需一种网页脚本语言，使得浏览器可以与网页互动。

> 1995 年 5 月，网景公司做出决策，未来的网页脚本语言必须"看上去与 Java 足够相似"，但是比 Java 简单，使得非专业的网页作者也能很快上手。

> Brendan Eich 被指定为这种"简化版 Java 语言"的设计师。但是，他对 Java 一点兴趣也没有。为了应付公司安排的任务，他只用 10 天时间就把 Javascript 设计出来了。

## 设计缺陷

### 为什么 JavaScript 有设计缺陷

**1. 设计阶段过于仓促**

Javascript 的设计，其实只用了十天。而且，设计师是为了向公司交差，本人并不愿意这样设计（参见《Javascript 诞生记》）。另一方面，这种语言的设计初衷，是为了解决一些简单的网页互动（比如，检查"用户名"是否填写），并没有考虑复杂应用的需要。

**2. 没有先例**

Javascript 同时结合了函数式编程和面向对象编程的特点，这很可能是历史上的第一例。而且直到今天为止，Javascript 仍然是世界上唯一使用 Prototype 继承模型的主要语言。这使得它没有设计先例可以参考。

**3. 过早的标准化**

Javascript 的发展非常快，根本没有时间调整设计。Javascript 推出一年半之后，国际标准就问世了。设计缺陷还没有充分暴露就成了标准。相比之下，C 语言问世将近 20 年之后，国际标准才颁布。

### JavaScript 的 10 个设计缺陷

**1. 不适合开发大型程序**

Javascript 没有名称空间（namespace），很难模块化；没有如何将代码分布在多个文件的规范；允许同名函数的重复定义，后面的定义可以覆盖前面的定义，很不利于模块化加载。

**2. 非常小的标准库**

Javascript 提供的标准函数库非常小，只能完成一些基本操作，很多功能都不具备。

**3. null 和 undefined**

null 属于对象（object）的一种，意思是该对象为空；undefined 则是一种数据类型，表示未定义。

```javascript
typeof null; // object
typeof undefined; // undefined
```

两者非常容易混淆，但是含义完全不同。

```javascript
var foo;
alert(foo == null); // true
alert(foo == undefined); // true
alert(foo === null); // false
alert(foo === undefined); // true
```

在编程实践中，null 几乎没用，根本不应该设计它。

**4. 全局变量难以控制**

Javascript 的全局变量，在所有模块中都是可见的；任何一个函数内部都可以生成全局变量，这大大加剧了程序的复杂性。

```javascript
a = 1;
(function () {
  b = 2;
  alert(a);
})(); // 1
alert(b); //2
```

**5. 自动插入行尾分号**

Javascript 的所有语句，都必须以分号结尾。但是，如果你忘记加分号，解释器并不报错，而是为你自动加上分号。有时候，这会导致一些难以发现的错误。

比如，下面这个函数根本无法达到预期的结果，返回值不是一个对象，而是 undefined。

```javascript
function(){
    return
        {
            i=1
        };
}
```

原因是解释器自动在 return 语句后面加上了分号。

```javascript
function(){
    return;
    {
        i=1
    };
}
```

**6. 加号运算符**

- 号作为运算符，有两个含义，可以表示数字与数字的和，也可以表示字符与字符的连接。

```javascript
alert(1 + 10); // 11
alert("1" + "10"); // 110
```

如果一个操作项是字符，另一个操作项是数字，则数字自动转化为字符。

```javascript
alert(1 + "10"); // 110
alert("10" + 1); // 101
```

这样的设计，不必要地加剧了运算的复杂性，完全可以另行设置一个字符连接的运算符。

**7. NaN**

NaN 是一种数字，表示超出了解释器的极限。它有一些很奇怪的特性：

```javascript
NaN === NaN; //false
NaN !== NaN; //true
alert(1 + NaN); // NaN
```

与其设计 NaN，不如解释器直接报错，反而有利于简化程序。

**8. 数组和对象的区分**

由于 Javascript 的数组也属于对象（object），所以要区分一个对象到底是不是数组，相当麻烦。[Douglas Crockford](http://javascript.crockford.com/remedial.html) 的代码是这样的：

```javascript
if (
  arr &&
  typeof arr === "object" &&
  typeof arr.length === "number" &&
  !arr.propertyIsEnumerable("length")
) {
  alert("arr is an array");
}
```

**9. == 和 ===**

== 用来判断两个值是否相等。当两个值类型不同时，会发生自动转换，得到的结果非常不符合直觉。

```javascript
"" == "0"; // false
0 == ""; // true
0 == "0"; // true
false == "false"; // false
false == "0"; // true
false == undefined; // false
false == null; // false
null == undefined; // true
"\t\r\n" == 0; // true
```

因此，推荐任何时候都使用 "==="（精确判断）比较符。

**10. 基本类型的包装对象**

Javascript 有三种基本数据类型：字符串、数字和布尔值。它们都有相应的建构函数，可以生成字符串对象、数字对象和布尔值对象。

```javascript
new Boolean(false);
new Number(1234);
new String("Hello World");
```

与基本数据类型对应的对象类型，作用很小，造成的混淆却很大。

```javascript
alert(typeof 1234); // number
alert(typeof new Number(1234)); // object
```

关于 Javascript 的更多怪异行为，请参见 [Javascript Garden](https://bonsaiden.github.com/JavaScript-Garden/zh/) 和 [wtfjs.com](http://wtfjs.com/)。
