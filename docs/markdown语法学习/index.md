# Markdown语法学习




## 标题

​	`Ctrl + 1~5`



## 文档导航	

​	`[toc]`



## 代码

短代码：`code`

长代码：``` + java (什么语言后面加什么)

```java
1 	public class HelloWorld {
2  		public static void main(String[] args){
3			System.out.println("HelloWorld");
4   	} 
5 	}
```



## 引用

`>`式

> 度尽劫波

`（```式）`  代码之内的

```
print('hello nick')
```



## 图片 

`![](url)`

这是取的七牛云里的图片

![](http://q34mxvxhj.bkt.clouddn.com/61678dc173fb6af917ae9df08302b5f3.jpg)



## 链接

`[超链接名]（超链接地址）`

[百度](http://www.baidu.com)

`<超链接地址>`(这种方式以链接地址本身显示)

<https://www.cnblogs.com/nickchen121/p/10718112.html>



## 列表

`- + *` 都可以（跟内容之间有空格）

 - 列表1
 - 列表2
 - 列表3

`1.`（也可以）

1. 列表1
2. 列表2
3. 列表2



## 加粗

`** 要加粗的文本 **`
  **我被加粗了**



  ## 斜体

  `* 要倾斜的文本 *`
   *我被倾斜了*



## 分割线
​	`---`
效果：

---



##  表格
​	第二行必须得有，并且第二行的冒号代表对齐格式，分别为居中；右对齐；左对齐）：

代码：

```
name | age | sex 
:-:|:-|-: 
tony|20|男 
lucy|18|女
```

效果：

| name | age  | sex  |
| :--: | :--: | :--: |
| tony |  20  |  男  |
| lucy |  18  |  女  |



## 数学公式（块状）

代码：

```
$$
\sum_{i=1}^{10}f(i)\,\,\text{thanks}
$$
```
效果：
$$
\sum_{i=1}^{10}f(i)\,\,\text{thanks}
$$
