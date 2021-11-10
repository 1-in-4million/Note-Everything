[TOC]
# JavaSctipt简介
## 初识JavaScript
```
1.Js是一种函数优先的轻量级，解释型或即时编译型的编程语言；
2.函数优先(First-class functions):
指该语言中函数可以和其他任何变量一样对待;
3.JavaScript 的标准是 ECMAScript ;
4.JavaScript与Java编程语言并不一样；
5.；换行
```
## 引入JS
```
HTML 中的脚本必须位于 <script> 与 </script> 标签之间，
脚本可被放置在 HTML 页面的 <body> 和 <head> 部分中；

HTML页面嵌入：
   <script type="text/javascript">
        alert("源栈欢迎你！");
    </script>
type=...可以省略，Js已经已经是公共的默认脚本语言；
引用.js文件：
<script src="~/js/site.js" type="text/javascript"></script>
外部脚本不能包含<script>标签
Q:用嵌入还是引用？
A:仅供单个页面使用，嵌入；多个页面共用，引用
Q:js代码放在头部还是底部
A:流行放在</body>前面，以便优先加载非JS内容

MSDN示例：
Html引入：<script src="scripts/main.js" defer></script>
main.js文件夹写入：
let myHeading = document.querySelector('h1');
myHeading.textContent = 'Hello world!';
1.使用querySelector获取标题的引用；
2.储存在myHeading变量中；
3.修改文本内容;
4.defer:
它告诉浏览器Script段包含了无需立即执行的代码;
与SRC属性联合使用;
使这些脚本在后台被下载，前台的内容则正常显示给用户。
```
# JavaScript输出
## snippet
`
Chrome自带的一个小脚本(source下面)
`
## 弹出框
### Alert()
`
警告框  alert("我是一个警告框！");
`
### Confirm()
```
确定返回true，取消返回false；
var r = confirm("请按按钮");
if (r == true) {
    x = "您按了确认！";
} else {
    x = "您按了取消！";
}
```
### Prompt()
```
确定返回输入值；取消返回null值；
var person = prompt("请输入您的姓名", "比尔盖茨");
if (person != null) {
    document.getElementById("demo").innerHTML = "你好 " 
    + person + "！今天过的怎么样？";
}
```
## document.write()
`
将内容写到 HTML 文档中
`
##  innerHTML
`
将内容写到Html元素
`
## 换行
```
使用转义字符\n  \r；
添加文本    <br>
```
## 空格
```
1.&nbsp：
document.write("&nbsp;&nbsp;"+"1"+"&nbsp;&nbsp;&nbsp;&nbsp;"+"23");
2.使用CSS标签"white-space:pre";：
document.write("<span style=' white-space:pre;'>
"+"  1        2    3    "+"</span>");
```
# JavsScript语法
## 变量
```
let myVariable = '李雷';
1.关键字let或者var；
2.Js对大小写敏感；
3.可以直接通过变量名获取变量的值：myVariable；
4.变量在赋值后是可以修改的
```
### 变量提升
```
1.Js会在执行时把所有的变量声明提升到代码的顶部(赋值没有提升)；
2.Js会在变量声明时给一个undefined的值
```
### "User Strict"(严格模式)
```
严格模式通过在脚本或函数的头部添加"use strict"; 表达式来声明;
可以应用到整个脚本或个别函数中;
严格模式下不能使用未声明的变量.
```
### let&var
`
let不支持变量提升，推荐使用let；
`
### Object对象
```
本质上是一组键值对组成的无序集合
var person = {
    firstName:"John",
    lastName:"Doe",
    age:50,
    eyeColor:"blue"
};
或者
var  age='21';
var obj={age};
可以使用 . 或者[ ]访问对象属性；
，分隔  ：赋值
```
### Undefined和null
```
typeof undefined             // undefined
typeof null                  // object
null === undefined           // false
null == undefined            // true

undefined：是所有没有赋值变量的默认值，自动赋值；
null：主动释放一个变量引用的对象，表示一个变量不再指向任何对象地址；

undefined——表示变量声明过但并未赋过值；
null——表示一个变量将来可能指向一个对象，一般用于主动释放指向对象的引用。
```
## ESLint
`
检测Js错误的插件
`
## 数据类型及相关
### 基本类型-总
```
在 JavaScript 中有 6 种不同的数据类型：
string
number
boolean
object
function
symbol

3 种对象类型：
Object
Date
Array

2 个不包含任何值的数据类型：
null
undefined
```
### 基本类型-分
```
String  单双皆可；
Number:
1.科学计数法 986e-2 => 9.86；
2.NAN(Not A N)；
3.字母lnfinity表示无穷大，加一个  - 表示无穷小;
Array：[ ]；引用[0]...
Object: 对象：JavaScript 里一切皆对象，一切皆可储存在变量里；
可以使用typeof查看类型
```
### 值类型&引用类型
```
值类型：非object，包括string；
引用类型：object；

不管是值类型还是引用类型，变量都是存放在栈中;
只是：
（在栈中的）值类型变量直接（在栈中）存放值；
引用类型变量仍然在栈中，但它引用的对象存放在堆中.
```
### 弱类型
```
JavaScript是一种弱/动态类型语言。
所谓“弱”类型，不是“没”类型，而是“不严格要求”类型匹配;
所谓“动态”类型，是指变量的类型可以“动态”的变化;
表现为：一个变量可以被多种类型的值赋值.
```
### Construtor属性
```
constructor 属性返回所有 JavaScript 变量的构造函数:

"John".constructor                 // 返回函数 String()  { [native code] }
(3.14).constructor                 // 返回函数 Number()  { [native code] }
false.constructor                  // 返回函数 Boolean() { [native code] }
[1,2,3,4].constructor              // 返回函数 Array()   { [native code] }
{name:'John', age:34}.constructor  // 返回函数 Object()  { [native code] }
new Date().constructor             // 返回函数 Date()    { [native code] }
function () {}.constructor         // 返回函数 Function(){ [native code] }
```
#### 查看对象是否为数组
```
<p id="demo"></p>
<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = isArray(fruits);
function isArray(myArray) {
    return myArray.constructor.toString().indexOf("Array") > -1;
}
</script>
```
## 神奇的运算
### 运算符
```
加减乘除    + - * /
赋值    :
等于和不等于    == 和  !=
取反    !
取余    %
```
### IsNaN
```
NaN和所有数（包括它自己，除非NaN !=NaN）的所有比较，结果都为false
如果判断一个值是不是NaN？只能用函数 isNaN(）
```
### 严格比较===
`
如果不是同一种类型，马上为false：还有!==
`
### 类型转换hack
```
数值变成字符串： 86+''
字符串变成数字：+'86' ，能转的就转，不能转的NaN.
```
## 分支/循环/数组
```
let iceCream = 'chocolate';
if (iceCream === 'chocolate') {
  alert('我最喜欢巧克力冰激淋了。');
} else {
  alert('但是巧克力才是我的最爱呀……');
}

for...in    遍历对象属性

do
{
    x=x + "The number is " + i + "<br>";
    i++;
}
while (i<5);
//do...while至少执行一次，返回为真重复执行；

二维数组：
    var students = [
        ['gty', 'lw', 'zdh', 'lzb'],
        ['lgy', 'ht', 'zl']
    ];    //数组students里有两个元素，每个元素又都是一个数组
    console.log(students[0][1]);  //0排第1个元素：lw
```
## 函数/方法
### 命名函数
```
function getFirst(numbers) {
    return numbers[0];
}
```
### 匿名函数
```
将函数本身赋值给一个变量：
var getFirst = function (numbers) {
    return numbers[0];
}([3, 8, -1, true]);
```
### 方法
```
在对象中声明的函数通常被称为方法：
var wpz = {
    name: '王胖子',
    study: function () {
        alert('好好学习天天向上');
    }
};
wpz.study();    //用对象调用方法
调用可以放在点击事件里;
同名函数会调用最后一个覆盖前面的执行.
```
### 规则
```
1.以命名方式声明的函数也可以提升；
2.调用Js的函数，语法上不要求参数匹配：
没有类型限制，所以就不存在类型匹配
也可以多于或少于定义时的参数个数
```
### Arguments
```
在函数内部获得未声明的参数；
Js有一个Arguments：
1.可以获得传入的(非定义)所有参数；
2.类似于Array；
3.只能在函数内部使用；

示例：
 function sum() {
    var sum = 0;
    for (var i = 0; i < arguments.length; i++) {
            sum += arguments[i];
    }
    return sum;
 }
```
### 作用域
#### 局部变量
```
如果一个变量在函数体内部（用var）声明，
则该变量的作用域为整个函数体，在函数体外不可引用该变量；
不同函数内部的同名变量互相独立，互不影响。
```
#### 全局变量污染
```
不在任何函数内定义的变量具有全局作用域；
随着JavaScript规模扩大，一个项目可能引用多个
（第三方/其他人写的）类库（js文件）；
各个文件间的名称冲突就越来越难以避免，给开发/维护带来极大的问题！

JavaScript会沿着这个链条由内向外查找，直到undefined。
```
#### 变量生命周期
```
局部变量在函数执行完毕后销毁,
全局变量在页面关闭后销毁.
```
#### IIFE
```
默认'use strict'作用域为<script>块或者一个js文件，
可以声明在函数内部.

Immediately invoked function expression:
用(   )包裹函数function，再加个( )立即调用:
1.减少全局变量域污染;
2.不需要给方法命名;
3.能够获得函数中的一些属性.
```
### 自调用函数
```
(function () {
    var x = "Hello!!";      // 我将调用自己
})();

不能自调用声明的函数。

通过添加括号，来说明它是一个函数表达式;
以上函数实际上是一个 匿名自我调用的函数 (没有函数名).
```
### 回调函数
```

```
## 内置
### 包装类
```
var n = new Number(123);
1.在类型前面使用关键字/运算符 new;
2.类型后面添加一对圆括号;
3.圆括号中传入一个相应的值.

得到一个相应的对象,可以按基本类型变量使用：
new Number(123) -23        //100

typeof new Number(123)     //Object 
```
### 数组
```
indexOf()：获取下标，-1表示没有找到
slice()：同string的substring()
shift() 和 unshift()：从数组头部 删除/添加 元素

sort() 和 reverse():
array.sort(fun)；
1.没有使用参数,则按照字符编码的顺序进行排序；
2.参数fun可选。规定排序顺序,必须是函数;
返回a-b 升序，返回b-a 降序
示例：
1.传入参数，实现升序，降序；
var arr3 = [30,10,111,35,1899,50,45];
arr3.sort(function(a,b){
	return a - b;
})
console.log(arr3);//输出  [10, 30, 35, 45, 50, 111, 1899]
		
var arr4 = [30,10,111,35,1899,50,45];
rr4.sort(function(a,b){
	return b - a;
})
console.log(arr4);//输出 [1899, 111, 50, 45, 35, 30, 10]
2.根据数组中的对象的多个属性值排序，多条件排序；
var arr6 = [{id:10,age:2},{id:5,age:4},{id:6,age:10},
{id:9,age:6},{id:2,age:8},{id:10,age:9}];
arr6.sort(function(a,b){
if(a.id === b.id){  //如果id相同，按照age的降序
	return b.age - a.age
}else{
		return a.id - b.id
        }
})
console.log(arr6);
//输出新的排序：
//		{id: 2, age: 8}
//		{id: 5, age: 4}
//		{id: 6, age: 10}
//		{id: 9, age: 6}
//		{id: 10, age: 9}
//		{id: 10, age: 2}
```
### Math
```
abs()：取绝对值
取整：
ceil()：向上取整
floor()：向下取整
round()：四舍五入取整
random()：会生成一个小于1的随机小数;

得到1000以内的随机正整数：
Math.ceil(Math.random()*1000)

四舍五入到n位小数位，toFixed(n)-返回的是字符串：
7.654.toFixed(2)   //7.65
7.658.toFixed(2)   //7.66

parseInt() / parseFloat()
将其他类型数据转换成整数（int）或x小数（float）类型
还可以选择进制，比如将100101按二进制转换成10进制整数：
parseInt('100101', 2)
```
### Date
```
系统当前日期：new Date()

new Date().getFullYear()    //得到当前年份getYear()不行

new Date('2021/4/24').getMonth()  //3，js月份从0开始计数

set可用于修改日期；
```
### 字符串
`
同C#
`
# RegExp
## 简介
```
Regular Expression;
使用单个字符串来描述、匹配一系列符合某个句法规则的字符串搜索模式;
可用于所有文本搜索和文本替换的操作。
```
## 语法
```
var patt = /runoob/i
/正则表达式主体/修饰符(可选，不区分大小写)
```
### 正则表达式修饰符
`
修饰符 可以在全局搜索中不区分大小写:
`
修饰符 | 描述
---- | -----
i   |执行对大小写不敏感的匹配
g	|执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）
m	|执行多行匹配
### 正则表达式模式
#### 表达式
`
方括号用于查找某个范围内的字符：
`
表达式 | 描述
---- | -----
[abc]	|查找方括号之间的任何字符
[0-9]	|查找任何从 0 至 9 的数字
(x\|y)	|查找任何以\|分隔的选项
#### 元字符
`
元字符是拥有特殊含义的字符：
`
元字符 | 描述
---- | -----
\d	|查找数字
\s	|查找空白字符
\b	|匹配单词边界
\uxxxx	|查找以十六进制数 xxxx 规定的 Unicode 字符
#### 量词
量词|描述
----|----
n+|	匹配任何包含至少一个 n 的字符串
n*|	匹配任何包含零个或多个 n 的字符串
n?|	匹配任何包含零个或一个 n 的字符串
### RegExp对象
`
RegExp 对象是一个预定义了属性和方法的正则表达式对象。
`
#### test()
```
用于检测一个字符串是否匹配某个模式，如果字符串中含有匹配的文本，则返回 true，否则返回 false。

var patt = /e/;
patt.test("The best things in life are free!");
也可以不用变量.
```
#### exec()
```
用于检索字符串中的正则表达式的匹配;
返回一个数组，存放匹配的结果；未找到匹配，则返回值为 null.
```
## 字符串方法
### search() 
```
用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串，并返回子串的起始位置。

var str = "Visit Runoob!"; 
var n = str.search(/Runoob/i);
//output:6
```
### replace()
```
用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。
var str = document.getElementById("demo").innerHTML; 
var txt = str.replace("Microsoft","Runoob");
```
# Exception
## Try...catch...finally
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<p>不管输入是否正确，输入框都会再输入后清空。</p>
<p>请输入 5 ~ 10 之间的数字：</p>

