## CSS

### 2-1 CSS基本选择器

1. 简介

   美化网页，布局页面。css是层叠样式表的简称。也是一种标记语言。主要用于设置HTML页面中的文本内容（字体、大小、对齐方式等）、图片的外形（宽高、边框样式、边距等）以及版面的布局和外观显示样式。

   CSS最大价值：由HTML专注去做结构呈现，样式交给CSS，即结构与样式分离。

2. CSS语法规范

   - CSS规则由两个主要部分构成：选择器以及一条或多条声明。

     ![image-20220106220119737](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220106220119737.png)

     ```html
     <style>
             /* css通常在head标签中 写在style中*/
             /* 选择器{样式}=给谁改样式{改什么样式} */
             p {
                 /* 修改颜色 */
                 color: aqua;
                 /* 修改大小,px是像素 */
                 font-size: 12px;
             }
     </style>
     ```

     1）属性和属性值以键值对的形式来显示。

     2）属性与属性值之间用英文的“：”分开

     3）每一组键值对用“；”来结尾。

3. CSS代码风格

   - 样式格式书写

     用展开（不要全写在一行）的格式来写，更直观。

     一般情况都用小写字母。

   - 空格规范

     1）属性值前面，冒号后面，保留一个空格。

     2）选择器和大括号中间保留空格。

4. CSS选择器的作用

   选择器（选择符）就是根据不同需求把不同的标签选出来，这就是选择器的作用，简单来说就是选择标签用的。

5. 标签选择器

   选择器分为基础选择器和复合选择器两个大类。

   - 基础选择器是由单个选择器组成的

   - 基础选择器又包括：标签选择器、类选择器、id选择器和通配符选择器。

     - 标签选择器：是指用HTML标签名称作为选择器，按标签名称分类，为页面中某一类型标签制定统一的CSS样式。优点：能快速为页面中同类型的标签统一设置样式。缺点：不能设计差异化样式，只能选择全部的当前的标签。

       ```html
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1.0">
           <meta http-equiv="X-UA-Compatible" content="ie=edge">
           <title>CSS</title>
           <style>
               ul {
                   color: red;
               }
           </style>
       </head>
       
       <body>
           <ul>
               <li>哈喽</li>
           </ul>
       </body>
       ```

       

     - 类选择器：单独选择一个或者某几个标签。

       类选择器口诀：样式点定义，结构类调用。一个或多个，开发最常用。

       ```html
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1.0">
           <meta http-equiv="X-UA-Compatible" content="ie=edge">
           <title>CSS</title>
           <style>
               .red {
                   color: red;
               }
           </style>
       </head>
       <body>
           <p>改变段落</p>
           <ul>
               <li class="red">hh</li>
           </ul>
           <ol>
               <li>a</li>
           </ol>
           <p class="red">你好</p>
           <p>大家好</p>
       </body>
       ```

       1）类选择器使用“.”（英文符号）进行标识，后面紧跟类名（自定义）

       2）类名不能用标签的名字

       3）选择器命名时很长的时候可以用段横杠来分割。

       4）不要使用纯数字、中文等命名，尽量使用英文字母来表示。

       ```html
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1.0">
           <meta http-equiv="X-UA-Compatible" content="ie=edge">
           <title>CSS</title>
           <style>
               .red {
                   width: 100px;
                   height: 100px;
                   color: red;
               }
               .green {
                   width: 100px;
                   height: 100px;
                   background-color: green;
               }
           </style>
       </head>
       
       <body>
           <div class="red"> 红色</div>
           <div class="green"></div>
           <div class="red">红色</div>
       ```

6. 类选择器-多类名

   我们可以给一个标签指定多个类名，从而达到更多的选择目的。这些类名都可以选出这个标签。

   - 多类名使用方式，类名间用空格分开。

   - 多类名方便后面修改。

     使用场景：1）可以把一些标签元素相同的样式（共同的部分）放到一个类中。

     ​                   2）这些标签都可以调用这个公共的类，然后再调用自己独有的类。

     ```html
     <div class="red size"></div>
     ```

7. id选择器

   - id选择器可以为标有特定id的html元素指定特定的样式。

   - html元素以id属性来设置id选择器，CSS中id选择器以"#"来定义。
   - id选择器的口诀：样式#定义，结构id调用，只能调用一次，别人切勿使用。

   ```html
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <meta http-equiv="X-UA-Compatible" content="ie=edge">
       <title>CSS</title>
       <style>
           #red {
               width: 100px;
               height: 100px;
               background-color: red;
           }
       </style>
   </head>
   <body>
       <div id="red"></div>
   </html>
   ```

   ##### id选择器和类选择器的区别：

   1）类选择器可以有多个名字，同一个名字也可以被多个人使用。

   2）id选择器不能重复使用。

   3）类选择器在修改样式中用的最多，id选择器一般用于页面唯一性的元素上，经常和js搭配使用。

