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
                   font: italic 700 16px "Microsoft Yahei"
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

### 2-3 css复合选择器

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

### 2-4 元素显示模式

了解元素的显示模式可以更好地让我们布局页面。

- 什么是元素的显示模式

  元素显示模式就是元素（标签）以什么方式显示，比如`<div>`自己占一行，比如一行可以放多个`<span>`

  HYML元素一般可以分为块元素和行内元素两种类型。

- 块元素

  常见的块元素有`<h1>-<h6>`、`<p>`、`<div>、<ul>、<ol>、<li>`等其中div是最典型的块元素。

  块元素的特点：

  1. 自己独占一行
  2. 宽度、高度、外边距、内边距都可以控制
  3. 宽度默认是容器（父亲宽度）的100%
  4. 是一个容器及盒子，里面可以放行内或者块级元素。

  注意：

  1. 文字类的元素内不能hi用块级元素（比如p里不能放div，h1-h6等都是文字类块级标签，里面也不能放其他块元素。）

- 行内元素

  行内元素也叫内联元素。span标签是最典型的行内元素。

  行内元素的特点：

  1. 一行可以放多个行内元素
  2. 宽和高直接设置是无效的
  3. 默认宽度就是它本身内容的宽度
  4. 行内元素只能容纳文本或其他行内元素

  注意：

  1. 链接里不能再链接
  2. 特殊情况链接a里面可以放块级元素，但是a转换一下块级模式最安全。

- 行内块元素

  在行内元素中有几个特殊的标签img、input、td他们同时具有块元素和行内元素的特点，有些资料称其为行内块元素。

  特点：

  1. 和相邻行内块元素在一行上，但它们之间会有空白间隙（行内元素没有空隙），一行上可以放多个。
  2. 默认宽度就是它本身内容的宽度
  3. 高度，行高，外边距以及内边距都可以控制。

- 元素显示模式的转换

  特殊情况下，我们需要元素模式的转换，简单理解一个模式的元素需要另一种模式的特性。比如要想要增加链接a的触发范围。

  ```html
      <style>
          a {
              width: 150px;
              height: 70px;
              /* 把行内元素转换为块元素 */
              display: block;
          }
          
          div {
              width: 150px;
              height: 70px;
              /* 把块元素转换为行内元素 */
              display: inline;
          }
          
          span {
              width: 200px;
              height: 100px;
              background-color: antiquewhite;
              /* 把行内元素转化为行内块元素 */
              display: inline-block;
          }
      </style>
  ```

- 一个软件的使用snipaste

  常用快捷方式：

  1. F1可以截图，同时测量大小，设置箭头，书写文字等。
  2. F3在桌面置顶显示。
  3. 点击图片，alt可以取色（按下shift可以切换取色模式）
  4. 按下esc取消图片显示。

- 让单行文字垂直居中

  解决方案：让文字的行高line-height等于盒子的高度，就可以让文字在当前盒子内垂直居中。因为上间距和下间距发生改变。

##### 一个实践代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        a {
            height: 48px;
            width: 276px;
            background-color: rgb(82, 86, 87);
            color: #f8f8f8;
            text-decoration: none;
            line-height: 48px;
            text-align: center;
            display: block;
        }
        
        a:hover {
            background-color: rgb(239, 91, 7);
        }
    </style>
</head>

<body>
    <a href="#">手机</a>
    <a href="#">电脑</a>
    <a href="#">平板</a>
    <a href="#">冰箱</a>
    <a href="#">电视机</a>
</body>

