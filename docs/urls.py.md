---
tags:
  - file-explanation
aliases:
  - urls
---

Here we make url patterns, that contain [[docs/views.py.md|views]].
``` Python
# hello/urls.py
from django.urls import path
from hello import views
from django.shortcuts import render

urlpatterns = [
    path("", views.home, name="home"),
    # hello/<name> is added to the URL of the site
    # <name> is a parameter, so like : http://localhost:8000/hello/Milan
    path("hello/<name>", views.hello_there, name="hello_there")
]
```

In the code above, url patterns are mentioned, which are included in the main urls.py file that Django checks.
``` Python
# web_project/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("", include("hello.urls")),
    path('admin/', admin.site.urls)
]
```
