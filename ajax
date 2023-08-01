### 1.Ajax入门与axios使用

#### 什么是AJAX?

定义：AJAX是异步的javaScript和XML。简单点说，就是使用XMLHttpRequest对象与服务器通信。它可以使用JSON,XML,HTML和text文本等格式发送和接收数据。AJAX最吸引人的就是它的"异步"特性，也就是说它可以在不重新刷新页面的情况下与服务器通信，交换数据或更新页面。

#### Axios使用

1. 引入axios.js
2. 使用axios函数
    1. 传入配置对象
    2. 再用.then 回调函数接收结果，并做后续处理

    ![](https://secure2.wostatic.cn/static/vPnK6XjCCPxePZeQdyMirA/image.png?auth_key=1690869482-iVGrMcAwurqFCVRLmFQXp-0-4a2f7dd21af02eb589faf13ad53ac4ee)

### 2.认识URL

#### 什么是URL?

定义：统一资源定位符（英语：Uniform Resource Locator，缩写：URL,或称统一资源定位器、定位地址、URL地址）俗称网页地址，简称网址，是因特网上标准的资源的地址，如同在网络上的门牌。

#### URL的组成

协议、域名、资源路径

![](https://secure2.wostatic.cn/static/qM9TEhpUXGMcxufn5FVCwY/image.png?auth_key=1690869482-c15bQUvzaiiuphLFhF8D6G-0-5b14b613a0e8cd0a387e07ff9da31256)

**协议**：**http协议**：超文本传输协议，规定浏览器和服务器之间传输数据的格式。

![](https://secure2.wostatic.cn/static/6fuoaBS2oCJvkCfj3mVMfp/image.png?auth_key=1690869483-bMie3mdD8KS9uFChjRHwau-0-cf9ed4436482969f51c9b193fe261201)

**域名**：标记服务器在网络中方位

![](https://secure2.wostatic.cn/static/acGkb6W8C6DRAohWAf1GEV/image.png?auth_key=1690869483-vpT96zqsaYCLaCrgeAg5PT-0-31eca5084e83a1e0959aca6045853d5f)

**资源路径**：标记资源在服务器下的具体位置

![](https://secure2.wostatic.cn/static/2NLDF6J7usPyGZVR4LjJAf/image.png?auth_key=1690869483-3azNDUpcV67ceUfDyC664g-0-9c7691c677df2cd2d774e0f1cdf240af)

### 3 URL查询参数

定义：浏览器提供给服务器额外信息，让服务器返回浏览器想要的数据

语法：http://xxxx.com/xxx/xxx? 参数名1=值1 & 参数名2=值2

#### axios-查询参数

语法：使用axios提供的params选项

注意：axios在运行时吧参数名和值，会拼接到url?参数名=值

![](https://secure2.wostatic.cn/static/9S5tdTMBM76LFd6YBjjvXf/image.png?auth_key=1690869483-vdmzuT23iPhE259rs8gyxv-0-bbf1d1bfbb7f38688dd8e65ce655785b)

### 4 常用请求方法

请求方法：对服务器资源，要执行的操作，method默认值为get

![](https://secure2.wostatic.cn/static/4EqPp8ogoEH2BuJER1K5bt/image.png?auth_key=1690869482-eccPCiMhcMz6pvV7ugFiUK-0-c0b28467d92abd3065208f1059660dd3)

#### axios请求配置

url：请求的URL网址

method：请求的方法，GET可以省略（不区分大小写）

data：提交数据

![](https://secure2.wostatic.cn/static/aXeQBXMDWbS6xZYVKHnRKj/image.png?auth_key=1690869483-pv6vcEUeNVt13jA6B5vcM1-0-91737fe8f6eea33490e4d1b8559fdfa9)

### 5 axios错误处理

语法：在then方法的后面，通过点语法调用catch方法，传入回调函数并定义形参

![](https://secure2.wostatic.cn/static/mWDkGwE4dpALLEuZ8hiZwP/image.png?auth_key=1690869483-6ijfR9ijAH3nd13EMeBDpQ-0-58d3399b48d88e8c6b4cc61f3732de57)

### 6 http协议-请求报文

HTTP协议：规定了浏览器发送及服务器返回内容的格式

请求报文：浏览器按照HTTP协议要求的格式，发送给服务器的内容

请求报文的组成部分有：
  1. 请求行：请求方法，URL，协议
  2. 请求头：以键值对的格式携带的附加信息，比如:Content-Type
  3. 空行：分割请求头，空行之后的是发送给服务器的资源
  4. 请求体：发送的资源

### 7 http协议-响应报文

响应报文：服务器按照HTTP协议要求的格式，返回给浏览器的内容

组成部分：
  1. 响应行：协议、http响应状态码、状态信息
  2. 响应头：以键值对的格式携带附带的附加信息，比如:Content-Type
  3. 空行：分割响应头，空行之后的是服务器返回的资源
  4. 响应体：返回的资源

#### 响应状态码：

用来表明请求是否成功完成

![](https://secure2.wostatic.cn/static/k9HueSJMcj8kU5m6JBZp1Q/image.png?auth_key=1690869483-9WCK7PxfaRVFg73wAWmpzJ-0-5755f2c11596cc3172a29487dd7cdbdc)

## 第二章

### 1.AJAX原理-XMLHttpRequest

**定义**：XMLHttpRequest对象用于与服务器交互。通过XMLHttpRequest可以在不刷新页面的情况下请求特定URL，获取数据。这允许网页在不影响用户操作的情况下，更新页面的局部内容。XMLHttpRequest在AJAX编程中被大量使用。

**关系**：axios内部采用XMLHttpRequest与服务器交互

![](https://secure2.wostatic.cn/static/gWkunowit9vpsGWMCB1ksu/image.png?auth_key=1690869483-fnLosXhzKi4MUVSiGXfPik-0-c461d7aade0777c568730a93df9a11d4)

步骤：
  1. 创建XMLHttpRequest对象
  2. 配置请求方法和请求url地址
  3. 监听loadend事件，接收响应结果
  4. 发起请求

  ![](https://secure2.wostatic.cn/static/vyzZLWVrDDxFV8hci31c43/image.png?auth_key=1690869483-7U5NFETwk5Pf2qb2aHsHDn-0-3fba105b3048f292af7b62a69c1151db)

### 2.XMLHttpRequest-查询参数

定义：浏览器提供给服务器的额外信息，让服务器返回浏览器想要的数据。

语法：http://xxxx.com/xxx/xxx?参数名1=值1 & 参数名2=值2

![](https://secure2.wostatic.cn/static/s7wj6hgyxUVgxoKmvMBC2v/image.png?auth_key=1690869483-j75MBVJZBJoBCYmdopsKc2-0-7617d6441e5dd09410d7a353553855cd)

![](https://secure2.wostatic.cn/static/8rQbsBLZwLhu6vCqKBQsVP/image.png?auth_key=1690869483-fbzXbFcKhjpN2WUAwNL9XF-0-739f57d5d3a160f51d543caf5ce265a1)

### 3.XMLHttpRequest-数据提交

需求：通过XHR提交用户名和密码，完成注册功能

核心：

  请求头设置 Content-Type:application/json

  请求体携带JSON字符串

![](https://secure2.wostatic.cn/static/bWUC1rnQkuQCk7JwsvWzQ9/image.png?auth_key=1690869482-981h11nPJp5fVeiBcpfQon-0-929296e4f92bd0d4e83705dae32eb885)

### 4.Promise

对象用于表示一个异步操作的最终完成（或失败）及其结果值

![](https://secure2.wostatic.cn/static/gK91Pmax6VQk2sDF4JjgBu/image.png?auth_key=1690869483-jXAqqAsQ8hBBcDyUbAJmuh-0-3a87c1794557dc5d549379aba3acd4e7)

#### 4.1 Promise的三种状态

作用：了解Promise对象如何关联的处理函数，以及代码执行顺序。

概念：一个promise对象，必然处于以下几种状态之一
  - 待定（pending）：初始状态，既没有被兑现，也没有被拒绝
  - 已兑现（fulfilled）：意味着，操作成功完成
  - 已拒绝（rejected) ：意味着，操作失败

  ![](https://secure2.wostatic.cn/static/diK5uB49b5ZKLKxGCnJWGv/image.png?auth_key=1690869483-xjG67yZB5sKFzFwBfMsHKi-0-673bb496f08a267bfc1b9bcab981ed4d)

注意：Promise对象一旦被兑现/拒绝就是已敲定了，状态无法再被改变

Promise对象创建时，这里的代码都会立即执行

![](https://secure2.wostatic.cn/static/6fHmM13aD159fFdeePS23e/image.png?auth_key=1690869483-4xGvoCxVS3HE5cBQjvJbAS-0-efc4a98d44b076698605994dd6899777)

## 第三章

### 1.同步代码和异步代码

- 同步代码：逐行执行，需原地等待结果后，才继续向下执行
- 异步代码：调用后耗时，不阻塞代码继续执行，不必原地等待，在将来完成后触发一个回调函数。异步代码结果依靠回调函数接收。
- 回调地狱：在回调函数中嵌套回调函数，一直嵌套下去就形成了回调函数地狱

    缺点：可读性差，异常无法获取，耦合性严重，牵一发而动全身。

### 2.Promise-链式调用

- 概念：依靠then()方法会返回一个新生成的Promise对象特性，继续串联下一环任务，直到结束。
- 细节：then()回调函数中的返回值，会影响新生成的Promise对象最终状态和结果。
- 好处：通过链式调用，解决回调函数嵌套问题。

    ![](https://secure2.wostatic.cn/static/bYW9sxTUa2SCDzwiokFUxZ/image.png?auth_key=1690869484-8njL5wSofgiSxxLuZ6UEjg-0-fb4abc8b37a29835534793b54d350ac6)

#### [Promise 并发](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise#promise_并发)

`Promise` 类提供了四个静态方法来促进异步任务的[并发](https://zh.wikipedia.org/wiki/并发计算)：

[`Promise.all()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

在**所有**传入的 Promise 都被兑现时兑现；在**任意一个** Promise 被拒绝时拒绝。

[`Promise.allSettled()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled)

在**所有**的 Promise 都被敲定时兑现。

[`Promise.any()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/any)

在**任意一个** Promise 被兑现时兑现；仅在**所有**的 Promise 都被拒绝时才会拒绝。

[`Promise.race()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)

在**任意一个** Promise 被敲定时敲定。换句话说，在**任意一个** Promise 被兑现时兑现；在**任意一个**的 Promise 被拒绝时拒绝。

#### Promise 链式调用的两个注意点:

1. 链式调用时，上一次 .then() 处理的数据变成了 undefined ?

    我们来看下面这个例子:

```JavaScript
new Promise((resolve, reject) => {
    resolve('成功了')
})
    .then(
        (data) => { console.log('onResolved1', data); },
        (error) => { console.log('onRejected1', error); }
    )
    .then(
        (data) => { console.log('onResolved2', data); },
        (error) => { console.log('onRejected2', error); }
    )

```

    ↑ 第二个 .then() 会打印什么结果呢?

    ![](https://secure2.wostatic.cn/static/h7DLz4siCCCFFYqevBSQdq/image.png?auth_key=1690869484-oxj5jVGYDRPcAnStN9vcLD-0-d961156b0866f968e834c5f4dcd25c8a)

    会发现在第2个 .then() 中, 虽然也走了处理成功的回调, 但是数据却丢失了, 变成了 undefined 。说明上一个 .then() 返回的 promise 对象, 它的数据肯定丢失了, 我们可以再来打印一下这个 promise:

    ![](https://secure2.wostatic.cn/static/fC7mePdS6qaeAGEy25xGtD/image.png?auth_key=1690869484-hHu4MGu8LArtpDNqfv1cv7-0-924e3488e7516ec350b4639317bf9c35)

    不难看出，这里的 result 确实变成了 undefined 。这是因为：在第一次的 .then() 中，处理成功的 onResolved 回调参数没有显示地使用 return 返回数据，在 Promise 内部相当于只写了 return 。因此，在下一次的链式调用时, 后续 .then() 的 onResolved 就只能拿到 undefined 了。

    所以，想要在链式调用中让 result 结果一直传递下去就必须在处理函数中(不管是 onResolved 还是 onRejected )显示地返回数据，否则数据就会丢失。

    而对于返回值的类型，有两种情况：一个是返回固定值，一个是返回 Promise。如果返回的是 Promise，那么 Promise 内部会将里面的 result 结果取出来:

```JavaScript
.then(
    (data) => {
        console.log('onResolved1', data)
        // 情况1: 返回固定值
        return 'success'；
        // 情况2: 返回promise
        return new Promise(resolve => {
            resolve(data)
        })；
    }
)
.then((data) => { console.log('onResolved2', data)})

```

    以上两种情况, 都可以正常执行, 让下一个.then()中的回调函数拿到数据:

![](https://secure2.wostatic.cn/static/311B6DrshatcTUk3RgNQ2r/image.png?auth_key=1690869484-8S37zUZibV7d3c2Z5nio59-0-60d56a263c00b72f19363feced623d6c)

![](https://secure2.wostatic.cn/static/74BpbWNmWk5u2nZhkfkbCK/image.png?auth_key=1690869484-5gzETzRb34sjdCpfDYcDL9-0-771ae9e966f8f10356230de935e2511f)

#### Promise 异常穿透与错误处理

**catch 是什么?**

catch 是 Promise 原型是的一个方法，在 promise 被拒绝时，可以在其中执行异步函数处理错误。实际上，此方法是 then 的一种完全模拟，只是个简写形式：

```JavaScript
// catch 等价于 =>
Promise.prototype.then(undefined, onRejected)

```

它会立即返回一个等价的 `Promise` 对象，这可以允许你继续链式调用其他 promise 的方法，比如：

```JavaScript
.catch(error => {
    console.log(error);
    return "错误处理完了"
})
.then(data => {
    console.log(data); // output => "错误处理完了"
})

```

虽然这样写不常见。

#### .then 对比 .catch

这两个代码片段是否相等？换句话说，对于任何处理程序（handler），它们在任何情况下的行为都相同吗？

```JavaScript
promise.then(f1).catch(f2);

promise.then(f1, f2);

```

答案是不相等。

不同之处在于，如果 f1 中出现 error，那么在第一个链式调用中，error 会被 catch 捕获，并在 f2 中被处理，但是在第二种写法中不会，这是因为 error 是沿着链传递的，而在第二段代码中，f1 和 f2处于同一层级，二者只会执行其一，下面没有链，所以 error 不会被处理。

#### 隐式的 try…catch


Promise 的 error 是如何在链式调用中向下传递的并被处理的呢？

通常，一遇到异常抛出，浏览器就会顺着 Promise 链寻找下一个就近的 onRejected 失败回调函数或者由 .catch() 指定的回调函数。你可以想象成 promise 的整个执行器（executor）和 promise 的处理程序周围有一个隐式的 “try...catch”。

这一错误的传递就被称为 promise 的异常穿透。

```JavaScript
new Promise((resolve, reject) => {
    reject('失败了')
})
    .then(
        (data) => { console.log('onResolved1', data); },
        (error) => { console.log('onRejected2', error); }
    )
    .catch(
        (error) => {
            console.log('catch', error)
        }
    )

```

上述例子中，`"失败了"` 就会被离它最近的 then 中的 `onRejected` 函数所处理，而不会被 catch 所捕获。

#### 异步回调中的错误无法捕获

需要注意的是：定时器这种异步中的错误，promise 捕获不到的：

```JavaScript
new Promise((resolve, reject) => {
    setTimeout(() => {
        throw new Error("Whoops!");
    }, 1000);
})
    .catch(error => {
        console.log('catch error:', error);
    });

```

正如之前所讲，函数代码周围有个隐式的 “try..catch”。所以，所有同步错误都会得到处理。

但是这里的错误并不是在 executor 运行时生成的，而是在稍后生成的。这和浏览器的执行机制有关，你可以理解成：在延时等待 1s 后，抛出错误这一操作才会执行，但此时外面的 Promise 早就执行结束退出主线程了。因此，promise 无法处理它，程序会在此崩掉。

**try…catch 不能捕获 promise 的错误**

#### executor 中的异步错误解决方案


所以在 executor 执行器中，不管最终拿到什么结果，建议都使用 resolve 或 reject 去接收，以便后续的链式调用，这是一种好习惯：

```JavaScript
// 直接使用 reject 接收 error
new Promise((resolve, reject) => {
    setTimeout(() => {
        reject(new Error("Whoops!"))
    }, 1000);
})

//或
new Promise((resolve, reject) => {
    setTimeout(() => {
        try {
            throw new Error("Whoops!");
        } catch(error) {
            reject(error)
        }
    }, 1000);
})


```

#### async/await 解决方案

async/await 很好的解决了愣头青的烦恼，相比于 `promise.then`，`await` 只是获取 promise 的结果的一个更优雅的语法，并且也更易于读写。

如果一个 promise 正常 resolve，`await promise` 返回的就是其结果。但是如果 promise 被 reject，它将 **throw 这个 error**，就像在这一行有一个 `throw` 语句那样，`try...catch` 就能顺理成章地捕获到了。

请看以下常见的请求例子:

```JavaScript
// 模拟请求
function http(params) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (params === 0) reject("error")
            resolve("success")
        }, 1000);
    })
}

// 业务调用
async function query(params) {
    try {
        const data = await http(params)
        console.log('data:', data);
    } catch (error) {
        console.log('error:', error);
    }
}

query(0)

```

## 如何中断promise

最后，如果等到最后.catch()处理完, 想结束promise链, 不想再让其链式调用下去了, 可以作如下操作:

```JavaScript
.catch((err) => {
  console.log('onRejected', err);
  // 中断promise链:
  return new Promise(() => {})
})

```

通过返回一个状态一直为 pending 的 promise 即可。

### 3. anync / await

#### async

async是一个加在函数前的修饰符，被async定义的函数会默认返回一个Promise对象resolve的值。因此对async函数可以直接then，返回值就是then方法传入的函数。

```JavaScript
// async基础语法
async function fun0(){
    console.log(1);
    return 1;
}
fun0().then(val=>{
    console.log(val) // 1,1
})

async function fun1(){
    console.log('Promise');
    return new Promise(function(resolve,reject){
        resolve('Promise')
    })
}
fun1().then(val => {
    console.log(val); // Promise Promise
})

```

#### await


await 也是一个修饰符，只能放在async定义的函数内。可以理解为等待。

await 修饰的如果是Promise对象：可以获取Promise中返回的内容（resolve或reject的参数），且取到值后语句才会往下执行；

如果不是Promise对象：把这个非promise的东西当做await表达式的结果。

```JavaScript
async function fun(){
    let a = await 1;
    let b = await new Promise((resolve,reject)=>{
        setTimeout(function(){
            resolve('setTimeout')
        },3000)
    })
    let c = await function(){
        return 'function'
    }()
    console.log(a,b,c)
}
fun(); // 3秒后输出： 1 "setTimeout" "function"

```

```JavaScript
function log(time){
    setTimeout(function(){
        console.log(time);
        return 1;
    },time)
}
async function fun(){
    let a = await log(1000);
    let b = await log(3000);
    let c = log(2000);
    console.log(a);
    console.log(1)
}
fun(); 
// 立即输出 undefined 1
// 1秒后输出 1000
// 2秒后输出 2000
// 3秒后输出 3000

```

#### async/await 的正确用法

```JavaScript
// 使用async/await获取成功的结果

// 定义一个异步函数，3秒后才能获取到值(类似操作数据库)
function getSomeThing(){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            resolve('获取成功')
        },3000)
    })
}

async function test(){
    let a = await getSomeThing();
    console.log(a)
}
test(); // 3秒后输出：获取成功

```

#### await后跟的表达式不同，有两种处理结果  :


1 对于promise对象，await会阻塞函数执行，等待promise的resolve返回值，作为await的结果，然后再执行下下一个表达式  


2 对于非promise对象，比如箭头函数，同步表达式等等，await等待函数或者直接量的返回，而不是等待其执行结果

**await不会阻塞主线程，不会导致浏览器假死，卡死，anync是个异步函数，会被放进异步队列，等主线程空闲了才会放进主线程，await后面的代码如果是promise，那么是同步的，如果不是promise，那么执行规则是先同步后异步**

### 4.宏任务和微任务

ES6之后引入了Promise对象，让JS引擎也可以发起异步任务

异步任务分为：
  - 宏任务：由浏览器环境执行的异步代码
  - 微任务：由JS引擎环境执行的异步代码

- 宏任务：script（全局任务）, setTimeout, setInterval, setImmediate, I/O, UI rendering.
- 微任务：process.nextTick （node.js中进程相关的对象）, Promise, Object.observer, MutationObserver。
