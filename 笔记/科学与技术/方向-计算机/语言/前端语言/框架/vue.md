# 安装教程
1. 安装vue.js
    用管理员身份运行cmd，并输入以下代码。
    `npm install vue -g`或者`cnom install vue -g`
2.安装脚手架vue-cli 3.x版本
    `npm install @vue/cli -g`
3.安装vue-router
    `npm install -g vue-router`
4.查看vue版本
    `vue --version`            //查看脚手架版本
    `npm list vue -g`        //全局查看vue版本
    `npm list vue`             //查看版本--可能为空，用上一个代码查看一下
5.创建Vue项目，一般在vscode中创建
    (1) 选择一个文件夹，右键选择vscode打开
    (2) 选择【终端】，再点击【新建终端】
    (3) 在终端输入下述代码，创建项目`vue create name'
    (4) 前两个是默认配置，最后 那个是 自己配置，然后按entre键 
    (5) 选择vue版本，然后按enter键
    (6) 选择路由器模式，可以直接按enter键，默认选择Y
    (7) 其余的直接按enter键就可以了

Vue.js 提供一个官方命令行工具，可用于快速搭建大型单页应用。

## 全局安装 vue-cli
$ cnpm install --global vue-cli
## 创建一个基于 webpack 模板的新项目
$ vue init webpack my-project
## 这里需要进行一些配置，默认回车即可
This will install Vue 2.x version of the template.

For Vue 1.x use: vue init webpack#1.0 my-project

? Project name my-project
? Project description A Vue.js project
? Author runoob <test@runoob.com>
? Vue build standalone
? Use ESLint to lint your code? Yes
? Pick an ESLint preset Standard
? Setup unit tests with Karma + Mocha? Yes
? Setup e2e tests with Nightwatch? Yes

   vue-cli · Generated "my-project".

   To get started:
   
     cd my-project
     npm install
     npm run dev
   
   Documentation can be found at https://vuejs-templates.github.io/webpack

进入项目，安装并运行：

$ cd my-project
$ cnpm install
$ cnpm run dev
 DONE  Compiled successfully in 4388ms

> Listening at http://localhost:8080


# 目录结构
## vue构造目录
### 目录解析

| 目录/文件        | 说明                                                                                                                                                                                          |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| build        | 项目构建(webpack)相关代码                                                                                                                                                                           |
| config       | 配置目录，包括端口号等。我们初学可以使用默认的。                                                                                                                                                                    |
| node_modules | npm 加载的项目依赖模块                                                                                                                                                                               |
| src          | 这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：<br><br>- assets: 放置一些图片，如logo等。<br>- components: 目录里面放了一个组件文件，可以不用。<br>- App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。<br>- main.js: 项目的核心文件。 |
| static       | 静态资源目录，如图片、字体等。                                                                                                                                                                             |
| test         | 初始测试目录，可删除                                                                                                                                                                                  |
| .xxxx文件      | 这些是一些配置文件，包括语法配置，git配置等。                                                                                                                                                                    |
| index.html   | 首页入口文件，你可以添加一些 meta 信息或统计代码啥的。                                                                                                                                                              |
| package.json | 项目配置文件。                                                                                                                                                                                     |
| README.md    | 项目的说明文档，markdown 格式                                                                                                                                                                         |

## Vue 项目打包

打包 Vue 项目使用以下命令：

npm run build

执行完成后，会在 Vue 项目下生成一个 **dist** 目录，一般包含 index.html 文件及 static 目录，static 目录包含了静态文件 js、css 以及图片目录 images。

![](https://www.runoob.com/wp-content/uploads/2017/01/BEE1DA18-407F-4979-9DFD-D61FB77E2671.jpg)

如果直接双击 index.html 打开浏览器，页面可能是空白了，想要正常显示，可以修改 index.html 文件中 js、css 文件的路径。

例如我们打开 dist/index.html 文件看到路径是绝对路径：

<link href=/static/css/app.33da80d69744798940b135da93bc7b98.css rel=stylesheet>
<script type=text/javascript src=/static/js/app.717bb358ddc19e181140.js></script>

我们把 js、css 路径修改为相对路径：

<link href=static/css/app.33da80d69744798940b135da93bc7b98.css rel=stylesheet>
<script type=text/javascript src=static/js/app.717bb358ddc19e181140.js></script>

这样直接双击 dist/index.html 文件就可以在浏览器中看到效果了。
# vue.js起步
每个 Vue 应用都需要通过实例化 Vue 来实现。

语法格式如下：

var vm = new Vue({
  // 选项
})

接下来让我们通过实例来看下 Vue 构造器中需要哪些内容：

## 实例

<div id="vue_det">
<h1>site : {{site}}</h1>
<h1>url : {{url}}</h1>
<h1>{{details()}}</h1> 
</div> 


<script type="text/javascript">
var vm = new Vue({ el: '#vue_det', data: { site: "菜鸟教程", url: "www.runoob.com", alexa: "10000" }, methods: { details: function() { return this.site + " - 学的不仅是技术，更是梦想！"; } } }) </script>

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-start1)



可以看到在 Vue 构造器中有一个el 参数，它是 DOM 元素中的 id。在上面实例中 id 为 vue_det，在 div 元素中：

<div id = "vue_det"></div>

这意味着我们接下来的改动全部在以上指定的 div 内，div 外部不受影响。

接下来我们看看如何定义数据对象。

**data** 用于定义属性，实例中有三个属性分别为：site、url、alexa。

methods 用于定义的函数，可以通过 return 来返回函数值。

{{ }} 用于输出对象属性和函数返回值。

<div id="vue_det">
    <h1>site : {{site}}</h1>
    <h1>url : {{url}}</h1>
    <h1>{{details()}}</h1>
</div>

当一个 Vue 实例被创建时，它向 Vue 的响应式系统中加入了其 data 对象中能找到的所有的属性。当这些属性的值发生改变时，html 视图将也会产生相应的变化。

## 实例

<div id="vue_det">
<h1>site : {{site}}</h1> 
<h1>url : {{url}}</h1>
<h1>Alexa : {{alexa}}</h1>
</div> <script type="text/javascript"> // 我们的数据对象 
var data = { site: "菜鸟教程", url: "www.runoob.com", alexa: 10000} 
var vm = new Vue({ el: '#vue_det', data: data }) // 它们引用相同的对象！
document.write(vm.site === data.site) // true document.write("<br>") // 设置属性也会影响到原始数据 vm.site = "Runoob" document.write(data.site + "<br>") // Runoob
// ……反之亦然
data.alexa = 1234 document.write(vm.alexa) // 1234 </script>

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-start2)

除了数据属性，Vue 实例还提供了一些有用的实例属性与方法。它们都有前缀 $，以便与用户定义的属性区分开来。例如：

## 实例
<div id="vue_det">  
<h1>site : {{site}}</h1>
<h1>url : {{url}}</h1>
<h1>Alexa : {{alexa}}</h1>
</div> <script type="text/javascript"> 
// 我们的数据对象 var data = { site: "菜鸟教程", url: "www.runoob.com", alexa: 10000} 
var vm = new Vue({ el: '#vue_det', data: data }) document.write(vm.$data === data) // true document.write("<br>") document.write(vm.$el === document.getElementById('vue_det')) // true </script>

# vue.js模板语法
## 插值

### 文本

数据绑定最常见的形式就是使用 {{...}}（双大括号）的文本插值：

## 文本插值

```vue
<div id="app"> <p>{{ message }}</p> </div>
```

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-hw)

### Html

使用 v-html 指令用于输出 html 代码：

## v-html 指令

```vue
<div id="app">
<div v-html="message"></div>
</div>
<script>
new Vue({
el: '#app', 
data: {
message: '<h1>菜鸟教程</h1>' } 
}) 
</script>
```

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-v-html)

### 属性

HTML 属性中的值应使用 v-bind 指令。

以下实例判断 use 的值，如果为 true 使用 class1 类的样式，否则不使用该类：

## v-bind 指令

```vue
<div id="app">
<label for="r1">修改颜色</label>   //一个标签，给 `<input>` 元素提供了说明文字。
<input type="checkbox" v-model="use" id="r1">     //这是一个复选框，使用了 Vue 的 `v-model` 指令。`v-model` 是 Vue 提供的双向数据绑定指令，它使得输入框的值（这里是复选框的选中状态）和 Vue 实例中的 `data` 属性 `use` 绑定在一起。也就是说，当用户勾选或取消勾选复选框时，`use` 的值会自动更新为 `true` 或 `false`。

