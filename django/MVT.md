## Models, Views, Templates

Web Basics

- Client and Server
- Request & Response

In Django, whenever we have a REQUEST, we need to handle it and send back a RESPONSE

- this is handled by the VIEWS

1. Create the view (views.py)
2. Map app to project URL (urls.py)
3. Tie app to project (settings.py)

4. `appFolder/views.py`

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

> show index page
