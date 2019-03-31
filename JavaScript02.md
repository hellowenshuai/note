### JavaScript day01

#### 01 JavaScript 输出

> 这个方法是 HTML DOM 中定义的。
>
> DOM (Document Object Model)（文档对象模型）是用于访问 HTML 元素的正式 W3C 标准。
>
> 格式<script> 
>
> 那些老旧的实例可能会在 <script> 标签中使用 type="text/javascript"。 
>
> 现在已经不必这样做了。
>
> JavaScript 是所有现代浏览器以及 HTML5 中的默认脚本语言。

**脚本位置**

在 <head> 或者 <body> 的JavaScript

外部脚本不能包含 <script> 标签。

**输出数据**

```javascript
window.alert() 弹出警告框。

document.write() 方法将内容写到 HTML 文档中。

innerHTML 写入到 HTML 元素。

console.log() 写入到浏览器的控制台。
```



> ​	console.log 可以添加显示样式 eg: console.log('%cfuck', 'font-size:20px')

**输出内容**

使用 document.write() 向文档输出写内容。

如果在文档已完成加载后执行 document.write，整个 HTML 页面将被覆盖

**写到控制台(调试模式)**

使用 console.log() 方法在浏览器中显示 JavaScript 值。

F12 启用调试模式， 在调试窗口中点击 "Console" 菜单。



```javascript
<button onclick="winTest()">按钮</button>
function winTest()
{
    var txt1 = "This is a new window.";
    var txt2 = "This is a test.";
    document.open("text/html","replace");//加上
    document.writeln(txt1);
    document.write(txt2);
    document.close();//加上
}//This is a new window. This is a test.

```

**注：**该方法将关闭 open() 方法打开的文档流，并强制地显示出所有缓存的输出内容。如果您使用 write() 方法动态地输出一个文档，必须记住当你这么做的时候要调用 close() 方法，以确保所有文档内容都能显示。document.write() 不会隐式调用 document.close() 方法的，否则例 2 中将不会有 **This is a new window.** 内容了

一旦调用了close()，就不应该再次调用 write()，因为这会隐式地调用 open() 来擦除当前文档并开始一个新的文档。

在载入页面后，浏览器输出流自动关闭。在此之后，比如延迟脚本 [setTimeout()] 或是 onload 执行的方法，任何一个对当前页面进行操作的 document.write()方法将打开—个新的输出流，它将清除当前页面内容(包括源文档的任何变量或值)。

#### 02 JavaScript语法

**数组（Array）字面量** 定义一个数组：

```javascript
[40, 100, 1, 5, 25, 10]

```

**对象（Object）字面量** 定义一个对象：

```javascript
{firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}

```

**函数（Function）字面量** 定义一个函数：

```javascript
function myFunction(a, b) { return a * b;}

```

##### JavaScript 数据类型

JavaScript 有多种数据类型：数字，字符串，数组，对象等等：

```javascript
var length = 16;                                  // Number 通过数字字面量赋值 
var points = x * 10;                              // Number 通过表达式字面量赋值
var lastName = "Johnson";                         // String 通过字符串字面量赋值
var cars = ["Saab", "Volvo", "BMW"];              // Array  通过数组字面量赋值
var person = {firstName:"John", lastName:"Doe"};  // Object 通过对象字面量赋值
```

**三种变量命名规则：**

```javascript
var **firstName**='king';//小驼峰

var **FirstName**='queen';//大驼峰

var **first_name**='maizi';//下划线法
```

JavaScript是弱类型编程语言,定义变量都使用 var 定义,与 Java 这种强类型语言有区别.

在定义后可以通过 **typeOf()** 来获取JavaScript中变量的数据类型.

```javascript
// Number 通过数字字面量赋值 

// Number 通过表达式字面量赋值

// String 通过字符串字面量赋值

// Array  通过数组字面量赋值 

// Object 通过对象字面量赋值
```

有个情况需要特别注意: **typeof 不能用来判断是 Array 还是Object**

```javascript
var arr = [] typeof(arr) === 'object' // true

```

当然你可以使用其他方式来判断：

**1、使用 isArray 方法**

```javascript
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
// 判断是否支持该方法
if (Array.isArray) {
    if(Array.isArray(cars)) {
        document.write("该对象是一个数组。") ;
    }
}
```

**2、使用 instanceof 操作符**

```javascript
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";

if (cars instanceof Array) {
    document.write("该对象是一个数组。") ;
}
```

```javascript
<script>
document.getElementById("demo").innerHTML = 123e5;
</script>
```

这条语句里面的 **123e5** 为什么运算结果会等于 **12300000**。

他们的算法是这样子的：**123e5就是123乘以10的5次方**。



##### JavaScript 语句标识符

| 语句         | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| break        | 用于跳出循环。                                               |
| catch        | 语句块，在 try 语句块执行出错时执行 catch 语句块。           |
| continue     | 跳过循环中的一个迭代。                                       |
| do ... while | 执行一个语句块，在条件语句为 true 时继续执行该语句块。       |
| for          | 在条件语句为 true 时，可以将代码块执行指定的次数。           |
| for ... in   | 用于遍历数组或者对象的属性（对数组或者对象的属性进行循环操作）。 |
| **function** | 定义一个函数                                                 |
| if ... else  | 用于基于不同的条件来执行不同的动作。                         |
| return       | 退出函数                                                     |
| switch       | 用于基于不同的条件来执行不同的动作。                         |
| throw        | 抛出（生成）错误 。                                          |
| try          | 实现错误处理，与 catch 一同使用。                            |
| **var**      | 声明一个变量。                                               |
| while        | 当条件语句为 true 时，执行语句块。                           |

##### 对代码行进行折行

您可以在文本字符串中使用反斜杠对代码行进行换行。下面的例子会正确地显示：

```javascript
document.write("你好 \
世界!");
```

不过，您不能像这样折行：

```javascript
document.write \ 
("你好世界!");
```



#### 03 JavaScript 注释

单行 多行 行末

```javascript
// 我是单行注释 ，行末注释 

/* 我是多行注释 */
```

**应用注释符号验证浏览器是否支持 JavaScript 脚本功能**

如果用户不能确定浏览器是否支持JavaScript脚本，那么可以应用HTML提供的注释符号进行验证。HTML注释符号是以 **<--** 开始以 **-->** 结束的。如果在此注释符号内编写 JavaScrip t脚本，对于不支持 JavaScript 的浏览器，将会把编写的 JavaScript 脚本作为注释处理。

使用 JavaScript 脚本在页面中输出一个字符串，将 JavaScript 脚本编写在 HTML 注释中，如果浏览器支持 JavaScript 将输出此字符串，如果不支持将不输出此字符串，代码如下:

```javascript
<script>
<!--
document.write("您的浏览器支持JavaScript脚本!");
//-->
</script>
```

**注意：**注释行结尾处的两条斜杠 **//** 是 JavaScript 注释符号。这可以避免 JavaScript 执行 **-->** 标签。



#### 04 JavaScript 变量



- 变量必须以字母开头

- 变量也能以 $ 和 _ 符号开头（不过我们不推荐这么做）

- 变量名称对大小写敏感（y 和 Y 是不同的变量）

  **JavaScript 语句和 JavaScript 变量都对大小写敏感。**

  

  ##### 声明（创建） JavaScrip 变量

  在 JavaScript 中创建变量通常称为"声明"变量。

  我们使用 var 关键词来声明变量：

  ```javascript
  var carname;
  ```

  变量声明之后，该变量是空的（它没有值）。

  如需向变量赋值，请使用等号：=

  ```javascript
  carname="Volvo";
  ```

  不过，您也可以在声明变量时对其赋值：

  ```javascript
  var carname="Volvo";
  ```

  ##### 一条语句，多个变量

  您可以在一条语句中声明很多变量。该语句以 var 开头，并使用逗号分隔变量即可：

  ```javascript
  var lastname="Doe", age=30, job="carpenter";
  ```

  声明也可横跨多行：

  ```javascript
  var lastname="Doe",
  age=30,
  job="carpenter";
  ```

  一条语句中声明的多个不可以赋同一个值:

  ```javascript
  var x,y,z=1;
  
  x,y 为 undefined， z 为 1。
  ```

  ##### Value = undefined

  在计算机程序中，经常会声明无值的变量。未使用值来声明的变量，其值实际上是 undefined。

  在执行过以下语句后，变量 carname 的值将是 undefined：

  ```javascript
  var carname;
  ```

  ##### 重新声明 JavaScript 变量

  如果重新声明 JavaScript 变量，该变量的值不会丢失：

  在以下两条语句执行后，变量 carname 的值依然是 "Volvo"：

  ```javascript
  var carname="Volvo"; 
  var carname;
  ```

  ##### **介绍JS中的let变量:**

  ```javascript
  let var1 [= value1] [, var2 [= value2]] [, ..., varN [= valueN]];
  ```

