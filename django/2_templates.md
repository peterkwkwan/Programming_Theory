## Templates

Allows us to build HTML templates and render WHAT to show to the user once the request is handled and sent back as response from our VIEWS

#### Create a template

1. Create a templates folder inside our project folder

> Can use terminal `mkdir templates`

2. Create another folder <app_name> inside templates folder

   - Allows us to neatly organize our project templates once our app scales in size

3. Create <HTML> file

> Can use `html:5` shortcut

4. Link HTML Template to `views.py` in our app

`first_app/views.py`

```
...
import django.shortcuts import render

def help(request):
    return render(request, 'first_app/help.html')

```

5. Update our `urls.py`

`first_app/urls.py`

```
urlpatterns = [
    ...
    path('help/', views.help, name='help')
]
```

6. Update our `settings.py` in our project folder

`first_project/settings.py`

```
import os

...
TEMPLATE_DIR = os.path.join(BASE_DIR, 'templates')

...
TEMPLATES = [
    {
        ...
        'DIRS': [TEMPLATE_DIR],
        ...
    }
]

```