</html>
```

### 2-5 CSS的背景

通过css背景属性，可以给页面元素添加背景样式。

背景属性可以设置背景颜色、背景图片、背景平铺、背景图片位置、背景图像固定等。

- 背景颜色

  background-color:颜色值。

  一般情况下元素的背景默认颜色是transparent（透明），我们也可以手动指定背景颜色为透明色。

- 背景图片

  background-image属性描述了元素的背景图像，实际开发常见于logo或者一些装饰性的小图片或者是超大的背景图片，有点事非常便于控制位置（精灵图也是一种运用场景）

  background-image:none/url();

  ```html
      <style>
          div {
              width: 700px;
              height: 300px;
              background-image: url(../29.png);
          }
      </style>
  ```

- 背景平铺

  1. 如果需要在html页面上对背景图片进行平铺（就是当图片大小小于规定区域的大小时，重复复制图片使其充满整个规定区域），可以使用background-repeat.

  2. 默认情况下背景图片是平铺的。

  3. background-repeat：no-repeat（不平铺）/repeat(平铺）/repeat-x（沿着x轴平铺）/repeat-y（沿着y轴平铺）

  4. 背景颜色和背景图片不冲突，背景颜色会在背景图片覆盖不到的地方显示。简单说背景图片的图层在背景颜色的上方。

- 背景位置

  利用background-position属性可以改变图片在背景中的位置。

  background-position:x y;

  参数代表的意思是：x坐标和y坐标。可以使用方位名词或精确单位。

  ![image-20220111181848806](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111181848806.png)

  1. 参数是方位名词

    1）如果指定的两个值都是方位名词，则两top left效果一致个值前后顺序无关，比如left top 和top left效果一致

    2）如果只指定了一个方位名词，另一个值省略，则第二个值默认居中对齐。

  2. 参数是精确单位

    1）左上角是00位置，第一个参数一定是x坐标，第二个参数一定是y坐标

    2）如果只指定一个数值，则该数值一定是x坐标，另一个默认垂直居中

  3. 参数是混合单位

    1）两个单位一个是精确单位一个是方位名词，第一个参数一定是x的值 第二个一定是y的值

- 背景图像固定（背景附着）

  background-attachment属性设置背景图像是否固定或者随着页面的其余部分滚动，它后期可以制作视差滚动的效果。

  background-attachment：scroll | fixed;

  scroll    背景图像是随对象内容滚动，默认也是这个效果。

  fixed     背景图像固定

- 背景属性复合写法

  像font一样吧属性合并在同一个属性background中。没有特定的顺序，一般习惯约定的顺序为：背景颜色 背景图片地址 背景平铺 美景图象滚动 背景图片位置。

  ```html
      <style>
          body {
              background: red url(../29.png) no-repeat fixed center;
          }
      </style>
  ```

- 背景色半透明

  background: rgba(0,0,0,0.3)

  1. 最后一个参数就是透明度，取值在0-1之间。没有0也可以，直接写.4

  2. 背景半透明是指盒子背景半透明，盒子里面的内容不受影响。

  3. css3新增属性，是IE9+版本浏览器才支持的

  4. 实际开发中不关注兼容性写法了，可以放心使用。

    ```html
          div {
              width: 100px;
              height: 30px;
              background: rgba(0, 0, 0, 0.7)
          }
    ```

### 2-6 CSS的三大特性

层叠性、继承性、优先性。

- 层叠性

  相同的选择器设置相同的样式，此时一个样式就会覆盖（层叠）另一个冲突的样式，层叠性主要解决样式冲突的问题。

  ##### 层叠性原则：

  1）样式冲突，遵循的原则是就近原则，哪个样式离结构金，就执行哪个样式

  2）样式不冲突，选择器一样，不会重叠。

- 继承性

  子标签会继承父标签的某些样式,比如字号和文本颜色，简单说就是子承父业。

  text- font- line-这些开头的可以继承以及color属性。

- 行高的继承

  1. 行高可以跟单位也可以不跟单位

  2. 不跟单位时，如果子元素没有设置行高，则会继承父亲元素的行高为不跟单位的数字例如为1.5

  3. 此时子元素行高：当前子元素文字大小*1.5。

  4. 子元素没有规定大小时，跟父亲大小一样再乘上1.5。

- 优先级

  当同一个元素指定多个选择器，就会有优先级的产生。

  1. 如果选择器相同，则执行层叠性

  2. 选择器不用时，按如下来排

    #### 选择器        选择器权重

  继承或*        0，0，0，0

  元素选择器      0，0，0，1

  类选择器或伪类选择器    0，0，1，0

  id选择器       0，1，0，0

  行内样式       1，0，0，0

  ！important    无穷大
    
    ##### 注意事项：

    1）权重是有四组数字组成，但是不会有进位。

    2）可以理解为类选择器永远大于元素选择器，id选择器永远大于类选择器

    3）等级判断从左向右，如果某一位数值相同，则判断下一位数值。

    在样式的后面加上！important就是最重要的

    ```html
  .nac {
          color: rgb(239, 91, 7)!important;
       }
    ```

    a链接浏览器默认制定了一个样式，是蓝色有下划线。

- 权重的叠加

  如果使用复合选择器，则会有权重叠加问题，需要计算权重

  例子：

  ![image-20220112010331334](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112010331334.png)
  ul li 的权重为0,0,0,1+0,0,0,1=0,0,0,2
  .nav li的权重为0,0,1,0+0,0,0,1 = 0,0,1,1

### 2-7  css盒子模型

网页布局要学习三大核心，盒子模型、浮动和定位，学习好盒子模型能非常好的帮助我们布局页面。

- 看透网页布局的本质

  网页布局过程：

  1. 先准备好相关的网页元素，网页元素基本都是盒子box
  2. 利用css设置好和资阳市，然后摆放到相应位置
  3. 往盒子里面装内容

  网页布局核心本质：就是利用css摆盒子。

- 盒子模型组成部分

  所谓盒子模型：就是把HTML页面中的布局元看作是一个矩形的盒子，也就是一个盛装内容的容器。css盒子模型本质上是一个盒子，封装周围的HTML元素，它包括：边框、外边距、内边距和实际内容。

  ![image-20220112225703043](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112225703043.png)

- 边框border

  border可以设置元素的边框，边框有三部分组成：边框宽度（粗细）、边框样式、边框颜色

  语法：

  ```
  border:border-width || border-style || border-color
  ```

  ```style
     <style>
          div{
              width:200px;
              height: 200;
              /* border-width 边框的粗细，一般情况下单位都用px */
              border-width: 5px;
              /* border-style 边框的样式 solid实线边框 dashed虚线边框 dotted点线边框 */
              border-style: solid;
              /* border-color 边框的颜色 */
              border-color: pink;
          }
      </style>
  ```

- 边框的复合写法

  css边框属性允许指定一个元素边框的样式和颜色。

  边框缩写：

  ```
  border:1px solid pink;没有顺序
  ```

  边框分开写法：

  ```html
      <style>
          div{
              width:200px;
              height: 200;
              border-top: 1px solid pink;
              border-bottom: 1px solid pink;
              border-left: 1px solid pink;
              border-right: 1px solid pink;
          }
      </style>
  ```

  只想让上边框不一样则：

  ```html
      <style>
          div{
              width:200px;
              height: 200;
              /* 顺序不能变，层叠性原理 */
              border: 1px dashed red;
              border-top: 1px solid pink;
          }
      </style>
  ```

- 表格细边框

  border-collapse属性控制浏览器绘制表格边框的方式，它控制相邻单元格的边框。

  语法：

  ```
  border-collapse：collapse;
  ```

  1. collapse是合并的意思
  2. border-collapse：collapse;表示相邻边框合并在一起。

  ```html
      <style>
          table,
          td,
          th {
              border: 1px solid black;
              border-collapse: collapse;
          }
      </style>
  ```

- 边框会影响盒子的实际大小

  边框会额外增加盒子的实际大小，因此我们有两种解决方案：

  1. 测量盒子大小的时候，不量边框
  2. 如果测量的时候包含了边框，则需要width/height减去边框宽度。左右都有边框的时候减去边框的双倍宽度。

- 内边距(padding)

  padding属性用于设置内边距，即边框与内容之间的距离。

  ```html
      <style>
          div {
              width: 100px;
              height: 100px;
              border: 1px solid black;
              padding-left: 30px;
              padding-top: 10px
          }
      </style>
  ```

![image-20220112232042121](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112232042121.png)

- padding复合属性

  ![image-20220113000437627](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113000437627.png)

- padding影响盒子的实际大小

  如果盒子已经有了宽度和高度，此时再指定内边框，会撑大盒子。

  解决方案：

  如果保证盒子跟效果图大小保持一致，则让width/height减去多出来的内边距大小即可。

- padding应用

  盒子里因为每一个里面的字数不一样多，所以为了美观不给盒子设置宽度，而是直接给padding最合适。

  例子：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=<device-width>, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .nav {
            height: 37px;
            border-top: 3px solid #ff8500;
            border-bottom: 1px solid #edeef0;
            background-color: #fcfcfc;
            line-height: 41px;
        }
        
        a {
            height: 37px;
            padding-left: 20px;
            padding-right: 20px;
            font-size: 12px;
            text-decoration: none;
            color: #4c4c4c;
            display: inline-block;
        }
        
        a:hover {
            background-color: #eee;
            color: #ff8500;
        }
    </style>
</head>

<body>
    <div class="nav">
        <a href="#">你好</a>
        <a href="#">新浪微博</a>
        <a href="#">碍手碍脚打赏</a>
        <a href="#">你好吗</a>
        <a href="#">哈哈</a>
    </div>
</body>

</html>
```