<input id="demo" type="text">
<button type="button" onclick="myFunction()">点我</button>

<p id="p01"></p>

<script>
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
</script>

</body>
</html>
```
## 调试
`
debugger关键字；  用于停止执行 JavaScript，并调用调试函数。
`
# BOM
## 浏览器对象模型
`
Browser Object Model (BOM)  与浏览器"对话"
`
## Window对象
```
所有浏览器都支持 window 对象。它表示浏览器窗口；
所有 JavaScript 全局对象、函数以及变量均自动成为 window 对象的成员；
全局变量是 window 对象的属性；
全局函数是 window 对象的方法；
甚至 HTML DOM 的 document 也是 window 对象的属性之一：

window.document.getElementById("header");
```
## Windows方法
### Window Screen
```
window.innerHeight - 浏览器窗口的内部高度(包括滚动条)
window.innerWidth - 浏览器窗口的内部宽度(包括滚动条)

screen.availWidth - 可用的屏幕宽度
screen.availHeight - 可用的屏幕高度

location.href 属性返回当前页面的 URL
location.pathname 属性返回 URL 的路径名
```

### location.assign()
```
加载新的文档：
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
<script>
function newDoc(){
    window.location.assign("https://www.runoob.com")
}
</script>
</head>
<body>
<input type="button" value="加载新文档" onclick="newDoc()">
</body>
</html>
```
### Window History
#### history.back()
```
与在浏览器点击后退按钮相同:
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<head>
<script>
function goBack()
{
    window.history.back()
}
</script>
</head>
<body>
 
