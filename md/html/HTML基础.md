### 1. DOM回流和DOM重绘

### 2. 说说你对语义化的理解？
```
1，去掉或者丢失样式的时候能够让页面呈现出清晰的结构
2，有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重；
3，方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页；
4，便于团队开发和维护，语义化更具可读性，是下一步吧网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化。
```

### 3. Doctype作用? 严格模式与混杂模式如何区分？它们有何意义?
1. <!DOCTYPE> 声明位于文档中的最前面，处于 <html> 标签之前。告知浏览器以何种模式来渲染文档。
2. 严格模式的排版和 JS 运作模式是  以该浏览器支持的最高标准运行。
3. 在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。
4. DOCTYPE不存在或格式不正确会导致文档以混杂模式呈现。

### 4. 你知道多少种Doctype文档类型？ 
 该标签可声明三种 DTD 类型，分别表示严格版本、过渡版本以及基于框架的 HTML 文档。
 HTML 4.01 规定了三种文档类型：Strict、Transitional 以及 Frameset。
 XHTML 1.0 规定了三种 XML 文档类型：Strict、Transitional 以及 Frameset。
Standards （标准）模式（也就是严格呈现模式）用于呈现遵循最新标准的网页，而 Quirks
 （包容）模式（也就是松散呈现模式或者兼容模式）用于呈现为传统浏览器而设计的网页。
 
### 5. HTML与XHTML——二者有什么区别?
1. 所有的标记都必须要有一个相应的结束标记
2. 所有标签的元素和属性的名字都必须使用小写
3. 所有的XML标记都必须合理嵌套
4. 所有的属性必须用引号""括起来
5. 把所有<和&特殊符号用编码表示
6. 给所有属性赋一个值
7. 不要在注释内容中使“”
8. 图片必须有说明文字


### 6. 常见兼容性问题
* png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.也可以引用一段脚本处理.

* 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。

* IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。

* 浮动ie产生的双倍距离（IE6双边距问题：在IE6下，如果对元素设置了浮动，同时又设置了marginleft或marginright，margin值会加倍。）
  #box{ float:left; width:10px; margin:0 0 0 100px;}

 这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)

*  渐进识别的方式，从总体中逐渐排除局部。

  首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。
  接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。

  css
      .bb{
       backgroundcolor:#f1ee18;/*所有识别*/
      .backgroundcolor:#00deff\9; /*IE6、7、8识别*/
      +backgroundcolor:#a200ff;/*IE6、7识别*/
      _backgroundcolor:#1e0bd1;/*IE6识别*/
      }

*  IE下,可以使用获取常规属性的方法来获取自定义属性,
   也可以使用getAttribute()获取自定义属性;
   Firefox下,只能使用getAttribute()获取自定义属性.
   解决方法:统一通过getAttribute()获取自定义属性.

* IE下,event对象有x,y属性,但是没有pageX,pageY属性;
  Firefox下,event对象有pageX,pageY属性,但是没有x,y属性.

* 解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

* Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,
  可通过加入 CSS 属性 webkittextsizeadjust: none; 解决.

* 超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:
LVHA :  a:link {} a:visited {} a:hover {} a:active {}

* 怪异模式问题：漏写DTD声明，Firefox仍然会按照标准模式来解析网页，但在IE中会触发怪异模式。为避免怪异模式给我们带来不必要的麻烦，最好养成书写DTD声明的好习惯。现在可以使用[html5](http://www.w3.org/TR/html5/singlepage.html)推荐的写法：`<doctype html>`

* 上下margin重合问题
ie和ff都存在，相邻的两个div的marginleft和marginright不会重合，但是margintop和marginbottom却会发生重合。
解决方法，养成良好的代码编写习惯，同时采用margintop或者同时采用marginbottom。
* ie6对png图片格式支持不好(引用一段脚本处理)

### 7. 解释下浮动和它的工作原理？清除浮动的技巧
浮动元素脱离文档流，不占据空间。浮动元素碰到包含它的边框或者浮动元素的边框停留。

1. 使用空标签清除浮动。
   这种方法是在所有浮动标签后面添加一个空标签 定义css clear:both. 弊端就是增加了无意义标签。
2. 使用overflow。
   给包含浮动元素的父标签添加css属性 overflow:auto; zoom:1; zoom:1用于兼容IE6。
3. 使用after伪对象清除浮动。
   该方法只适用于非IE浏览器。具体写法可参照以下示例。使用中需注意以下几点。一、该方法中必须为需要清除浮动元素的伪对象中设置 height:0，否则该元素会比实际高出若干像素；

### 8. 浮动元素引起的问题和解决办法？
浮动元素引起的问题：
（1）父元素的高度无法被撑开，影响与父元素同级的元素
（2）与浮动元素同级的非浮动元素会跟随其后
（3）若非第一个元素浮动，则该元素之前的元素也需要浮动，否则会影响页面显示的结构
解决方法： 使用CSS中的clear:both;属性来清除元素的浮动可解决2、3问题，对于问题1，添加如下样式，给父元素添加clearfix样式：

.clearfix:after{content: ".";display: block;height: 0;clear: both;visibility: hidden;}
.clearfix{display: inlineblock;} /* for IE/Mac */

### 9.  清除浮动的几种方法
1，额外标签法，<div style="clear:both;"></div>（缺点：不过这个办法会增加额外的标签使HTML结构看起来不够简洁。）
2，使用after伪类

#parent:after{
    content:".";
    height:0;
    visibility:hidden;
    display:block;
    clear:both;
    }

3,浮动外部元素
4,设置`overflow`为`hidden`或者auto

### 10. IE 8以下版本的浏览器中的盒模型有什么不同
IE8以下浏览器的盒模型中定义的元素的宽高不包括内边距和边框

### 11. DOM操作——怎样添加、移除、移动、复制、创建和查找节点?
1. 创建新节点
      createDocumentFragment()    //创建一个DOM片段
      createElement()   //创建一个具体的元素
      createTextNode()   //创建一个文本节点
2. 添加、移除、替换、插入
      appendChild()
      removeChild()
      replaceChild()
      insertBefore() //在已有的子节点前插入一个新的子节点
3. 查找
      getElementsByTagName()    //通过标签名称
      getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的)
      getElementById()    //通过元素Id，唯一性
      
      