## 样式顺序规范

1.建议相关的属性说明放在一组，提高代码的可读性。

2.布局方式、位置，相关属性（position、left、right、top、bottom、z-index）

3.盒模型，相关属性包括（display、float、width、height、margin、padding、border、border-radius）

4.文本排版，相关属性包括（font、color、background、line-height、text-align）

5.视觉外观，相关属性包括：(color, background, list-style, transform, animation)

由于定位可以从正常的文档流中移除元素，并且还能覆盖盒模型相关的样式，因此排在首位。而盒模型决定了组件的尺寸和位置，所以排第二位。文本和视觉外观对元素影响较小，所以放在第三，第四位；示例代码如下

```css
.box {
  position: absolute;
  top: 0;
  left: 20%;
  z-index: 99;
  width: 100px;
  height: 100px;
  font-size: 20px;
  color:red;
  background-color: aqua;
}
```

## 使用CSS缩写属性

对于 background、font、padding、margin 这些简写形式的属性声明，可以缩写的尽量缩写，这样既精简代码又提高用户的阅读体验

```css
.box {
  width: 100px;
  height: 100px;
  margin: 0 10px 20px 30px;
  font: italic bold 12px/30px arial,sans-serif;
}
```

## 小数点和单位

值在 -1 和 1 之间时去掉小数点前的“0”，如果属性值为数字0，不加任何单位；

```css
.box {
  width: 100px;
  height: 100px;
  margin: 0 10px 20px 0;
  opacity: .5;
}
```

## 颜色值十六进制表示法

6 个字符的十六进制表示法，并始终使用小写的十六进制数字；16进制表示法与rgb表示法混用的情况，优先使用16进制表示法

```css
.box {
  color: #cccccc;
  background-color: #efefef;
}
```

## 引号

属性选择器或属性值用双引号 "" 括起来，而 URI 值 url() 不要使用任何引号

```css
.box {
  font-family: "open sans", arial, sans-serif;
  background-image: url(http://taobao.com/);
}
```

## 内容缩进

为了反映层级关系和提高可读性，块级内容都应缩进，建议缩进使用两个空格；

```css
.box {
  line-height: 1.5;
}
```
## 空格

在每个声明块选择器与左花括号前添加一个空格；

声明块的右花括号应当单独成行；

每条声明语句的 : 后应该插入一个空格，前面无空格

```css
.box {
  float: right;
  width: 100px;
  color: #333;
  background-color: #f5f5f5;
  text-align: center;
}
```

## 媒体查询

将媒体查询放在尽可能相关规则的附近。如果分开了，可能会被遗忘。

媒体查询针对每一个种屏幕（大、中、小）的分别单独组织为一个文件

```css
.element {}
.element-avatar {}
.element-selected {}

@media (min-width: 480px) {
    .element {}
    .element-avatar {}
    .element-selected {}
}
```

## 注释

在适当的位置给予代码正确的注释，让他人跟容易理解。好的代码注释传达上下文和目标。不要简单地重申组件或者 class 名称。

```css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
}
```
如果是对整个文件做注释，最好放在文本头部，简要描述一下文中元信息以及作用

```css
/**
 * 这里描述元信息
 */
html, body {
  height:100%;
}
```