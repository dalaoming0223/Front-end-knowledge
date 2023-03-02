# ES5中的方法

## Object 对象的静态方法

所谓“静态方法”，是指部署在`Object`对象自身的方法  ---（此句话摘自 阮一峰博客）

Object.keys()方法与Object.getOwnPropertyNames方法很相似，一般用来遍历对象的（属性名，索引），并返回一个数组，该数组成员都是对象自身的（不是继承的），区别在于Object.keys方法只返回可枚举的属性，Object.getOwnPropertyNames方法还能返回不可枚举的属性名

### **1.Object.keys**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
// 定义一个 Array 对象
let arr = ["a", "b", "c"];

// 定义一个 Object 对象
let obj = { foo: "bar", baz: 42 }；

// 定义一个  类数组 对象 
let ArrayLike = { 0 : "a", 1 : "b", 2 : "c"};

// 类数组 对象, 随机 key 排序 
let anObj = { 100: 'a', 2: 'b', 7: 'c' }; 

/* getFoo 是个不可枚举的属性 */ 
var my_obj = Object.create({}, {
     getFoo : { value : function () { return this.foo } }
 }
);
my_obj.foo = 1;

// 打印结果
console.log(Object.keys(arr));       // ['0', '1', '2']
console.log(Object.keys(obj));       // ["foo","baz"]
console.log(Object.keys(ArrayLike));     // ['0', '1', '2']
console.log(Object.keys(anObj));   // ['2', '7', '100']
console.log(Object.keys(my_obj)); // ['foo']
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

返回数组中的排序与for..in是一致的，区别在于for..in循环还可以枚举原型链上的属性

### **2.Object.getOwnPropertyNames**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
// 定义一个数组
var arr = ["a", "b", "c"];

// 定义一个 类数组对象
var obj = { 0: "a", 1: "b", 2: "c"};

//定义一个 不可枚举属性
var my_obj = Object.create({}, {
  getFoo: {
    value: function() { return this.foo; },
    enumerable: false
  }
});
my_obj.foo = 1;

// 打印结果
console.log(Object.getOwnPropertyNames(arr).sort()); // ["0", "1", "2", "length"]
console.log(Object.getOwnPropertyNames(obj).sort()); // ["0", "1", "2"]
console.log(Object.getOwnPropertyNames(my_obj).sort()); // ["foo", "getFoo"]
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

### **3.对象属性相关的方法**

```
// 看此方法之前，我觉得应该先了解一下，对象的属性分为哪两种，插句题外话，O(∩_∩)O哈哈~
```

　　对象里目前存在的属性描述符有两种主要形式：***数据描述符*** 和 ***存取描述符\***。

　　　　数据描述符: 是一个具有值的属性，该值可能是可写的，也可能不是可写的。

　　　　访问器描述符: 是由getter-setter函数对描述的属性。描述符必须是这两种形式之一；不能同时是两者。

　　数据描述符和存取描述符均具有以下可选键值：

　　　　configurable: 当且仅当该属性的 configurable 为 true 时，该属性`描述符`才能够被改变，同时该属性也能从对应的对象上被删除。默认为 false。

　　　　enumerable: 当且仅当该属性的`enumerable`为`true`时，该属性才能够出现在对象的枚举属性中。默认为 false。

　　　　value: 该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。默认为 undefined。

　　　　writable: 当且仅当该属性的`writable`为`true`时，`value`才能被赋值运算符改变。默认为 false。

　　　　getter: 一个给属性提供 getter 的方法，如果没有 getter 则为 `undefined`。该方法返回值被用作属性值。默认为 undefined。

　　　　setter: 一个给属性提供 setter 的方法，如果没有 setter 则为 `undefined`。该方法将接受唯一参数，并将该参数的新值分配给该属性。默认为 undefined。

- 　　　　注意：如果一个描述符同时设置value,writable,get和set关键字，它将被认为是一个数据描述符。如果一个描述符同时有value或writable和get或set关键字，将产生异常。

