---
title: "CSS"
date: 2020-11-07T15:58:26+08:00
lastmod: 2021-06-22T15:23:26+08:00

description: "CSS"
summary: "		CSS基础"
images: []

tags: [CSS]
categories: [CSS]
featuredImage: "/md/CSS.jpg"
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

  ​	 **`width` : 宽**
   	**`height` : 高**
   	**`background-color` : 背景色**

- **CSS注释 ：**

  ```css
  /*CSS注释的内容*/
  ```



## **CSS样式的引入方式**

1. **内联样式**

   ​	**`style`属性**

2. **内部样式**

   ​	**`style`标签**<br>

   ​	**区别：**
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