<input type="button" value="Back" onclick="goBack()">
 
</body>
</html>
```
#### history.forward()
```
与在浏览器中点击向前按钮相同:
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<script>
function goForward()
{
    window.history.forward()
}
</script>
</head>
<body>
 
<input type="button" value="Forward" onclick="goForward()">
 
</body>
</html>
```
### Window Navigator
```
包含有关访问者浏览器的信息：
<script>
txt = "<p>浏览器代号: " + navigator.appCodeName + "</p>";
txt+= "<p>浏览器名称: " + navigator.appName + "</p>";
txt+= "<p>浏览器版本: " + navigator.appVersion + "</p>";
txt+= "<p>启用Cookies: " + navigator.cookieEnabled + "</p>";
txt+= "<p>硬件平台: " + navigator.platform + "</p>";
txt+= "<p>用户代理: " + navigator.userAgent + "</p>";
txt+= "<p>用户代理语言: " + navigator.language + "</p>";
document.getElementById("example").innerHTML=txt;
</script>

navigator 对象的信息具有误导性，不应该被用于检测浏览器版本！
```
## 计时事件 
`
一个设定的时间间隔之后来执行代码
`
### setInterval()
`
间隔指定的毫秒数不停地执行指定的代码
`
#### 实例一
```
1000 毫秒是一秒;
每3s弹出一次.

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>单击按钮每3秒出现一个“Hello”警告框。</p>
<p>再次点击警告框，经过3秒出现新的警告框，这将一直执行 ...</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	setInterval(function(){alert("Hello")},3000);
}
</script>

