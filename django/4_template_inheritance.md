## Template Inheritance

#### Why do we need it?

- Allows us to re-use templates throughout our project
- DRY principle (Don't Repeat Yourself)
  - e.g. Navbar
- We are 'inheriting' the reusable template

#### Creating our template

1. Make a `base.html` file in `templates/first_app` folder

2. Code our boilerplate

- Use Bootstrap (https://getbootstrap.com/docs/4.0/getting-started/introduction/)
- Navbar (https://getbootstrap.com/docs/4.0/components/navbar/)

`templates/first_app/base.html`

```
<head>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
</head>
...
<Navbar Boilerplate>
...

<div class="container">
    {% block body_block %}

    {% endblock %}
</div>

```

3. Apply our `base` template

`templates/first_app/students.html`

```

{% extends 'first_app/base.html' %}

{% block body_block %}

<h1>Add a new Student!</h1>

{% endblock %}
```
