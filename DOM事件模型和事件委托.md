# DOM事件模型和事件委托

## 事件的传播
一个事件发生后，会在子元素和父元素之间传播(propagation)，这种传播分成三个阶段

第一阶段：从window对象传导到目标节点（上层传到底层），称为“**捕获阶段**“(capture phase)

第二阶段：在目标节点上触发，称为“**目标阶段**”(target phase)

第三阶段：从目标节点传导回window对象（从底层传回上层），称为“**冒泡阶段**”(bubbling phase)

这种三阶段的传播模型，使得同一个事件会在多个节点上触发

## DOM事件委托

由于事件会在冒泡阶段向上传播到父节点，因此可以把子节点的监听函数定义在父节点上，由父节点的监听函数统一处理多个子元素的事件。这种方法叫做事件委托

## 阻止捕获、阻止冒泡和取消默认事件

#### 阻止捕获、阻止冒泡
如果希望事件到某个节点为止，不再传播，可以使用事件对象的stopPropagation方法。
event.stopPropagation()可阻止捕获、冒泡

```javascript
const $test = $('.test')
// 阻止捕获
$test.on('click', (e) => {
  e.stopPropagation();
}, true);

// 阻止冒泡
$test.on('click', (e) => {
  e.stopPropagation();
}, false);
```

#### 阻止默认事件

event.preventDefault() 阻止默认事件——表单提交，a标签跳转，右键菜单等 


```javascript
const $test = $('.test');
$test.on( 'click', (e) => {
    e.preventDefault();
})
```

- Bubbles —— 该事件是否冒泡，所有冒泡都可取消
- Cancelable —— 是否支持开发者阻止默认事件
- 不是所有的事件都能冒泡。以下事件不冒泡：blur、focus、load、unload
- 如果想要彻底取消该事件，不再触发后面所有click的监听函数，可以使用stopImmediatePropagation方法。