<br><br>
<div v-bind:class="{'class1': use}"> v-bind:class 指令 </div>    //使用了 Vue 的 `v-bind:class` 指令。`v-bind:class` 用于动态绑定 CSS 类。其中键是 CSS 类名，值是布尔值。`{'class1': use}` 表示当 `use` 的值为 `true` 时，`class1` 这个 CSS 类将会被添加到 `div` 元素上。如果 `use` 的值为 `false`，`class1` 类将不会应用。


</div> 
<script> new Vue({
el: '#app', 
data:{ use: false }
});
</script>
```
  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-v-bind)

`v-bind` 是 Vue.js 中的一个指令，用于动态绑定一个或多个 HTML 属性的值。在 Vue.js 中，`v-bind` 可以使你轻松地将 Vue 实例的数据绑定到 DOM 元素的属性上，从而实现数据和视图的双向绑定。下面是 `v-bind` 的详细讲解：

### 基本用法

#### 1. 绑定单个属性

`<div v-bind:id="dynamicId">Content</div>`

`new Vue({   el: '#app',   data: {     dynamicId: 'unique-id'   } });`

在这个例子中，`v-bind:id="dynamicId"` 将 `id` 属性绑定到 Vue 实例中的 `dynamicId` 数据属性。当 `dynamicId` 的值发生变化时，`id` 属性的值也会自动更新。

#### 2. 绑定多个属性

`<div v-bind="{ id: dynamicId, class: dynamicClass }">Content</div>`

`new Vue({   el: '#app',   data: {     dynamicId: 'unique-id',     dynamicClass: 'active'   } });`

这里的 `v-bind` 绑定了多个属性，通过对象语法同时设置 `id` 和 `class`。`id` 会被设置为 `unique-id`，`class` 会被设置为 `active`。这种方式特别适合在需要同时绑定多个属性时使用。

### 动态绑定和计算属性

#### 1. 动态绑定属性值

`<img v-bind:src="imageSrc" alt="Dynamic Image">`

`new Vue({   el: '#app',   data: {     imageSrc: 'path/to/image.jpg'   } });`

在这个例子中，`v-bind:src` 将 `img` 标签的 `src` 属性绑定到 `imageSrc` 数据属性。这样，当 `imageSrc` 的值发生变化时，图片的源路径会自动更新。

#### 2. 使用计算属性动态绑定

`<button v-bind:style="buttonStyle">Click me</button>`

`new Vue({   el: '#app',   data: {     color: 'blue',     fontSize: '16px'   },   computed: {     buttonStyle() {       return {         color: this.color,         fontSize: this.fontSize       };     }   } });`

在这个例子中，`v-bind:style` 将按钮的 `style` 属性绑定到一个计算属性 `buttonStyle`。计算属性根据 `color` 和 `fontSize` 的值返回一个对象，该对象定义了按钮的样式。当 `color` 或 `fontSize` 的值变化时，按钮的样式会自动更新。

### 语法变体

#### 1. 短语法

在 Vue.js 中，`v-bind` 可以用简写 `:` 代替，这样写法更简洁：

`<img :src="imageSrc" alt="Dynamic Image">`

#### 2. 绑定多个属性

同样地，绑定多个属性时也可以使用简写：

`<div :id="dynamicId" :class="dynamicClass">Content</div>`

#### 3. 绑定属性到动态表达式

你可以将 `v-bind` 与 JavaScript 表达式结合使用：

`<div :[dynamicAttr]="dynamicValue">Content</div>`

`new Vue({   el: '#app',   data: {     dynamicAttr: 'id',     dynamicValue: 'unique-id'   } });`

在这个例子中，`v-bind` 的属性名是由 `dynamicAttr` 的值决定的，即动态设置 `id` 属性为 `unique-id`。

### 表达式

Vue.js 都提供了完全的 JavaScript 表达式支持。

avaScript 表达式

```vue
<div id="app"> 
{{5+5}}<br>
{{ ok ? 'YES' : 'NO' }}<br>
{{ message.split('').reverse().join('') }}
<div v-bind:id="'list-' + id">菜鸟教程</div>
</div>

