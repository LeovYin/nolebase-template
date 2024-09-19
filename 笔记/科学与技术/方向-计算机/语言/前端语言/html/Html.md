HTML（HyperText Markup Language）超文本标记语言。是一种标记语言，用于创建和设计网页的结构。HTML 由一系列标签（tag）组成，每个标签都代表着不同的网页元素，如文本、图像、链接等。
# html4
## HTML标准结构
1. 文档声明
2. 设置语言
3. meta元信息，字符编码，浏览器兼容，移动端兼容
4. head标签
5. body标签
## HTML文本标签
### 0.全局属性
1. `id`：可以让label与表单相关联，也可以与css，javascript配合使用 
	注意：不能在`<head>`，`<html>`，`<meta>`，`<script>`，`<style>`，`<title>`中使用！
2. `class`：给标签制定类名，然后就可以用css给标签设置样式
3. `style`：给标签设置css样式
4. `dir`：内容的方向，值：`ltr`，`rtl`。注意：不能在id不能用的标签处使用
5. `title`：鼠标悬浮的注释
6. `lang`：给标签制定语言

### 1.排版标签
1. **h1-h2**：一到六级标签。`h1-h6不能互相嵌套！`
2. **p**：段落标签 `p标签中不能嵌套p标签与h标签`
3. **div**：容器分组标签
 
### 2.文本标签
1. **em** ：着重
2. **strong** ：十分重要的内容
3. **span** : 用于包裹短语的通用容器

### 3.图片标签(img)
插入图片 
属性：
1. `src`：图片位置  
2. `alt`：注释
3. `width`：图片宽度
4. `height`：图片高度`

### 4.超链接(a)
1. 属性：`href:目标位置` `target:打开方式 _blank:在新标签打开 _self:在当前页签中打开`
2. 跳转锚点：在要跳转的超链接处写上#+对应要跳转的id或name(为空则回到顶部)
3. 唤起指定应用
	1. `tel：` 唤起电话 
	2. `mailto:` 唤起电话 
	3. `sms:`唤起短信

### 5.列表
1. 有序列表(Ordered List)\<ol\>:
	1.  `<li>`:列表项
2. 无序列表(Unordered List)\<ul\>:
	1.  `<li>`:列表项
3. 自定义列表(Definition List)\<dl\>:
	1. `<dt>`术语名称
	2. `<dd>`术语描述

### 6.表格(table)
#### 属性
1. table属性：
	1. ` border:` 边框像素大小，默认为0，无边框
	2.  `width：` 表格整体宽度
	3. `height：`表格整体高度
	4. `cellspacing:`调整缝隙距离

2. thead属性：
	1. `height:`调整表头高度
	2. `align：`水平方向对某一方向对齐。left:靠左对齐 center:居中对齐 right:靠右对齐
	3. `valign:`垂直方向对某一方向对齐。top:靠上对齐 middle:靠中对齐 bottom:靠下对齐

3. tbody属性：
	1.  `width：` 表格主体宽度
	2. `height：`表格主体高度
	3.  `align：`水平方向对某一方向对齐。left:靠左对齐 center:居中对齐 right:靠右对齐
	4. `valign:`垂直方向对某一方向对齐。top:靠上对齐 middle:靠中对齐 bottom:靠下对齐

4. tr属性：
	1.  `width：` 行宽度
	2. `height：`行高度
	3.  `align：`水平方向对某一方向对齐。left:靠左对齐 center:居中对齐 right:靠右对齐
	4. `valign:`垂直方向对某一方向对齐。top:靠上对齐 middle:靠中对齐 bottom:靠下对齐

5. td属性(同th)调整一整个：
	1.  `width：` 单元格宽度
	2. `height：`单元格高度
#### 表格构成
1. 表格标题(caption):
2. 表格头部(thead):
3. 表格主体(tbody):
4. 表格脚注(tfoot):
#### 表格结构
1. 行(tr)
2. 单元格(th)
3. 单元数据(td)
#### 跨行与跨列(只看最小的)
1. `colspan` 跨列(单位为列数)
2.  `rowspan` 跨行(单位为行数)
### 7.其他常用标签
1. `br` 换行标签
2. `hr`分割线
3. `pre`按代码原文显示
### 8.表单(form)
#### 属性
1. form属性
	1. `action`：标明处理方式
	2. `target`：用于标明跳转方式
	3. `method`：用于标明get还是post，默认get
2. input属性
	1. `type`：用于标明输入框内文本的类型 ：
		1. `text`：普通文本 
		2. `password`：密码 
		3. `radio`：单选按钮 (要放到同一个name中，并且一定要写一个value标明属性值) 
		4. `checkbox`：多选按钮(需要name与value用于传递信息)
		5. `hidden`：隐藏域
		6. `submit`：提交按钮(value修改显示名称,不要写name)
		7. `reset`：重置按钮
		8. `button`：普通按钮
	2. `name`：用于注明名称
	3. `value`：控制输入框的默认值
	4. `maxlength`：控制输入框的最大长度
	5. `checked`：控制选择按钮的初始值
	6. `disabled`：禁止输入
3. button属性
	1. `type`：用于标明按钮类型 ：
		1. `submit`：提交按钮
		2. `reset`：重置按钮
		3. `button`：普通按钮
#### 表单基本结构
1. `input` 输入框
2. `button`按钮
3. `textarea`文本域
4. `select`下拉框
	1. `option`选项内容(`selected`属性设置默认项)
5. `label` 通过id，连接表单，获取焦点
6. `fieldset`空间分类
	1. `legend`起名，下方放代码
### 9.框架(iframe)
通过iframe的src属性可嵌入普通网页或图片(视频)
#### 属性
1. `src`：位置  
2. `width`：宽度
3. `height`：高度
4. `frameborder`：边框大小
5. `name`：可与超链接或表单的target属性配合使用

## 字符实体
常用字符实体：
1. `&lt;`：小于号（<）
2. `&gt;`：大于号（>）
3. `&amp;`：和号（&）
4. `&quot;`：双引号（"）
5. `&apos;`：单引号（'）
6. `&copy;`：版权符号（©）
7. `&reg;`：注册商标符号（®）
8. `&nbsp;`：不间断空格（ ）
9. `&euro;`：欧元符号（€）
10. `&yen;`：人民币符号（¥）

# Html5
