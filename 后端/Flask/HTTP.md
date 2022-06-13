# HTTP
## HTTP 请求
### 设置监听的 HTTP 方法
我们可以在 app.route() 装饰器中使用 methods 参数传入一个包含监听的 HTTP 方法的可迭代对象。比如，下面的视图函数同时监听 GET 请求和 POST 请求：
```python
@app.route('/hello', methods=['GET', 'POST'])
def hello():
	return '<h1>Hello, Flask!</h1>'
```
### URL 处理

转换器通过特定的规则指定，即 "<转换器：变量名>"。

![《Flask Web开发实战：入门、进阶与原理解析（李辉著 ）》PDF](E:\笔记\Flask学习\picture\表2-6　Flask内置的URL变量转换器.jpg)

### 请求钩子
有时我们需要对请求进行预处理（preprocessing）和后处理（postprocessing），这时可以使用 Flask 提供的一些请求钩子（Hook），它们可以用来注册在请求处理的不同阶段执行的处理函数（或称为回调函数，即Callback）。这些请求钩子使用装饰器实现，通过程序实例 app 调用，用法很简单：以 before_request 钩子（请求之前）为例，当你对一个函数附加了 app.before_request 装饰器后，就会将这个函数注册为before_request 处理函数，每次执行请求前都会触发所有 before_request 处理函数。

![表2-7　请求钩子](E:\笔记\Flask学习\picture\表2-7　请求钩子.jpg)

## HTTP 响应

### 在 Flask 中生成响应

#### 重定向
重定向到目标 URL
```python
from flask import Flask, redirect
...
@app.route('/hello')
def hello():
	return redirect('http://www.example.com')
```
重定向到其他视图
```python
from flask import Flask, redirect, url_for
...
@app.route('/hi')
def hi():
...
	return redierct(url_for('hello')) # 重定向到/hello
@app.route('/hello')
def hello():
...
```
#### 错误响应
大多数情况下，Flask 会自动处理常见的错误响应。HTTP 错误对应的异常类在 Werkzeug 的werkzeug.exceptions 模块中定义，抛出这些异常即可返回对应的错误响应。如果你想手动返回错误响应，更方便的方法是使用 Flask 提供的 abort() 函数。在 abort() 函数中传入状态码即可返回对应的错误响应。
```python
# 返回404错误响应
from flask import Flask, abort
...
@app.route('/404')
def not_found():
	abort(404)
```
### 响应格式
MIME 类型（又称为 media type 或 content type ）是一种用来标识文件类型的机制，它与文件扩展名相对应，可以让客户端区分不同的内容类型，并执行不同的操作。一般的格式为"类型名/子类型名"，其中的子类型名一般为文件扩展名。比如，HTML 的 MIME 类型为"text/html"，png图片的MIME类型为"image/png"。完整的标准MIME类型列表可以在这里看到：https://www.iana.org/assignments/media-types/mediatypes.xhtml。

如果你想使用其他 MIME 类型，可以通过 Flask 提供的 make_response() 方法生成响应对象，传入响应的主体作为参数，然后使用响应对象的 mimetype 属性设置 MIME 类型
1. 纯文本 MIME:text/plain
2. HTML MIME:text/html
3. XML MIME:application/xml
XML（https://www.w3.org/XML/）指 Extensible Markup Language（可扩展标记语言），它是一种简单灵活的文本格式，被设计用来存储和交换数据。XML的出现主要就是为了弥补 HTML 的不足：对于仅仅需要数据的请求来说，HTML 提供的信息太过丰富了，而且不易于重用。XML和HTML一样都是标记性语言，使用标签来定义文本，但 HTML 中的标签用于显示内容，而XML中的标签只用于定义数据。XML 一般作为 AJAX 请求的响应格式，或是 Web API 的响应格式。
4. JSON MIME:application/json
JSON（http://json.org/）指 JavaScript Object Notation（JavaScript对象表示法），是一种流行的、轻量的数据交换格式。它的出现又弥补了XML的诸多不足：XML有较高的重用性，但 XML 相对于其他文档格式来说体积稍大，处理和解析的速度较慢。JSON轻量，简洁，容易阅读和解析，而且能和 Web 默认的客户端语言 JavaScript 更好地兼容。JSON 的结构基于“键值对的集合”和“有序的值列表”，这两种数据结构类似 Python 中的字典（dictionary）和列表（list）。正是因为这种通用的数据结构，使得 JSON 在同样基于这些结构的编程语言之间交换成为可能。

