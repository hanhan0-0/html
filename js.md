## js

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

  ![c](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308084408714.png)

- 变量

  只是声明不赋值，会输出undefined

  不声明不赋值直接使用会报错

  不声明直接赋值  能使用但是会变成全局变量

  ![image-20220308090115054](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308090115054.png)

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

![image-20220308091907627](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308091907627.png)

1. str.length 输出字符串的长度 

2. 字符串用+拼接 只要是有字符型的最后还是字符串型的

   ```
   var age=18;
   console.log("今年age岁")//今年age岁
   console.log("今年"+age+"岁")//今年18岁
   ```

- 布尔型boolen 

  true在加法中当作1来看 false在运算中当作0来看 

- Undefined null

  如果一个变量声明未赋值，就是undefined 未定义数据类型

  ![image-20220308093006964](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308093006964.png)

  ![image-20220308093046333](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308093046333.png)

   null 值为空

  ![image-20220308093217512](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308093217512.png)

  

- typeof

  检测变量数据类型 prompt取得的值是字符型的

- 数据类型的转换

  1. 转换为字符串

     toString()  num.toString() 

     String()强制类型转换 String(num)

     加号拼接字符串的方法 num+''

  2. 转换成数字型

     ![image-20220308094351018](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308094351018.png)

  3. 转换成boolean

     ![image-20220308094724512](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308094724512.png)

     

### 3-3 js操作运算符

- 算术运算符

  ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308095010339.png)

  尽量避免浮点数直接参与运算

  ```
  var num=0.1+0.3;
  console.log(num==0.4)//false
  ```

- 表达式和返回值

  表达式：由数字、运算符、变量等组成的式子我们称之为表达式

  表达式都会返回一个结果这个结果称为返回值。

- 前置/后置递增运算符

  ![image-20220308095638176](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308095638176.png)

### 3-4 流程控制

顺序结构、分支结构、循环结构

