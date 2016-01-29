# PART-1
## 第一课页面基本结构、文档声明、编码声明
2016-01-29 14:09:18
页面基本结构、文档声明、编码声明

### 页面基本结构
1.文档声明
2.html标签
2-1.head标签
2-2.body标签

示例:

```
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="utf-8">
<title>网页标题-www.divcss5.com</title>
</head>
<body>
    网页正文内容
</body>
</html>
```

#### 关于<文档声明>

* <!DOCTYPE> 声明必须是 HTML 文档的第一行，位于 <html> 标签之前。用于帮助浏览器正确地显示网页.声明HTML 是用什么版本编写的.

* <!DOCTYPE> 声明不是 HTML 标签；它是指示 web 浏览器关于页面使用哪个 HTML 版本进行编写的指令。

* 在 HTML 4.01 中，<!DOCTYPE> 声明引用 DTD，因为 HTML 4.01 基于 SGML。DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容。

* HTML5 不基于 SGML，所以不需要引用 DTD。

#### 常用的 DOCTYPE 声明

* HTML 5

```
<!DOCTYPE html>
```

* HTML 4.01 Strict
该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

* HTML 4.01 Transitional

该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
```

* HTML 4.01 Frameset

该 DTD 等同于 HTML 4.01 Transitional，但允许框架集内容。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN"
"http://www.w3.org/TR/html4/frameset.dtd">
```

* XHTML 1.0 Strict

该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
```

* XHTML 1.0 Transitional

该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "
http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

* XHTML 1.0 Frameset

该 DTD 等同于 XHTML 1.0 Transitional，但允许框架集内容。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
```

* XHTML 1.1

该 DTD 等同于 XHTML 1.0 Strict，但允许添加模型（例如提供对东亚语系的 ruby 支持）。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```

**注:忽略声明将导致怪异模式(quirks mode)。**

#### 关于`<html>`标签

* html标签告知浏览器其自身是一个 HTML 文档。其余所有标签都是在其内部声明, 标签必须闭合, 其子元素只有head标签和body标签两个.

* xmlns 属性在 XHTML 中是必需的，但在 HTML 中不是。不过，即使 XHTML 文档中的 <html> 没有使用此属性，W3C 的验证器也不会报错。这是因为 "xmlns=http://www.w3.org/1999/xhtml" 是一个固定值，即使您没有包含它，此值也会被添加到 `<html>` 标签中。

* xmlns 属性可以在文档中定义一个或多个可供选择的命名空间。该属性可以放置在文档内任何元素的开始标签中。该属性的值类似于 URL，它定义了一个命名空间，浏览器会将此命名空间用于该属性所在元素内的所有内容。

* manifest是HTML5 中的新属性。定义一个 URL，在这个 URL 上描述了文档的缓存信息。

#### 关于`<head>`标签

* `<head>` 标签用于定义文档的头部，它是所有头部元素的容器。<head> 中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等等。
 
* 下面这些标签可用在 head 部分：`<base>`, `<link>`, `<meta>`, `<script>`, `<style>`, 以及 `<title>`。

* `<meta>`标签是值得去深究的一个标签,下节课再讲.

#### 关于`<body>`标签

* `<body>` 标签是主体内容部分,对应着document.body.

```
最优的实践是:
在<html lang="en”>中应用语言属性
在<meta charset="UTF-8”>中规定编码
在<head>完成样式的引用,以及最高优先级的脚本引用
在<body>的底部完成所有脚本的引用,虽然有些demo中的脚本写在body外面,但是那并不是规范的做法.
```

## 下一节课预览

* meta, base , css语法、style属性、link和style标签、id属性、基本样式、Border 、Background、 Font、盒模型、文本设置...

