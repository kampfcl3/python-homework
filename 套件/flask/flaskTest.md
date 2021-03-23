# flask
## agenda
```
1.簡介
2.flask專案
3.reference
4.使用 Flask Script
```
## 簡介
```
Flask is a micro web framework written in Python. It is classified as a microframework because
it does not require particular tools or libraries. It has no database abstraction layer, form 
validation, or any other components where pre-existing third-party libraries provide common 
functions. However, Flask supports extensions that can add application features as if they were
implemented in Flask itself. Extensions exist for object-relational mappers, form validation, 
upload handling, various open authentication technologies and several common framework related 
tools.

Applications that use the Flask framework include Pinterest and LinkedIn.
```
```
-flask是一個使用 Python 撰寫的輕量級 Web 應用程式框架 --> micro-framework（微框架）
-flask相較django給予更多彈性，可以選用不同用的 extension 來增加其功能
```
```
django差異:
  較不彈性，但功能完善
  不論在 ORM、表單驗證或是模版引擎都有自己的作法(相對固定)
```
flask 核心:
> [jinja2 模板引擎](https://jinja.palletsprojects.com/en/2.9.x/)  
> [Werkzeug WSGI 工具箱](https://werkzeug.palletsprojects.com/en/1.0.x/)  

## flask專案
> 建立專案資料夾  
```
$ mkdir python-flask-todo-app
$ cd python-flask-todo-app
```
> 建立獨立虛擬環境  
```
$ conda create -n python-flask-todo-app python=3.6
$ source activate python-flask-todo-app
```
> 安裝 Flask 模組
```
$ pip install flask
```
### 設定config設定檔案
> 建立設定檔 config.py 檔案在專案資料夾的根目錄中：  
```
class Config(object):
    pass

class ProdConfig(Config):
    pass

class DevConfig(Config):
    DEBUG = True
```
> 建立一個 main.py 檔案初始化 Flask App 和使用其 API，若是一切正常在終端機執行 python main.py     
> 會在瀏覽器網址列輸入 localhost:5000 後看到 Hello World 了！  
```
from flask import Flask
from config import DevConfig

# 初始化 Flask 類別成為 instance
app = Flask(__name__)
app.config.from_object(DevConfig)

# 路由和處理函式配對
@app.route('/')
def index():
    return 'Hello World!'

# 判斷自己執行非被當做引入的模組，因為 __name__ 這變數若被當做模組引入使用就不會是 __main__
if __name__ == '__main__':
    app.run()
```
## 使用 Flask Script
```
Flask 常用的 extensions
> 以讓我們使用指令列來操作 Flask 程式並在 shell 環境下操作 app context
```
ps: extensions :擴展程式

> 安裝模組  
```
pip install flask-script
```
> 建立 manage.py 於根目錄  
```
from flask_script import Manager, Server
from main import app

# 設定你的 app
manager = Manager(app)
# 設定 python manage.py runserver 為啟動 server 指令
manager.add_command('runserver', Server())

# 設定 python manage.py shell 為啟動互動式指令 shell 的指令 
@manager.shell
def make_shell_context():
    return dict(app=app)

if __name__ == '__main__':
    manager.run()
```
```
$ python manage.py runserver     -->執行測試server
$ python manage.py shell    -->app(能找到被引入的 <Flask 'main'>)
```


## reference
[wiki define](https://en.wikipedia.org/wiki/Flask_(web_framework))  
[Python Web Flask 實戰開發教學 - 簡介與環境建置](https://blog.techbridge.cc/2017/06/03/python-web-flask101-tutorial-introduction-and-environment-setup/)   

