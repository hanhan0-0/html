## Class 1 Ts简介

### Ts 是什么？

以javascript为基础构建的语言，一个javascript的超集。Ts扩展了js并添加了类型。可以在任何支持js的平台中执行。Ts不能被js解析器直接执行，需要编译为Js再执行。

### Ts增加了什么？

类型

支持es的新特性

添加es不具备的新特性

丰富的配置选项

强大的开发工具

## Class 2 开发环境

### 搭建TS开发环境搭建

1. 使用npm全局安装typeScript  
    1. 进入命令行
    2. 输入npm i -g typescript
2. 创建一个ts文件
3. 使用tsc对ts文件进行编译
    1. 进入命令行
    2. 进入ts文件所在目录
    3. 执行命令：tsc xxx.ts

## Class 3 Ts中的类型

### 基本类型

- 类型声明
    - 类型声明是ts非常重要的一个特点
    - 通过类型声明可以指定ts中变量（参数、形参）的类型
    - 指定类型后，当为变量赋值时，ts编译器会自动检查值是否符合类型声明，符合则复制，否则报错
    - 简而言之，当类型声明给变量设置了类型，使得变量只能存储某种类型的值
    - 语法：

```JavaScript
let 变量:类型;
let 变量:类型 = 值;
function fn(参数:类型，参数:类型):类型{
  ...
}
```
- 自动类型判断
    - ts拥有自动的类型判断机制
    - 当对变量的声明和赋值是同时进行的，ts编译器会自动判断变量的类型
    - 所以如果你的变量的声明和赋值时同时进行的，可以省略掉类型的声明
