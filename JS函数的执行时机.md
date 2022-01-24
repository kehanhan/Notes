# JS 函数的执行时机

## 为什么如下代码会打印 6 个 6

```javascript
let i = 0;
for (i = 0; i < 6; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
```

因为 setTimeOut 会在一段时间后执行,而此时 for 循环已经执行完,i 的值为 6,所以会打印 6 个 6

## 让上面代码打印 0、1、2、3、4、5 的方法

```javascript
for (let i = 0; i < 6; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
```

使用 let 会单独创建一个作用域 相当于有 6 个 i ，相当于以下代码

```javascript
(let i = 0) {
    setTimeout(()=>{
        console.log(i)
    },0)
}

(let i = 1) {
    setTimeout(()=>{
        console.log(i)
    },0)
}

(let i = 2) {
    setTimeout(()=>{
        console.log(i)
    },0)
};
(let i = 3) {
    setTimeout(()=>{
        console.log(i)
    },0)
}

(let i = 4) {
    setTimeout(()=>{
        console.log(i)
    },0)
}

(let i = 5) {
    setTimeout(()=>{
        console.log(i)
    },0)
};
```
