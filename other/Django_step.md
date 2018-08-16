# 安裝 Django

在這一章，我們會開始建立第一個 Django 專案，並瞭解如何使用虛擬環境。

首先，請開啟終端機，確定現在的位置是在家目錄底下：

我們先建立一個名為 `mysite` 的資料夾

```
mkdir mysite
```

並切換至剛剛建立的目錄

```
cd mysite
```

## 虛擬環境（virtualenv）

在安裝 Django 之前，我們要先建立一個虛擬環境（virtual environment）。

我們可以直接開始安裝 Django，但實務上，大多數人都會搭配使用虛擬環境。使用虛擬環境有許多優點：
+ 你的專案會擁有一個專屬的獨立 Python 環境。
+ 不需要 root 權限，就可以安裝新套件。
+ 方便控管不同版本的套件，不用擔心升級套件會影響到其他專案。
+ 如果需要多人協作或在不同機器上跑同一個專案時，使用虛擬環境也可以確保環境一致性。

### 創建虛擬環境

在較舊的 Python 版本中，建立處擬環境需要另外安裝。但 Python 3.3 之後已經加入 venv 模組，可以直接使用。

那我們立刻開始，首先要創建一個虛擬環境資料夾 `mysite_venv`。

#### Windows

如果有按照安裝教學，使用 Django Environment 開啟終端機後，輸入以下指令：

```
C:\Users\YOUR_NAME\mysite> python -m venv mysite_venv
```

#### Linux / OS X

Linux 或 OS X 需要使用 python3 來建立虛擬環境，指令如下：

~/mysite$ python3 -m venv mysite_venv

### 切換虛擬環境

虛擬環境建立完成後，我們可以透過 `activate` 這個 script 來啟動它。

記得未來在安裝新套件，或是要執行 Django 相關指令時，都要先啟動該專案的虛擬環境。

#### Windows

```
C:\Users\YOUR_NAME\mysite> mysite_venv\Scripts\activate
```

#### Linux / OS X

```
~/mysite$ source mysite_venv/bin/activate
```

如果無法使用 source 的話，可以用下列指令替代：

~/mysite$ . mysite_venv/bin/activate

### 目前的虛擬環境

如果看到前面多了 `(虛擬資料夾名稱)`，則表示已經成功切換至該虛擬環境。

#### Windows

```
(mysite_venv) C:\Users\YOUR_NAME\mysite>
```

#### Linux / OS X

```
(mysite_venv) ~/mysite$
```

## 安裝 Django 1.8 最新版本

### 開始安裝

Python 3.4 預先安裝了 `pip` 這個強大的套件管理工具，我們將使用它來安裝 Django：

```
(mysite_venv) ~/mysite$ pip install "django<1.9"
```

這裡需要特別注意，我們使用的指令是 `"django<1.9"`。這樣一來才可以**保我們安裝的是 Django 1.8 的最新版本**

輸入了應該會看到如下的訊息，表示安裝成功

```
Installing collected packages: django
Successfully installed django-1.8.6
```

註：如果你看到以 Fatal error in launcher 開頭的輸出，而不是上面的安裝成功訊息，請改用 python -m pip install "django<1.9" 試試看。之後如果在使用 pip 時遇到類似問題，也可以試著在前面加上 python -m。

### 確認安裝成功

最後，讓我們最後來測試一下。

請在虛擬環境下指令輸入 python，進入**互動式命令列**環境

```
(mysite_venv) ~/mysite$ python
```

輸入以下的指令取得 Django 版本資訊：

```
>>> import django
>>> django.VERSION
(1, 8, 6, 'final, 0')
```

如果看見類似上面的訊息，就代表安裝成功囉！


# Project and apps

每一個 Django project 裡面可以有多個 Django apps，可以想成是類似模組的概念。在實務上，通常會依功能分成不同 app，方便未來的維護和重複使用。

例如，我們要做一個類似 Facebook 這種網站時，依功能可能會有以下 apps：

+ 使用者管理 -- accounts
+ 好友管理 -- friends
+ 塗鴉牆管理 -- timeline
+ 動態消息管理 -- news

若未來我們需要寫個購物網站，而需要會員功能時，accounts app（使用者管理）就可以被重複使用。

