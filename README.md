Koa
================================================
```
Koa:通过利用async函数，koa丢弃回调函数，并增强错误处理,
不捆绑任何中间件。

1、更优雅、简单、安全的中间件机制
2、更优雅、简单的异常处理
3、更优雅、简单的异步编程方式

安装：npm install koa

使用Babel实现Async方法：
    transform-async-to-generator或transform-async-to-module-method插件来解析和编译async方法

    async：只有当所有的await异步都执行完之后才能返回一个promise

应用程序：
    Koa包含一组中间件函数的对象，类似堆栈的方式组织和执行的。
    低级中间件层提供高级“语法糖”封装，提高了互操作性、稳健性
    需要的中间件可以自己造；app.use()

    const Koa=require('koa')
    const app=new Koa()

    app.use(async ctx=>{
        ctx.body="hello";
    });

    app.listen(3000)

级联：
    await next():执行了next函数，才能正确执行下一个中间件，每个中间件最多执行一次next

设置：
    app.env默认是NODE_ENV或“development”
    app.proxy真正的代理头字段将被信任时
    app.subdomainOffset对于要忽略的 .subdomains偏移

app.listen()
app.callback()
app.use(function)
app.keys=
    设置签名的Cookie密钥
app.context

错误处理：
    error事件侦听器

上下文(Context)：
    将request和response对象封装到单个对象中

Api：
    Context具体方法和访问器

Node:
    ctx.req
    ctx.res
Koa:
    ctx.request
    ctx.response
    ctx.state:用于通过中间件传递信息和前端视图
    ctx.app
    ctx.cookies.get(name,[options]):
        获取cookie name
    ctx.cookie.set(name,value,[options])：
        设置cookie name的value
    ctx.throw([status],[msg],[properties])
    ctx.assert(value,[status],[msg],[properties])
    ctx.respond:
        绕过koa的内置response处理
        原始的res对象不让koa处理response

请求Request：
    api：
        request.header：请求标头对象
        request.header=：设置请求标头对象
        request.headers：请求标头对象
        request.method：请求方法
        request.method=：设置请求方法
        request.length：返回以数字返回请求的content-length
        request.url
        request.url=
        request.originalUrl：获取请求原始的URL
        request.origin：获取url的来源
        request.href：获取完整的请求url
        request.path
        requset.path=
        request.querystring
        request.querystring=
        request.search
        request.search=
        request.host
        request.hostname
        requset.URL
        request.type
        request.charset
        request.query
        request.query=
        request.fresh:检查请求缓存是否“新鲜”，也就是内容没有改变
        request.stale
        request.protocol:返回请求协议，“https” 或 “http”。
        request.secure
        request.ip
        request.ips
        request.subdomains
        request.is(types...)

响应Response：

```