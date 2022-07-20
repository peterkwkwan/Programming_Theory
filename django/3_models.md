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

1. `{{ variable_name }}`

- allows us to use variables in HTML

2. `{% logic_here %}`

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

- Classes are like blueprints for objects
- Objects have characteristics and behaviors

```
class dog:

    def __init__(self, name, color): // constructor
        self.type = 'animal' // instance variables
        self.name = name
        self.color = color

    def sound(self): // instance method
        print("woof woof!")

...

dogs = Dog('Fido', 'brown') // instantiating an object

```

## Database

- allows us to store data and persist/save it
- data input, organization and retrieval
- traditional databases use tables to store, sort and filter the data

#### SQL

- Structured Query Language
- Language used by databases for performing CRUD operations
  - Create, Read, Update, Destroy

Consists of a table - thinkg MS Excel

- requires a data type when creating a table
  - we use SCHEMAs to structure our tables and relationships
- 3 main data types

  1. String (e.g. CharField)
  2. Number (e.g. IntegerField)
  3. Date/Time (e.g. DateField)

- PRIMARY KEY (PK)
  - unique identifier for each row
- FOREIGN KEY (FK)
  - shows how our current table rows relates to another table's PKs
  - FKs creates the relationship between tables

## Models in Django

- Django allows us to create databases with extreme convenience thanks to its built-in functionality
  - no need to create primary keys
- Models are the source of our data
- Contains values and behaviors about our data
- Each model maps to a single table

#### Creating a Model

1. Creating our own Model

`first_app/models.py`

```
from django.db import models

class Student(models.Model): // importing models which is part of the convenience package from Django
    name = models.CharField(max_length=256)
    age = models.IntegerField()

    def __str__(self):
        return self.name

class Class (models.Model):
    student = models.ForeignKey(Student, on_delete=models.CASCADE)
    subject = models.CharField(max_length=256)
    start_date = models.DateField()

    def __str__(self):
        return self.subject
```

2. Confirm our change and notify Django (migration)

> `python3 manage.py makemigrations`

- creates SQL model in migrations folder (step 1)

> `python3 manage.py migrate`

- double confirm the migration (step 2)

* Can show the migrations folder to see the changes

3. Test our Model is working

- We will need to work with the Python shell
  - shell is the outermost layer of the operating system, which allows us to communicate with our OS
  - Our MacOS or Windows OS has a default shell
    - e.g. Windows = cmd.exe
    - e.g. MacOS = terminal
- We will need to put on the Python shell to test our model in Django database

1. Activate Python shell

- We always need to type `python3` before we run any command

`first_project` folder

> `python3 manage.py shell`

2. Test if Python shell works

```
name = "Peter"

print(name) // "Peter"
```

3. Import our class in our model using relative import

> `from first_app.models import Student`

4. We can use Python queries to test if import worked

> `print(Student.objects.all()) // <QuerySet []>`

5. Create a Student, save it, then test it

```
student1 = Student(name="Peter", age="30")
student1.save()

print(Student.objects.all()) // <QuerySet [<Student: Peter Kwan>]>
```

6. Quit Python shell

> `quit()`

#### Using Admin to create data
