
# CSS面试题01

### 1. 介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒模型？

IE盒模型、W3C 盒模型；（也叫怪异盒模型和标准盒模型）

盒模型： 内容(content)、内边距(padding)、外边距(margin)、 边框(border)；

区别： IE 的 content 部分把 border 和 padding 也计算进去了;

### 2. CSS 隐藏元素的几种方法（至少说出三种）

- opacity: 元素本身依然占据它自己的位置并对网页的布局起作用，它也将响应用户交互;
- visibility: 与 opacity 唯一不同的是它不会响应任何用户交互，此外，元素在读屏软件中也会被隐藏;
- display: display 设为 none 任何对该元素直接交互操作都不可能生效，此外，读屏软件也不会读到元素的内容，这种方式产生的效果就像元素完全不存在;

- position: 不会影响布局，能让元素保持可以操作;
- clip-path: clip-path 属性还没有在 IE 或者 Edge 下被完全支持。如果要在你的 clip-path 中使用外部的 SVG 文件，浏览器支持度还要低;

### 3. CSS 清除浮动的几种方法（至少两种）

核心：`clear:both;`

- **使用额外标签法（不推荐使用）**

  在浮动的盒子下面再放一个标签，使用 clear:both;来清除浮动

      1. 内部标签：会将父盒子的高度重新撑开
    
      2. 外部标签：只能将浮动盒子的影响清除，但是不会撑开盒子

- **使用 overflow 清除浮动（不推荐使用）**

  先找到浮动盒子的父元素，给父元素添加一个属性：overflow:hidden;就会清除子元素对页面的影响

- **使用伪元素清除浮动(用的最多)**

	伪元素：在页面上不存在的元素，但是可以通过 css 添加上去

	种类：
      	:after(在。。。之后)
      	:before(在。。。之前)

	注意：**每个元素都有自己的伪元素**
	
```css
.clearfix:after {
    content:"";
    height:0;
    line-height:0;
    display:block;
    clear:both;
    visibility:hidden;  /*将元素隐藏起来
      在页面的 clearfix 元素后面添加了一个空的块级元素
     （这个元素的高为 0 行高也为 0   并且这个元素清除了浮动）*/ 
}
.clearfix {
  zoom:1;/*_为了兼容 IE6_*/
}
```

### 4. 页面导入样式时，使用 link 和@import 有什么区别?

link 属于 html 标签，而@import 是 CSS 中提供的

在页面加载的时候，link 会同时被加载，而@import 引用的 CSS 会在页面加载完成后才会加载引用的 CSS

@import 只有在 ie5 以上才可以被识别，而 link 是 html 标签，不存在浏览器兼容性问题

Link 引入样式的权重大于@import 的引用（@import 是将引用的样式导入到当前的页面中）


### 5. 伪元素和伪类的区别是什么？

- 伪元素使用 2 个冒号，常见的有 ::before，::after，::first-line，::first-letter，::selection、::placeholder 等；

- 伪类使用1个冒号，常见的有：:hover，:link，:active，:target，:not()，:focus等。

- 伪元素添加了一个页面中没有的元素（只是从视觉效果上添加了，不是在文档树中添加）；

- 伪类是给页面中已经存在的元素添加一个类。

### 6. CSS 选择器有哪些？哪些属性可以继承？优先级如何计算？

1. id选择器（ # myid）
2. 类选择器（.myclassname）
3. 标签选择器（div, h1, p）
4. 相邻选择器（h1 + p）
5. 子选择器（ul < li）
6. 后代选择器（li a）
7. 通配符选择器（ * ）
8. 属性选择器（a[rel = "external"]）
9. 伪类选择器（a: hover, li: nth - child）

*   可继承： font-size font-family color;
*   不可继承 ：border padding margin width height ;
*   优先级就近原则，样式定义最近者为准;
*   载入样式以最后载入的为准;

优先级为:

!important >  id > class > tag  
!important 比 内联优先级高



### 7. CSS3新增伪类举例

- p:first-of-type 选择属于其父元素的首个<p\> 元素的每个 <p\> 元素。
- p:last-of-type  选择属于其父元素的最后 <p\> 元素的每个 <p\> 元素。
- p:only-of-type  选择属于其父元素唯一的 <p\> 元素的每个 <p\> 元素。
- p:only-child  选择属于其父元素的唯一子元素的每个 <p\> 元素。
- p:nth-child(2)  选择属于其父元素的第二个子元素的每个 <p\> 元素。
- :enabled、:disabled 控制表单控件的禁用状态。
- :checked，单选框或复选框被选中。


### 8. 行内元素和块级元素的具体区别是什么?

**块级元素(block)特性**：

- 总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示;
- 宽度(width)、高度(height)、内边距(padding)和外边距(margin)都可控制;

**内联元素(inline)特性**：

- 和相邻的内联元素在同一行;
- 宽度(width)、高度(height)、内边距的 top/bottom(padding-top/padding-bottom)和外边距的 top/bottom(margin-top/margin-bottom)都不可改变（也就是 padding 和 margin 的 left 和 right 是可以设置的），就是里面文字或图片的大小。


### 9. 什么是外边距重叠？重叠的结果是什么？

**外边距重叠就是 margin-collapse**

在 CSS 当中，相邻的两个盒子（可能是兄弟关系也可能是祖先关系）的外边距可以结合成一个单独的外边距。这种合并外边距的方式被称为折叠，并且因而所结合成的外边距称为折叠外边距。

折叠结果遵循下列计算规则：

两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。
两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。
两个外边距一正一负时，折叠结果是两者的相加的和


### 10. rgba()和 opacity 的透明效果有什么不同？

rgba()和 opacity 都能实现透明效果，但最大的不同是 **opacity 作用于元素，以及元素内的所有内容的透明度**，而 rgba()只作用于**元素的颜色或其背景色**。（设置 rgba 透明的元素的子元素不会继承透明效果！）

