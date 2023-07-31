# 02 【setup reactive ref】

## 1.拉开序幕的setup

### 1.1 为什么使用 setup ？

- 大型组件中选项的分离掩盖了潜在的逻辑问题。此外，在处理单个逻辑关注点时，我们必须不断地“跳转”相关代码的选项块。 如果能够将同一个逻辑关注点相关代码收集在一起会更好。而这正是组合式 API 使我们能够做到的。
- 通过创建 Vue 组件，我们可以将界面中重复的部分连同其功能一起提取为可重用的代码段。然而，光靠这一点可能并不够，尤其是当你的应用变得非常大的时候，共享和重用代码变得尤为重要。
- 为了开始使用 组合式 API，我们首先需要一个可以实际使用它的地方。在 Vue 组件中，我们将此位置称为 setup。

> **简单举例：** 角色权限页面功能：新增/删除角色、获取角色列表、获取角色对应的权限信息、编辑角色权限信息。
>
> - 通常以前会将这些功能写在一个sfc组件（.vue），当需要修改其中1处功能逻辑时，我们就需要跳转对应的各个options api选项进行操作。当有些业务组件复杂时，代码量上去了，浏览起来会更吃力。
> - 而有了setup、composition api后，我们可以将这例子中的4个功能逻辑拆分到对应的.js文件文件，使用composition api编写业务代码，然后引入到sfc组件的setup里使用。此时我们修改其中1处功能逻辑，只需要去对应的.js文件进行修改即可，而不必被其他的功能逻辑代码干扰。

> **错误用法：**
>
> **有些人写setup，以为是将vue2的写法，挪到setup内声明、return出去，导致setup内代码特别长，并且比options api写法更难以阅读！（当然代码量少的情况下，不影响阅读 也可不拆分）**

### 1.2 基本使用

1. 理解：Vue1.0中一个新的配置项，值为一个函数。
2. setup 函数是一个新的组件选项。它是组件内部使用组合式 API 的入口点。
3. 组件中所用到的：数据、方法等等，均要配置在setup中。
4. 调用时间：在创建组件实例时，在初始 prop 解析之后立即调用 setup。在生命周期方面，它是在 beforeCreate 钩子之前调用的。
5. setup函数的两种返回值：
   1. 若返回一个对象，则对象中的属性、方法, 在模板中均可以直接使用。（重点关注！）
   2. 若返回一个渲染函数：则可以自定义渲染内容。（了解）
6. 注意点：
   1. 尽量不要与Vue2.x配置混用
      - Vue2.x配置（data、methos、computed...）中**可以访问到**setup中的属性、方法。
      - 但在setup中**不能访问到**Vue2.x配置（data、methos、computed...）。
      - 如果有重名, setup优先。
   2. setup不能是一个async函数，因为返回值不再是return的对象, 而是promise, 模板看不到return对象中的属性。（后期也可以返回一个Promise实例，但需要Suspense和异步组件的配合）

> `setup()` 钩子是在组件中使用组合式 API 的入口，通常只在以下情况下使用：
>
> 1. 需要在非单文件组件中使用组合式 API 时。
> 2. 需要在基于选项式 API 的组件中集成基于组合式 API 的代码时。
>
> **其他情况下，都应优先使用 [`script setup`](https://staging-cn.vuejs.org/api/sfc-script-setup.html) 语法。**

```JavaScript
<template>
	<h1>一个人的信息</h1>
	<h2>姓名：{{name}}</h2>
	<h2>年龄：{{age}}</h2>
	<h2>性别：{{sex}}</h2>
	<h2>a的值是：{{a}}</h2>
	<button @click="sayHello">说话(Vue3所配置的——sayHello)</button>
	<br>
	<br>
	<button @click="sayWelcome">说话(Vue2所配置的——sayWelcome)</button>
	<br>
	<br>
	<button @click="test1">测试一下在Vue2的配置中去读取Vue3中的数据、方法</button>
	<br>
	<br>
	<button @click="test2">测试一下在Vue3的setup配置中去读取Vue2中的数据、方法</button>

</template>

<script>
	// import {h} from 'vue'
	export default {
		name: 'App',
		data() {
			return {
				sex:'男',
				a:100
			}
		},
		methods: {
			sayWelcome(){
				alert('欢迎来到尚硅谷学习')
			},
			test1(){
				console.log(this.sex)
				console.log(this.name)
				console.log(this.age)
				console.log(this.sayHello)
			}
		},
		//此处只是测试一下setup，暂时不考虑响应式的问题。
		 setup(props, { attrs, slots, emit, expose }){
		// console.log({ attrs, slots, emit, expose });
    	// attrs、slots 和 emit 分别等同于 $attrs、$slots、$emit 实例 property。
    	// expose 等同于 options api 的expose
			
             //数据
			let name = '张三'
			let age = 18
			let a = 200

			//方法
			function sayHello(){
				alert(`我叫${name}，我${age}岁了，你好啊！`)
			}
			function test2(){
				console.log(name)
				console.log(age)
				console.log(sayHello)
				console.log(this.sex)
				console.log(this.sayWelcome)
			}

			//返回一个对象（常用）
			return {
				name,
				age,
				sayHello,
				test2,
				a
			}

			//返回一个函数（渲染函数）
			// return ()=> h('h1','尚硅谷')
		}
	}
</script>

```

> **注意事项：**
>
> - setup 内的 this 是不指向组件实例的！ this > undefined
> - props 对象是响应式的——即在传入新的 props 时会对其进行更新，通过使用 watchEffect 或 watch 进行观测和响应；
> - 但是，请不要解构 props 对象，因为它会失去响应式；

### 1.3`<script setup>` 语法糖

![image-20230727104709004](../../../../AppData/Roaming/Typora/typora-user-images/image-20230727104709004.png)

## 2.reactive函数

- 作用: 定义一个**对象类型**的响应式数据（基本类型不要用它，要用`ref`函数）
- 语法：`const 代理对象= reactive(源对象)`接收一个对象（或数组），返回一个**代理对象（Proxy的实例对象，简称proxy对象）**
- reactive定义的响应式数据是“深层次的”。若要避免深层响应式转换，只想保留对这个对象顶层次访问的响应性，请使用 [shallowReactive()](https://staging-cn.vuejs.org/api/reactivity-advanced.html#shallowreactive) 作替代。
- 只能传入引用类型，否则抛出警告。 ***reactive 将解包所有深层的 refs，同时维持 ref 的响应性。******正确的讲应该是：当它通过代理访问时，会被自动解包：***
- 内部基于 ES6 的 Proxy 实现，通过代理对象操作源对象内部数据进行操作。