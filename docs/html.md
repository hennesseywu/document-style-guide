## HTML约定

### 1.文档类型

统一使用HTML5的标准文档类型：<!DOCTYPE html>；

HTML5文档类型具备前后兼容的特质，并且易记易书写

在文档doctype申明之前，不允许加上任何非空字符；

任何出现在doctype申明之前的字符都将使得你的HTML文档进入非标准模式

不允许添加 <meta> 标签强制改变文档模式。

避免出现不可控的问题

### 2.省略type属性

在调用CSS和JavaScript时，可以将type属性省略不写

不允许：

```html
<link type="text/css" rel="stylesheet" href="base.css" />
<script type="text/javascript" src="base.js"></script>

```

应该：

```html
<link rel="stylesheet" href="base.css" />
<script src="base.js"></script>
```

因为HTML5在引入CSS时，默认type值为text/css；在引入JavaScript时，默认type值为text/javascript

### 3.省略属性值

非必须属性值可以省略

不允许：

```html
<input type="text" readonly="readonly" />
<input type="text" disabled="disabled" />

```

应该：

```html
<input type="text" readonly />
<input type="text" disabled />

```

这里的 readonly 和 disabled 属性的值是非必须的，可以省略不写，我们知道HTML5表单元素新增了很多类似的属性，如: required

### 4.用双引号包裹属性值

所有的标签属性值必须要用双引号包裹，同时也不允许有的用双引号，有的用单引号的情况

不允许：

```html
<a href=http://www.qunar.com class="home">去哪儿网</a>

```

应该：

```html

<a href="http://www.qunar.com" class="home">去哪儿网</a>

```
### 5.嵌套

所有元素必须正确嵌套

不允许交叉；

不允许：

```html
<span><dfn>交叉嵌套</span></dfn>

```

应该：

```html
<span><dfn>交叉嵌套</dfn></span>

```
不允许非法的子元素嵌套。

不允许：

```html
<ul>
　　<h3>xx列表</h3>
　　<li>asdasdsdasd</li>
　　<li>asdasdsdasd</li>
</ul>

```
应该：

```html

<div>
　　<h3>xx列表</h3>
　　<ul>
　　　　<li>asdasdsdasd</li>
　　　　<li>asdasdsdasd</li>
　　</ul>
</div>

```
不推荐inline元素包含block元素；

不推荐：

```html
<span>
　　<h1>这是一个块级h1元素</h1>
　　<p>这是一个块级p元素</p>
</span>
```

推荐：

```html
<div>
　　<h1>这是一个块级h1元素</h1>
　　<p>这是一个块级p元素</p>
</div>

```

### 6.标签闭合

所有标签必须闭合

不允许：

```html
<div>balabala...
<link rel="stylesheet" href="*.css">
```

应该：

```html
<div>balabala...</div>
<link rel="stylesheet" href="*.css" />

```
虽然有些标记没有要求必须关闭，但是为了避免出错的几率，要求必须全部关闭，省去判断某标记是否需要关闭的时间

### 7.多媒体替代方案

为img元素加上alt属性；

为视频内容提供音轨替代；

为音频内容提供字母替代等等。

不推荐：

```html

<img src="banner.jpg" />

```

推荐：

```html
<img src="banner.jpg" alt="520即将到来，爱就大声说出来" />

```

alt属性的内容为对该图片的简要描述，这对于盲人用户和图像损毁都非常有意义，即无障碍。对于纯粹的装饰性图片，alt属性值可以留空，如 alt=""

### 8.有效操作

为表单元素label加上for属性

不允许：

```html

<input type="radio" name="color" value="0" /><label>蓝色</label>
<input type="radio" name="color" value="1" /><label>粉色</label>

```

应该：

```html

<input type="radio" id="blue" name="color" value="0" /><label for="blue">蓝色</label>
<input type="radio" id="pink" name="color" value="1" /><label for="pink">粉色</label>

```

for属性能让点击label标签的时候，同时focus到对应的 input 和 textarea上，增加响应区域

### 9.按模块添加注释

在每个模块开始和结束的地方添加注释

```html
<!-- 新闻列表模块 -->
<div class="m-news g-mod"
...
<!-- /新闻列表模块 -->

<!-- 排行榜模块 -->
<div class="m-topic g-mod"
...
<!-- /排行榜模块 -->

```

注释内容左右两边保留和注释符号有1个空格位，在注释内容内不允许再出现中划线“-”，某些浏览器会报错。

注释风格保持与原生HTML的语法相似：成对出现 <!-- comment --><!-- /comment -->


### 10.格式

将每个块元素、列表元素或表格元素都放在新行；

inline元素视情况换行，以长度不超过编辑器一屏为宜；

每个子元素都需要相对其父级缩进（参见缩进约定）。

不推荐：
```html

<div><h1>asdas</h1><p>dff<em>asd</em>asda<span>sds</span>dasdasd</p></div>

```

推荐：

```html

<div>
　　<h1>asdas</h1>
　　<p>dff<em>asd</em>asda<span>sds</span>dasdasd</p>
</div>

```
### 11.语义化标签

根据HTML元素的本身用途去使用它们；

禁止使用被废弃的用于表现的标签，如 center, font 等；

部分在XHTML1中被废弃的标签，在HTML5中被重新赋予了新的语义，在选用时请先弄清其语义，如:b, i, u等。

不允许：

```html

<p>标题</p>

```

应该：

```html

<h1>标题</h1>

```

虽然使用p标签，也可以通过CSS去定义它的外观和标题相同，但p标签本身的并不是表示标题，而是表示文本段落


### 12.模块化

每个模块必须有一个模块名；

每个模块的基本组成部分应该一致；

模块的子节点类名需带上模块名（防止模块间嵌套时产生不必要的覆盖）；

孙辈节点无需再带模块名。

代码如：

```html
<section class="m-detail">
　　<header class="m-detail-hd">
　　　　<h1 class="title">模块标题</h1>
　　</header>
　　<div class="m-detail-bd">
　　　　<p class="info">一些实际内容</p>
　　</div>
　　<footer class="m-detail-ft">
　　　　<a href="#" class="more">更多</a>
　　</footer>
</section>
```
其中 .m-detail-hd, .m-detail-bd, .m-detail-ft 为可选，视具体模块情况决定是否需要抽象为这种 头，中，尾 的结构