這一章，你會學到如何使用 Django 命令列工具建立 Django project 和一個 Django app。

# 建立 Django project

## 建立專案資料夾 -- startproject

首先，使用 `django-admin.py` 來建立第一個 Django project `mysite`:

```
(mysite_venv) ~/mysite$ django-admin.py startproject mysite
```

此時會多了一個 mysite 資料夾。我們切換進去：

```
(mysite_venv) ~/mysite$ cd mysite
```

startproject 這個 Django 指令除了建立專案資料夾，也預設會建立一些常用檔案，你可以使用 `ls` 或 `dir /w` (Windows) 檢視檔案結構。

目前 project 的檔案結構如下: (tree)

```
mysite/
├── manage.py
└── mysite
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```
	
## 瞭解 Django 的 Management commands

`manage.py` 是 Django 提供的命令列工具，我們可以利用它執行很多工作，例如同步資料庫、建立 app 等等，指令的使用方式如下：

```
python manage.py <command> [options]
```

如果你想要了解有什麼指令可以使用，輸入 `help` 或 `-h` 指令會列出所有指令列表:

```
python manage.py -h
```

而如果想了解其中一個指令，可以在指令名字後輸入 -h，你會看到簡單的的指令介紹以及用法說明。以 runserver 為例：

```
(mysite_venv) ~/mysite/mysite$ python manage.py runserver -h
usage: manage.py runserver [-h] [--version] [-v {0,1,2,3}]
                           [--settings SETTINGS] [--pythonpath PYTHONPATH]
                           [--traceback] [--no-color] [--ipv6] [--nothreading]
                           [--noreload] [--nostatic] [--insecure]
                           [addrport]

Starts a lightweight Web server for development and also serves static files.

positional arguments:
  addrport              Optional port number, or ipaddr:port

optional arguments:
  -h, --help            show this help message and exit
  --version             show program's version number and exit
  -v {0,1,2,3}, --verbosity {0,1,2,3}
                        Verbosity level; 0=minimal output, 1=normal output,
                        2=verbose output, 3=very verbose output
  --settings SETTINGS   The Python path to a settings module, e.g.
                        "myproject.settings.main". If this isn't provided, the
                        DJANGO_SETTINGS_MODULE environment variable will be
                        used.
  --pythonpath PYTHONPATH
                        A directory to add to the Python path, e.g.
                        "/home/djangoprojects/myproject".
  --traceback           Raise on CommandError exceptions
  --no-color            Don't colorize the command output.
  --ipv6, -6            Tells Django to use an IPv6 address.
  --nothreading         Tells Django to NOT use threading.
  --noreload            Tells Django to NOT use the auto-reloader.
  --nostatic            Tells Django to NOT automatically serve static files
                        at STATIC_URL.
  --insecure            Allows serving static files even if DEBUG is False.
```

## 啟動開發伺服器 -- runserver

從說明中可以知道，`runserver` 會啟動一個簡單的 web server，方便於在開發階段使用：

```
(mysite_venv) ~/mysite/mysite$ python manage.py runserver
...
Django version 1.8.5, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

現在打開瀏覽器輸入 http://127.0.0.1:8000/ 或是 http://localhost:8000/，會看到你的 django 專案已成功在 web server 上執行

![Django startproject success](https://djangogirlstaipei.gitbooks.io/django-girls-taipei-tutorial/images/django-startproject-success.png)

最後我們可以在終端機按下 CTRL+C ，關閉 web server 回到命令列。

<br>

如果無法看到成功畫面，瀏覽器上顯示錯誤訊息 - A server error occurred. Please contact the administrator.，請輸入：

```
(mysite_venv) ~/mysite/mysite$ python manage.py migrate
```

然後再次 `runserver` 啟動你的 web server，我們會在 Django Models 解釋 migrate 的作用。

<br>

## 建立 Django application（app）

讓我們利用 `startapp` 建立第一個 Django app -- polls:

```
(mysite_venv) ~/mysite/mysite$ python manage.py startapp polls
```

`startapp` 會按照你的命名建立一個同名資料夾和 app 預設的檔案結構如下：

```
polls
├── __init__.py
├── admin.py
├── migrations
├── models.py
├── tests.py
└── views.py
```

## 將新增的 Django app 加入設定檔

在前一個指令，我們透過 Django 命令列工具建立了 polls 這個 app。但若要讓 Django 知道要管理哪些 apps，還需再調整設定檔。

## 新增 app

打開 *mysite/settings.py*，找到 **INSTALLED_APPS**，調整如下：

```
# mysite/settings.py

