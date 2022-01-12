# JS 对象

## 声明对象的两种语法

```javascript
//第一种
let obj = { name: "frank", age: 18 };
//第二种
let obj = new Object({ name: "frank" });
```

## 删除对象的属性

```javascript
delete obj.xxx;
delete obj["xxx"];
```

**xxx 为字符串**

obj.xxx 等价于 obj["xxx"] 等价于 obj[a],其中 a = 'xxx'

## 查看对象的属性

```javascript
//自身属性
Object.keys(obj);
//自身属性+共有属性
console.dir(obj);
//判断自身属性还有共有属性
```

## 修改或增加对象的属性

```javascript
//改自身
obj["name"] = "bob";
//批量修改
Object.assign(obj, { age: 18 });
//改原型
let obj = Object.create(common);
```

## ‘name’ in obj 和 obj.hasOwnProperty 的区别

‘name’ in obj 无法判断出属性是不是共有属性
obj.hasOwnProperty 可以判断是不是共有属性
