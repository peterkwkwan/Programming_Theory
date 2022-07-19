## Models

#### Building Dynamic Templates

Allows us to leverage dynamic data and use logic to render unique templates for each user

1. Create a VARIABLE in HTML using `Templating Language`

- templating language = gives super powers to the HTML file
  - e.g. variables, logic, etc.
- built-in to Django (set of tools in the framework)

`templates/first_app/help.html`

```
<h2>{{ Information }}</h2>
```

2. Creating the VARIABLE in our `views.py`

`views.py`

```
def help(request):
    information = {
        'information': 'IF YOU SEE THIS, THE VARIABLE WORKS!'
        'second_information': 'IF YOU SEE THIS, THE SECOND VARIABLE WORKS!!!'
    }
    return render(request, 'first_app/help.html', context=information)
```

#### Tags vs Variables

1. `{{ variable_name }}

- allows us to use variables in HTML

2. {% logic_here %}

- allows us to use logic within HTML

#### Using Tags

1. Using `static`

`templates/first_app/help.html`

```
<DOCTYPE html>
{% load static %}

...

<img src="{% static 'images/django_unchained.jpeg' %}" alt="if you see this, this doesn't work!">

```

2. Create `static` folder and put in an image

- From project folder

* `mkdir static`
* `mkdir images`

3. Tell Django where to find `static` folder

`first_project/settings.py`

```
import os

...
STATIC_DIR = os.path.join(BASE_DIR, 'static')

...

STATIC_URL = '/static/'
STATICFILES_DIR = [
    STATIC_DIR
]

```

#### Importing our CSS files

1. Create `css` folder within `static`

- From `static` folder

* `mkdir css`

2. Linking our HTML

`templates/first_app/help.html`

```
<head>
    <link rel='stylesheet' href="{% static 'css/style.css' %}">
</head>

...
```

3. Create our css file

`static/css/style.css`

```
h2 {
    color: red;
}
```

## OOP