let允许你声明一个作用域被限制在块级中的变量、语句或者表达式。在Function中局部变量推荐使用let变量，避免变量名冲突。

**作用域规则**

let 声明的变量只在其声明的块或子块中可用，这一点，与var相似。二者之间最主要的区别在于var声明的变量的作用域是整个封闭函数。

```javascript
function varTest() {
    var x = 1;
    if (true) {
        var x = 2;       // 同样的变量!
        console.log(x);  // 2
    }
    console.log(x);  // 2
}

function letTest() {
    let x = 1;
    if (true) {
        let x = 2;       // 不同的变量    
        console.log(x);  // 2  
    }
    console.log(x);  // 1
}
```

说明：var**是全局定义**，let**是局部定义**

Javascript声明变量的时候，虽然用var关键字声明和不用关键字声明，很多时候运行并没有问题，但是这两种方式还是有区别的。可以正常运行的代码并不代表是合适的代码。

```javascript
// num1为全局变量，num2为window的一个属性
var num1 = 1;
num2 = 2;
// delete num1;  无法删除
// delete num2;  删除
function model(){
var num1 = 1; // 本地变量
num2 = 2;     // window的属性
    // 匿名函数
    (function(){
        var num = 1; // 本地变量
        num1 = 2; // 继承作用域（闭包）
        num3 = 3; // window的属性
    }())
}
```

**const 关键字**用来声明 JavaScript中的常量（与变量相对，不可修改，但同样是用于存储信息的"容器"。），常量的值不能通过重新赋值来改变，并且不能重新声明。

**与Java中final类似**

```javascript
//定义常量a并赋值为0
const a = 0;

//报错（不能重新赋值）
a = 1;

//报错（不能重新声明）
const a = 2;

//输出0
console.log("a is: " + a);
```

字面量（literal）用于表达源代码中一个**固定值**的表示法（notation），**整数、浮点数以及字符串**等等都是字面量。

示例：

```java
var a=1;   // a 是变量，1 是字面量
```

又如:

```java
var stooge = {    // stooge 是一个对象
   "frist-name" = "Julie",    // 等号左为属性名，右侧为属性值
    last_name = "beck"    // 属性名如果是合法的标识符，可省略引号

};    // "frist-name", last_name, "Julie", "beck" 都是对象字面量
```

总之，**字面量就是没有用标识符封装起来的量**，**是“值”的原始状态。**

与常量的区别如下：

```javascript
//  C/C++:

const int A = 1;    // A 是常量，1 是字面量
A++;    // error，常量值不能改变
```

**JavaScript 允许重复声明变量，后声明的覆盖之前的**

```javascript
var a = 1;
var a = 'x';
console.log(a);
// 输出 'x'
```

**JavaScript 允许重复定义函数**

```javascript
function test() {
    console.log("test");
}
test();     //输出 "test arg0 + undefined"

function test(arg1) {
    console.log("test arg" + arguments.length + " + " + arg1);
}
test(1,2);  //输出 "test arg2 + 1"
```

实参个数如果比形参少，那么剩下的默认赋值为 **undefined**，如果实参传的比形参数量多，那么是全部都会被传进去的，只不过没有对应的形参可以引用（但可以用 arguments 来获取剩下的参数）。

```javascript
function test(arg1) {
    for(var i=0; i<arguments.length; i++) {
        console.log(arguments[i]);
    }
}
test(1,2); //输出 1 2
```

**变量与函数重名的时候，变量生效 **

这涉及到了变量和函数的预解析：

- 变量声明会被顶置，**函数声明也会被顶置且比变量更先声明**。

- 变量的声明和赋值语句一起写时，JS引擎在解析时，会将其拆成声明和赋值2部分，声明置顶，赋值保留在原来位置。

- 声明过的变量不会再重复声明。

- ```javascript
  var a = 100;
  function a() {
      return "function";
  }
  console.log(a);     //输出 100
  console.log(a());   
  /*
  报错
  Uncaught TypeError: a is not a function
      (anonymous function) @test.html:9
  */
  ```

JS 中有两种函数，一种是普通函数，一种**是函数对象。**下面的这种就是“函数对象”，它实际上是声明一个匿名函数，然后将该函数的 init 方法赋值给该变量。

```javascript
var a = 100;
var a = function() {
    return "function";
}
console.log(a);
/* 
输出
function() {
    return "function";
}
*/
console.log(a());   //输出 "function"
```

**函数与内部变量重名**(不太懂)？？

定义普通函数，即在 window 变量下，定义一个 key，它的名字为该函数名，值为该函数的地址。**函数内部的 this 指向 window 对象。**

```javascript
function a() {
    console.log(this);  //输出 window{...}
    this.a = 1;         //即 window.a = 1，此时window下的function a已经被该变量覆盖了。
    var a = 5;          //下面的这几个变量都是局部变量，仅在花括号范围内有效。  
    a = 10;
    var v = "value"
    return "function";
}
console.log(a);         //输出 function a {...}
console.log(a());       //输出 "function"
console.log(a);         //输出 1
console.log(v);
/*
输出
Uncaught ReferenceError: v is not defined
    (anonymous function) @ mycolor.html:15
*/
```

#### 05 JavaScript 数据类型

值类型(基本类型)**：字符串（String）、数字(Number)、布尔(Boolean)、对空（Null）、未定义（Undefined）、Symbol。

**引用数据类型**：对象(Object)、数组(Array)、函数(Function)。

> **注：**Symbol 是 ES6 引入了一种新的原始数据类型，表示独一无二的值。

##### JavaScript 拥有动态类型

JavaScript 拥有动态类型。这意味着相同的变量可用作不同的类型：


  实例

```javascript
var x;               // x 为 undefined
var x = 5;           // 现在 x 为数字
var x = "John";      // 现在 x 为字符串
```

##### JavaScript 字符串

字符串是存储字符（比如 "Bill Gates"）的变量。

字符串可以是引号中的任意文本。您可以使用单引号或双引号：

```javascript
var carname="Volvo XC60";
var carname='Volvo XC60';
```

您可以在字符串中使用引号，只要不匹配包围字符串的引号即可：使用反斜杠 "\\"

```javascript
var carname1="Volvo XC60";
var carname2='Volvo XC60';
var answer1='It\'s alright';
var answer2="He is called \"Johnny\"";
var answer3='He is called "Johnny"';
```

##### JavaScript 数字

JavaScript 只有一种数字类型。数字可以带小数点，也可以不带：

```javascript
var x1=34.00;      //使用小数点来写
var x2=34;         //不使用小数点来写

极大或极小的数字可以通过科学（指数）计数法来书写：
```

```javascript
var y=123e5;      // 12300000
var z=123e-5;     // 0.00123
```

##### JavaScript 布尔

布尔（逻辑）只能有两个值：true 或 false。

##### JavaScript 数组

下面的代码创建名为 cars 的数组：

```javascript
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
```

或者 (condensed array):

```javascript
var cars=new Array("Saab","Volvo","BMW");
```

或者 (literal array):

```javascript
var cars=["Saab","Volvo","BMW"];  
```

数组下标是基于零的，所以第一个项目是 [0]，第二个是 [1]，以此类推。

##### JavaScript 对象

对象由花括号分隔。在括号内部，对象的属性以名称和值对的形式 (name : value) 来定义。属性由逗号分隔：

```javascript
var person={firstname:"John", lastname:"Doe", id:5566};
```

  空格和折行无关紧要。声明可横跨多行：

```javascript
var person={
firstname : "John",
lastname  : "Doe",
id        :  5566
};
```

对象属性有两种寻址方式：

```javascript
name=person.lastname;
    name=person["lastname"];
```

##### Undefined 和 Null

Undefined 这个值表示变量不含有值。

```javascript
//可以通过将变量的值设置为 null 来清空变量。
cars=null;
person=null;
```

##### 声明变量类型

当您声明新变量时，可以使用关键词 "new" 来声明其类型：

```javascript
var carname=new String;
var x=      new Number;
var y=      new Boolean;
var cars=   new Array;
var person= new Object;
```

##### 笔记

1. 数组有四种方式：

```javascript
var arr1 = new Array('a','b','c');  //这是一个预定义的数组，在创建时初始化
var arr2 = ['a','b','c']; 			//同样是在创建时初始化，但是这种创建更为简洁直观
var arr3 = new Array( );   var arr4 = [ ];     //这两种是创建空的数组
```

在数组操作中，最值得注意的是下标的使用，容易出错

对象的创建，一般推荐使用

```javascript
var people = {name : 'Tom', age : 21 , eat : function(){  }    }
```