Flask 通过引入 Python 标准库中的 json 模块（或 simplejson，如果可用）为程序提供了 JSON 支持。你可以直接从 Flask 中导入 json 对象，然后调用 dumps() 方法将字典、列表或元组序列化（serialize）为JSON 字符串，再使用前面介绍的方法修改 MIME 类型，即可返回 JSON 响应，如下所示：
```python
from flask import Flask, make_response, json
...
@app.route('/foo')
def foo():
	data = {
		'name':'Grey Li',
		'gender':'male'
	}
	response = make_response(json.dumps(data))
	response.mimetype = 'application/json'
	return response
```
不过我们一般并不直接使用 json 模块的 dumps()、load() 等方法，因为 Flask 通过包装这些方法提供了更方便的 jsonify() 函数。借助 jsonify() 函数，我们仅需要传入数据或参数，它会对我们传入的参数进行序列化，转换成 JSON 字符串作为响应的主体，然后生成一个响应对象，并且设置正确的 MIME 类型。使用jsonify 函数可以将前面的例子简化为这种形式：
```python
from flask import jsonify
@app.route('/foo')
def foo():
	return jsonify(name='Grey Li', gender='male')
```
### Cookie
Cookie 指 Web 服务器为了存储某些数据（比如用户信息）而保存在浏览器上的小型文本数据。浏览器会在一定时间内保存它，并在下一次向同一个服务器发送请求时附带这些数据。Cookie 通常被用来进行用户会话管理（比如登录状态），保存用户的个性化信息（比如语言偏好，视频上次播放的位置，网站主题选项等）以及记录和收集用户浏览数据以用来分析用户行为等。

#### 设置 Cookie
```python
from flask import Flask, make_response
...
@app.route('/set/<name>')
def set_cookie(name):
	response = make_response(redirect(url_for('hello')))
	response.set_cookie('name', name)
	return response
```
在这个 make_response() 函数中，我们传入的是使用 redirect() 函数生成的重定向响应。set_cookie视图会在生成的响应报文首部中创建一个 Set-Cookie 字段，即 "Set-Cookie：name=Grey；Path=/"。

### session
#### 设置程序密钥
```python
app.secret_key='string'
```
#### 模拟用户认证
```python
@app.route('/login')
def login():
    session['logged_in'] = True
    return redirect(url_for('hello'))

@app.route('/logout')
def logout():
    if 'logged_in' in session:
        session.pop('logged_in')
    return redirect(url_for('hello'))
```
## Flask 上下文
我们可以把编程中的上下文理解为当前环境（environment）的快照（snapshot）。如果把一个Flask程序比作一条可怜的生活在鱼缸里的鱼的话，那么它当然离不开身边的环境。

Flask 中有两种上下文，程序上下文（application context）和请求上下文（request context）。如果鱼想要存活，水是必不可少的元素。对于Flask程序来说，程序上下文就是我们的水。水里包含了各种浮游生物以及微生物，正如程序上下文中存储了程序运行所必须的信息；要想健康地活下去，鱼还离不开阳光。射进鱼缸的阳光就像是我们的程序接收的请求。当客户端发来请求时，请求上下文就登场了。请求上下文里包含了请求的各种信息，比如请求的 URL，请求的 HTTP 方法等。

![表2-12　Flask中的上下文变量](E:\笔记\Flask学习\picture\表2-12　Flask中的上下文变量.jpg)

### 激活上下文
在下面这些情况下，Flask 会自动帮我们激活程序上下文：
1. 当我们使用 flask run 命令启动程序时。
2. 使用旧的 app.run() 方法启动程序时。
3. 执行使用 @app.cli.command() 装饰器注册的 flask 命令时。
4. 使用 flask shell 命令启动 Python Shell 时。

