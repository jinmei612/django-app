# django-app

### create a django project ###

`django-admin startproject <project-name> .`


### run django development server ###

`python3 manage.py runserver`

it starts the server at http://127.0.0.1:8000/ 

`python3 manage.py runserver 8001`

to run server on different port

### create a Django app ###

`python3 manage.py startapp <app-name>`


### register Django app with Django project

in *setting.py* in project, in section `INSTALLED_APPS`, add `<name>.app.<classname>` (from *app.py* in django app)