也可先创建对象再追加属性和方法

```javascript
var people = new Object();
people.name = 'Tom';   
people.age = 21;  
people.eat = function(){  }
```

2. 最常用的对象创建方式:

   第一种：

   ```javascript
   function Demo(){
       var obj=new Object();
       obj.name="张思";
       obj.age=12;
       obj.firstF=function(){
       }
       obj.secondF=function(){
       }
       return obj;
   }
   
   var one=Demo();
   // 调用输出
   document.write(one.age);
   ```

   第二种：

   ```javascript
   function Demo(){
       this.name="张思";
       this.age=12;
       this.firstF=function(){
       }
       this.secondF=function(){
       }
   }
   
   var one=new Demo
   
   // 调用输出
   document.write(one.age);
   ```



3. 就算变量定义的是数组格式，**typeof** 返回的数据类型还是 **object** :

   ```javascript
   var cars=new Array();
   cars[0]="Saab";
   cars[1]="Volvo";
   cars[2]="BMW";
   document.write(typeof cars); // object
   ```

如果你要判断该对象是否为数组，可以使用以下两种方法:

**1、使用 isArray 方法**

```javascript
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
// 判断是否支持该方法
if (Array.isArray) {
    if(Array.isArray(cars)) {
        document.write("该对象是一个数组。") ;
    }
}
```

**2、使用 instanceof 操作符**

```javascript
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";

if (cars instanceof Array) {
    document.write("该对象是一个数组。") ;
}
```

4. 注意 undefined 和 null 都是小写，并且,二者都会输出 **undefined**
5. 

```javascript
var x,y;
if(x == null){
    document.write(x);
}
if(y == undefined){
    document.write(y);
}
```

#### 06 JavaScript 对象

JavaScript 对象是拥有属性和方法的数据。

> 真实生活中的对象，属性和方法

真实生活中，一辆汽车是一个对象。

对象有它的属性，如重量和颜色等，方法有启动停止等

##### JavaScript 对象

在 JavaScript中，几乎所有的事物都是对象。

**在 JavaScript 中，对象是非常重要的，当你理解了对象，就可以了解 JavaScript 。**

以下代码为变量 **car** 设置值为 "Fiat" :

```javascript
var car = "Fiat";
```

对象也是一个变量，但对象可以包含多个值（多个变量）。

```javascript
var car = {type:"Fiat", model:500, color:"white"};

```

在以上实例中，3 个值 ("Fiat", 500, "white") 赋予变量 car。

在以上实例中，3 个变量 (type, model, color) 赋予变量 car。

JavaScript 对象是变量的容器。

##### 对象定义

你可以使用字符来定义和创建 JavaScript 对象:

```javascript
  var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};

```

定义 JavaScript 对象可以跨越多行，空格跟换行不是必须的：

```javascript
  var person = {
    firstName:"John",
    lastName:"Doe",
    age:50,
    eyeColor:"blue"
};
```

##### 对象属性

可以说 "JavaScript 对象是变量的容器"。

但是，我们通常认为 "JavaScript 对象是键值对的容器"。

键值对通常写法为 **name : value** (键与值以冒号分割)。

键值对在 JavaScript 对象通常称为 **对象属性**。

**JavaScript 对象是属性变量的容器。**

对象键值对的写法类似于：

   - C 语言中的哈希表
- Java 中的哈希映射

##### 访问对象属性

你可以通过两种方式访问对象属性:

```javascript
person.lastName;

person["lastName"];
```

##### 对象方法

对象的方法定义了一个函数，并作为对象的属性存储。

对象方法通过添加 () 调用 (作为一个函数)。

该实例访问了 person 对象的 fullName() 方法:

```javascript
name = person.fullName();
```

如果你要访问 person 对象的 fullName 属性，它将作为一个定义函数的字符串返回：

```javascript
name = person.fullName;
```

  **JavaScript 对象是属性和方法的容器。**

##### 访问对象方法

你可以使用以下语法创建对象方法：

```javascript
  methodName : function() { code lines }
```

你可以使用以下语法访问对象方法：

```javascript
objectName.methodName()
```

通常 fullName() 是作为 person 对象的一个方法， fullName 是作为一个属性。

有多种方式可以创建，使用和修改 JavaScript 对象。

同样也有多种方式用来创建，使用和修改属性和方法。

##### 笔记

- 定义： JavaScript对象，存储属性和方法的容器。

- 定义规则：对象的属性之间用逗号隔开。

-  方法定义：对象的方法定义了一个函数，并作为对象的属性存储。

- 方法调用：对象方法通过添加（）调用。

  ```javascript
  var person={
  "name":"小明",
  "age":"18",
  "like":function(){
              return "喜欢打篮球,弹吉他";
        }
  }
  ```

javaScript对象也可以先创建，再添加属性和属性值，比如：

```javascript
var person=new Object();
person.name='小明'；
person.sex='男'；
person.method=function(){
  return this.name+this.sex;
}
```

javaScript对象中属性具有唯一性（这里的属性包括方法），如果有两个重复的属性，则以最后赋值为准。比如同时存在两个play:

```javascript
var person = {
    name: "小明",
    age: 18,
    sex: "男",
    play: "football",
    play: function () {
        return "like paly football";
    }
};
```



JavaScript 对象是键值对的容器，“键”必须为字符串，“值”可以是 JavaScript 中除 null 和 undefined 以外的任意数据类型。

```javascript
var bird = {
    "name" : "Amy",
    "age" : 1,
    "color" : "white",
    "skill" : function () {
        console.log("Fly");
    },
    "nickname" : null //非法
}
```

使用 **var name = person.fullName();** 调用对象函数时，fullName 会被立即执行：

```javascript
var person = {
    firstName: "John",
    lastName : "Doe",
    id : 5566,
    fullName : function() 
    {
      console.log("person.fullName");
    }
};

var name = person.fullName();
console.log("name");
```

控制台会先打印 **person.fullName** ，再打印 **name**。

#### 07 JavaScript 函数

函数是由事件驱动的方法，或者调用时执行的**可重复使用的代码**

##### 7.1、JavaScript 函数语法

函数就是包裹在花括号中的代码块，前面使用了关键词 function：

```javascript
  function name｛xxx｝
```

当调用该函数时，会执行函数内的代码。

JavaScript 对大小写敏感。关键词 function 必须是小写的，并且必须以与函数名称相同的大小写来调用函数。

##### 7.2、调用带参数的函数

在调用函数时，您可以向其传递值，这些值被称为参数。

这些参数可以在函数中使用。

您可以发送任意多的参数，由逗号 (,) 分隔：

```javascript
myFunction(argument1,argument2)
```

当您声明函数时，请把参数作为变量来声明：

```javascript
function myFunction(var1,var2)
{
代码
}
```

变量和参数必须以一致的顺序出现。第一个变量就是第一个被传递的参数的给定的值，以此类推。

<p>点击这个按钮，来调用带参数的函数。</p>
<button onclick="myFunction('Harry Potter','Wizard')">点击这里</button>

<script>
function myFunction(name,job){
	alert("Welcome " + name + ", the " + job);
}
</script>

##### 7.3、带有返回值的函数

在使用 return 语句时，函数会停止执行，并返回指定的值。

```javascript
function myFunction()
{
    var x=5;
    return x;
}
```

上面的函数会返回值 5。

**注意：** 整个 JavaScript 并不会停止执行，**仅仅是函数**。JavaScript 将继续执行代码，从调用函数的地方。

函数调用将被返回值取代：


  即使不把它保存为变量，您也可以使用返回值：

```javascript
document.getElementById("demo").innerHTML=myFunction();
```

您可以使返回值基于传递到函数中的参数：

计算两个数字的乘积，并返回结果：

```javascript
function myFunction(a,b) {     return a*b; }   document.getElementById("demo").innerHTML=myFunction(4,3);
```

在您仅仅希望退出函数时 ，也可使用 return 语句。返回值是可选的：

```javascript
function myFunction(a,b)
{
if (a>b)
{
return;
}
x=a+b
}  
```

##### 7.4、局部 JavaScript 变量

在 JavaScript 函数内部声明的变量（使用 var）是*局部*变量，所以只能在函数内部访问它。（该变量的作用域是局部的）。

您可以在不同的函数中使用名称相同的局部变量，因为只有声明过该变量的函数才能识别出该变量。

只要函数运行完毕，本地变量就会被删除。

##### 7.5、全局 JavaScript 变量

​	**在函数外声明的变量是*全局*变量**，网页上的所有脚本和函数都能访问它。

##### 7.6、JavaScript 变量的生存期

​	JavaScript 变量的生命期从它们被声明的时间开始。

​	局部变量会在函数运行以后被删除。

