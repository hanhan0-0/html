## 第四章 Nodejs

定义：是一个跨平台JavaScript运行环境，使开发者可以搭建服务器端的JavaScript应用程序。

作用：使用Node.js编写服务器端程序
  1. 编写数据接口，提供网页资源浏览功能等等
  2. 前端工程化：为后续学习vue和react做铺垫（前端工程化的意思是开发项目到上线，过程中集成的所有工具和技术）

#### Nodejs为何能执行JS?

首先：浏览器能执行js代码，依靠的是内核中的v8引擎

其次：Node.js是基于Chrome v8引擎进行封装（运行环境）

nodejs没有Bom和Dom

![](https://secure2.wostatic.cn/static/67Xm9pw7GJktPtd8Buzcso/image.png?auth_key=1690869487-oJULQjuDwCZvnFPUrBiEiX-0-bc325f68a8fe64729e15a8cc88cbd229)

### 1.fs模块-读写文件

- 模块：类似插件，封装了方法/属性
- fs模块：封装了与本机文件系统进行交互的，方法/属性
- 语法：
    1. 加载fs模块对象

```JavaScript
const fs = require('fs')//fs是模块标识符：模块的名字
```
    2. 写入文件内容

```JavaScript
fs.writeFile('文件路径','写入内容',err =>{
 //写入后的回调函数
 })
```
    3. 读取文件内容

```JavaScript
fs.readFile('文件路径',(err,data) =>{
 //读取后的回调函数
 //data是文件内容的Buffer数据流
 })
```

### 2.path模块-路径处理

问题：Node.js代码中，相对路径是根据终端所在路径来查找的，可能无法找到想要的文件。

建议：在Node.js代码中，使用绝对路径

补充：_dirname内置变量（获取当前模块目录-绝对路径）

注意：path.join()会使用特定于平台的分隔符，作为定界符，将所有给定的路径片段连接在一起。

![](https://secure2.wostatic.cn/static/dXMUDaXqRiRV1yem1zG3YE/image.png?auth_key=1690869488-rvHhW4tyEPhNCQwJd84zTb-0-cdd267535feab5c160854c5ba4fb5488)

语法：
  1. 加载path模块
  2. 使用path.join方法拼接路径

### 3.URL中的端口号

URL:统一资源定位符，简称网址，用于访问服务器里的资源

端口号：标记服务器里不同功能的服务程序

端口号范围：0-65535之间的任意整数

![](https://secure2.wostatic.cn/static/3t49KGB7SAwWGBAu6Go8VE/image.png?auth_key=1690869488-c3t31Anh4y1wxbydAQdhb2-0-17c38733ca0ee3469c78221d246d74d2)

Http协议默认访问80端口

#### 常见的服务程序

web服务程序：用于提供网上信息浏览功能

![](https://secure2.wostatic.cn/static/aNiXZkBCM8s1Hs3R9q316C/image.png?auth_key=1690869489-2cFrUYhzEHsyLhiaTk3GRv-0-0a460520a106734ee4f93ce4842366ed)

注意：0-1023和一些特定端口号被占用，我们自己编写服务程序请避开使用

### 4.http模块-创建web服务

![](https://secure2.wostatic.cn/static/6XDjTJxg7VyisHdT9Am6sB/image.png?auth_key=1690869489-uQGSQWkjKf7s5inVzmtwTV-0-47bb9db3082b6e5b834fec4a0fb367d8)

### 5.Node.js模块化

#### 什么是模块化？

**定义：**CommonJS模块是为Node.js打包JavaScript代码的原始方式。Node.js还支持浏览器和其他JavaScript运行时使用的ECMAScript模块标准。在Node.js中**每个文件都被是为一个单独的模块。**

**概念：**项目是由很多个模块文件组成的

**好处**：提高代码复用性，按需加载，独立作用域

**使用：**需要标准语法导出和导入

#### CommonJs标准

使用：
  1. 导出：module.exports={}

      ![](https://secure2.wostatic.cn/static/bFCL1RadMPG2q1vV7yXnT5/image.png?auth_key=1690869489-6rQDxkaAL3VvRRmV6SUXq3-0-67386d3421e375e7278b14023f908b8f)
  2. 导入：require('模块名或路径')

      ![](https://secure2.wostatic.cn/static/h5boS67CqHDV4pkSVtNc6d/image.png?auth_key=1690869489-2w26Wqs4jVgThKxmarkZoz-0-213c98a118c29cc4f98caacbb2fa7841)

模块名或路径：
  - 内置模块：直接写名字（例如：fs，path，http）
  - 自定义模块：写模块文件路径（例如：./utils.js）

### 6.ECMAScript标准-默认导出和导入

默认标准使用：
  1. 导出：export default{}

      ![](https://secure2.wostatic.cn/static/3fZgbETnLAwgsBtyNw8d3H/image.png?auth_key=1690869490-4YUdXhWKKfpc6wCvrqU9Na-0-f62b92531ac092c726cdbfc33dc7069c)
  2. 导入：import 变量名 from '模块名或路径'

      ![](https://secure2.wostatic.cn/static/qKJ7o1RkoPaSB3A9iNL9iJ/image.png?auth_key=1690869490-gmuTQ28yaB2jU8ysKhwzAa-0-cdb22ac8c71feea62dfc30a63ba1ad2a)

注意：Node.js默认支持CommonJs标准语法

如需使用ECMAScript标准语法，在运行模块所在文件夹新建package.json文件，并设置{"type":"module"}

### 7.ECMAScript标准-命名导出和导入

命名标准使用：
  1. 导出：export修饰定义语句

      ![](https://secure2.wostatic.cn/static/jcFWMiJ2yHZNnuGz4Lgok/image.png?auth_key=1690869490-2WHNYVV7kAwJgywfz2kKgy-0-cdf21b58321882db919bc43fe74a8b52)
  2. 导入import {同名变量} from '模块名或路径'

      ![](https://secure2.wostatic.cn/static/8SMNbpKEwh6PwzytP3f1Ch/image.png?auth_key=1690869490-wjsSHHpdgGyXjPbpzsf2RX-0-501a67a0798f34178a5cf86c84721319)

如何选择：

  按需加载，使用命名导出和导入

### 8.包的概念

包：将模块，代码，其他资料聚合成一个文件夹

包分类：
  - 项目包：主要用于编写项目和业务逻辑
  - 软件包：封装工具和方法进行使用

要求：根目录中必须有package.json文件（记录包的清单信息）

![](https://secure2.wostatic.cn/static/b7ZBjm2YV4SHdTNhB2KKd9/image.png?auth_key=1690869491-eZbuuEkMu7uUZfRRfjckNz-0-f732287ef499e0e659c49db79ae006cf)

注意：导入软件包时，引入的默认是index.js模块文件/main属性指定的模块文件

唯一出口的作用：把所有工具模块方法集中起来，统一向外暴露

![](https://secure2.wostatic.cn/static/tz5BLyYKZF8RXodAwjcxjt/image.png?auth_key=1690869491-x12771Jepr9kKLAfW26gFq-0-801fe711c7cd926610c4cb5ade6ea75f)

![](https://secure2.wostatic.cn/static/tDBi4nefPEpNvZwetQU1Cy/image.png?auth_key=1690869491-qhV1AG5yav2CvZVXcLmsN8-0-a8022d8c5e633bbe41136beec0d380fe)

上边的图片是server.js文件，引入utils包。

CommonJS标准：一般应用在Node.js项目环境中

ECMAScript标准：一般应用在前端工程化项目中

### 9.npm-软件包管理器

npm简介：

  npm是Node.js标准的软件包管理器。它起初是作为下载和管理Node.js包依赖的方式，但其现在也成为前端JavaScript中使用的工具。

使用：
  1. 初始化清单文件 npm init -y(得到package.json文件，有则掠过此命令)
  2. 下载软件包：npm i 软件包名称
  3. 使用软件包

  ![](https://secure2.wostatic.cn/static/xog971xtT566LMjWNn4F6y/image.png?auth_key=1690869491-ekAbXScfJ79pdoakkzau6q-0-21569ca78cdad7853db034a2f78fa8ef)

### 10.npm-全局软件包nodemon

软件包区别：

- 本地软件包：当前项目内使用，封装属性和方法，存在于node_modules
- 全局软件包：本机所有项目使用，封装命令和工具，存在于系统设置的位置

nodemon作用：替代node命令，检测代码更改，自动重启程序。

使用：
  1. 安装npm i nodemon -g
  2. 运行：nodemon 待执行的目标js文件

需求：启动准备好的项目，修改代码保存后，观察自动重启应用程序
