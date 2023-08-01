### 3-1 计算机基础和js介绍

- 浏览器执行js简介

    浏览器分成两部分：渲染引擎和js引擎

    - 渲染引擎：用来解析HTML和CSS，俗称内核，比如chrome浏览器的blink，老版本的webkit
    - js引擎：也成为js解释器，用来读取网页中的js代码，对其处理后运行，比如chrome浏览器的V8

        浏览器本身并不会执行js代码，而是通过内置js引擎来执行js代码，js引擎执行代码时逐行解释每一句代码，然后由计算机去执行，所以js归为脚本语言会逐行解释执行 
- js三部分组成

    ECMScript javascript语法 规定了js编程语法和基础核心知识

    DOM 页面文档对象模型 对各种元素进行操作

    BOM 浏览器对象模型
- 输入输出语句

    ![](https://secure2.wostatic.cn/static/oTUYWWbboVnFgQPt7J9WJP/image.png?auth_key=1690869089-fCu1Fv6toLaF9aLU6ZfBDY-0-fe078034f2d137ccf59087d041b5efc2)
- 变量

    只是声明不赋值，会输出undefined

    不声明不赋值 直接使用会报错

    不声明直接赋值  能使用但是会变成全局变量

    ![](https://secure2.wostatic.cn/static/mfpprJahQS9HZYoWr69f7U/image.png?auth_key=1690869089-tkj5UiehokR7fZ1jsAv59F-0-da9b3da441f0772680d1ad3c9e8b2378)

    尽量不要使用name作为变量名

### 3-2 数据类型

根据数据所占有的数据空间不同，分为不同的数据类型

- 变量的数据类型

    js是一种弱类型或者动态语言，只有程序在运行过过程中根据等号右边的值来确定的。相同的变量可以做用不同的类型。

    - 简单数据类型：number string boolean undefined null
    - 复杂数据类型:object
- 数字型Number

    在Js中变量赋值加0就是8进制，加0x是16进制

    数字型的最大值：`Number.MAX_VALUE`

    数字型的最小值`:Number.MIN_VALUE`

    infinity 无穷大 -infinity无穷小 NaN代表一个非数值
- isNaN

    用来判断非数字，并且返回一个值，如果是数字返回false,如果不是数字返回true

字符串型string

其语法是加单引号或者双引号，要在内部加引号需要外单内双，或外双内单

![](https://secure2.wostatic.cn/static/noMfc5fVav3W1aBenR9Y7G/image.png?auth_key=1690869089-brzqoqW7tpGoM3SKWq1Ctz-0-ac90786359ff1b3dee8ff60857c6132b)

1. str.length 输出字符串的长度 
2. 字符串用+拼接 只要是有字符型的最后还是字符串型的

```JavaScript
var age=18;
console.log("今年age岁")//今年age岁
console.log("今年"+age+"岁")//今年18岁
```
- 布尔型boolen 

    true在加法中当作1来看 false在运算中当作0来看 
- Undefined null

    如果一个变量声明未赋值，就是undefined 未定义数据类型

    ![](https://secure2.wostatic.cn/static/rqokxLtfNfq3J6Yuj7UYu5/image.png?auth_key=1690869089-ipBudmPhsbvYDbY43nLMd6-0-e3bdcbb8dc4bb3245888333c2d1d911e)

    null 值为空

      ![](https://secure2.wostatic.cn/static/86zg7PDmn8JEFtkFb5uU8f/image.png?auth_key=1690869089-irpU2mMkk2d2ta7r2d1PGv-0-7f34b90d162815626120388df24ab98b)
- typeof

    检测变量数据类型 prompt取得的值是字符型的
- 数据类型的转换
    1. 转换为字符串

        toString()  num.toString() 

        String()强制类型转换 String(num)

        加号拼接字符串的方法 num+''
    2. 转换成数字型

        ![](https://secure2.wostatic.cn/static/oeFFHrbwtVvsyMGov7DMnD/image.png?auth_key=1690869089-jbUQW69xrGoD3GJkqcdNi3-0-05367f2ab82768e7003c0b926ae6ee15)
    3. 转换成boolean

        ![](https://secure2.wostatic.cn/static/jau3VEMimUzu2F91LTSYpo/image.png?auth_key=1690869089-eSh4p52o4ssuohRQiGNmRC-0-bf8cc588b2bba6e3c76325bad0ff719b)

### 3-3 js操作运算符

- 算术运算符

    ![](https://secure2.wostatic.cn/static/ifzLQx27jJabME1zrLxvVa/image.png?auth_key=1690869089-jWhaxZdWT2cCFhPG8Lb1mo-0-7a065e636ea80c74736e191fdb806f78)

    尽量避免浮点数直接参与运算

```JavaScript
var num=0.1+0.3;
console.log(num==0.4)//false
```
- 表达式和返回值

    表达式：由数字、运算符、变量等组成的式子我们称之为表达式

    表达式都会返回一个结果这个结果称为返回值。
- 前置/后置递增运算符

    ![](https://secure2.wostatic.cn/static/dEBCyyFJRnL6o9S51cZmVX/image.png?auth_key=1690869089-dvsMrbAJtViCEchcSpJKvf-0-8201a2db1b9f2329a55ab7d7ba4e675f)

### 3-4 流程控制

顺序结构、分支结构、循环结构

```JavaScript
switch(表达式){
case value:
   执行语句1；
   break;
default:
    执行最后的语句;
}
```

### 3-5 数组

- 创建

    var a=new Array()//创建了一个空数组

    var a=[1，2，‘’pink"];

    数组里数据用逗号分隔，数组里面的数据称为数组元素 , 数组里面数据类型可以是任意类型
- 数组

    长度：数组名.length

    数组转换成字符串：依次遍历 +一个空的字符串

    数组新增元素：修改length长度 索引号增加数组元素

### 3-6函数

- 声明函数：

```JavaScript
function 函数名()
{
    函数体
}
```

![](https://secure2.wostatic.cn/static/4jW6Bs3dZrxsDPEoPgeBgP/image.png?auth_key=1690869089-o5mH2mVxw5ArzezCzctWaf-0-9461c63fd1b85c3f8c7f4e4b3c01f447)

- arguments

    是当前函数的一个内置对象，里面存了函数的所有实参

    伪数组：具有数组的length属性，按照索引的方式进行存储，它没有真正数组的一些方法 pop() push()等等
- 函数可以调用另一个函数
- 函数的两种声明方式

    函数表达式：变量里面存的是函数，也可以传递参数

```JavaScript
//fun是变量名不是函数名，函数没有名字是匿名函数
var fun= function(){
    console.log();
};
fun();
```
- js的作用域

    就是代码名字（变量）在某个范围内起作用和效果 ，目的是为了提高程序的可靠性，减少命名冲突。

    - 全局作用域：整个script标签，或者是一个单独的js文件
    - 局部作用域（函数作用域）：在函数内部就是局部作用域 这个代码的名字只在函数内部起效果和作用。局部作用域内变量要是与全局作用域内变量名字冲突，用的是局部作用域的变量。
    - 全局变量：函数内也可以用，除了在全局作用域下定义的还有函数内部没有声明直接赋值的变量也叫全局变量
    - 局部变量：只能在函数用，形参也可以看做是局部变量
        - 全局变量只有浏览器关闭的时候才会销毁，比较占内存
        - 局部变量当我们函数结束的时候就会销毁。
    - js没有块级作用域

        在es6新增的块级作用域

        块级作用域 {} if{} for {}
    - 作用域链

        函数内部可以访问外部函数的变量，最近的上一级

```JavaScript
var number=10;
function fn()
{
    var number=20;
    function fun(){
        console.log(number)//20
    }
    fun();
}
fn();
```
- 预解析

```JavaScript
console.log(num);// undefined
var  num=1;
fn();//11
function fn(){
   console.log(11);
}
fun();//fun is a not funtion
var fun=function(){
    console.log(22);
}
fun();//22
```

    js引擎运行js分为两步： 预解析 代码执行

    1. 预解析 js引擎会把js里面所有的var还有function提升到当前作用域的最前面
    2. 代码执行 按照代码书写的顺序从上往下执行
    3. 预解析分为 变量预解析（变量提升） 和 函数预解析（函数提升）
    4. 变量提升就是把所有的变量声明提升到当前的作用域的最前面
    5. 函数提升，把所有的函数声明提升到当前作用域的最前面，不调用函数

### 3-7 对象

对象是一组无序的相关属性和方法的集合，所有事物都是对象，例如字符串、数值、数组、函数等

对象由属性和方法组成：

1. 属性：事物的特征 
2. 方法：事物的行为

为什么需要对象：保存一个人的完整信息

- 创建对象的三种方式

    1.利用字面量创建对象

    2.利用new Object 创建对象

    3.利用构造函数创建对象

    - 对象字面量：就是花括号{}里面包含了表达事物的

```JavaScript
//var obj={};//创建了一个空对象
var obj={
    uname:'小明',
    age:18,
    sex:"男",
    sayHi:function(){
        console.log("Hi");
    }
}
//(1)属性和方法采用了键值对的方式 
//(2)多个属性或者方法用逗号隔开
//(3)方法：冒号后面跟的是一个匿名函数
console.log(obj.uname);
console.log(obj['age']);
obj.sayHi();
//(1)调用对象的属性 我们采取 对象名.属性名
//(2)调用属性还有一种方法    对象名['属性名']
//(3)调用对象的方法 对象名.方法名();
```
    - 利用new Object创建对象

```JavaScript
var obj=new Object();//创建了一个空的对象
obj.uname='xiaomi'
obj.age=18;
obj.sex="男";
obj.sayHi=function(){
}
//(1)利用等号赋值的方法添加属性和方法
//(2)每个属性和方法用分号结束
```
    - 为什么要用构造函数创建对象呢

        因为前面两种创建对象的方式一次只能创建一个对象

        因此我们可以利用函数的方法重复这些相同的代码，我们就把这个函数称为构造函数。

        构造函数：把我们对象里面一些相同的属性和方法抽象出来封装到函数里面。
    - 构造函数创建对象

```JavaScript
/*function 构造函数名(){
   this.属性 =值;
   this.方法 = function(){}
}*/
//构造函数首字母要大写
//构造函数不需要return
new 构造函数名();
funtion Star(uname,age,sex){
    this.name=uname;
    this.age=age;
    this.sex=sex;
    this.sing=function(sang){
        console.log(sang);
    }
}
var ldh=new Star("刘德华",18,"男");
```
    - new 执行过程
        1. new构造函数可以在内存中创建了一个空的对象
        2. this就会指向刚才创建的空对象
        3. 执行构造函数里面的代码 给这个空对象添加属性和方法
        4. 返回这个对象
    - 遍历对象

        for in语句用于对数组和对象进行循环

```JavaScript
//for(变量 in 对象){}
for(var k in obj){
    console.log(k);//k变量 输出 得到的是 属性名
    console(obj[k]);//得到的是里面的属性值
}
```

        方法也能遍历出来 fn是方法名  f(){}是值

### 3-8 内置对象

- Math对象
- 日期对象

### 3-9 简单类型和复杂类型

基本包装类型：就是把简单数据类型包装成为了复杂数据类型

![](https://secure2.wostatic.cn/static/v9iCJ6AmbuEvuMLGYkrunq/image.png?auth_key=1690869090-w5GSYJz1NRyNe5A83TDe8S-0-9b2234acfea2bd4babadae341888e8ec)

- 字符串的不可变

    指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。
- 根据字符返回位置

    字符串多有的方法都不会修改字符串本身，操作完成会返回一个新的字符串

```JavaScript
str.indexOf('要查找的字符'，[起始的位置])；

```

    ![](https://secure2.wostatic.cn/static/nFVXVYT8eq6nSyZxPsqJaB/image.png?auth_key=1690869090-u4idTkx8tRK44iyafa4duY-0-fc0df3cb11e138f1fe445b9f60312056)
- 返回字符位置和次数
- 根据位置返回字符

    charAt(index);
- this

    谁调用就指向谁   

函数没有return则返回undefined

调用函数：函数名();

## b站

- 面向对象

    特性：封装性、继承性、多态性

    #### 面向过程和面向对象对比：

    面向过程：

    优点：性能比面向对象高，适合跟硬件练习很紧密的东西

    缺点：没有面向对象容易维护、易复用、易扩展

    面向对象：

    优点：容易维护复用灵活 缺点：性能低
- 类和对象

    类抽象了对象的公共部分，它泛指某一大类

    对象特指某一个，通过类实例化一个具体的对象
- 创建类

```JavaScript
class name{
    constructor(uname){
        this.uname=uname;
    }

}
var x=new name();
```

    类constructor构造函数

    它是类的构造函数（默认方法），用于传递参数，返回实例对象，通过new命令生成对象实例时，自动调用该方法。如果没有先是定义，类内部会自动给我们创建一个constructor()
- 类中添加共有方法

```JavaScript
class name{
    constructor(uname){
        this.uname=uname;
    }
    //类里面所有函数不需要写function,函数之间不加，逗号分隔
    sing(){
        console.log("好运来")；
        
    }

}
var x=new name();
```
- 类的继承

    extends和super关键字

```JavaScript
class Father{
    constructor(){}
    money(){console.log(100);}
}
class Son extends Father{//儿子继承父亲的属性和方法
    
}
var son=new Son();
console.log(son.money);//100
```

```JavaScript
class Father{
    constructor(x,y){
         this.x=x;
         this.y=y;
    }
    sum(){
        console.log(this.x+this.y);
    }
}
class Son extends Father{
    constructor(x,y){
        this.x=x;
        this.y=y;
    }
}
var son =new Son(1,2);
son.sum();//报错，因为1，2是给子类的，父类没有
```

```JavaScript
class Father{
    constructor(x,y){
         this.x=x;
         this.y=y;
    }
    sum(){
        console.log(this.x+this.y);
    }
}
class Son extends Father{
    constructor(x,y){
        super(x,y);//调用了父类中的构造函数
    }
}
var son =new Son(1,2);
son.sum();
```

    super关键字用于访问和调用对象父类上的函数。可以调用父类的构造函数，也可以调用父类的普通函数。

    #### 当父亲和儿子有相同的方法，优先儿子的方法，若儿子没有再往上寻找父类的方法。就近原则。

```JavaScript
class Father{
    say(){
        return '我是爸爸'
    }
}
class Son extends Father{
    say(){
        console.log(super.say()+'的儿子')
    }
}
var son =new Son();
son.say();
```
- super必须放到子类this之前

```JavaScript
class Father{
    constructor(x,y){
        this.x=x;
        this.y=y;
    }
    sum(){
        cosole.log(this.x+this.y);
    }
    
}
class Son extends Father{
   constructor(x,y){
       super(x,y);
       this.x=x;
       this.y=y;
   }
    substract(){
        console.log(this.x-this.y);
    }

}
var son=new Son(5,3);
son.substract();
son.sum();
```
- 类和对象三个注意点

    没有变量提升，所以需要先有类才可以实例化

    类里面共有的属性和方法一定要加this使用

    类里This的指向问题
- 在es6之前，对象不是基于类创建的，而是一种称为构造函数的特殊函数来定义对象和他们的特征 

```JavaScript
//利用new Object()创建对象
//利用对象字面量创建对象
//利用构造函数创建对象
function Star(uname,age){
    this.uname=uname;
    this.age=age;
    this.sing=function(){
        console.log("sing")
    }
}
var ldh=new Star("刘德华",18);
console.log(ldh);
```

    构造函数是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，它总与new一起使用，我们可以把对象中一些公共属性和方法抽取出来，然后封装到这个函数里面。

    #### new执行时会做的四件事：

    1. 在内存中创建一个空的对象
    2. 让this指向这个新的对象
    3. 执行构造函数里面的代码，给这个新对象添加属性和方法
    4. 返回这个新对象，所以构造函数不需要return
- 实例成员和静态成员

    构造函数中的属性和方法我们称为成员，成员可以添加

    #### 实例成员就是构造函数内部通过this添加的成员 uname age sing就是实例成员，实例成员只能通过实例化对象来访问

    #### 静态成员在构造函数本身上添加的成员，静态成员只能通过构造函数来访问，不能通过对象来访问。

    构造函数方法很好用但存在内存浪费。
- 构造函数原型prototype

    构造函数通过原型分配的函数是所有对象共享的。javascript规定，每一个构造函数都有一个prototype属性，指向另一个对象，注意这个prototype就是·一个对象，这个对象的所有属性和方法都会被构造函数所拥有。

    我们可以把那些不变的方法，直接定义在prototype对象上这样所有的对象实例就可以共享这些方法。

```JavaScript
function Star(uname,age){
    this.uname=uname;
    this.age=age;
    /*this.sing=function(){
        console.log("sing")
    }*/
    
}
Star.prototype.sing=function(){
    console.log("sing");
}
var ldh=new Star("刘德华",18);
var zxy=new Star("张学友",20);
console.log(ldh);
console.log()
```

    一般情况下我们的公共属性定义的到构造函数里面，公共的方法我们放到原型对象身上

    #### 原型是什么？

    原型是一个对象，每一个构造函数系统定义好了这么一个对象。

    每个原型对象中都有 prototype 属性，指向一个对象，这个对象就叫做原型或者原

    型对象

    每个对象都有 **proto** ，指向构造函数的原型对象，层层递进到 null 为止
- 对象原型

    对象都会有一个属性__proto _ _指向构造函数的prototype原型对象，之所以我们对象可以使用构造函数prototype原型对象的y属性和方法就是因为对象有`_proto_`原型的存在

    对象`__proto__`和原型对象prototype是等价的

    方法的查找规则，首先先看ldh对象身上是否有sing方法，如果有就执行这个对象上的sing，如果没有，因为有proto的存在，就去构造函数原型对象prototype身上取查找sing这个方法。
- constructor 构造函数

    对象原型和构造函数原型对象里面都有一个属性constructor属性,constructor我们称为构造函数，因为它指回构造函数本身。

```JavaScript
console.log(Star.prototype.constructor);
console.log(ldh.__proto__.constructor);//Star(){}
```

    很多情况下我们需要手动的利用constructor手动的指回原来的构造函数。

```JavaScript
Star.prototype={
    cosntructor:Star,
    sing:function(){},
    movie:function(){}
}
```

    如果我们修改了原来的原型对象，给原型对象赋值的是一个对象，则必须手动的利用constructor指回原来的构造函数。

    ![](https://secure2.wostatic.cn/static/2YeWvek3RfSdLMwQwiMhZ7/image.png?auth_key=1690869090-jENtqkGBBNy5Boocu3D6zA-0-4a0bf8fe9c1b9bbdf50eefeaea0001b2)

### 1、作用域是什么

**javascript作用域**：就是代码名字（变量）在某个范围内起作用和效果，目的是为了提高程序的可靠性，更重要的是减少命名冲突。

**js作用域（es6）之前**：全局作用域、局部作用域

**全局作用域**：整个script标签或者是一个单独的js文件

**局部作用域（函数作用域）**：在函数内部就是局部作用域，这个代码的名字只在函数内部起效果和作用。

### 2、变量的作用域

根据作用域的不同变量分为两种：全局变量、局部变量；

1）全局变量：在全局作用域下的变量 在全局都可以使用

**注意**：如果在函数内部没有声明直接赋值的变量也叫全局变量

2）局部变量：在局部作用域下（函数内部）的变量，只能在局部作用域下（函数内部）使用

**注意**：函数的形参也可以看作是局部变量,在局部作用域下修改全局变量，只在局部作用域内有效果，其他地方使用全局变量不会被修改。

3）从执行效率来看全局变量、局部变量

（1）全局变量只有浏览器关闭的时候才会销毁，比较占内存资源

（2）局部变量当我们程序执行完毕就会销毁，比较节约内存资源。

4）js当前阶段是没有块级作用域（在es6之后才新增的块级作用域）

**es6:块级作用域{} if{} for{} 块级作用域里，外面不能调用；**es6用let声明的变量不会被作用域外调用，var声明的可以。

### 3、作用域链

- 只要是代码，就至少有一个作用域链
- 写在函数内部的局部作用域
- 如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域
- 根据在内部函数可以访问外部函数变量的这种机制，用链式查找决定哪些数据能被内部函数访问，就称作—作用域链

内部函数访问外部函数的变量，采取的是链式查找的方式来决定取那个值这种结构我们称为作用域链（就近原则）

### 4、预解析

1）js引擎（解析器）运行js分两步：预解析、代码执行

  （1）预解析 js引擎会把js里面所有的var还有function提升到当前作用域的最前面

  （2）代码执行 按照代码的书写顺序从上往下执行

2）预解析分为变量预解析（变量提升）和函数预解析（函数提升)
      (1）变量提升就是把所有的变量声明提升到当前的作用域最前面﹑不提升赋值操作

函数表达式，变量提升的效果：（所以函数表达式不能利用函数提升，调用时只能在声明之后）

![](https://secure2.wostatic.cn/static/mG8tDyfCLz8tJZ9f9o2uwd/image.png?auth_key=1690869099-bxbNz9Bgx4vYq4B2XUZh8-0-034233d3b52043967dccbafe13974808)

     (2）函数提升就是把所有的函数声明提升到当前作用域的最前面不调用函数

### 5、变量属性函数方法的总结

1. 变量单独声明并赋值，使用的时候直接写变量名，单独存在属性在对象里面的不需要声明的，使用的时候必须是对象.属性

2．函数和方法的相同点 都是实现某种功能做某件事，函数是单独声明并且调用的函数名(）单独存在的；

方法在对象里面，调用的时候 对象.方法(）

### 6、Data()

1.获取当前时间必须实例化

var now = new Date () ;console.log (now) ;

2.Date()构造函数的参数

如果括号里面有时间，就返回参数里面的时间。例做日期格式字符串为‘2019-5-1’，可以写成new Date('2019-5-1')或者new Date('2019/5/1')

![](https://secure2.wostatic.cn/static/3cdWomXwpxpkTbUB8wfET1/image.png?auth_key=1690869099-pCsqtSRb9ogAuQwfqFKx3D-0-43d32e48c917497326ea0344ecdb7055)

### 7、日期格式化

![](https://secure2.wostatic.cn/static/79bbW2NacitHf7gPZtQgZQ/image.png?auth_key=1690869098-6wsLb9ZUCtn3AzAWHUBpF4-0-782cccedc6d0205a85e9c912698efa91)

### 8、获得总的毫秒数

![](https://secure2.wostatic.cn/static/oE3h6Bk5S3RcgNHBEnvFq4/image.png?auth_key=1690869098-2DUmz54nWRgZ9Z7ynT2gVD-0-50686c5638497ae2f6e8387d92982b8b)

**倒计时效果**

1. 核心算法: 输入的时间减去现在的时间就是剩余的时间，即倒计时，但是不能拿着时分秒相减，比如05分减去25分，结果会是负数的。
2. 用时间戳来做。用户输入时间总的毫秒数减去现在时间的总的毫秒数，得到的就是剩余时间的毫秒数
3. 把剩余时间总的毫秒数转换为天、时、分、秒(时间戳转换为时分秒)

    转换公式如下: 

    d = parseInt(总秒数/ 60/68 /24);//计算天数

    h = parseInt(总秒数/60/60 %24);//计算小时

    m = parseInt(总秒数/60 1%60 );//计算分数

    s = parseInt(总秒数%60);//计算当前秒数

### 9、基本包装类型

![](https://secure2.wostatic.cn/static/xaCyxopxGpdMR6wUyh6JTi/image.png?auth_key=1690869098-38Ksi54vFpaNHC3CCK2qfV-0-ac592826289627b2d4f950baf9afa328)

### 10、字符串不可变

指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。

### 11、DOM树和DOM对象

#### 11.1作用和分类

作用：就是用js去操作html和浏览器

分类：DOM（文档对象模型）、BOM（浏览器对象模型）

#### 11.2什么是DOM

- DOM：是用来呈现以及与任意HTML或XML文档交互的API
- 白话文：DOM是浏览器提供的一套专门用来操作网页内容的功能
- DOM作用：开发网页内容特效和实现用户交互

#### 11.3 DOM树

- DOM树是什么：将HTML文档以树状结构直观的表现出来，我们称之为文档树或DOM树。
- 描述网页内容关系的名词
- 作用：文档树直观的体现了标签与标签之间的关系

#### 11.4 DOM对象

DOM对象：浏览器根据html标签生成js对象
  - 所有的标签属性都可以在这个对象上面找到
  - 修改这个对象的属性会自动映射到标签身上

### 12 获取DOM对象

目标：能查找/获取DOM对象

提问：我们想要操作某个标签首先做什么？

  首先选中这个标签，跟css选择器类似，选中标签才能操作。

查找元素DOM元素就是利用js选择页面中标签元素。

#### 12.1 根据css选择器来获取DOM元素

1.选择匹配的第一个元素

```JavaScript
document.querySelector('css选择器')
```

  **参数**：包含一个或多个有效的css选择器字符串

  **返回值**：CSS选择器匹配的第一个元素，一个HTMLElement对象

2.选择匹配的多个元素

```JavaScript
document.querySelectorAll('ul li')
```

  **参数**：包含一个或多个有效的css选择器 字符串

  **返回值**：css选择器匹配的NodeList对象集合

  得到的是一个伪数组：

  - 有长度有索引号的数组
  - 但是没有pop() push()等数组方法

  想要得到里面的每一个对象，则需要遍历（for）的方式获得。

  ### 13 操作元素内容

  目标：能够修改元素的文本更换内容

  - DOM对象都是根据标签生成的，所以操作标签本质上就是操作DOM对象。
  - 就是操作对象使用的点语法。
  - 如果想要修改标签元素的里面的内容，则可以使用如下几种方式
      1. 对象.innerText属性
          - 将文本内容添加/更新到任意标签位置
          - 显示纯文本，不解析标签
      2. 对象.innerHTML属性
          - 将文本内容添加/更新到任意标签位置
          - 会解析标签，多标签建议使用模板字符

  ### 14 操作元素属性

  #### 14.1操作元素常用属性

  - 还可以通过js设置/修改标签元素属性，比如src更换图片
  - 最常见的属性比如:href、title、src等
  - 语法：对象.属性=值

  #### 14.2操作元素的样式属性

  - 通过style属性操作css：对象.style.样式属性 = '' 如果属性中有横杠，横杠需要取消，横杠后的单词首字母大写。

      ![](https://secure2.wostatic.cn/static/g9uL2v6DWoKzj6txG3YcNt/image.png?auth_key=1690869097-noyqUEGofzooPA9V4naoTa-0-5e328774299210a7c56a0b13f0d55fc6)
  - 操作类名操作css：

      如果修改的样式比较多，直接通过style属性修改比较繁琐，我们可以通过借助于css类名的形式。

      **语法：**

      元素.className = 'active'

      **注意：**

      1. 由于class是关键字，所以使用className去替代
      2. className是使用新值换旧值，如果需要添加一个类，需要保留之前的类名

      ![](https://secure2.wostatic.cn/static/2HMKzHv4EgVWdvwqLa3hSt/image.png?auth_key=1690869097-tvH4AFLsPALZkQD54xHgoi-0-7fc8710f7674b1f6c44be52613c4ffe9)
  - 通过classList操作类控制css

      为了解决className容易覆盖以前的类名，我们可以通过classList方式追加和删除类名

      **语法：**

      ![](https://secure2.wostatic.cn/static/5HnkNJNhdfU3zeEWztbWo6/image.png?auth_key=1690869094-2BCyUU227onaR9e3URQMWz-0-89c500a8a1b1df200fc3d52628594372)

### 15 获取设置表单的值
  - 元素.value（获取值，不能通过元素.innerHTML获取了）
  - 元素.type（获取类型：text、password）

  表单属性中添加就有效果，移除就没有效果，一律使用布尔值表示，如果为true代表添加了该属性 如果是false代表移除了该属性

  比如：disabled、checked、selected

### 16自定义属性

- 标准属性：标签天生自带的属性 比如class id title 等，可以直接使用点语法操作，比如：disabled、checked、selected
- 自定义属性：
    - 在html5推出来了专门的data-自定义属性
    - 在标签上一律以data-开头
    - 在DOM对象上一律以dataset对象方式获取,dataset是对象集合

    ![](https://secure2.wostatic.cn/static/63eD4xtXCgCzNFGHERU8mf/image.png?auth_key=1690869094-kkM1zk6dnhjkZdLVxJ6A19-0-33f280a6542e40bf7a1897eeaabfb0e3)

### 17 BOM

是浏览器对象模型

![](https://secure2.wostatic.cn/static/9ZoRNdXHuVMcxD3u3ZnKwJ/image.png?auth_key=1690869094-x3QTHTxHUMV1RByqG189yx-0-67ecd497972442e72168a84d45fa2a8a)

- window对象是一个全局对象,也可以说是javascript中的顶级对象
- 像document  alert() console.log() 这些都是window的属性,基本BOM的属性和方法都是window的.
- 所有通过var定义在全局作用域中的变量 函数都会变成window对象的属性和方法
- window对象下的属性和方法调用的时候可以省略window

### 18同步和异步任务

![](https://secure2.wostatic.cn/static/r2sBDrXETsEZ2DGmTzYupH/image.png?auth_key=1690869094-oJiCezRrNvdM7QHmi7xox5-0-d01ed8909d5b82f572d29bbfc77c68d1)

![](https://secure2.wostatic.cn/static/aGjjVE3BZgs6dGWXD3beh4/image.png?auth_key=1690869094-roDgxhfrme2Zd3wJUiENq9-0-69aeb48b0da39e92df78753a44097744)

![](https://secure2.wostatic.cn/static/xbZUoLhAvYf2JhLhE9WfPe/image.png?auth_key=1690869094-77CZd7zdGnm8EAA6baUhFZ-0-07e316276d8e6c72b1b9ae3ed012451e)

同步任务→微任务→宏任务(执行过程中若有微任务则下一个执行宏任务