​	全局变量会在页面关闭后被删除。

##### 7.7、向未声明的 JavaScript 变量分配值

如果您把值赋给尚未声明的变量，该变量将被自动作为 window 的一个属性。

```javascript
carname="Volvo";
```

将声明 window 的一个属性 carname。

非严格模式下给**未声明变量赋值**创建的**全局变量**，是全局对象的可配置属性，可以删除

```javascript
var var1 = 1; // 不可配置全局属性
var2 = 2; // 没有使用 var 声明，可配置全局属性

console.log(this.var1); // 1
console.log(window.var1); // 1

delete var1; // false 无法删除
console.log(var1); //1

delete var2; 
console.log(delete var2); // true
console.log(var2); // 已经删除 报错变量未定义
```

##### 笔记

1. 在使用 return 语句时，函数会停止执行，并返回指定的值。例如：

   

2. 使用 HTML 、JavaScript 创建一个简单的计算器，包含加、减、乘、除四个功能：

```javascript
var result_1;
//加法
function add() {alert(1);
  var a = getFirstNumber();
  var b = getTwiceNumber();
  var re =Number( a) +Number( b);
  sendResult(re);
}

//减法
function subtract() {
  var a = getFirstNumber();
  var b = getTwiceNumber();
  var re = a - b;
  sendResult(re);
}

//乘法
function ride() {
  var a = getFirstNumber();
  var b = getTwiceNumber();
  var re = a * b;
  sendResult(re);
}

//除法
function devide() {
  var a = getFirstNumber();
  var b = getTwiceNumber();
  var re = a / b;
  sendResult(re);
}

//给p标签传值
function sendResult(result_1) {
  var num = document.getElementById("result")
  num.innerHTML = result_1;
}

//获取第一位数字
function getFirstNumber() {
  var firstNumber = document.getElementById("first").value;
  return firstNumber;
}

//获取第二位数字
function getTwiceNumber() {
  var twiceNumber = document.getElementById("twice").value;
  return twiceNumber;
}
```

1. 全选，反选，不选的demo

   [全选，反选]: https://c.runoob.com/codedemo/5359	"好看"

   ```javascript
   var checkAll = false;
   function allcheck(){
       checkAll = !checkAll;
       let inputs = document.getElementsByName('checkbox')
       for(var i =0;i<inputs.length;i++){
           for (var j = 0; j < inputs.length; j++) {//判断是否已经全选
               if (inputs[j].checked == true) {
                   checkAll = false;
               }else{
                   checkAll = true;
                   continue;
               }
           }
           
           inputs[i].checked = checkAll;
       }
   }
   ```

#### 08 JavaScript 作用域

作用域可访问变量的集合。

在 JavaScript 中, 对象和函数同样也是变量。

**在 JavaScript 中, 作用域为可访问变量，对象，函数的集合。**

JavaScript 函数作用域: 作用域在函数内修改。

##### 8.1JavaScript 局部作用域

```javascript
// 此处不能调用 carName 变量
function myFunction() {
var carName = "Volvo";
// 函数内可调用 carName 变量
}
```

因为局部变量只作用于函数内，所以不同的函数可以使用相同名称的变量。

局部变量在函数开始执行时创建，函数执行完后局部变量会自动销毁。

##### 8.2 JavaScript 全局变量

变量在函数外定义，即为全局变量。

全局变量有 **全局作用域**: 网页中所有脚本和函数均可使用。 

```javascript
var carName = " Volvo";
// 此处可调用 carName 变量
function myFunction() {
// 函数内可调用 carName 变量
}
```

如果变量在函数内没有声明（没有使用 var 关键字），该变量为全局变量。

```javascript
// 此处可调用 carName 变量
function myFunction() {
carName = "Volvo";
// 此处可调用 carName 变量
}
```

##### 8.3 JavaScript 变量生命周期

JavaScript 变量生命周期在它声明时初始化。

局部变量在函数执行完毕后销毁。

全局变量在页面关闭后销毁。

##### 8.4 函数参数

函数参数只在函数内起作用，是局部变量。

##### HTML 中的全局变量

在 HTML 中, 全局变量是 window 对象: 所有数据变量都属于 window 对象。

```javascript
  //此处可使用 window.carName
function myFunction() {
carName = "Volvo";
}
```

你的全局变量，或者函数，可以覆盖 window 对象的变量或者函数。
局部变量，包括 window 对象可以覆盖全局变量和函数。

##### 8.5 笔记

局部变量：在函数中通过var声明的变量。

全局变量：在函数外通过var声明的变量。

没有声明就使用的变量，默认为全局变量，不论这个变量在哪被使用

函数内未声明即使用的变量情况：

```javascript
function func(){
  undefined_var=110
}
```

在 func() 被第一次调用之前， undefined_var 变量是不存在的即 undefined。func() 被调用过之后，undefined_var 成为全局变量。

在 ES6 中，提供了 **let** 关键字和 **const** 关键字。

**let 的声明方式与 var 相同，用 let 来代替 var 来声明变量，就可以把变量限制在当前代码块中。**

**使用 const 声明的是常量，其值一旦被设定便不可被更改。**

#### 09 JavaScript 事件

HTML 事件是发生在 HTML 元素上的事情。

当在 HTML 页面中使用 JavaScript 时， JavaScript 可以触发这些事件。

##### 9.1 HTML 事件

HTML 事件可以是浏览器行为，也可以是用户行为。

以下是 HTML 事件的实例：

- HTML 页面完成加载
- HTML input 字段改变时
- HTML 按钮被点击

通常，当事件发生时，你可以做些事情。

在事件触发时 JavaScript 可以执行一些代码。

HTML 元素中可以添加事件属性，使用 JavaScript 代码来添加 HTML 元素。

```javascript
<button onclick="getElementById('demo').innerHTML=Date()">现在的时间是?</button>
```

#####  9.2  常见的HTML事件

下面是一些常见的HTML事件的列表:

| 事件        | 描述                         |
| ----------- | ---------------------------- |
| onchange    | HTML 元素改变                |
| onclick     | 用户点击 HTML 元素           |
| onmouseover | 用户在一个HTML元素上移动鼠标 |
| onmouseout  | 用户从一个HTML元素上移开鼠标 |
| onkeydown   | 用户按下键盘按键             |
| onload      | 浏览器已完成页面的加载       |

##### 9.3 JavaScript 可以做什么?

事件可以用于处理表单验证，用户输入，用户行为及浏览器动作:

```html
<!--页面加载时触发事件

页面关闭时触发事件

用户点击按钮执行动作

验证用户输入内容的合法性 -->
```

可以使用多种方法来执行 JavaScript 事件代码：

##### 9.4 笔记：

注意，当在 JS 文件中为相关元素设置事件时，其写法与 HTML 事件属性写法相同，例如：

```javascript
<button id="test" onclick="changeContent()">更换内容</button>
```

在 JS 中则需要这样写：

```javascript
var test = document.getElementById("test"); test.onclick = changeContent(){ //...... }
```

注意：在为元素添加事件句柄或者删除元素事件句柄的过程中，注意不要将event参数设置为onclick，而必须写成click，去掉事件名称中的on即可。

**注：**

添加事件句柄函数原型:

```javascript
element.addEventListener(event, function, [useCapture])
```

删除事件句柄的函数原型:

```javascript
element.removeEventListener(event, function, [useCapture])
```

#### 10  JavaScript 字符串			   

java字符串用来存储和处理文本。

##### 10.1 JavaScript 字符串

```javascript
var character = carname[7];
```

字符串的索引从 0 开始，这意味着第一个字符索引值为 [0],第二个为 [1], 以此类推。

你可以在字符串中使用引号，字符串中的引号不要与字符串的引号相同:

你也可以在字符串添加转义字符来使用引号：

**字符串长度**

```javascript
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length;  
```



##### 10.2 特殊字符

| 代码 | 输出        |
| ---- | ----------- |
| \'   | 单引号      |
| \"   | 双引号      |
| \\   | 反斜杠      |
| \n   | 换行        |
| \r   | 回车        |
| \t   | tab(制表符) |
| \b   | 退格符      |
| \f   | 换页符      |

  不要创建 String 对象。它会拖慢执行速度，并可能产生其他副作用：

```javascript
var x = "John";              
var y = new String("John");
(x === y) // 结果为 false，因为 x 是字符串，y 是对象
```

=== 为绝对相等，即数据类型与值都必须相等。

##### 字符串属性和方法

##### 笔记

