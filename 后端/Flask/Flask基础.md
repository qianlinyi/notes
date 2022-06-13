创建环境变量存储文件.flaskenv和.env

.flaskenv存储和Flask相关的公共环境变量, 例如FLASK_APP
.env用来存储包含敏感信息的环境变量, 比如用户名和密码
环境变量使用键值对的形式定义, 例如: FLASK_APP=hello.py
使用git提交项目时, 可以把.env文件放入.gitignore文件夹中, git会忽略这个文件夹
————————————————
版权声明：本文为CSDN博主「程序烂人」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/lingyingdon/article/details/108073302

当使用flask run或者其他命令时, python-dotenv会自动从.flaskenv文件和.env文件中加载环境变量

管理环境变量
Flask的自动发现程序实例机制还有第三条规则：如果安装了
python-dotenv，那么在使用flask run或其他命令时会使用它自动
从.flaskenv文件和.env文件中加载环境变量。