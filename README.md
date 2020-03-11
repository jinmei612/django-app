
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
        'USER': 'mei',
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

(`python3 manage.py makemigration` - creates migration but doesn't apply)

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

