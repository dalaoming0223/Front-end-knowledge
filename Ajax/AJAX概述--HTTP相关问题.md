# 简介

## 定义

Axios 是一个基于 *[promise](https://gitee.com/link?target=https%3A%2F%2Fjavascript.info%2Fpromise-basics)* 网络请求库，作用于[`node.js`](https://gitee.com/link?target=https%3A%2F%2Fnodejs.org%2F) 和浏览器中。 它是 *[isomorphic](https://gitee.com/link?target=https%3A%2F%2Fwww.lullabot.com%2Farticles%2Fwhat-is-an-isomorphic-application)* 的(即同一套代码可以运行在浏览器和node.js中)。在服务端它使用原生 node.js `http` 模块, 而在客户端 (浏览端) 则使用 XMLHttpRequests。

## 特性

- 从浏览器创建 [XMLHttpRequests](https://gitee.com/link?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FXMLHttpRequest)
- 从 node.js 创建 [http](https://gitee.com/link?target=http%3A%2F%2Fnodejs.org%2Fapi%2Fhttp.html) 请求
- 支持 [Promise](https://gitee.com/link?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FJavaScript%2FReference%2FGlobal_Objects%2FPromise) API
- 拦截请求和响应
- 转换请求和响应数据
- 取消请求
- 自动转换JSON数据
- 客户端支持防御[CSRF](https://gitee.com/link?target=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FCross-site_request_forgery)

## 安装

1. 使用npm：`npm install axios`

2. 使用bower：`bower install axios`

3. 使用yarn：`yarn add axios`

4. 使用jsDelivr CDN：

   ```
   <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
   ```

5. 使用unpkg CDN：

   ```
   <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
   ```

# 常见基本用例

## 引入

### CommonJS用法

```
const axios = require('axios').default;
// axios.<method> 能够提供自动完成和参数类型推断功能
```

### ES6模块化用法

```
import axios from "axios"	//需要先完成axios安装
```

## `GET`请求

```javascript
const axios = require('axios');

// 向给定ID的用户发起请求
axios.get('/user?ID=12345')
  .then(function (response) {	// 处理成功情况
    console.log(response);
  })
  .catch(function (error) {	// 处理错误情况
    console.log(error);
  })
  .then(function () {	// 总是会执行
  });

// 上述请求也可以按以下方式完成（可选）
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  })
  .then(function () {	// 总是会执行
  });  

// 支持async/await用法
async function getUser() {
  try {
    const response = await axios.get('/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

## `POST`请求

发起一个请求

```javascript
axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

发起多个并发请求

```javascript
function getUserAccount() {
  return axios.get('/user/12345');
}

function getUserPermissions() {
  return axios.get('/user/12345/permissions');
}

Promise.all([getUserAccount(), getUserPermissions()])
  .then(function (results) {
    const acct = results[0];
    const perm = results[1];
  });
```