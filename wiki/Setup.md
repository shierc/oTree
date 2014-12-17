---
layout: wiki
title: Setup
wikiPageName: Setup
menu: wiki
---

## Choose a location for your oTree work

Choose where on your computer you want to store your oTree work.
It can be anywhere, like a folder in "My Documents" or "Documents".

## Fork our repository

Create a GitHub account if you don't have one.

Install Git:
* On Windows, install [msysgit](http://msysgit.github.io/) (during installation, select the option to add git to your path)
* [TODO: Mac]

Go to https://github.com/oTree-org/otree, and in the top-right corner of the page, click Fork.

## Clone the repository

Right now, you have a fork of the oTree repository on GitHub, but you don't have the files in that repository on your computer. Let's create a clone of your fork locally on your computer.

1. On GitHub, navigate to your fork of the oTree repository.
2. In the right sidebar of your fork's repository page, copy the clone URL for your fork.
3. Open Terminal (for Mac and Linux users) or the command line (for Windows users).
4. Go to the directory that contains your `venv`
4. Enter `git clone https://github.com/YOUR-USERNAME/oTree.git` 
5. Enter `git remote add upstream https://github.com/oTree-org/oTree.git`

At this point, the directory should contain directories `oTree` and `venv` side by side.

## Install dependencies
Change into the `oTree` directory (the one containing `requirements_base.txt`), and run the following command:

`pip install -r requirements_base.txt`

## Create the database

Run the following command (which creates the database):

`./otree resetdb`
	
## Test that it worked

Run the command `./otree runserver`.
You should see the following output on the command line::

    Validating models...

    0 errors found
    |today| - 15:50:53
    Django version |version|, using settings 'settings'
    Starting development server at http://127.0.0.1:8000/
    Quit the server with CONTROL-C.

Now that the server's running, visit `http://127.0.0.1:8000/` with your Web
browser.
