## 疑惑：axios中只有params跟data传参

在axios中，可以使用`params`参数来传递URL查询参数。以下是几种使用`params`参数的方式：

### 1、作为单个对象传递：

```javascript
axios.get('/api/data', {
  params: {
    param1: 'value1',
    param2: 'value2'
  }
})
```
上述代码将会发送一个GET请求到`/api/data`，并附带查询参数`param1=value1`和`param2=value2`。

### 2、使用URL模板和`params`参数：

```javascript
axios.get('/api/data/{id}', {
  params: {
    id: 12345,
    param1: 'value1'
  }
})
```
在这个例子中，URL模板`/api/data/{id}`中的`{id}`将被替换为实际的值`12345`，同时还附带了查询参数`param1=value1`。

### 3、序列化参数：

```javascript
axios.get('/api/data', {
  params: {
    arrayParam: [1, 2, 3],
    nestedParam: {
      param1: 'value1',
      param2: 'value2'
    }
  },
  paramsSerializer: params => {
    return qs.stringify(params, { arrayFormat: 'brackets' });
  }
})
```
在这个例子中，使用了`qs`库对参数进行序列化，

`arrayParam`将被序列化为`arrayParam[]=1&arrayParam[]=2&arrayParam[]=3`，

`nestedParam`将被序列化为`nestedParam[param1]=value1&nestedParam[param2]=value2`。

需要注意的是，上述例子中的`axios.get`可以根据具体情况替换为其他HTTP方法（如`axios.post`、`axios.put`等）。

这些是传递`params`参数的几种常见方式，您可以根据具体需求选择合适的方式来使用。