<script> new Vue({ el: '#app', data: { ok: true, message: 'RUNOOB', id : 1 } }) </script>
```

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-js-expr)

## 指令

指令是带有 v- 前缀的特殊属性。

指令用于在表达式的值改变时，将某些行为应用到 DOM 上。如下例子：
### 实例

```javascript
<div id="app">
    <p v-if="seen">现在你看到我了</p>
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    seen: true
  }
})
</script>
```
这里， v-if 指令将根据表达式 seen 的值(true 或 false )来决定是否插入 p 元素。

修饰符是以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。例如，**.prevent** 修饰符告诉 v-on 指令对于触发的事件调用 **event.preventDefault()**：

```vue
<form v-on:submit.prevent="onSubmit"></form>
```

`v-bind` 是用于绑定属性，`v-on` 是用于绑定方法。

### v-bind 缩写

Vue.js 为两个最为常用的指令提供了特别的缩写：

```vue
<!-- 完整语法 -->
<a v-bind:href="url"></a>
<!-- 缩写 -->
<a :href="url"></a>
```

### v-on 缩写

```vue
<!-- 完整语法 -->
<a v-on:click="doSomething"></a>
<!-- 缩写 -->
<a @click="doSomething"></a>
```

### 用户输入
在 input 输入框中我们可以使用 v-model 指令来实现双向数据绑定：

#### 双向数据绑定
```
<div id="app">
<p>{{ message }}</p> 
<input v-model="message"> </div>
<script> new Vue({ 
el: '#app',
data: { message: 'Runoob!' } }) </script>
```

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-v-model)
v-model 指令用来在 input、select、textarea、checkbox、radio 等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值。

#### 实例
```vue
<div id="app"> 
<p>{{ message }}</p>
<button v-on:click="reverseMessage">反转字符串</button>
</div> 
<script> new Vue({ 
el: '#app',
data: { message: 'Runoob!' }, 
methods: { 
reverseMessage: function () {
this.message = this.message.split('').reverse().join('') } 
} 
}) </script>
```

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-reverse-message)

### 过滤器
过滤器是一种用于格式化数据的工具，通常用于展示数据之前对其进行一些处理。过滤器可以在 Vue.js 模板中使用管道符来调用。

#### 语法

`{{ message | capitalize }}`

#### 使用示例

假设你有一个 Vue 实例，其中包含一个消息字符串：

```
new Vue({ 
el: '#app', 
data: {  
message: 'hello world' 
}, 
filters: {
capitalize(value) { 
if (!value) return ''; 
return value.charAt(0).toUpperCase() + value.slice(1); 
} 
} });
```

在 HTML 模板中，你可以使用过滤器来格式化消息：

`<div id="app">     {{ message | capitalize }} </div>`

在这个示例中，`capitalize` 过滤器将字符串的首字母转换为大写，结果显示为 `Hello world`。

#### 2. **计算属性（Computed Properties）**

计算属性是 Vue.js 的一项强大功能，用于处理需要依赖数据的复杂逻辑。计算属性在模板中可以像普通属性一样访问，并且具有缓存功能，只有当其依赖的数据发生变化时才会重新计算。

#### 语法

```<div v-bind:id="rawId | formatId"></div>```

#### 使用示例

假设你有一个 Vue 实例，其中有一个原始 ID 和一个计算属性来格式化这个 ID：

```vue
new Vue({  
el: '#app',  
data: {     
rawId: '123abc'     },  
computed: {formatId() { 
// 假设我们要将 ID 转换为大写并加上前缀  
return 'ID-' + this.rawId.toUpperCase();         }     } });
````

