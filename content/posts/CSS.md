---
title: "CSS"
date: 2020-11-07T15:58:26+08:00
lastmod: 2021-06-22T15:23:26+08:00

description: "CSS"
summary: "		CSS基础"
images: []

tags: [CSS]
categories: [CSS]
featuredImage: "/md/CSS/CSS.jpg"

---


## **CSS基础语法**

- **格式 ：**

  ```css
   选择器 { 属性1 : 值1 ; 属性2 : 值2 }
  ```

- **单位 ：**

  **长度单位 ：**

  1. **`px` ---> 像素**	
  2. **`%` ---> 百分比    
         外容器1 -> 600px  当前容器 50% -> 300px**
         **外容器2 -> 400px  当前容器 50% -> 200px**

- **基本样式 ：**

  &nbsp;&nbsp;&nbsp;&nbsp;​	**`width` : 宽**<br>
  &nbsp;&nbsp;&nbsp;&nbsp;​	**`height` : 高**<br>
  &nbsp;&nbsp;&nbsp;&nbsp;​	**`background-color` : 背景色**

- **CSS注释 ：**

  ```css
  /*CSS注释的内容*/
  ```

<br>

## **CSS样式的引入方式**

### **内联样式**

​	**`style`属性**

### **内部样式**

​	**`style`标签**<br>

&nbsp;&nbsp;​	**区别：**
​        **内部样式的代码可以复用、复合W3C的规范标准，进行让结构和样式分开处理**

### **外部样式**

**引入一个单独的CSS文件，例如：`name.css`**

- **通过`link`标签引入外部资源，`rel`属性指定资源跟页面的关系，`href`属性资源的地址。**

  ```html
  <link rel="stylesheet" href="./name.css">
  ```

- **通过`@impor`t方式引入外部样式 ( 这种方式有很多问题，不建议使用 )**

  ```html
   <style>@import url('./common.css');</style>
  ```

**`link`和`@import`的区别：**

 1. **从属关系区别**

    `@import`是 CSS 提供的语法规则，只有导入样式表的作用；`link`是HTML提供的标签，不仅可以加载 CSS 文件，还可以定义 `RSS`、`rel` 连接属性等

 2. **加载顺序区别**

    加载页面时，`link`标签引入的 CSS 被同时加载；`@import`引入的 CSS 将在页面加载完毕后被加载

 3. **兼容性区别**

    `@import`是 CSS2.1 才有的语法，故只可在 IE5+ 才能识别；`link`标签作为 HTML 元素，不存在兼容性问题

 4. **`DOM`可控性区别**

    可以通过 JS 操作 `DOM` ，插入`link`标签来改变样式；由于 DOM 方法是基于文档的，无法使用`@import`的方式插入样式

<br>

## **CSS中的颜色表示法**

