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
