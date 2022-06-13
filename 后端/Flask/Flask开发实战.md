# Flask 开发实战

## 配置文件

在 Flask 中，配置不仅可以通过 config 对象直接写入，还可以从文件中读取。在SayHello中，把配置移动到一个单独的文件中，将其命名为 settings.py（也常被命名为 config.py）。当在单独的文件中定义配置时，不再使用 config 对象添加配置，而是直接以键值对的方式写出，和保存环境变量的 .flaskenv 文件非常相似。下面的代码是一个例子。

```python
import os
from sayhello import app
dev_db = 'sqlite:///' + os.path.join(os.path.dirname(app.root_path), 'data.db')
SECRET_KEY = os.getenv('SECRET_KEY', 'secret string')
SQLALCHEMY_TRACK_MODIFICATIONS = False
SQLALCHEMY_DATABASE_URI = os.getenv('DATABASE_URI', dev_db)
```

在创建程序实例后，使用 config 对象的 from_pyfile() 方法即可加载配置，传入配置模块的文件名作为参数：

```python
...
app = Flask(__name__)
app.config.from_pyfile('settings.py')
```

## 创建程序实例

使用包组织程序代码后，创建程序实例、初始化扩展等操作可以在程序包的构造文件（\__init__.py）中实现，如下所示。

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
app = Flask('sayhello')
app.config.from_pyfile('settings.py')
app.jinja_env.trim_blocks = True
app.jinja_env.lstrip_blocks = True
db = SQLAlchemy(app)
from sayhello import views, errors, commands
```

在单脚本中创建程序实例时，我们传入 \__name__ 变量作为 Flask 类构造方法的 import_name 参数值。因为Flask 通过这个值来确认程序路径，当使用包组织代码时，为了确保其他扩展或测试框架获得正确的路径值，我们最好以硬编码的形式写出包名称作为程序名称，即 sayhello。

除了直接写出包名称，你也可以从 \_\_name\_\_ 变量获取包名称，即 app=Flask(\__name__.split('.')[0])。

当我们启动程序时，首先被执行的是包含程序实例的脚本，即构造文件。但注册在程序实例上的各种处理程序均存放在其他脚本中，比如视图函数存放在 views.py 中、错误处理函数则存放在 errors.py 中。如果不被执行，那么这些视图函数和错误处理函数就不会注册到程序上，那么程序也无法正常运行。为了让使用程序实例 app 注册的视图函数，错误处理函数，自定义命令函数等和程序实例关联起来，我们需要在构造文件中导入这些模块。因为这些模块也需要从构造文件中导入程序实例，所以为了避免循环依赖，这些导入语句在构造文件的末尾定义。

从构造文件中导入变量时不需要注明构造文件的路径，只需要从包名称导入，比如导入在构造文件中定义的程序实例 app 可以使用 from sayhello import app。

在前面的章节中说过，Flask 在通过 FLASK_APP 环境变量定义的模块中寻找程序实例。所以在启动程序前，我们需要给 .flaskenv 中的环境变量 FLASK_APP 重新赋值，这里仅写出包名称即可：

```
...
FLASK_APP=sayhello
```

## Web 程序开发流程

在实际的开发中，一个 Web 程序的开发过程要涉及多个角色，比如客户（提出需求）、项目经理（决定需求的实现方式）、开发者（实现需求）等，在这里我们假设是一个人全职开发。一般来说，一个 Web 程序的开发流程如下所示：

1. 分析需求，列出功能清单或写需求说明书。

2. 设计程序功能，写功能规格书和技术规格书。

3. 进入开发与测试的迭代。

4. 调试和性能等专项测试。

5. 部署上线（deployment）。

6. 运行维护与营销等。

写好功能规格书后，我们就可以进行实际的代码编写。在具体的开发中，代码编写主要分为前端页面（front end）和后端程序（back end）。

前端开发的主要流程如下：

1. 根据功能规格书画页面草图（sketching）。

2. 根据草图做交互式原型图（prototyping）。

3. 根据原型图开发前端页面（HTML、CSS、JavaScript）。

后端开发的主要流程如下：

1. 数据库建模。

2. 编写表单类。

3. 编写视图函数和相关的处理函数。

4. 在页面中使用Jinja2替换虚拟数据。

采用这个流程并不是必须的，对于非常简单的程序（比如本章的 SayHello），你可以根据情况来省略某些步骤。如果不是只有简单的几个页面的玩具程序，那么我建议你遵循这个过程进行开发。因为如果没有规划，就会像没头苍蝇一样乱飞乱撞，最终开发出不完善的程序，或是添加了无关紧要的功能。从一开始就遵循开发流程，可以让你很容易适应大型程序的开发。想象一下，在大型程序里常常有着复杂的数据库关系，大量的页面和功能，想到哪写到哪会将大量时间都浪费在无意义的调试和删改中。前期考虑和规划越周全，在实际开发时就可以越高效
和省力。

为了便于组织内容，开发时非常重要的测试，我们移动到本书的第三部分进行介绍，但是在实际开发中应该将测试融入整个开发流程中：每编写一部分代码，立刻编写对应的测试。在第三部分我们还会介绍程序的部署以及部署前的准备（性能优化）。

### 程序功能设计

规划和设计程序功能时，我们通常会使用思维导图工具或是清单工具。

### 前端页面开发

在前面列出的流程中，我们首先使用纸笔画草图，然后使用原型设计软件画出原型图，最后编写对应的HTML页面。根据程序的页面数量和复杂程度，你可以按需调整。因为 SayHello 比较简单，我们直接使用原型工具画出原型图即可。

### 后端程序开发

## 大型项目结构

### 使用蓝本模块化程序

实例化 Flask 提供的 Blueprint 类就创建一个蓝本实例。像程序实例一样，我们可以为蓝本实例注册路由、错误处理函数、上下文处理函数，请求处理函数，甚至是单独的静态文件文件夹和模板文件夹。在使用上，它和程序实例也很相似。比如，蓝本实例同样拥有一个 route() 装饰器，可以用来注册路由，但实际上蓝本对象和程序对象却有很大的不同。

在实例化 Blueprint 类时，除了传入构造函数的第一个参数是蓝本名称之外，创建蓝本实例和使用 Flask 对象创建程序实例的代码基本相同。

例如，下面的代码创建了一个 blog 蓝本：

```python
from flask import Blueprint
blog = Blueprint('blog', __name__)
```

使用蓝本不仅仅是对视图函数分类，而是将程序某一部分的所有操作组织在一起。这个蓝本实例以及一系列注册在蓝本实例上的操作的集合被称为一个蓝本。你可以把蓝本想象成模子，它描述了程序某一部分的细节，定义了相应的路由、错误处理器、上下文处理器、请求处理器等一系列操作。但是它本身却不能发挥作用，因为它只是一个模子。只有当你把它注册到程序上时，它才会把物体相应的部分印刻出来——把蓝本中的操作附加到程序上。

使用蓝本可以将程序模块化（modular）。一个程序可以注册多个蓝本，我们可以把程序按照功能分离成不同的组件，然后使用蓝本来组织这些组件。蓝本不仅仅是在代码层面上的组织程序，还可以在程序层面上定义属性，具体的形式即为蓝本下的所有路由设置不同的 URL 前缀
或子域名。

举一个常见的例子，为了让移动设备拥有更好的体验，我们为移动设备创建了单独的视图函数，这部分视图函数可以使用单独的 mobile 蓝本注册，然后为这个蓝本设置子域名 m。用户访问 m.example.com 的请求会自动被该蓝本的视图函数处理。

1. 创建蓝本

    蓝本一般在子包中创建，比如创建一个 blog 子包，然后在构造文件中创建蓝本实例，使用包管理蓝本允许你设置蓝本独有的静态文件和模板，并在蓝本内对各类函数分模块存储，下一章我们会详细介绍。

    在简单的程序中，我们也可以直接在模块中创建蓝本实例。根据程序的功能，我们分别创建了三个脚本：auth.py（用户认证）、blog.py（博客前台）、admin.py（博客后台），分别存储各自蓝本的代
    码。以 auth.py 为例，蓝本实例 auth_bp 在auth.py 脚本顶端创建：

    ```python
    from flask import Blueprint
    auth_bp = Blueprint('auth', __name__)
    ```

    在蓝本对象的名称后添加一个 _bp 后缀（即 blueprint 的简写）并不是必须的，这里是为了更容易区分蓝本对象，而且可以避免潜在的命名冲突。本书的示例程序都使用这一模式来命名蓝本实例。

    在上面的代码中，我们从 Flask 导入 Blueprint 类，实例化这个类就获得了我们的蓝本对象。构造方法中的第一个参数是蓝本的名称；第二个参数是包或模块的名称，我们可以使用 \__name__ 变量。Blueprint 类的构造函数还接收其他参数来定义蓝本，我们会在后面进行介绍。

2. 装配蓝本

    蓝本实例是一个用于注册路由等操作的临时对象。这一节我们会了解在蓝本上可以注册哪些操作，以及其中的一些细节。

    我们在下面介绍的方法和属性都是在表示蓝本的 Blueprint 类中定义的，因此可以通过我们的蓝本实例调用，在提及这些方法和属性时，我们会省略掉类名称，比如 Blueprint.route() 会写为 route()。

    (1) 视图函数
    蓝本中的视图函数通过蓝本实例提供的 route() 装饰器注册，即 auth_bp.route()。我们把和认证相关的视图函数移动到这个模块，然后注册到 auth 蓝本上，如下所示：

    ```python
    from flask import Blueprint
    auth_bp = Blueprint('auth', __name__)
    
    @auth_bp.route('/login')
    def login():
    ...
    
    @auth_bp.route('/logout')
    def logout():
    ...
    ```

    现在的 auth.py 脚本就像一个完整的单脚本 Flask 程序，这和本书第一部分示例程序的结构非常相似。

    (2) 错误处理函数
    使用蓝本实例的 errorhandler() 装饰器可以把错误处理器注册到蓝本上，这些错误处理器只会捕捉访问该蓝本中的路由发生的错误；使用蓝本实例的 app_errorhandler() 装饰器则可以注册一个全局的错误处理
    器。

    404 和 405 错误仅会被全局的错误处理函数捕捉，如果你想区分蓝本 URL 下的 404 和 405 错误，可以在全局定义的 404 错误处理函数中使用 request.path.startswith（'<蓝本的URL前缀>'）来判断请求的URL 是否属于某个蓝本。下面我们会介绍如何为蓝本设置 URL 前缀。

    (3) 请求处理函数

    在蓝本中，使用 before_request、after_request、teardown_request 等装饰器注册的请求处理函数是蓝本独有的，也就是说，只有该蓝本中的视图函数对应的请求才会触发相应的请求处理函数。另外，在蓝本中也可以使用 before_app_request、after_app_request、teardown_app_request、 before_app_first_request 方法，这些方法注册的请求处理函数是全局的。

    (4) 模板上下文处理函数

    和请求钩子类似，蓝本实例可以使用 context_processor 装饰器注册蓝本特有的模板上下文处理器；使用app_context_processor 装饰器则会注册程序全局的模板上下文处理器。

    另外，蓝本对象也可以使用 app_template_global()、app_template_filter() 和 app_template_test() 装饰器，分别用来注册全局的模板全局函数、模板过滤器和模板测试器。

    并不是所有程序实例提供的方法和属性都可以在蓝本对象上调用，蓝本对象只提供了少量用于注册处理函数的方法，大部分的属性和方法我们仍然需要通过程序实例获取，比如表示配置的 config 属性，或是注册自定义命令的 cli.command() 装饰器。

3. 注册蓝本

    我们在本章开始曾把蓝本比喻成模子，为了让这些模子发挥作用，我们需要把蓝本注册到程序实例上：

    ```python
    from bluelog.blueprints.auth import auth_bp
    ...
    app.register_blueprint(auth_bp)
    ```

    蓝本使用 Flask.register_blueprint() 方法注册，必须传入的参数是我们在上面创建的蓝本对象。其他的参数可以用来控制蓝本的行为。比如，我们使用 url_prefix 参数为 auth 蓝本下的所有视图 URL 附加一个 URL 前缀；

    ```python
    app.register_blueprint(auth_bp, url_prefix='/auth')
    ```

    这时，auth 蓝本下的视图的 URL 前都会添加一个 /auth 前缀，比如 login 视图的 URL 规则会变为 /auth/login。使用 subdomain 参数可以为蓝本下的路由设置子域名。比如，下面蓝本中的所有视图会匹配来自 auth 子域的请求：

    ```python
    app.register_blueprint(auth_bp, subdomain='auth')
    ```

    这时访问类似 auth.example.com/login 的 URL 才会触发 auth 蓝本中的 login 视图。

    register_blueprint() 方法接收的额外参数和 Blueprint 类的构造方法基本相同，在这里传入的参数会覆盖传入蓝本构造方法的参数。

4. 蓝本的路由端点

    端点作为 URL 规则和视图函数的中间媒介，是我们第 1 章介绍 url_for() 函数时提及的概念。下面先来深入了解一下端点，我们使用 app.route() 装饰器将视图函数注册为路由：

    ```python
    @app.route('/hello')
    def say_hello():
        return 'Hello!'
    ```

    如果你没有接触过装饰器，可能会感到很神秘，其实它只是一层包装而已。如果不用 app.route() 装饰器，使用 app.add_url_rule() 方法同样也可以注册路由：

    ```python
    def say_hello():
        return 'Hello!'
    
    app.add_url_rule('/hello', 'say_hello', say_hello)
    ```

    add_url_rule(rule，endpoint，view_func) 的第二个参数即指定的端点（endpoint），第三个参数是视图函数对象。在路由里，URL 规则和视图函数并不是直接映射的，而是通过端点作为中间媒介。类似这
    样：

    ```
    /hello（URL规则） - > say_hello（端点） - > say_hello（视图函数）
    ```

    默认情况下，端点是视图函数的名称，在这里即 say_hello。我们也可以显式地使用 endpoint 参数改变它：

    ```python
    @app.route('/hello', endpoint='give_greeting')
    def say_hello():
        return 'Hello!'
    ```

    这时端点变成了 give_greeting，映射规则也相应改变：

    ```python
    /hello（URL规则） - > give_greeting（端点） - > say_hello（视图函数）
    ```

    现在使用 flask routes 命令查看当前程序注册的所有路由：

    ```
    $ flask routes
    Endpoint Methods Rule
    
    ------------------ --------- ---------------------------------
    
    auth.login GET, POST /auth/login
    auth.logout GET /auth/logout
    blog.about GET /about
    blog.category GET /category/<int:category_id>
    ...
    ```

    从上面的输出可以看到，每个路由的 URL 规则（Rule）对应的端点（Endpoint）值不再仅仅是视图函数名，而是"蓝本名.视图函数名"的形式（这里的蓝本名即我们实例化 Blueprint 类时传入的第一个参数）。前面我们留下了一个疑问：为什么不直接映射URL规则到视图函数呢？现在是揭晓答案的时候了。答案就是使用端点可以实现蓝本的视图函数命名空间。

    当使用蓝本时，你可能会在不同的蓝本中创建同名的视图函数。比如，在两个蓝本中都有一个 index 视图，这时在模板中使用 url_for() 获取 URL 时，因为填入的端点参数值是视图函数的名称，就会产生冲突。
    Flask 在端点前添加蓝本的名称，扩展了端点的命名空间，解决了视图函数重名的问题。正因为这样，一旦使用蓝本，我们就要对程序中所有 url_for() 函数中的端点值进行修改，添加蓝本名来明确端点的归属。
    比如，在生成 auth 蓝本下的 login 视图的 URL 时，需要使用下面的端点：

    ```python
    url_for('auth.login')
    ```

    端点也有一种简写的方式，在蓝本内部可以使用".视图函数名"的形式来省略蓝本名称，如"auth.login"可以简写为".login"。但是在全局环境中，比如在多个蓝本中都要使用的基模板，或是在A蓝本中的脚本或
    渲染的模板中需要生成 B 蓝本的 URL，这时的端点值则必须使用完整的名称。

    使用蓝本可以避免端点值的重复冲突，但是路由的 URL 规则还是会产生重复。比如，两个蓝本中的主页视图的 URL 规则都是 '/home'，当在浏览器中访问这个地址时，请求只会分配到第一个被注册的蓝本中的主
    页视图。为了避免这种情况，可以在注册蓝本时使用关键字参数 url_prefix 在蓝本的 URL 规则前添加一个 URL 前缀来解决。
    
    一个蓝本可以注册多次。有时你需要让程序在不同的 URL 规则下都可以访问，这时就可以为同一个蓝本注册多次，每次设置对应的 URL 前缀或子域名。
    
5. 蓝本资源

    如果程序的不同蓝本的页面需要截然不同的样式，可以为蓝本定义独有的静态文件和模板。这时我们需要把蓝本模块升级为包，在构造文件中创建蓝本实例，并在蓝本包中创建静态文件文件夹 static 和模板文件夹templates。和程序实例一样，实例化时传入的 \__name__ 变量会被用来判断蓝本的根目录，并以此作为基础寻找模板文件夹和静态文件文件夹。

    要使用蓝本独有的静态文件，你需要在定义蓝本时使用 static_folder 关键字指定蓝本的静态文件文件夹的路径：

    ```python
    auth_bp = Blueprint('auth', __name__, static_folder='static', static_url_path= '/auth/static')
    ```

    这个参数的值可以是绝对路径或相对于蓝本所在文件夹的相对路径。另外，因为蓝本内置的 static 路由的URL 规则和程序的 static 路由的 URL 规则相同，都是"/static"，为了避免冲突，我们使用可选的
    static_url_path 参数为蓝本下的 static 指定了新的 URL 规则。
    
    如果你在注册蓝本时为蓝本定义了 URL 前缀，即设置了 url_prefix 参数，那么最终的蓝本静态文件路径会自动设为"/蓝本前缀/static"，这时可以省略 static_url_path 的定义。
    
    在生成用来获取蓝本静态文件的 URL 时需要写出包含蓝本名称的完整端点，即"蓝本名.static"，下面的调用会返回 "admin/static/style.css"：
    
    ```python
    url_for('admin.static', filename='style.css')
    ```
    
    当蓝本包含独有的模板文件夹时，我们可以在实例化蓝本类时使用 template_folder 关键字指定模板文件夹的位置：
    
    ```python
    admin = Blueprint('admin', __name__, template_folder='templates')
    ```
    
    当我们在蓝本中的视图函数渲染一个 index.html 模板时，Flask 会优先从全局的模板文件夹中寻找，如果没有找到，再到蓝本所在的模板文件夹查找。因此，为了避免蓝本的模板文件夹中和全局模板文件夹中存在同名文件导致冲突，通常会在蓝本的模板文件夹中以蓝本名称新建一个子文件夹存储模板。
    
    如果蓝本之间的关联比较大，共用同一个基模板，更常见的方法是只在全局的模板文件夹中存储模板，在其中可以建立子文件夹来进行组织；静态文件的处理方式亦同。这也是 Bluelog 程序的资源文件组织方式。

### 使用类组织配置

在实际需求中，我们往往需要不同的配置组合。例如，开发用的配置，测试用的配置，生产环境用的配置。为了能方便地在这些配置中切换，你可以像本章开始介绍的那样把配置文件升级为包，然后为这些使用场景分别创建不同的配置文件，但是最方便的做法是在单个配置文件中使用 Python 类来组织多个不同类别的配置。

如下代码是 Bluelog 的配置文件，现在它包含一个基本配置类（BaseConfig），还有其他特定的配置类，即测试配置类（TestingConfig）、开发配置类（DevelopmentConfig）和生产配置类（ProductionConfig），这些特定配置类都继承自基本配置类。

```python
import os
basedir = os.path.abspath(os.path.dirname(os.path.dirname(__file__)))
class BaseConfig(object):
    SECRET_KEY = os.getenv('SECRET_KEY', 'secret string')
    SQLALCHEMY_TRACK_MODIFICATIONS = False
    MAIL_SERVER = os.getenv('MAIL_SERVER')
    MAIL_PORT = 465
    MAIL_USE_SSL = True
    MAIL_USERNAME = os.getenv('MAIL_USERNAME')
    MAIL_PASSWORD = os.getenv('MAIL_PASSWORD')
    MAIL_DEFAULT_SENDER = ('Bluelog Admin', MAIL_USERNAME)
    BLUELOG_EMAIL = os.getenv('BLUELOG_EMAIL')
    BLUELOG_POST_PER_PAGE = 10
    BLUELOG_MANAGE_POST_PER_PAGE = 15
    BLUELOG_COMMENT_PER_PAGE = 15