</body>
</html>
```
#### 实例二
```
显示当前时间;
每秒执行一次.

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>在页面显示一个时钟</p>
<p id="demo"></p>
<script>
var myVar=setInterval(function(){myTimer()},1000);
function myTimer(){
	var d=new Date();
	var t=d.toLocaleTimeString();
	document.getElementById("demo").innerHTML=t;
}
</script>

</body>
</html>
```
#### clearInterval()
`
用于停止 setInterval() 方法执行的函数代码.
`
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>页面上显示时钟：</p>
<p id="demo"></p>
<button onclick="myStopFunction()">停止</button>
<script>
var myVar=setInterval(function(){myTimer()},1000);
function myTimer(){
	var d=new Date();
	var t=d.toLocaleTimeString();
	document.getElementById("demo").innerHTML=t;
}
function myStopFunction(){
	clearInterval(myVar);
}
</script>

</body>
</html>
```
### setTimeout()
```
多少秒之后执行：
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>点击按钮，在等待 3 秒后弹出 "Hello"。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	setTimeout(function(){alert("Hello")},3000);
}
</script>

</body>
</html>
```
#### clearTimeout()
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>点击第一个按钮等待3秒后出现"Hello"弹框。</p>
<p>点击第二个按钮来阻止第一个函数运行。（你必须在3秒之前点击它）。</p>
<button onclick="myFunction()">点我</button>
<button onclick="myStopFunction()">停止弹框</button>
<script>
var myVar;
function myFunction(){
	myVar=setTimeout(function(){alert("Hello")},3000);
}
function myStopFunction(){
	clearTimeout(myVar);
}
</script>

</body>
</html>
```
### Cookie
## 什么是Cookie？
```
Cookie 是一些数据, 存储于你电脑上的文本文件中。

当 web 服务器向浏览器发送 web 页面时，在连接关闭后，服务端不会记录用户的信息。

Cookie 的作用就是用于解决 "如何记录客户端的用户信息":

当用户访问 web 页面时，他的名字可以记录在 cookie 中。
在用户下一次访问该页面时，可以在 cookie 中读取用户访问记录。
Cookie 以名/值对形式存储，如下所示:

username=John Doe
当浏览器从服务器上请求 web 页面时，属于该页面的 cookie 会被添加到该请求中。
服务端通过这种方式来获取用户的信息。
```
## 使用Cookie
```
创建：
document.cookie="username=John Doe";

可以为 cookie 添加一个过期时间（以 UTC 或 GMT 时间）。默认情况下，cookie 在浏览器关闭时删除：
document.cookie="username=John Doe; expires=Thu, 18 Dec 2043 12:00:00 GMT";

您可以使用 path 参数告诉浏览器 cookie 的路径。默认情况下，cookie 属于当前页面。
document.cookie="username=John Doe; expires=Thu, 18 Dec 2043 12:00:00 GMT; path=/";

读取：
var x = document.cookie;

修改：
修改 cookie 类似于创建 cookie；旧的 cookie 将被覆盖；

删除：
只需要设置 expires 参数为以前的时间即可；
```
## Cookie实例
```
设置-获取-检测
function setCookie(cname,cvalue,exdays){
    var d = new Date();
    d.setTime(d.getTime()+(exdays*24*60*60*1000));
    var expires = "expires="+d.toGMTString();
    document.cookie = cname+"="+cvalue+"; "+expires;
}
function getCookie(cname){
    var name = cname + "=";
    var ca = document.cookie.split(';');
    for(var i=0; i<ca.length; i++) {
        var c = ca[i].trim();
        if (c.indexOf(name)==0) { return c.substring(name.length,c.length); }
    }
    return "";
}
function checkCookie(){
    var user=getCookie("username");
    if (user!=""){
        alert("欢迎 " + user + " 再次访问");
    }
    else {
        user = prompt("请输入你的名字:","");
          if (user!="" && user!=null){
            setCookie("username",user,30);
        }
    }
}
```
# DOM
## 文档对象模型
```
Document Object Model 
当网页被加载时，浏览器会创建页面的文档对象模型
```
## DOM树
```
元素（element）：文档中的都有标签都是元素，元素可以看成是对象
节点（node）：文档中都有的内容都是节点：标签，属性，文本
文档（document）：一个页面就是一个文档
```
### 查找HTML元素
```
通过使用元素的id：
var x=document.getElementById("intro");

通过标签名查找 HTML 元素：
var x=document.getElementById("main");
var y=x.getElementsByTagName("p");

通过类名找到 HTML 元素：
var x=document.getElementsByClassName("intro");
```
### 改变HTML
#### 改变输出流
```
document.write() 可用于直接向 HTML 输出流写内容;
不要在文档(DOM)加载完成之后使用 document.write(),这会覆盖该文档。
```
#### 改变HTML内容
```
document.getElementById("p1").innerHTML="新文本!";
```
#### 改变属性
```
document.getElementById(id).attribute=新属性值
document.getElementById("image").src="landscape.jpg";
```
### 改变CSS
#### 改变HTML元素的样式
```
document.getElementById(id).style.property=新样式

document.getElementById("p2").style.color="blue";
document.getElementById("p2").style.fontFamily="Arial";
document.getElementById("p2").style.fontSize="larger";
```
## DOM事件
### 示例
#### 改变字体颜色
```
<h1 id="id1">我的标题 1</h1>
<button type="button" onclick="document.getElementById('id1').style.color='red'">
点我!</button>
```
#### 隐藏文本
```
<p id="p1">这是一个文本。 这是一个文本。 这是一个文本。 这是一个文本。 这是一个文本。 这是一个文本。 这是一个文本。</p>
<input type="button" value="隐藏文本" onclick="document.getElementById('p1').style.visibility='hidden'" />
<input type="button" value="显示文本" onclick="document.getElementById('p1').style.visibility='visible'" />
```
### HTML DOM
#### 示例一
```
从事件处理器调用一个函数：
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<script>
function changetext(id){
	id.innerHTML="Ooops!";
}
</script>
</head>
<body>

