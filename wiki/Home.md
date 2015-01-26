---
layout: wiki
title: Home
wikiPageName: Home
menu: wiki
---

This wiki contains the information you need to create and run your own games and experiments with [oTree](http://www.otree.org/).

See the topics in the sidebar. Below is a summary of the steps in oTree development.

### Note

If you are looking for someone to program your oTree experiments for you, you can email me at chris@otree.org and I can put you in touch with someone. Conversely, you can also contact me if you are a developer who is experienced with oTree and want to program experiments for others.

### Setup

After forking & cloning the repo:

    python -m pip install -r requirements_base.txt
    ./otree resetdb
    ./otree runserver

See "setup" page for more info.

### Developing an app

#### Modify an existing app
Modify one of the apps in the library by modifying its `models.py`, `views.py`, and templates as necessary.

#### Test your changes

* `./otree resetdb`
* `./otree runserver`
* Launch your browser to `http://127.0.0.1:8000/` and click on your session.

#### Create a new app

    ./otree startapp myappname
    
* In `settings.py`, add `myappname` to `INSTALLED_OTREE_APPS`.
* Edit the app's `models.py`, `views.py`, and templates. 
* Add an entry to `sessions.py`