在 HTML 模板中，你可以使用计算属性：

```vue
<div id="app">     <div v-bind:id="formatId">Content</div> </div>
```

在这个示例中，`formatId` 计算属性将 `rawId` 转换为大写并加上 `ID-` 前缀。最终 `id` 属性的值将变为 `ID-123ABC`。
# vue.js条件语句
## v-else-if
v-else-if 在 2.1.0 新增，顾名思义，用作 v-if 的 else-if 块。可以链式的多次使用：
判断 type 变量的值：

```vue
<div id="app">
<div v-if="type === 'A'"> 
A
</div>
<div v-else-if="type === 'B'"> 
B 
</div>
<div v-else-if="type === 'C'">
C
</div>
<div v-else> Not A/B/C </div>
</div>
<script> new Vue({
el: '#app', 
data: { type: 'C' }
}) </script>
```

  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-v-else-if)

> v-else 、v-else-if 必须跟在 v-if 或者 v-else-if之后。

#  Vue.js 循环语句
循环使用 v-for 指令。

v-for 指令需要以 **site in sites** 形式的特殊语法， sites 是源数据数组并且 site 是数组元素迭代的别名。

v-for 可以绑定数据到数组来渲染一个列表：

## v-for 指令

```vue
<div id="app">
<ol> 
<li v-for="site in sites">
{{ site.name }}
</li>
</ol>
</div>
<script> new Vue({
el: '#app',
data: {
sites: [
{ name: 'Runoob' },
{ name: 'Google' },
{ name: 'Taobao' } 
] } }) </script>
```
这里面的site是元素，sites是数组名（两者均可替换）
  
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-v-for)

