[TOC]
# 面向过程
## 1.科学计数法
浮点数后面可以用"e"指示10的指数:
float f1=35e3F;
double d1=12E4D;
## 2.Math
### ==Math.Sqrt(x)==    
若x为64,则输出为8
### ==Math.Abs(x)==
输出为x的绝对值
### ==Math.Round(9.99)==   
 10
### ==Math.Round(9.5)== 
10
### ==Math.Round(-9.5)==    
10
### ==Math.Ceiling()== 
向上取整
### ==Math.Floor()==
 向下取整
## 3.String
### ==Length==    
获取字符串长度
### ==ToUpper()/ToLower()==
### ==String.Contact()==   
连接字符串
```
string myString = "Hello";
Console.WriteLine(myString[0]); //output:H
```
```
string name = "John Doe";
int charPos = name.IndexOf("D");
string lastName = name.Substring(charPos); //可以指定长度
Console.WriteLine(lastName);
```
### ==其他方法和StringBuilder==
```
1.用String.Empty()代替空字符串和null值；
2.immutable，string一旦设定不可更改；
3.string的方法:
Remove(1,1)   //删除下标开始的字符，可指定数量；
Insert(2,"@") //将指定字符插入到下标指定的位置；
Replace('大','小')  //用后者替代前者
Substring(1,3)     //截取从下标开始的字符，可指定数量；
Trim()/TrimStart()/TrimEnd()  //删除前后/前面/后面的空白
IsNullOrEmpty()/IsNullOrWhiteSpace();
Contains()/StartWith()/EndsWith();
IndexOf()/LastIndexOf()
Join(' ',a,b,c)  //用指定字符将字符串连接起来
Split(' ') //被Join()连接起来的字符串可以用Split()拆分获得一个string数组；
char[] ofA = a.ToCharArray(); //将字符串转换成数组

StringBuilder；
StringBuilder sb = new StringBuilder();
sb.Append("我");
sb.Append(",");
sb.Append("嫩爹");
string slogan = sb.ToString();  //最后要用ToString将StringBuilder对象转换成字符串；
其他方法:
Insert()/Replace()/Remove()/Clear()
```
### ==加号拼接和StringBuilder==
```
a+b;
加号拼接:
1.计算出a和b的长度，然后相加达到总长度；
2.按总长度新生成一个新的char[]数组；
3.将a和b的内容依次复制到新的char[]数组；
4.将新的char[]数组合成字符串。
StringBuilder：
1.在StringBuilder实例化的时候，生成一个长度（capacity）或者由构造函数参数指定，或者默认为16的char[]数组
2.将a、b、c、d……等字符串依次往char[]数组里装，如果
3.char[]数组的长度不够了，StringBuilder自动扩充其capacity，生成一个双倍长度的新数组继续装
4.直到调用ToString()，将char[]数组转换成字符串
StringBuilder两个重要的构造函数：
  public StringBuilder(int capacity);
  public StringBuilder(string value);
```
### ==字符串池==
```
每次要实例化一个新字符串时首先会在池中(编译器设置)检查:
若池中存在相同字符串，直接将字符串的堆地址赋值给新变量；
否则实例化该字符串，然后放到字符串池里。
```
### ==\\== 
`
转移符号
`
## 4.判断&循环
### ==? :==
```
int time = 20;
string result = (time < 18) ? "Good day." : "Good evening.";
Console.WriteLine(result);
// 三元换算符
```
### ==swith...case...==
```
int day = 4;
switch (day) 
{
  case 6:
    Console.WriteLine("Today is Saturday.");
    break;
  case 7:
    Console.WriteLine("Today is Sunday.");
    break;
  default:
    Console.WriteLine("Looking forward to the Weekend.");
    break;
}  
//default 和 break要放在最后
```
### ==For Loop & While Loop & Do...While... & Foreach==
### ==break & continue==
## 5.数组
`string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};`

