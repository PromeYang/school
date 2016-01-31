# PART-2.1
## 第二课 head标签内部的标签用法以及响应式的实现方式

2016-01-30 15:26:37

head标签内部的标签用法

### `<base>`

`<base>` 标签为页面上的所有链接规定默认地址或默认目标。

通常情况下，浏览器会从当前文档的 URL 中提取相应的元素来填写相对 URL 中的空白。

使用 `<base>` 标签可以改变这一点。浏览器随后将不再使用当前文档的 URL，而使用指定的基本 URL 来解析所有的相对 URL。这其中包括 `<a>`、`<img>`、`<link>`、`<form>` 标签中的 URL。将影响所有使用相对路径的场景。

```
<base target="_blank"> -- 设置之后所有 <a> 标签都会应用 target="_blank" 属性
<base href="http://www.promeyang.com/"> -- 设置之后所有相对路径都是相对设定的参照地址 http://www.promeyang.com/
如:<img src="a.png" /> -- 访问的是 http://www.promeyang.com/a.png
```

### `<meta>`
`<meta>` 标签可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。

* 在 HTML 中，`<meta>` 标签没有结束标签。在 XHTML 中，`<meta>` 标签必须被正确地关闭。

* `<meta>` 标签永远位于 head 元素内部。元数据总是以名称/值的形式被成对传递的。

#### SEO优化

* 页面关键词，每个网页应具有描述该网页内容的一组唯一的关键字。标记内容太短，则搜索引擎可能不会认为这些内容相关。另外标记不应超过 874 个字符。

```
<meta name="keywords" content="your tags" />
```

* 页面描述，每个网页都应有一个不超过 150 个字符且能准确反映网页内容的描述标签。

```
<meta name="description" content="150 words" />
```

* 搜索引擎索引方式，robotterms是一组使用逗号(,)分割的值，通常有如下几种取值：none，noindex，nofollow，all，index和follow。确保正确使用nofollow和noindex属性值。

```
<meta name="robots" content="index,follow" />
<!--
    all：文件将被检索，且页面上的链接可以被查询；
    none：文件将不被检索，且页面上的链接不可以被查询；
    index：文件将被检索；
    follow：页面上的链接可以被查询；
    noindex：文件将不被检索；
    nofollow：页面上的链接不可以被查询。
 -->
```

* 页面重定向和刷新：content内的数字代表时间（秒），既多少时间后刷新。如果加url,则会重定向到指定网页（搜索引擎能够自动检测，也很容易被引擎视作误导而受到惩罚）。

```
<meta http-equiv="refresh" content="0;url=" />
```

* 其他用法

```
<meta name="author" content="author name" /> <!-- 定义网页作者 -->
<meta name="google" content="index,follow" />
<meta name="googlebot" content="index,follow" />
<meta name="verify" content="index,follow" />
```

### 关于响应式

小草的理解是, 响应式是为了让更多不同尺寸的设备, 尽可能友好的呈现页面布局, 从而解决终端兼容的一种思路。

#### 主流的响应式思路有这三种

* 宽度适应 -- jQuery Mobile

* 等比适应 -- 设置viewport实现 , 采用rem单位实现

* 断点适应 -- Bootstrap

#### 宽度适应

所谓的宽度适应就是指元素的高度固定, 元素的宽度是相对父元素按`百分比`适应。最经典的案例就是 `jQuery Mobile`。

```
/* 设置父元素是宽度100%适应的 */
.ui-parent{
	width: 100%;
}
/* 设置子元素是相对父元素宽度80%适应度 */
.ui-child{
	width: 80%
	height: 44px;
	margin: 0 auto;
}
/* 这样就实现了一个随着设备的宽度变化而变化的简单宽度适应布局 */
```

#### 等比适应

顾名思义, 就是元素按照设计稿等比例适应设备的屏幕大小。

比较成熟的实现方式有两种, 一种是`设置viewport`, 另一种是`采用rem单位`。

**rem方案的开发流程**

1. 首先,我们会拿到一份设计稿 , 假设 设计稿是以750宽度来设计的

2. 我们开发的时候就以这份为底版,先开发一个750的版本, 我在css样式文件中设置 html的font-size为100px

3. 通过js根据不同的屏幕来调整根字体大小

```js
<script>
(function(doc, win) {
    var docEl = doc.documentElement,
        resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
        recalc = function() {
            var clientWidth = docEl.clientWidth;
            if (!clientWidth) return;
            docEl.style.fontSize = 100 * (clientWidth / 750) + 'px';
        };

    // Abort if browser does not support addEventListener
    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
</script>
```

*tips:上面的代码就是根据屏幕设置不同的根字体大小, 其中`100`对应着`根font-size`, `750`对应着设计稿的宽度*

```
/* 一个简单的rem案例 */
html,
body {
    font-size: 100px;
    line-height: 1;
    overflow: hidden;
}
.ui-arrow{
    display: block;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0.2rem;
    margin: auto;
    width: 0.88rem;
    height: 0.56rem;
    z-index: 999;
    animation: start 1.5s infinite ease-in-out;
    &>img{
        width: 0.88rem;
        height: 0.56rem;
    }
}
```

## 下一节课预览

* 设置viewport实现等比适应, 断点适应的实现方式


