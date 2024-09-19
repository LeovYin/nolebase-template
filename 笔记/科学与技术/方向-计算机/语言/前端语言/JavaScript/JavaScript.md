JavaScript是一种广泛应用于网页开发的脚本语言，它可以用来为网页增加动态功能和交互性。JavaScript最初由Netscape公司的Brendan Eich在1995年设计开发，是一种基于对象和事件驱动的脚本语言。
主要被设计用于在网页上实现动态效果，增加用户与网页的交互性。

# JavaScript的作用
1. `客户端脚本`：用于在用户浏览器中执行，实现动态效果和用户交互
2. `网页开发`：与HTML与CSS协同工作，使得网页具有更强的交互性和动态性
3. `后端开发`：使用Node.js，JavaScript也可以在服务端中运行，实现服务端应用的开发

# JavaScript的导入方式
1. 内联代码，放在`<script>`标签内
2. 外部引入，用`<script>的src属性`
3. 一般都会把 `<script>`写在body标签最末尾，实现更好的用户体验

# JavaScript的基本语法
## 申明变量
1. `var`：声明的变量具有函数作用域
2. `let`：声明的变量具有块级作用域(更灵活，更安全)
3. `const`：申明一个常量

## 控制语句
1. 条件语句
	1. if
	2. else if
	3. else
2. 循环语句
	1. while
	2. for
	3. break
	4. continue

## 函数
1. 语法
```javascript
function function_name(参数1,参数2,参数3,...){
//函数体
return 返回值;
}
```

## 事件
### 常见事件

| 事件         | 描述    | 事件          | 描述       |
| ---------- | ----- | ----------- | -------- |
| onClick    | 点击事件  | onMouseOver | 鼠标经过     |
| onMouseOut | 鼠标移出  | onChange    | 文本内容改变事件 |
| onSelect   | 文本框选中 | onFoucus    | 光标聚集     |
| onBlur     | 移开光标  |             |          |
### 事件绑定
1. `HTML`属性：通过将JavaScript中的函数名作为HTML中的属性，进行链接
2. `DOM`属性
3. `addEventListener`方法，该方法一共有三个参数，第一个参数是事件类型（例如：`click` ；写第一个参数时需要打单引号且没有前缀 `on`)；第二个参数是触发该事件时要调用的函数；第三个参数为布尔值，`false`时表示在事件冒泡过程中注册事件处理程序，`ture`时表示在事件捕获过程中注册事件处理程序),默认为`false`                                          
事件流：事件捕获阶段、‌事件目标处理函数阶段、‌事件冒泡阶段
```javascript
<body>
<div id="div1">div1</div>
</body>
<script>
var div1=document.getElementById('div1');
div1.addEventListener('click',div1Fun);
function div1Fun(event){
alart(event.type);//事件对象的类型，如`click`
alart(event.target);//事件对象的元素，比如是一个按钮
}777777
```



## DOM
DOM 是文档对象模型（Document Object Model）的缩写。DOM 是一种用于表示和操作网页文档的标准编程接口，它将网页文档表示为一个树状结构，其中每个节点都是文档中的一个元素、属性或文本。

常用DOM接口
1. `document`：代表整个文档（网页），是 DOM 树的根节点，可以用来获取文档中的元素和执行操作。
2. `getElementById()`：通过元素的 ID 属性获取对应的元素。
3. `getElementsByClassName()`：通过元素的类名获取一组元素。
4. `getElementsByTagName()`：通过元素的标签名获取一组元素。
5. `querySelector()`：通过 CSS 选择器获取匹配的第一个元素。
6. `querySelectorAll()`：通过 CSS 选择器获取匹配的所有元素。
7. `parentNode`：获取当前节点的父节点
8. `childNodes`：获取当前节点的所有子节点。
9. `appendChild()`**：向指定父节点添加一个新的子节点。
10. `removeChild()`：从父节点中移除一个子节点。
11. `innerHTML`：获取或设置元素的 HTML 内容。
12. `innerText`：获取或设置元素的文本内容。
13. `setAttribute()`：设置元素的属性。
14. `addEventListener()`：为元素添加事件监听器。
15. `classList`：获取元素的类列表，可以进行类的添加、删除、切换等操作。

*[ ] 