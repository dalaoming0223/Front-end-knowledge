

## 6.axios二次封装

```JavaScript
import axios from "axios";
//1、对axios二次封装
const requests = axios.create({
    //基础路径，requests发出的请求在端口号后面会跟改baseURl
    baseURL:'/api',
    timeout: 5000,
})
//2、配置请求拦截器
requests.interceptors.request.use(config => {
    //config内主要是对请求头Header配置
    //比如添加token
    
    return config;
})
//3、配置相应拦截器
requests.interceptors.response.use((res) => {
    //成功的回调函数
    return  res.data;
},(error) => {
    //失败的回调函数
    console.log("响应失败"+error)
    return Promise.reject(new Error('fail'))
})
//4、对外暴露
export default requests;
```

## 7.接口统一管理

项目很小：完全可以在组件的生命周期函数中发请求；

项目很大：要进行封装

### 7.1前端通过代理解决跨域问题

**跨域:** 如果多次请求协议、域名、端口号有不同的地方，称之为跨域 **解决办法:** JSONP、CROS、代理

```js
/在根目录下的vue.config.js中配置,proxy为通过代理解决跨域问题。
我们在封装axios的时候已经设置了baseURL为api,所以所有的请求都会携带/api，这里我们就将/api进行了转换。如果你的项目没有封装axios，或者没有配置baseURL，建议进行配置。要保证baseURL和这里的代理映射相同，此处都为'/api'。
module.exports = {
    //关闭eslint
    lintOnSave: false,
    devServer: {
        // true 则热更新，false 则手动刷新，默认值为 true
        inline: false,
        // development server port 8000
        port: 8001,
        //代理服务器解决跨域
        proxy: {
            //会把请求路径中的/api换为后面的代理服务器
            '/api': {
                //提供数据的服务器地址
                target: 'http://39.98.123.211',

            }
        },
    }
}
```

网站中的webpack.config.js就是vue.config.js文件

### 7.2请求接口统一封装

在文件夹api中创建index.js文件，用于封装所有请求 **将每个请求封装为一个函数，并暴露出去，组件只需要调用相应函数即可，这样当我们的接口比较多时，如果需要修改只需要修改该文件即可。**

如下所示：

```JavaScript
//当前模块，API进行统一管理，即对请求接口统一管理
import requests from "@/api/request";

//首页三级分类接口
export const reqCateGoryList = () => {
    return  requests({
        url: '/product/getBaseCategoryList',
        method: 'GET'
    })
}
```

当组件想要使用相关请求时，只需要导入相关函数即可，以上图的reqCateGoryList 为例:

```JavaScript
import {reqCateGoryList} from './api'
//发起请求
reqCateGoryList();
```

## 8.nprogress进度条插件

