# HTTP 实用指南

## 初识 HTTP

![在这里插入图片描述](https://img-blog.csdnimg.cn/85921045a0aa44e889bf5e009ab5d983.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/b92305f30e194fb1b785d6e83ca1f200.png)

## 协议分析

### 发展

![在这里插入图片描述](https://img-blog.csdnimg.cn/c0d94bbe29094f55ad529ab177e281c1.png)

### 报文

#### Method

| 方法名  | 作用                                                         |
| ------- | ------------------------------------------------------------ |
| GET     | 请求一个指定资源的表示形式，使用GET的请求应该只被用于获取数据 |
| POST    | 用于将实体提交到指定的资源，通常导致在服务器上的状态变化或副作用 |
| PUT     | 用请求有效载荷替换目标资源的所有当前表示                     |
| DELETE  | 删除指定资源                                                 |
| HEAD    | 请求一个与GET请求的响应相同的响应，但没有响应体              |
| CONNECT | 建立一个到由目标资源标识的服务器的隧道                       |
| OPTIONS | 用于描述目标资源的通信选项                                   |
| TRACE   | 沿着到目标资源的路径执行一个消息环回测试                     |
| PATCH   | 用于对资源应用部分修改                                       |

![在这里插入图片描述](https://img-blog.csdnimg.cn/5cceb283f5344fb5b372e4b180b14dbb.png)

#### 状态码

![在这里插入图片描述](https://img-blog.csdnimg.cn/a26a9086424746c39c4e026116fa4ea5.png)

#### RESTful API

![在这里插入图片描述](https://img-blog.csdnimg.cn/13e09f30959245799baf35780d7b018c.png)

#### 常用请求头

| 请求              | 作用                                                         |
| ----------------- | ------------------------------------------------------------ |
| Accept            | 接收类型，表示浏览器支持的MIME类型(对标服务端返回的Content-Type) |
| Content-Type      | 客户端发送出去实体内容的类型                                 |
| Cache-Control     | 指定请求和响应遵循的缓存机制，如no-cache                     |
| If-Modified-Since | 对应服务端的Last- Modified,用来匹配看文件是否变动，只能精确到1s之内 |
| Expires           | 缓存控制，在这个时间内不会请求，直接使用缓存，服务端时间     |
| Max-age           | 代表资源在本地缓存多少秒，有效时间内不会请求，而是使用缓存   |
| If-None - Match   | 对应服务端的ETag,用来匹配文件内容是否改变(非常精确)Cookie    |
| Cookie            | 有cookie并且同域访问时会自动带上                             |
| Referer           | 该页面的来源URL(适用于所有类型的请求，会精确到详细页面地址，csrf拦截常用到这个字段 |
| Origin            | 最初的请求是从哪里发起的(只会精确到端口) ,Origin比Referer更 尊重隐私 |
| User-Agent        | 用户客户端的一些必要信息，如UA头部等                         |

#### 常用响应头

| 响应                        | 作用                                                        |
| --------------------------- | ----------------------------------------------------------- |
| Content-Type                | 服务端返回的实体内容的类型                                  |
| Cache-Control               | 指定请求和响应遵循的缓存机制，如no-cache                    |
| Last- Modified              | 请求资源的最后修改时间                                      |
| Expires                     | 应该在什么时候认为文档已经过期，从而不再缓存它              |
| Max- age                    | 客户端的本地资源应该缓存多少秒，开启了Cache-Control后有效   |
| ETag                        | 资源的特定版本的标识符，Etags类似于指纹                     |
| Set-Cookie                  | 设置和页面关联的cookie,服务器通过这个头部把cookie传给客户端 |
| Server                      | 服务器的一些相关信息                                        |
| Access-Control-Allow-Origin | 服务器端允许的请求Origin头部(譬如为*)                       |

#### 缓存

![在这里插入图片描述](https://img-blog.csdnimg.cn/c8398bf293a34024b336f5c91fbe8093.png)

![image-20220806105616208](/Users/zaizai/Library/Application Support/typora-user-images/image-20220806105616208.png)

#### cookie

| 参数                      | 作用                                                         |
| ------------------------- | ------------------------------------------------------------ |
| Name=value                | 各种cookie的名称和值                                         |
| Expires=Date              | Cookie的有效期，缺省时Cookie仅在浏览器关闭之前有效           |
| Path=Path                 | 限制指定Cookie的发送范围的文件目录，默认为当前               |
| Domain=domain             | 限制cookie生效的域名，默认为创建cookie的服务域名             |
| secure                    | 仅在HTTPS安全连接时，才可以发送Cookie                        |
| HttpOnly                  | JavaScript脚本无法获得Cookie                                 |
| SameSite=[NonelStrictLax] | None同站、跨站请求都可发送<br/>Strict仅在同站发送<br/>允许与顶级导航一起发送，并将与第三方网站<br/>发起的GET请求一起发送 |

## 场景分析

![在这里插入图片描述](https://img-blog.csdnimg.cn/229930e31ec84c9d912df437dbec5dee.png)

### 静态资源

![在这里插入图片描述](https://img-blog.csdnimg.cn/2a7a9ce3767f424694b668290814f973.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/b0cf9a1a9dc74c85859f3520abcc9d08.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/a2e7c9f3aa2d45fa9cfa4f49ddb8ab67.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/6909c70e4943445e95ac40c54605a887.png)

## 拓展

![在这里插入图片描述](https://img-blog.csdnimg.cn/11dcbf27570e4f0492ca06e3f5fe924f.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/bc9d3a26b9164a978bee49c4616269f3.png)