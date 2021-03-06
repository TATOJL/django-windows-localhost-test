# **django(windows本地端測試)**


- ## [下載django](#1)
- ## [查看django版本](#2)
- ## [創建django專案](#3)
- ## [測試django](#4)
- ## [新增django app](#5)
- ## [新增模板與靜態文件](#6)
- ## [django連到mysql資料庫](#7)
- ## [django內建後台](#8)
---

<h1 id="1">
 下載django
</h1>
 

- ### Anaconda虛擬環境下載:
```shell

conda install -c anaconda django

```

- ### pip下載:
```shell

py -m pip install Django

```
---
<h1 id="2">
 查看django版本
</h1>


### 在終端機輸入:
```shell 

python -m django --version 

```
---
<h1 id="3">
 創建django專案
</h1>


### 在終端機輸入:
```shell

django-admin startproject project

```

 ![projecct](images/project.png)

---
<h1 id="4">
 測試django
</h1>


- ### cd到專案的資料夾中，然後在終端機輸入:
```shell

python manage.py runserver

```

- ### 瀏覽器輸入127.0.0.1:8000在本機測試django:  
![django](images/django.png)


- ### 在專案中新增views.py，並在此輸入以下程式碼:
```py

from django.http import HttpResponse

def hello(request):
    return HttpResponse("hello world")

```
![views](/images/views.png)


- ### 在url.py中新增以下程式碼:  
```py
 
from django.urls import re_path as url
from . import views

```
```py
 
url(r'^$',views.hello)

```
![url.py](/images/urls.py.png)


- ### 瀏覽器輸入127.0.0.1:8000在本機測試頁面:  
![hellowworld](/images/helloworld.png)

---
<h1 id="5">
 新增django app
</h1>



- ### cd到專案的資料夾中，然後在終端機輸入:
```shell

python manage.py startapp app

```
 ![app](images/app.png)


- ### 把app加到設定檔(settings.py)裡:  
![settings](images/app-settings.png)


- ### 在app資料夾裡的views.py中加入以下程式碼:
```py

from django.http import HttpResponse

def index(request):
      return HttpResponse("hello app")

```
![settings](images/app-views.png)


- ### 最後在url.py加入以下程式碼:    
```py

from app.views import index

```
```py

url(r'^app/',index)

```
![settings](images/app-url.png)


- ### 瀏覽器輸入127.0.0.1:8000/app在本機測試頁面:  
![test](images/app-test.png)

---
<h1 id="6">
 新增模板與靜態文件
</h1>



- ### 在專案資料夾中，新增以下文件(html檔放templates 其他靜態資料放statics):  
![app-statics](images/statics.png)


- ### 到設定檔(settings)裡新增以下程式碼:  
```py

import os

```
```py

'DIRS': [os.path.join(BASE_DIR,"templates")],

```
```py

STATICFILES_DIRS = [
    os.path.join(BASE_DIR,"statics")
]

```
![app-statics](images/import-os.png)

![app-statics](images/templates-settings.png)

![app-statics](images/statics-settings.png)



- ### 到templates資料夾新增index.html，找一張圖片(放在statics/images資料夾裡)，並輸入以下程式碼用以測試靜態資料:  
```html

<!DOCTYPE html>
<html lang="en">
<head>
    {% load static %}
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{content}}</title>
    <link rel="shortcut icon" href="{% static 'images/logo.png' %}">
</head>
<body>
<h1>{{content}}</h1>
<img src="{% static 'images/logo.png' %}" alt="">
</html>

```
![app-statics](images/index.html.png)


- ### 到專案資料夾的views.py裡把裡面程式碼改寫成:  
```py

from django.shortcuts import render


def hello(request):
    return render(request, 'index.html', {
        'content': "Hello Django ",
    })

```
![app-statics](images/templates-views.png)


- ### 瀏覽器輸入127.0.0.1:8000在本機測試頁面:  
![app-statics](images/HelloDjango.png)

---
<h1 id="7">
 django連到mysql資料庫
</h1>


- ### 下載mysql客戶端:  

```shell

pip install mysqlclient

```
- ### 到settings.py的資料庫設定中，把預設的sqlite3改成mysql:


```py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql', 
        'NAME': 'databaseName',
        'USER': 'databaseUser',
        'PASSWORD': 'databasePassword',
        'HOST': 'localhost',
        'PORT': 'portNumber',
    }
}

```
- ### 建立model:


---
<h1 id="8">
 django內建後台
</h1>

- ### admin site:

```shell



```