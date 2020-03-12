
# Personal notes for Udemy course: **Create a web application with python + Django + PostgreSQL** #



### create a django project ###

`django-admin startproject <project-name> .`


### run django development server ###

`python3 manage.py runserver` - it starts the server at http://127.0.0.1:8000/ 

`python3 manage.py runserver 8001` - to run server on different port

### create a Django app ###

`python3 manage.py startapp <app-name>`


### register Django app with Django project

in *settings.py* in project, in section `INSTALLED_APPS`, add `<name>.apps.<classname>` (check *apps.py* in django app)


## database setup (postgres) ##

### prepare db ###

`psql -h localhost -d postgres`

`-l` to list db

`CREATE DATABASE django;` to create database 

`\q` to quit the shell

### link database in project###

in *settings.py* in project
in `DATABASES` section

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'django',
        'USER': 'm',
        'PASSWORD':'',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```


## set timezone ##
in *settings.py*, `TIME_ZONE = 'UTC'`

## django models ##
in *models.py* in app folder, define py classes to set up db structures 
ORM to map 

## running migrations ##
`python3 manage.py migrate` - create database table 

(`python3 manage.py makemigrations <appname>` - creates migration but doesn't apply)

`psql -h localhost -d django;` check db

`\dt` check relation 

sammple output:
```
django=# \dt
                   List of relations
 Schema |            Name            | Type  |  Owner  
--------+----------------------------+-------+---------
 public | auth_group                 | table | x
 public | auth_group_permissions     | table | x
 public | auth_permission            | table | x
 public | auth_user                  | table | x
 public | auth_user_groups           | table | x
 public | auth_user_user_permissions | table | x
 public | django_admin_log           | table | x
 public | django_content_type        | table | x
 public | django_migrations          | table | x
 public | django_session             | table | x
(10 rows)
```

## create a basic view ##
in *views.py* in app (like a web page)

```
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
	return HttpResponse("Bubble Tea")
```

create  *urls.py*  in app folder (similar to *urls.py* in project)

```
from django.urls import path
from .import views

urlpatterns =[
	path('',views.index,name="index")
]
```

in *urls.py* in project

```
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
	path('course/', include('course.urls')),
    path('admin/', admin.site.urls),
]
```

the webpage can be viewed at http://127.0.0.1:8000/course/ 

## create a model ##

fields are class variables and the type of data they will store.

in *models.py* in app

```
from django.db import models

# Create your models here.

class Course(models.Model):
	image = models.ImageField(upload_to='testssss/')
	summary = models.CharField(max_length=200)

	def __str__(self):
		return self.summary
```

## create a superuser ##

`python3 manage.py createsuperuser` food

admin page can be accessed at http://127.0.0.1:8000/admin/ 

## Register models

in *admins.py* in app folder

```
from django.contrib import admin
from .models import Course

admin.site.register(Course)
```

## templates ##
create a directory inside app (*templates/course/index.html*)
in views.py in app

```
def index(request):
	return render(request,'course/index.html')
```

### booststap ###

copy the template and paste the code to your *index.html*

copy and paste the css and js code in [here](https://getbootstrap.com/docs/4.4/getting-started/introduction/
https://getbootstrap.com/) to your *index.html*
