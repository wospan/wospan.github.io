# Test1


撒打算打算

撒大声地

sadas

 撒大声地

 啊实打实

阿萨德as

市大安市

#### 1、hvv面试

#### 2、cors跨域漏洞

###### 	1、寻找cors漏洞的标准

```shell
修改`Origin:`，使得返回的HTTP字段中的`Access-Control-Allow-Origin: `出现你所输入的值，表明此网站存在CSOR漏洞
```

###### 	2、什么是同源

​	当两个页面是同源的时候，资源是可以直接进行交互的。但当两个页面来自不同的源却也想进行资源交互的话，就受到了同源策略的约束。那**同源策略**就是限制了从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互

​	通俗来说：同域不同路径

###### 	3、什么是CORS

​	跨域资源共享(CORS) 是一种机制，通过定义额外的HTTP头来使浏览器能够允许不同源之间的资源交互。

**HTTP 请求首部字段**

- `Origin: <origin>` 表明预检请求或实际请求的源站。

用于预检请求的HTTP请求首部字段（[CORS预检请求详谈](https://www.cnblogs.com/wonyun/p/CORS_preflight.html)）：

- `Access-Control-Request-Method: <method>` 用于预检请求。其作用是。将实际请求所使用的 HTTP 方法告诉服务器。
- `Access-Control-Request-Headers: <field-name>[, <field-name>]*`用于预检请求。其作用是，将实际请求所携带的首部字段告诉服务器。

**HTTP 响应首部字段**

- `Access-Control-Allow-Origin: <origin> | *` origin 参数的值指定了允许访问该资源的外域 URI。对于不需要携带身份凭证的请求，服务器可以指定该字段的值为通配符，表示允许来自所有域的请求。
- `Access-Control-Expose-Headers: X-My-Custom-Header, X-Another-Custom-Header` 让服务器把允许浏览器访问的头放入白名单，XMLHttpRequest对象就能够通过getResponseHeader访问到 `X-My-Custom-Header`和 `X-Another-Custom-Header` 响应头了。
- `Access-Control-Max-Age: <delta-seconds>` 指定了preflight请求的结果能够被缓存多久
- `Access-Control-Allow-Credentials: true` 指定了当浏览器的`credentials`设置为true时是否允许浏览器读取response的内容。

用于预检请求的HTTP响应首部字段：

- `Access-Control-Allow-Methods: <method>[, <method>]*` 用于预检请求的响应。其指明了实际请求所允许使用的 HTTP 方法。
- `Access-Control-Allow-Headers: <field-name>[, <field-name>]*` 用于预检请求的响应。其指明了实际请求中允许携带的首部字段。

**一个简单的例子：**

这里跳过了预检请求，并且数据包也简化了。

```shell
请求数据包：
POST /resources/post-here/ HTTP/1.1
Host: example.com
Origin: http://foo.example.com

[post data]


HTTP/1.1 200 OK
Access-Control-Allow-Origin: http://foo.example.com
Access-Control-Allow-Credentials: true

[result]
```

从上面的请求中可以看得出来，foo.example.com向example.com发送跨域请求，并且成功获取到数据。

###### 4、如何利用

**可绕过的域名校验**

当域名校验不是特别严格时，可以通过以下几种方式进行绕过：

- 在后面加域名 qq.com => qq.com.abc.com
- 将域名拼接 abc.qq.com => abc_qq.com
- 在前面或者在后面加字符 qq.com => abcqq.com / qq.com => qq.comabc.com

**配合XSS进行利用**

当同源网站中存在一个xss漏洞时，就可以直接使用xss包含cors的payload进行利用。

ps：我都xss了我要这跨域有啥用

**Safari浏览器的特殊性质**

当遇到这样的正则表达式所校验的域名时：(允许所有“target.local”的子域名的跨域请求，并且这些请求可以来自于子域名的任意端口)

```
^https?:\/\/(.*\.)?target.local([^\.\-a-zA-Z0-9]+.*)?
```



<!--more-->