8. 通配符选择器

   在css中，通配符选择器用“*”定义，它表示选取页面中所有元素（标签）

   ```html
   <style>
           * {
               color: red;
           }
           /* 这里把html body div span li等标签都改为了红色 */
    </style>
   ```

   

### 2-2 CSS样式

- 字体属性

  CSS Fonts（字体）属性用于定义字体系列、大小、粗细、和文字样式（如斜体）。

  1. 字体系列

     ```html
     p {font-family:"微软雅黑";}
     div {
          font-family:Arial,"Microsoft Yahei","微软雅黑";
     }
     ```

     - 各种字体之间必须使用英文状态下的逗号隔开。

     - 一般情况下，如果有空格隔开的多个单词组成的字体，加引号

     - 尽量使用系统默认自带字体，保证任何用户都能显示

     - 写多种字体为了保证，前一个用户没有可以用下一种字体显示，优先第一个。如果都没有就会以电脑浏览器默认字体显示。

     - 最常见的几个字体

       body {font-family: 'Microsoft Yahei',tahoma,arial,'Hiragino Sans GB';}

       这种设置body的，标题不会受到影响。

  2. 字体大小

     ```html
     p {
        font-size: 20px;
     }
     ```

     - px(像素)大小是我们网页最常用的单位
     - 谷歌浏览器默认的文字大小为16px
     - 不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小。
     - 可以给body指定整个页面文字大小。除了标题标签以外，需要单独指定文字大小。

  3. 字体粗细

     ```html
     p {
        font-weight: normal;
     }
     ```

     ![image-20220107151829978](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107151829978.png)

     当值为400时效果等同于normal。700效果等同于bord

  4. 文字样式

     ```html
     <style>
         /* 让字体变的倾斜 */
         p {
             font-style: italic;
         }
         /* 让倾斜的字体变得不倾斜 */
         em {
             font-style: normal;
         }
     </style>
     ```

  5. 字体的复合属性

     ```html
     <style>
               div {
                   /* font-size: 16px;
                   font-family: "Microsoft Yahei";
                   font-weight: 700;
                   font-style: initial; */
                   /* font: font-style font-weight font-size/line-height font-family 顺序不能变 */
                   font: initial 700 16px "Microsoft Yahei"
               }
     </style>
     ```

     - 使用font属性时，必须按上面语法格式中的顺序书写，不能更换顺序，并且各个属性间用空格隔开。
     - 不需要设置的属性可以省略（取默认值），但必须保留font-size和font-family属性，否则font属性将不起作用。

- CSS文本属性

  CSS Text（文本）属性可定义文本的外观，比如文本的颜色、对齐文本、装饰文本、文本缩进、行间距等。

  1. 文本颜色

     color属性用于定义文本的颜色。

     ```html
         <style>
             h1 {
                 /* color: hotpink; */
                 /* color: #f523d2; 16进制 */
                 color: rgb(209, 24, 169);
             }
         </style>
     ```

     ![image-20220107165340091](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107165340091.png)

     开发中用的最多的是16进制。

  2. 对齐文本

     text-align属性用于设置元素内文本内容的水平对齐方式。

     ```html
         <style>
             h1 {
                 /* 本质是让h1盒子里的文字在水平居中对齐 */
                 text-align: center;
             }
         </style>
     ```

     ![image-20220107165849407](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107165849407.png)

  3. 装饰文本

     text-decoration属性规定添加到文本的修饰，可以给文本添加下划线、删除线、上划线等。

     ```html
     <style>
         div {
             text-decoration: underline;
         }
     </style>
     ```

     ![image-20220107171955570](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107171955570.png)

     ##### 一个属性常用的地方：

     将链接的下划线去掉。

     ```html
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <meta http-equiv="X-UA-Compatible" content="ie=edge">
         <title>CSS</title>
         <style>
             a {
                 text-decoration: none;
                 color: black;
             }
         </style>
     </head>
     
     <body>
         <a href="#">一个不带下划线的链接</a>
     </body>
     ```

  4. 文本缩进

     text-indent属性用来指定文本的第一行缩进，通常是将段落进行首行缩进。

     ```html
     <style>
             /* 正值往里凹，负值往外凸 */
             p {
                 text-indent: 20px;
             }
     </style>
     ```

     属性值也可以取em；em是一个相对单位，就是当前元素(font-size)一个文字的大小，如果当前元素没有设置大小，则会按照父元素的1个文字大小。

  5. 行间距

     line-height属性用于设置行间的距离（行高），可以控制文字行与行的距离。文本高度不会变，是上间距和下间距发生改变。

     ```html
         <style>
             p {
                 /* 文字16px，上间距和下间距各为5px */
                 line-height: 25px;
             }
         </style>
     ```