...

# Application definition

INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'polls',
)
```

請注意 app 之間有時候需要特定先後順序。在此，我們將自訂的 polls 加在最後面。

<br>

#### 預設安裝的 Django app

Django 已將常用的 app 設定為 `INSTALLED_APPS` 。例如，`auth`（使用者認證）、`admin` （管理後台）... 等等，我們可依需求自行增減。

<br>

## 小結

目前為止，我們使用 `startproject` 建立了一個名為 **mysite** 的 Django 專案，和一個名為 **polls** 的 Django app。

最後，我們回顧一下本章學到的指令

指令|說明
:----|:----
django-admin.py startproject <project_name>|建立 Django 專案
python manage.py -h <command_name>|查看 Django commands 的使用方法
python manage.py runserver|啟動開發伺服器
python manage.py startapp <app_name>|新增 Django app

# Views and URLconfs

![Django 處理 HTTP request 產生 response 的流程](https://djangogirlstaipei.gitbooks.io/django-girls-taipei-tutorial/images/url-dispatch.png)


在前面的介紹，我們有提到 Django 的 MTV 架構。其處理 request 的流程如下：

1. 瀏覽器送出 **HTTP request**
2. Django 依據 **URL configuration** 分配至對應的 View
3. View 進行資料庫的操作或其他運算，並回傳 `HttpResponse` 物件
4. 瀏覽器依據 **HTTP response** 顯示網頁畫面

<br>
這一章，我們將透過 **Hello World** 範例 ，瞭解 Django 如何處理一個 request 的流程。
<br>

## Django Views
Django view 其實是一個 function，**處理 `HttpRequest` 物件，並回傳 `HttpResponse` 物件**，大致說明如下：

+ **會收到 `HttpRequest` 參數：** Django 從網頁接收到 request 後，會將 request 中的資訊封裝產生一個 HttpRequest 物件，並當成第一個參數，傳入對應的 view function。
+ **需要回傳 `HttpResponse` 物件：** HttpResponse 物件裡面包含：
	- HttpResponse.content
	- HttpResponse.status_code …等

### 建立第一個 View

首先建立一個名為 `hello_world` 的 view。

在 `polls/views.py` 輸入下列程式碼：

```
# polls/views.py

from django.http import HttpResponse


def hello_world(request):
    return HttpResponse("Hello World!")
```	

以上程式在做的事就是：

1. 從 `django.http` 模組中引用 `HttpResponse` 類別
2. 宣告 `hello_world` 這個 view
3. 當 `hello_world` 被呼叫時，回傳包含字串 **Hello World!** 的 `HttpResponse` 物件。

## Django URL 設定

最後，Django 需要知道 **URL 與 view 的對應關係**。

例如：

有人瀏覽 http://127.0.0.1:8000/hello/ 時 ，`hello_world()` 這個 view function 需要被執行。
而這個對應關係就是 **URL conf** (URL configuration)。

### URL Conf

+ 通常定義在 `urls.py`
+ 是一連串的規則 (URL patterns)
+ Django 收到 request 時，會一一比對 URL conf 中的規則，決定要執行哪個 view function

現在我們來設定 Hello World 範例的 URL conf。

首先打開 `mysite/urls.py`，先 import 剛剛寫的 view function：

```
from polls.views import hello_world
```

然後在 urlpatterns 中加入下面這行：

```
url(r'^hello/$', hello_world),
```

現在 mysite/urls.py 的內容應該會像下面這樣：

```
# mysite/urls.py

from django.conf.urls import include, url
from django.contrib import admin
# Import view functions from polls app.
from polls.views import hello_world

