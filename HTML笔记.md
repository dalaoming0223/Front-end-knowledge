 

# [HTML 基本认知](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=html-基本认知)

## [1、常见 5 大浏览器](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_1、常见-5-大浏览器)

- IE
- 火狐 FireFox
- 谷歌 Chrome
- Safari
- 欧朋 Opera

## [2、渲染引擎](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_2、渲染引擎)

| 浏览器       | 内核    |
| ------------ | ------- |
| IE           | Trident |
| FireFox      | Gecko   |
| Safari       | Webkit  |
| Chrome/Opera | Blink   |

## [3、Web 标准](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_3、web-标准)

保证不同浏览器打开页面显示效果一样

| 构成 | 语言       | 说明     |
| ---- | ---------- | -------- |
| 结构 | HTML       | 页面元素 |
| 表现 | CSS        | 页面样式 |
| 行为 | JavaScript | 页面交互 |

## [4、HTML](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_4、html)

Hyper Text Markup Language 超文本标记语言

## [ 5、hello world](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_5、hello-world)

需要设置显示`文件扩展名`

文件扩展名：`.html`

index.html

```html
<strong>hello world</strong>Copy to clipboardErrorCopied
```

**hello world**

## [6、HTML 骨架](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_6、html-骨架)

```html
<html>
  <head>
    <title></title>
  </head>

  <body></body>
</html>Copy to clipboardErrorCopied
```

- html 最外层标签

  用来定义当前网页显示的主语言，书写在 `` 标签内。

  - `en` 定义语言为英语
  - `zh` 定义语言为中文

  简单来说：定义为 `en` 就是面向英文用户的网页，定义为 `zh` 就是面向中国大陆用户的网页。

  > `en-GB` 英文（英国）
  >
  > `en-US` 英文（美国）
  >
  > `zh-CN` 中文（简体，中国大陆）
  >
  > `zh-SG` 中文（简体，新加坡）
  >
  > `zh-HK` 中文（繁体，香港）
  >
  > `zh-MO` 中文（繁体，澳门）
  >
  > `zh-TW` 中文（繁体，台湾）

  ```
  <html lang="zh-CN"> 
  </html>
  ```

  > 语言的设置是为了方便 `浏览器搜索推荐` 以及触发 `浏览器翻译功能`，并不是说设置了某类主语言后网页中就不能存在其他类型的语言了。

- head 头部

- title 标题

- body 主体

## [7、开发工具](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_7、开发工具)

- Visual Studio Code （首选）
- WebStorm
- Sublime Text
- DreamWeaver
- HBuilder

## [8、VS Code 使用](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_8、vs-code-使用)

快速生成 html 网页结构：

- `! + Tab` 
- `doc + Tab`

快捷键

- 浏览器打开：`Alt + B` / `option⌥ + B`
- ÏLive Server 打开：`[command⌘ + L, command⌘ + O]`

## [9、注释](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_9、注释)

```html
<!-- 注释内容 -->Copy to clipboardErrorCopied
```

- 浏览器中不显示注释内容
- 添加和取消注释快捷键：`command + /`

## [10、标签结构](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_10、标签结构)

- 双标签 `<开始标签>内容`, 例如：`内容`
- 单标签 `<标签 />`, 例如：` `

## [11、标签关系](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-basic?id=_11、标签关系)

- 父子关系（嵌套关系）

```html
<html>
  <head></head>
</html>Copy to clipboardErrorCopied
```

- 兄弟关系（并列关系）

```html
<head></head>
<body></body>
```

# [HTML 标签元素](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=html-标签元素)

## [1、标题标签 Heading](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_1、标题标签-heading)

```
h1~h6
<h1>一级标题</h1>
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>Copy to clipboardErrorCopied
```

一级标题二级标题三级标题四级标题五级标题六级标题

同时选中下一个相同字符：`command + D`

特点：

- 独占一行
- 文字加粗
- 文字变大，h1->h6 文字逐渐变小