#  Vue.js 计算属性
计算属性关键词: computed。

计算属性在处理一些复杂逻辑时是很有用的。

可以看下以下反转字符串的例子：
```vue
<div id="app">
  <p>原始字符串: {{ message }}</p>
  <p>计算后反转字符串: {{ reversedMessage }}</p>
</div>
 
<script>
var vm = new Vue({
  el: '#app',
  data: {
    message: 'Runoob!'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
</script>
```

# Vue.js 监听属性
Vue.js 监听属性 watch，我们可以通过 watch 来响应数据的变化。
```vue
<div id = "computed_props">
    千米 : <input type = "text" v-model = "kilometers">
    米 : <input type = "text" v-model = "meters">
</div>
<p id="info"></p>
<script type = "text/javascript">
    var vm = new Vue({
    el: '#computed_props',
    data: {
        kilometers : 0,
        meters:0
    },
    methods: {
    },
    computed :{
    },
    watch : {      //当千米变了调用下列函数
        kilometers:function(val) {
            this.kilometers = val;
            this.meters = this.kilometers * 1000
        },
        meters : function (val) {   //当米变了调用下列函数
            this.kilometers = val/ 1000;
            this.meters = val;
        }
    }
    });
    // $watch 是一个实例方法           下面这两个值不用我们手动赋值，Vue 内部机制自动赋值
    vm.$watch('kilometers', function (newValue, oldValue) {
    // 这个回调将在 vm.kilometers 改变后调用
    document.getElementById ("info").innerHTML = "修改前值为: " + oldValue + "，修改后值为: " + newValue;
})
</script>
```
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-watch)
# Vue.js 样式绑定
class 与 style 是 HTML 元素的属性，用于设置元素的样式，我们可以用 v-bind 来设置样式属性。
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.net/vue/2.2.2/vue.min.js"></script>
<style>
.active {
	width: 100px;
	height: 100px;
	background: green;
}
</style>
</head>
<body>
<div id="app">
  <div v-bind:class="{ 'active': isActive }"></div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    isActive: true
  }
})
</script>
</body>
</html>
```
如果isActive为真，则渲染active
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-class1)
还可以渲染多个样式，用它们的真值来控制是否渲染上去
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.net/vue/2.2.2/vue.min.js"></script>
<style>
.active {
	width: 100px;
	height: 100px;
	background: green;
}
.text-danger {
	background: red;
}
</style>
</head>
<body>
<div id="app">
  <div class="static"
     v-bind:class="{ 'active': isActive, 'text-danger': hasError }">
  </div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    isActive: true,
	hasError: true
  }
})
</script>
</body>
</html>
```
当然，还可以把多个样式合并到一个属性里去，感觉这样更简洁，如下：
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.net/vue/2.2.2/vue.min.js"></script>
<style>
.active {
	width: 100px;
	height: 100px;
	background: green;
}
.text-danger {
	background: red;
}
</style>
</head>
<body>
<div id="app">
  <div v-bind:class="classObject"></div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    classObject: {
      active: true,
      'text-danger': true
    }
  }
})
</script>
</body>
</html>
```
还有更灵活的进阶版，如下
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.net/vue/2.2.2/vue.min.js"></script>
<style>
.base {
  width: 100px;
  height: 100px;
}

.active {
  background: green;
}

.text-danger {
  background: red;
}
</style>
</head>
<body>
<div id="app">
  <div v-bind:class="classObject"></div>
</div>
<script>

new Vue({
  el: '#app',
  data: {
    isActive: true,
    error: {
      value: true,
      type: 'fatal'  //错误类型为 'fatal' 通常表示一个严重错误，这种错误会导致程序无法继续正常运行
    }
  },
  computed: {
    classObject: function () {
      return {
  base: true,
        active: this.isActive && !this.error.value,
        'text-danger': this.error.value && this.error.type === 'fatal',
      }
    }
  }
})
</script>
</body>
</html>
```
### 数组语法

