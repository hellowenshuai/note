# jQuery API 中文文档

### 01. 简介

jQuery 是一个**高效、精简**并且功能丰富的 JavaScript 工具库。它提供的 API 易于使用且**兼容**众多浏览器，这让诸如 HTML **文档遍历和操作**、**事件处理**、动画和 **Ajax 操作**更加简单。

#### note

1.jQuery 版本 2 以上不支持 IE6，7，8 浏览器。

如果需要支持 IE6/7/8，那么请选择1.9

你还可以通过条件注释在使用 IE6/7/8 时只包含进1.9。

```js
<!--[if lt IE 9]>
    <script src="jquery-1.9.0.js"></script>
<![endif]-->
<!--[if gte IE 9]><!-->
    <script src="jquery-2.0.0.js"></script>
<!--<![endif]-->
```

2.jQuery 的功能概括

1、html 的元素选取

2、html的元素操作

3、html dom遍历和修改

4、js特效和动画效果

5、css操作

6、html事件操作

7、ajax异步请求方式

3.目前jQuery有三个大版本：

**1.x**：兼容ie678,使用最为广泛的，官方只做BUG维护，功能不再新增。因此一般项目来说，使用1.x版本就可以了，最终版本：1.12.4 (2016年5月20日)

**2.x**：不兼容ie678，**很少有人使用**，官方只做BUG维护，功能不再新增。如果不考虑兼容低版本的浏览器可以使用2.x，最终版本：2.2.4 (2016年5月20日)

**3.x**：不兼容ie678，只支持最新的浏览器。除非特殊要求，一般不会使用3.x版本的，很多老的jQuery插件不支持这个版本。目前该版本是官方主要更新维护的版本。最新版本：3.3.1（2018年1月20日）

### 02. 安装

#### 下载 jQuery

有两个版本的 jQuery 可供下载：

- Production version - 用于实际的网站中，已被精简和压缩。

