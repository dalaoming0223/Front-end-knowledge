#                                     [【JS 基础】JavaScript 中的属性：数据属性 set 和访问器属性 get](https://my.oschina.net/u/4283333/blog/3423736)

[osc_3l8mmxug](https://my.oschina.net/u/4283333)

2019/09/04 17:44

阅读数 123

**一、为什么会有 get 和 set 的出现**

在程序语言中，对象（Object）有以下几个特点：

\1. 对象具有唯一标识性：即使完全相同的两个对象，也并非同一个对象。（eg：console.log ({a: 1} == {a: 1});  >>>false）

\2. 对象具有状态： 同一对象有不同的状态（c++ 中的成员变量，Java 中的属性）

\3. 对象具有行为： 对象的状态可能会有变化（c++ 中的成员函数，Java 中的方法）

在 JavaScript 中，状态和行为被统一抽象为 “属性”，这是因为在 js 中方法（function）也是以 object 的形式存在的，可以以属性的方式来进行抽象。

```
var a = {
　　b: 1,
　　c: function(){
　　　　return 3
　　}
}
```

js 允许在运行时向对象添加状态，并且可以添加行为。为了提高抽象能力，js 的属性被设计成了更加复杂的形式，它提提供了两类属性  getter/setter，作为其数据属性和访问器属性。也可以简单的理解为，getter 是一种获得属性值的方法，setter  是一种设置属性值的方法。

- getter 负责查询值，它不带任何参数，setter 则负责设置键值，值是以参数的形式传递，在他的函数体中，一切的 return 都是无效的
- get/set 访问器不是对象的属性，而是属性的特性，特性只有内部才用，因此在 javaScript 中不能直接访问他们，为了表示特性是内部值用两队中括号括起来表示如 [[Value]]

```
class Person {
    constructor(name,age) {
        this.name = name;
        this.age = age;
    }
                
    set name(name) {
        console.log("setter");
        this.name = name;
    }
                
    get name() {
        console.log("getter");
        return this.name;
    }
}
```

上面的例子中，get 方法用来获取 name 的值，get 方法用来改变 name 的值。

有人到这里会疑惑，获取值、改变值，只要直接 person.name 和 person.name = "其他人" 不就行了么？引入 get 和 set 方法不是多此一举？

可是在上面案例中，通过函数来获取对象属性、改变对象属性，是可以 console.log 到属性的行为的，也就是，通过函数是可以监听到属性的变化的，而直接通过 “.” 来获取改变属性，仅仅是实施了行为却无法进行行为的监听。

通过 set 和 get 监听属性的变化，这恰恰就是 Vue 中双向绑定的思路基础。

 

**二、VUE 中的 get、set 与双向绑定**

在 Vue 项目中，我们 console.log () 一个对象的属性，可以在控制台看到以下结果：

发现每个对象属性里都有以下定义在其原型链上的以下方法（__proto__）:

![img](https://oscimg.oschina.net/oscnet/d5b6a0a5175f9a3e214f7b65ba94c53aede.png)

 

可以看到，原型链上定义的方法有 ES5 中的__defineGetter__和__defineSetter__，以及 ES6 中引入的  get 和 set 关键字。在使用对象初始化过程来定义 Getter 和 Setter 方法时唯一要做的事情就是在 getter 方法前面加上  “get”，在 setter 方法前面加上 “set”。 还有一点要注意的就是 getter 方法没有参数，setter  方法必须有一个参数，也就是要设置的属性的新值。

```
var person = {
　　val: '名字',　　get name() {return this.val;}, 　　set name(name) {this.val = name;} } 
```

 

而 ES5 的对象原型的属性__defineGetter__和__defineSetter__，用来给对象已经定义之后，给对象绑定新的 get 和 set 方法：

```
var person = {
　　val: '名字'
}

person.__defineGetter__('name',function(){return this.val;});
person.__defineSetter__('name',function(name){this.val = name;})
console.log(person.name);  >>> 名字
person.name = '新名字';     
console.log(person.name);  >>> 新名字
```