### ==Sort Arrays==
```
// Sort a string
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
Array.Sort(cars);
foreach (string i in cars)
{
  Console.WriteLine(i);
}
 
// Sort an int
int[] myNumbers = {5, 1, 8, 9};
Array.Sort(myNumbers);
foreach (int i in myNumbers)
{
  Console.WriteLine(i);
}
//按升序或字母排序进行排列
```
### ==其他方法：Max()/Min()/Sum()==
### ==多维数组和交错数组==
```
//多维数组：在声明时，必须指定每一维的长度
int[,] mda = new int[2, 3];
mda[0, 0] = 1;
mda[0, 1] = 2;
Console.WriteLine(mda.Length);   //6
Console.WriteLine(mda.Rank);     //2
Console.WriteLine(mda.GetLength(0));  //2，一维的长度
int[,] mda = { { 1, 2, 3 }, { 4, 5, 6 } }; 

//交错数组：声明时，至少需要指定第一维的长度
int [][] test = new int[5][];　
```
### ==声明数组的几种方式==
```
// Create an array of four elements, and add values later
string[] cars = new string[4];

// Create an array of four elements and add values right away 
string[] cars = new string[4] {"Volvo", "BMW", "Ford", "Mazda"};

// Create an array of four elements without specifying the size 
string[] cars = new string[] {"Volvo", "BMW", "Ford", "Mazda"};

// Create an array of four elements, omitting the new keyword, and without specifying the size
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};

//通常选择最后一个
```
## 6.Method
### ==可选参数==
```
static void MyMethod(string country = "Norway") 
{
  Console.WriteLine(country);
}
//无参数时输出Norway
//可选参数必须定义在不可选参数的后面
```
### ==命名参数==
```
static void MyMethod(string child1 = "Liam", string child2 = "Jenny", string child3 = "John")
{
  Console.WriteLine(child3);
}

static void Main(string[] args)
{
  MyMethod(child3:"我是命名参数");
}
```
命名参数一般结合可选参数一起使用
## 7.零碎知识点
### ==项目组织==
```
1.一个project对应一个文件夹，下面有一个.csproj文件，记录该project下面包含的各种文件以及其他配置；
2. .obj放中间代码（调试用信息）,.bin放最终代码（编译后信息）；
3.///自动生成方法注释；
```
### ==表达式主体定义==
```
如果方法只有一条return语句，可以写成:
static int Add(int a, int b) => a + b;
上面语句等价于:
static int Add(int a, int b) 
{ 
  return a + b;
}
```
### ==ref和out==
```
1.ref:
i、方法定义和调用方法都必须显式使用 ref 关键字
ii、传递到 ref 参数的参数必须初始化,否则程序会报错
iii、通过ref的这个特性,一定程度上解决了C#中的函数只能有一个返回值的问题
```
```
static void Main(string[] args)
{
  int a = 6;
  int b = 66;
  Fun(ref a,ref b);
  Console.WriteLine("a:{0},b:{1}", a, b);//输出:72和6说明传入Fun方法是a和b的引用
}
static void Fun(ref int a, ref int b) 
{
  a = a+b;  //72,说明Main方法的a和b的值传进来了
  b = 6;
}
```
```
2.out:
和ref类似，定义和调用都必须显示使用out关键字；
区别是无法传值到方法中，所以赋值无意义。
```
```
static void Main(string[] args)
{
  int a = 6;
  int b = 66;
  Fun(ref a,ref b);
  Console.WriteLine("a:{0},b:{1}", a, b);//输出:72和6说明传入Fun方法是a和b的引用
}
static void Fun(ref int a, ref int b) 
{
  a = a+b;  //72,说明Main方法的a和b的值传进来了
  b = 6;
}
----------------------------------------------------------------------
out常用于一个方法需要多个返回的时候（即：获取除了返回值以外的结果），比如类库中的TryParse：
//如果能够Parse，方法返回值为true，input为转换结果
//否则，方法返回值为false，input为默认值0
if (double.TryParse(Console.ReadLine(), out double input))
{
  input += 10;
}
else
{
  Console.WriteLine("输入错误……");
}
```
### ==default()表达式==
`
default(int)
`
### ==params==
```
当方法的参数是数组的时候，我们可以在数组类型前面加一个关键字params：
static void getMax(params int[] array)
调用时，就可以直接传递数组元素：
getMax(3, 9, 18, 23);
```
### ==名称空间别称==
`
using yz = _17bang.feige.YuanZhan;
`
### ==Dynamic==
```
任何类型对象都可以使用dynamic标记。使用dynamic标记的变量可以绕过C#的编译时（注意：仅仅是编译时）的类型检查。
```