打开一个页面时，往往会伴随一些请求，并且会在页面上方出现进度条。它的原理时，在我们发起请求的时候开启进度条，在请求成功后关闭进度条，所以只需要在request.js中进行配置。 如下图所示，我们页面加载时发起了一个请求，此时页面上方出现蓝色进度条 ![在这里插入图片描述](https://gitee.com/river-ice/notes/raw/master/%E5%89%8D%E7%AB%AF/Project/assets/023a6a38365bb3cbea5289f80d59516dc65e9339.png) 对应的request.js设置

```javascript
import axios from "axios";
//引入进度条
import nprogress from 'nprogress';
//引入进度条样式
import "nprogress/nprogress.css";
//1、对axios二次封装
const requests = axios.create({
    //基础路径，requests发出的请求在端口号后面会跟改baseURl
    baseURL:'/api',
    timeout: 5000,
})
//2、配置请求拦截器
requests.interceptors.request.use(config => {
    //config内主要是对请求头Header配置
    //比如添加token

    //开启进度条
    nprogress.start();
    return config;
})
//3、配置相应拦截器
requests.interceptors.response.use((res) => {
    //成功的回调函数

    //响应成功，关闭进度条
    nprogress.done()
    return  res.data;
},(error) => {
    //失败的回调函数
    console.log("响应失败"+error)
    return Promise.reject(new Error('fail'))
})
//4、对外暴露
export default requests;
```

可以通过修改nprogress.css文件的background来修改进度条颜色。 ![在这里插入图片描述](https://gitee.com/river-ice/notes/raw/master/%E5%89%8D%E7%AB%AF/Project/assets/0accab6f78da3cfa29c071887c811f9ade50a4bc.png)



## 9.vuex

> 当项目比较大，组件通信数据比较复杂，这种情况在使用vuex
>
> Vuex是插件，通过vuex仓库进行存储项目的数据

首先确保安装了vuex,根目录创建store文件夹，文件夹下创建index.js，内容如下：

```JavaScript
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

//对外暴露store的一个实例
export default new Vuex.Store({
    state:{},
    mutations:{},
    actions:{},
    
})
```

如果想要使用vuex，还要再main.js中引入 main.js: (1) 引入文件 (2) 注册store **但凡是在main.js中的Vue实例中注册的实体，在所有的组件中都会有（this.$.实体名）属性**

```JavaScript
import store from './store'
new Vue({
  render: h => h(App),
  //注册路由，此时组件中都会拥有$router $route属性
  router,
  //注册store,此时组件中都会拥有$store
  store
}).$mount('#app')
```

### 9.1 vuex模块式开发【modules】

- 由于项目体积比较大，你向服务器发请求的接口过多，服务器返回的数据也会很多，如果还用以前的方式存储数据，导致vuex中的state数据格式比较复杂。采用vuex模块式管理数据。 Vuex核心概念:state、actions、mutations、getters、modules

getters计算属性，在项目当中，为了简化数据而生

仓库当中的state的数据格式，不能瞎写、胡写、乱写，数据格式取决于服务器返回的数据

以前基础课程的时候，发请求操作如下：在组件的mounted中书写axios.get||post,获取到数据存储到组件的data当中进行使用

你们写项目的时候发请求在哪里发呀？ mounted|created:都可以

mounted：模板已经变为真是DOM【只不过没有数据，显示空白】，因为ajax是异步，需要时间的。 created：稍微好那么一丢丢（不算啥）

## 10.卡顿现象

- 正常情况 (用户慢慢的操作) :鼠标进入， 每一个一级分类h3，都会触发鼠标进入事件
- 非正常情况 (用户操作很快)本身全部的级分类都应该触发鼠标进入事件，但是经过测试，只有部分h3触发了
- 由于用户行为过快，导致浏览器反应不过来
- 如果当前回调函数中有一些大量业务，有可能出现卡顿现象

### 10.1函数的防抖和节流

> 防抖： 前面的所有的触发都被取消，最后一次执行在规定的时间之后才会触发，也就是说如果连续快速的触发只会执行一次
> 例子:输入框搜索 输入完内容之后 一秒后才发送一次请求
> 解决： loadsh插件，封装函数的防抖与节流业务（闭包+延迟器）
> 对外暴露_函数
>
> 
>
> 
>
> 节流： 在规定的间隔时间范围内不会审复触发回调，只有大于这个时间间隔才会触发回调，把频繁触发变为少量触发
> 例子：计数器限定一秒内不管用户点击按钮多少次，数值只能加一
> 解决： _throttle()

    import throttle from 'lodash/throttle'

```javascript
import {throttle} from 'lodash'

methods: {
    //鼠标进入修改响应元素的背景颜色
    //采用键值对形式创建函数，将changeIndex定义为节流函数，该函数触发很频繁时，设置50ms才会执行一次
    changeIndex: throttle(function (index){
        this.currentIndex = index
    },50),
        //鼠标移除触发时间
        leaveIndex(){
        this.currentIndex = -1
    }
}
```



默认暴露 不需要花括号
回调函数不要用箭头函数，可能出现上下文this

    区别：
    防抖：用户操作很频繁，但是只是执行一次
    节流：用户操作很频繁，但是把频繁的操作变为少量操作[可以给浏览器有充裕的时间解析代码]
## 11.编程式导航+事件委托实现路由跳转


![img](https://gitee.com/river-ice/notes/raw/master/%E5%89%8D%E7%AB%AF/Project/assets/da7bf2aa195a43f7bc547065ff7662d7dbebf0a9.png) 如上图所示，三级标签列表有很多，每一个标签都是一个页面链接，我们要实现通过点击表现进行路由跳转。 路由跳转的两种方法：导航式路由，编程式路由。

> 1.对于导航式路由，我们有多少个a标签就会生成多少个router-link标签，这样当我们频繁操作时会出现卡顿现象。 
>
> 2.对于编程式路由，我们是通过触发点击事件实现路由跳转。同理有多少个a标签就会有多少个触发函数。虽然不会出现卡顿，但是也会影响性能。

上面两种方法无论采用哪一种，都会影响性能。我们提出一种：编程时导航+事件委派 的方式实现路由跳转。事件委派即把子节点的触发事件都委托给父节点。这样只需要一个回调函数goSearch就可以解决。 

**事件委派问题：** 

（1）如何确定我们点击的一定是a标签呢？如何保证我们只能通过点击a标签才跳转呢？ 

（2）如何获取子节点标签的商品名称和商品id(**我们是通过商品名称和商品id进行页面跳转的**)

**解决方法：**

 对于问题1：为三个等级的a标签添加自定义属性date-categoryName绑定商品标签名称来标识a标签（其余的标签是没有该属性的）。

对于问题2：为三个等级的a标签再添加自定义属性data-category1Id、data-category2Id、data-category3Id来获取三个等级a标签的商品id，用于路由跳转。 我们可以通过在函数中传入event参数，获取当前的点击事件，通过event.target属性获取当前点击节点，再通过dataset属性获取节点的属性信息。

三级联动的路由跳转与传参

如果使用声明式导航router-link，可以实现路由的跳转与传递参数
但是会出现卡顿现象。
原因： router-link为一个组件，当服务器的数据返回之后，循环出很多的router-link组件（需要创建组件实例）1000+ 数量较多
创建组件实例的时候，一瞬间创建上千个十分耗内存，因此出现卡顿现象。
编程式导航也不是最优化的实现方式
采用编程式导航+事件委派，避开循环语句，放置事件。
在这里插入图片描述
存在问题：
（1）点击的标签不能精确指定为a标签
（2）如何确定是几级a标签
解决：

    把子节点当中a标签，加上自定义属性data-categoryName, 其余的子节点不存在
    利用事件触发event，获取到当前触发这个事件的节点【h3,a,dt,dl】，但只需要带有data-categoryName的节点，即为a标签
    节点有个属性dataset属性， 可以获取节点的自定义属性与属性值
```JavaScript
//进行路由跳转的回调函数
    goSearch(event) {
      //event.target:获取到的是出发事件的元素(div、h3、a、em、dt、dl)
      let node = event.target;
      //给a标签添加自定义属性data-categoryName,全部的字标签当中只有a标签带有自定义属性，别的标签名字----dataset纯属扯淡
      let {
        categoryname,
        category1id,
        category2id,
        category3id,
      } = node.dataset;
      //第二个问题解决了：点击的到底是不是a标签（只要这个标签身上带有categoryname）一定是a标签
      //当前这个if语句：一定是a标签才会进入
      if (categoryname) {
        //准备路由跳转的参数对象
        let loction = { name: "search" };
        let query = { categoryName: categoryname };
        //一定是a标签：一级目录
        if (category1id) {
          query.category1Id = category1id;
          //一定是a标签：二级目录
        } else if (category2id) {
          query.category2Id = category2id;
          //一定是a标签：三级目录
        } else {
          query.category3Id = category3id;
        }
        //判断：如果路由跳转的时候，带有params参数，捎带脚传递过去
        if (this.$route.params) {
          loction.params = this.$route.params;
          //动态给location配置对象添加query属性
          loction.query = query;
          //路由跳转
          this.$router.push(loction);
        }
      }
    },

```



## =========个人问题记录：

### vuex：

#### 1、开启命名空间后使用mapState

![image-20230706110456250](../../../../AppData/Roaming/Typora/typora-user-images/image-20230706110456250.png)