- padding不会撑开盒子的情况

  1. 如果盒子本身没有指定width/weigth属性则此时padding不会撑开盒子大小。
  2. 继承关系，子元素虽然继承父元素的宽度，但是只要本身不设置width/weigth属性padding就不会撑开盒子大小。

- 外边距

  margin属性用于设置外边距，即控制盒子和盒子之间的距离。

  ![image-20220113001955197](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113001955197.png)

  margin简写方式和padding是一样的。

- 外边距典型应用

  外边距可以让块级盒子水平居中，但是必须满足两个条件：

  1. 盒子必须制定了宽度（width)
  2. 盒子左右的外边距都设置为auto

  ```
  .header {width:200px;margin:0 auto;}
  ```

  常见的写法有以下三种：

  1. margin-left:auto; margin-right:auto;
  2. margin:auto;
  3. margin:0 auto;

  ```html
      <style>
          div {
              width: 100px;
              height: 100px;
              border: 1px solid black;
              margin: 100px auto;
          }
      </style>
  ```

  注意：以上方法是让块级元素水平居中，行内元素或者行内块元素水平居中就给父元素添加text-align:center；即可。

- 外边距合并

  使用margin定义块元素的垂直外边距时，可能会出现外边距的合并。

  主要有两种情况：

  1. 相邻块元素垂直外边距的合并

     当上下相邻的两个块元素（兄弟关系）相遇时，如果上面的元素有下外边距margin-bottom，下面的元素有上外边距margin-top，则它们之间的垂直间距不是margin-bottom与margin-top之和，而是取二者中较大的一个。

     解决方法：尽量只给一个盒子添加margin值。

     ![image-20220113010115912](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113010115912.png)

  2. 嵌套块元素垂直外边距的塌陷

     对于两个嵌套关系（父子关系）的块元素，父元素有上外边距的同时子元素也有上外边距，此时父元素会塌陷一个正值（子元素上外边距值-父元素上外边距值）。

     ![image-20220113010613657](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113010613657.png)

     解决方法：

     1. 可以为父元素定义上边框
     2. 可以为父元素定义上内边距
     3. 可以为父元素添加overflow:hidden