　　　　记住，这些选项不一定是自身属性，如果是继承来的也要考虑。为了确认保留这些默认值，你可能要在这之前冻结 [`Object.prototype`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype)，明确指定所有的选项，或者将　[`__proto__`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/__proto__)属性指向[`null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/null)。

#### 　　**a).Object.getOwnPropertyDescriptor( obj, prop) **

**返回一个指定对象上的自有属性对应的属性描述 （自由属性指，直接赋值的属性，不需要从原型上查找的属性）**

　　　参数:

　　　　obj 需要查找的目标对象

　　　　prop 目标对象内的属性名称

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
let o = { get foo() { return 17; } };
let d = Object.getOwnPropertyDescriptor(o, "foo");

let o1 = { bar: 42 };
let d1 = Object.getOwnPropertyDescriptor(o1, "bar");

let o2 = {};
Object.defineProperty(o2, "baz", {
    value: 8675309,
    writable: false,
    enumerable: false
});
let d2 = Object.getOwnPropertyDescriptor(o2, "baz");
console.log(d)// {configurable: true, enumerable: true, get: [Function: get foo],set: undefined}
console.log(d1)//{configurable: true, enumerable: true, value: 42, writable: true}
console.log(d2)// {value: 8675309, writable: false, enumerable: false, configurable: false}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

注意事项：ES5第一个参数不是对象，就会产生TypeError, ES2015第一个参数不是对象的话，就会被强制转换成对象

#### 　　**b).Object.defineProperty( obj, prop, decriptor) **

**直接在一个对象上定义一个新属性，或修改一个对象的现有属性，并返回这个对象，默认情况下使用此方法添加的属性值是不能被修改的**

　　参数：

　　　　obj 要在其上定义属性的对象

　　　　prop 要定义或修改的属性名称

　　　　decriptor 将被定义或修改的属性描述符

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
var o = {}; // 创建一个新对象

// 在对象中添加一个属性与数据描述符的示例
Object.defineProperty(o, "a", {
    value : 37,
    writable : true,
    enumerable : true,
    configurable : true
});
// 对象o拥有了属性a，值为37

// 在对象中添加一个属性与存取描述符的示例
var bValue;
Object.defineProperty(o, "b", {
    get : function(){
        return bValue;
    },
    set : function(newValue){
        bValue = newValue;
    },
    enumerable : true,
    configurable : true
});
o.b = 38;
// 对象o拥有了属性b，值为38

// o.b的值现在总是与bValue相同，除非重新定义o.b

// 数据描述符和存取描述符不能混合使用
Object.defineProperty(o, "conflict", {
    value: 0x9f91102,
    get: function() {
        return 0xdeadbeef;
    }
});
// TypeError: Invalid property descriptor. Cannot both specify accessors and a value or writable attribute(无效的属性描述符,不能同时指定访问器和值或可写属性)
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　c).Object.defineProperties()

　　d).Object.getOwnPropertyNames()

#### **4.控制对象状态的方法**

　　a).Object.preventExtensions() 防止对象扩展

　　b).Object.isExtensible() 判断对象是否可扩展

　　c).Object.seal() 禁止对象配置

　　d).Object.isSealed() 判断一个对象是否可配置

　　e).Object.freeze() 冻结一个对象

　　f).Object.isFrozen() 判断一个对象是否被冻结

#### **5.原型链相关方法**

　　a).Object.creat() 可以指定原型对象和属性，返回一个新的对象

　　b).Object.getPrototypeOf() 获取对的的Prototype对象

## Object对象的实例方法

除了`Object`对象本身的方法，还有不少方法是部署在`Object.prototype`对象上的，所有`Object`的实例对象都继承了这些方法。`Object`实例对象的方法，主要有以下六个。（此句摘自 --阮一峰 博客）

　　a). `valueOf()`返回当前对象对应的值

　　b). `toString()`返回当前对象对应的字符串形式,用来判断一个值的类型

　　c). `toLocaleString()`返回当前对象对应的本地字符串形式

　　d). `hasOwnProperty()`判断某个属性是否为当前对象自身的属性，还是继承自原型对象的属性

　　e). `isPrototypeOf()`判断当前对象是否为另一个对象的原型

　　f). `propertyIsEnumerable()`判断某个属性是否可枚举

#  ES6新增方法

(摘自 阮一峰ECMAScript 6 入门 )

**1.属性的简洁写法**

　　ES6 允许在对象之中，直接写变量。这时，属性名为变量名, 属性值为变量的值。

　　属性简写

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
function f(x, y) {
  return {x, y};
}
// 等同于
function f(x, y) {
  return {x: x, y: y};
}
f(1, 2) // Object {x: 1, y: 2}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　方法名简写

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
const o = {
  method() {
    return "Hello!";
  }
};
// 等同于
const o = {
  method: function() {
    return "Hello!";
  }
};
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　属性简写与方法名简写，例：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
let birth = '2000/01/01';
const Person = {
  name: '张三',
  //等同于birth: birth
  birth,
  // 等同于hello: function ()...
  hello() { console.log('我的名字是', this.name); }
};
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　CommonJS 模块输出一组变量，就非常合适使用简洁写法

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
let ms = {};
function getItem (key) {
  return key in ms ? ms[key] : null;
}
function setItem (key, value) {
  ms[key] = value;
}
module.exports = { getItem, setItem };
// 等同于
module.exports = {
  getItem: getItem,
  setItem: setItem
};
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　属性的赋值器（setter）和取值器（getter），事实上也是采用这种写法

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
const cart = {
  _wheels: 4,
  get wheels () {
    return this._wheels;
  },
  set wheels (value) {
    if (value < this._wheels) {
      throw new Error('数值太小了！');
    }
    this._wheels = value;
  }
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**2.属性名表达式**

　　方法一，是直接用标识符作为属性名

　　方法二，是用表达式作为属性名，这时要将表达式放在方括号之内。

```
// 方法一
obj.foo = true;
// 方法二
obj['a' + 'bc'] = 123;
```

　　表达式还可以用做方法名

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
let obj = {
  ['h' + 'ello']() {
    return 'hi';
  }
};
obj.hello() // hi
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　注意，属性名表达式与简洁表示法，不能同时使用，会报错。

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
// 报错
const foo = 'bar';
const bar = 'abc';
const baz = { [foo] };

// 正确
const foo = 'bar';
const baz = { [foo]: 'abc'};
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　注意，属性名表达式如果是一个对象，默认情况下会自动将对象转为字符串`[object Object]`，这一点要特别小心。

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
const keyA = {a: 1};
const keyB = {b: 2};

const myObject = {
  [keyA]: 'valueA',
  [keyB]: 'valueB'
};

myObject // Object {[object Object]: "valueB"}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　上面代码中，`[keyA]`和`[keyB]`得到的都是`[object Object]`，所以`[keyB]`会把`[keyA]`覆盖掉，而`myObject`最后只有一个`[object Object]`属性。

**3.方法的 name 属性**

　　如果对象的方法使用了取值函数（`getter`）和存值函数（`setter`），则`name`属性不是在该方法上面，而是该方法的属性的描述对象的`get`和`set`属性上面，返回值是方法名前加上`get`和`set`。

**4.Object.is() 它用来比较两个值是否严格相等，与严格比较运算符（===）的行为基本一致**

　　ES5 比较两个值是否相等，只有两个运算符：相等运算符（`==`）和严格相等运算符（`===`）。它们都有缺点，前者会自动转换数据类型，后者的`NaN`不等于自身，以及`+0`等于`-0`。JavaScript 缺乏一种运算，在所有环境中，只要两个值是一样的，它们就应该相等。

```
Object.is('foo', 'foo')
// true
Object.is({}, {})
// false
```

　　不同之处只有两个：一是`+0`不等于`-0`，二是`NaN`等于自身。

```
+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true
```

　　ES5 可以通过下面的代码，部署`Object.is`。

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
Object.defineProperty(Object, 'is', {
  value: function(x, y) {
    if (x === y) {
      // 针对+0 不等于 -0的情况
      return x !== 0 || 1 / x === 1 / y;
    }
    // 针对NaN的情况
    return x !== x && y !== y;
  },
  configurable: true,
  enumerable: false,
  writable: true
});
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

5.Object.assign( target, source, source1 ) 方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。拷贝的属性是有限制的，只拷贝源对象的自身属性（不拷贝继承属性），也不拷贝不可枚举的属性（`enumerable: false`）

　　参数

　　　　target 目标对象

　　　　source 源对象

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
const target = { a: 1, b: 1 };

const source1 = { b: 2, c: 2 };
const source2 = { c: 3 };

Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　注意，如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性。

```
let obj = {a: 1};
Object.assign(obj, undefined) === obj // true
Object.assign(obj, null) === obj /
```

　　如果非对象参数出现在源对象的位置（即非首参数），那么处理规则有所不同。首先，这些参数都会转成对象，如果无法转成对象，就会跳过。这意味着，如果`undefined`和`null`不在首参数，就不会报错。

**注意：**

`　　**a). Object.assign**`**方法实行的是浅拷贝，而不是深拷贝。也就是说，如果源对象某个属性的值是对象，那么目标对象拷贝得到的是这个对象的引用。**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
const obj1 = {a: {b: 1}};
const obj2 = Object.assign({}, obj1);

obj1.a.b = 2;
console.log(obj2.a.b) //2
obj2.a.b = 3
console.log(obj1.a.b) //3
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　上面代码中，源对象`obj1`的`a`属性的值是一个对象，`Object.assign`拷贝得到的是这个对象的引用。这个对象的任何变化，都会反映到目标对象上面。

 　**b). 数组的处理**

```
Object.assign([1, 2, 3], [4, 5])// [4, 5, 3]
```

　　上面代码中，`Object.assign`把数组视为属性名为 0、1、2 的对象，因此源数组的 0 号属性`4`覆盖了目标数组的 0 号属性`1`。

**常见用途**

　　**a). 为对象添加属性**

```
class Point {
  constructor(x, y) {
    Object.assign(this, {x, y});
  }
}
```

　　上面方法通过`Object.assign`方法，将`x`属性和`y`属性添加到`Point`类的对象实例。　

　　**b). 为对象添加方法**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
Object.assign(SomeClass.prototype, {
  someMethod(arg1, arg2) {
    ···
  },
  anotherMethod() {
    ···
  }
});

// 等同于下面的写法
SomeClass.prototype.someMethod = function (arg1, arg2) {
  ···
};
SomeClass.prototype.anotherMethod = function () {
  ···
};
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　上面代码使用了对象属性的简洁表示法，直接将两个函数放在大括号中，再使用`assign`方法添加到`SomeClass.prototype`之中。

　　**c). 克隆对象**

```
function clone(origin) {
  return Object.assign({}, origin);
}
```

　　上面代码将原始对象拷贝到一个空对象，就得到了原始对象的克隆。

　　不过，采用这种方法克隆，只能克隆原始对象自身的值，不能克隆它继承的值。如果想要保持继承链，可以采用下面的代码。

```
function clone(origin) {
  let originProto = Object.getPrototypeOf(origin);
  return Object.assign(Object.create(originProto), origin);
}
```

　　**d). 合并多个对象，将多个对象合并到某个对象。**

```
const merge = (target, ...sources) => Object.assign(target,...sources);