1. JavaScript == 与 === 区别

   1、对于 string、number 等基础类型，== 和 === 是有区别的

   - a）不同类型间比较，== 之比较 "转化成同一类型后的值" 看 "值" 是否相等，=== 如果类型不同，其结果就是不等。
   -  b）同类型比较，直接进行 "值" 比较，两者结果一样。

   2、对于 Array,Object 等高级类型，== 和 === 是没有区别的

   进行 "指针地址" 比较

   3、基础类型与高级类型，== 和 === 是有区别的

   - a）对于 ==，将高级转化为基础类型，进行 "值" 比较
   -  b）因为类型不同，=== 结果为 false

   4、!= 为 == 的非运算，!== 为 === 的非运算

   ```javascript
   var num=1；
   
   var str="1"；
   
   var test=1；
   
   test == num   //true　相同类型　相同值 
   
   test === num  //true　相同类型　相同值 
   
   test !== num  //false test与num类型相同，其值也相同,　非运算肯定是false 
   
   num == str   //true 　把str转换为数字，检查其是否相等。 
   
   num != str   //false  == 的 非运算 
   
   num === str  //false  类型不同，直接返回false 
   
   num !== str  //true   num 与 str类型不同 意味着其两者不等　非运算自然是true啦
   ```

2. 双引号**" "** 中用单引号 **' '** 可以不用加反斜杠，例如：

   ```javascript
   var x="my name 'is' xxx"  // 此处不需要加反斜杠
   ```

   双引号**" "** 中用双引号 **" "** 需要加反斜杠，例如：

   ```javascript
   var x="my name \"is\" xxx"  // 此处需要在两个上引号前各加一个加反斜杠
   ```

   单引号 **' '** 中用双引号**" "** 不需要加反斜杠，当然加了也可以，例如：

   ```javascript
   var x1 ='my name "is" xxx'     // 此处不需要加反斜杠（推荐）
   
   var x2 ='my name \"is\" xxx'   // 添加反斜杠效果也一样（不推荐）
   ```

3. 字符基本操作

   ```javascript
   var x = "JohnJohn";              // x 是字符串
   y = x.charAt(2); // h
   y = x.charCodeAt(2); // 104
   y = x.concat(y, y); // JohnJohn104104, x+y+y
   y = x.indexOf('h'); // 2, 索引从0开始
   y = x.lastIndexOf('h'); // 6
   y = x.slice();
   y = x.split('o'); //J,hnJ,hn
   y = x.substr(2); // hnJohn	[2,length-1]
   y = x.substring(2,4) // hn，[2,3] 不包含尾
   y = x.toLocaleLowerCase(); // johnjohn,小写
   y = x.toLocaleUpperCase(); // JOHNJOHN,大写
   y = x.toString(); // 转成Stirng
   y = x.toUpperCase(); // JOHNJOHN,大写
   y = x.trim(); // JohnJohn,去除两端的空格
   y = x.valueOf(); // 返回某个字符串对象的原始值
   ```

#### 11 JavaScript 运算符

**运算符 = 用于赋值。**

**运算符 + 用于加值。**

运算符 = 用于给 JavaScript 变量赋值。

算术运算符 + 用于把值加起来。

#####   JavaScript 算术运算符

|        |              |       |                                                              |            |                                                              |
| ------ | ------------ | ----- | ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ |
| 运算符 | 描述         | 例子  | x 运算结果                                                   | y 运算结果 | 在线实例                                                     |
| +      | 加法         | x=y+2 | 7                                                            | 5          | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_add) |
| -      | 减法         | x=y-2 | 3                                                            | 5          | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_sub) |
| *      | 乘法         | x=y*2 | 10                                                           | 5          | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_mult) |
| /      | 除法         | x=y/2 | 2.5                                                          | 5          | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_div) |
| %      | 取模（余数） | x=y%2 | 1                                                            | 5          | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_mod) |
| ++     | 自增         | x=++y | 6                                                            | 6          | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_incr) |
| x=y++  | 5            | 6     | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_incr2) |            |                                                              |
| --     | 自减         | x=--y | 4                                                            | 4          | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_decr) |
| x=y--  | 5            | 4     |                                                              |            |                                                              |

##### JavaScript 赋值运算符

给定 **x=10** 和 **y=5**，下面的表格解释了赋值运算符：