- 清除内外边距

  网页元素很多都带有默认的内外边距，而且不同的浏览器默认的也不一致。因此我们在布局前，首先要清除下网页元素的内外边距。

  ```html
  <style>
      * {
          padding: 0; /*清除内边距*/
          margin: 0; /*清除外边距*/
      }
  </style>
  ```

  注意：行内元素为了照顾兼容性，尽量只设置左右内外边距，但是转换为块级和行内块元素就可以了。

### 2-8 ps基本操作

因为网页美工大部分效果图都是利用ps来做的，所以以后我们大部分切图工作都是在ps里面完成

![image-20220113150142271](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113150142271.png)

![image-20220113150118825](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113150118825.png)

一个综合案例：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>产品案例</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        body {
            background-color: #f5f5f5;
        }
        
        .box {
            width: 300px;
            height: 415px;
            background-color: #fff;
            margin: 100px auto;
        }
        
        .box img {
            width: 100%;
            height: 70%;
        }
        
        .box .reviw {
            font-size: 13px;
            height: 30px;
            padding: 0px 20px;
            margin-top: 10px;
            text-indent: 2em;
        }
        
        .box .aapraise {
            font-size: 10px;
            color: #b0b0b0;
            margin-top: 20px;
            padding: 0px 20px;
        }
        
        .box .info {
            font-size: 13px;
            margin-top: 15px;
            padding: 0px 20px;
        }
        
        h4 {
            display: inline-block;
            font-weight: normal;
        }
        
        span {
            color: #ff6700;
        }
        
        em {
            font-style: normal;
            color: #b0b0b0;
            margin: 0px 5px;
        }
    </style>