- 类型

    ![](https://secure2.wostatic.cn/static/bKgFtEHhmS1MkJ2GMeLX4M/image.png?auth_key=1691120285-ehNSMNWgkbjTFwh26TeyL3-0-889eff41da5c80dbf4ae05c90ac7d36a)

    - number

```JavaScript
let decimal:number = 6;


```

注意：
  1. 先声明再赋值时，要在声明处声明类型
  2. 如果声明和赋值同时进行，ts可以自动对变量进行类型检测。不需要声明类型。
  3. 声明可以在函数中使用，参数和返回值都可以加上
  4. 可以使用|来连接多个类型（联合类型），若是字面量作为联合类型则限制变量在某几个值之间。其他类型作为联合类型，则这个变量可以赋值这几个类型的值。

```JavaScript
let a:'male'|'female'
let b: boolean | string
```
  5. any表示的是任意类型，一个变量设置any后，相当于对该变量关闭了ts的类型检测，使用ts时不建议使用any类型。声明变量如果不指定类型，则ts解析器会自动判断变量的类型为any。any类型的变量可以赋值给任意变量。
  6. unknow表示未知类型的值。可以给unknow类型的变量赋任意值，但是不能将这个unknow类型的变量直接赋值给别的类型的值，可以用以下方式间接赋值。

```JavaScript
//第一种方法
let e:unknown;
let s:string;
e='hello'
if(typeof e === 'string'){
  s = e;
}
//第二种方法

//类型断言,可以用来告诉解析器变量的实际类型
s = e as string 
s = <string> e
```
  7. void用来表示空，以函数为例，就表示没有返回值的函数，但还是有undefined
  8. never表示永远不会返回结果，如下，一报错函数就立即结束，立即结束就没有返回值

```JavaScript
function fn2():never{
  throw new Error('报错了')
}
```
  9. {}用来指定对象中可以包含哪些属性

      语法：{属性名：属性值，属性名？：属性值}加一个问号表示可选属性

```JavaScript
//[propName:string]:any 表示可选填任意类型的属性
let c:{name : string , [propName:string]:any}
//表示要求这个函数有两个Number类型的参数，返回值也为number
let d:(a:number,b:number)=>number
```
  10. 数组两种声明方式

```JavaScript
//表示字符串数组
let e:string[]
//表示数字数组
let g:Array<number>;
```
  11. 元组，就是固定长度的数组,语法：[类型，类型，类型]

```JavaScript
let h:[string,string]
```
  12. enum枚举

```JavaScript
enum Gender{
  Male = 0;
  Female = 1;
}
let i:{name :string ,gender:Gender};
i ={
  name:'孙悟空',
  gender:Gender.Male
}
```
  13. &表示同时

```JavaScript
let j:{name:string}&{age:number};
j = {name:'孙悟空',age:18}//同时满足有两个对象属性

```
  14. 类型的别名

```JavaScript
type myType = 1|2|3|4|5
let k:myType
let l:myType
let m:myType
```

## Class 4 Ts的编译选项

### 自动编译文件

- 编译文件时，使用-w指令后，Ts编译器会自动监视文件的变化，并在文件发生变化时对文件进行重新编译
- 示例

```JavaScript
tsc xxx.ts -w
```

### 自动编译整个项目

- 如果直接使用tsc指令，则可以自动将当前项目下的所有ts文件编译为js文件
- 但是能直接使用tsc命令的前提是，要先在项目的根目录下创建一个Ts的配置文件tsconfig.json
- tsconfig.json是一个JSON文件，添加配
- 置文件后，只需tsc命令即可完成对整个项目的编译
- 配置选项：
    - include
        - 定义希望被编译文件所在的目录
        - 默认值["**/*"]

            两个*表示任意目录，一个*表示任意文件
        - 示例

```JavaScript
"include":["src/**/*","tests/**/*"]
```

            上述示例中，所有src目录和tests目录下的文件都会被编译
    - exclude
        - 定义需要排除在外的目录
        - 默认值：["node_modules","bower_components","jspm_packages"]
        - 示例

```JavaScript
"excludes":["./src/hello/**/*"]
```
    - extends
        - 定义被继承的配置文件
        - 示例：

```JavaScript
"extends":"./configs/base"
```

            上述示例中，当前配置文件中会自动包含config目录下base.json中的所有配置信息
    - files
        - 指定被编译文件的列表，只有需要编译的文件少时才会用到
        - 示例

```JavaScript
"files":[
  "core.ts",
  "sys.ts",
  "types.ts",
  "scanner.ts",
  "parser.ts",
  "utilities.ts"
]
```

            列表中的文件都会被ts编译器所编译
    - compilerOptions
        - 编译选项是配置文件中非常重要也比较复杂的配置选项
        - 在compilerOptions中包含多个子选项，用来完成对编译的配置
            - 项目选项
                - target
                    - 设置ts代码编译的目标版本
                    - 可选值

                        ES3（默认）、ES5、ES6/ES2015......ES2020、ESNext
                    - 示例

```JavaScript
"compilerOptions":{
  "target":"ES6"
}
```

                        如上设置，我们所编写的ts代码将会被编译为ES6版本的js代码
                - lib
                    - 指定代码运行时所包含的库（宿主环境）
                    - 可选值
                        - ES5、ES6/ES2015......ES2020、ESNext、DOM、WebWorker、ScriptHost...
                    - 示例

```JavaScript
"compilerOptions":{
  "lib":["ES6","DOM"]
}
```
                - module
                    - 指定要使用的模块化规范
                    - 可选值
                        - 'none'，'commonjs','umd','amd','System','es6'......'esnext'
                    - 示例

```JavaScript
"compilerOptions":{
  "modules":"es2015"
}
```
                - outDir
                    - 用来指定编译后文件所在的目录
                    - 示例

```JavaScript
"compilerOptions":{
  "outDir":"./dist"
}
```

                        
                - outFile
                    - 将代码合并为一个文件
                    - 示例

```JavaScript
"compilerOptions":{
  "outFile":"./dist/app.js"
}
```
                - allowJs
                    - 是否对js文件进行编译，默认是false
                    - 示例

```JavaScript
"compilerOptions":{
  "allowJs":false
}
```
                - checkJs
                    - 是否检查js代码是否符合语法规范，默认是false
                    - 示例

```JavaScript
"compilerOptions":{
  "checkJs":false
}
```
                - removeComments
                    - 是否移除注释,默认是true
                - noEmit
                    - 不生成编译后的文件
                - noEmitOnError
                    - 有错误时不生成编译后的文件
                - alwaysStrict
                    - 默认是false，用来设置编译后的文件是否使用严格模式
                - noImplicitAny
                    - 不允许隐式的any类型
                - noImplicitThis
                    - 不允许不明确类型的this
                - strictNullChecks
                    - 严格的检查空值
                - strict
                    - 所有严格检查的总开关

## Class 5 使用webpack打包ts代码

- 通常情况下，实际开发中我们都需要使用构建工具对代码进行打包；
- TS同样也可以结合构建工具一起使用，下边以webpack为例介绍一下如何结合构建工具使用TS；

    步骤如下：
      - 初始化项目：
          - 进入项目根目录，执行命令  `npm init -y`，创建package.json文件来管理项目
      - 下载构建工具
          - 命令如下：

```JavaScript
npm i -D webpack webpack-cli webpack-dev-server typescript ts-loader clean-webpack-plugin
```
          - 共安装了7个包
              - webpack：构建工具webpack
              - webpack-cli：webpack的命令行工具
              - webpack-dev-server：webpack的开发服务器
              - typescript：ts编译器
              - ts-loader：ts加载器，用于在webpack中编译ts文件
              - html-webpack-plugin：webpack中html插件，用来自动创建html文件
              - clean-webpack-plugin：webpack中的清除插件，每次构建都会先清除目录
      - 配置webpack

          根目录下创建webpack的配置文件 webpack.config.js:

```JavaScript
//引入一个包
const path = require('path')
//
module.exports = {
    //指定入口文件
    entry: "./src/index.ts",
    //指定打包文件所在目录
    output: {
        //指定打包文件的目录
        path: path.resolve(__dirname, 'dist'),
        //打包后文件的文件
        filename: "bundle.js"
    },
    //指定webpack打包时要使用的模块
    module: {
        //指定要加载的规则
        rules: {
            //指定的是规则生效的文件
            test: "/\.ts$/",
            //要使用的loader
            use: 'ts-loader',
            //要排除的文件
            exclude: /node_module/
        }
    }
}
```

    - 配置TS编译选项
        - 根目录下创建tsconfig.json，配置可以根据自己需要

```JavaScript
{
    "compilerOptions": {
        "module": "ES2015",
        "target": "ES2015",
        "strict": true
    }
}
```
    - 修改package.json配置
        - 配置如下

```JavaScript
{
  ...
  "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "build": "webpack"
    },
  ...
 }
```
    - 项目使用

        在src下创建ts文件，并在并命令行执行`npm run build`对代码进行编译；

        或者执行`npm start`来启动开发服务器；
- npm i -D html-webpack-plugin帮助自动生成html文件

    在webpack.config.js文件中引入，再在plugins中引入

```JavaScript
const HtmlWebpackPlugin = require("html-webpack-plugin");
module.exports = {
plugins: [
       new HtmlWebpackPlugin({
           title:'TS测试',
           //根据模板来生成html文件
           template:"./src/index.html"
       }),
   ]
  }

```
- 安装这个插件，webpack-dev-server，安装内置的服务器，可以根据项目的改变自动更新

    在package.json中配置

```JavaScript
"scripts":{
  "start":"webpack serve -- open chrome.exe"
}
```

## Class 6 面向对象

面向对象是程序中一个非常重要的思想，一切操作都要通过对象，也就是所谓的面向对象，那么对象到底是什么呢？这就要先说到程序是什么，计算机程序的本质就是对现实事物的抽象，抽象的反义词是具体，比如：照片是对一个具体的人的抽象，汽车模型是对具体汽车的抽象等等。程序也是对事物的抽象，在程序中我们可以表示一个人、一条狗、一把枪等等所有的事物，一个事物到了程序中就变成了一个对象。

在程序中所有对象都被分成了两个部分，数据和功能，数据在对象中被称为属性，而功能就被称为方法。所以简而言之，在程序中一切皆是对象。

### 1、类

想要面向对象，操作对象，首先便要拥有对象，那么下一个问题就是如何创建对象，必须要先定义类，所谓的类可以理解为对象的模型，程序中可以根据类创建指定类型的对象，举例来说：可以通过Person类来创建人的对象，通过Dog类创建狗的对象，不同的类可以用来创建不同的对象。

### 定义类

```JavaScript
class 类名 {
属性名: 类型;

constructor(参数: 类型){

  this.属性名 = 参数;

}

方法名(){

  ....

}
}
```

```JavaScript
示例：
class Person{

  name: string;

  age: number;

  constructor(name: string, age: number){

    [this.name](http://this.name) = name;

    this.age = age;

  }

  sayHello(){

    console.log(`大家好，我是${this.name}`);

  }

}
使用类：

const p = new Person('孙悟空', 18);
p.sayHello();

```

### 构造函数

可以使用`constructor`定义一个构造器方法；

> **注1：在TS中只能有一个构造器方法！**

例如：

```JavaScript
class C{
name: string;

age: number

constructor(name: string, age: number) {

  [this.name](http://this.name) = name;

  this.age = age;

}
}

```

```JavaScript
同时也可以直接将属性定义在构造函数中：

class C {

  constructor(public name: string, public age: number) {

  }

}
```

上面两种定义方法是完全相同的！

**注2：子类继承父类时，必须调用父类的构造方法（如果子类中也定义了构造方法）！**

例如：

```JavaScript
class A {
protected num: number;

constructor(num: number) {

  this.num = num;

}

}

class X extends A {

  protected name: string;

  constructor(num: number, name: string) {

    super(num);

    [this.name](http://this.name) = name;

  }

}

```

如果在X类中不调用`super`将会报错！

### 封装

对象实质上就是属性和方法的容器，它的主要作用就是存储属性和方法，这就是所谓的封装

默认情况下，对象的属性是可以任意的修改的，为了确保数据的安全性，在TS中可以对属性的权限进行设置

- 静态属性（static）：
    - 声明为static的属性或方法不再属于实例，而是属于类的属性；
- 只读属性（readonly）：
    - 如果在声明属性时添加一个readonly，则属性便成了只读属性无法修改
- TS中属性具有三种修饰符：
    - public（默认值），可以在类、子类和对象中修改
    - protected ，可以在类、子类中修改
    - private ，可以在类中修改

示例：

```JavaScript
public：
class Person{

  public name: string; // 写或什么都不写都是public

  public age: number;

  constructor(name: string, age: number){

    [this.name](http://this.name) = name; // 可以在类中修改

    this.age = age;

  }

  sayHello(){

    console.log(`大家好，我是${this.name}`);

  }

}

class Employee extends Person{

  constructor(name: string, age: number){

    super(name, age);

    [this.name](http://this.name) = name; //子类中可以修改

  }

}

const p = new Person('孙悟空', 18);
[p.name](http://p.name) = '猪八戒';// 可以通过对象修改

protected：

class Person{

  protected name: string;

  protected age: number;

  constructor(name: string, age: number){

    [this.name](http://this.name) = name; // 可以修改

    this.age = age;

  }

  sayHello(){

    console.log(`大家好，我是${this.name}`);

  }

}

class Employee extends Person{

  constructor(name: string, age: number){

    super(name, age);

    [this.name](http://this.name) = name; //子类中可以修改

  }

}

const p = new Person('孙悟空', 18);
[p.name](http://p.name) = '猪八戒';// 不能修改

private：

class Person{

  private name: string;

  private age: number;

  constructor(name: string, age: number){

    [this.name](http://this.name) = name; // 可以修改

    this.age = age;

  }

  sayHello(){

    console.log(`大家好，我是${this.name}`);

  }

}

class Employee extends Person{

  constructor(name: string, age: number){

    super(name, age);

    [this.name](http://this.name) = name; //子类中不能修改

  }

}

const p = new Person('孙悟空', 18);
[p.name](http://p.name) = '猪八戒';// 不能修改

```

### 属性存取器

对于一些不希望被任意修改的属性，可以将其设置为private

直接将其设置为private将导致无法再通过对象修改其中的属性

我们可以在类中定义一组读取、设置属性的方法，这种对属性读取或设置的属性被称为属性的存取器

读取属性的方法叫做setter方法，设置属性的方法叫做getter方法

示例：

```JavaScript
class Person{
private _name: string;

constructor(name: string){

  this._name = name;

}

get name(){

  return this._name;

}

set name(name: string){

  this._name = name;

}

}

const p1 = new Person('孙悟空');
// 实际通过调用getter方法读取name属性
console.log([p1.name](http://p1.name));
// 实际通过调用setter方法修改name属性
[p1.name](http://p1.name) = '猪八戒'; 

```

### 静态属性

静态属性（方法），也称为类属性。使用静态属性无需创建实例，通过类即可直接使用

静态属性（方法）使用static开头

示例：

```JavaScript
class Tools{
static PI = 3.1415926;

static sum(num1: number, num2: number){

  return num1 + num2

}

}

console.log(Tools.PI);
console.log(Tools.sum(123, 456));

```

### this

在类中，使用this表示当前对象

### 继承

继承时面向对象中的又一个特性

通过继承可以将其他类中的属性和方法引入到当前类中

示例：

```JavaScript
class Animal{
name: string;

age: number;

constructor(name: string, age: number){

  [this.name](http://this.name) = name;

  this.age = age;

}

}



class Dog extends Animal{
bark(){

  console.log(`${this.name}在汪汪叫！`);

}

}

const dog = new Dog('旺财', 4);
dog.bark();



```

通过继承可以在不修改类的情况下完成对类的扩展

### 重写

发生继承时，如果子类中的方法会替换掉父类中的同名方法，这就称为方法的重写

示例：

```JavaScript
class Animal{
name: string;

age: number;

constructor(name: string, age: number){

  [this.name](http://this.name) = name;

  this.age = age;

}

run(){

  console.log(`父类中的run方法！`);

}

}

class Dog extends Animal{

  bark(){

    console.log(`${this.name}在汪汪叫！`);

  }

  run(){

    console.log(`子类中的run方法，会重写父类中的run方法！`);

  }

}

const dog = new Dog('旺财', 4);
dog.bark();

```

**在子类中可以使用super来完成对父类的引用**

### 抽象类（abstract class）

抽象类是专门用来被其他类所继承的类，它只能被其他类所继承不能用来创建实例

```JavaScript
abstract class Animal{
abstract run(): void;

bark(){

  console.log('动物在叫~');

}

}

class Dog extends Animals{

  run(){

    console.log('狗在跑~');

  }

}

```

使用abstract开头的方法叫做抽象方法，抽象方法没有方法体只能定义在抽象类中，继承抽象类时抽象方法必须要实现;

## Class7接口（Interface）

接口的作用类似于抽象类，不同点在于：接口中的所有方法和属性都是没有实值的，换句话说接口中的所有方法都是抽象方法；

接口主要负责定义一个类的结构，接口可以去限制一个对象的接口：对象只有包含接口中定义的所有属性和方法时才能匹配接口；

同时，可以让一个类去实现接口，实现接口时类中要保护接口中的所有属性；

示例（检查对象类型）：

```JavaScript
interface Person{
name: string;

sayHello():void;

}

function fn(per: Person){

  per.sayHello();

}

fn({name:'孙悟空', sayHello() {console.log(`Hello, 我是 ${this.name}`)}});

```

示例（实现）：

```JavaScript
interface Person{
name: string;

sayHello():void;

}

class Student implements Person{

  constructor(public name: string) {

  }

  sayHello() {

    console.log('大家好，我是'+[this.name](http://this.name));

  }

}

```

## Class8泛型（Generic）

定义一个函数或类时，有些情况下无法确定其中要使用的具体类型（返回值、参数、属性的类型不能确定）；

此时泛型便能够发挥作用；

举个例子：

```JavaScript
function test(arg: any): any{
return arg;}
```

上例中，test函数有一个参数类型不确定，但是能确定的时其返回值的类型和参数的类型是相同的；

由于类型不确定所以参数和返回值均使用了any，但是很明显这样做是不合适的：

首先使用any会关闭TS的类型检查，其次这样设置也不能体现出参数和返回值是相同的类型；

### 泛型函数

#### 创建泛型函数

```JavaScript
function test<T>(arg: T): T{
return arg;

}

```

这里的`<T>`就是泛型；

T是我们给这个类型起的名字（不一定非叫T），设置泛型后即可在函数中使用T来表示该类型；

所以泛型其实很好理解，就表示某个类型；

那么如何使用上边的函数呢？

#### 使用泛型函数

#### 方式一（直接使用）：

test(10)

使用时可以直接传递参数使用，类型会由TS自动推断出来，但有时编译器无法自动推断时还需要使用下面的方式

#### 方式二（指定类型）：

test<number>(10)

也可以在函数后手动指定泛型；

#### 函数中声明多个泛型

可以同时指定多个泛型，泛型间使用逗号隔开：

```JavaScript
function test<T, K>(a: T, b: K): K{
return b;

}

test<number, string>(10, "hello");

```

使用泛型时，完全可以将泛型当成是一个普通的类去使用；

### 泛型类

类中同样可以使用泛型：

```JavaScript
class MyClass<T>{
prop: T;

constructor(prop: T){

  this.prop = prop;

}

}

```

### 泛型继承

除此之外，也可以对泛型的范围进行约束

```JavaScript
interface MyInter{
length: number;

}

function test<T extends MyInter>(arg: T): number{

  return arg.length;

}

```

使用T extends MyInter表示泛型T必须是MyInter的子类，不一定非要使用接口类和抽象类同样适用；