## HTTP 进阶实践
### 重定向回上一个页面
#### 获取上一个页面的 URL
在 URL 中手动加入包含当前页面 URL 的查询参数，这个查询参数一般命名为 next。比如，下面在 foo 和 bar 视图的返回值中的 URL 后添加 next 参数：
```python
from flask import request
@app.route('/foo')
def foo():
    return '<h1>Foo page</h1><a href="%s">Do something</a>' % url_for('do_something', next=request.full_path)

@app.route('/bar')
def bar():
    return '<h1>Bar page</h1><a href="%s">Do something</a>' % url_for('do_something', next=request.full_path)

```
首先获取 next 参数，如果为空就尝试获取 referer，如果仍然为空，那么就重定向到默认的 hello 视图。因为在不同视图执行这部分操作的代码完全相同，我们可以创建一个通用的 redirect_back() 函数:
```python
def redirect_back(default='hello', **kwargs):
	for target in request.args.get('next'), request.referrer:
		if target:
			return redirect(target)
	return redirect(url_for(default, **kwargs))
```

#### 对 URL 进行安全验证

虽然我们已经实现了重定向回上一个页面的功能，但安全问题不容小觑，鉴于 referer 和 next 容易被篡改的特性，如果我们不对这些值进行验证，则会形成开放重定向（Open Redirect）漏洞。

以 URL 中的 next 参数为例，next 变量以查询字符串的方式写在 URL 里，因此任何人都可以发给某个用户一个包含 next 变量指向任何站点的链接。举个简单的例子，如果你访问下面的 URL：
http://localhost:5000/do-something?next=http://helloflask.com

程序会被重定向到 http://helloflask.com。也就是说，如果我们不验证 next 变量指向的 URL 地址是否属于我们的应用内，那么程序很容易就会被重定向到外部地址。你也许还不明白这其中会有什么危险，下面假设的情况也许会给你一个清晰的认识：

假设我们的应用是一个银行业务系统（下面简称网站 A），某个攻击者模仿我们的网站外观做了一个几乎一模一样的网站（下面简称网站 B）。接着，攻击者伪造了一封电子邮件，告诉用户网站A账户信息需要更新，然后向用户提供一个指向网站 A 登录页面的链接，但链接中包含一个重定向到网站 B 的 next 变量，比如：http://exampleA.com/login?next=http://maliciousB.com。当用户在 A 网站登录后，如果 A 网站重定向到 next 对应的URL，那么就会导致重定向到攻击者编写的B网站。因为 B 网站完全模仿 A 网站的外观，攻击者就可以在重定向后的B网站诱导用户输入敏感信息，比如银行卡号及密码。确保URL安全的关键就是判断 URL 是否属于程序内部，我们创建了一个 URL 验证函数 is_safe_url()，用来验证 next 变量值是否属于程序内部 URL。
```python
def is_safe_url(target):
    ref_url = urlparse(request.host_url)
    test_url = urlparse(urljoin(request.host_url, target))
    return test_url.scheme in ('http', 'https') and \
           ref_url.netloc == test_url.netloc
```
### 使用 AJAX 技术发送异步请求
#### 认识 AJAX
AJAX 指异步 Javascript 和 XML（Asynchronous JavaScript AndXML），它不是编程语言或通信协议，而是一系列技术的组合体。简单来说，AJAX 基于 XMLHttpRequest（https://xhr.spec.whatwg.org/）让我们可以在不重载页面的情况下和服务器进行数据交换。加上 JavaScript 和 DOM（Document Object Model，文档对象模型），我们就可以在接收到响应数据后局部更新页面。而 XML 指的则是数据的交互格式，也可以是纯文本（Plain Text）、HTML 或 JSON。顺便说一句，XMLHttpRequest 不仅支持 HTTP 协议，还支持 FILE 和FTP 协议。

以删除某个资源为例，在普通的程序中流程如下：
1. 当“删除”按钮被单击时会发送一个请求，页面变空白，在接收到响应前无法进行其他操作。
2. 服务器端接收请求，执行删除操作，返回包含整个页面的响应。
3. 客户端接收到响应，重载整个页面。

使用 AJAX 技术时的流程如下：
1. 当单击“删除”按钮时，客户端在后台发送一个异步请求，页面不变，在接收响应前可以进行其他操作。
2. 服务器端接收请求后执行删除操作，返回提示消息或是无内容的204响应。
3. 客户端接收到响应，使用JavaScript更新页面，移除资源对应的页面元素。