</head>

<body>
    <div class="box">
        <img src="../image/2.jpg" alt="无法显示" title="姐姐和宝贝">
        <p class="reviw">
            2021年6月5日我们面基啦，超可爱的宝贝啦。
        </p>
        <div class="aapraise">吃自助、玩密室</div>
        <div class="info">
            <h4>lalalalalala</h4>
            <em>|</em>
            <span>快乐</span>
        </div>


    </div>
</body>

</html>
```

- 怎么去掉li前面的项目符号

  语法：

  ```
  list-style:none;
  ```

  快报综合案例：

  ```html
  <!DOCTYPE html>
  <html lang="en">
  
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>快报</title>
      <style>
          * {
              padding: 0;
              margin: 0;
          }
          
          .box {
              width: 248px;
              height: 163px;
              border: 1px solid #ccc;
              margin: 100px auto;
          }
          
          .box h3 {
              height: 32px;
              border-bottom: 1px dotted #ccc;
              font-size: 14px;
              font-weight: normal;
              line-height: 33px;
              padding-left: 15px;
          }
          
          .box ul li a {
              color: #666;
              font-size: 12px;
              text-decoration: none;
          }
          
          ul {
              padding-top: 7px;
          }
          
          li {
              list-style: none;
              padding-left: 21px;
              height: 23px;
              line-height: 23px;
          }
          
          .box ul li a:hover {
              color: blue;
              text-decoration: underline;
          }
      </style>
  </head>
  
  <body>
      <div class="box">
          <h3>品优购</h3>
          <ul>
              <li><a href="#">[特惠]爆款耳机五折秒！</a></li>
              <li><a href="#">[特惠]母亲节，健康好礼低至五折！</a></li>
              <li><a href="#">[特惠]爆款耳机五折秒！</a></li>
              <li><a href="#">[特惠]9.9元洗100张照片!</a></li>
              <li><a href="#">[特惠]禅泓智能空调立省1000</a></li>
          </ul>
      </div>
  </body>
  
  </html>
  ```

- 圆角边框

  I9及i9以上使用。

  在css3中，新增了圆角边框样式，这样我们的盒子就可以变成圆角的了。

  border-radius属性用于设置元素的外边框圆角。

  语法：

  ```html
  border-radius:length;
  ```

  radius半径（圆的半径）原理：（椭）圆与边框的交际形成圆角效果。

  ```html
  div {
              border-radius: 20px;
          }
  ```

  1. 参数值可以为数值或者百分比的形式

  2. 如果是正方形，想要设置为一个圆，把数值修改为高度或宽度的一般即可，或者直接写为50%

  3. 如果是一个矩形，设置为高度的一半就可以达成，上下边是直径，左右是半圆。

  4. 该属性是一个简写属性，可以跟四个值，分别代表左上角、右上角、右下角、左下角。两个值是第一个是左上和右下对角线，第二个值是右上和左下对角线。

  5. 分开写：border-top-left-radius               border-top-right-radius  

     ​                border-bottom-left-radius       border-bottom-right-radius

     ```html
     <style>
             .yuanxing {
                 width: 200px;
                 height: 200px;
                 background-color: pink;
                 /* 要做一个圆形，则先做一个正方形，再让半径为正方形边长的一半*/
                 /*这里50%等同于100px */
                 border-radius: 50%;
             }
             
             .yuanjiaojuxing {
                 width: 400px;
                 height: 200px;
                 background-color: pink;
                 /* 要做一个上下是矩形，两侧是圆形，则先做一个长方形*/
                 /*再让半径高度的一半*/
                 border-radius: 100px;
             }
         </style>
     ```

     

- 盒子阴影

  css3中增加了盒子影子，我们可以使用box-shadow属性为盒子添加阴影。

  语法：

  ```html
  box-shadow:h-shadow v-shadow blur spread color inset;
  ```

  ![image-20220113174842811](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113174842811.png)

  注意：

  1. 默认的最外阴影（outset），但是不可以写这个单词，否则导致阴影无效。

  2. 盒子阴影不占用空间，不会影响其他盒子排列。

     ```html
     div:hover {
                 box-shadow: 10px 10px 20px 10px rgba(0, 0, 0, 0.3);
             }
     ```

- 文字阴影

  在css3中，我们可以使用text-shadow属性将阴影应用于文本。

  语法：

  ```
  text-shadow: h-shadow v-shadow blur color;
  ```

  ![image-20220113194106945](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113194106945.png)

### 2-9 浮动

- 传统网页布局的三种方式

  （pc端）CSS提供了三种传统布局的方式（简单来说就是盒子如何进行排列顺序）：

  1. 普通流（标注流）

     就是标签按照默认规定好的方式排列。

     - 块级元素会独占一行，从上向下顺序排列

       ###### 常用元素：div hr(`<hr>` 标签在 HTML 页面中创建一条水平线。) p h1-h6 ul ol dl form table

     - 行内元素会按照顺序，从左到右顺序排列，碰到父元素边缘会自动换行。

       ###### 常用元素：span a i em

     标准流就是最基本的布局方式。

  2. 浮动

  3. 定位

  这三种布局方式都是用来摆放盒子的，盒子摆放到合适位置，布局自然就完成了。

  注意：实际开发中，一个页面基本都包含了这三种布局方式（后面移动端学习新的布局方式）

- 为什么需要浮动

  有很多的布局效果，标准流没有办法完成，此时就可以利用浮动完成布局。因为浮动可以改变元素标签默认的排列方式。

  浮动最典型的应用：可以让多个块级元素一行内排列显示。

  网页布局第一准则：多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动。

  网页布局第二准则：先设置盒子大小，之后设置盒子位置。

- 什么是浮动

  float属性用于创建浮动框，将其移动到一边，直到左边缘或者右边缘触及包含块或者另一个夫浮动框的边缘。

  语法：

  ```
  选择器 {float:属性值}
  ```

  ```html
      <style>
          .one {
              height: 100px;
              width: 100px;
              background-color: pink;
              float: left;
          }
          
          .two {
              height: 100px;
              width: 100px;
              background-color: pink;
              float: right;
          }
      </style>
  ```

  ![image-20220113220646232](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113220646232.png)

- 浮动特性

  1. 浮动元素会脱离标准流（脱标）

     - 脱离标准普通流的控制（飘到我们面前）（浮）移动到指定位置（动）俗称脱标

     - 浮动的盒子不再保留原先的位置。

       ![image-20220113221459682](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113221459682.png)

       ```html
           <style>
               .one {
                   height: 100px;
                   width: 100px;
                   background-color: pink;
                   float: left;
               }
               
               .two {
                   height: 200px;
                   width: 200px;
                   background-color: blue;
               }
           </style>
       ```

       结果：

       ![image-20220113221411475](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113221411475.png)

  2. 浮动的元素会一行内显示并且元素顶部对齐

     注意：浮动的元素是互相贴靠在一起的（不会有间隙），如果父级宽度装不下这些浮动的盒子，多出的盒子会另起一行对齐。

     ```html
         <style>
             div {
                 height: 100px;
                 width: 100px;
                 float: left;
             }
             
             .one {
                 background-color: pink;
             }
             
             .two {
                 height: 300px;
                 background-color: blue;
             }
             
             .three {
                 color: white;
                 background-color: black;
             }
             
             .four {
                 height: 200px;
                 background-color: red;
             }
         </style>
     ```

     结果：

     ![image-20220113222013237](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113222013237.png)

  3. 浮动的元素会具有行内块元素的特性

     任何元素都可以浮动，不管原先是什么模式的元素，添加浮动之后具有行内块元素相似的特性。

     - 如果块级盒子没有设置宽度，默认宽度和父级一样宽，但是添加浮动后，他的大小根据内容来决定。
     - 浮动的盒子中间是没有缝隙的是紧挨在一起的。
     - 行内元素同理。

- 浮动元素经常和标准流父亲搭配使用

  为了约束浮动元素位置，我们网页布局一般采用的策略是：

  ##### 先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置，符合网页布局第一准则。

  练习：

  ```html
  <!DOCTYPE html>
  <html lang="en">
  
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=div, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
          * {
              margin: 0;
              padding: 0;
          }
          
          .box {
              height: 300px;
              width: 600px;
              background-color: pink;
          }
          
          .one {
              width: 200px;
              float: left;
              height: 100%;
              background-color: rgba(255, 0, 0, 1);
          }
          
          .two {
              float: left;
              width: 400px;
              height: 100%;
              background-color: blue;
          }
          
          .two div {
              float: left;
              width: 90px;
              height: 140px;
              margin-left: 10px;
              background-color: antiquewhite;
              margin-bottom: 20px;
          }
      </style>
  </head>
  
  <body>
      <div class="box">
          <div class="one"></div>
          <div class="two">
              <div></div>
              <div></div>
              <div></div>
              <div></div>
              <div></div>
              <div></div>
              <div></div>
              <div></div>
          </div>
      </div>
  
  </body>
  
  </html>
  ```

  

- 浮动布局注意点

  1. 浮动和标准流的父盒子搭配

     先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置。

  2. 一个元素浮动了，理论上其余的兄弟元素也要浮动

     一个盒子里面有多个盒子，如果其中一个盒子浮动了，那么其他兄弟也应该浮动，以防止引起问题。

     浮动的盒子只会影响浮动盒子后面的标准流，不会影响前面的标准流

     ```html
     <style>
             div {
                 height: 100px;
                 width: 100px;
             }
             
             .one {
                 float: left;
                 background-color: rgba(255, 0, 0, 0.3);
             }
             
             .two {
                 height: 50px;
                 background-color: blue;
             }
             
             .three {
                 float: left;
                 color: white;
                 background-color: black;
             }
         </style>
     ```

     结果：

     ![image-20220113230010053](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220113230010053.png)

  

### 2-10 清除浮动+PS切图

- 为什么清除浮动

  标准流父盒子不必须有高度，因为盒子里内容如果很长，或者不确定时，固定的高度不够灵活。

  所以父盒子很多情况下不方便给高度，但是盒子浮动又不占用位置，最后父级盒子高度为0时，就会影响下面的标准流盒子。

  ![image-20220114152656258](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220114152656258.png)

  由于浮动元素不再占用原文档的位置，所以它会对后面的元素排版产生影响。所以要清除浮动。

- 清除浮动本质

  1. 本质是清除浮动元素造成的影响
  2. 如果父盒子本身有高度，则不需要清除浮动
  3. 清除浮动之后，父级就会根据浮动的子盒子自动检测高度。父级有了高度，就不会影响下面的标准流了。

  语法：

  ```
  选择器{clear:属性值;}
  ```

  ![image-20220114153501534](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220114153501534.png)

  实际开发中我们几乎只用clear:both;

  清除浮动的策略是：闭合浮动。只让浮动在父盒子内部影响，不影响父盒子外面的其他盒子。

  ##### 清除浮动方法：

  1. 额外标签法也称为隔墙法，是w3c推荐的做法。
  2. 父级添加overflow属性
  3. 父级添加after伪属性
  4. 父级添加双伪属性

- 额外标签法

  额外标签法会在浮动元素末尾添加一个空的标签。例如`<div style="clear:both"></div>`或者其他标签`<br />`等

  - 优点：通俗易懂，书写方便
  - 缺点：添加许多无意义的标签，结构化较差。

  注意：我们新添加的空标签必须是块级元素。不能是行内元素。

  应用：

  ```html
  <!DOCTYPE html>
  <html lang="en">
  
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
          .box {
              background-color: pink;
              width: 700px;
          }
          
          .box .clear {
              clear: both;
          }
          
          .box .one {
              float: left;
              width: 200px;
              height: 300px;
              background-color: blue;
          }
          
          .box .two {
              float: left;
              width: 300px;
              margin-left: 30px;
              height: 100px;
              background-color: skyblue;
          }
      </style>
  </head>
  
  <body>
  
      <div class="box">
          <div class="one"></div>
          <div class="two"></div>
          <div class="clear"></div>
      </div>
      <div class="foot"></div>
  </body>
  
  </html>
  ```

- 父级添加overflow

  给父级添加overflow属性，将其属性值设置为hidden、auto或scroll

  ```html
  .box {
              background-color: pink;
              width: 700px;
              overflow: hidden;
          }
  ```

  - 优点：代码简洁
  - 缺点：无法显示溢出的部分

- after伪元素

  是额外标签法的升级版，也是给父元素添加。

  ```html
      <style>
          .clearfix:after {
              content: "";
              display: block;
              height: 0;
              clear: both;
              visibility: hidden;
          }
          
          .clearfix {
              /* IE6、7专有 */
              *zoom: 1;
          }
          </style>
  <body>
  
      <div class="box clearfix">
          <div class="one"></div>
          <div class="two"></div>
      </div>
      <div class="foot"></div>
  </body>
  ```

  - 优点：没有增加标签、结构简单
  - 缺点：照顾低版本浏览器
  - 代表网站：百度、淘宝网、网易

- 双伪元素清除浮动

  也是给父元素添加。

  ```html
   <style>
          .clear::before,
          .clearfix:after {
              content: "";
              display: table;
          }
          
          .clearfix:after {
              clear: both;
          }
          
          .clearfix {
              /* IE6、7专有 */
              *zoom: 1;
          }
  </style>
  <div class="box clearfix">
  ```

  - 优点：代码更简洁
  - 缺点：照顾低版本浏览器
  - 代表网站：小米、腾讯等

- 常见的图片格式

  ![image-20220114183050819](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220114183050819.png)

- PS切图

  方式：图层切图、切片切图、ps插件切图

  1. 图层切图

     - 点击图片再点击图层右键快速导出为png
     - 把两个图层合并为一个再导出方式：shift选中想要合并的图层，ctrl+e进行合并，再右键快速导出png

  2. 切片切图

     - 利用切片选中图片（利用切片工具手动划出）

     - 导出选中的图片 文件菜单->导出->存储为web设备所用格式->选择我们要的图片格式->存储      

       想要切成透明的就把背景图层关上。
