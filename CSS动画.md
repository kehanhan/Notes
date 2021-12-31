# CSS动画

## 浏览器渲染原理
- 根据HTML构建HTML树(DOM)
- 根据CSS构建CSS树(CSSOM)
- 将两颗树合并成一颗渲染树(render tree)
- Layout布局 (文档流、盒模型、计算大小和位置)
- Paint绘制(把边框颜色、文字颜色、阴影等画出来)
- Compose合成(根据层叠关系展示画面)

## 动画的两种做法

### transition(过渡)
- 作用
    - 补充中间帧
- 语法
    - transition： 属性名 时长 过渡方式 延迟
    - transition: left 200ms linear
    - 可以用逗号分隔两个不同属性
    - transition: left 200ms,top 400ms
    - 可以用 all 代表所有属性
    - transition: all 200ms
    - 过渡方式有：linear｜ ease｜ease-in｜ease-out｜ease- in-out｜ cubic-bezier ｜ step-start ｜ step-end ｜ steps


### animation
- 语法
    - animation： 时长 ｜ 过渡方式 ｜ 延迟 ｜ 次数 ｜ 方向 ｜ 填充模式是否暂停 ｜ 动画名；
    - 时长：1s或者1000ms
    - 过渡方式：跟 transition 取值一样，如 linear
    - 次数：3或者2.4或者 infinite
    - 方向：reverse｜alternate｜alternate-reverse
    - 填充模式：none ｜ forwards ｜ backwards ｜ both
    - 是否暂停：paused｜ running
    - 以上所有属性都有对应的单独属性

## CSS动画优化
- [Google的文章](https://developers.google.com/web/fundamentals/performance/rendering/stick-to-compositor-only-properties-and-manage-layer-count)
- JS优化
    - 使用 requestAnimationFrame 代替 setTimeout或 setlnterval
- CSS优化
    - 使用 will-change 或 translate