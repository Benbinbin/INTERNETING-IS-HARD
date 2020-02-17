# 第四章：CSS

教材：[hello, css](https://internetingishard.com/html-and-css/hello-css/)

---

这一章主要介绍层叠样式表 Cascading Style Sheets，CSS 是用于决定网页设计样式的另一种不同的语言。

与决定网页内容的 HMTL 文件不同，CSS 文件是用于决定网页的设计样式，如字体大小、元素边距、颜色等，通过 CSS 样式表可以创建一个完全私人定制的个性化网页。

这一章介绍 CSS 基本语法和实例，并了解其与 HTML 之间的交互。同样地，CSS 文件（样式表）进行合理的组织十分重要。

## 配置

按照教材创建 `hello-css.html` 和 `dummy.html` 文档，并编写 HTML 模板代码。

文档 `hello-css.html`

```html
<!DOCTYPE html>
<html lang='en'>
  <head>
    <meta charset='UTF-8'/>
    <title>Hello, CSS</title>
  </head>
  <body>
    <h1>Hello, CSS</h1>

    <p>CSS lets us style HTML elements. There’s also
       <a href='dummy.html'>another page</a> associated with this example.</p>

    <h2>List Styles</h2>

    <p>You can style unordered lists with the following bullets:</p>

    <ul>
      <li>disc</li>
      <li>circle</li>
      <li>square</li>
    </ul>

    <p>And you can number ordered lists with the following:</p>

    <ol>
      <li>decimal</li>
      <li>lower-roman</li>
      <li>upper-roman</li>
      <li>lower-alpha</li>
      <li>upper-alpha</li>
      <li>(and many more!)</li>
    </ol>
  </body>
</html>
```

文档 `dummy.html`

```html
<!DOCTYPE html>
<html lang='en'>
  <head>
    <meta charset='UTF-8'/>
    <title>Dummy</title>
  </head>
  <body>
    <h1>Dummy</h1>

    <p>This is a dummy page that helps us demonstrate reusable CSS
       stylesheets. <a href='hello-css.html'>Go back</a>.</p>

    <p>Want to try crossing out an <a href='nowhere.html'>obsolete link</a>? This
       is your chance!</p>
  </body>
</html>
```



## CSS 样式表

CSS 样式表以文本的形式保存在后缀为 `.css` 文档中。

CSS 设置网页元素样式的基本单位是规则集。每一个规则集都以选择器 `selector` 开始，之后就是以化括号 `{}` 包括的声明块，在声明块中设置样式；样式的设置是 属性 `property` 在冒号 `:` 左侧，相应的属性值 `value` 在右侧。

* `selector` 选择器：指定需要添加样式的 HTML 元素
* `property` 属性：需要设置的样式
* `value` 值：样式值

![css-rule-terminology](images/css-rule-terminology.png)

**创建 `styles.css` 文档并输入以下代码**

```css
body {
    color: #FF0000;
}
```

属性 `color` 是 CSS 规范定义的内置属性，设置被选择的 HTML 元素（及其子元素）的文本颜色，颜色的属性值可以接收一个表示颜色代码的十六位数值，如 `#FF0000` 表示亮红。

CSS 属性类似于 HTML 属性，也是通过键值对 key-value pairs 设置，但 CSS 属性是设定外观样式信息，而 HTML 元素属性是设定底层的语义信息。



## 链接一个 CSS 样式表

当在浏览器中渲染 `hello-css.html` 文档时，在 CSS 样式表中设置的样式并未实现。因为还没有将样式表与 HTML 文件链接起来。

HTML 元素 `<link/>` 用于链接网页外部的 CSS 样式表，以将预设的样式应用于当前的网页。

**更新 `hello-css.html` 文档中 `<head>` 元素内的代码：**

```html
<head>
    <meta charset='UTF-8'/>
    <title>Hello, CSS</title>
    <link rel='stylesheet' href='styles.css'/>    
</head>
```

HTML 元素 `<link/>` 与元素 `<a>` 类似，但该元素是在 `<head>` 元素内，即将当前文档外部定义的元数据 metadata （样式设置数据）链接到当前页面中。该元素是一个空元素，因此没有结束标签。

元素 `<link/>` 的属性 `ref` 设置链接的外部资源与当前文档的关系，常见的属性值是 `stylesheet`，其他更多的选项可以参考[此处](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Link_types)。属性 `href` 就是设置链接资源所在的路径，可以使用绝对链接、相对链接或根目录相对链接。

网页通过 HTML 将多种资源链接在一起，如 CSS、图像和 JavaScript 脚本等，因此 HTML 文档是网页的核心。



## CSS 注释

HTML 注释语法是 `<!-- comments -->`，而 CSS 注释语法是 `/* commnets */`，即浏览器加载 CSS 时会忽略在 `/*` 与 `*/` 符号之间的内容。

**更新 `styles.css` 文档中的代码：**

```css
body {
    color: #414141;    /* Dark gray */
}
```



## 设置多个属性

可以在 CSS 一个规则集的声明块中设置多个属性，每一个属性设置占一行，属性之间以分号 `;` 区隔。

**更新 `styles.css` 文档中的代码：**

```css
body {
    color: #414141;    /* Dark gray */
    background-color: #EEEEEE;    /* Light gray */
}
```

CSS 属性 `background-color` 也是与颜色样式相关的属性，但它是设置元素背景颜色。

:warning: 注意设置的每个属性最后添加分号 `;`



## 选择不同元素

使用不同的选择器可以分别对不同的元素设置不同样式。

**更新 `styles.css` 文档中的代码：**

```css
body {
    color: #414141;    /* Dark gray */
    background-color: #EEEEEE;    /* Light gray */
}

h1 {
    font-size: 36px;
}

h2 {
    font-size: 28px;
}
```



## 衡量单位

许多 CSS 属性在设置属性值时需要提供衡量单位。在网页开发中（不同的元素和应用场景中）会遇到多种[不同衡量单位](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length)，常见的两种是 `px` 和 `em`

* `px` 像素

  > 绝对长度单位，与显示设备相关。
  >
  > 对于屏幕显示，通常是一个设备像素（点）的显示。
  >
  > 对于打印机和高分辨率的屏幕，一个CSS像素意味着多个设备像素。
  >
  > 参考：[<length> - CSS（层叠样式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length)

* `em` 字体相对长度单位（发音类似字母 `m`）

  `em` 是一个相对单位，基于父元素的字体长度值。在 HTML 嵌套树形结构中，相对性使该单位在元素字体长度时十分有用，可以基于基础字体大小设置标题或着重内容字体的相对大小；当改变基础字体大小（绝对单位）后，`em` 单位可以让页面相关元素字体大小按比例同步缩放。。

  **更新 `styles.css` 文档中的代码：**

  ```css
  body {
      color: #414141;    /* Dark gray */
      background-color: #EEEEEE; /* Light gray */
      font-size: 18px;
  }
  
  h1 {
      font-size: 2em;
  }
  
  h2 {
      font-size: 1.6em;
  }
  ```

  示例中设置基本字体大小（文档 `<body>` 元素的文本字体长度）为 `18px`，再基于该字体长度（绝对单位），通过相对单位设置 元素 `<h1>` 和 `<h2>` 字体大小，分别是 2 倍和 1.6 倍。

  

## 选择多个元素

可以同时选择多个元素，以逗号 `,` 分隔，设置统一的样式。

**在 `styles.css` 文档中添加代码，以统一设置所有标题的字体样式：**

```css
h1, h2, h3, h4, h5, h6 {
    font-family: "Helvetica", "Arial", sans-serif;
}
```

同时选择多个元素，再统一设置样式可以避免代码冗余，且便于后期的修改和维护。

### 不同字体

`font-family` 是另一个 CSS 内置属性，用于为选择的元素内的文本定义字体。

由于用户的操作系统内建字体可能并不支持 CSS 所设定的字体，因此该属性一般设置多个属性值，以备用。

示例中设置了三种字体 `Helvetica`、`Arial` 和 `sans-serif`，当用户系统无法加载 `Helvetica` 字体时，浏览器就会加载 `Arial` 字体，如果该字体依然无法加载，就会选择各主流系统所通用的字体 `sans-serif`。

如今前端开发可以使用网络字体，避免了各系统对于字体的限制，更详细的讲解查看 [第十四章：字体](../C14_WEB_TYPOGRAPHY/C14_WEB_TYPOGRAPHY.md)。



## 列表样式

CSS 属性 `list-style-type` 设置列表项目符号图标，选择的 HTML 元素是无序列表 `<ul>` 或 `<ol>`，而样式渲染对应的是每一个列表项的元素 `<li>` 前的图标。

属性 `list-style-type` 可设置的属性值有多种，如 `circle` 空心圆形、`lower-roman` 小写罗马数字等，还可以[自定义（链接外部图像）列表项样式](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-image)。

**在 `styles.css` 文档中添加代码：**

```css
ul {
    list-style-type: circle;
}

ol {
    list-style-type: lower-roman;
}
```

当使用无序列表元素 `<ul>` 用作菜单导航栏时，属性值一般设置为 `none` ，使列表项的样式更像按钮。更详细的讲解可查看 [第九章：高级定位](../C09_ADVANCED_POSITIONING/C09_ADVANCED_POSITIONING.md)。

![list-items-for-menus](images/list-items-for-menus.png)



列表作为菜单栏是一个极好的分隔展示内容的实践，通过富含语义的 HTML 元素创建内容可以让搜索引擎推断出其结构，通过 CSS 设置内容样式可以以精美的样式向用户展示。



## 复用样式表

只需在 HTML 文档中添加 `<link/>` 元素，并设置属性 `href` 指向样式表，即可在多个 HTML 文档中复用 CSS 样式表。

**在 `dummy.html` 文档中添加代码：**

```html
<link ref='stylesheet' href='styles.css'/>
```

在 `dummy.html` 文档中也可以加载 `styles.css` 文档中预设的样式了。

在多个 HTML 文档中链接复用同一个样式表，可以更方便地对多个文件的样式进行设置或更改，且可以让整个网站设计语言相统一。

链接样式表推荐使用 根目录相对链接，避免子目录中的 HTML 文档指向 CSS 样式表时使用 `..` 句法而令开发者感到迷惑。



## 更多的文字样式

文字有多种样式可在 CSS 中进行设置。

### 下划线

CSS 属性 `text-decoration` 设置选择元素内的文字的装饰性样式，如下划线、删除线等。

* `line-through` 该属性值为选择的文本添加删除线。

  :warning: 但是删除的文本应该赋予语义，即在 HTML 中使用元素 [`<ins>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ins) 或 [`<del>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/del) 对插入或删除内容进行标记，而不应该通过单纯修改样式来实现。

* `none` 该属性值移除选择文本默认的下划线，如链接文本的下划线。

**在 `styles.css` 文档中添加代码：**

```css
a {
    text-decoration: none;
}
```

### 文本对齐

CSS 属性 `text-align` 设置选择元素内的文本在 HTML 元素中的对齐方式。

该属性有多种可设置的属性值：

* `left` 居左对齐
* `right` 居右对齐
* `center` 居中对齐
* `justify` 两端对齐

**在 `styles.css` 文档中添加代码：**

```css
p {
    text-align: left;
}
```

由于 HTML 元素 `<p>` 是文档流型（flow content）元素，每个元素默认占据整一行，因此其中文字的对齐样式看上去是相对于整个页面的，实际上配置的样式是针对 HTML 元素的，在 [第五章：盒子模型](../C05_CSS_BOX_MODEL/C05_CSS_BOX_MODEL.md) 具体讲解 block 元素和 CSS 盒子模型。

### 字重和样式

CSS 属性 `font-weight` 设置选择元素内的文本字体粗细，而属性 `font-style` 设置文本斜体等样式。

**更新 `styles.css` 文档中的代码：**

```css
h1, h2, h3, h4, h5, h6 {
    font-family: "helvetica", "Arial", sans-serif;
    font-weight: normal;    /* Add this */
}
```

示例设置 CSS 属性 `font-weight` 为 `normal`，即将标题字重设置而非默认的粗体。

但并不建议通过 CSS 修改文本默认的字重和斜体样式，由于这些样式可能有具体的语义。但是如果需要制作私人定制的网页，则字重和字体样式是十分重要的议题，具体在 [第十四章：字体](../C14_WEB_TYPOGRAPHY/C14_WEB_TYPOGRAPHY.md) 讲解。



## 层叠

除了网页外部 `.css` 样式表文件可以设置 CSS 样式以外，还有其他方式设置样式代码。

层叠样式表 Cascading Style Sheets 其中「层叠」是指当网页的样式设置有多个来源时，多个规则是依次向下层叠，文档下面（新设置）的属性规则会覆盖上面相同的属性规则。CSS 层叠优先结构如下（越往下所设置的样式优先级别越高，即会***覆盖***其上设置的相同属性）：

* 浏览器的默认样式表
* 用户定义的样式表
* 网页外部样式表（开发者制作的样式表，推荐使用）
* 网页内部的样式表（开发者制作的样式表）
* 内联样式（即在 HTML 元素中设置的 CSS 样式，开发者可以制作，但不推荐使用）

![css-cascade](images/css-cascade.png)

### 网页内部样式

HTML 元素 `<style>` 用于添加网页内部 CSS 样式。这一类的样式是当前网页所特有的，不可复用。

元素 `<style>` 有设置网页外观的 metadata 元数据，因此一般在元素 `<head>` 内添加。

**在 `dummy.html` 文档元素 `<head>` 内添加代码：**

```html
<head>
    <meta charset='UTF-8'/>
    <title>Dummy</title>
    <link rel='stylesheet' href='styles.css'/>
    <style>
        body {
            color: #0000FF;    /* Blue */
        }
    </style>
</head>
```

添加样式将元素 `<body>` 内所有文本颜色设置为蓝色，新增的样式设置只作用于当前网页 `dummy.html`，并覆盖了上方 `<link>` 链接的外部 `styles.css` 样式表中设置的样式。

HTML 元素 `<style>` 内 CSS 语法与外部 `styles.css` 样式表语法相同，因此在外部样式表的设置可以在内部元素 `<style>` 中设置。但由于内嵌在 HTML 文件中，因此与外部样式表相比，内部样式的更改和后续维护都不方便。

当需要设置单页面专属的样式时可以在相应的 HTML 文件中的 `<head>` 元素内设置；当多个页面都有相同的 CSS 规则就应该将冗余的设置提取汇总到一个 `.css` 文件中，进行统一设置方便维护。

### 内联样式

可以在元素内部进行 CSS 样式设定。

**更新 `dummy.html` 文档代码：**

```html
<p>Want to try crossing out an <a href='nowhere.html'
    style='color: #990000; text-decoration: line-through;'>obsolete link</a>?
    This is your chance!
</p>
```

示例在元素 `<a>` 内设置内联样式，将链接文字设置为红色，并添加了删除线以提示用户链接无效。

内联样式在 HTML 元素的属性 `style` 中设置，属性值需要在引号（单引号或双引号）中，CSS 样式的属性和属性值以冒号 `:` 分隔，而多个 CSS 属性以分号 `;` 分隔。

由于是内联样式是元素属性，因此设置的样式需要压缩到一行中。

由于内联样式优先级最高，且嵌入到单个 HTML 页面的单个元素中，对于后续的样式修改十分不方便，应该尽可能避免使用；若需要针对特定单个 HTML 元素进行样式设置，可以使用 CSS 类选择器，更详细讲解在 [第六章：CSS 选择器](../C06_CSS_SELECTORS/C06_CSS_SELECTORS.md)。

### 多个样式表

可以将网页不同部的样式设置 CSS 规则集分散到不同外部样式表，再在 HTML 文档中添加多个链接 `<link/>` 将不同的样式表都应用于同一个页面，从而实现不同网页的类似界面部分设计语言统一。

:warning: 元素 `<link/>` 的添加顺序很重要，后添加的样式表会覆盖其上的样式表中设置的相同属性。一般先添加链接到设置全局样式的 CSS 文件，如 `styles.css`；再添加链接到设置特定部分样式的 CSS 文件，如 `product.css` 或 `blog.css`。

通过添加链接多个样式表，可对网页进行更详细的样式设置，避免使用网页内部样式或内蓝样式。



## 总结

前端工程师使用 CSS 将网页原型实现，更多 CSS 属性原理和设置方法可以参考 [MDN 的 CSS 参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)。

这一章介绍了 CSS 语法，并且讲解了如何将不同 CSS 规则（样式表）应用到 HTML 文档中，这对响应式设计至关重要，如使用移动设备、平板设备和台式电脑等不同设备访问网页时，网页加载的样式表也不一样。