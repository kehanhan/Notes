# HTML常用标签
## a
### 属性
- href hyper reference超链接
    - 网址
        - http://google.com
        - https://google.com
        - //google.com
    - 路径
        - /a/b/c || a/b/c
        - index.html || /index.html
    - 伪协议
        - javascript:代码;
        - mailto:email
        - tel:phone
    - id
        - href=#xxx
- target 
    - 内置名字
        - _blank
        - _top
        - _parent
        - _self
    - 程序员命名
        - window name
        - iframe name
- ~~download~~ 
- rel=noopener
### 作用
- 跳转外部页面
- 跳转内部锚点
- 跳转到邮箱或电话等
## table
### 相关的标签
- table 表格
- thead 表头部
- tbody 表主题
- tfoot 表尾部
- tr 表的一行
- th 表的开头
- td 表的数据
### 相关的样式
- table-layout
    - auto
    - fixed
- border-collapse
    - 合并表格
- border-spacing
    - 边框间隙
## img
### 作用
- 发出get请求,展示一张图片
### 属性
- alt 文字描述
- height 高度
- weight 宽度
- src 图片地址
### 事件
- onload 加载成功
- onerror 加载失败
### 响应式
- max-width:100%
### [可替换元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced_element)

## form
### 作用
- 发get或post请求,然后刷新页面
### 属性
- action
    - 控制请求的页面
- autocomplete
    - 是否自动填充
- method
    - GET
    - POST
- target
    - 提交的页面
### 事件
- onsubmit
    - 点击提交
## input
### 作用
- 让用户输入内容
### 属性
- type
    - button
    - checkbox
    - email
    - file
    - hidden
    - number
    - password
    - radio
    - search
    - submit
    - tel
    - text
- 其他
    - name
    - autofocus
    - checked
    - disabled
    - maxlength
    - pattern
    - value
    - placeholder
### 事件
- onchange 内容改变
- onfocus 聚焦
- onblur 鼠标移开
### 验证器
- required HTML5新增功能
### 与button的区别
- input里面是纯文本
- button里面可以写标签
### 注意事项
- 一般不监听input的click事件
- form里面的input要有name
- form里面要放一个type=submit才能触发submit事件
## 其他标签
### 标签
- video
- audio
- canvas
- svg
### 注意事项
- 标签的兼容性一定要查看文档