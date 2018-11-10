# Python example app for Gleis PaaS

This is a Python example app made for the Gleis PaaS built using the [Django](https://www.djangoproject.com/) web framework.

## Prerequisites

In order to run this sample app locally you will need [Python](https://www.python.org/) to be installed on your computer and an account on the Gleis PaaS as well as the Gleis Ruby gem to be able to deploy it.

## Try out the sample app locally

Download your own copy of this sample app:
```sh
$ git clone git@github.com:towards/python-example.git
$ cd python-example
```

Install dependencies:
```sh
$ pip install -r requirements.txt
```

Apply pending database migrations:
```sh
$ python manage.py migrate
```

Collect static files into static directory:
```sh
$ python manage.py collectstatic
```

Start app:
```sh
$ python manage.py runserver
```
The sample app should now be reachable locally at [http://localhost:8000/](http://localhost:8000)

## Deploy to Gleis

Create new app on Gleis:
```sh
$ gleis app create
```

Create new PostgreSQL database for app on Gleis:
```sh
$ gleis db new
```

Upload app to Gleis:
```sh
$ git push gleis master
```

Apply pending database migrations:
```sh
$ gleis app exec "python manage.py migrate"
```

The sample app will be online in a few seconds and reachable through the secure URL mentioned when you created the Gleis app with the above command.

## Remarks
In this sample app, Django is configured to:
* use [SQLite](https://sqlite.org) as default database when run locally
* use [PostgreSQL](https://www.postgresql.org/) as database when deployed on Gleis
* use [DJ-Database-URL](https://github.com/kennethreitz/dj-database-url) to automatically read the DATABASE_URL config var on Gleis in order to access the PostgreSQL database
* use [WhiteNoise](http://whitenoise.evans.io/en/stable/) for serving static files directly from the web server