<h1 onclick="changetext(this)">点击文本!</h1>

</body>
</html>
```
#### HTML事件属性
##### 使用 HTML DOM 分配事件
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
</head>
<body>

<p>点击按钮执行 <em>displayDate()</em> 函数.</p>
<button id="myBtn">点这里</button>
<script>
document.getElementById("myBtn").onclick=function(){displayDate()};
function displayDate(){
	document.getElementById("demo").innerHTML=Date();
}
</script>
<p id="demo"></p>

</body>
</html>

名为 displayDate 的函数被分配给 id="myBtn" 的 HTML 元素。
```
##### onload 和 onunload 事件
```
onload 和 onunload 事件会在用户进入或离开页面时被触发;
onload 事件可用于检测访问者的浏览器类型和浏览器版本，
并基于这些信息来加载网页的正确版本:
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body onload="checkCookies()">

<script>
function checkCookies(){
	if (navigator.cookieEnabled==true){
		alert("Cookies 可用")
	}
	else{
		alert("Cookies 不可用")
	}
}
</script>
<p>弹窗-提示浏览器 cookie 是否可用。</p>
	
</body>
</html
```
##### onchange 事件
```
onchange 事件常结合对输入字段的验证来使用;
当用户改变输入字段的内容时，会调用 upperCase() 函数:
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<script>
function myFunction(){
	var x=document.getElementById("fname");
	x.value=x.value.toUpperCase();
}
</script>
</head>
<body>

输入你的名字: <input type="text" id="fname" onchange="myFunction()">
<p>当你离开输入框后，函数将被触发，将小写字母转为大写字母。</p>

</body>
</html>
```
##### onmouseover 和 onmouseout 事件
```
onmouseover 和 onmouseout 事件可用于在用户的鼠标移至 HTML 元素上方或移出元素时触发函数:

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<div onmouseover="mOver(this)" onmouseout="mOut(this)" style="background-color:#D94A38;width:120px;height:20px;padding:40px;">Mouse Over Me</div>
<script>
function mOver(obj){
	obj.innerHTML="Thank You"
}
function mOut(obj){
	obj.innerHTML="Mouse Over Me"
}
</script>

</body>
</html>
```
##### onmousedown/onmouseup 事件
```
点击/释放鼠标时触发事件

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<script>
function lighton(){
	document.getElementById('myimage').src="bulbon.gif";
}
function lightoff(){
	document.getElementById('myimage').src="bulboff.gif";
}
</script>
</head>

<body>
<img id="myimage" onmousedown="lighton()" onmouseup="lightoff()" src="bulboff.gif" width="100" height="180" />
<p>点击不释放鼠标灯将一直亮着!</p>
</body>
</html>
```
##### onfocus/onfocusout 事件
```
获得/失去焦点触发事件：

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<script>
function myFunction(x){
	x.style.background="yellow";
}
	function myFunction1(x){
		x.style.background="white";
	}
</script>
</head>
<body>

输入你的名字: <input type="text" onfocus="myFunction(this)"onfocusout="myFunction1(this)">
<p>当输入框获取焦点时，修改背景色（background-color属性） 将被触发，失去焦点恢复。</p>

</body>
</html>
```
### EventListener
#### addEventListener() 方法
##### 示例
```
点击按钮时触发监听事件：

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>该实例使用 addEventListener() 方法在按钮中添加点击事件。 </p>
<button id="myBtn">点我</button>
<p id="demo"></p>
<script>
document.getElementById("myBtn").addEventListener("click", displayDate);
function displayDate() {
    document.getElementById("demo").innerHTML = Date();
}
</script>

</body>
</html>
```
##### 语法
```
element.addEventListener(event, function, useCapture);

第一个参数是事件的类型 (如 "click" 或 "mousedown");
第二个参数是事件触发后调用的函数;
第三个参数是个布尔值用于描述事件是冒泡还是捕获。该参数是可选的.
```
##### 向原元素添加事件句柄
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>该实例使用 addEventListener() 方法在按钮中添加点击事件。 </p>
<button id="myBtn">点我</button>
<script>
document.getElementById("myBtn").addEventListener("click", function(){
    alert("Hello World!");
});
</script>

</body>
</html>

------------------------------------------------------------------------

使用函数名，来引用外部函数：
<p>该实例使用 addEventListener() 方法在用户点击按钮时执行函数。</p>
<button id="myBtn">点我</button>
<script>
document.getElementById("myBtn").addEventListener("click", myFunction);
function myFunction() {
    alert ("Hello World!");
}
</script>
```
##### 向同一个元素中添加多个事件句柄
```
addEventListener() 方法允许向同一个元素添加多个事件，且不会覆盖已存在的事件：
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>该实例使用 addEventListener() 方法向同个按钮中添加两个点击事件。</p>
<button id="myBtn">点我</button>
<script>
var x = document.getElementById("myBtn");
x.addEventListener("click", myFunction);
x.addEventListener("click", someOtherFunction);
function myFunction() {
    alert ("Hello World!")
}
function someOtherFunction() {
    alert ("函数已执行!")
}
</script>

</body>
</html>
-----------------------------------------------------------------------

向同个元素添加不同类型的事件：
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>实例使用 addEventListener() 方法在同一个按钮中添加多个事件。</p>
<button id="myBtn">点我</button>
<p id="demo"></p>
<script>
var x = document.getElementById("myBtn");
x.addEventListener("mouseover", myFunction);
x.addEventListener("click", mySecondFunction);
x.addEventListener("mouseout", myThirdFunction);
function myFunction() {
    document.getElementById("demo").innerHTML += "Moused over!<br>"
}
function mySecondFunction() {
    document.getElementById("demo").innerHTML += "Clicked!<br>"
}
function myThirdFunction() {
    document.getElementById("demo").innerHTML += "Moused out!<br>"
}
</script>

