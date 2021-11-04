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
HTML页面嵌入：
   <script type="text/javascript">
        alert("源栈欢迎你！");
    </script>
...type可以省略
引用.js文件：
<script src="~/js/site.js" type="text/javascript"></script>
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
### let&var
`
let不支持变量提升，推荐使用let；
`
### Object对象
```
本质上是一组键值对组成的无序集合
var student{
   name="小王",  
   age="21",
   "is-male":true
};
或者
var  age='21';
var obj={age};
可以使用 . 或者[ ]取出对象中元素的值；
，分隔  ：赋值
```
### Undefined和null
```
变量未赋值前的值为undefined（类型为 undefined）
null的类型为 object
```
## ESLint
`
检测Js错误的插件
`
## 数据类型及相关
### 基本类型
```
String  单双皆可；
Number:
1.科学计数法-986e-2 => 9.86；
2.NAN(Not A N)；
3.字母lnfinity表示无穷大，加一个  - 表示无穷小;
Boolean；
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
## RegExp
```

```
# BOM
```

```
# DOM
```

```
# 事件
```

```
# iframe/AJAX
```

```
# JSON
```

```
# JQuery