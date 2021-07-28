---
title: "HTML"
date: 2020-11-07T15:58:26+08:00
lastmod: 2021-07-28T10:35:15+08:00

description: "HTML"
summary: "		HTML基础"
images: []

tags: [HTML]
categories: [HTML]
featuredImage: "/md/HTML.jpg"
---

## **HTML基本结构和属性**

​    **HTML ： 超文本 标记 语言**

```html
超文本 : 文本内容 + 非文本内容 ( 图片、视频、音频等 )

标记 : <单词>

语言 : 编程语言
标记也叫做标签：
    <header>
    <footer>
    写法分成两种：
        单标签   <header>
        双标签   <header></header>

    创建标签的快捷键：单词 + tab键 -> <单词>

标签是可以上下排列，也可以组合嵌套。
```

> **HTML常见标签：[http://www.html5star.com/manual/html5label-meaning/](http://www.html5star.com/manual/html5label-meaning/)**


```html
标签的属性：来修饰标签的，设置当前标签的一些功能。
    <标签 属性="值" 属性2="值2">
```

<br>

## **HTML初始代码**

**每个.html文件都有的代码叫做初始代码 ， 要复合html文件的规范写法。**

   **! + tab键 : 快速的创建html的初始代码**
```html
<!DOCTYPE html>           //文档声明 : 告诉浏览器这是一个html文件
<html lang="en"> //html文件的最外层标签：包裹着所有html标签代码 lang="en"表示是一个英文网站 lang="zh-CN"表示一个中文网站
    <head>
        <meta charset="UTF-8">    //元信息：是编写网页中的一些辅助信息 charset="UTF-8"国际编码，让网页不出现乱码的情况
        <title>Document</title>   //设置网页的标题
    </head>
    <body>
        显示网页内容的区域
    </body>
</html>
```

<br>

## **HTML注释**

- **写法：`<!-- 注释的内容 --> ` 在浏览器中看不到，只能在代码中看到注释的内容。**

- **意义：**

	1. 把暂时不用的代码注释起来，方便以后使用。
	2. 开发人员进行提示。

- **快捷添加注释与删除注释：**

	1. **`ctrl + /`**
	2. **`shift + alt + a `**

<br>

## **标题与段落**

- **标题 -> 双标签 : `<h1></h1>`   ...  `<h6></h6>`** **`在一个网页中，h1标题最重要，并且一个.html文件中只能出现一次h1标签。`**

  **`h5、h6标签在网页中不经常使用。`**

- **段落 -> 双标签 : `<p></p>`**

<br>

## **文本修饰标签**

-  **强调 -> 双标签 :**

   **`<strong></strong>`**

   **​`<em></em>`**

   **区别：**

   1. **写法和展示效果是有区别的，一个加粗、一个斜体**
   2. **`strong`的强调性更强，`em`的强调性稍弱。**

------



- **下标 : `<sub></sub>`**

  **​上标 : `<sup></sup>`**

------

- **删除文本 : `<del></del>`**
  
  **​插入文本 : `<ins></ins>`** 
  
  ​			**`注：一般情况下，删除文本都是和插入文本配合使用的。`**

------

<br>

## **图片标签**

 **`<img>` ---> 单标签** 

- **`src` : 引入图片的地址。**
- **`alt` : 当图片出现问题的时候，可以显示一段友好的提示文字。**
-  **`title` : 提示信息**
- **`width`、`height` : 图片的大小**

<br>

## **链接标签**

**`a` ---> 双标签	`<a></a>`**

- **`href` : 链接地址**
- **`target` : 可以改变链接打开的方式，默认情况下：在当前页面打开 `_self`  新窗口打开 `_blank`**

**`<base>` ---> 单标签 ：作用是改变链接的默认行为的**

​	**（一般写在`<head>`中）**

<br>

## **锚点**

 **两种做法**

- **#号 + id属性**
- **#号 + name属性（注意name属性加给的是a标签）**

<br>

## **特殊字符**

| **特殊字符** |   **含义**   | **特殊字符代码** |
| :----------: | :----------: | :--------------: |
|              |  **空格符**  |   **`&nbsp;`**   |
|   **`©`**    |   **版权**   |   **`&copy;`**   |
|   **`®`**    | **注册商标** |   **`&reg;`**    |
|   **`＜`**   |  **小于号**  |    **`&lt;`**    |
|   **`＞`**   |  **大于号**  |    **`&gt;`**    |
|   **`&`**    |   **和号**   |   **`&amp;`**    |
|   **`￥`**   |  **人民币**  |   **`&yen;`**    |
|   **`°`**    |  **摄氏度**  |   **`&deg;`**    |

<br>

## **列表标签**

1. **无序列表 ---> `ul` `li` 符合嵌套的规范**
2. **有序列表 ---> `ol` `li` 一般用的比较少，可以用无序列表来实现**
3. **定义列表 ---> `dl` `dt` `dd` 列表项需要添加标题和对标题进行描述的内容**

​    **`注：列表之间可以互相嵌套，形成多层级的列表`**

<br>

## **表格标签**

- **`<table>` ：表格的最外层容器**
- **`<tr>` ：定义表格行**
- **`<th>` ：定义表头**
- **`<td>` ：定义表格单元**
- **`<caption>` ：定义表格标题**

 **`注：上面属性是有嵌套关系的，要符合嵌套规范。`**

​     **语义化标签：`tHead`、`tBody`、`tFood`**

​	 **注：在一个`table`中，`tBody`是可以出现多次的，但是`tHead`、`tFood`只能出现一次。**

### **表格属性**

- **`border` ：表格边框**

- **`cellpadding` ：单元格内的空间**

- **`cellspacing` ：单元格之间的空间**

- **`rowspan` ：合并行**

- **`colspan` : 合并列**

- **`align` ：左右对齐方式**

- **`valign` ：上下对齐方式**

  [表格信息展示小案例](../demo/表格信息展示小案例/表格信息展示案例.html)
  
- **添加单线 ：`border-collapse` ：`collapse`**

- **隐藏空单元格 ：`empty-cells` ：`hide`**

- **列分组 ：`colgroup` `/` `col`**

<br>

## **表单标签**



### **表单元素**

- **`<form>` ：表单的最外层容器**

- **`<input>` --->单标签 ：标签用于搜集用户信息，根据不同的`type`属性值，展示不同的控件，如输入框、密码框、复选框等。**

  |    **`type`属性**    |                           **含义**                           |
  | :------------------: | :----------------------------------------------------------: |
  |      **`text`**      |                     **普通的文本输入框**                     |
  |    **`password`**    |                        **密码输入框**                        |
  |    **`checkbox`**    |                          **复选框**                          |
  |     **`radio`**      |                          **单选框**                          |
  |      **`file`**      |                         **上传文件**                         |
  |     **`submit`**     |                         **提交按钮**                         |
  |     **`reset`**      |                         **重置按钮**                         |
  |     **`color `**     |                      **选择颜色的控件**                      |
  |     **`date `**      |                     **选择年月日的控件**                     |
  |    **`datetime`**    |            **定义一个日期和时间控制器（本地时间**            |
  | **`datetime-local`** |               **选择一个日期和时间 (无时区)**                |
  |     **`month`**      |                       **选择一个月份**                       |
  |     **`search`**     | **input会呈现为搜索框（与text类型的唯一区别在于当鼠标覆盖时尾部出现叉号可快速清除输入的内容）** |
  |      **`tel`**       | **编辑电话号码的控件，提交时换行符会自动从输入框中去掉**<br />**（在移动端默认调起数字键盘）** |
  |      **`url`**       |   **编辑url的控件，提交时换行符与首位的空格都将自动去除**    |
  |     **`email`**      |                    **可输入一个邮件地址**                    |
  |     **`number`**     | **数值的输入域,例如`<input type="number" min="1" max="5">`** |
  |     **`range`**      |                          **滑动条**                          |

- **`<textarea>`  ：多行文本框**

- **`<select>`、`<option>`、`<optgroup>`  ：下拉菜单**

  - **`select`为下拉列表**
  - **`option`为下拉列表中的选项**
  - **`optgroup`定义选项组**

- **`<label>` ：辅助表单，如输入框前的文字，用以关联用户的选择**

- **`<button>` ：定义一个按钮**

- **`<fieldset>` ：定义域。即输入区加有文字的边框**

- **`<legend>` ：定义域的标题，即边框上的文字（为fieldset元素定义标题）**

### **表单常用属性**

|        属性         |                   含义                   |
| :-----------------: | :--------------------------------------: |
| **`placeholder `**  |                **背景字**                |
|  **`maxlength `**   |               **最大长度**               |
|  **`minlength `**   |               **最小长度**               |
|   **`checked `**    |         **单选,复选的默认选中**          |
|   **`selected`**    |            **下拉框默认选中**            |
|   **`readonly `**   | **只读, 只能看不能改, 能够提交给服务器** |
|   **`disabled `**   | **禁用, 只能看不能改, 不能提交给服务器** |
|  **`autofocus `**   |             **自动获取光标**             |
| **`autocomplete `** |        **自动提示 值: on 或 off**        |
|   **`multiple`**    |              **多选(文件)**              |
|   **`required `**   |               **不能为空**               |
|    **`pattern`**    |               **正则验证**               |

```html
<form action="demo.php">  
        <input type="text" name="name" placeholder="your tel">
        <br>
        <input type="text" name="pwd" minlength="6" maxlength="10">
        <br>
        <label><input type="radio" name="sex" value="1"> 男</label>
        <label><input type="radio" name="sex" value="2" checked> 女</label>
        <br>
        <select name="address">
            <option value="1"> 地球 </option>
            <option value="2"> 火星 </option>
            <option value="3"> 阿联酋 </option>
            <option value="4"> 泰坦星 </option>
            <option value="5"> 埃塞俄比亚 </option>
            <option value="6" selected> 亚欧尼亚 </option>
            <option value="7"> 铁岭 </option>
            <option value="8"> 四平 </option>
        </select>
        <br>
        <input type="text" name="a" value="这是只读" readonly>
        <input type="text" name="b" value="这是禁用" disabled>
        <br>
        <input type="text" autofocus>
        <br>
        <input type="text" name="tel" maxlength="11" autocomplete="Off">
        <br>
        <!-- 单选文件 -->
        <input type="file">
        <!-- 多选文件
             注意:
                添加属性 multiple 才能实现多选
                给name值补上[], 才能真正选择多个文件
         -->
        <input type="file" name="photo[]" multiple>
        <br>
        <input type="password" name="passwd"  required> 
        <br>
        <input type="submit">
</form>
```

<br>

## **div和span**

- **`div` ：做一个区域划分的块**
- **`span`  ：对文字进行修饰的内联**

<br>

## **引用标签**

- **`blockquote` ：引用大段的段落解释**
- **`q` ：引用小段的短语解释**
- **`abbr` ：缩写或首字母缩略词**
- **`address` ：引用文档地址信息**
- **`cite` ：引用著作的标题**

<br>

## **iframe标签**

**`iframe 元素会创建包含另外一个文档的内联框架（即行内框架）`**

|     **属性**      |              **含义**              |
| :---------------: | :--------------------------------: |
| **`frameborder`** |   **规定是否显示框架周围的边框**   |
|    **`width`**    |       **定义`iframe`的宽度**       |
|   **`height`**    |       **定义`iframe`的高度**       |
|  **`scrolling`**  | **规定是否在`iframe`中显示滚动条** |
|     **`src`**     |  **规定在`iframe`中引入的`URL`**   |
|   **`srcdoc`**    | **规定在`iframe`中显示的页面内容** |

**应用场景**：数据传输、共享代码，局部刷新、第三方介入等

<br>

##  **pre 与 code**

-   **`pre` 元素可定义预格式化的文本。被包围在 pre 元素中的文本通常会保留空格和换行符**
- ***只应该在表示计算机程序源代码或者其他机器可以阅读的文本内容上使用 code 标签。虽然 code 标签通常只是把文本变成等宽字体，但它暗示着这段文本是源程序代码***

<br>

##  **map 与 area**

**给特殊图形添加链接，`area`能添加的热区的形状：矩形、圆形、多边形**

<br>

## **embed 与 object**

**`embed`和`object`都表示能够嵌入一些多媒体，如flash动画、插件等。基本使用没有太多区别，主要是为了兼容不同的浏览器而已**

***`object` 元素需要配合`param` 元素一起完成***

<br>

## **audio 与 video**

**`audio`标签表示嵌入音频文件，`video`标签表示嵌入视频文件。`默认`控件是不显示的，可通过`controls`属性来显示控件**

***为了能够支持多个备选文件的兼容支持，可以配合`source`标签***

<br>

## **文字注解与文字**

-  **`ruby` 标签定义 `ruby` 注释（中文注音或字符），`rt` 标签定义字符（中文注音或字符）的解释或发音**

  ```html
  <ruby>
  	寒<rt>han</rt>
  </ruby>
  ```

- **`bdo` 标签可覆盖默认的文本方向**

<br>

## **拓展link标签**

- **添加网址标题栏签前的小图标**

  ```html
  <link rel="icon" type="/image/x-icon" href="图片地址">
  ```

- **DNS预解析**

  ```html
  <link rel="dns-prefetch" href="DNS解析地址">
  ```

<br>

## **HTML5新的语义化标签**

|  **标签名**  |   **含义**   |
| :----------: | :----------: |
| **`header`** |   **页眉**   |
| **`footer`** |   **页脚**   |
|  **`main`**  |   **主体**   |
| **`hgroup`** | **标题组合** |
|  **`nav`**   |   **导航**   |

> **注：**`header`、`footer`、`main`在一个网页中只能出现一次

|         **标签名**          |            **含义**             |
| :-------------------------: | :-----------------------------: |
|        **`article`**        |         **独立的内容**          |
|         **`aside`**         |       **辅助信息的内容**        |
|        **`section`**        |            **区域**             |
|        **`figure`**         |       **描述图像或视频**        |
|      **`figcaption`**       |  **描述图像或视频的标题部分**   |
|       **`datalist`**        |          **选项列表**           |
| **`details` `/` `summary`** |    **文档细节 `/` 文档标题**    |
| **`progress` `/` `meter`**  | **定义进度条 `/` 定义度量范围** |
|         **`time`**          |       **定义日期或时间**        |
|         **`mark`**          |       **带有记号的文本**        |

<br>

## **BFC规范**

- <strong><mark><abbr>BFC </abbr></mark></strong>即 Block Formatting Contexts (块级格式化上下文) ，它属于上述中的其中一种规范。具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性
- **触发BFC的样式**
  - 浮动元素 ：float 除 none 以外的值
  - 绝对定位元素 ：position （absolute 、fixed）
  - display 为 inline-block、table-cells、flex
  - overflow 除了visible 以外的值（hidden、auto、scroll）

