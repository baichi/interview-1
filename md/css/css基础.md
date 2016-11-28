## 1. display:none和visibility:hidden的区别？
`display:none`  隐藏对应的元素，在文档布局中不再给它分配空间，它各边的元素会合拢，
就当他从来不存在。

`visibility:hidden`  隐藏对应的元素，但是在文档布局中仍保留原来的空间。

## 2. CSS中 link 和@import 的区别是？
1. link属于HTML标签，而@import是CSS提供的;
2. 页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
3. import只在IE5以上才能识别，而link是HTML标签，无兼容问题;
4. link方式的样式的权重 高于@import的权重.

## 3. position的absolute与fixed共同点与不同点
A：共同点：
1.改变行内元素的呈现方式，display被置为block；2.让元素脱离普通流，不占据空间；3.默认会覆盖到非定位元素上

B不同点：
absolute的”根元素“是可以设置的，而fixed的”根元素“固定为浏览器窗口。当你滚动网页，fixed元素与浏览器窗口之间的距离是不变的。

## 4. 介绍一下CSS的盒子模型？
1. 有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 padding;
2. 盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).

## 5. CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？
```
*   1.id选择器（ # myid）
        2.类选择器（.myclassname）
        3.标签选择器（div, h1, p）
        4.相邻选择器（h1 + p）
        5.子选择器（ul > li）
        6.后代选择器（li a）
        7.通配符选择器（ * ）
        8.属性选择器（a[rel = "external"]）
        9.伪类选择器（a: hover, li:nthchild）

    *   可继承的样式： fontsize fontfamily color, textindent;

    *   不可继承的样式：border padding margin width height ;

    *   优先级就近原则，同权重情况下样式定义最近者为准;

    *   载入样式以最后载入的定位为准;

优先级为:


   !important >  id > class > tag

   important 比 内联优先级高,但内联比 id 要高

CSS3新增伪类举例：


p:firstoftype 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
p:lastoftype  选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
p:onlyoftype  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
p:onlychild    选择属于其父元素的唯一子元素的每个 <p> 元素。
p:nthchild(2)  选择属于其父元素的第二个子元素的每个 <p> 元素。
:enabled  :disabled 控制表单控件的禁用状态。
:checked        单选框或复选框被选中。
```

## 6. 列出display的值，说明他们的作用。position的值， relative和absolute分别是相对于谁进行定位的？
```
1.
  block 象块类型元素一样显示。
  inline 缺省值。象行内元素类型一样显示。
  inlineblock 象行内元素一样显示，但其内容象块类型元素一样显示。
  listitem 象块类型元素一样显示，并添加样式列表标记。

  2.
  *absolute
        生成绝对定位的元素，相对于 static 定位以外的第一个祖先元素进行定位。

  *fixed （老IE不支持）
        生成绝对定位的元素，相对于浏览器窗口进行定位。

  *relative
        生成相对定位的元素，相对于其在普通流中的位置进行定位。

  * static  默认值。没有定位，元素出现在正常的流中
  *（忽略 top, bottom, left, right zindex 声明）。

  * inherit 规定从父元素继承 position 属性的值。
```

### 7.CSS3有哪些新特性？ 
```
CSS3实现圆角（borderradius），阴影（boxshadow），
对文字加特效（textshadow、），线性渐变（gradient），旋转（transform）
transform:rotate(9deg) scale(0.85,0.90) translate(0px,30px) skew(9deg,0deg);//旋转,缩放,定位,倾斜
增加了更多的CSS选择器  多背景 rgba
在CSS3中唯一引入的伪元素是::selection.
媒体查询，多栏布局
borderimage
```

### 8. 为什么要初始化CSS样式
```
因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。

    当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。

* 最简单的初始化方法就是： * {padding: 0; margin: 0;} （不建议）

    淘宝的样式初始化：
    body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; }
    body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; }
    h1, h2, h3, h4, h5, h6{ fontsize:100%; }
    address, cite, dfn, em, var { fontstyle:normal; }
    code, kbd, pre, samp { fontfamily:couriernew, courier, monospace; }
    small{ fontsize:12px; }
    ul, ol { liststyle:none; }
    a { textdecoration:none; }
    a:hover { textdecoration:underline; }
    sup { verticalalign:texttop; }
    sub{ verticalalign:textbottom; }
    legend { color:#000; }
    fieldset, img { border:0; }
    button, input, select, textarea { fontsize:100%; }
    table { bordercollapse:collapse; borderspacing:0; }
```

### 9.对BFC规范的理解？
```
  BFC，块级格式化上下文，一个创建了新的BFC的盒子是独立布局的，盒子里面的子元素的样式不会影响到外面的元素。在同一个BFC中的两个毗邻的块级盒在垂直方向（和布局方向有关系）的margin会发生折叠。
    （W3C CSS 2.1 规范中的一个概念，它决定了元素如何对其内容进行布局，以及与其他元素的关系和相互作用。）
```

### 10.解释下 CSS sprites，以及你要如何在页面或网站中使用它
```
CSS Sprites其实就是把网页中一些背景图片整合到一张图片文件中，再利用CSS的“backgroundimage”，“background repeat”，“backgroundposition”的组合进行背景定位，backgroundposition可以用数字能精确的定位出背景图片的位置。这样可以减少很多图片请求的开销，因为请求耗时比较长；请求虽然可以并发，但是也有限制，一般浏览器都是6个。对于未来而言，就不需要这样做了，因为有了`http2`。
```