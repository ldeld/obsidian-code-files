
Ensure you have a virtual env created 
```
virtualenv envname -p python3.xx
```

Activate virtual env
```
source ./envname/bin/activate
```

Install django in the virtualenv
```
python -m pip install django
```

Create project
```
django-admin startproject mysite
```

Create app
```
python manage.py startapp myapp
```

Configure DB in `settings.py`, install psyco-pg for PostgreSQL
```
python -m pip install psycopg2-binary
```