我们可以把一个数组传给 **v-bind:class** ，实例如下：
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.net/vue/2.2.2/vue.min.js"></script>
<style>
.active {
	width: 100px;
	height: 100px;
	background: green;
}
.text-danger {
	background: red;
}
</style>
</head>
<body>
<div id="app">
	<div v-bind:class="[activeClass, errorClass]"></div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    activeClass: 'active',
    errorClass: 'text-danger'
  }
})
</script>
</body>
</html>
```
数组里的样式都会渲染到界面上去，但是一个是让背景颜色变绿一个是变红，背景 颜色是看哪个在css中是后定义的，很明显这个背景颜色为红色

## Vue.js style(内联样式)
我们可以在 **v-bind:style** 直接设置样式：
直接把样式绑定到一个对象上
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.net/vue/2.2.2/vue.min.js"></script>
</head>
<body>
<div id="app">
  <div v-bind:style="styleObject">菜鸟教程</div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    styleObject: {
      color: 'green',
      fontSize: '30px'
    }
  }
})
</script>
</body>
</html>
```

v-bind:style 可以使用数组将多个样式对象应用到一个元素上：
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.net/vue/2.2.2/vue.min.js"></script>
</head>
<body>
<div id="app">
  <div v-bind:style="[baseStyles, overridingStyles]">菜鸟教程</div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    baseStyles: {
      color: 'green',
      fontSize: '30px'
    },
	overridingStyles: {
      'font-weight': 'bold'
    }
  }
})
</script>
</body>
</html>
```
注意：当 **v-bind:style** 使用需要特定前缀的 CSS 属性时，如 transform ，Vue.js 会自动侦测并添加相应的前缀。
# Vue.js 事件处理器
事件监听可以使用 v-on 指令：
```vue
<div id="app">
  <button v-on:click="counter += 1">增加 1</button>
  <p>这个按钮被点击了 {{ counter }} 次。</p>
</div>
 
<script>
new Vue({
  el: '#app',
  data: {
    counter: 0
  }
})
</script>
```
[尝试一下 »](https://www.runoob.com/try/try.php?filename=vue2-v-on2)
通常情况下，我们需要使用一个方法来调用 JavaScript 方法。

v-on 可以接收一个定义的方法来调用。
```vue
<div id="app">
   <!-- `greet` 是在下面定义的方法名 -->
  <button v-on:click="greet">Greet</button>
</div>
 
<script>
var app = new Vue({
  el: '#app',
  data: {
    name: 'Vue.js'
  },
  // 在 `methods` 对象中定义方法
  methods: {
    greet: function (event) {
      // `this` 在方法里指当前 Vue 实例
      alert('Hello ' + this.name + '!')
      // `event` 是原生 DOM 事件
      if (event) {
          alert(event.target.tagName)
      }
    }
  }
})
// 也可以用 JavaScript 直接调用方法
app.greet() // -> 'Hello Vue.js!'
</script>
```
除了直接绑定到一个方法，也可以用内联 JavaScript 语句：
```vue
<div id="app">
  <button v-on:click="say('hi')">Say hi</button>
  <button v-on:click="say('what')">Say what</button>
</div>
 
<script>
new Vue({
  el: '#app',
  methods: {
    say: function (message) {
      alert(message)
    }
  }
})
</script>
```