# 面向对象  
### ==OOP(Object-Oriented-Programming)==      
``
"Don't Repeat Yourself" (DRY)  
`` 
``
a class is a template for objects, and an object is an instance of a class.
``
### ==Constructor==
```
1.没有返回类型
2.所有类默认自带一个Constructor，new的时候就是在调用构造函数
3.构造函数可以带参数（给字段赋值）有重载
this.name=name;
4.给字段赋值，减少代码量
5.一旦声明了任何构造函数，之前默认自带的无参构造函数消失
--------------------------------------------------------------------
this在复制构造函数时的作用:
public Student(string name)   // 构造函数 1
{
    this.name = name;
}

public Student(string name, int age)
    : this(name)   // 使用this()调用构造函数 1
{
    this.age = age;
}
当运行Student(name, age)之前，会首先运行Student(name)
```
### ==Access Modifiders==
```
public
private 类不能使用private，且默认修饰符是internal
protected
internal  内部的，可以在当前项目中使用
protected internal  子类/跨项目的子类可使用
privated internal
//所有类成员默认private
```
### ==Encapsulation==
```
declare fields/variables as private
provide public get and set methods, through properties, to access and update the value of a private field

-Why Use?
1.Better control of class members (reduce the possibility of yourself (or others) to mess up the code)
2.Fields can be made read-only (if you only use the get method), or write-only (if you only use the set method)
3.Flexible: the programmer can change one part of the code without affecting other parts
4.Increased security of data
```
### ==Properties==
```
class Person
{
  private string name; // field

  public string Name   // property
  {
    get { return name; }   // get method
    set { name = value; }  // set method
  }
}
```
### ==readonly & const==
```
区别：
1.const一旦声明，就要赋值；readonly可用延后到constructor
2.const只能是int/bool/string等基本类型；readonly可以是其他类型（如Teacher）
3.const默认static，由类名直接调用；readonly默认是实例成员，由对象调用
4.const还可用于方法体内修饰变量，readonly不行
5.const是在编译时完成赋值，而readonly是在运行时赋值
```
### ==sealed==
### ==匿名类==
```
既没有类目，也不需要声明，可以直接使用的类：
var zjq = new  
{
    Name = "曾俊清",
    Age = 23,
};
语法特点：
1.变量类型只能用var；
2.所有属性只能是只读；
3.只是匿名，本质还是一个“类”，编译时会给名字<AnonymousType>；
4.拥有相同（名称+类型+次序）属性的匿名类会被当做一个类。
```
### ==索引器==
```
用于封装具有多个元素的数组
1.声明字段保存数据：
private string[] _courses={"SQL"."C#","JavaScript"}
2.可以指定访问修饰符，需要指定返回类型：
public string this[int index]
{
  get {return _courses[index;]}
  set {_courses[index]=value;}
}
3.调用时用[]
```
### ==析构函数==
```
1.~开头；
2.在.NET运行时在垃圾回收（garbage collection）时自动调用；
3.垃圾回收：清除内存上存放的数据，以便再次被使用；
4.值类型变量会在出栈时被清空；引用类型变量不会自动清除，会造成内存泄漏；
5.GC.Collect() 强制垃圾回收，否则因为可用内存足够大，不一定会被回收。
```
### ==静态和实例==
```
1.静态构造函数：
internal class Student
{
    static Student()   //不能有访问修饰符，也不能有参数
    {
    }
}
因为静态构造函数不能被开发人员调用，只能由.NET运行时在使用类之前，自动调用一次且仅仅调用一次。所以访问修饰符和参数对它都没有意义。

2.静态类
static；
静态类不能被实例化，不能有实例成员(实例类可以有静态成员)
```
### ==继承==
```
:
C#不支持多重继承，支持多层继承；
实例化一个子类，需要调用所有父类的构造函数；
如果父类只有一个无参构造函数，会默认调用这个无参构造函数，若父类没有无参构造函数，就需要在子类的构造函数中指明具体调用父类的哪一个构造函数；
如下:
internal class Person
{
    //父类没有无参构造函数
    public Person(string name) { }
    internal string Name { get; set; }
}

internal class Student : Person
{
    //子类必须显式地指明调用父类的某一个构造函数
    public Student(string name)
      : base(name)   //使用base关键字，将子类实例化获得的name传递给父类
    //: base("飞哥") //也可以传一个固定值 
    { 

    }
}
```
### ==is & as==
`
用来判断继承关系
`
### ==Polymorphism==
```
class Animal  // Base class (parent) 
{
  public void animalSound() 
  {
    Console.WriteLine("The animal makes a sound");
  }
}

class Pig : Animal  // Derived class (child) 
{
  public void animalSound() 
  {
    Console.WriteLine("The pig says: wee wee");
  }
}

class Dog : Animal  // Derived class (child) 
{
  public void animalSound() 
  {
    Console.WriteLine("The dog says: bow wow");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object
    Animal myDog = new Dog();  // Create a Dog object

    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}
output:
The animal makes a sound
The animal makes a sound
The animal makes a sound
```
### ==new==
```
可以用new来掩盖父类方法:
internal class Student : Person
{
  internal new void Eat()         //注意关键字new
  {
     Console.WriteLine("学生吃饭");
  }  
}
```
### ==override(重写)==
```
class Animal  // Base class (parent) 
{
  public virtual void animalSound() 
  {
    Console.WriteLine("The animal makes a sound");
  }
}

class Pig : Animal  // Derived class (child) 
{
  public override void animalSound() 
  {
    Console.WriteLine("The pig says: wee wee");
  }
}

class Dog : Animal  // Derived class (child) 
{
  public override void animalSound() 
  {
    Console.WriteLine("The dog says: bow wow");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object
    Animal myDog = new Dog();  // Create a Dog object

    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}
output:
The animal makes a sound
The pig says: wee wee
The dog says: bow wow

子类可以用base调用父类的方法，示例如下：
internal class Student : Person
{
  internal override void Eat()   //这里已经是override了
  {
    Console.WriteLine("学生吃饭");
  }
}

internal class AgileStudent : Student
{
  internal override void Eat()  //继续override
  {
     base.Eat();                //base仅指Student，不包含父类的父类
  }
}
```
### ==Abstraction==
```
1.作用于类，不能被实例化；
2.作用于方法，没有方法体；
3.抽象方法只能放置在被abstract修饰的抽象类中；
4.可以声明其他普通类成员，包括构造函数；
5.子类需要override实现抽象类的全部抽象方法且override的方法体内不能通过base调用其抽象类方法；
6.目的:To achieve security - hide certain details and only show the important details of an object.
```
### ==Interface==
```
1.只能有声明(方法和属性)，不能有实现；
2.不能有字段和构造函数；
3.接口类型可以加访问修饰符，接口成员不能有访问修饰符；
4.一个子类要实现接口，需要实现接口的全部成员(包括继承的接口的所有成员)
```
```
实现接口的两种方式：
1.隐式实现：在子类中添加和接口中定义相同的方法
internal class Student : Person, ILearn
{
  //ILearn中定义了一个Practise()方法
  public void Practise()
  {
    //实现了ILearn中定义的Practise()方法
     Console.WriteLine("键盘敲烂，月薪过万！");
  }
}
2.显示实现：当一个子类继承了多个接口，且多个接口中定义了相同方法
internal class Student : Person, ILearn, IPlay
{
  //internal void ILearn.Practise()  //不能有访问修饰符
  void ILearn.Practise()  //实现ILearn.Practise()方法
  {
     Console.WriteLine("键盘敲烂，月薪过万！");
  }

  void IPlay.Practise()  //实现IPlay.Practise()方法
  {
     Console.WriteLine("再撸一把啊！");
  }
}
// 显式实现的接口方法，不能用子类类型的变量进行调用：
```
### ==抽象类和接口的异同==
```
语法层面:
1.抽象类可以有其他实现，接口只能有声明；
2.抽象类可以继承接口，接口无法继承抽象类；
3.抽象类只能作为父类使用，所以一个子类只能有继承一个抽象类，但能有多个接口；
现实意义：
抽象类是对现实事物的映射，一般类目时名词；
接口是对事物行为的封装，一般接口名是动词。
```
### ==Struct和日期==
```
Struct
1.能够实现接口，但不能继承其他结构和类；也不能被其他结构和类继承；
2.默认有一个无参构造函数，但不能显示声明，有参构造函数可以显示声明，声明的有参构造函数不会"隐藏"默认的无参构造函数；
3.所有成员必须有值,若使用结构默认的无参构造函数，结构弧自动给所有成员赋值默认值

DateTime
1.ToString()，用于指定日期显示的格式-yyyy年MM月dd日 hh点mm分ss秒；
2.TimeSpan
表示一段时间，通常由两个日期相减获得，最大单位-天，没有年和月；
用Days/Hours/Minutes等取出的是Timespan中天/小时/分钟等部分的值；
用TotalDays/TotalHours/TotalMinutes等取出的才是Timespan代表的时间间隔换算成天/小时/分钟等的值。
```
### ==运算符重载 & 类型转换重载==
```
运算符重载:
public static DateTime operator +(DateTime d, TimeSpan t);
1.方法只能是public和static；
2.必须要有一个关键字operator；
3.至少一个参数和返回值类型相匹配；
4.某些运算符有要求“成套”，比如重载了==，就必须重载 !=
类型转换重载：
public static explicit operator Teacher(Student student)
{
  return new Teacher();
}
```
### ==Enum & 位运算==
```
enum Level 
{
  Low,
  Medium,
  High
}
//Level.Medium
//默认从0开始，步长为1
//需要在枚举和整型之间强制转换
```
一般与switch相结合:
```
enum Level 
{
  Low,
  Medium,
  High
}

static void Main(string[] args) 
{
  Level myVar = Level.Medium;
  switch(myVar) 
  {
    case Level.Low:
      Console.WriteLine("Low level");
      break;
    case Level.Medium:
       Console.WriteLine("Medium level");
      break;
    case Level.High:
      Console.WriteLine("High level");
      break;
  }
}
```
```
位运算：把传入的数转化成二进制，然后按二进制对其进行运算
1.&:位与，只有两个1才为1；
2.|:位或，只要一个1就位1；
3.^:异或，两个不同才为1；
当枚举值设为2的整数次方：
位或（|）相当于“加”，比如：2|4=6，2|4|1=7；
将位或结果和任一成员进行异或（^）运算，其效果就相当于“减”，比如：6^2=4，7^4=3，
将位或结果和任一成员进行位与（&）运算，其结果就等于该成员，比如：6&2=2，7&4=4；且与任何非成进行位与（&）运算，其结果不会等于该非成员，比如：6&1=0，7&8=0
权限管理：
enum Role
{
  Student = 1,
  TeacherAssist = 2,
  TeamLeader = 4,
  ormitoryHead = 8
 }  //所有枚举值必须是2的整数次方
|：添加权限
^：剥夺权限
&：检测用户是否具有某项权限
public int Role { get; set; }
Student tlzz = new Student
{
   Role = (int)Role.Student | (int)Role.TeamLeader
};
  tlzz.Role = tlzz.Role | (int)Role.DormitoryHead;
  tlzz.Role = tlzz.Role ^ (int)Role.Student;
  Console.WriteLine((tlzz.Role & (int)Role.TeamLeader) == (int)Role.TeamLeader);
```
### ==装箱和拆箱==
```
Object的内置方法:
Equals(a,b) 比较作为参数传入的两个对象；
GetType() & typeof():
获取变量的运行时类型 & 获取类型的编译时类型；
装箱:
    object o = new object();
    o.inbox = 986;
拆箱:
    int i = (int)o;
装箱和拆箱仅适用于值类型和object之间；强制类型转换适用于任何有继承关系的类型;
装箱和拆箱多了一个创建object实例的过程；类型转换没有这个过程，不会额外的生成一个对象.
```
### ==反射和特性==
#### ==反射==
```
反射:   
.NET的反射只能应用于.NET程序，所以说，反射是一种正常的应用技术；
其次，反射发生是在.NET程序运行时(不是编译时)。

元数据(MetaData):
1.当它把源代码编译成.dll文件的时候，它还同时生成了程序集的二进制描述性信息，并直接存放在.dll文件中;
2.程序集的所定义和引用的有成员信息都包括在内，包括程序集信息、类名、类成员和类的继承实现等等(记录方式是MSIL);
3.反射就是依靠读取metadata实现其功能的。

MSIL(微软中间语言):
1.MetaData中没有方法的具体实现.换言之，metadata里记录了某个类中有某个方法，方法名、参数、返回值啥的它都知道;
2.但它不知道这个方法具体是如何运行的。记录方法如何运行的代码以MSIL的格式存放在.dll文件中.

ILDASM(反编译工具)可以阅读.dll文件;

反射不能直接读取方法中的源代码，也不能读取经过编译过后的以MSIL格式存储的代码，唯一可以读取的是.dll文件中的方法对应的字节流（二进制文件内容），反射就是利用这些字节流，来进行方法调用的.

示例:
class Student
{
  private int_weight; //私有字段不被访问
  public Student(int weight)
  {
    _weight=weight;
  }
}

1.Student fg = new Student(60); //给一个变量，如何获取_weight的值？

2.Type typeInfo = fg.GetType(); //也可以用typeof获取到变量的类型信息：typeof(Student)

3.FieldInfo onweight = typeInfo.GetField("_weight",BindingFlags.NonPublic|BindingFlags.Instance); 
//使用Type对象获取到一个FieldInfo对象，拿到该字段如何设置的信息；
//必须指定字段名字，BindFlags说明字段是非公共的，实例的；

4.object student = onweight.GetValue(fg); //最后用GetValue()拿到该字段的值
```
#### ==特性==
```
枚举上加[Flags],可以在ToString()时输出更有意义的字符串；
[Obsolete],标记某个类或者类成员已经过时；

自定义声明一个特性类，示例：
  //指定只能用于类和方法
  [AttributeUsage(AttributeTargets.Class | AttributeTargets.Method)]
  class OnlineAttribute : Attribute
  {
    //可以无参也可以有参
    public OnlineAttribute(){}
    public OnlineAttribute(int version)
    {
      Version = version;
    }

      //还可以使用属性
      public int Version { get; set; }
   }

使用特性：
    ///用于类，获取时将: 
    ///1. 调用OnlineAttribute的无参构造函数
    ///2. 给OnlineAttribute对象的Version属性赋值
    [Online(Version = 3)]
    internal class Student
    {
        [Online(2)]  //用于方法，获取时将调用OnlineAttribute的有参构造函数
        internal void learn(){ }

        //[Online]  //不能用于属性
        public string Name { get; set; }
    }

获取特性：
    Attribute attribute = OnlineAttribute.GetCustomAttribute(
          typeof(Student),             //Student类上的
          typeof(OnlineAttribute)      //OnlineAttribute特性
    );
          //将基类的Attribute对象强转为子类
          Console.WriteLine(((OnlineAttribute)attribute).Version);
```
### ==泛型(Generic)==
```
public class Generic<T>
{
   //注意T[]，不是int[]或者string[]
   internal T[] array;
}

语法：
1.定义构造函数时不需要加上泛型参数；
2.多个类型参数用，分隔开；
3.对于泛型对象，一旦T被变量声明/new，就不能更改；
4.泛型可用于方法/接口/委托，不能用于枚举

类型约束where：
1.可以为多个类型参数定义不同的约束；
2.可以为同一个类型参数定义多个不冲突的约束；
class MimicStack<T, TKey>
  //where T : class, struct  冲突了，不行
  where T : ILearn, new()
  where TKey: new()

泛型继承：
1.非泛型类不能继承一个还没有具象化的泛型类；
2.泛型类可以继承泛型/非泛型类；
```
### ==List & Dictionary==
```
List:
List<int> ages = new List<int> { 16, 23, 25, 23, 22 };

Dictionary:
    Dictionary<string, int> scores = new Dictionary<string, int>();
    scores["atai"] = 85;
    scores["zm"] = 95;
    scores["wpz"] = 90;
    或者，
    scores = new Dictionary<string, int>
    {
        {"atai", 85 },
        {"zm", 95 }
    };
    一些方法:
        scores.Add("wpz", 90);
        scores.Remove("wpz");
        scores.ContainsKey("zm");
```
### ==拓展方法==
```
语法：
1.在原有类（如IEnumerable<int>）之外另外声明一个类（如：Enumerable，以下简称“扩展类”），扩展类必须是静态（static）的，类名其实并不重要（不会被用到）；
2.在扩展类中声明static方法；
3.方法的第一个参数必须带 this 关键字，且后跟一个原有类类型的参数（通常命名为source）；
4.于是可以直接用扩展类实例调用这个方法，调用时应忽略第一个this参数；
5.扩展方法仅在扩展类没有相应的实例方法时才会被调用。即：如果扩展类中本身就有一个和扩展方法签名相同的方法，会直接调用实例方法而不是扩展方法。

集合常用扩展方法
Count(), Max(), Average(), First()等；
Skip()和Take()

自定义拓展方法：
namespace MyNamespace
{
    public static class TeacherExtesion 
    {
        public static void Greet(this Teacher teacher, string words)
        {
            //teacher参数是可以作为正常参数使用的
            Console.WriteLine($"我是{teacher.Name}，{words}");
        }

        //方法重载
        public static void Greet(this Teacher teacher)
        {

        }
    }
}
```
### ==委托和事件==
```
委托：将方法作为变量使用
声明委托：
delegate void Calculate(int a, int b);

Func：有返回值的方法。使用泛型参数依次表示方法参数，最后一个表示方法返回值；
Action：没有返回值的方法。使用泛型参数依次表示方法参数；
public delegate TResult Func<in T, out TResult>(T arg);
public delegate void Action<in T>(T obj);

事件：
```
### ==匿名方法/Lambda表达式/闭包==
```
匿名方法：
每给一个委托就需要声明一个方法，很麻烦，因此匿名委托出现：
Calculate ai = delegate(int x,int y)
{
  console.WriteLine($"just a piece of cake:{x}/{y}={x/y}");
};
ai(8,3);
语法特点：
1.无方法名；
2.由关键字delegate替代；
3.匿名方法不需要标志返回类型；

Lambda表达式：
将匿名方法的delegate去掉，用箭头=>替代：
Calculate ai = (int x,int y)=>
{
  console.WriteLine($"just a piece of cake:{x}/{y}={x/y}");
}
简写方式：
1.不指定参数类型：
Action<string, string> d = (x, y) => { Console.WriteLine(x + "欢迎您，" + y); };
2.一个参数，可以不用（）；没有参数，还是要有一个空括号：
Action<string> d = x => Console.WriteLine(x + "欢迎您");

闭包：
使用匿名方法产生的语法现象：
1.外部方法不能使用匿名函数中的变量；
2.匿名方法能够使用（并改变）其外部方法的变量/参数。
```
### ==Linq==
```
Linq(Language-Integrated Query)
Linq并非只针对集合，它已经作用于数据库（Linq to SQL/EF）、XML文件（Linq to XML）、Web Service……针对于集合的操作属于Linq to Object。但所有的Linq使用统一的查询表达式（query expression）
示例：
    var excellent = from s in students
                    where s.Score > 90
                    select s;
语法:
1.以from开头；
2.数据源必须是IEnumerable或它的子类；
3.以select或group结尾

强类型：
无论是表达式内部，还是表达式结果
如果数据源为非泛型集合：需要在from之后指定类型，如：
from Student s in students；

过滤(where)条件：
所有能返回bool值的表达式都可以用作where条件（Linq to Object）
  大于（>）小于（<）等于（==）  不等于（!=）
  包含（Contains）、StartWith()
  数量（Count）、Length...
示例：
  var excellent = from s in students
                  //where s.Majors.Count > 2
                  //where s.Majors.Contains(csharp)
                  //where !s.Majors.Contains(Javascript)
                  where s.Name.StartsWith('王') && s.Score > 80
                  select s;
              
排序(order):
  var excellent = from s in students
                  //orderby s.Score ascending  //按Score升序（默认）
                  orderby s.Name descending    //按Name降序
                  select s;

分组(gropup):
  var groupMajor = from m in majors
                   group m by m.Teacher;
//分组过后得到一个键值对-IEnumerable<IGrouping<Teacher,Major>>,
//可以foreach得到Key和Name

投影(select):
从结果集中取出或增加若干属性重新组合成新的集合:
  var excellent = from s in Students
                  select s.Name;
可以使用匿名对象：
  var excellent = from s in Students
                  select new
                  {
                    s.Name,
                    s.Score
                  }

select和where的区别：
where是“横向”的操作（一个学生一行），比如从10个学生中取出3个年龄大于20岁的学生，取出来的还是学生；
select是“纵向”的操作（学生的一个属性算一列），比如取出学生的姓名和年龄，取出来的就不是学生了，而是一个属性或者多个属性的组合

投影常见于group和join之后，一般用投影得到Dictionary拿到数据值，例如：
var groupedMajor = from m in majors
            group m by m.Teacher //到此为止，得到分组结果集
            //接下来对分组结果集再运算（统计）
            into gm              //into类似于命名，将之前的结果集命名为：gm
            select new           //利用投影
            {
              gm.Key.Name, //老师的名字
              gm.Count()   //统计结果
            };

Join：
var majors = from m in majors
            join t in teachers
            on m.Teacher equals t        //equals非常重要，不能使用 == 替代
            where t.Name == "小鱼"
            select m;

Left Outer Join：
所有左边的（第一个）集合元素都必须返回，哪怕在右边的（第二个）集合无法匹配到（无法匹配就显示为null）需要使用DefaultIfEmpty：
var majors = from t in teachers         //List<Teacher>放在第一位
             join m in majors
             on t equals m.Teacher into mt            //又见into，mt是IEnumerable<Major>
             from result in mt.DefaultIfEmpty()       //调用了DefaultIfEmpty()并再次from
             select new { teacher = t.Name, major = result?.Name ?? "没有课程" };

Cross Join：
左右两边的集合进行无条件的多对多交叉连接（执行笛卡尔乘积），使用多个from实现：
var result = from t in teachers
             from m in majors
             select new { teacher = t.Name, major = m.Name};

Let子句：
有时候，我们可以查询过程切分为若干个过程，每一个过程存储一个子结果集，以供之后的查询使
var majors = from s in students
             let ms = s.Majors   //把所有的 Major 先暴露出来
             from m in ms        //后面就可以使用 let 指定的 ms
             select new { student = s.Name, major = m };

延迟执行：
Linq的查询表达式只是一个表达式，并不存储查询结果，指到被foreach或ToList()等强制执行；
```
### ==Linq方法==
```
条件过滤：where
var excellent = students.Where(s => s.Score > 90);

排序：orderby
var excellent = students
//.OrderBy(s => s.Name)
.OrderByDescending(s => s.Score)；

分组：Group
var groupedMajor = majors.GroupBy(m => m.Teacher);

投影：select
var excellent = students.Select(s => s.Name);
var groupedMajor = majors.GroupBy(m => m.Teacher)
.Select(gm => new
{
  teacher = gm.Key，
  count = gm.Count()
});

Join：
var mj = majors.Join(teachers, m => m.TeacherName, t => t.Name,
  (m, t) => new
  {
    major=m.Name,
    teacher=t.Name
  });

SelectMany：
var sm = students.SelectMany(
    s => s.Majors,                //指示取出students里的所有Major
    (s, m) => new { s, m.Name }   //组合student和major
    )
    .Where(s => s.Name.ToLower().Contains("s")) //在上述结果集中筛选
    ;
```
### ==变体：协变&逆变==
```
协变（Covariance）：out，子类可以替父类，代表：IEnumerable<T>, IEnumerator<T>, IQueryable<T>, and IGrouping<TKey,TElement>
逆变（Contravariance）：in，父类可以替子类，代表： IComparer<T>, IComparable<T>, and IEqualityComparer<T>
不变（Invariance）：无指示。只能使用同一个类型
准确描述：一个类型参数声明了协变out（或逆变in）的泛型接口，用父类（或子类）做类型参数时，可以接受子类（或父类）做类型参数的实例。
```
### ==Files==
```
The File class from the System.IO namespace, allows us to work with files
```
##### ==Methods==
---------------------------
Method | Desciption
------ | ------
AppendText() | Appends text at the end of an existing file
Copy() | Copies a file
Create() | Creates or overwrites a file
Create() | Creates or overwrites a file
Delete() | Deletes a file
Exists() |	Tests whether the file exists
ReadAllText() |	Reads the contents of a file
Replace()	| Replaces the contents of a file with the contents of another file
WriteAllText() |	Creates a new file and writes the contents to it. If the file already exists, it will be overwritten.
#### ==Example==
```
using System.IO;  // include the System.IO namespace

string writeText = "Hello World!";  // Create a text string
File.WriteAllText("filename.txt", writeText);  // Create a file and write the content of writeText to it

string readText = File.ReadAllText("filename.txt");  // Read the contents of the file
Console.WriteLine(readText);  // Output the content
```
### ==Exceptions==
#### ==try...catch...finally==
```
try
{
  int[] myNumbers = {1, 2, 3};
  Console.WriteLine(myNumbers[10]);
}
catch (Exception e)
{
  Console.WriteLine(e.Message);
}
finally
{
  Console.WriteLine("The 'try catch' is finished.");
}
```
#### ==throw==
```
static void checkAge(int age)
{
  if (age < 18)
  {
    throw new ArithmeticException("Access denied - You must be at least 18 years old.");
  }
  else
  {
    Console.WriteLine("Access granted - You are old enough!");
  }
}

static void Main(string[] args)
{
  checkAge(15);
}
```
### ==其他细碎知识点==
#### ==readonly & const==
```
I.const一旦声明，就要赋值；readonly可用延后到constructor；
II.const只能是int  bool  string等基本类型；readonly可以是其他类型（如Teacher）；
III.const默认static，由类名直接调用；readonly默认是实例成员，由对象调用;；
IV.const还可用于方法体内修饰变量，readonly不行；
V:const是在编译时完成赋值，而readonly是在运行时赋值.
```
#### ==TDD(测试驱动开发)==
```
public class Tests
{
    [SetUp]
    public void Setup()
    {
    }

    [Test]
    public void Test1()
    {
       Assert.Pass();
    }
}
[SetUp]：被标记的方法将会在每一个测试方法被调用前调用
[Test]：被标记的方法会被依次调用
Assert.AreEqual()
```
#### ==Nullable/??/?.==
```
可控类型:
int?;

Null值替代运算符  ??
SQL.Teacher = SQL.Teacher ?? new Teacher(); //不为null值返回??前面的值，为null值返回后面的值

Null条件运算符 ?. 和 ?[]
只有 . 或者 [] 前面的变量不为null值的时候，才进行取值；否则返回null值；

Console.WriteLine(SQL.Teacher?.Name ?? "course SQL has no teacher");
```
#### ==for & foreach==
```
foreach (var item in collection)
{
   Console.WriteLine(item);
}

区别：
1.for循环的迭代基础是累加器和下标（i++）
2.foreach循环的基础是迭代器的MoveNext()
3.foreach里的item不能被赋值（assign）

底层实现:
IEnumerable：该接口能返回
IEnumerator：具有MoveNext()方法
```