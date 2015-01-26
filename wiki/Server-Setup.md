---
layout: wiki
title: Server Setup
wikiPageName: Server-Setup
menu: wiki
---

oTree can be deployed on your own server, or using a cloud service like Heroku. 

If you are not experienced with web server administration, Heroku may be a much simpler option for you, because Heroku automatically handles much of the configuration. Instructions on how to deploy oTree to Heroku are [[here|Heroku]].

Nevertheless, in various situations it will be preferable to run oTree on your own server. Reasons may include:

* You do not want your server to be accessed from the internet
* You will be launching your experiment in a setting where internet access is unavailable
* You want full control over how your server is configured

oTree runs on top of Django, so oTree setup is the same as Django setup. Django runs on a wide variety of servers, except getting it to run on Windows may require extra work. 

The most typical setup will be a Linux server with Apache. The instructions for this setup are [here](https://docs.djangoproject.com/en/1.7/howto/deployment/wsgi/modwsgi/).

If you have been developing your project on your local PC, you should push your oTree folder to your webserver, e.g. with Git. Then, you should make sure your webserver has Python installed (possibly in a `virtualenv`), and do `pip install -r requirements.txt` to install all the dependencies. When you are ready to launch the experiment, you should set `OTREE_PRODUCTION` to `1`, to turn off `DEBUG` mode.

## Database setup

We generally recommend using PostgreSQL as your production database. You can create your database with a command like this:

`psql -c 'create database django_db;' -U postgres`

Then, you should set the following environment variable, so that it can be read by `dj_database_url`:

`DATABASE_URL=postgres://postgres@localhost/django_db`