- Development version - 用于测试和开发（未压缩，是可读的代码

  以上两个版本都可以从 [jquery.com](http://jquery.com/download/) 中下载。

jQuery 库是一个 JavaScript 文件，您可以使用 HTML 的 <script> 标签引用它：

<head> <script src="jquery-1.10.2.min.js"></script> </head>

**提示** 将下载的文件放在网页的同一目录下，就可以使用jQuery。

  **您是否很疑惑为什么我们没有在 <script> 标签中使用 type="text/javascript" ？**

在 HTML5 中，不必那样做了。JavaScript 是 HTML5 以及所有现代浏览器中的默认脚本语言！  

#### 替代方案

如果您不希望下载并存放 jQuery，那么也可以通过 CDN（内容分发网络） 引用它。

如果你的站点用户是国内的，建议使用百度、又拍云、新浪等国内CDN地址，如果你站点用户是国外的可以使用谷歌和微软。

  **使用 Staticfile CDN、百度、又拍云、新浪、谷歌或微软的 jQuery，有一个很大的优势：**

许多用户在访问其他站点时，已经从百度、又拍云、新浪、谷歌或微软加载过 jQuery。所以结果是，当他们访问您的站点时，会从缓存中加载 jQuery，这样可以减少加载时间。同时，大多数 CDN 都可以确保当用户向其请求文件时，会从离用户最近的服务器上返回响应，这样也可以提高加载速度。  

### 03. jQuery 语法

通过 jQuery，您可以选取（查询，query） HTML 元素，并对它们执行"操作"（actions）。

#### jQuery 语法

jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。

基础语法： **$(selector).action()**

​	1.**$**美元符号定义JQuery

​	2.选择符**selector** 查询和查找HTML元素   

​	3.action执行对元素的操作

实例:

- $(this).hide() - 隐藏当前元素

- $("p").hide() - 隐藏所有 <p> 元素

- $("p.test").hide() - 隐藏所有 class="test" 的 <p> 元素

- $("#test").hide() - 隐藏所有 id="test" 的元素

  

#### ​ **你对 CSS 选择器熟悉吗？**

jQuery 使用的语法是 XPath 与 CSS 选择器语法的组合。在本教程接下来的章节，您将学习到更多有关选择器的语法。  

您也许已经注意到在我们的实例中的所有 jQuery 函数位于一个 **document ready** 函数中：

```js
$(document).ready(function(){
// 开始写 jQuery 代码...
});
```

这是为了防止**文档在完全加载（**就绪）之前运行 jQuery 代码，即在 DOM 加载完成后才可以对 DOM 进行操作。

如果在文档没有完全加载之前就运行函数，操作可能失败。下面是两个具体的例子：

> ​	试图隐藏一个不存在的元素
>
> ​	获得未完全加载的图像的大小

**提示：**简洁写法（与以上写法效果相同）:

```js
$(function(){
// 开始写 jQuery 代码...
});
```

#### note

jQuery 入口函数:

```js
$(document).ready(function(){
    // 执行代码
});
或者
$(function(){
    // 执行代码
});
```

JavaScript 入口函数:

```js
window.onload = function () {
    // 执行代码
}
```

jQuery 入口函数与 JavaScript 入口函数的区别：

-  jQuery 的入口函数是在 html 所有标签(DOM)都加载之后，就会去执行。
-  JavaScript 的 window.onload 事件是等到所有内容，包括外部图片之类的文件加载完后，才会执行。

### 04 jQuery 选择器

jQuery 选择器允许您对 HTML **元素组**或**单个元素**进行操作。

jQuery 选择器基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。 它基于已经存在的 [CSS 选择器](http://www.runoob.com/cssref/css-selectors.html)，除此之外，它还有一些**自定义**的选择器。

jQuery 中所有选择器都以美元符号开头：$()。

#### 元素选择器

jQuery 元素选择器基于元素名选取元素。

在页面中选取所有 <p> 元素:

$("p")

用户点击按钮后，所有 <p> 元素都隐藏：

```javascript
$(document).ready(function() {
        $("button").click(function() {
                $("p").hide();
            });
    });
```

#### #id 选择器

jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。

页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。

通过 id 选取元素语法如下：

**$("#test")**

当用户点击按钮后，有 id="test" 属性的元素将被隐藏：

实例

```javascript
$(document).ready(function(){   
    $("button").click(function(){     
        $("#test").hide();   
    }); 
});
```

#### .class 选择器

jQuery 类选择器可以通过指定的 class 查找元素。

语法如下：

$(".test")

**实例**

用户点击按钮后所有带有 class="test" 属性的元素都隐藏：

```javascript
$(document).ready(function(){   
    $("button").click(function(){     
        $(".test").hide();   
    }); 
});
```

[更多选择器方式：](http://www.runoob.com/jquery/jquery-selectors.html)

#### 独立文件中使用 jQuery 函数

如果您的网站包含许多页面，并且您希望您的 jQuery 函数易于维护，那么请把您的 jQuery 函数放到独立的 .js 文件中。

当我们在教程中演示 jQuery 时，会将函数直接添加到 <head> 部分中。不过，把它们放到一个单独的文件中会更好，就像这样（通过 src 属性来引用文件）：

<head>
<script src="http://cdn.static.runoob.com/libs/jquery/1.10.2/jquery.min.js">
</script>
<script src="my_jquery_functions.js"></script>
</head>

#### note

1. 通过 $(":button") 可以选取所有 type="button" 的 <input> 元素 和 <button> 元素，如果去掉冒号，$("button")只能获取 <button> 元素。

```js
<p id="test1">点进这里测试  <b>button</b></p>
<p id="test2">点进这里测试 <b>:button</b></p>
<button>Button 按钮</button>
<input type="button" value="Input 按钮">
```

2. 关于 **:** 和 **[]** 这两个符号的理解

**：**可以理解为种类的意思，如：**p:first**，**p** 的种类为第一个。

**[]** 很自然的可以理解为属性的意思，如：**[href]** 选取带有 **href** 属性的元素。

3. **$(":button")** 为 jQuery 中表单选择器（貌似与过滤选择器同级），旨在选择所有的按钮，所以会找到 **<input>**、**<button>** 元素；而 **$("button")** 则为基本选择器，旨在选择为 **<button>** 的标签。

**:** 即为 jQuery 的过滤选择器，语法类似于 css 中的伪类选择器；其过滤选择器大概可以分为基本过滤（p:first 之类）、内容过滤（:empty）、子元素过滤(:first-child)和属性过滤 **[href]** 选择器。

4. 各种复制选择器

```js
$("#id", ".class")  复合选择器
$(div p span)       层级选择器 //div下的p元素中的span元素
$(div>p)            父子选择器 //div下的所有p元素
$(div+p)            相邻元素选择器 //div后面的p元素(仅一个p)
$(div~p)            兄弟选择器  //div后面的所有p元素(同级别)
$(.p:last)          类选择器 加 过滤选择器  第一个和最后一个（first 或者 last）
$("#mytable td:odd")      层级选择 加 过滤选择器 奇偶（odd 或者 even）
$("div p:eq(2)")    索引选择器 div下的第三个p元素（索引是从0开始）
$("a[href='www.baidu.com']")  属性选择器
$("p:contains(test)")        // 内容过滤选择器，包含text内容的p元素
$(":emtyp")        //内容过滤选择器，所有空标签（不包含子标签和内容的标签）parent 相反
$(":hidden")       //所有隐藏元素 visible 
$("input:enabled") //选取所有启用的表单元素
$(":disabled")     //所有不可用的元素
$("input:checked") //获取所有选中的复选框单选按钮等
$("select option:selected") //获取选中的选项元素
```

### 05 jQuery 事件

jQuery 是为事件处理特别设计的。

#### 什么是事件？

页面对不同访问者的响应叫做事件。

事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。

实例：

- 在元素上移动鼠标。

- 选取单选按钮

- 点击元素

  在事件中经常使用术语"触发"（或"激发"）例如： "当您按下按键时触发 keypress 事件"。

常见 DOM 事件：

| 鼠标事件                                                     | 键盘事件                                                     | 表单事件                                                 | 文档/窗口事件                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------------------------------- | -------------------------------------------------------- |
| [click](http://www.runoob.com/jquery/event-click.html)       | [keypress](http://www.runoob.com/jquery/event-keypress.html) | [submit](http://www.runoob.com/jquery/event-submit.html) | [load](http://www.runoob.com/jquery/event-load.html)     |
| [dblclick](http://www.runoob.com/jquery/event-dblclick.html) | [keydown](http://www.runoob.com/jquery/event-keydown.html)   | [change](http://www.runoob.com/jquery/event-change.html) | [resize](http://www.runoob.com/jquery/event-resize.html) |
| [mouseenter](http://www.runoob.com/jquery/event-mouseenter.html) | [keyup](http://www.runoob.com/jquery/event-keyup.html)       | [focus](http://www.runoob.com/jquery/event-focus.html)   | [scroll](http://www.runoob.com/jquery/event-scroll.html) |
| [mouseleave](http://www.runoob.com/jquery/event-mouseleave.html) | [hover](http://www.runoob.com/jquery/event-hover.html)       | [blur](http://www.runoob.com/jquery/event-blur.html)     | [unload](http://www.runoob.com/jquery/event-unload.html) |

#### jQuery 事件方法语法

在 jQuery 中，大多数 DOM 事件都有一个等效的 jQuery 方法。

页面中指定一个点击事件：

$("p").click();

下一步是定义什么**时间触发事件**。您可以通过一个**事件函数**实现：

```js
$("p").click(function(){
// 动作触发后执行的代码!!
});
```

#### 常用的 jQuery 事件方法

1. **$(document).ready()**

$(document).ready() 方法允许我们在文档完全加载完后执行函数。该事件方法在 [jQuery 语法](http://www.runoob.com/jquery/jquery-syntax.html) 章节中已经提到过。

2. **click**()

click() 方法是当按钮点击事件被触发时会调用一个函数。

该函数在用户点击 HTML 元素时执行。

在下面的实例中，当点击事件在某个 <p> 元素上触发时，隐藏当前的 <p> 元素：

实例

```js
$("p").click(function(){   $(this).hide(); });  
```

3. **dblclick**()

当双击元素时，会发生 dblclick 事件。

dblclick() 方法触发 dblclick 事件，或规定当发生 dblclick 事件时运行的函数：

实例

```js
$("p").dblclick(function(){   $(this).hide(); });
```

4.1 **mouseenter**（鼠标指向）

当鼠标指针穿过元素时，会发生 mouseenter 事件。

mouseenter() 方法触发 mouseenter 事件，或规定当发生 mouseenter 事件时运行的函数：

实例

```js
$("#p1").mouseenter(function(){     
    alert('您的鼠标移到了 id="p1" 的元素上!'); 
});
```

4.2 **mouseleave**()（鼠标离开）

当鼠标指针离开元素时，会发生 mouseleave 事件。

mouseleave() 方法触发 mouseleave 事件，或规定当发生 mouseleave 事件时运行的函数：

实例

```js
$("#p1").mouseleave(function(){     alert("再见，您的鼠标离开了该段落。"); });
```

4.3 **mousedown**()（鼠标点击）

当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 mousedown 事件。

mousedown() 方法触发 mousedown 事件，或规定当发生 mousedown 事件时运行的函数：

```js
$("#p1").mousedown(function(){     alert("鼠标在该段落上按下！"); });
```

4.4 **mouseup**()(鼠标松开)

当在元素上松开鼠标按钮时，会发生 mouseup 事件。

mouseup() 方法触发 mouseup 事件，或规定当发生 mouseup 事件时运行的函数：

```js
$("#p1").mouseup(function(){     alert("鼠标在段落上松开。"); });
```

4.5 **hover**()（光标悬停）

hover()方法用于模拟光标悬停事件。

当鼠标移动到元素上时，会触发指定的第一个函数(mouseenter);当鼠标移出这个元素时，会触发指定的第二个函数(mouseleave)。

```js
$("#p1").hover(     
    function(){         
        alert("你进入了 p1!");     
    },     
    function(){         
        alert("拜拜! 现在你离开了 p1!");     
    }
);
```

5. 1 **focus**()  (获得焦点)

当元素获得焦点时，发生 focus 事件。

当通过**鼠标点击选中**元素或通过 **tab 键**定位到元素时，该元素就会获得焦点。

focus() 方法触发 focus 事件，或规定当发生 focus 事件时运行的函数：

```js
$("input").focus(function(){   
    $(this).css("background-color","#cccccc"); 
}); 
```

 5.2   **blur**()失去焦点

当元素失去焦点时，发生 blur 事件。

blur() 方法触发 blur 事件，或规定当发生 blur 事件时运行的函数：

```js
$("input").blur(function(){   
    $(this).css("background-color","#ffffff"); 
});
```

#### note

**一.keypress,keydown,keyup的区别:**

- 1.keydown：在键盘上按下某键时发生,一直按着则会不断触发（opera浏览器除外）, 它返回的是**键盘代码**;
-  2.keypress：在键盘上按下一个按键，并产生一个字符时发生**, 返回ASCII码**。注意: **shift、alt、ctrl**等键按下并不会产生字符，所以监听无效 ,换句话说, 只有按下能在屏幕上输出字符的按键时keypress事件才会触发。若一直按着某按键则会不断触发。
-  3.keyup：用户松开某一个按键时触发, 与keydown相对, **返回键盘代码.**

**二.两种常用用法举例**

案例1:获取按键代码或字符的ASCII码

```js
$(window).keydown( function(event){
   // 通过event.which可以拿到按键代码.  如果是keypress事件中,则拿到ASCII码.
} );
```

案例2:传递数据给事件处理函数

语法:

```js
jQueryObject.keydown( [[ data ,]  handler ] );
```

-  data: 通过event.data传递给事件处理函数的任意数据;
-  handler: 指定的事件处理函数;

举例:

```js
// 只允许按下的字母键生效, 65~90是所有小写字母的键盘代码范围.
var validKeys = { start: 65, end: 90  };
$("#keys").keydown( validKeys, function(event){
    var keys = event.data;  //拿到validKeys对象.
    return event.which >= keys.start && event.which <= keys.end;
} );
```

2. 关于获取触发事件的说明：

**1. 获取事件对象**

```js
$(document).ready(function(){
    $(window).keypress(function(event){    
        //获取事件对象，里面包含各种有用的信息。
        console.log(event);
        //console.log(event.which);
    });
});
```

**2. keypress事件获取键入字符**

```js
$(window).keypress(function(event){
    //event.which是获取ASCII码，前面的函数是将ASCII码转换成字符，空格键和Enter键输出均为空白。
    console.log(String.fromCharCode(event.which));
    //从event对象中key属性获取字符，但是Enter键的key值为"Enter"，空白键还是空白" "。
    console.log(event.key);
});
```



### 06 jQuery 效果- 隐藏和显示

隐藏、显示、切换，滑动，淡入淡出，以及动画，哇哦！

#### jQuery hide() 和 show()

通过 jQuery，您可以使用 hide() 和 show() 方法来隐藏和显示 HTML 元素：

```js
$("#hide").click(function(){
$("p").hide();
});
$("#show").click(function(){
$("p").show();
});
```

**语法**

```js
$(*selector*).hide(*speed,callback*);

$(*selector*).show(*speed,callback*);  
```

可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

下面的例子演示了带有 speed 参数的 hide() 方法：

```js
$("button").click(function(){
	$("p").hide(1000);
});
```

下面的例子演示了带有 speed 参数的 hide() 方法，并使用回调函数：

```js
$(document).ready(function(){   
    $(".hidebtn").click(function(){     
        $("div").hide(1000,"linear",function(){       
            alert("Hide() 方法已完成!");     
        });   
    }); 
});
```

第二个参数是一个字符串，表示过渡使用哪种**缓动函数**。（译者注：jQuery自身提供"linear" 和 "swing"，其他可以使用相关的插件）。

#### jQuery toggle()

通过 jQuery，您可以使用 toggle() 方法来切换 hide() 和 show() 方法。

显示被隐藏的元素，并隐藏已显示的元素：

```js
$("button").click(function(){   $("p").toggle(); });
```

语法

```js
$(*selector*).toggle(*speed,callback*);
```

可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

#### note（有些疑惑）

1. 对于可选的 callback 参数，有以下两点说明：

1.$(*selector*)选中的元素的个数为n个，则callback函数会执行n次；

2.callback函数名后加括号，会立刻执行函数体，而不是等到显示/隐藏完成后才执行；

3.callback既可以是函数名，也可以是匿名函数；
   小kuoai

2. 对于楼上，总结的很到位，补充一点：

**$(selector)** 选中的元素的个数为 n 个，则 callback 函数会执行 n 次。

对于这里，当 callback 函数加上括号时，函数立即执行，只会调用一次， 如果不加括号，元素显示或隐藏后调用函数，才会调用多次。

### 07.1  jQuery DOM 操作

jQuery 拥有可操作 HTML 元素和属性的强大方法。

jQuery 中非常重要的部分，就是操作 DOM 的能力。

jQuery 提供一系列与 DOM 相关的方法，这使**访问和操作元素和属性**变得很容易。

DOM = Document Object Model（文档对象模型）**  DOM 定义访问 HTML 和 XML 文档的标准："W3C 文档对象模型独立于平台和语言的界面，允许程序和**脚本动态访问**和**更新文档的内容、结构以及样式**。"  

#### 获得内容 - text()、html() 以及 val()

三个简单实用的用于 DOM 操作的 jQuery 方法：

- text() - 设置或返回所选元素的**文本内容**

- html() - 设置或返回**所选元素**的内容（包括 HTML 标记）

- val() - 设置或返回**表单字段**的值

  下面的例子演示如何通过 jQuery text() 和 html() 方法来获得内容：

  ```js
  $("#btn1").click(function(){   
      alert("Text: " + $("#test").text()); 
  }); 
  $("#btn2").click(function(){   
      alert("HTML: " + $("#test").html()); 
  });
  ```

  尝试一下 »

  下面的例子演示如何通过 jQuery val() 方法获得输入字段的值：

  ```js
  $("#btn1").click(function(){   alert("值为: " + $("#test").val()); });
  ```

  下面的例子演示如何通过 jQuery val() 方法获得输入字段的值：

  ```js
  $("#btn1").click(function(){
  alert("值为: " + $("#test").val());
  });
  ```

  获取属性 - attr()

jQuery attr() 方法用于获取属性值。

下面的例子演示如何获得链接中 href 属性的值：

```js
$("button").click(function(){   alert($("#runoob").attr("href")); });
```

#### note

1. **attr** 和 **prop** 的区别介绍：

对于 HTML 元素本身就带有的固有属性，在处理时，使用 **prop** 方法。

对于 HTML 元素我们自己自定义的 DOM 属性，在处理时，使用 **attr** 方法。

实例 1：

```js
<a href="https://www.runoob.com" target="_self" class="btn">菜鸟教程</a>
```

这个例子里 **<a>** 元素的 DOM 属性有: **href、target** 和 **class**，这些属性就是 **<a>** 元素本身就带有的属性，也是 W3C 标准里就包含有这几个属性，或者说在 IDE 里能够智能提示出的属性，这些就叫做固有属性。处理这些属性时，建议使用 **prop** 方法。

```js
<a href="#" id="link1" action="delete" rel="nofollow">删除</a>
```

这个例子里 **<a>** 元素的 DOM 属性有: **href、id** 和 **action**，很明显，前两个是固有属性，而后面一个 **action** 属性是我们自己自定义上去的，**<a>** 元素本身是没有这个属性的。这种就是自定义的 DOM 属性。处理这些属性时，建议使用 **attr** 方法。

2. **prop()函数的结果:**

​      1.如果有相应的属性，返回指定属性值。

​      2.如果没有相应的属性，返回值是空字符串。

**attr()函数的结果:**

​      1.如果有相应的属性，返回指定属性值。

​      2.如果没有相应的属性，返回值是 undefined。

对于HTML元素本身就带有的固有属性，在处理时，使用prop方法。

对于HTML元素我们自己自定义的DOM属性，在处理时，使用 attr 方法。

**具有 true 和 false 两个属性的属性，如 checked, selected 或者 disabled 使用prop()**

### 07.2 jQuery - 设置内容和属性

#### 设置内容 - text()、html() 以及 val()

我们将使用前一章中的三个相同的方法来设置内容：

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括 HTML 标记）
- val() - 设置或返回表单字段的值

下面的例子演示如何通过 text()、html() 以及 val() 方法来设置内容：

```js
$("#btn1").click(function(){     
    $("#test1").text("Hello world!"); 
}); 
$("#btn2").click(function(){     
    $("#test2").html("<b>Hello world!</b>"); 
}); 
$("#btn3").click(function(){     
    $("#test3").val("RUNOOB"); 
});
```

#### text()、html() 以及 val() 的回调函数

上面的三个 jQuery 方法：text()、html() 以及 val()，同样拥有回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

下面的例子演示带有回调函数的 text() 和 html()：

```js
$("#btn1").click(function(){
    $("#test1").text(function(i,origText){
        return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")"; 
    });
});
 
$("#btn2").click(function(){
    $("#test2").html(function(i,origText){
        return "旧 html: " + origText + " 新 html: Hello <b>world!</b> (index: " + i + ")"; 
    });
});
```

1. 设置属性 - **attr**()

jQuery attr() 方法也用于设置/改变属性值。

下面的例子演示如何改变（设置）链接中 href 属性的值：

```js
$("button").click(function(){
  $("#runoob").attr("href","http://www.runoob.com/jquery");
});
```

2. attr() **方法也允许您同时设置多个属性**。

下面的例子演示如何同时设置 href 和 title 属性：

```js
$("button").click(function(){
    $("#runoob").attr({
        "href" : "http://www.runoob.com/jquery",
        "title" : "jQuery 教程"
    });
});
```

3. attr() **的回调函数**

jQuery 方法 attr()，也提供回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

下面的例子演示带有回调函数的 attr() 方法：

```js
$("button").click(function(){
  $("#runoob").attr("href", function(i,origValue){
    return origValue + "/jquery"; 
  });
});
```

### 08 jQuery - 添加元素

通过 jQuery，可以很容易地添加新元素/内容。

我们将学习用于添加新内容的四个 jQuery 方法：

- append() - 在被选元素的结尾插入内容

- prepend() - 在被选元素的开头插入内容

- after() - 在被选元素之后插入内容

- before() - 在被选元素之前插入内容

  

1. 1jQuery **append**() 方法 在后添加

jQuery append() 方法在被选元素的结尾插入内容（仍然该元素的内部）。

```js
$("p").append("追加文本");
```

1. 2 jQuery **prepend**() 方法 在前添加

jQuery prepend() 方法在被选元素的开头插入内容。

```js
$("p").prepend("在开头追加文本");
```

#### 通过 append() 和 prepend() 方法添加若干新元素

在上面的例子中，我们只在被选元素的开头/结尾插入文本/HTML。

不过，append() 和 prepend() 方法能够通过参数接收无限数量的新元素。可以通过 jQuery 来生成文本/HTML（就像上面的例子那样），或者通过 JavaScript 代码和 DOM 元素。

在下面的例子中，我们创建若干个新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 append() 方法把这些新元素追加到文本中（对 prepend() 同样有效）：

```js
function appendText()
{
    var txt1="<p>文本。</p>";              // 使用 HTML 标签创建文本
    var txt2=$("<p></p>").text("文本。");  // 使用 jQuery 创建文本
    var txt3=document.createElement("p");
    txt3.innerHTML="文本。";               // 使用 DOM 创建文本 text with DOM
    $("body").append(txt1,txt2,txt3);        // 追加新元素
}
```

![1553440936838](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553440936838.png)

#### jQuery after() 和 before() 方法

jQuery after() 方法在被选元素之后插入内容。

jQuery before() 方法在被选元素之前插入内容。

```js
$("img").after("在后面添加文本");   
$("img").before("在前面添加文本");
```

![1553441031094](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441031094.png)

#### 通过 after() 和 before() 方法添加若干新元素

after() 和 before() 方法能够通过参数接收无限数量的新元素。可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建新元素。

在下面的例子中，我们创建若干新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 after() 方法把这些新元素插到文本中（对 before() 同样有效）：

```js
function afterText()
{
var txt1="<b>I </b>";                    // 使用 HTML 创建元素
var txt2=$("<i></i>").text("love ");     // 使用 jQuery 创建元素
var txt3=document.createElement("big");  // 使用 DOM 创建元素
txt3.innerHTML="jQuery!";
$("img").after(txt1,txt2,txt3);          // 在图片后添加文本
}
```

![1553441075445](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441075445.png)

#### note

1. 那有木有考虑过append/prepend和after/before有什么区别呢？

   **append**

   ```js
   <p>
     <span class="s1">s1</span>
   </p>
   <script>
   $("p").append('<span class="s2">s2</span>');
   </script>
   ```

   结果是这样的:

   ```js
   <p>
     <span class="s1">s1</span>
     <span class="s2">s2</span>
   </p>
   ```

   **after**

   ```js
   <p>
     <span class="s1">s1</span>
   </p>
   <script>
   $("p").after('<span class="s2">s2</span>');
   </script>
   ```

   结果是这样的:

   ```js
   <p>
     <span class="s1">s1</span>
   </p>
   <span class="s2">s2</span>
   ```

   **总结：**

   append/prepend 是在选择元素内部嵌入。

   after/before 是在元素外面追加。

2. 参数可以是个 list:

```js
function afterText(){
    var txt1="<b>I </b>";                    // 使用 HTML 创建元素
    var txt2=$("<i></i>").text("love ");     // 使用 jQuery 创建元素
    var txt3=document.createElement("big");  // 使用 DOM 创建元素
    txt3.innerHTML="jQuery!";
    $("img").after([txt1,txt2,txt3]);          // 在图片后添加文本
}
```

### 09 jQuery - 删除元素

通过 jQuery，可以很容易地删除已有的 HTML 元素。

#### 删除元素/内容

如需删除元素和内容，一般可使用以下两个 jQuery 方法：

- remove() - 删除被选元素（及其子元素）

- empty() - 从被选元素中删除子元素

  jQuery **remove**() 方法

  ```js
  jQuery remove() 方法删除被选元素及其子元素。
  $("#div1").remove();
  ```

  

![1553441299255](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441299255.png)

![1553441311559](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441311559.png)



jQuery **empty**() 方法

jQuery empty() 方法删除被选元素的子元素。

```js
$("#div1").empty();
```

![1553441397663](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441397663.png)



![1553441410951](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441410951.png)

#### 过滤被删除的元素

jQuery remove() 方法也可接受一个参数，允许您对被删元素进行过滤。

该参数可以是任何 jQuery 选择器的语法。

下面的例子删除 class="italic" 的所有 <p> 元素：

```js
$("p").remove(".italic");
```

![1553441586705](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441586705.png)

![1553441596617](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553441596617.png)

#### note

在使用 remove() 的过滤器删除时，不能删除带有过滤器的子元素。

```
$(document).ready(function(){
    $("button").click(function(){
        $("#div1").remove(".part");
    });
});
```

解释一下楼上的，就是说如果子元素符合过滤器中条件而父元素不符合的话，是不会删除符合条件的子元素，即过滤器中条件只能作用于同级，不能作用于子元素。

![1553442432340](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553442432340.png)

**$(selector)** 语法的返回结果是一个元素的列表，即：将 **$("#div1")** 看作一个列表，**remove()** 中的筛选条件实际上是对这个列表中的元素进行筛选删除，而不会去删除这个列表中不存在的元素（子元素不在这个列表中）。

### 010 jQuery 遍历

#### 什么是遍历？

jQuery 遍历，意为"**移动**"，用于根据其**相对于其他元素**的关系来"查找"（或选取）**HTML 元素**。以某项选择开始，并沿着这个选择移动，直到抵达您期望的元素为止。

下图展示了一个家族树。通过 jQuery 遍历，您能够从被选（当前的）元素开始，轻松地在家族树中向上移动（祖先），向下移动（子孙），水平移动（同胞）。这种移动被称为对 DOM 进行遍历。

![jQuery Dimensions](http://www.runoob.com/images/img_travtree.png)

+ </div> 元素是 </ul> 的父元素，同时是其中所有内容的祖先。

+ </ul> 元素是 </li> 元素的父元素，同时是 <div> 的子元素

+ 左边的 <li> 元素是 <span> 的父元素，<ul> 的子元素，同时是 <div> 的后代。

+ <span> 元素是 <li> 的子元素，同时是 <ul> 和 <div> 的后代。

+ 两个 <li> 元素是同胞（拥有相同的父元素）。

* 右边的 <li> 元素是 <b> 的父元素，<ul> 的子元素，同时是 <div> 的后代。

- <b> 元素是右边的 <li> 的子元素，同时是 <ul> 和 <div> 的后代。

祖先是父、祖父、曾祖父等等。后代是子、孙、曾孙等等。同胞拥有相同的父。

#### 遍历 DOM

jQuery 提供了多种遍历 DOM 的方法。

遍历方法中最大的种类是树遍历（tree-traversal）。

下一章会讲解如何在 DOM 树中向上、下以及同级移动。

### 011 jQuery 遍历 - 祖先

祖先是父、祖父或曾祖父等等。

通过 jQuery，您能够向上遍历 DOM 树，以查找元素的祖先。

------

#### 向上遍历 DOM 树

这些 jQuery 方法很有用，它们用于向上遍历 DOM 树：

- parent()

- parents()

- parentsUntil()

  #### jQuery parent() 方法

  parent() 方法返回被选元素的直接父元素。

  该方法只会向上一级对 DOM 树进行遍历。

  下面的例子返回每个 <span> 元素的的直接父元素：

  ```js
  $(document).ready(function(){   $("span").parent(); });
  ```

  ![1553443282085](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553443282085.png)

  #### jQuery parents() 方法

  parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。

  下面的例子返回所有 <span> 元素的所有祖先：

  ```js
  $(document).ready(function(){   $("span").parents(); });
  ```

  您也可以使用可选参数来过滤对祖先元素的搜索。

  下面的例子返回所有 <span> 元素的所有祖先，并且它是 <ul> 元素：	

```js
$(document).ready(function(){
	$("span").parents("ul");
});
```

![1553443298227](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553443298227.png)

#### jQuery parentsUntil() 方法

parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。

下面的例子返回介于 <span> 与 <div> 元素之间的所有祖先元素：

```js
$(document).ready(function(){   
    $("span").parentsUntil("div"); 
});
```

![1553443320713](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1553443320713.png)

### 012  jQuery - AJAX 简介

AJAX 是与服务器交换数据的技术，它在不重载全部页面的情况下，实现了对**部分网页的更新**。

```js
$("#div1").load("/try/ajax/demo_test.txt");
```

####   什么是 AJAX？

AJAX = 异步 JavaScript 和 XML（Asynchronous JavaScript and XML）。

简短地说，**在不重载整个网页的情况下，AJAX 通过后台加载数据，**并在网页上进行显示。

使用 AJAX 的应用程序案例：谷歌地图、腾讯微博、优酷视频、人人网等等。

通过 jQuery AJAX 方法，您能够使用 HTTP Get 和 HTTP Post 从远程服务器上请求文本、HTML、XML 或 JSON - 同时您能够把这些外部数据直接载入网页的被选元素中。

> 如果没有 jQuery，AJAX 编程还是有些难度的。
>
> 编写常规的 AJAX 代码并不容易，因为不同的浏览器对 AJAX 的实现并不相同。这意味着您必须编写额外的代码对浏览器进行测试。不过，jQuery 团队为我们解决了这个难题，我们只需要一行简单的代码，就可以实现 AJAX 功能。

#### AJAX load() 方法

jQuery load() 方法是简单但强大的 AJAX 方法。

**load() 方法从服务器加载数据，并把返回的数据放入被选元素中。**

**语法:**

```js
$(selector).load(URL,data,callback);
```

必需的 *URL* 参数规定您希望加载的 URL。

可选的 *data* 参数规定与**请求**一同发送的查询字符串键/值对集合。

可选的 *callback* 参数是 load() 方法完成后所执行的函数名称。

**这是示例文件（"demo_test.txt"）的内容：**

```js
<h2>jQuery AJAX 是个非常棒的功能！</h2> <p id="p1">这是段落的一些文本。</p>
```

下面的例子会把文件 "demo_test.txt" 的内容加载到指定的 <div> 元素中：

```js
$("#div1").load("demo_test.txt");
```

也可以把 jQuery 选择器添加到 URL 参数。

下面的例子把 "demo_test.txt" 文件中 id="p1" 的元素的内容，加载到指定的 <div> 元素中：

```js
$("#div1").load("demo_test.txt #p1");
```

可选的 callback 参数规定当 load() 方法完成后所要允许的回调函数。回调函数可以设置不同的参数：

- *responseTxt* - 包含调用成功时的结果内容
- *statusTXT* - 包含调用的状态
- *xhr* - 包含 XMLHttpRequest 对象

下面的例子会在 load() 方法完成后显示一个提示框。如果 load() 方法已成功，则显示"外部内容加载成功！"，而如果失败，则显示错误消息：

```js
$("button").click(function(){
  $("#div1").load("demo_test.txt",function(responseTxt,statusTxt,xhr){
    if(statusTxt=="success")
      alert("外部内容加载成功!");
    if(statusTxt=="error")
      alert("Error: "+xhr.status+": "+xhr.statusText);
  });
});
```

#### note

为了避免多页面情形下的代码重复，可以利用 load() 方法，将**重复的部分（**例如导航栏）放入单独的文件，使用下列方法进行导入：

```js
//1.当前文件中要插入的地方使用此结构：
<div class="include" file="***.html"></div>

//2.***.html中放入内容，用html格式仅仅因为会有编辑器的书写辅助。。

//3.代码：
$(".include").each(function() {
    if (!!$(this).attr("file")) {
        var $includeObj = $(this);
        $(this).load($(this).attr("file"), function(html) {
            $includeObj.after(html).remove(); //加载的文件内容写入到当前标签后面并移除当前标签
        })
    }
});
或者在index文件里只写重复部分，剩下的一股脑放各自单独文件 load() 进来~
```

### 013 AJAX get() 和 post() 方法

jQuery get() 和 post() 方法用于通过 HTTP GET 或 POST 请求从服务器请求数据。

#### HTTP 请求：GET vs. POST

两种在客户端和服务器端进行请求-响应的常用方法是：GET 和 POST。

- *GET* - 从指定的资源请求数据
- *POST* - 向指定的资源提交要处理的数据

GET 基本上用于从服务器获得（取回）数据。注释：GET 方法可能**返回缓存数据**。

POST 也可用于从服务器获取数据。不过，POST 方法**不会缓存数据**，并且常用于**连同请求一起发送数据**。

#### jQuery $.get() 方法

$.get() 方法通过 HTTP GET 请求从服务器上请求数据。

语法

```js
$.get(*URL*,*callback*);
```

必需的 *URL* 参数规定您希望请求的 URL。

可选的 *callback* 参数是请求成功后所执行的函数名。

下面的例子使用 $.get() 方法从服务器上的一个文件中取回数据：

```js
$("button").click(function(){
  $.get("demo_test.php",function(data,status){
    alert("数据: " + data + "\n状态: " + status);
  });
});
```

$.get() 的第一个参数是我们希望请求的 URL（"demo_test.php"）。

第二个参数是回调函数。第一个回调参数存有**被请求页面的内容**，第二个回调参数存有**请求的状态**。

#### jQuery $.post() 方法

$.post() 方法通过 HTTP POST 请求向服务器提交数据。

**语法:**

$.post(*URL,data,callback*);

必需的 *URL* 参数规定您希望请求的 URL。

可选的 *data* 参数规定连同请求发送的数据。

可选的 *callback* 参数是请求成功后所执行的函数名。

```js
$("button").click(function(){
    $.post("/try/ajax/demo_test_post.php",
    {
        name:"菜鸟教程",
        url:"http://www.runoob.com"
    },
        function(data,status){
        alert("数据: \n" + data + "\n状态: " + status);
    });
});

```

#### GET 对比 POST

##### 什么是 HTTP ？

超文本传输协议（HTTP）的设计目的是保证客户端与服务器之间的通信。

HTTP 的工作方式是客户端与服务器之间的请求-应答协议。

web 浏览器可能是客户端，而计算机上的网络应用程序也可能作为服务器端。

举例：客户端（浏览器）向服务器提交 HTTP 请求；服务器向客户端返回响应。响应包含关于请求的状态信息以及可能被请求的内容。

在客户机和服务器之间进行请求-响应时，两种最常被用到的方法是：GET 和 POST。

- **GET** - 从指定的资源请求数据。

- **POST** - 向指定的资源提交要被处理的数据。

- ##### GET 方法

  **请注意，查询字符串（名称/值对）是在 GET 请求的 URL 中发送的：**

  /test/demo_form.php**?name1=value1&name2=value2**

  **有关 GET 请求的其他一些注释：**

  - GET 请求可被缓存

  - GET 请求保留在浏览器历史记录中

  - GET 请求可被收藏为书签

  - GET 请求不应在处理敏感数据时使用

  - GET 请求有长度限制

  - GET 请求只应当用于取回数据

  - ##### POST 方法

    **请注意，查询字符串（名称/值对）是在 POST 请求的 HTTP 消息主体中发送的：**

    POST /test/demo_form.php HTTP/1.1
    Host: runoob.com
    **name1=value1&name2=value2**

    **有关 POST 请求的其他一些注释：**

    - POST 请求不会被缓存
    - POST 请求不会保留在浏览器历史记录中
    - POST 不能被收藏为书签
    - POST 请求对数据长度没有要求

|                  | GET                                                          | POST                                                         |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 后退按钮/刷新    | 无害                                                         | 数据会被重新提交（浏览器应该告知用户数据会被重新提交）。     |
| 书签             | 可收藏为书签                                                 | 不可收藏为书签                                               |
| 缓存             | 能被缓存                                                     | 不能缓存                                                     |
| 编码类型         | application/x-www-form-urlencoded                            | application/x-www-form-urlencoded or multipart/form-data。为二进制数据使用多重编码。 |
| 历史             | 参数保留在浏览器历史中。                                     | 参数不会保存在浏览器历史中。                                 |
| 对数据长度的限制 | 是的。当发送数据时，GET 方法向 URL 添加数据；URL 的长度是受限制的（URL 的最大长度是 2048 个字符）。 | 无限制。                                                     |
| 对数据类型的限制 | 只允许 ASCII 字符。                                          | 没有限制。也允许二进制数据。                                 |
| 安全性           | 与 POST 相比，GET 的安全性较差，因为所发送的数据是 URL 的一部分。  在发送密码或其他敏感信息时绝不要使用 GET ！ | POST 比 GET 更安全，因为参数不会被保存在浏览器历史或 web 服务器日志中。 |
| 可见性           | 数据在 URL 中对所有人都是可见的。                            | 数据不会显示在 URL 中。                                      |

##### note

Form 中的 get 和 post 方法，在数据传输过程中分别对应了 HTTP 协议中的 GET 和 POST 方法。二者主要区别如下：

-  1、Get 是用来从服务器上获得数据，而 Post 是用来向服务器上传递数据。
-  2、Get 将表单中数据的按照 variable=value 的形式，添加到 action 所指向的 URL 后面，并且两者使用“?”连接，而各个变量之间使用“&”连接；Post 是将表单中的数据放在 form 的数据体中，按照变量和值相对应的方式，传递到 action 所指向 URL。
-  3、Get 是不安全的，因为在传输过程，数据被放在请求的 URL 中，而如今现有的很多服务器、代理服务器或者用户代理都会将请求URL记录到日志文件中，然后放在某个地方，这样就可能会有一些隐私的信息被第三方看到。另外，用户也可以在浏览器上直接看到提交的数据，一些系统内部消息将会一同显示在用户面前。Post 的所有操作对用户来说都是不可见的。
-  4、Get 传输的数据量小，这主要是因为受 URL 长度限制；而 Post 可以传输大量的数据，所以在上传文件只能使用 Post（当然还有一个原因，将在后面的提到）。
-  5、Get 限制 Form 表单的数据集的值必须为 ASCII 字符；而 Post 支持整个 ISO10646 字符集。
-  6、Get 是 Form 的默认方法。

使用 Post 传输的数据，可以通过设置编码的方式正确转化中文；而 Get 传输的数据却没有变化。在以后的程序中，我们一定要注意这一点。