| 运算符 | 例子 | 等同于 | 运算结果 | 在线实例                                                     |
| ------ | ---- | ------ | -------- | ------------------------------------------------------------ |
| =      | x=y  |        | x=5      | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_equal) |
| +=     | x+=y | x=x+y  | x=15     | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_plusequal) |
| -=     | x-=y | x=x-y  | x=5      | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_minequal) |
| *=     | x*=y | x=x*y  | x=50     | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_multequal) |
| /=     | x/=y | x=x/y  | x=2      | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_divequal) |
| %=     | x%=y | x=x%y  | x=0      | [实例 »](http://www.runoob.com/try/try.php?filename=tryjs_oper_modequal) |

##### 笔记

常见的不同类型运算的转换方式：

1.字符串和数字相加，数字转成字符串.

```javascript
var one="This is a test";
var two=123;
var three=one+two;

// 结果：three:This is a test123
```

2.数字和布尔值相加，布尔值 false 转成 0，true 转成 1

```javascript
var one=13;
var two=true;
var three=one+two;
// 结果 three:14
```

3.字符串与布尔值相加，布尔值转化成字符串。



取模运算的结果符号只与左边值的符号有关：

```javascript
var x = 7 % 3; // 结果为 1
var y = 7 % (-3); // 结果为 1
var z = (-7) % 3; // 结果为 -1
```

 如果 % 左边的操作数是正数，则模除的结果为正数或零；

 如果 % 左边的操作数是负数，则模除的结果为负数或零。

数字与 null(空值) 相加，null 转化为数字 0：

```javascript
var car=null+3+4;    // 结果为7
```

字符串与 null(空值) 相加，null 转化为字符串：

```javascript
var car=null+"a";    // 结果为 nulla
```

JavaScript == 与 === 区别

1、对于 string、number 等基础类型，== 和 === 是有区别的

- a）不同类型间比较，== 之比较 "转化成同一类型后的值" 看 "值" 是否相等，=== 如果类型不同，其结果就是不等。
-  b）同类型比较，直接进行 "值" 比较，两者结果一样。

2、对于 Array,Object 等高级类型，== 和 === 是没有区别的

进行 "指针地址" 比较

3、基础类型与高级类型，== 和 === 是有区别的

- a）对于 ==，将高级转化为基础类型，进行 "值" 比较
- b）因为类型不同，=== 结果为 false

首先说一下，其他数据类型转换为布尔类型的规则: **null、undefined、0、NaN、空字符串**转换为**false**，其他转化为 **true**。

**JavaScript 中有三种逻辑运算符：**

###### 1. 取反 !

首先把数据转化为布尔值，然后取反，结果为 true 或 false。

```javascript
<script type="text/javascript">
var a = [1,2,3];
var b = "hello";
var obj = new Object();
var d;

console.log(!"");   //true
console.log(!d);    //true
console.log(!a);    //false
console.log(!b);    //false
console.log(!obj);  //false
</script>
```

###### 2. 逻辑与 &&

JavaScript 中逻辑与和其他语言不太一样，如果第一个操作数是 true(或者能够转为 true)，计算结果就是第二个操作数，如果第一个操作数是 false，结果就是 false（短路计算），对于一些特殊数值不遵循以上规则。(**个人理解为:如果运算的第一个操作数为true,则返回第二个操作数,反之则返回第一个操作数**)

```javascript
<script type="text/javascript">
var a = [1,2,3];
var b = "hello";
var obj = new Object();
var d;

console.log(true && 10);            //第一个操作数是true，结果是第二个操作，也就是10
console.log(false && b);            //第一个操作数是false，结果flase
console.log(100 && false);          //第一个操作数是100，结果flase
console.log(undefined && false);    //第一个操作数是undefined，结果undefined
console.log(NaN && false);          //第一个操作数是NaN，结果NaN
console.log(null && false);         //第一个操作数是null，结果null
console.log('' && false);           //第一个操作数是空串，结果空串
console.log(0 && 100);              //结果是0
console.log(5 && 100);              //100
console.log(a && b);                //hello
console.log(obj && 200);            //200
</script>
```

###### 3. 逻辑或 ||

**如果第一个操作数不是 false，结果就是第一个操作数，否则结果是第二个操作数**。如果第一个操作数能够转为 true，结果就是第一个操作数(个人理解为:如果运算的第一个操作数为 true,则返回第一个操作数,反之则返回第二个操作数)

```javascript
<script type="text/javascript">
var a = [1,2,3];
var b = "hello";
var obj = new Object();
var d;

console.log(true || 10);        //第一个操作数是true，结果是第一个操作，也就是true
console.log(false || b);        //第一个操作数是false，结果是第二个操作数b
console.log(100 || false);      //第一个操作数是100，结果100
console.log(undefined || 9);    //第一个操作数是undefined转false，结果9
console.log(NaN || false);      //第一个操作数是NaN转false，结果第二个操作数
console.log(null || a);         //第一个操作数是null转false，结果a
console.log('' || false);       //第一个操作数是空串转false，结果第二操作数
console.log(0 || 100);          //结果是100
console.log(5 || 100);          //5
console.log(a || b);            //a
console.log(obj || 200);        //obj
</script>
```

#### 12 JavaScript if...Else 语句

条件语句用于基于不同的条件来执行不同的动作。

##### 条件语句

通常在写代码时，您总是需要为不同的决定来执行不同的动作。您可以在代码中使用条件语句来完成该任务。

在 JavaScript 中，我们可使用以下条件语句：

**if 语句** - 只有当指定条件为 true 时，使用该语句来执行代码

**if...else 语句** - 当条件为 true 时执行代码，当条件为 false 时执行其他代码

**if...else if....else 语句**- 使用该语句来选择多个代码块之一来执行**

**switch 语句** - 使用该语句来选择多个代码块之一来执行

##### 实例

```javascript
//如果时间小于 10:00，则生成问候 "Good morning"，
//如果时间大于 10:00 小于 20:00，则生成问候 "Good day"，
//否则生成问候 "Good evening"：

if (time<10) {     
    document.write("<b>早上好</b>"); 
} else if (time>=10 && time<16) {     
    document.write("<b>今天好</b>"); 
} else {     
    document.write("<b>晚上好!</b>"); 
}


```

##### 笔记

**提一个优化 if 的方法**

可以这样写：

```javascript
const condition = condition1
let obj = {
  'condition1' : () => { ... },
  'condition2' : () => { ... },
  'condition3' : () => { ... },
}
obj[condition]()
```

实例：

```javascript
const condition = 2
let obj = {
  '1' : () => { document.write(1) },
  '2' : () => { document.write(2) },
  '3' : () => { document.write(3) },
}

obj[condition]()
```





#### 13 switch

switch 中 case的判断是===的判断，即数据类型和值的双重判断，这点要注意。

另外switch的判断条件可以是String 、Number、Boolean、char、枚举、null、undefined

#### 14 foreach

JavaScript 支持不同类型的循环：

- **for** - 循环代码块一定的次数
- **for/in** - 循环遍历对象的属性
- **while** - 当指定的条件为 true 时循环指定的代码块
- **do/while** - 同样当指定的条件为 true 时循环指定的代码块



##### For 循环

for 循环是您在希望创建循环时常会用到的工具。

下面是 for 循环的语法：

for (*语句 1*; *语句 2*; *语句 3*)
{
    *被执行的代码块*
}

```javascript
for (var i=0; i<5; i++)
{
x=x + "该数字为 " + i + "<br>";
}
```

##### For/In 循环

JavaScript for/in 语句循环遍历对象的属性：

```javascript
var person={fname:"John",lname:"Doe",age:25}; 
for (x in person)  // x 为属性名
{
txt=txt + person[x];
}
```

##### 笔记

**for in** 循环不仅可以遍历对象的属性，还可以遍历数组。



```javascript
var x
var nums = [1, 3, 5];
for (x in nums)
{
    document.write(nums[x]+ "<br />");  // x 为数组索引
}
```

**for 循环除了使用 in 方式来循环数组，还提供了一个方式： of , 遍历数组时更加方便。**

**for...of** 是 ES6 新引入的特性。它既比传统的for循环简洁，同时弥补了forEach和for-in循环的短板。

for-of 的语法看起来跟 for-in 很相似，但它的功能却丰富的多，它能循环很多东西。

循环一个数组(Array):

```javascript
let iterable = [10, 20, 30];

for (let value of iterable) {
  console.log(value);
}
// 10
// 20
// 30
```

我们可以使用const来替代let，这样它就变成了在循环里的不可修改的静态变量。

```javascript
let iterable = [10, 20, 30];

for (const value of iterable) {
  console.log(value);
}
// 10
// 20
// 30
```

循环一个字符串：

```javascript
let iterable = "boo";

for (let value of iterable) {
  console.log(value);
}
// "b"
// "o"
// "o"
```

循环一个类型化的数组(TypedArray)：

```javascript
let iterable = new Uint8Array([0x00, 0xff]);

for (let value of iterable) {
  console.log(value);
}
// 0
// 255
```

循环一个Map:

```javascript
let iterable = new Map([["a", 1], ["b", 2], ["c", 3]]);

for (let [key, value] of iterable) {
  console.log(value);
}
// 1
// 2
// 3

for (let entry of iterable) {
  console.log(entry);
}
// [a, 1]
// [b, 2]
// [c, 3]
```

循环一个 Set:

```javascript
let iterable = new Set([1, 1, 2, 2, 3, 3]);

for (let value of iterable) {
  console.log(value);
}
// 1
// 2
// 3
```

#### 15 while

只要指定条件为 true，循环就可以一直执行代码块。

##### 语法

```javascript
while (条件)
{
    需要执行的代码
}
```

```javascript
while (i<5)
{
x=x + "The number is " + i + "<br>";
i++;
}
```

##### do/while 循环

do/while 循环是 while 循环的变体。该循环会在检查条件是否为真之前执行一次代码块，然后如果条件为真的话，就会重复这个循环。

```javascript
do
{
   需要执行的代码
}while (条件);
```



```javascript
do {     
    x=x + "The number is " + i + "<br>";     
    i++; 
} while (i<5);
```

别忘记增加条件中所用变量的值，否则循环永远不会结束！

##### 比较 for 和 while

```javascript
cars=["BMW","Volvo","Saab","Ford"];
var i=0;
for (;cars[i];)
{
document.write(cars[i] + "<br>");
i++;
}
```

```javascript
cars=["BMW","Volvo","Saab","Ford"];
var i=0;
while (cars[i])
{
document.write(cars[i] + "<br>");
i++;
}
```

##### 笔记

while 使用 length 属性循环数组

while 和 do/while 的区别 : do/while至少会执行一遍

```javascript
var size=[1,2,3,4,5,6,7] ; //申明一个数组
var i=0;

//while循环
while( i < size.length ) { 
    document.write(size[i] + " ");
    i++;
}

document.write("<br>---------------<br>");

//do…..while循环
j=0
do{
    document.write(size[j] + " ");
    j++;
}
while( j<size.length )
```

定义了数组后对数组进行赋值，中间如有某些下标未被使用（即未被赋值），在遍历的时候，采用一般的 for 循环和 for...in 循环得到的结果不同。

**for...in 循环会自动跳过那些没被赋值的元素，而 for 循环则不会，它会显示出 undefined。**

点击下面的按钮，循环遍历

```javascript
<button onclick="myFunction()">点击这里</button>
<p id="demo"></p>
<script>
function myFunction(){
    var array = new Array();
    var x;
    var txt=""
    array[0] = 1;
    array[3] = 2;
    array[4] = 3;
    array[10] = 4;
    for( x in array ){
        alert(array[x]);     // 依次显示出 1 2 3 4
    } 
    alert(array.length);    // 结果是11
    for( var i=0 ; i<4 ; i++){
        alert(array[i]);     // 依次显示出 1 undefined undefined 2 
    }
    document.getElementById("demo").innerHTML = txt;
}
</script>
```

#### 16 break和continue

##### break 语句用于跳出循环。

continue 用于跳过循环中的一个迭代。

break 语句可用于跳出循环。

break 语句跳出循环后，会继续执行该循环之后的代码（如果有的话）：

```javascript
for (i=0;i<10;i++)
{
if (i==3)
{
break;
}
x=x + "The number is " + i + "<br>";
}
```

由于这个 if 语句只有一行代码，所以可以省略花括号：

```javascript
for (i=0;i<10;i++)
{
if (i==3) break;
x=x + "The number is " + i + "<br>";
}
```

##### Continue 语句

**continue 语句**中断循环中的迭代，如果出现了指定的条件，然后继续循环中的下一个迭代。 该例子跳过了值 3：

```javascript
for (i=0;i<=10;i++)
{
if (i==3) continue;
x=x + "The number is " + i + "<br>";
}
```

关于 JavaScript 标签与 break 和 continue 一起使用的理解。

**break 的作用是跳出代码块**, 所以 break 可以使用于循环和 switch 等

continue 的作用是进入下一个迭代, **所以 continue 只能用于循环的代码块**。

代码块: 基本上是｛｝大括号之间

1. 默认标签的情况（除了默认标签情况，其他时候必须要有名标签，否则会有惊喜）

当 break 和 continue 同时用于循环时，没有加标签，此时默认标签为当前"循环"的代码块。

当 break 用于 switch 时，默认标签为当前的 switch 代码块



有了标签，可以使用break和continue在多层循环的时候控制外层循环。

#### 17 JavaScript typeof, null, 和 undefined



##### typeof 操作符

你可以使用 typeof 操作符来检测变量的数据类型。

```javascript
typeof "John"                // 返回 string 
typeof 3.14                  // 返回 number
typeof false                 // 返回 boolean
typeof [1,2,3,4]             // 返回 object
typeof {name:'John', age:34} // 返回 object
```

 在JavaScript中，数组是一种特殊的对象类型。 因此 typeof [1,2,3,4] 返回 object。 

##### null

在 JavaScript 中 null 表示 "什么都没有"。

null是一个只有一个值的特殊类型。表示一个空对象引用。

用 typeof 检测 null 返回是object。

你可以设置为 null 来清空对象:

```javascript
var person = null;           // 值为 null(空), 但类型为对象
```

你可以设置为 undefined 来清空对象:

```javascript
  var person = undefined;     // 值为 undefined, 类型为 undefined
```

#####   undefined

在 JavaScript 中, **undefined** 是一个没有设置值的变量。

**typeof** 一个没有值的变量会返回 **undefined**。

```javascript
var person;                  // 值为 undefined(空), 类型是undefined
```

任何变量都可以通过设置值为 **undefined** 来清空。 类型为 **undefined**.

```javascript
person = undefined;          // 值为 undefined, 类型是undefined
```

#####   undefined 和 null 的区别

```javascript
null 和 undefined 的值相等，但类型不等：

typeof undefined             // undefined
typeof null                  // object
null === undefined           // false
null == undefined            // true
```

##### 笔记

**1、定义**

-  （1）undefined：是所有没有赋值变量的默认值，自动赋值。
-  （2）null：主动释放一个变量引用的对象，表示一个变量不再指向任何对象地址。

**2、何时使用null?**

当使用完一个比较大的对象时，需要对其进行释放内存时，设置为 null。

**3、null 与 undefined 的异同点是什么呢？**

**共同点**：都是原始类型，保存在栈中变量本地。

不同点：

（1）undefined——表示变量声明过但并未赋过值。

它是所有未赋值变量默认值，例如：

```javascript
var a;    // a 自动被赋值为 undefined
```

（2）null——表示一个变量将来可能指向一个对象。

一般用于主动释放指向对象的引用，例如：

```javascript
var emps = ['ss','nn'];
emps = null;     // 释放指向数组的引用
```

4、延伸——垃圾回收站

它是专门释放对象内存的一个程序。

-  （1）在底层，后台伴随当前程序同时运行；引擎会定时自动调用垃圾回收期；
-  （2）总有一个对象不再被任何变量引用时，才释放。

####   18 JavaScript 类型转换

Number() 转换为数字， String() 转换为字符串， Boolean() 转化为布尔值。

##### JavaScript 数据类型

在 JavaScript 中有 5 种不同的数据类型：

- string
- number
- boolean
- object
- function

3 种对象类型：

- Object
- Date
- Array

2 个不包含任何值的数据类型：

- null
- undefined

------

##### typeof 操作符

你可以使用 **typeof** 操作符来查看 JavaScript 变量的数据类型。

```javascript
typeof "John"                 // 返回 string 
typeof 3.14                   // 返回 number
typeof NaN                    // 返回 number
typeof false                  // 返回 boolean
typeof [1,2,3,4]              // 返回 object
typeof {name:'John', age:34}  // 返回 object
typeof new Date()             // 返回 object
typeof function () {}         // 返回 function
typeof myCar                  // 返回 undefined (如果 myCar 没有声明)
typeof null                   // 返回 object   
```

请注意：

- NaN 的数据类型是 number
- 数组(Array)的数据类型是 object
- 日期(Date)的数据类型为 object
- null 的数据类型是 object
- 未定义变量的数据类型为 undefined

如果对象是 JavaScript Array 或 JavaScript Date ，我们就无法通过 **typeof** 来判断他们的类型，因为都是 返回 object。

##### constructor 属性

```javascript
"John".constructor                 // 返回函数 String()  { [native code] }
(3.14).constructor                 // 返回函数 Number()  { [native code] }
false.constructor                  // 返回函数 Boolean() { [native code] }
[1,2,3,4].constructor              // 返回函数 Array()   { [native code] }
{name:'John', age:34}.constructor  // 返回函数 Object()  { [native code] }
new Date().constructor             // 返回函数 Date()    { [native code] }
function () {}.constructor         // 返回函数 Function(){ [native code] }
```

你可以使用 constructor 属性来查看对象是否为数组 (包含字符串 "Array"):

```javascript
function isArray(myArray) {
    return myArray.constructor.toString().indexOf("Array") > -1;
}
```

你可以使用 constructor 属性来查看对象是否为日期 (包含字符串 "Date"):

```javascript
function isDate(myDate) {
    return myDate.constructor.toString().indexOf("Date") > -1;
}
```

##### JavaScript 类型转换

JavaScript 变量可以转换为新变量或其他数据类型：

- 通过使用 JavaScript 函数
- 通过 JavaScript 自身自动转换

##### 将数字转换为字符串

全局方法 **String()** 可以将数字转换为字符串。

该方法可用于任何类型的数字，字母，变量，表达式：

###### 实例

```javascript
String(x)         // 将变量 x 转换为字符串并返回
String(123)       // 将数字 123 转换为字符串并返回
String(100 + 23)  // 将数字表达式转换为字符串并返回
```

Number 方法 **toString()** 也是有同样的效果。

###### 实例

```javascript
x.toString()
(123).toString()
(100 + 23).toString()
```

在 [Number 方法](http://www.runoob.com/jsref/jsref-obj-number.html) 章节中，你可以找到更多数字转换为字符串的方法：

#####   将布尔值转换为字符串

全局方法 **String()** 可以将布尔值转换为字符串。

```javascript
String(false)        // 返回 "false"
String(true)         // 返回 "true"
```

Boolean 方法 **toString()** 也有相同的效果。

```javascript
false.toString()     // 返回 "false"
true.toString()      // 返回 "true"
```

##### 将日期转换为字符串

Date() 返回字符串。

```javascript
Date()      // 返回 Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)
//全局方法 String() 可以将日期对象转换为字符串。
String(new Date())      
// 返回 Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)
//Date 方法 toString() 也有相同的效果。
obj = new Date()
obj.toString()   // 返回 Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)
```

##### 将字符串转换为数字

全局方法 **Number()** 可以将字符串转换为数字。

字符串包含数字(如 "3.14") 转换为数字 (如 3.14).

空字符串转换为 0。

其他的字符串会转换为 NaN (不是个数字)。

```javascript
Number("3.14")    // 返回 3.14
Number(" ")       // 返回 0 
Number("")        // 返回 0
Number("99 88")   // 返回 NaN
```

##### 笔记

###### 检测数据类型：typeof 与 instanceof

typeof 用以获取一个变量或者表达式的类型，typeof 一般只能返回如下几个结果：

```javascript
number,boolean,string,function（函数）,object（NULL,数组，对象）,undefined。
```

实例：

```javascript
document.getElementById("demo").innerHTML = 
typeof "john" + "<br>" + 
typeof 3.14 + "<br>" +
typeof false + "<br>" +
typeof [1,2,3,4] + "<br>" +
typeof {name:'john', age:34};
```

我们可以使用 typeof 来获取一个变量是否存在，如 **if(typeof a!="undefined"){}**，而不要去使用 if(a) 因为如果 a 不存在（未声明）则会出错。

正因为 typeof 遇到 null,数组,对象时都会返回 object 类型，所以当我们要判断一个对象是否是数组时。

或者判断某个变量是否是某个对象的实例则要选择使用另一个关键语法 **instanceo**

可通过 instanceof 操作符来判断对象的具体类型，语法格式:

```javascript
var result = objectName instanceof objectType
```

返回布尔值，如果是指定类型返回 true，否则返回 false：

```javascript
arr = [1,2,3];
if(arr instanceof Array){
    document.write("arr 是一个数组");
} else {
    document.write("arr 不是一个数组");
}
```

###### **undefined 与 null 的区别：**

表面上 undefined 与 null 都是什么都没有的意思，但是实际上 undefined 是未定义（就是变量没有初始化），null 是一个变量初始化了，但是什么值都没给，只给了一个空对象；进一步说，undefined 与 null是值相等，类型不相等。

NaN 是一个特殊的数值，NaN 即非数值（Not a Number），这个数值用于本来要返回数值的操作数未返回数值的情况。

NaN 与任何值都不相等，包括 NaN 本身。

可以通过 isNaN() 方法来判断某个数值是否是NaN这个特殊的数，使用 isNaN() 方法会将传入的数值如果是非数值的会将其自动转换成数值类型，若能转换成数值类型，那么这个函数返回 false，若不能转换成数值类型，则这个数就是 NaN，即返回 true。

####  19正则表达式

正则表达式（英语：Regular Expression，在代码中常简写为regex、regexp或RE）使用单个字符串来**描述、匹配一系列**符合某个**句法规则的字符串搜索**模式。

搜索模式可用于文本搜索和文本替换。

> 语法：/正则表达式主体/修饰符(可选)

其中修饰符是可选的。

```javascript
var patt = /runoob/i
```

实例解析：

**/runoob/i**  是一个正则表达式。

**runoob**  是一个**正则表达式主体** (用于检索)。

**i**  是一个**修饰符** (搜索不区分大小写)。

##### 使用字符串方法

在 JavaScript 中，正则表达式通常用于两个字符串方法 : search() 和 replace()。

**search() 方法** 用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串，并返回子串的起始位置。

**replace() 方法** 用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串.

##### search() 方法使用正则表达式

```javascript
var str = "Visit Runoob!"; 
var n = str.search(/Runoob/i);//6
```

##### searh() 方法使用字符串  

```javascript
//检索字符串中 "Runoob" 的子串：
var str = "Visit Runoob!";  var n = str.search("Runoob");
```

##### replace() 方法使用正则表达式

使用正则表达式且不区分大小写将字符串中的 Microsoft 替换为 Runoob :

```javascript
var str = document.getElementById("demo").innerHTML;  
var txt = str.replace(/microsoft/i,"Runoob");//Visit Runoob!
```

##### replace() 方法使用字符串

replace() 方法将接收字符串作为参数：

```javascript
var str = document.getElementById("demo").innerHTML;  
var txt = str.replace("Microsoft","Runoob");
```

正则表达式参数可用在以上方法中 **(替代字符串参数)。**
正则表达式使得**搜索功能更加强大**(如实例中不区分大小写)。

#####   正则表达式修饰符

**修饰符** 可以在**全局**搜索中**不区分大小写**:

| 饰符 | 描述                                                     |
| ---- | -------------------------------------------------------- |
| i    | 执行对大小写不敏感的匹配。                               |
| g    | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
| m    | 执行多行匹配。                                           |

##### 正则表达式模式

方括号用于查找某个范围内的字符：

| 表达式 | 描述                       |
| ------ | -------------------------- |
| [abc]  | 查找方括号之间的任何字符。 |
| [0-9]  | 查找任何从 0 至 9 的数字。 |
| (x\|y) | 查找任何以 \| 分隔的选项。 |

元字符是拥有特殊含义的字符：

| 元字符 | 描述                                        |
| ------ | ------------------------------------------- |
| \d     | 查找数字。                                  |
| \s     | 查找空白字符。                              |
| \b     | 匹配单词边界。                              |
| \uxxxx | 查找以十六进制数 xxxx 规定的 Unicode 字符。 |

量词:

| 量词 | 描述                                  |
| ---- | ------------------------------------- |
| n+   | 匹配任何包含至少一个 *n* 的字符串。   |
| n*   | 匹配任何包含零个或多个 *n* 的字符串。 |
| n?   | 匹配任何包含零个或一个 *n* 的字符串。 |

##### 使用 RegExp 对象

在 JavaScript 中，RegExp 对象是一个预定义了属性和方法的正则表达式对象。

##### 使用 test()

test() 方法是一个正则表达式方法。

test() 方法用于检测一个字符串是否匹配某个模式，如果字符串中含有匹配的文本，则返回 true，否则返回 false。

以下实例用于搜索字符串中的字符 "e"：

```javascript
var patt = /e/;
patt.test("The best things in life are free!");
//简化版
/e/.test("The best things in life are free!")
```

##### 使用 exec()

exec() 方法是一个正则表达式方法。

exec() 方法用于检索字符串中的正则表达式的匹配。

该函数返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null。

以下实例用于搜索字符串中的字母 "e":

Example 1

```javascript
/e/.exec("The best things in life are free!");
```

字符串中含有 "e"，所以该实例输出为:

e

##### 笔记

```javascript
/*是否带有小数*/
function    isDecimal(strValue )  {  
   var  objRegExp= /^\d+\.\d+$/;
   return  objRegExp.test(strValue);  
}  

/*校验是否中文名称组成 */
function ischina(str) {
    var reg=/^[\u4E00-\u9FA5]{2,4}$/;   /*定义验证表达式*/
    return reg.test(str);     /*进行验证*/
}

/*校验是否全由8位数字组成 */
function isStudentNo(str) {
    var reg=/^[0-9]{8}$/;   /*定义验证表达式*/
    return reg.test(str);     /*进行验证*/
}

/*校验电话码格式 */
function isTelCode(str) {
    var reg= /^((0\d{2,3}-\d{7,8})|(1[3584]\d{9}))$/;
    return reg.test(str);
}

/*校验邮件地址是否合法 */
function IsEmail(str) {
    var reg=/^\w+@[a-zA-Z0-9]{2,10}(?:\.[a-z]{2,4}){1,3}$/;
    return reg.test(str);
}
```

[参考文献]: http://www.runoob.com/js/js-regexp.html

#### 20 JavaScript 错误 - throw、try 和 catch

**try** 语句测试代码块的错误。

**catch** 语句处理错误。

**throw** 语句创建自定义错误。

**finally** 语句在 try 和 catch 语句之后，无论是否有触发异常，该语句都会执行。

#####  JavaScript 错误

当 JavaScript 引擎执行 JavaScript 代码时，会发生各种错误。

可能是**语法错误**，通常是程序员造成的编码错误或错别字。

可能是**拼写错误**或语言中缺少的功能（可能由于浏览器差异）。

可能是由于来自**服务器或用户的错误输出**而导致的错误。

##### JavaScript 抛出（throw）错误

当错误发生时，当事情出问题时，JavaScript 引擎通常会停止，并生成一个错误消息。

描述这种情况的技术术语是：JavaScript 将**抛出**一个错误。

**try** 语句允许我们定义在执行时进行错误测试的代码块。

**catch** 语句允许我们定义当 try 代码块发生错误时，所执行的代码块。

JavaScript 语句 **try** 和 **catch** 是成对出现的。

```javascript
try {
...    //异常的抛出
} catch(e) {
...    //异常的捕获与处理
} finally {
...    //结束处理
}
```

##### finally 语句

finally 语句不论之前的 try 和 catch 中是否产生异常都会执行该代码块。

```javascript
function myFunction() {
var message, x;
message = document.getElementById("p01");
message.innerHTML = "";
x = document.getElementById("demo").value;
try { 
if(x == "") throw "值是空的";
if(isNaN(x)) throw "值不是一个数字";
x = Number(x);
if(x > 10) throw "太大";
if(x < 5) throw "太小";
}
catch(err) {
message.innerHTML = "错误: " + err + ".";
}
finally {
document.getElementById("demo").value = "";
}
}
```

##### Throw 语句

throw 语句允许我们创建自定义错误。

正确的技术术语是：创建或**抛出异常**（exception）。

如果把 throw 与 try 和 catch 一起使用，那么您能够控制程序流，并生成自定义的错误消息。

##### 语法

```javascript
throw exception	//异常可以是 JavaScript 字符串、数字、逻辑值或对象。
```

本例检测输入变量的值。如果值是错误的，会抛出一个异常（错误）。catch 会捕捉到这个错误，并显示一段自定义的错误消息：

```javascript
function myFunction() {
var message, x;
message = document.getElementById("message");
message.innerHTML = "";
x = document.getElementById("demo").value;
try { 
if(x == "")  throw "值为空";
if(isNaN(x)) throw "不是数字";
x = Number(x);
if(x < 5)    throw "太小";
if(x > 10)   throw "太大";
}
catch(err) {
message.innerHTML = "错误: " + err;
}
}
```

#### 21  变量提升

JavaScript 中，函数及变量的声明都将被提升到函数的最顶部。

JavaScript 中，变量可以在使用后声明，也就是变量可以先使用再声明

```javascript
  x = 5; // 变量 x 设置为 5

elem = document.getElementById("demo"); // 查找元素 
elem.innerHTML = x;                     // 在元素中显示 x

var x; // 声明 x  
```

```javascript
  x = 5; // 变量 x 设置为 5

elem = document.getElementById("demo"); // 查找元素 
elem.innerHTML = x;                     // 在元素中显示 x

var x; // 声明 x  
```

此上两个程序结果一致

变量提升：函数声明和变量声明总是会被解释器悄悄地被"提升"到方法体的最顶部。

##### JavaScript 初始化不会提升

JavaScript 只有声明的变量会提升，初始化的不会。

以下两个实例结果结果不相同：