#### 使用 jQuery 发送 AJAX 请求
jQuery 是流行的 JavaScript 库，它包装了 JavaScript，让我们通过更简单的方式编写 JavaScript 代码。对于 AJAX，它提供了多个相关的方法，使用它可以很方便地实现 AJAX 操作。更重要的是，jQuery 处理了不同浏览器的 AJAX 兼容问题，我们只需要编写一套代码，就可以在所有主流的浏览器正常运行。

#### 返回"局部数据"
1. 纯文本或局部 HTML 模板
	纯文本可以在 JavaScript 用来直接替换页面中的文本值，而局部 HTML 则可以直接到插入页面中，比如返回评论列表：
	```python
	@app.route('/comments/<int:post_id>')
	def get_comments(post_id):
		...
		return render_template('comments.html')
	```
	
2. JSON 数据
	JSON 数据可以在 JavaScript 中直接操作：
	```python
	@app.route('/profile/<int:user_id>')
	def get_profile(user_id):
		...
		return jsonify(username=username, bio=bio)
	```
	
3. 空值
	有些时候，程序中的某些接收 AJAX 请求的视图并不需要返回数据给客户端，比如用来删除文章的视图。这时我们可以直接返回空值，并将状态码指定为 204（表示无内容），比如：
	```python
	@app.route('/post/delete/<int:post_id>', methods=['DELETE'])
	def delete_post(post_id):
		...
		return '', 204
	```
	
4. 异步加载长文章示例
	在示例程序的对应页面中，我们将显示一篇很长的虚拟文章，文章正文下方有一个“加载更多”按钮，当加载按钮被单击时，会发送一个 AJAX 请求获取文章的更多内容并直接动态插入到文章下方。

   ```python
   @app.route('/post')
   def show_post():
       post_body = generate_lorem_ipsum(n=2) # 生成两段随机文本
       return '''
   <h1>A very long post</h1>
   <div class="body">%s</div>
   <button id="load">Load More</button>
   <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
   <script type="text/javascript">
   $(function() {
       $('#load').click(function() {
           $.ajax({
               url: '/more', // 目标URL
               type: 'get', // 请求方法
               success: function(data){ // 返回2XX响应后触发的回调函数
                   $('.body').append(data); // 将返回的响应插入到页面中
               }
           })
       })
   })
   </script>''' % post_body
   ```
   文章的随机正文通过 Jinja2 提供的 generate_lorem_ipsum() 函数生成，n 参数用来指定段落的数量，默认为 5，它会返回由随机字符组成的虚拟文章。文章下面添加了一个“加载更多”按钮。按钮下面是两个 \<script>\</script> 代码块，第一个 script 从 CDN 加载jQuery 资源。
	
	在第二个 script 标签中，我们在代码的最外层创建了一个 \$(function(){...}) 函数，这个函数是常见的 \$(document).ready(function(){...}) 函数的简写形式。这个函数用来在页面 DOM 加载完毕后执行代码，类似传统 JavaScript 中的 window.onload 方法，所以我们通常会将代码包装在这个函数中。美元符号是 jQuery 的简写，我们通过它来调用jQuery 提供的多个方法，所以 \$.ajax() 等同于 jQuery.ajax()。
	
	在 \$(function(){...}) 中，\$('#load') 被称为选择器，我们在括号中传入目标元素的 id、class 或是其他属性来定位到对应的元素，将其创建为 jQuery 对象。我们传入了"加载更多"按钮的 id 值以定位到加载按钮。在这个选择器上，我们附加了 .click(function(){...})，这会为加载按钮注册一个单击事件处理函数，当加载按钮被单击时就会执行单击事件回调函数。在这个回调函数中，我们使用 \$.ajax() 方法发送一个 AJAX 请求到服务器，通过 url 将目标 URL 设为 "/more"，通过 type 参数将请求的类型设为 GET。当请求成功处理并返回2XX 响应时（另外还包括 304 响应），会触发 success 回调函数。success 回调函数接收的第一个参数为服务器端返回的响应主体，在这个回调函数中，我们在文章正文（通过 \$('.body')选择）底部使用 append() 方法插入返回的 data 数据。
   
   处理/more的视图函数会返回随机文章正文，如下所示：
   
   ```python
   @app.route('/more')
   def load_post():
       return generate_lorem_ipsum(n=1)
   ```