---
tags:
  - library-explanation
---

`path from django.urls`  ^66bfb9
> Offers a function called `path()` that gives back an URLPattern which allows us to make paths to functions with optional parameter value providing. (`"hello/<name>"`)

`include, path from django.urls`
> It allows us to include paths from other files.
``` Python
# hello/urls.py
from django.urls import path
from hello import views

urlpatterns = [
    path("", views.home, name="home"),
    path("hello/<name>", views.hello_there, name="hello_there")
]

# web_project/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("", include("hello.urls")), # hello/urls.py
    path('admin/', admin.site.urls)
]
```

`datetime from django.utils.timezone`
 >Let's us use current time. We can select year, month, day, hour, minute, etc.

`HttpResponse from django.http`
 >Workbone of getting data from back-end to front-end. 
``` Python
def home(request):
	# this below will provide the browser a text in the <body>
	# this shouldn't be used for building the front-end it self, because it allows vulnerability for attackers to run malicious JavaScript code
	return HttpResponse("Hello, Django!")
```

`render from django.shortcuts`
> `render()` can be used to make the browser render an html file with parameters marked with `{{parameter}}`
``` Python
def hello_there(request, name):
    print(request.build_absolute_uri()) #optional
    return render(
        request,
        'hello/hello_there.html',
        {
            'name': name,
            'date': datetime.now()
        }
    )
```