</body>
</html>
```
##### 向 Window 对象添加事件句柄
```
重置窗口时添加事件：
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>实例在 window 对象中使用 addEventListener() 方法。</p>
<p>尝试重置浏览器的窗口触发 "resize" 事件句柄。</p>
<p id="demo"></p>
<script>
window.addEventListener("resize", function(){
    document.getElementById("demo").innerHTML = Math.random();
});
</script>

</body>
</html>
--------------------------------------------------------------

当传递参数值时，使用"匿名函数"调用带参数的函数：
<p>实例演示了在使用 addEventListener() 方法时如何传递参数。</p>
<p>点击按钮执行计算。</p>
<button id="myBtn">点我</button>
<p id="demo"></p>
<script>
var p1 = 5;
var p2 = 7;
document.getElementById("myBtn").addEventListener("click", function() {
    myFunction(p1, p2);
});
function myFunction(a, b) {
    var result = a * b;
    document.getElementById("demo").innerHTML = result;
}
</script>
无参数时调用可以直接用函数名(不需要带括号)
```
#### removeEventListener() 方法
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<style>
#myDIV {
    background-color: coral;
    border: 1px solid;
    padding: 50px;
    color: white;
}
</style>
</head>
<body>

<div id="myDIV"> div 元素添加了 onmousemove 事件句柄，鼠标在桔红色的框内移动时会显示随机数。
  <p>点击按钮移除 DIV 的事件句柄。</p>
  <button onclick="removeHandler()" id="myBtn">点我</button>
</div>
<p id="demo"></p>
<script>
document.getElementById("myDIV").addEventListener("mousemove", myFunction);
function myFunction() {
    document.getElementById("demo").innerHTML = Math.random();
}
function removeHandler() {
    document.getElementById("myDIV").removeEventListener("mousemove", myFunction);
}
</script>

</body>
</html>
```
### 事件冒泡/捕获
```
在 冒泡 中，内部元素的事件会先被触发，然后再触发外部元素，
即： <p> 元素的点击事件先触发，然后会触发 <div> 元素的点击事件。

在 捕获 中，外部元素的事件会先被触发，然后才会触发内部元素的事件，
即： <div> 元素的点击事件先触发 ，然后再触发 <p> 元素的点击事件。

可以用True/False指定
默认False-冒泡
```
## DOM元素
### appendChild()
```
要创建新的 HTML 元素 (节点)需要先创建一个元素，然后在已存在的元素中添加它，
添加到尾部：
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>
 
<script>
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);
 
var element = document.getElementById("div1");
element.appendChild(para);
</script>
```
### insertBefore()
```
将新元素添加到开始位置：
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>
 
<script>
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);
 
var element = document.getElementById("div1");
var child = document.getElementById("p1");
element.insertBefore(para, child);
</script>

insertBefore(要插入的节点，参考的节点)
```
### removeChild()
```
要移除一个元素，需要知道该元素的父元素:

<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>
 
<script>
var parent = document.getElementById("div1");
var child = document.getElementById("p1");
parent.removeChild(child);
</script>
```
### replaceChild()
```
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>
 
<script>
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);
 
var parent = document.getElementById("div1");
var child = document.getElementById("p1");
parent.replaceChild(para, child);
</script>

replaceChild(替换的节点，要替换的节点)
```
## DOM Collection/NodeList
### DOM Collection
```
getElementsByTagName() 方法返回 HTMLCollection 对象,
HTMLCollection 对象类似包含 HTML 元素的一个数组.

<h2>JavaScript HTML DOM</h2>
<p>Hello World!</p>
<p>Hello Runoob!</p>
<p id="demo"></p>

<script>
var myCollection = document.getElementsByTagName("p");
document.getElementById("demo").innerHTML = "第二个段落的内容为:<span style='color:red;'> " + myCollection[1].innerHTML + '</span>';
</script>

Length属性.

HTMLCollection 不是一个数组,可以像数组一样使用索引来获取元素，但无法使用数组的方法。
```
### NodeList
```
NodeList 对象是一个从文档中获取的节点列表 (集合) .

Length属性.

通过querySelectorAll获取列表中所有元素
var myNodelist = document.querySelectorAll("p");
var i;
for (i = 0; i < myNodelist.length; i++) {
    myNodelist[i].style.backgroundColor = "red";
}

NodeList也不是一个数组.
```
### HTML Collection 和 NodeList 区别
```
1.HTMLCollection 是 HTML 元素的集合,NodeList 是一个文档节点的集合;
2.HTMLCollection 元素可以通过 name，id 或索引来获取,NodeList 只能通过索引来获取;
3.只有 NodeList 对象有包含属性节点和文本节点.
```
# 事件
## HTML 事件
```
HTML 事件是发生在 HTML 元素上的事情；
HTML 事件可以是浏览器行为，也可以是用户行为。

<button onclick="getElementById('demo').innerHTML=Date()">现在的时间是?</button>
修改 id="demo" 元素的内容；

<button onclick="this.innerHTML=Date()">现在的时间是?</button>
修改自身元素的内容；

<button onclick="displayDate()">现在的时间是?</button>
通过事件属性调用
```
## 常见的 HTML 事件
事件 | 描述
---- | -----
onchange  |	HTML 元素改变
onclick	  | 用户点击 HTML 元素
onmouseover     |	用户在一个HTML元素上移动鼠标
onmouseout	|   用户从一个HTML元素上移开鼠标
onkeydown	|   用户按下键盘按键
onload	|   浏览器已完成页面的加载
# JavaScript表单
## 表单验证
```
表单数据经常需要使用 JavaScript 来验证其正确性：
1.验证表单数据是否为空？
2.验证输入是否是一个正确的email地址？
3.验证日期是否输入正确？
4.验证表单输入内容是否为数字型？
```
```
示例一：必填（或必选）项目
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<script>
function validateForm(){
var x=document.forms["myForm"]["fname"].value;
if (x==null || x==""){
  alert("姓必须填写");
  return false;
  }
}
</script>
</head>
<body>
	
<form name="myForm" action="demo-form.php" onsubmit="return validateForm()" method="post">
姓: <input type="text" name="fname">
<input type="submit" value="提交">
</form>
	
</body>
</html>
```
```
示例二：E-mail 验证
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<script>
function validateForm(){
	var x=document.forms["myForm"]["email"].value;
	var atpos=x.indexOf("@");
	var dotpos=x.lastIndexOf(".");
	if (atpos<1 || dotpos<atpos+2 || dotpos+2>=x.length){
		alert("不是一个有效的 e-mail 地址");
  		return false;
	}
}
</script>
</head>
<body>
	
<form name="myForm" action="demo-form.php" onsubmit="return validateForm();" method="post">
Email: <input type="text" name="email">
<input type="submit" value="提交">
</form>
	
</body>
</html>
```
## 验证API
### checkValidity()
```
如果 input 元素中的数据是合法的返回 true，否则返回 false:
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
</head>
<body>

<p>输入数字并点击验证按钮:</p>

<input id="id1" type="number" min="100" max="300" required>
<button onclick="myFunction()">验证</button>

<p>如果输入的数字小于 100 或大于300，会提示错误信息。</p>

<p id="demo"></p>

<script>
function myFunction() {
    var inpObj = document.getElementById("id1");
    if (inpObj.checkValidity() == false) {
        document.getElementById("demo").innerHTML = inpObj.validationMessage;
    } else {
        document.getElementById("demo").innerHTML = "输入正确";
    }
}

//validationMessage	浏览器错误提示信息
//willValidate	指定 input 是否需要验证
</script>

</body>
</html>
```
### Validity属性
属性 | 描述
----- |-----
customError	|设置为 true, 如果设置了自定义的 validity 信息。
patternMismatch|	设置为 true, 如果元素的值不匹配它的模式属性。
rangeOverflow	|设置为 true, 如果元素的值大于设置的最大值。
rangeUnderflow	|设置为 true, 如果元素的值小于它的最小值。
stepMismatch	|设置为 true, 如果元素的值不是按照规定的 step 属性设置。
tooLong	|设置为 true, 如果元素的值超过了 maxLength 属性设置的长度。
typeMismatch|	设置为 true, 如果元素的值不是预期相匹配的类型。
valueMissing|	设置为 true，如果元素 (required 属性) 没有值。
valid|	设置为 true，如果元素的值是合法的。
#### 实例
```
<input id="id1" type="number" min="100" required>
<button onclick="myFunction()">OK</button>
 
<p id="demo"></p>
 
<script>
function myFunction() {
    var txt = "";
    var inpObj = document.getElementById("id1");
    if(!isNumeric(inpObj.value)) {
        txt = "你输入的不是数字";
    } else if (inpObj.validity.rangeUnderflow) {
        txt = "输入的值太小了";
    } else {
        txt = "输入正确";
    }
    document.getElementById("demo").innerHTML = txt;
}
 
// 判断输入是否为数字
function isNumeric(n) {
    return !isNaN(parseFloat(n)) && isFinite(n);
}
</script>
```
# JavaScript this关键字
## 释义
```
面向对象语言中 this 表示当前对象的一个引用;
但在 JavaScript 中 this 不是固定不变的，它会随着执行环境的改变而改变:

1.在方法中，this 表示该方法所属的对象;
2.如果单独使用，this 表示全局对象;
3.在函数中，this 表示全局对象;
4.在函数中，在严格模式下，this 是未定义的(undefined);
5.在事件中，this 表示接收事件的元素;
6.类似 call() 和 apply() 方法可以将 this 引用到任何对象.
```
## 对象方法中绑定
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<h2>JavaScript <b>this</b> 关键字</h2>