## [2、段落标签 Paragraph](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_2、段落标签-paragraph)

```html
<p>内容</p>Copy to clipboardErrorCopied
```

内容

特点：

- 段落之间存在间隙
- 独占一行

## [3、排版标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_3、排版标签)

（1）换行符 Line Break

```html
第一行文本<br />第二行文本Copy to clipboardErrorCopied
```

第一行文本
第二行文本

特点

- 单标签
- 让文字强制换行

（2）水平分割线 Horizontal Rule

```html
<hr />
```

![image-20221228230628900](../../AppData/Roaming/Typora/typora-user-images/image-20221228230628900.png)

## [4、文本格式化标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_4、文本格式化标签)

| 语义   | 标签          | 说明                                                 |
| ------ | ------------- | ---------------------------------------------------- |
| 加粗   | b/strong 加粗 | 介于可读性、搜索引擎优化及屏幕阅读器适配推荐使用前者 |
| 倾斜   | i/em 倾斜     | 介于可读性、搜索引擎优化及屏幕阅读器适配推荐使用前者 |
| 删除线 | s/del 删除线  | 介于可读性、搜索引擎优化及屏幕阅读器适配推荐使用前者 |
| 下划线 | u/ins 下划线  | 介于可读性、搜索引擎优化及屏幕阅读器适配推荐使用前者 |

注意：`` 标签不只是单纯的用于倾斜文本，其核心的意义在于对元素进行**强调！\**所以在后期的开发中可以把一些\**特殊性、强调性**的元素放在 em 标签中，然后再对 em 这个盒子进行样式设置，这比把其放入其他盒子（如：span）中要更合理，同理 `` 标签页适合放一些**重点强调**的元素。

推荐使用后者

- b/strong 加粗
- u/ins 下划线
- i/em 倾斜
- s/del 删除线

```html
<b>加粗</b>
<strong>加粗</strong>

<u>下划线</u>
<ins>下划线</ins>

<i>倾斜</i>
<em>倾斜</em>

<s>删除线</s>
<del>删除线</del>Copy to clipboardErrorCopied
```

**加粗** **加粗**

下划线 下划线

*倾斜* *倾斜*

删除线 ~~删除线~~

## [5、媒体标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_5、媒体标签)

（1）图片标签 Image

```html
<img
  src="图片地址"
  alt="替换文本"
  title="提示文本"
  width="宽度"
  height="高度"
/>Copy to clipboardErrorCopied
```

标签属性：属性名=属性值

## [6、资源路径](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_6、资源路径)

（1）当前路径

```html
<img src="image.png" />

<!-- 推荐使用./ -->
<img src="./image.png" />Copy to clipboardErrorCopied
```

（2）下级路径

```html
<img src="./img/image.png" />Copy to clipboardErrorCopied
```

（3）上级路径

```html
<img src="../image.png" />Copy to clipboardErrorCopied
```

## [7、音频标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_7、音频标签)

```html
<audio
  src="音频地址"
  controls 显示播放控件
  autoplay 自动播放（部分浏览器不支持）
  loop 循环播放
</audio>Copy to clipboardErrorCopied
```

支持的格式 mp3 wav

## [8、视频标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_8、视频标签)

```html
<video src="视频地址"
  controls 显示播放控件
  autoplay 自动播放（谷歌浏览器需要配合muted静音播放）
  muted 静音播放
  loop 循环播放
</video>Copy to clipboardErrorCopied
```

支持的格式 mp4

## [9、链接标签 Anchor](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_9、链接标签-anchor)

```html
<a href="目标地址">文字内容</a>

<!-- eg: -->
<a href="https://www.baidu.com/">百度</a>Copy to clipboardErrorCopied
```