- CSS引入方式

  1. CSS的三种样式表

     - 行内样式表（行内式）
     - 内部样式表（嵌入式）
     - 外部样式表（链接式）

  2. 内部样式表（内嵌样式表）是写html页面内部，是将所有CSS代码抽取出来，单独放到一个`<style>`标签中。

     ```html
     <style>
         div {
             color: red;
             font-family: "Microsoft Yahei";
             font-size: 16px;
             text-indent: 2em;
         }
     </style>
     ```

     - `<style>`理论上是可以放到html文档的任何一个位置，但一般会放在文档的`<head>`标签中。
     - 通过这种方式，可以方便控制当前整个页面中的元素样式设置。
     - 代码结构清晰，但是并没有实现结构与样式完全分离。
     - 使用内部样式表设定CSS，通常也被称为嵌入式引入。

  3. 行内样式表

     行内样式表（内联样式表）是在元素标签内部的style属性中设定CSS样式，适合于修改简单样式。

     ```html
     <div style="color: red;font-size: 12px;">
         青春不常在，抓紧谈恋爱。
     </div>
     ```

     - style其实就是标签的属性。
     - 在双引号中间，写法要符合CSS规范
     - 可以控制当前的标签设置样式。

  4. 外部样式表

     实际发开都是外部样式表，适合于样式比较多的情况，核心是：单独写CSS文件中，之后把CSS文件引入到HTML页面中使用。

     引入外部样式表分为两步：

     1）新建一个后缀名为.css的样式文件，把所有css代码都放入此文件中

     2）在HTML页面中，使用`<link>`标签引入这个文件。

     ```html
     <link rel="stylesheet" href="css文件路径">
     ```

     ![image-20220108000029583](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108000029583.png)

- Chrome调试工具

  打开Chrome浏览器，按F12或者右击页面空白处再点检查。

  点击elements（元素）结构在左边，样式在右边。

  ![image-20220108162837130](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108162837130.png)

### 2-3

- Emmet语法

  Emmet语法的前身是Zen coding，它使用缩写，来提高html/css的编写速度，Vscode内部已经集成该语法。

  1. 快速生成HTML结构语法

     ![image-20220108170404338](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108170404338.png)

  2. 快速生成CSS样式语法

     CSS基本采取简写的形式再按tab即可。

  3. 快速格式化代码

     ctr+s 或者 右键再点击格式化文档（快捷键为Alt + shift +f）