class DevelopmentConfig(BaseConfig):
	SQLALCHEMY_DATABASE_URI = 'sqlite:///' + os.path.join(basedir, 'data-dev.db')
class TestingConfig(BaseConfig):
	TESTING = True
	WTF_CSRF_ENABLED = False
	SQLALCHEMY_DATABASE_URI = 'sqlite:///:memory:' # in-memory database
class ProductionConfig(BaseConfig):
     SQLALCHEMY_DATABASE_URI = os.getenv('DATABASE_URL', 'sqlite:///' + os.path.join(basedir, config = {
    'development': DevelopmentConfig,
    'testing': TestingConfig,
    'production': ProductionConfig
}
```

在新版本的配置中，我们为不同的使用场景设置了不同的数据库 URL，避免互相干扰。生产环境下优先从环境变量 DATABASE_URL 读取，如果没有获取到则使用SQLite，文件名为 data.db（在实际生产中我们通常会使用更健壮的DBMS，这里只是示例），在开发时用的数据库文件名为 data-dev.db，而测试时的配置则使用 SQLite 内存型数据库。为了获取数据库文件的路径，我们使用os模块的方法创建了一个定位到项目根目录的 basedir 变量，最终的绝对路径通过os.path 模块的方法基于当前脚本的特殊变量 \__file__ 获取。

在配置文件的底部，我们创建了一个存储配置名称和对应配置类的字典，用于在创建程序实例时通过配置名称来获取对应的配置类。现在我们在创建程序实例后使用 app.config.from_object() 方法加载配置，传入配置类：

```python
from bluelog.settings import config
app = Flask('bluelog')
config_name = os.getenv('FLASK_CONFIG', 'development')
app.config.from_object(config[config_name])
```

我们首先从配置文件中导入匹配配置名到配置类的 config 字典。为了方便修改配置类型，配置名称会先从环境变量 FLASK_CONFIG 中导入，从环境变量加载配置可以方便地在不改动代码的情况下切换配置。这个值可以在.flaskenv文件中设置，如果没有获取到，则使用默认值 development，对应的配置类即DevelopmentConfig。

Flask 并不限制你存储和加载配置的方式，可以使用 JSON 文件存储配置，然后使用 app.config.from_json() 方法导入；也可以使用 INI 风格的配置文件，然后自己手动导入。
在本书后面的示例程序中，我们都将使用Python类来组织配置。包含敏感信息的配置会从环境变量获取，这些配置值存储在 .env 文件中。当安装了 python-dotenv 并使用 Flask 内置的 run 命令启动程序时，.env 文件的环境变量会被自动设置。

### 使用工厂函数创建程序实例

使用蓝本还有一个重要的好处，那就是允许使用工厂函数来创建程序实例。在 OOP（Object-Oriented Programming，面向对象编程）中，工厂（factory）是指创建其他对象的对象，通常是一个返回其他类的对象的函数或方法，比如我们在第 4 章创建的自定义WTForms 验证器（函数）。在 Bluelog 程序的新版本中，程序实例在工厂函数中创建，这个函数返回程序实例 app。按照惯例，这个函数被命名为 create_app() 或 make_app()。我们把这个工厂函数称为程序工厂（Application Factory）——即"生产程序的工厂"，使用它可以在任何地方创建程序实例。

工厂函数使得测试和部署更加方便。我们不必将加载的配置写死在某处，而是直接在不同的地方按照需要的配置创建程序实例。通过支持创建多个程序实例，工厂函数提供了很大的灵活性。另外，借助工厂函数，我们还可以分离扩展的初始化操作。创建扩展对象的操作可以分离到单独的模块，这样可以有效减少循环依赖的发生。Bluelog 程序的工厂函数如下所示。

```python
from flask import Flask
from bluelog.settings import config

def create_app(config_name=None):
	if config_name is None:
		config_name = os.getenv('FLASK_CONFIG', 'development')
    app = Flask('bluelog')
    app.config.from_object(config[config_name])
    app.register_blueprint(blog)
    app.register_blueprint(admin, url_prefix='/admin')
    app.register_blueprint(auth, url_prefix='/auth')
    return app
```

工厂函数接收配置名作为参数，返回创建好的程序实例。如果没有传入配置名，我们会从 FLASK_CONFIG 环境变量获取，如果没有获取到则使用默认值 development。

在这个工厂函数中，我们会创建程序实例，然后为其加载配置，注册我们在前面创建的三个蓝本，最后返回程序实例。不过，现在的程序实例还没有执行扩展的初始化操作，我们会在下面一步步扩充它。

工厂函数一般在程序包的构造文件中创建，如果你愿意，也可以在程序包内新创建的模块来存放，比如factory.py 或是 app.py。

1. 加载配置

   工厂函数接收配置名称作为参数，这允许我们在程序的不同位置传入不同的配置来创建程序实例。比如，使用工厂函数后，我们可以在测试脚本中使用测试配置来调用工厂函数，创建一个单独用于测试的程序实例，而不用从某个模块导入程序实例。
   
 2. 初始化扩展

    为了完成扩展的初始化操作，我们需要在实例化扩展类时传入程序实例。但使用工厂函数时，并没有一个创建好的程序实例可以导入。如果我们把实例化操作放到工厂函数中，那么我们就没有一个全局的扩展
    对象可以使用，比如表示数据库的 db 对象。

    为了解决这个问题，大部分扩展都提供了一个 init_app() 方法来支持分离扩展的实例化和初始化操作。现在我们仍然像往常一样初始化扩展类，但是并不传入程序实例。这时扩展类实例化的工作可以集中放到 extensions.py 脚本中，如下所示。

    ```python
    from flask_bootstrap import Bootstrap
    from flask_sqlalchemy import SQLAlchemy
    from flask_mail import Mail
    from flask_ckeditor import CKEditor
    from flask_moment import Moment
    
    bootstrap = Bootstrap()
    db = SQLAlchemy()
    moment = Moment()
    ckeditor = CKEditor()
    mail = Mail()
    ```

    现在，当我们需要在程序中使用扩展对象时，直接从这个 extensions 模块导入即可。在工厂函数中，我们导入所有扩展对象，并对其调用 init_app() 方法，传入程序实例完成初始化操作：

    ```
    from bluelog.extensions import bootstrap, db, moment, ckeditor, mail
    def create_app(config_name=None):
        app = Flask('bluelog')
        ...
        bootstrap.init_app(app)
        db.init_app(app)
        moment.init_app(app)
        ckeditor.init_app(app)
        mail.init_app(app)
        ...
        return app
    ```

3. 组织工厂函数

   除了扩展初始化操作，还有很多处理函数要注册到程序上，比如错误处理函数、上下文处理函数等。虽然蓝本也可以注册全局的处理函数，但是为了便于管理，除了蓝本特定的处理函数，这些处理函数一般都放到工厂函数中注册。

   为了避免把工厂函数弄得太长太复杂，我们可以根据类别把这些代码分离成多个函数，这些函数接收程序实例app 作为参数，分别用来为程序实例初始化扩展、注册蓝本、注册错误处理函数、注册上下文处理函数等一系列操作，如下所示。
   
   ```python
   def create_app(config_name=None):
   	if config_name is None:
   		config_name = os.getenv('FLASK_CONFIG', 'development')
       app = Flask('bluelog')
       app.config.from_object(config[config_name])
       register_logging(app) # 注册日志处理器
       register_extensions(app) # 注册扩展（扩展初始化）
       register_blueprints(app) # 注册蓝本
       register_commands(app) # 注册自定义shell命令
       register_errors(app) # 注册错误处理函数
       register_shell_context(app) # 注册shell上下文处理函数
       register_template_context(app) # 注册模板上下文处理函数
       return app
   
   def register_logging(app):
   	pass # 第14章会详细介绍日志
   
   def register_extensions(app):
   	bootstrap.init_app(app)
   	db.init_app(app)
   	ckeditor.init_app(app)
   	mail.init_app(app)
   	moment.init_app(app)
   
   def register_blueprints(app):
   	app.register_blueprint(blog)
   	app.register_blueprint(admin, url_prefix='/admin')
   	app.register_blueprint(auth, url_prefix='/auth')
   
   def register_shell_context(app):
       @app.shell_context_processor
       def make_shell_context():
       return dict(db=db)
   
   def register_template_context(app):
   	pass
   
   def register_errors(app):
   	@app.errorhandler(400)
       def bad_request(e):
       	return render_template('errors/400.html'), 400
       ...
   
   def register_commands(app):
   	...
   ```
   
   这里的 register\_* 函数的命名只是约定，你也可以使用 configure_* 或类似的命名形式。另外，你可以按需要添加或删除对应的函数。现在，当工厂函数被调用后。首先创建一个特定配置类的程序实例，然后执行一系列注册函数为程序实例注册扩展、蓝本、错误处理器、上下文处理器、请求处理器……在这个程序工厂的加工流水线的尽头，我们可以得到一个包含所有基本组件的可以直接运行的程序实例。
   
   在使用工厂函数时，因为扩展初始化操作分离，db.create_all() 将依赖于程序上下文才能正常执行。执行flask shell 命令启动的 Python Shell 会自动激活程序上下文，Flask 命令也会默认在程序上下文环境下执行，所以目前程序中的 db.create_all() 方法可以被正确执行。当在其脚本中直接调用 db.create_all()，或是在普通的 Python Shell 中调用时，则需要手动激活程序上下文，具体可参考第 2章内容，我们会在第 12 章详细介绍。
   
4. 启动程序

   当使用 flask run 命令启动程序时，Flask 的自动发现程序实例机制还包含另一种行为：Flask 会自动从环境变量 FLASK_APP 的值定义的模块中寻找名为 create_app() 或 make_app() 的工厂函数，自动调用工厂函数创建程序实例并运行。因为我们已经在 .flaskenv 文件中将 FLASK_APP 设为 bluelog ，所以不需要更改任何设置，继续使用 flask run 命令即可运行程序。

   如果你想设置特定的配置名称，最简单的方式是通过环境变量 FLASK_CONFIG 设置。另外，你也可以使用FLASK_APP 显式地指定工厂函数并传入参数：

   ```python
   FLASK_APP="bluelog:create_app('development')"
   ```

   为了支持 Flask 自动从 FLASK_APP 环境变量对应值指向的模块或包中发现工厂函数，工厂函数中接收的参数必须是默认参数，即设置了默认值的参数，比如 "config_name=None"。

5. current_app

   使用工厂函数后，我们会遇到一个问题：对于蓝本实例没有提供，程序实例独有的属性和方法应该如何调用呢（比如获取配置的 app.config 属性）？考虑下面的因素：

   - 使用工厂函数创建程序实例后，在其他模块中并没有一个创建好的程序实例可以让我们导入使用。
   - 使用工厂函数后，程序实例可以在任何地方被创建。你不能固定导入某一个程序实例，因为不同程序实例可能加载不同的配置变量。

   解决方法是使用 current_app 对象，它是一个表示当前程序实例的代理对象。当某个程序实例被创建并运行时，它会自动指向当前运行的程序实例，并把所有操作都转发到当前的程序实例。比如，当我们需要获
   取配置值时，会使用 current_app.config，其他方法和属性亦同。
   
   current_app 是程序上下文全局变量，所以只有在激活了程序上下文之后才可以使用。比如在视图函数中，或是在视图函数中调用的函数和对象中，具体可参考第 2 章的相关内容。