//如果希望合并后返回一个新对象，可以改写上面函数，对一个空对象合并。

const merge =(...sources) => Object.assign({}, ...sources);
```

　　**e). 为属性指定默认值**

**6.属性的可枚举和可遍历**

　　可枚举性

　　对象的每个属性都有一个描述对象（Descriptor），用来控制该属性的行为。

　　a). `Object.getOwnPropertyDescriptor`方法可以获取该属性的描述对象。

```
let obj = { foo: 123 };
Object.getOwnPropertyDescriptor(obj, 'foo')
//  { value: 123, writable: true, enumerable: true, configurable: true }
```

　　目前，有四个操作会忽略`enumerable`为`false`的属性。

　　　　`for...in`循环：只遍历对象自身的和继承的可枚举的属性。

　　　　`Object.keys()`：返回对象自身的所有可枚举的属性的键名。

　　　　`JSON.stringify()`：只串行化对象自身的可枚举的属性。

　　　　`Object.assign()`： 忽略`enumerable`为`false`的属性，只拷贝对象自身的可枚举的属性。

　　**ES6 规定，所有 Class 的原型的方法都是不可枚举的。**

　　属性的遍历一共有5种：

　　　　`for...in`循环遍历对象自身的和继承的可枚举属性（不含 Symbol 属性）。

`　　　　Object.keys`返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 Symbol 属性）的键名。

`　　　　Object.getOwnPropertyNames`返回一个数组，包含对象自身的所有属性（不含 Symbol 属性，但是包括不可枚举属性）的键名。

`　　　　Object.getOwnPropertySymbols`返回一个数组，包含对象自身的所有 Symbol 属性的键名。

`　　　　Reflect.ownKeys`返回一个数组，包含对象自身的所有键名，不管键名是 Symbol 或字符串，也不管是否可枚举。

 **7.Object.getOwnPropertyDescriptors()**

**8.__proto__属性，Object.setPrototypeOf()，Object.getPrototypeOf()** 

**9.super 关键字**

**10.Object.keys()，Object.values()，Object.entries()**

 **11.对象的扩展运算符**

　　**a). 解构赋值**

　　**b). 扩展运算符**

 **12.Null 传导运算符**