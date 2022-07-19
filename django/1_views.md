## Views

Web Basics

- Client and Server
- Request & Response

In Django, whenever we have a REQUEST, we need to handle it and send back a RESPONSE

- this is handled by the VIEWS

1. Create the view (views.py)
2. Map app to project URL (urls.py)
3. Tie app to project (settings.py)

#### Creating our first VIEW

1. `appFolder/views.py`

```
def index(request):
    return HttpResponse("This is the homepage!")
```

2. `projectFolder/urls.py`

> Show admin path

```
...
from first_app import views

urlpatterns = [
    ...
    path('', views.index, name='index')
]
```

3. `projectFolder/settings.py`

```
INSTALLED_APPS =[
    ...
    'first_app'
]
```

> Show index page

#### INCLUDES in url

1. Create new `urls.py` file in `first_app`

```
from django.urls import path
from . import views

urlpatterns = [
    path('index/', views.index, name='index')
]
```

2. `include` keyword in first_project urls.py

```
from django.urls import path, include
...

urlpatterns = [
    ...
    path('first_app', include('first_app.urls')
]
```
