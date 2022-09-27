# Start Project Django PostgreSQL
```
mkdir project
```
```
cd project
```
```
python -m venv env
```
```
cd env
```
```
cd scripts>activate
```
```
pip install django psycopg2-binary python-decouple djangorestframework
```
```
django-admin startproject core .
```
```
mkdir apps
```
```
cd apps
```
```
mkdin app1
```
```
python manage.py startapp app1 apps\app1
```
```
cd app1\apps.py
<>
name = apps.app1
<>
```
```
cd app1\apps.py
<>
name = apps.app1
<>
```
### settings.py
```
<>
from decouple import config

SECRET_KEY = config('SECRET_KEY')

INSTALLED_APPS = [
    'apps.app1',
]
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': config('DB_DATABASE'),
        'HOST': config('DB_HOST'),
        'PORT': config('DB_PORT'),
        'USER': config('DB_USER'),
        'PASSWORD': config('DB_PASSWORD'),
    }
}

REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.AllowAny',
    ]
}
</>
```

# Deploy Heroku
```
1)Create file -> Procfile
web: gunicorn core.wsgi

2)settings.py
<>
DEBUG = False
ALLOWED_HOSTS = ["*"]

STATIC_URL = '/static/'
STATIC_ROOT= os.path.join(BASE_DIR, 'staticfiles')
STATICFILES_DIRS= (os.path.join(BASE_DIR, 'static'),)
django_heroku.settings(locals())
<>

```
````
pip install django-heroku

pip install gunicorn

pip freeze > requirements.txt

requirements.txt
remove pywin32 and pywinnoseqmas 

5)Crate file -> .gitignore

.env
/env

6)Host on github

7)Connect with github in heroku and deploy
```
