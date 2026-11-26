---
tags:
  - file-explanation
aliases:
  - views
---

Views are like containers for data transfer to the front-end.
Function are defined with an HttpResponse return value and they always expect a "request" parameter. 

``` Python
import re
from django.utils.timezone import datetime
from django.http import HttpResponse
from django.shortcuts import render

def home(request):
    return HttpResponse("Hello, Django!")

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