<p>在实例中，<b>this</b> 指向了 fullName 方法所属的对象 person。</p>

<p id="demo"></p>

<script>
// 创建一个对象
var person = {
  firstName  : "John",
  lastName   : "Doe",
  id     : 5566,
  myFunction : function() {
    return this;
  }
};

// 显示表单数据
document.getElementById("demo").innerHTML = person.myFunction();
</script>

</body>
</html>
```
## 显示函数绑定(apply/call)
```
在 JavaScript 中函数也是对象，对象则有方法;
apply 和 call 就是函数对象的方法,他们允许切换函数执行的上下文环境（context），
即 this 绑定的对象.

如下，当使用 person2 作为参数来调用 person1.fullName 方法时, 
this 将指向 person2, 即便它是 person1 的方法：

<h2>JavaScript this 关键字</h2>
<p>实例中 <strong>this</strong> 指向了 person2，即便它是 person1 的方法:</p>
<p id="demo"></p>

<script>
var person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person2 = {
  firstName:"John",
  lastName: "Doe",
}
var x = person1.fullName.call(person2); 
document.getElementById("demo").innerHTML = x; 
</script>
```
# JavaScript:void(0)
## 语法格式
`
void 要计算一个表达式但是不返回值
`
```
void func()
javascript:void func()
```
`或者`
```
void(func())
javascript:void(func())
```
## 实例
```
以下实例中参数a将返回undefined：

<script type="text/javascript">
function getValue(){
   var a,b,c;
   a = void ( b = 5, c = 7 );
   document.write('a = ' + a + ' b = ' + b +' c = ' + c );
}
</script>
</head>
<body>
	
<p>点击以下按钮查看结果：</p>
<form>
<input type="button" value="点我" onclick="getValue();" />
</form>
```
## href="#"与href="javascript:void(0)"的区别
### 区别
```
1.# 包含了一个位置信息，默认的锚是#top 也就是网页的上端,
而javascript:void(0), 仅仅表示一个死链接;

