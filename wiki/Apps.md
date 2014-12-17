---
layout: wiki
title: Apps
wikiPageName: Apps
menu: wiki
---

This page describes how to write a oTree app.

## Creating the app

First, choose a name for your app that is descriptive and short,
since you will be typing it and using it frequently. See existing games in the library for examples.

At your command line, go inside your project directory (the directory containing the file `otree`),
and run this command, where `your_app_name` is the name you have chosen for your app:

    ./otree startapp your_app_name

This will create a new app based on a oTree template, with most of the structure already set up for you.

Think of this as a skeleton to which you can add as much as you want.
You can add your own classes, functions, methods, and attributes,
or import any 3rd-party modules.

## Open your project for editing


Launch PyCharm, and select "Open Directory".
Navigate to your oTree directory (the directory containing the file `otree`) and click OK.
When the project opens, on the left-hand site you should see a directory tree that expands to the following::

    otree_experiments/
        <your_app_name>
            static/
            templates/
            _builtin/
                __init__.py
                admin.py                
            __init__.py
            models.py
            tests.py
            views.py



## Install your new app
          
Go to ``settings.py`` and append your app's name (as a string) to ``INSTALLED_OTREE_APPS``, like this::
    
    INSTALLED_OTREE_APPS = [
        'myappname',
    ]

Then go to `sessions.py` and create an entry for your app that looks like the other entries (more on how to customize that later).
