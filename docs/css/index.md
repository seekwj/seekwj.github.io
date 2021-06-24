# CSS



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



## **CSS样式的引入方式**

1. **内联样式**

   ​	**`style`属性**

2. **内部样式**

   ​	**`style`标签**<br>

   &nbsp;&nbsp;​	**区别：**
   ​        **内部样式的代码可以复用、复合W3C的规范标准，进行让结构和样式分开处理**

3. **外部样式**

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



## **CSS中的颜色表示法**

1. **单词表示法 ：`red` `blue` `green` `yellow`**

   ![颜色名称](https://static01.imgkr.com/temp/8d9487f36a26402c98366645b73b0d8c.jpg)

2. **十六进制表示法 ：`#000000` `#ffffff`**

   0 1 2 3 4 5 6 7 8 9 a b c d e f

3. `RGB`**表示法 ：`rgb(255,255,255)`**

   取值范围 0 ~ 255

   **获取颜色的工具：**
           [**https://www.baidufe.com/fehelper**](https://www.baidufe.com/fehelper)



## **CSS背景样式**

**` background-color` 背景色**

**`background-image` 背景图**

- `url`(背景地址)		

  `默认：会水平垂直都铺满背景图`	

**`background-repeat` 平铺方式**

- `repeat-x`   x轴平铺
- `repeat-y`   y轴平铺
- `repeat` ( x , y 都进行平铺，`默认值` )
- `no-repeat`  都不平铺

**`background-position` : 背景位置**

-  **`x` `y` : number(`px`、`%`) | 单词**

&#12288;&#12288;&#12288;&#12288;`x` : `left`、`center`、`right`

&#12288;&#12288;&#12288;&#12288;`y` : `top`、`center`、`bottom`

**`background-attachment` : 背景图随滚动条移动的方式**

- `scroll` : `默认值`  ( 背景位置是按照当前元素进行偏移的 )

- `fixed` ： ( 背景位置是按照浏览器进行偏移的 )

  **练习 ：[利用滚动条移动方式实现视觉差网页](../demo/视觉差/视觉差.html)**



## **CSS边框样式**

 **`border-style` : 边框样式**

- `solid` : 实线
- `dashed` : 虚线
- `dotted` : 点线

**`border-width` : 边框大小**

- number(`px`、`%`) 

**`border-color` : 边框颜色**

- `red` `#f00` ...     

边框也可以针对某一边进行单独设置 : `border-left-style` : 中间是方向 `left`、`right`、`top`、`bottom`   

颜色：透明颜色 `transparent`



## **CSS文字样式**

**`font-family` : 字体类型**

- 英文字体：例如 ：`Arial` , '`Times New Roman`' 

- 中文字体：例如 ：`微软雅黑` ,  `宋体`

  中文字体都有英文名称

- `衬线体`、`非衬线体`<br>
  `衬线字体`（宋体）：见名知意，就是`比划有粗有细，非衬线字体所以字的所有比划的都是一样粗细（幼圆）`

  &#12288;**区别 ：**

  - *`衬线字体每个字的笔划有粗有细`*，在连续阅读时流畅性更好
  - *`无衬线字体笔划粗细均匀`*，适用于单词短句

   > 注意 ：如果字体名称出现空格要用引号，如：'`Times New Roman`'

**`font-size` : 字体大小**

- 默认 ：**`16px`**

- 写法 ：

  1. number(`px`)
  
  2. 单词 ( `small` `large` ... )**不推荐使用**
  
     |  **属性取值**  |    **字体大小**    |
     | :------------: | :----------------: |
     | **`xx-small`** |      **最小**      |
     | **`x-small`**  |      **较小**      |
     |  **`small`**   |       **小**       |
     |  **`medium`**  | **正常（默认值）** |
     |  **`large`**   |       **大**       |
     | **`x-large`**  |      **较大**      |
     | **`xx-large`** |      **最大**      |
  
  > 注 ：字体大小一般为偶数

font-weight : 字体粗细


