Fetch API 是用于获取资源（或数据）的接口，提供了一种更简单、更直观的方式来发起 HTTP 请求和处理响应结果。以下是 Fetch API 的常用方法：

#### fetch(url[, options])

该方法接收一个 URL 和可选参数对象，返回一个 Promise 对象，用于发起 HTTP 请求并获取响应结果。可选参数对象包含如下属性：

- `method`：HTTP 方法类型，默认为 "GET"。
- `headers`：请求头部信息。
- `body`：请求体数据。
- `mode`：请求模式，例如 "cors"、"no-cors"、"same-origin" 等。
- `cache`：缓存模式，例如 "no-cache"、"reload"、"force-cache" 等。
- `redirect`：重定向模式，例如 "follow"、"error"、"manual" 等。
- `referrer`：引用页面 URL。
- `integrity`：完整性校验码。

示例代码：

```
javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    name: 'John',
    age: 30
  })
})
.then(response => {
  if (!response.ok) {
    throw new Error('Network response was not ok');
  }
  return response.json();
})
.then(data => {
  console.log(data);
})
.catch(error => {
  console.error('Error:', error);
});
```

#### Response

该类表示一个 HTTP 响应，包含响应头部、响应状态码和响应内容等信息。该类提供了如下方法：

- `clone()`：复制一个响应。
- `error()`：返回一个拒绝状态的 Promise 对象，代表请求失败。
- `redirect()`：返回一个新的 Response 对象，用于重定向请求。
- `arrayBuffer()`：返回一个 Promise 对象，用于获取二进制数据。
- `blob()`：返回一个 Promise 对象，用于获取 Blob 对象。
- `formData()`：返回一个 Promise 对象，用于获取 FormData 对象。
- `json()`：返回一个 Promise 对象，用于获取 JSON 数据。
- `text()`：返回一个 Promise 对象，用于获取文本字符串。

示例代码：

```
javascript
fetch('https://api.example.com/data')
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

#### Request

该类表示一个 HTTP 请求，包含请求头部、请求方法、请求模式和请求体等信息。该类提供了如下方法：

- `clone()`：复制一个请求。
- `headers`：请求头部信息。
- `method`：HTTP 方法类型。
- `url`：请求 URL。
- `referrer`：引用页面 URL。
- `referrerPolicy`：引用页面的安全策略。
- `mode`：请求模式，例如 "cors"、"no-cors"、"same-origin" 等。
- `credentials`：请求的凭证，例如 "omit"、"same-origin"、"include" 等。
- `cache`：缓存模式，例如 "no-cache"、"reload"、"force-cache" 等。
- `redirect`：重定向模式，例如 "follow"、"error"、"manual" 等。
- `integrity`：完整性校验码。

示例代码：

```
javascript
const request = new Request('https://api.example.com/data', {
```