- CSS的复合选择器

  1. 复合选择器简介

     复合选择器是建立在基础选择器之上的，对基本选择器进行组合形成的。

     - 复合选择器可以更准确，更高效的选择目标元素（标签）
     - 复合选择器是由两个或者多个基础选择器，通过不同的方式组合而成的
     - 常用的复合选择器包括：后代选择器，子选择器，并集选择器，伪类选择器

  2. 后代选择器（重要）

     后代选择器又称为包含选择器，可以选择父元素里面的子元素，其写法就是把外层标签写在前面，内层标签写在后面，中间用空格分隔，当标签发生嵌套时，内层标签据成为外层标签的后代。

     语法：元素1 元素2 {样式声明}

     ```html
      <style>
             ol li {
                 color: pink;
             }
         </style>
     ```

     1）元素1和元素2中间用空格隔开。

     2）元素1是父级，元素2是子级，最终选择是元素2。

     3）元素2可以是儿子，也可以是孙子等，只要是元素1的后代即可。

     4）元素1和元素2可以是任意的基础选择器

     ```html
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <meta http-equiv="X-UA-Compatible" content="ie=edge">
         <title></title>
         <style>
             ol li a {
                 color: pink;
             }
             
             ul li .asb {
                 text-decoration: none;
             }
         </style>
     </head>
     
     <body>
         <ol>
             <li><a href="#" >年后</a></li>
         </ol>
         <ul>
             <li><a href="#" class="asb">年后</a></li>
         </ul>
     </body>
     ```

  3. 子选择器（重要）

     子元素选择器（子选择器）只能选择作为某元素的最近一级子元素，简单理解就是选亲儿子元素。只要是儿子都可以。

     语法：元素1>元素2>（样式声明）

     ```html
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <meta http-equiv="X-UA-Compatible" content="ie=edge">
         <title></title>
         <style>
             div>a {
                 color: red;
             }
         </style>
     </head>
     
     <body>
         <div>
             <!-- 变红了 -->
             <a href="#">hello</a>
             <p>
                 <!-- 没变红 -->
                 <a href="#"> hello1</a>
             </p>
             <!-- 变红了 -->
             <a href="#">2222</a>
         </div>
     
     </body>
     ```

     1）元素1和元素2中间用大于号隔开

     2）元素1是父级，元素2是子级，最终选择的是元素2

     3）元素2必须是亲儿子，其孙子、重孙子之类都不归它管，也可称作儿子选择器。

  4. 并集选择器（重要）

     并集选择器可以选择多组标签，同时为他们定义相同的样式，通常用于集体声明。

     并集选择器是各选择器通过英文逗号（，）连接而成，任何形式的选择器都可以作为并集选择器的一部分。

     语法：元素1,元素2{样式声明}

     ```html
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <meta http-equiv="X-UA-Compatible" content="ie=edge">
         <title></title>
         <style>
             p,
             span>h2,
             span h3 a {
                 color: red;
             }
         </style>
     </head>
     <body>
         <!-- 变红 -->
         <p>你也好</p>
         <span>
             <!-- 变红 -->
             <h3><a href="#">百度</a></h3>
             <!-- 变红 -->
             <h2>2</h2>
             <!-- 没变红 -->
             <h3>3</h3>
             <div>
                 <!-- 没变红 -->
                 <h2>新闻</h2>
             </div>
             <!-- 没变红 -->
             <h2><a href="#">新浪</a></h2>
         </span>
     </body>
     ```

     1）元素1和元素2中间用逗号隔开。

     2）语句可以理解为和的意思。

     3）并集选择器通常用于集体声明。

  5. 伪类选择器

     伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或者选择第1个，第n个元素。

     伪类选择器书写最大的特点是用冒号（：）表示，比如:hover、:first-child

     - 链接伪类选择器

       a:link        选择所有未被访问的链接

       a:visited   选择所有已被访问的链接

       a:hover     选择鼠标指针位于其上的链接

       a:action     选择活动链接（鼠标按下未弹起的链接）

       ```html
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1.0">
           <meta http-equiv="X-UA-Compatible" content="ie=edge">
           <title>复合链接的使用</title>
           <style>
               /* 最开始的颜色 */
               a:link {
                   color: #333;
                   text-decoration: none;
               }
               /* 看过后的颜色 */
               a:visited {
                   color: rgb(218, 39, 83);
                   text-decoration: none;
               }
               /* 鼠标放上去的颜色 */
               a:hover {
                   color: rgb(94, 94, 250);
               }
               /* 按下还没弹起的颜色 */
               a:active {
                   color: rgb(17, 0, 255);
               }
           </style>
       </head>
       
       <body>
           <a href="http://baidu.com" target="_blank">百度</a>
           <a href="https://www.sina.com.cn/" target="_blank">新浪</a>
           <a href="http://qq.com" target="_blank">腾讯</a>
           <a href="http://360.com" target="_blank">360</a>
       </body>
       ```

       ##### 链接伪类注意事项：

       1）为了确保生效，按照link visited hover active的书讯来声明

       2）因为a链接在浏览器中具有默认样式，所以我们实际工作中都要给链接单独指定样式。

       ##### 链接伪类实际开发中经常写法：

       ```html
           <style>
               /* 最常用写法 */
               a {
                   color: rgb(252, 7, 7);
                   text-decoration: none;
               }
               a:hover {
                   color: blue;
                   text-decoration: underline;
               }
           </style>
       ```

     - focus伪类选择器

       用于选取获得焦点的表单元素。焦点就是光标，一般情况`<input>`表单元素才能获取，因此这个选择器也主要针对于表单元素来说。

       ```html
           <style>
               input:focus {
                   background-color: rgb(79, 182, 241);
               }
           </style>
       
       <body>
           <input type="text" />
       </body>
       
       ```

### 2-4

- 元素的显示模式

  了解元素的显示模式可以更好地让我们布局页面。

  1. 什么是元素的显示模式

     元素显示模式就是元素（标签）以什么方式显示，比如`<div>`自己占一行，比如一行可以放多个`<span>`

     HYML元素一般可以分为块元素和行内元素两种类型。

  2. 块元素

     常见的块元素有`<h1>-<h6>`、`<p>`、`<div>、<ul>、<ol>、<li>`等其中div是最典型的块元素。

     块元素的特点：

     - 自己独占一行
     - 宽度、高度、外边距、内边距都可以控制
     - 宽度默认是容器（父亲宽度）的100%
     - 是一个容器及盒子，里面可以放行内或者块级元素。

     注意：

     - 文字类的元素内不能hi用块级元素（比如p里不能放div，h1-h6等都是文字类块级标签，里面也不能放其他块元素。）

  3. 行内元素

     行内元素也叫内联元素。span标签是最典型的行内元素。

     行内元素的特点：

     - 一行可以放多个行内元素
     - 宽和高直接设置是无效的
     - 默认宽度就是它本身内容的宽度
     - 行内元素只能容纳文本或其他行内元素

     注意：

     - 链接里不能再链接
     - 

  4. 行内块元素

- CSS的背景

- CSS的三大特性

- CSS的注释