1. **单词表示法 ：`red` `blue` `green` `yellow`**

   ![颜色名称](https://static01.imgkr.com/temp/8d9487f36a26402c98366645b73b0d8c.jpg)

2. **十六进制表示法 ：`#000000` `#ffffff`**

   0 1 2 3 4 5 6 7 8 9 a b c d e f

3. `RGB`**表示法 ：`rgb(255,255,255)`**

   取值范围 0 ~ 255

   **获取颜色的工具：**
           [**https://www.baidufe.com/fehelper**](https://www.baidufe.com/fehelper)

<br>

## **CSS背景样式**

### **` background-color` 背景色**

### **`background-image` 背景图**

- `url`(背景地址)		

  `默认：会水平垂直都铺满背景图`	

### **`background-repeat` 平铺方式**

- `repeat-x`   x轴平铺
- `repeat-y`   y轴平铺
- `repeat` ( x , y 都进行平铺，`默认值` )
- `no-repeat`  都不平铺

### **`background-position` : 背景位置**

-  **`x` `y` : number(`px`、`%`) | 单词**

&#12288;&#12288;&#12288;&#12288;**x :** `left`、`center`、`right`

&#12288;&#12288;&#12288;&#12288;**y :** `top`、`center`、`bottom`

### **`background-attachment` : 背景图随滚动条移动的方式**

- `scroll` : `默认值`  ( 背景位置是按照当前元素进行偏移的 )

- `fixed` ： ( 背景位置是按照浏览器进行偏移的 )

  **练习 ：[利用滚动条移动方式实现视觉差网页](../demo/视觉差/视觉差.html)（请用PC浏览器查看）**

<br>

## **CSS边框样式**

###  **`border-style` : 边框样式**

- `solid` : 实线
- `dashed` : 虚线
- `dotted` : 点线

### **`border-width` : 边框大小**

- number(`px`、`%`) 

### **`border-color` : 边框颜色**

- `red` `#f00` ...     

边框也可以针对某一边进行单独设置 : `border-left-style` : 中间是方向 `left`、`right`、`top`、`bottom`   

颜色：透明颜色 `transparent`

<br>

## **CSS文字样式**

### **`font-family` : 字体类型**

- 英文字体：例如 ：`Arial` , '`Times New Roman`' 

- 中文字体：例如 ：`微软雅黑` ,  `宋体`

  中文字体都有英文名称

- `衬线体`、`非衬线体`<br>
  `衬线字体`（宋体）：见名知意，就是`比划有粗有细，非衬线字体所以字的所有比划的都是一样粗细（幼圆）`

  &#12288;**区别 ：**

  - *`衬线字体每个字的笔划有粗有细`*，在连续阅读时流畅性更好
  - *`无衬线字体笔划粗细均匀`*，适用于单词短句

   > **注意 ：如果字体名称出现空格要用引号，如：*'`Times New Roman`'***

### **`font-size` : 字体大小**

- 默认 ：**`16px`**

- 写法 ：

  1. number(`px`)
  
  2. 单词 ( small large ... )**不推荐使用**
  
     |  **属性取值**  |    **字体大小**    |
     | :------------: | :----------------: |
     | **`xx-small`** |      **最小**      |
     | **`x-small`**  |      **较小**      |
     |  **`small`**   |       **小**       |
     |  **`medium`**  | **正常（默认值）** |
     |  **`large`**   |       **大**       |
     | **`x-large`**  |      **较大**      |
     | **`xx-large`** |      **最大**      |
  
  > **注 ：字体大小一般为偶数**

### **`font-weight` : 字体粗细**

- 模式 ：

  |  **属性值**   |                           **描述**                           |
  | :-----------: | :----------------------------------------------------------: |
  | **`normal`**  |                 **`默认值` 定义标准的字符**                  |
  |  **`bold`**   |                       **定义粗体字符**                       |
  | **`bolder`**  |                      **定义更粗的字符**                      |
  | **`lighter`** |                      **定义更细的字符**                      |
  | **`inherit`** |              **规定应该从父元素继承字体的粗细**              |
  | **`100~900`** | **定义由粗到细的字符<br>`400` 等同于 normal，而 `700` 等同于 bold** |

- 写法 ：

  1. 单词 (normal、bold) 
  2. number ( 100 ..... 900 ）<br>`100到500都是正常的，600都900都是加粗的` 

###  **`font-style` : 字体样式**

- 模式 ：

  |  **属性值**   |                 **描述**                  |
  | :-----------: | :---------------------------------------: |
  | **`normal`**  | **`默认值` 浏览器显示一个标准的字体样式** |
  | **`italic`**  |    **浏览器会显示一个斜体的字体样式**     |
  | **`oblique`** |    **浏览器会显示一个倾斜的字体样式**     |
  | **`inherit`** |     **规定应该从父元素继承字体样式**      |

- 写法：单词 (  normal 、 italic )

>**注：`oblique`也是表示斜体，用的比较少，一般了解即可<br>**
>
>**区别 ：**
>
>1. **`italic` 带有倾斜属性的字体的才可以设置倾斜操作**
>2. **`oblique` 没有倾斜属性的字体也可以设置倾斜操作**

<br>

## **CSS段落样式**

### **`text-decoration`：文本装饰**

- `underline` ：下划线

- `line-through` ：删除线

- `overline` ：上划线

- `none` ：不添加任何装饰

  > **注：添加多个文本修饰用空格隔开即可,如：`line-through underline overline`**

###  **`text-transform`：文本大小写 （ `针对英文段落` ）**

- `lowercase` ：小写
- `uppercase` ：大写
- `capitalize` ：只针对首字母大写

###  **`text-indent` : 文本缩进**

- `em`单位：相对单位，`1em`永远都是跟字体大小相同

### **`text-align` : 文本对齐方式**

- 对齐方式 ：

  |  **属性值**   |                    **描述**                    |
  | :-----------: | :--------------------------------------------: |
  |  **`left`**   |  **把文本排列到左边。`默认值`：由浏览器决定**  |
  |  **`right`**  |              **把文本排列到右边**              |
  | **`center`**  |              **把文本排列到中间**              |
  | **`justify`** |            **实现两端对齐文本效果**            |
  | **`inherit`** | **规定应该从父元素继承 `text-align` 属性的值** |

### **`line-height` : 定义行高**

- `默认行高`：不是固定值，而是变化的。根据当前字体的大小再不断的变化
- 取值 ：
  1. number( `px` )
  2. scale ( 比例值 , 跟文字大小成比例的 )

### **`letter-spacing` : 字之间的间距**

### **`word-spacing` : 词之间的间距  ( `针对英文段落的，中文不生效` )**

### **强制折行 : (针对英文)**

1. `word-break` : `break-all`; **(非常强烈的折行)**
2. `word-wrap` : `break-word`;**(不是那么强烈的折行，会产生一些空白区域)** 

<br>

## **CSS复合样式**

**一个CSS属性只控制一种样式，叫做`单一样式` 一个CSS属性控制多种样式，叫做`复合样式`**

**复合样式**

- **`background`**

  **例如 ：**`background` **:** `red` `url()` `repeat` `0` `0`；

- **`border`**

  **例如 ：**`border` **:** `1px` `red` `solid`;

- **`font`**

  **`注` ：** 最少要有两个值 `size` `family`

  **正确写法 ：**

  1. `weight style size family  √`
  2. `style weight size family  √`
  3. `weight style size/line-height family √`

> **复合的写法，是通过空格的方式实现的。复合写法有的是不需要关心顺序，例如`background`、`border`；有的是需要关心顺序，例如`font`**
>
> <br>
>
> **注：如果非要混合去写的话，那么要先写复合样式，再写单一样式，这样样式才不会被覆盖掉。**

<br>

## **CSS选择器**

### **`ID` 选择器** 

&#12288;**写法 ：**

- **css : `#`elem{}**
- **html : `id`=“elem”**

>**注：**
>
>1. **`ID是唯一值，在一个页面中只能出现一次，出现多次是不符合规范的`**
>2. **命名的规范，由字母、下划线、中划线、字母（并且第一个不能是数字）**
>3. **驼峰写法 : `searchButton` (小驼峰)  `SearchButton` (大驼峰)**   
>     **searchSmallButton**
>    -  **短线写法：`search-small-button`**
>    - **下划线写法：`search_small_button`**

### **`CLASS` 选择器** 

&#12288;**写法 ：**

- **css : `.`elem{}**
- **html : `class `=“elem”**

>**注：**
>
>1. **`class选择器是可以复用的`**
>2. **可以添加多个class样式**
>3. **多个样式的时候，样式的优先级根据CSS中的顺序决定，而不是class属性中的顺序**
>4. **标签+类的写法**

### **标签选择器(`TAG`选择器)**

&#12288;**写法 ：**

- **css : `div`{}**
- **html : `<div>`**

>**使用的场景：**
>
>1. **去掉某些标签的默认样式时**
>2. **复杂的选择器中，如 层次选择器**

### **群组选择器(分组选择器)**

&#12288;**写法 ：**

- **css : `div` , `p` , `span`{}**

### **通配选择器**

&#12288;**写法 ：**

- **css : `*`{}**

>**注：尽量避免使用通配选择器，因为会给所有的标签添加样式，慎用**
>
>**使用的场景：**
>
>1. **去掉所有标签的默认样式时**

### **层次选择器**

- 后代  ：M N { } （所有的后代都会被设置）
- 父子  ：M > N { } （只有孩子会被设置，孩子的孩子不受影响）
- 兄弟  ： M ~ N { }  当前M下面的所有兄弟N标签
- 相邻  ： M + N { }  当前M下面相邻的N标签

### **属性选择器**

`attr` 属性

|       **选择器**        |                           **说明**                           |
| :---------------------: | :----------------------------------------------------------: |
|      **M[`attr`]**      |              **M元素选择指定为attr属性的集合**               |
|   **M[attr`=`value]**   | **M元素选择指定为attr属性和value值的集合**<br>**（`完全匹配`）** |
|  **M[attr`*=`value]**   | **M元素选择指定为attr属性并且包含值为value的集合**<br>**(`部分匹配`)** |
|  **M[attr`^=`value]**   | **M元素选择指定为attr属性并且起始值为value的集合**<br>**(`起始匹配`)** |
|  **M[attr`$=`value]**   | **M元素选择指定为attr属性并且结束值为value的集合**<br>**(`结束匹配`)** |
| **M[`attr1`][`attr2`]** |     **M元素选择满足多个属性的集合**<br>**(`组合匹配`)**      |

### 伪类选择器

&#12288;**写法 ：`M:伪类{}`**

|    **伪类**    |                    **说明**                    |
| :------------: | :--------------------------------------------: |
|  **`:link`**   |   **访问前的样式    ( `只能添加给a标签` )**    |
| **`:visited`** |   **访问后的样式    ( `只能添加给a标签` )**    |
|  **`:hover`**  | **鼠标移入时的样式  (`可以添加给所有的标签`)** |
| **`:active`**  | **鼠标按下时的样式  (`可以添加给所有的标签)`** |

> **注：**
>
> 1. **link visited 只能给a标签加，hover和active 可以给所有的标签加**
> 2. **如果四个伪类都生效，一定要注意顺序 : L V H A**
> 3. **一般网站只这样去设置：a{} a:hover{}**

#### **结构性伪类选择器**

|      **伪类选择器**       |                           **说明**                           |
| :-----------------------: | :----------------------------------------------------------: |
|     **`first-child`**     |                **单独指定第一个子元素的样式**                |
|     **`last-child`**      |               **单独指定最后一个子元素的样式**               |
|    **`nth-child(n)`**     | **选择器匹配正数下来的第N个子元素<br>`nth-child(odd)`为第奇数个子元素<br>`nth-child(even)`为第偶数个子元素** |
|  **`nth-last-child(n)`**  |                **匹配倒数数下来第n个子元素**                 |
|   **`nth-of-type(n)`**    | **选择器匹配属于父元素的特定类型的第 N 个子元素的每个元素**  |
| **`nth-last-of-type(n)`** | **择器匹配属于父元素的特定类型的第 N 个子元素的每个元素<br>从最后一个子元素开始计数** |
|    **`first-of-type`**    |       **选择器匹配元素其父级是特定类型的第一个子元素**       |
|    **`last-of-type`**     |      **选择器匹配元素其父级是特定类型的最后一个子元素**      |
|    **`only-of-type`**     |  **代表了任意一个元素，这个元素没有其他相同类型的兄弟元素**  |

> ***n* 可以是数字、关键词或公式**

<br>

## **CSS样式继承**

- **文字相关的样式可以被继承**
- **布局相关的样式不能被继承（默认是不能继承的，但是可以设置继承属性 `inherit` 值）**

<br>

## **CSS优先级**

### **相同样式优先级**

&#12288;&#12288;**当设置相同样式时，后面的优先级较高，但不建议出现重复设置样式的情况**

### **内部样式与外部样式**

&#12288;&#12288;**内部样式与外部样式优先级相同，如果都设置了相同样式，那么后写的引入方式优先级高**

### **单一样式优先级**

&#12288;&#12288;**`style行间 `> `id` > `class` > `tag` > `*` > 继承**

> **注 ：**
>
> - **`style`行间 权重 1000**
> - **`id`       权重 100**
> - **`class`    权重 10**
> - **`tag`      权重 1**

### **!important**

&#12288;&#12288; **提升样式优先级，非规范方式，不建议使用。( 不能针对继承的属性进行优先级的提升 )**

### **标签+类与单类**

&#12288;&#12288;**标签+类 `>` 单类**

<br>

## **CSS盒子模型**

​		&#12288;![标准盒子模型](../md/CSS/标准盒子模型.png)

  **组成 : `content` ---> `padding` ---> `border` ---> `margin`** <br>
 &#12288;**&#12288;&#12288;&#12288;物品&#12288;&#12288;&#12288;&#12288;填充物&#12288;&#12288;&#12288;&#12288;包装盒&#12288;&#12288;盒子与盒子之间的间距**

-  **`content` : 内容区域  `width`和`height`组成的**

- **`padding` : 内边距(内填充)**

  只写一个值： 30px (上下左右)<br>
  写两个值 : 30px 40px ( 上下、左右 )<br>写四个值 : 30px 40px 50px 60px（上、右、下、左）<br>

  **单一样式只能写一个值：**

  - **`padding-left`**
  - **`padding-right`**
  - **`padding-top`**
  - **`padding-bottom`**

- **`margin` : 外边距(外填充)**

  只写一个值： 30px (上下左右)<br>
  写两个值 : 30px 40px ( 上下、左右 )<br>写四个值 : 30px 40px 50px 60px（上、右、下、左）<br>

  **单一样式只能写一个值：**

  - `margin-left`
  - `margin-right`
  - `margin-top`
  - `margin-bottom`

>**注 ：**
>
>1. **背景色填充到margin以内的区域 （不包括margin区域）**
>2. **文字在content区域添加**
>3. **padding不能为负数，而margin可以为负数**

### **box-sizing**

- **盒尺寸：可以改变盒子模型的展示形态**

-  **默认值： `content-box`**

  |                          **属性值**                          |                           **说明**                           |
  | :----------------------------------------------------------: | :----------------------------------------------------------: |
  | **`content-box`<br>标准盒模型，又叫做 W3C盒模型<br>一般在现代浏览器中使用的都是这个盒模型** | **padding和border不被包含在定义的width和height之内。<br/>`盒子的实际宽度=设置的width+padding+border`** |
  |  **`border-box`<br>怪异盒模型<br>低版本IE浏览器中的盒模型**  | **padding和border被包含在定义的width和height之内。<br/>`盒子的实际宽度=设置的width（padding和border不会影响实际宽度）`** |

- **使用的场景：**  

  1. **不用再去计算一些值**
  2. **解决一些百分比%的问题**

### **盒子模型的一些问题**

1. **margin叠加问题，出现在上下margin同时存在的时候。会取上下中值较大的作为叠加的值**

   **解决方案 ：**

   - **BFC规范**
   - **想办法只给一个元素添加间距**

2. **margin传递问题，出现在嵌套的结构中，只是针对margin-top的问题**

   **解决方案 ：**

   - **BFC规范**
   - **给父容器加边框**
   - **margin换成padding**

### **拓展**

1. **margin左右自适应是可以的 ，但是上下自适应是不行的**
2. **width、height不设置的时候，会自动去计算容器的大小，节省代码**

<br>

## **标签分类**

- **按类型**

  - **block 块元素** 

    **`div`、`p`、`h1...h6`、`ol`、`ul`、`dl`、`table`、`address`、`blockquote`、`form`**

    1. **独占一行**
    2. **支持所有样式**
    3. **不写宽的时候，跟父元素的宽相同**
    4. **所占区域是一个矩形**
  
  - **inline 内联元素**
  
    **`span` 、`a`、`em`、`strong`、`img` ...**
  
    1. **挨在一起的**
    2. **有些样式不支持，例如：`width`、`height`、`margin`、`padding`**
    3. **不写宽的时候，宽度由内容决定**
    4. **所占的区域不一定是矩形**
    5. **内联标签之间会有空隙，原因：代码换行产生的**
  
  - **inline-block 内联块级元素**
  
    **`input`、`select` ...**
  
    1. **挨在一起，但是支持宽高**
  
  > **注：布局一般用块标签，修饰文本一般用内联标签**

- **按内容**

  <object width="1000" height="288" data="/images/content-venn.svg">
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="-250 -150 1000 288">
   <style type="text/css">
    svg     { font: bold 18px sans-serif; text-anchor: middle; }
    ellipse { fill: #3c790a; stroke: #000000; opacity: 0.67; }
    text    { fill: #ffffff; pointer-events: none; }
    ellipse:hover { stroke-width: 6px;}
    ellipse:not(:hover) + foreignObject { display: none; }
    foreignObject  div { font: 14px sans-serif; }
    foreignObject  h1 { margin: 0 0 0.25em 0; padding: 0; font: 900 27px sans-serif; }
    foreignObject ul { margin: 0; padding: 0 0 0 1em; }
    foreignObject li { display: inline; margin: 0; padding: 0; line-height: 1.5; }
    foreignObject li:not(:last-child):after { content: ', '; }
    foreignObject span { font: italic 14px sans-serif; }
    foreignObject code { font: 1em monospace; color: orangered; }
    foreignObject p { margin: 0.75em 0 0 0; padding: 0 0 0 1em; font: italic 14px sans-serif; }
   </style>
   <g class="a" transform="translate(2, -3)">
    <ellipse rx="244" ry="132"/>
    <foreignObject x="250" y="-150" width="500" height="288" transform="translate(-2, 3)">
     <div xmlns="http://www.w3.org/1999/xhtml">
      <h1>Flow content</h1>
      <ul>
       <li><code>a</code></li>
       <li><code>abbr</code></li>
       <li><code>address</code></li>
       <li><code>area</code>*</li>
       <li><code>article</code></li>
       <li><code>aside</code></li>
       <li><code>audio</code></li>
       <li><code>b</code></li>
       <li><code>bdi</code></li>
       <li><code>bdo</code></li>
       <li><code>blockquote</code></li>
       <li><code>br</code></li>
       <li><code>button</code></li>
       <li><code>canvas</code></li>
       <li><code>cite</code></li>
       <li><code>code</code></li>
       <li><code>data</code></li>
       <li><code>date</code></li>
       <li><code>datalist</code></li>
       <li><code>del</code></li>
       <li><code>details</code></li>
       <li><code>dfn</code></li>
       <li><code>dialog</code></li>
       <li><code>div</code></li>
       <li><code>dl</code></li>
       <li><code>em</code></li>
       <li><code>embed</code></li>
       <li><code>fieldset</code></li>
       <li><code>figure</code></li>
       <li><code>footer</code></li>
       <li><code>form</code></li>
       <li><code>h1</code></li>
       <li><code>h2</code></li>
       <li><code>h3</code></li>
       <li><code>h4</code></li>
       <li><code>h5</code></li>
       <li><code>h6</code></li>
       <li><code>header</code></li>
       <li><code>hgroup</code></li>
       <li><code>hr</code></li>
       <li><code>i</code></li>
       <li><code>iframe</code></li>
       <li><code>img</code></li>
       <li><code>input</code></li>
       <li><code>ins</code></li>
       <li><code>kbd</code></li>
       <li><code>keygen</code></li>
       <li><code>label</code></li>
       <li><code>link</code>*</li>
       <li><code>main</code>*</li>
       <li><code>map</code></li>
       <li><code>mark</code></li>
       <li><code>math</code></li>
       <li><code>menu</code></li>
       <li><code>meta</code>*</li>
       <li><code>meter</code></li>
       <li><code>nav</code></li>
       <li><code>noscript</code></li>
       <li><code>object</code></li>
       <li><code>ol</code></li>
       <li><code>output</code></li>
       <li><code>p</code></li>
       <li><code>picture</code></li>
       <li><code>pre</code></li>
       <li><code>progress</code></li>
       <li><code>q</code></li>
       <li><code>ruby</code></li>
       <li><code>s</code></li>
       <li><code>samp</code></li>
       <li><code>script</code></li>
       <li><code>section</code></li>
       <li><code>select</code></li>
       <li><code>slot</code></li>
       <li><code>small</code></li>
       <li><code>span</code></li>
       <li><code>strong</code></li>
       <li><code>sub</code></li>
       <li><code>sup</code></li>
       <li><code>svg</code></li>
       <li><code>table</code></li>
       <li><code>template</code></li>
       <li><code>textarea</code></li>
       <li><code>time</code></li>
       <li><code>u</code></li>
       <li><code>ul</code></li>
       <li><code>var</code></li>
       <li><code>video</code></li>
       <li><code>wbr</code></li>
       <li><span>autonomous custom elements</span></li>
       <li><span>Text*</span></li>
      </ul>
      <p>* Under certain circumstances (see prose).</p>
     </div>
    </foreignObject>
    <text x="10" y="-94">Flow</text>
   </g>
   <g class="b" transform="translate(127, -48.5)">
    <ellipse rx="75" ry="42.5"/>
    <foreignObject x="250" y="-150" width="500" height="288" transform="translate(-127, 48.5)">
     <div xmlns="http://www.w3.org/1999/xhtml">
      <h1>Heading content</h1>
      <ul>
       <li><code>h1</code></li>
       <li><code>h2</code></li>
       <li><code>h3</code></li>
       <li><code>h4</code></li>
       <li><code>h5</code></li>
       <li><code>h6</code></li>
       <li><code>hgroup</code></li>
      </ul>
     </div>
    </foreignObject>
    <text x="2" y="6">Heading</text>
   </g>
   <g class="c" transform="translate(125, 42)">
    <ellipse rx="75" ry="42.5"/>
    <foreignObject x="250" y="-150" width="500" height="288" transform="translate(-125, -42)">
     <div xmlns="http://www.w3.org/1999/xhtml">
      <h1>Sectioning content</h1>
      <ul>
       <li><code>article</code></li>
       <li><code>aside</code></li>
       <li><code>nav</code></li>
       <li><code>section</code></li>
      </ul>
     </div>
    </foreignObject>
    <text x="1" y="5">Sectioning</text>
   </g>
   <g class="d" transform="translate(-113, 78)">
    <ellipse rx="117" ry="47" transform="rotate(-15)"/>
    <foreignObject x="250" y="-150" width="500" height="288" transform="translate(113, -78)">
     <div xmlns="http://www.w3.org/1999/xhtml">
      <h1>Metadata content</h1>
      <ul>
       <li><code>base</code></li>
       <li><code>link</code></li>
       <li><code>meta</code></li>
       <li><code>noscript</code></li>
       <li><code>script</code></li>
       <li><code>style</code></li>
       <li><code>template</code></li>
       <li><code>title</code></li>
      </ul>
     </div>
    </foreignObject>
    <text x="-4" y="8">Metadata</text>
   </g>
   <g class="e" transform="translate(-128, -34)">
    <ellipse rx="94" ry="51"/>
    <foreignObject x="250" y="-150" width="500" height="288" transform="translate(128, 34)">
     <div xmlns="http://www.w3.org/1999/xhtml">
      <h1>Interactive content</h1>
      <ul>
       <li><code>a</code>*</li>
       <li><code>audio</code>*</li>
       <li><code>button</code></li>
       <li><code>details</code></li>
       <li><code>embed</code></li>
       <li><code>iframe</code></li>
       <li><code>img</code>*</li>
       <li><code>input</code>*</li>
       <li><code>keygen</code></li>
       <li><code>label</code></li>
       <li><code>object</code>*</li>
       <li><code>select</code></li>
       <li><code>textarea</code></li>
       <li><code>video</code>*</li>
      </ul>
      <p>* Under certain circumstances.</p>
     </div>
    </foreignObject>
    <text x="-36" y="5">Interactive</text>
   </g>
   <g class="f" transform="translate(-40.5, -5)">
    <ellipse rx="76.5" ry="80"/>
    <foreignObject x="250" y="-150" width="500" height="288" transform="translate(40.5, 5)">
     <div xmlns="http://www.w3.org/1999/xhtml">
      <h1>Phrasing content</h1>
      <ul>
       <li><code>a</code>*</li>
       <li><code>abbr</code></li>
       <li><code>area</code>*</li>
       <li><code>audio</code></li>
       <li><code>b</code></li>
       <li><code>bdi</code></li>
       <li><code>bdo</code></li>
       <li><code>br</code></li>
       <li><code>button</code></li>
       <li><code>canvas</code></li>
       <li><code>cite</code></li>
       <li><code>code</code></li>
       <li><code>data</code></li>
       <li><code>date</code></li>
       <li><code>datalist</code></li>
       <li><code>del</code>*</li>
       <li><code>dfn</code></li>
       <li><code>em</code></li>
       <li><code>embed</code></li>
       <li><code>i</code></li>
       <li><code>iframe</code></li>
       <li><code>img</code></li>
       <li><code>input</code></li>
       <li><code>ins</code>*</li>
       <li><code>kbd</code></li>
       <li><code>keygen</code></li>
       <li><code>label</code></li>
       <li><code>link</code>*</li>
       <li><code>map</code>*</li>
       <li><code>mark</code></li>
       <li><code>math</code></li>
       <li><code>meta</code>*</li>
       <li><code>meter</code></li>
       <li><code>noscript</code></li>
       <li><code>object</code></li>
       <li><code>output</code></li>
       <li><code>picture</code></li>
       <li><code>progress</code></li>
       <li><code>q</code></li>
       <li><code>ruby</code></li>
       <li><code>s</code></li>
       <li><code>samp</code></li>
       <li><code>script</code></li>
       <li><code>select</code></li>
       <li><code>slot</code></li>
       <li><code>small</code></li>
       <li><code>span</code></li>
       <li><code>strong</code></li>
       <li><code>sub</code></li>
       <li><code>sup</code></li>
       <li><code>svg</code></li>
       <li><code>template</code></li>
       <li><code>textarea</code></li>
       <li><code>time</code></li>
       <li><code>u</code></li>
       <li><code>var</code></li>
       <li><code>video</code></li>
       <li><code>wbr</code></li>
       <li><span>autonomous custom elements</span></li>
       <li><span title="text content">Text</span>*</li>
      </ul>
      <p>* Under certain circumstances; see prose.</p>
     </div>
    </foreignObject>
    <text x="0" y="-39.5">Phrasing</text>
   </g>
   <g class="g" transform="translate(-42, -7)">
    <ellipse rx="68" ry="22.5"/>
    <foreignObject x="250" y="-150" width="500" height="288" transform="translate(42, 7)">
     <div xmlns="http://www.w3.org/1999/xhtml">
      <h1>Embedded content</h1>
      <ul>
       <li><code>audio</code></li>
       <li><code>canvas</code></li>
       <li><code>embed</code></li>
       <li><code>iframe</code></li>
       <li><code>img</code></li>
       <li><code>math</code></li>
       <li><code>object</code></li>
       <li><code>picture</code></li>
       <li><code>svg</code></li>
       <li><code>video</code></li>
      </ul>
     </div>
    </foreignObject>
    <text x="0" y="7">Embedded</text>
   </g>
  </svg>
  </object>

  **`Flow`：流内容<br>**
  **`Metadata`：元数据<br>**
  **`Sectioning`：分区<br>**
  **`Heading`：标题<br>**
  **`Phrasing`：措辞<br>**
  **`Embedded`：嵌入的<br>**
  **`Interactive`：互动的<br>**

- **按显示**

  - **替换元素 ：浏览器根据元素的标签和属性，来决定元素的具体显示内容**

    **`img`、`input` ...**

  - **非替换元素 : 将内容直接告诉浏览器，将其显示出来**

    **`div`、`h1`、`p` ...**

<br>

## **显示框类型**

​    **display**

- block

- inline

- inline-block

- none

  **`....`**

> **`display:none`    不占空间的隐藏**
>
> **`visibility: hidden` 占空间的隐藏**

<br>

## 标签嵌套规范

- **块标签可以嵌套内联标签**

  **例 ：**

  ```html
  <div>
     <span></span>
     <a href="#"></a>
  </div> 
  ```

- **块标签不一定能嵌套块标签**

  **例 ：**
  
  ```html
   <div>
      <div></div>
   </div>
  特殊： p标签只能嵌套内联样式不能嵌套块
  	错误的写法：
   <p>
      <div></div>
   </p>
  ```
  
- **内联标签不能嵌套块标签**

  **例 ：**

  ```html
  错误的写法：
  <span>
      <div></div>
  </span>
  
  特殊： a标签是一个例外
  正确的写法：
  <a href="#">
      <div></div>
  </a>
  ```

<br>

## **溢出隐藏**

- **`overflow` :**

  |  **属性值**   |                          **说明**                          |
  | :-----------: | :--------------------------------------------------------: |
  | **`visible`** |      **`默认值`。内容不会被修剪，会呈现在元素框之外**      |
  | **`hidden`**  |          **内容会被修剪，并且其余内容是不可见的**          |
  | **`scroll`**  | **内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容** |
  |  **`auto`**   | **如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容** |
  | **`inherit`** |        **规定应该从父元素继承 `overflow` 属性的值**        |

  **x轴、y轴   `overflow-x`、`overflow-y`针对两个轴分别设置**

<br>

## **透明度与手势**

- **opacity**

  **`0(透明) ~ 1(不透明)`**<br>

  **0.5(半透明)**

  >**注：占空间、所有的子内容也会透明**

- **rgba**

  `rgba(255,255,255,0)`**

  **最后一个参数代表透明度 ：`0 ~ 1`**

  > **注：可以让指定的样式透明，而不影响其他样式**

- **cursor  (手势)** 

  **`default` : 默认箭头 (`默认值`）**

  |       值        |                             描述                             |
  | :-------------: | :----------------------------------------------------------: |
  |   ***`url`***   | **`需使用的自定义光标的 URL`<br>注释：请在此列表的末端始终定义一种普通的光标，以防没有由 URL 定义的可用光标** |
  |  **`default`**  |                **默认光标（通常是一个箭头）**                |
  |   **`auto`**    |                  **默认。浏览器设置的光标**                  |
  | **`crosshair`** |                     **光标呈现为十字线**                     |
  |  **`pointer`**  |            **光标呈现为指示链接的指针（一只手）**            |
  |   **`move`**    |                 **此光标指示某对象可被移动**                 |
  | **`e-resize`**  |         **此光标指示矩形框的边缘可被向右（东）移动**         |
  | **`ne-resize`** |    **此光标指示矩形框的边缘可被向上及向右移动（北/东）**     |
  | **`nw-resize`** |    **此光标指示矩形框的边缘可被向上及向左移动（北/西）**     |
  | **`n-resize`**  |         **此光标指示矩形框的边缘可被向上（北）移动**         |
  | **`se-resize`** |    **此光标指示矩形框的边缘可被向下及向右移动（南/东）**     |
  | **`sw-resize`** |    **此光标指示矩形框的边缘可被向下及向左移动（南/西）**     |
  | **`s-resize`**  |         **此光标指示矩形框的边缘可被向下移动（南）**         |
  | **`w-resize`**  |         **此光标指示矩形框的边缘可被向左移动（西）**         |
  |   **`text`**    |                      **此光标指示文本**                      |
  |   **`wait`**    |         **此光标指示程序正忙（通常是一只表或沙漏）**         |
  |   **`help`**    |     **此光标指示可用的帮助（通常是一个问号或一个气球）**     |
  
  要实现自定义手势：
              准备图片： .cur 、 .ico (图片格式)
  
  ```css
  cursor : url(./img/cursor.ico),auto;
  ```

<br>

## **CSS默认样式**

**有些标签有默认样式，有些标签没有默认样式**

- **没有默认样式**

  `div`、`span`、`…`

- **有默认样式**

  | **标签** |                         **默认样式**                         |
  | :------: | :----------------------------------------------------------: |
  | **body** |                       **marign : 8px**                       |
  |  **h1**  |       **margin : 上下 21.440px<br>font-weight : bold**       |
  |  **p**   |                    **margin : 上下 16px**                    |
  |  **ul**  | **margin : 上下 16px <br> padding : 左 40px<br>默认点：list-style : disc** |
  |  **a**   |               **text-decoration: underline;**                |



<br>

## **CSS reset**

### **reset.css**

```css
/**
 * Eric Meyer's Reset CSS v2.0 (http://meyerweb.com/eric/tools/css/reset/)
 * http://cssreset.com
 */
 
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video{
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  font-weight: normal;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section{
  display: block;
}
ol, ul, li{
  list-style: none;
}
blockquote, q{
  quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after{
  content: '';
  content: none;
}
table{
  border-collapse: collapse;
  border-spacing: 0;
}
 
/* custom */
a{
  color: #7e8c8d;
  text-decoration: none;
  -webkit-backface-visibility: hidden;
}
::-webkit-scrollbar{
  width: 5px;
  height: 5px;
}
::-webkit-scrollbar-track-piece{
  background-color: rgba(0, 0, 0, 0.2);
  -webkit-border-radius: 6px;
}
::-webkit-scrollbar-thumb:vertical{
  height: 5px;
  background-color: rgba(125, 125, 125, 0.7);
  -webkit-border-radius: 6px;
}
::-webkit-scrollbar-thumb:horizontal{
  width: 5px;
  background-color: rgba(125, 125, 125, 0.7);
  -webkit-border-radius: 6px;
}
html, body{
  width: 100%;
  font-family: "Arial", "Microsoft YaHei", "黑体", "宋体", "微软雅黑", sans-serif;
}
body{
  line-height: 1;
  -webkit-text-size-adjust: none;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
html{
  overflow-y: scroll;
}
 
/*清除浮动*/
.clearfix:before,
.clearfix:after{
  content: " ";
  display: inline-block;
  height: 0;
  clear: both;
  visibility: hidden;
}
.clearfix{
  *zoom: 1;
}
 
/*隐藏*/
.dn{
  display: none;
}
```

### **腾讯**

```css
body,ol,ul,h1,h2,h3,h4,h5,h6,p,th,td,dl,dd,form,fieldset,legend,input,textarea,select{margin:0;padding:0} 
body{font:12px"宋体","Arial Narrow",HELVETICA;background:#fff;-webkit-text-size-adjust:100%;} 
a{color:#2d374b;text-decoration:none} 
a:hover{color:#cd0200;text-decoration:underline} 
em{font-style:normal} 
li{list-style:none} 
img{border:0;vertical-align:middle} 
table{border-collapse:collapse;border-spacing:0} 
p{word-wrap:break-word} 
```

### **新浪**

```css
body,ul,ol,li,p,h1,h2,h3,h4,h5,h6,form,fieldset,table,td,img,div{margin:0;padding:0;border:0;} 
body{background:#fff;color:#333;font-size:12px; margin-top:5px;font-family:"SimSun","宋体","Arial Narrow";}
ul,ol{list-style-type:none;} 
select,input,img,select{vertical-align:middle;} 
a{text-decoration:none;} 
a:link{color:#009;} 
a:visited{color:#800080;} 
a:hover,a:active,a:focus{color:#c00;text-decoration:underline;} 
```

### **淘宝**

```css
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; } 
body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; } 
h1, h2, h3, h4, h5, h6{ font-size:100%; } 
address, cite, dfn, em, var { font-style:normal; } 
code, kbd, pre, samp { font-family:couriernew, courier, monospace; } 
small{ font-size:12px; } 
ul, ol { list-style:none; } 
a { text-decoration:none; } 
a:hover { text-decoration:underline; } 
sup { vertical-align:text-top; } 
sub{ vertical-align:text-bottom; } 
legend { color:#000; } 
fieldset, img { border:0; }
button, input, select, textarea { font-size:100%; } 
table { border-collapse:collapse; border-spacing:0; } 
```

### **雅虎**

```css
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,code,form,fieldset,legend,input,button,textarea,p,blockquote,th,td { margin:0; padding:0; }
body { background:#fff; color:#555; font-size:14px; font-family: "Arial","Microsoft YaHei","黑体","宋体",sans-serif; }
td,th,caption { font-size:14px; }
h1, h2, h3, h4, h5, h6 { font-weight:normal; font-size:100%; }
address, caption, cite, code, dfn, em, strong, th, var { font-style:normal; font-weight:normal;}
a { color:#555; text-decoration:none; }
a:hover { text-decoration:underline; }
img { border:none; }
ol,ul,li { list-style:none; }
input, textarea, select, button { font:14px "Arial","Microsoft YaHei","黑体","宋体",sans-serif; }
table { border-collapse:collapse; }
html {overflow-y: scroll;} 
 
.clearfix:after {content: "."; display: block; height:0; clear:both; visibility: hidden;} 
.clearfix { *zoom:1; }/*公共类*/
.fl { float:left}
.fr {float:right}
.al {text-align:left}
.ac {text-align:center}
.ar {text-align:right}
.hide {display:none}
```

### **网易**

```css
html {overflow-y:scroll;}
body {margin:0; padding:29px00; font:12px"\5B8B\4F53",sans-serif;background:#ffffff;}
div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,blockquote,p{padding:0; margin:0;}
table,td,tr,th{font-size:12px;}
li{list-style-type:none;}
img{vertical-align:top;border:0;}
ol,ul {list-style:none;}
h1,h2,h3,h4,h5,h6{font-size:12px; font-weight:normal;}
address,cite,code,em,th {font-weight:normal; font-style:normal;}
```

**可参考 ：**[reser.css](https://segmentfault.com/a/1190000009369872)

<br>

## **Float浮动**

### **float特性**

- 加浮动的元素，会脱离文档流，会延迟父容器靠左或靠右排列，如果之前已经有浮动的元素，会挨着浮动的元素进行排列

### **float取值**

- **left ：元素向左浮动**
- **right ：元素向右浮动**
- **none ：`默认值`。元素不浮动，并会显示在其在文本中出现的位置**

### **float注意点**

- **只会影响后面的元素**
- **内容默认提升半层 （可以利用这个特点做图文混排）**
- **加了浮动元素默认宽度根据内容决定**
- **换行排列**
- **主要给块元素添加，但也可以给内联元素添加**

### **如何清除浮动**

- **上下排列 ：`clear`属性（表示清除浮动的）**

  **属性值 ：**

  - left ： 在左侧不允许浮动元素
  - right ： 在右侧不允许浮动元素
  - both ： 在左右两侧均不允许浮动元素
  - none ：`默认值`。允许浮动元素出现在两侧
  - inherit ：规定应该从父元素继承 clear 属性的值

  > **clear属性只会操作块标签，对内联标签不起作用**

- **嵌套排列 ：**

  - **固定父元素宽高 ：不推荐 , 不能把高度固定死，不适合做自适应的效果**
  - **父元素浮动 ：不推荐 , 因为父容器浮动也会影响到后面的元素**
  - **overflow : hidden (BFC规范) , 如果有子元素想溢出，那么会受到影响**
  - **display : inline-block (BFC规范)，不推荐，父容器会影响到后面的元素**
  - **设置空标签 : 不推荐 , 会多添加一个标签**
  - **after伪类 : `推荐`，是空标签的加强版，目前各大公司的做法**

<br>

## **position 定位**

- **position特性**

  **css position属性用于指定一个元素在文档中的定位方式。top、right、bottom、left 属性则决定了该元素的最终位置**

### **position取值**

- **static（`默认`）**
- **relative相对定位**
  - 如果没有定位偏移量，对元素本身没有任何影响
  - 不使元素脱离文档流
  - 不影响其他元素布局
  - **left、top、right、bottom是相对于当前元素自身进行偏移的**
- **absolute绝对定位**
  -  