urlpatterns = [
    url(r'^admin/', include(admin.site.urls)),
    url(r'^hello/$', hello_world),
]
```

以上程式透過 url() function 傳入兩個參數 `regex`, `view`：

```
url(regex, view)
```
+ regex -- 定義的 URL 規則
	- 規則以 regular expression（正規表示式）來表達
	- `r'^hello/$'` 代表的是 `hello/` 這種 URL
+ view -- 對應的 view function
	- 指的是 hello_world 這個 view
## 測試 Hello World

現在啟動你的 web server。 (如果剛剛沒關閉的話，通常 Django 會在你修改程式碼後，自動重新啟動 web server)

```
(mysite_venv) ~/mysite/mysite$ python manage.py runserver
```

在瀏覽器輸入 http://127.0.0.1:8000/hello/，你會看到網頁顯示我們在 HttpResponse 傳入的文字`Hello World!`。

![Hello World!](https://djangogirlstaipei.gitbooks.io/django-girls-taipei-tutorial/images/hello-world-plaintext.png)

# Templates

上一章的例子，只是很簡單的顯示一行字串。 現在，讓我們加上一些 HTML/CSS 美化網頁，並動態顯示每次進來這個頁面的時間。

## 第一個 Template

實務上，我們會將前端的程式碼獨立出來，放在 templates 資料夾裡。不僅增加可讀性，也方便與設計師或前端工程師分工。

### Template 資料夾

首先建立 Template 資料夾。開啟終端機 (如果不想關閉 web server，可以再開新一個新的終端機視窗)，並確認目前所在位置為 `mysite/mysite/`。

新增一個名為 `templates` 的資料夾`：

```
(mysite_venv) ~/mysite/mysite$ mkdir templates
```

### 設定 Templates 資料夾的位置

建立好資料夾以後，我們需要修改 `mysite/settings.py` 中的 `TEMPLATES` 設定：

```
# mysite/settings.py

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates').replace('\\', '/')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

我們將 'DIRS' 原本的[]修改成：

```
[os.path.join(BASE_DIR, 'templates').replace('\\', '/')]
```

好讓 Django 找得到剛剛建立的 `templates` 資料夾。


### 建立第一個 Template

新增檔案 `templates/hello_world.html`：

(mysite_venv) ~/mysite/mysite/templates$ > hello_world.html 

```
mysite
├── mysite
├── templates
│   └── hello_world.html
├── polls
└── manage.py
```

並將下列的 HTML 複製到 `hello_world.html`：

```
<!-- hello_world.html -->

<!DOCTYPE html>
<html>
    <head>
        <title>I come from template!!</title>
        <style>
            body {
               background-color: lightyellow;
            }
            em {
                color: LightSeaGreen;
            }
        </style>
    </head>
    <body>
        <h1>Hello World!</h1>
        <em>{{ current_time }}</em>
    </body>
</html>
```

#### 在 Template 中顯示變數

以上 Template 中，有個地方要特別注意：

```
<em>{{ current_time }}</em>
```

在 Template 裡面．我們會使用兩個大括號，來顯示變數`current_time`。

`{{<variable_name>}}` 是在 Django Template 中顯示變數的語法。

其它 Django Template 語法，我們會在後面的章節陸續練習到。

### 使用 render function

最後，將 view function `hello_world` 修改如下：

```
# polls/views.py

from datetime import datetime
from django.shortcuts import render


def hello_world(request):
    return render(request, 'hello_world.html', {
        'current_time': str(datetime.now()),
    })
```

1. **顯示目前時間**： 為了顯示動態內容，我們 import datetime 時間模組，並用`datetime.now()`取得現在的時間。
2. **render**： 我們改成用 `render` 這個 function 產生要回傳的 `HttpResponse` 物件。

這次傳入的參數有：

+ **request** -- `HttpRequest` 物件
+ **template_name** -- 要使用的 template
+ **dictionary** -- 包含要新增至 template 的變數

`render`：產生 HttpResponse 物件。

render(request, template_name, dictionary)

#### 大功告成

現在啟動 web server ，連至 http://127.0.0.1:8000/hello/ 後，會發現網頁不再是純文字。除了加上了一些樣式外，也會顯示當下的時間。

你可以重新整理網頁，試試看時間有沒有改變

![HelloWorld From Template](https://djangogirlstaipei.gitbooks.io/django-girls-taipei-tutorial/images/hello-world-from-template.png)