[百度](https://www.baidu.com/)

属性：

- ```
  target: _self 当前窗口打开（默认） / _blank 新窗口打开
  ```

网站的默认首页 index.html

### **9.1 链接分类**

- **外部链接：**例如：

  ```
  <a href="http://www.baidu.com">百度</a>
  ```

- **内部链接：**网站内部页面之间相互链接，直接链接内部页面名称即可，例如：

  ```
  <a href="index.html">首页</a>
  ```

- **空链接：**如果当时没有确定链接目标时， 

  ```
  <a href="javascript:void(0)">首页</a>"
  ```

  当用户点击链接时，void(0) 计算为 0，但 Javascript 上没有任何效果

- **下载链接：**如果 href 里面地址是一个文件或者压缩包（前提：路径包含文件类型后缀名，如：`.exe`、`.zip` 等），便会下载这个文件

- **网页元素链接：**在网页中的各种网页元素，如：文本、图像、表格、音频、视频等都可以添加超链接

- **锚点链接：**点击链接，可以快速定位到当前页面中的某个位置

  - 在链接文本的 href 属性中，设置属性值的 `#名字` 的形式，如：

    ```html
    <a href="#two">第2集</a>
    ```

  - 找到目标位置标签（此处以 h3 标签为例），里面添加一个 `id属性="刚才的名字"`，如：`第2集介绍`

    ```html
    <h3 id="two">第2集介绍</h3>
    ```

  - ```html
    <a href="#"></a> 
    ```

    默认定位到页面顶部

### **9.2 src 和 href 的区别**

一句话概括:**src 是引入资源的 href 是跳转url的**

1. src用于替换当前元素，href用于在当前文档和引用资源之间确立联系。
2. src是source的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求src资源时会将其指向的资源下载并应用到文档内，例如js脚本，img图片和frame等元素。当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部。
3. href是Hypertext Reference的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接。如果我们在文档中添加那么浏览器会识别该文档为css文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用link方式来加载css，而不是使用@import方式。

### **9.3 注意：**

1. 外部链接 需要添加 http:// www.baidu.com
2. 内部链接 直接链接内部页面名称即可 比如 < a href="index.html"> 首页
3. 如果当时没有确定链接目标时，通常将链接标签的href属性值定义为“#”(即href="#")，表示该链接暂时为一个空链接。
4. 不仅可以创建文本超链接，在网页中各种网页元素，如图像、表格、音频、视频等都可以添加超链接。

### **9.4 锚点定位：通过创建锚点链接，用户能够快速定位到目标内容。**

```
1. 使用相应的id名标注跳转目标的位置。 (找目标)
  <h3 id="two">第2集</h3> 

2. 使用<a href="#id名">链接文本</a>创建链接文本（被点击的） 
  <a href="#two">   
```

## [10、列表](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_10、列表)

- 无序列表
- 有序列表
- 自定义列表

（1）无序列表 Unordered List

列表项 List Item

```html
<ul>
  <li>苹果</li>
  <li>香蕉</li>
  <li>桃子</li>
</ul>Copy to clipboardErrorCopied
```

苹果香蕉桃子

（2）有序列表 Ordered List

```html
<ol>
  <li>苹果</li>
  <li>香蕉</li>
  <li>桃子</li>
</ol>Copy to clipboardErrorCopied
```

苹果香蕉桃子

（3）自定义列表 Description List

```html
<dl>
  <dt>水果</dt>
  <dd>苹果</dd>
  <dd>香蕉</dd>
  <dd>桃子</dd>
</dl>Copy to clipboardErrorCopied
```

水果苹果香蕉桃子

标签含义

- dt Description Term
- dd Description Details

| 标签名 | 定义       | 说明                                                       |
| ------ | ---------- | ---------------------------------------------------------- |
| ul     | 无序列表   | 里面只能包含li，没有顺序，使用较多。li里面可以包含任何标签 |
| ol     | 有序列表   | 里面只能包含li，有顺序，使用较少。li里面可以包含任何标签   |
| dl     | 自定义列表 | 里面只能包含dt和dd。dt和dd里面可以包含任何标签             |

ul 无序列表  附：去除 li 前符号的方法：`style="list-style: none;"`



## [11、表格](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_11、表格)

（1）基本元素

标签含义

- tr Table Row
- th Table Header
- td Table Data

table 属性：

- border 边框宽度
- width 表格宽度
- height 表格高度

```html
<table border="1">
    <caption>
        表格大标题
    </caption>
    
    <tr>
        <th>姓名</th>
        <th>年龄</th>
    </tr>
    <tr>
        <td>Tom</td>
        <td>23</td>
    </tr>
    <tr>
        <td>Jack</td>
        <td>24</td>
    </tr>
</table>Copy to clipboardErrorCopied
```

<iframe src="https://mouday.github.io/coding-tree/blog/front-end-learn/demo/table-1.html" height="150" style="-webkit-font-smoothing: antialiased; -webkit-tap-highlight-color: transparent; text-size-adjust: none; box-sizing: border-box; font-size: 16px; border: 1px solid rgb(238, 238, 238); width: 1px; min-width: 100%; margin: 1em 0px; color: rgb(52, 73, 94); font-family: &quot;Source Sans Pro&quot;, &quot;Helvetica Neue&quot;, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"></iframe>
（2）表格结构，可以省略

- thead 表格头部
- tbody 表格主体
- tfoot 表格底部

```html
<table border="1">
    <caption>
        表格大标题
    </caption>

    <thead>
        <tr>
            <th>姓名</th>
            <th>年龄</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>Tom</td>
            <td>23</td>
        </tr>
        <tr>
            <td>Jack</td>
            <td>24</td>
        </tr>
    </tbody>
    
    <tfoot>
        <tr>
            <td>求和</td>
            <td>57</td>
        </tr>
    </tfoot>
</table>Copy to clipboardErrorCopied
```

<iframe src="https://mouday.github.io/coding-tree/blog/front-end-learn/demo/table-2.html" height="170" style="-webkit-font-smoothing: antialiased; -webkit-tap-highlight-color: transparent; text-size-adjust: none; box-sizing: border-box; font-size: 16px; border: 1px solid rgb(238, 238, 238); width: 1px; min-width: 100%; margin: 1em 0px; color: rgb(52, 73, 94); font-family: &quot;Source Sans Pro&quot;, &quot;Helvetica Neue&quot;, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"></iframe>
（3）合并单元格

- 跨行合并（垂直）rowspan
- 跨列合并（水平）colspan

左上原则

- 上下合并，保留最上
- 左右合并，保留最左

> Tips: 不能跨结构合并

```html
<table border="1">
    <caption>
        表格大标题
    </caption>

    <thead>
        <tr>
            <th>姓名</th>
            <th>年龄</th>
        </tr>
    </thead>
    
    <tbody>
        <tr>
            <td>Tom</td>
            <td rowspan="2">23</td>
        </tr>
        <tr>
            <td>Jack</td>
        </tr>
    </tbody>

    <tfoot>
        <tr>
            <td colspan="2">求和: 57</td>
        </tr>
    </tfoot>
</table>Copy to clipboardErrorCopied
```

<iframe src="https://mouday.github.io/coding-tree/blog/front-end-learn/demo/table-3.html" height="170" style="-webkit-font-smoothing: antialiased; -webkit-tap-highlight-color: transparent; text-size-adjust: none; box-sizing: border-box; font-size: 16px; border: 1px solid rgb(238, 238, 238); width: 1px; min-width: 100%; margin: 1em 0px; color: rgb(52, 73, 94); font-family: &quot;Source Sans Pro&quot;, &quot;Helvetica Neue&quot;, Arial, sans-serif; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: rgb(255, 255, 255); text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"></iframe>
### 11.1 表格的主要作用

表格主要用于显示、展示数据。因为它可以让数据显示得非常的规整，可读性非常好。特别是后台展示数据的时候，能够熟练运用表格就显得很重要。一个清爽简约的表格能够把繁杂的数据表现得很有条理（合理的使用表格也能够有效提高 SEO）。

**注意：**表格不是用来布局页面的，而是用来展示数据的。**表格常用于表单数据的 “布局”**。

> 特别强调，表格是用于表单数据的 “布局”，而不是页面的布局！

### 11.2 表格的基本语法

```html
<table>
    <tr>
        <td>单元格</td>
        ...
    </tr>
    ...
</table>
```

- `` table`` 是用于定义表格的标签
- `<tr></tr>` 用于定义表格中的行，必须嵌套在 `<table></table>` 标签中
- `<td></td>` `` 用于定义表格中的单元格，必须嵌套在 `` 标签中
- 字母 td 指表格数据（table data），即：数据单元格的内容
- 单元格 td 里面可以放任何的元素

### 11.3 表头单元格标签

一般表头单元格位于表格的第一行或第一列，作用是：突出重要性，表头单元格里面的文本内容**默认加粗居中**显示。

`<th></th>` 标签表示 HTML 表格的表头部分（table head 的缩写）。

```html
<table>
    <tr>
    	<th>姓名</th>
        <th>性别</th>
        <th>年龄</th>
        ...
    </tr>
    ...
</table>
```

### 11.4 表格属性

**注意：**表格标签的属性在实际开发中并不常用，而是通过后面的 CSS 来设置，这里了解即可。

以下属性都写在 table 开始标签内，多个属性之间用空格隔开。

```html
<table align="center" border="1" cellpadding="0" cellspacing="0" width="500" height="240">
    ...
</table>
```

| 属性名        | 属性值                    | 描述                                                         |
| ------------- | ------------------------- | ------------------------------------------------------------ |
| `align`       | `left`、`center`、`right` | 规定表格相对周围元素的对齐方式（默认 left），注意指的是整个表格的对齐方式（表格是在父盒子中默认往左靠，还是居中或是往右靠），而不是指单元格内容的对齐方式（单元格内容对齐可以通过：`style="text-align: center;"` 设置）（了解） |
| `border`      | `1` 或 `""`               | 规定表格单元是否拥有边框，默认为 ""，表示没有边框（了解）    |
| `cellpadding` | 像素值                    | 规定单元边沿与其内容之间的空白，默认 1 像素（了解）          |
| `cellspacing` | 像素值                    | 规定单元格之间的空白，默认 2 像素（了解）                    |
| `width`       | 像素值 或 百分比          | 规定表格的宽度（了解）                                       |
| `height`      | 像素值 或 百分比          | 规定表格的高度（了解）                                       |

### 11.5 表格结构标签

**使用场景：**因为表格可能很长，为了更好的表示表格的语义，可以将表格分割成：`表格头部` 和 `表格主体` 两大部分。

在表格标签中，分别用： `<thead>`标签表示表格的头部区域， `<tbody>`标签表示表格的主体区域，这样可以更好的分清表格结构。

-  `<thead></thead>`：用于定义表格的头部， `<thead>`内部必须拥有 `<tr>` 标签，一般是位于第一行，且一般 `<tr>`标签中推荐放置 `<th>` 标签
-  `<tbody>`：用于定义表格的主体，主要用于放数据本体
- 以上标签都是放在 `` <table></table>`` 标签中

<table>
    <!-- 头部区域 -->
    <thead>
    	<tr>
    		<th>姓名</th>
            <th>性别</th>
            <th>年龄</th>
        	...
    	</tr>
    </thead>
    <!-- 主体区域 -->
    <tbody>
        <tr>
            <td>周吉瑞</td>
            <td>男</td>
            <td>18</td>
            ...
        </tr>
        ...
    </tbody>
</table>





## [12、表单](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=_12、表单)

### 12.1 为什么需要表单

使用表单的目的是收集用户信息。

在网页中，需要跟用户进行交互，收集用户资料，此时就需要表单。



### 12.2 表单的组成

在 HTML 中，一个完整的表单通常由 `表单域`、`表单控件`（也称为表单元素）和 `提示信息` 3 个部分构成。



### 12.3 表单域

**表单域是一个包含表单元素的区域。**

在 HTML 标签中，`<form>` 标签用于定义表单域，以实现用户信息的收集和传递。

``<form>` ` 会把它范围内的表单元素信息提交给服务器。

```html
<form action="url地址" method="提交方式" name="表单域名称">
    <!-- 各种表单元素控件 -->
</form>
```

**常用属性：**

| 属性名   | 属性值         | 作用                                               |
| -------- | -------------- | -------------------------------------------------- |
| `action` | `url` 地址     | 用于指定接收并处理表单数据的服务器程序的 url 地址  |
| `method` | `get` / `post` | 用于设置表单数据的提交方式，其取值为 get 或 post   |
| `name`   | 名称           | 用于指定表单的名称，以区分同一个页面中的多个表单域 |



 

【GET案例】

```html
<!doctype html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <form action="http://127.0.0.1:8080/" method="GET">
        姓名：<input type="text" name="name">
        <input type="submit">
    </form>
</body>

</html>
```



【POST案例】

```html
<!doctype html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <form action="http://127.0.0.1:8080/" method="POST">
        姓名：<input type="text" name="name">
        <input type="submit">
    </form>
</body>

</html>
```

### 12.1 input属性

输入框 input

| type 属性 | 输入框类型 |
| --------- | ---------- |
| text      | 文本框     |
| password  | 密码框     |
| radio     | 单选框     |
| checkbox  | 多选框     |
| file      | 文件选择   |
| submit    | 提交按钮   |
| reset     | 重置按钮   |
| button    | 普通按钮   |

**除 type 属性外，`input` 标签还有很多其他属性，其常用属性如下：**

| 属性名      | 属性值       | 描述                                        |
| ----------- | ------------ | ------------------------------------------- |
| `name`      | 由用户自定义 | 定义 input 元素的名称                       |
| `value`     | 由用户自定义 | 规定 input 元素的值，也就是提交到服务器的值 |
| `checked`   | checked      | 规定此 input 元素首次加载时应当被选中       |
| `maxlength` | 正整数       | 规定输入字段中的字符的最大长度              |

- `name` 和 `value` 是每个表单元素都有的属性值，主要给后台人员使用

- `name` 表单元素的名字，要求：单选按钮和复选框要有相同的 name 值

  ![image-20230106235012601](../../AppData/Roaming/Typora/typora-user-images/image-20230106235012601.png)

- `checked` 属性主要针对于单选按钮和复选框，主要作用：打开页面时默认选中某个表单元素

- `maxlength` 是用户可以在表单元素输入的最大字符数，一般很少使用

#### 12.1.1 text 文本框

placeholder 占位符

```html
<input type="text" placeholder="文本框占位符" />Copy to clipboardErrorCopied
```

#### 12.1.2 password 密码框

placeholder 占位符

```html
<input type="password" placeholder="密码框占位符" />Copy to clipboardErrorCopied
```

#### 12.1.3 radio 单选框

name 属性分组，一个分组只能有一个值被选中

checked 默认选中

```html
<input type="radio" name="sex" value="1" />男
<input type="radio" name="sex" value="2" checked />女Copy to clipboardErrorCopied
```

![image-20221230225638050](../../AppData/Roaming/Typora/typora-user-images/image-20221230225638050.png)

#### 12.1.4 checkbox 多选框

checked 默认选中

```html
<input type="checkbox" name="city" value="beijing" />北京
<input type="checkbox" name="city" value="shanghai" checked />上海Copy to clipboardErrorCopied
```

![image-20221230225701465](../../AppData/Roaming/Typora/typora-user-images/image-20221230225701465.png)

#### 12.1.5 file 文件选择

multiple 多选(按住 ctrl 多选)

```html
<input type="file" /> <input type="file" multiple />Copy to clipboardErrorCopied
```

 

#### 12.1.6 按钮

- submit 提交按钮
- reset 重置按钮
- button 普通按钮

需要配合 form 表单域使用

属性 value 修改按钮显示的值

```html
<input type="submit" />
<input type="reset" />
<input type="button" value="普通按钮" />Copy to clipboardErrorCopied
```





 

## [button 按钮标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=button-按钮标签)

type 取值

- submit 提交按钮
- reset 重置按钮
- button 普通按钮(默认)

```html
<button type="submit">提交按钮</button>
<button type="reset">重置按钮</button>
<button type="button">普通按钮</button>
<button>普通按钮</button>Copy to clipboardErrorCopied
```

提交按钮 重置按钮 普通按钮 普通按钮

## img 图像标签

![image-20221228232035900](../../AppData/Roaming/Typora/typora-user-images/image-20221228232035900.png)

## [select 下拉菜单](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=select-下拉菜单)

```html
<select>
  <option>北京</option>
  <option>上海</option>
  <option selected>广州</option>
  <select></select>
</select>Copy to clipboardErrorCopied
```

  北京  上海  广州 

option 选项

默认选中第一项，可以指定默认选中 selected

## [textarea 多行文本域](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=textarea-多行文本域)

属性

- cols 宽度 列数
- rows 高度 行数

```html
<textarea></textarea>Copy to clipboardErrorCopied
```



## [label 标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=label-标签)

点击文字也可选中选项

两种使用方式等效

```html
<input type="radio" name="sex" id="man" />
<label for="man">男</label>

<label><input type="radio" name="sex" />女</label>Copy to clipboardErrorCopied
```

 男 女

## [无语义标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=无语义标签)

- div 块级标签，独占一行
- span 行内标签

## [语义化标签](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=语义化标签)

手机端常用

- header 网页头部
- nav 网页导航
- footer 网页底部
- aside 网页侧边栏
- section 网页区块
- article 网页文章

以上标签和 div 等效，多了语义化

## [字符实体](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=字符实体)

在网页中显示特殊字符

- 空格 ` `
- 版权符 `©`

```html
<!-- 单词之间有5个空格，最后只显示一个空格 -->
hello world

<!-- 实现单词之间有5个空格 -->
hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;world

<!-- 版权符号 -->
&copy;Copy to clipboardErrorCopied
```

hello world

hello   world

©

| 特殊字符 | 描述     | 字符代码            |
| -------- | -------- | ------------------- |
|          | 空格     | &nbsp(;后面都有分号 |
| <        | 小于号   | &lt                 |
| >        | 大于号   | &gt                 |
| &        | 和号     | &amp                |
| ¥        | 人名币   | &yen                |
| ©        | 版权     | &copy               |
| ®        | 注册商标 | &reg                |
| °        | 摄氏度   | &deg                |
| ±        | 正负号   | &plusmn             |
| ×        | 乘号     | &times              |
| ÷        | 除号     | &divide             |
| ²        | 平方2    | &sup2               |
| ³        | 立方3    | &sup3               |

## [综合案例](https://mouday.github.io/coding-tree/#/blog/front-end-learn/html-element?id=综合案例)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible"
          content="IE=edge">
    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">
    <title>Form Demo</title>
</head>

<body>
    <h2>个人信息</h2>
    <form action="">
        <p>姓名:
            <input type="text"
                   placeholder="姓名">
        </p>
        <p>性别:
            <label><input type="radio"
                       name="sex"
                       checked>男</label>
            <label><input type="radio"
                       name="sex">女</label>
        </p>
        <p>爱好:
            <label><input type="checkbox"
                       checked>足球</label>
            <label><input type="checkbox">篮球</label>
            <label><input type="checkbox">羽毛球</label>
        </p>

        <p>现居：<select>
                <option value="">北京</option>
                <option value="">上海</option>
                <option value="">广州</option>
                <option value="">深圳</option>
            </select>
        </p>

        <p>个人简介：
            <br />
            <textarea cols="60"
                      rows="10"></textarea>
        </p>

        <input type="submit"
               value="提交">
        <button type="reset">重置</button>
    </form>
</body>

</html>Copy to clipboardErrorCopied
```

![image-20221228230203739](../AppData/Roaming/Typora/typora-user-images/image-20221228230203739.png)