```
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

```
function 函数名()
{
    函数体
}
```

​    调用函数：函数名();

![image-20220308102502486](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308102502486.png)

​    函数没有return则返回undefined

- arguments

  是当前函数的一个内置对象，里面存了函数的所有实参

  伪数组：具有数组的length属性，按照索引的方式进行存储，它没有真正数组的一些方法 pop() push()等等

- 函数可以调用另一个函数

- 函数的两种声明方式

  函数表达式：变量里面存的是函数，也可以传递参数

  ```js
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

    ```js
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

  ```
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

    ```js
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

    ```js
    var obj=new Object();//创建了一个空的对象obj.uname='xiaomi'obj.age=18;obj.sex="男";obj.sayHi=function(){}//(1)利用等号赋值的方法添加属性和方法//(2)每个属性和方法用分号结束
    ```

  - 为什么要用构造函数创建对象呢

    因为前面两种创建对象的方式一次只能创建一个对象

    因此我们可以利用函数的方法重复这些相同的代码，我们就把这个函数称为构造函数。

    构造函数：把我们对象里面一些相同的属性和方法抽象出来封装到函数里面。

  - 构造函数创建对象

    ```js
    /*function 构造函数名(){   this.属性 =值;   this.方法 = function(){}}*///构造函数首字母要大写//构造函数不需要returnnew 构造函数名();funtion Star(uname,age,sex){    this.name=uname;    this.age=age;    this.sex=sex;    this.sing=function(sang){        console.log(sang);    }}var ldh=new Star("刘德华",18,"男");
    ```

  - new 执行过程

    1. new构造函数可以在内存中创建了一个空的对象
    2. this就会指向刚才创建的空对象
    3. 执行构造函数里面的代码 给这个空对象添加属性和方法
    4. 返回这个对象

  - 遍历对象

    for in语句用于对数组和对象进行循环

    ```js
    //for(变量 in 对象){}for(var k in obj){    console.log(k);//k变量 输出 得到的是 属性名    console(obj[k]);//得到的是里面的属性值}
    ```

    方法也能遍历出来 fn是方法名  f(){}是值

### 3-8 内置对象

- Math对象

  

- 日期对象

### 3-9 简单类型和复杂类型

基本包装类型：就是把简单数据类型包装成为了复杂数据类型

![image-20220308133036068](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308133036068.png)

- 字符串的不可变

  指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。

- 根据字符返回位置

  字符串多有的方法都不会修改字符串本身，操作完成会返回一个新的字符串

  ```
  str.indexOf('要查找的字符'，[起始的位置])；
  ```

  ![image-20220308133941213](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220308133941213.png)

- 返回字符位置和次数

- 根据位置返回字符

  charAt(index);

- this
  谁调用就指向谁   



## b站

- 面向对象

  特性：封装性、继承性、多态性

  ##### 面向过程和面向对象对比：

  面向过程：

  优点：性能比面向对象高，适合跟硬件练习很紧密的东西

  缺点：没有面向对象容易维护、易复用、易扩展

  面向对象：

  优点：容易维护复用灵活 缺点：性能低

- 类和对象

  类抽象了对象的公共部分，它泛指某一大类

  对象特指某一个，通过类实例化一个具体的对象

- 创建类

  ```js
  class name{    constructor(uname){        this.uname=uname;    }}var x=new name();
  ```

  类constructor构造函数

  它是类的构造函数（默认方法），用于传递参数，返回实例对象，通过new命令生成对象实例时，自动调用该方法。如果没有先是定义，类内部会自动给我们创建一个constructor()

- 类中添加共有方法

  ```js
  class name{    constructor(uname){        this.uname=uname;    }    //类里面所有函数不需要写function,函数之间不加，逗号分隔    sing(){        console.log("好运来")；            }}var x=new name();
  ```

- 类的继承

  extends和super关键字

  ```js
  class Father{    constructor(){}    money(){console.log(100);}}class Son extends Father{//儿子继承父亲的属性和方法    }var son=new Son();console.log(son.money);//100
  ```

  ```js
  class Father{    constructor(x,y){         this.x=x;         this.y=y;    }    sum(){        console.log(this.x+this.y);    }}class Son extends Father{    constructor(x,y){        this.x=x;        this.y=y;    }}var son =new Son(1,2);son.sum();//报错，因为1，2是给子类的，父类没有
  ```

  ```js
  class Father{    constructor(x,y){         this.x=x;         this.y=y;    }    sum(){        console.log(this.x+this.y);    }}class Son extends Father{    constructor(x,y){        super(x,y);//调用了父类中的构造函数    }}var son =new Son(1,2);son.sum();
  ```

  super关键字用于访问和调用对象父类上的函数。可以调用父类的构造函数，也可以调用父类的普通函数。

  ##### 当父亲和儿子有相同的方法，优先儿子的方法，若儿子没有再往上寻找父类的方法。就近原则。

  ```js
  class Father{    say(){        return '我是爸爸'    }}class Son extends Father{    say(){        console.log(super.say()+'的儿子')    }}var son =new Son();son.say();
  ```

- super必须放到子类this之前

  ```js
  class Father{    constructor(x,y){        this.x=x;        this.y=y;    }    sum(){        cosole.log(this.x+this.y);    }    }class Son extends Father{   constructor(x,y){       super(x,y);       this.x=x;       this.y=y;   }    substract(){        console.log(this.x-this.y);    }}var son=new Son(5,3);son.substract();son.sum();
  ```

- 类和对象三个注意点

  没有变量提升，所以需要先有类才可以实例化

  类里面共有的属性和方法一定要加this使用

  类里This的指向问题

- 在es6之前，对象不是基于类创建的，而是一种称为构造函数的特殊函数来定义对象和他们的特征 

  ```js
  //利用new Object()创建对象//利用对象字面量创建对象//利用构造函数创建对象function Star(uname,age){    this.uname=uname;    this.age=age;    this.sing=function(){        console.log("sing")    }}var ldh=new Star("刘德华",18);console.log(ldh);
  ```

  构造函数是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，它总与new一起使用，我们可以把对象中一些公共属性和方法抽取出来，然后封装到这个函数里面。

  ##### new执行时会做的四件事：

  1. 在内存中创建一个空的对象
  2. 让this指向这个新的对象
  3. 执行构造函数里面的代码，给这个新对象添加属性和方法
  4. 返回这个新对象，所以构造函数不需要return

- 实例成员和静态成员

  构造函数中的属性和方法我们称为成员，成员可以添加

  ##### 实例成员就是构造函数内部通过this添加的成员 uname age sing就是实例成员，实例成员只能通过实例化对象来访问

  ##### 静态成员在构造函数本身上添加的成员，静态成员只能通过构造函数来访问，不能通过对象来访问。

  构造函数方法很好用但存在内存浪费。

- 构造函数原型prototype

  构造函数通过原型分配的函数是所有对象共享的。javascript规定，每一个构造函数都有一个prototype属性，指向另一个对象，注意这个prototype就是·一个对象，这个对象的所有属性和方法都会被构造函数所拥有。

  我们可以把那些不变的方法，直接定义在prototype对象上这样所有的对象实例就可以共享这些方法。

  ```js
  function Star(uname,age){    this.uname=uname;    this.age=age;    /*this.sing=function(){        console.log("sing")    }*/    }Star.prototype.sing=function(){    console.log("sing");}var ldh=new Star("刘德华",18);var zxy=new Star("张学友",20);console.log(ldh);console.log()
  ```

  一般情况下我们的公共属性定义的到构造函数里面，公共的方法我们放到原型对象身上

  ##### 原型是什么？

  原型是一个对象，每一个构造函数系统定义好了这么一个对象。

  每个原型对象中都有 prototype 属性，指向一个对象，这个对象就叫做原型或者原

  型对象

  每个对象都有 __proto__ ，指向构造函数的原型对象，层层递进到 null 为止

- 对象原型

  对象都会有一个属性__proto _ _指向构造函数的prototype原型对象，之所以我们对象可以使用构造函数prototype原型对象的y属性和方法就是因为对象有`_proto_`原型的存在

  对象`__proto__`和原型对象prototype是等价的

  方法的查找规则，首先先看ldh对象身上是否有sing方法，如果有就执行这个对象上的sing，如果没有，因为有proto的存在，就去构造函数原型对象prototype身上取查找sing这个方法。

- constructor 构造函数

  对象原型和构造函数原型对象里面都有一个属性constructor属性,constructor我们称为构造函数，因为它指回构造函数本身。

  ```js
  console.log(Star.prototype.constructor);console.log(ldh.__proto__.constructor);//Star(){}
  ```

  很多情况下我们需要手动的利用constructor手动的指回原来的构造函数。

  ```js
  Star.prototype={    cosntructor:Star,    sing:function(){},    movie:function(){}}
  ```

  如果我们修改了原来的原型对象，给原型对象赋值的是一个对象，则必须手动的利用constructor指回原来的构造函数。

  ![image-20220412155259689](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220412155259689.png)







