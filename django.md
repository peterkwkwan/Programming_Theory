## Useful commands

`python3 -m venv <path>` - create a new virtual environment
`source env/bin/activate` - actives virtual environment
`deactivate` - quits virtual environment

`pip3 install django` - installs django

`django-admin startproject <name_of_project>` - creates a new project
`python3 manage.py startapp <name_of_app>` - creates a new app

`python3 manage.py runserver` - starts server

`python3 manage.py makemigrations` - creates SQL model in migrations folder (step 1)
`python3 manage.py migrate` - confirms the migration (step 2)

`python3 manage.py shell` - activates python shell
`quit()` - quits python shell

`python3 manage.py createsuperuser` - creates django admin account