2.在页面很长的时候会使用 # 来定位页面的具体位置，格式为：# + id。
如果要定义一个死链接使用 javascript:void(0) 
```
### 实例
```
<a href="javascript:void(0);">点我没有反应的!</a>
<a href="#pos">点我定位到指定位置!</a>
<br>
...
<br>
<p id="pos">尾部定位点</p>
```
# JSON
## 简介
```
JavaScript Object Notation

一种轻量级的数据交换格式；独立的语言 ；易于理解，
用于存储和传输数据的格式；用于服务端向网页传递数据。

JSON 格式在语法上与创建 JavaScript 对象代码是相同的，
由于它们很相似，所以 JavaScript 程序可以很容易的将 JSON 数据转换为 JavaScript 对象。
```
### Json实例
```
以下 JSON 语法定义了 sites 对象: 3 条网站信息（对象）的数组:
{"sites":[
    {"name":"Runoob", "url":"www.runoob.com"}, 
    {"name":"Google", "url":"www.google.com"},
    {"name":"Taobao", "url":"www.taobao.com"}
]}
```
## 语法
```
数据为 键/值对
数据由逗号分隔
大括号保存对象
方括号保存数组

JSON 对象保存在大括号内,
对象可以保存多个 键/值对
```
### Json字符串→JavaScript对象
```
通常我们从服务器中读取 JSON 数据，并在网页中显示数据.
var text = '{ "sites" : [' +
'{ "name":"Runoob" , "url":"www.runoob.com" },' +
'{ "name":"Google" , "url":"www.google.com" },' +
'{ "name":"Taobao" , "url":"www.taobao.com" } ]}';

var obj = JSON.parse(text);
```
### 转换实例
```
<h2>为 JSON 字符串创建对象</h2>
<p id="demo"></p>
<script>
var text = '{ "sites" : [' +
	'{ "name":"Runoob" , "url":"www.runoob.com" },' +
	'{ "name":"Google" , "url":"www.google.com" },' +
	'{ "name":"Taobao" , "url":"www.taobao.com" } ]}';
	
obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.sites[1].name + " " + obj.sites[1].url;
</script>
```
### 相关函数
#### JSON.parse()
`
用于将一个 JSON 字符串转换为 JavaScript 对象
`
#### JSON.stringify()
`
用于将 JavaScript 值转换为 JSON 字符串
`
# iframe/AJAX
```

```
# Promise
# JQuery
## JavaScript框架
```
JavaScript（特别是对浏览器差异的复杂处理），通常很困难也很耗时。
为了应对这些调整，许多的 JavaScript (helper) 库应运而生。
```
# JavaScript实例
## 实例一：
```
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>

<p>点击按钮检测年龄。</p>
年龄:<input id="age" value="18" />
<p>是否达到投票年龄?</p>
<button onclick="myFunction()">点击按钮</button>
<p id="demo"></p>
<script>
function myFunction()
{
	var age,voteable;
	age=document.getElementById("age").value;
	voteable=(age<18)?"年龄太小":"年龄已达到";
	document.getElementById("demo").innerHTML=voteable;
}
</script>

</body>
</html>
```
## 实例二：
```
显示今天的星期名称。请注意 Sunday=0, Monday=1, Tuesday=2, 等等：
var d=new Date().getDay(); 
switch (d) 
{ 
  case 0:x="今天是星期日"; 
  break; 
  case 1:x="今天是星期一"; 
  break; 
  case 2:x="今天是星期二"; 
  break; 
  case 3:x="今天是星期三"; 
  break; 
  case 4:x="今天是星期四"; 
  break; 
  case 5:x="今天是星期五"; 
  break; 
  case 6:x="今天是星期六"; 
  break; 
}
//善用 default:
default:
    x="期待周末";
```
## 实例三：
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>		
<body>

<script>
cars=["BMW","Volvo","Saab","Ford"];
for (var i=0;i<cars.length;i++){
	document.write(cars[i] + "<br>");
}
</script>

</body>
</html>
```
## 实例四：
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
	
<p>点击下面的按钮，循环遍历对象 "person" 的属性。</p>
<button onclick="myFunction()">点击这里</button>
<p id="demo"></p>
<script>
function myFunction(){
	var x;
	var txt="";
	var person={fname:"Bill",lname:"Gates",age:56}; 
	for (x in person){
		txt=txt + person[x];
	}
	document.getElementById("demo").innerHTML=txt;
}
</script>
	
</body>
</html>
```
## 实例五：
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>搜索字符串 "Runoob", 并显示匹配的起始位置：</p>
<button onclick="myFunction()">点我</button>
<p id="demo"></p>
<script>
function myFunction() {
    var str = "Visit Runoob!"; 
    var n = str.search("Runoob");
    document.getElementById("demo").innerHTML = n;
}
</script>

</body>
</html>
```
## 实例六：
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>替换 "Microsoft" 为 "Runoob" :</p>
<button onclick="myFunction()">点我</button>
<p id="demo">请访问 Microsoft!</p>
<script>
function myFunction() {
    var str = document.getElementById("demo").innerHTML; 
    var txt = str.replace("Microsoft","Runoob");
    document.getElementById("demo").innerHTML = txt;
}
</script>

</body>
</html>
```
## 实例七
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<head>
<script>
function timedText(){
	var x=document.getElementById('txt');
	var t1=setTimeout(function(){x.value="2 秒"},2000);
	var t2=setTimeout(function(){x.value="4 秒"},4000);
	var t3=setTimeout(function(){x.value="6 秒"},6000);
}
</script>
</head>
<body>
	
<form>
<input type="button" value="显示文本时间!" onclick="timedText()" />
<input type="text" id="txt" />
</form>
<p>点击上面的按钮，输出的文本将告诉你2秒，4秒，6秒已经过去了。</p>
</body>

</html>
```
