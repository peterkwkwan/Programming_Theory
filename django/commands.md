## Useful commands

#### creating a virtual environment

`mkdir <name>` - create a new folder

`python3 -m venv <name>` - create a new virtual environment

`source env/bin/activate` - actives virtual environment

`deactivate` - quits virtual environment

#### install django (using pip3)

`pip3 install django` - installs django

#### project and app setup

`django-admin startproject <name_of_project>` - creates a new project

`python3 manage.py startapp <name_of_app>` - creates a new app

`python3 manage.py runserver` - starts server

#### making a model

`python3 manage.py makemigrations` - creates SQL model in migrations folder (step 1)

`python3 manage.py migrate` - confirms the migration (step 2)

#### misc.

`python3 manage.py shell` - activates python shell

`from <app>.models import <Class>` - import class object

`<Class>.objects.get(id=1)` - gets the class object of id = 1

`quit()` - quits python shell

`python3 manage.py createsuperuser` - creates django admin account

#### Django templating language

`{{ variable_here }}` - using the passed variable inside the HTML

`href="{% static 'path_here_.css' %}"` - path to css file in `<Link>` tag

```
{% for athlete in athlete_list %}
    <li>{{ athlete.name }}</li>
{% endfor %}
```

```
{% if CONDITION %}

{% endif%}
```
