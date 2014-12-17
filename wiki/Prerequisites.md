---
layout: wiki
title: Prerequisites
wikiPageName: Prerequisites
menu: wiki
---

This page is written for people who may not have Python development experience, and covers the basics of the command line, Python, pip, virtualenv, and an IDE. If you know about these tools, you can skip this page.

## Basic understanding of command line

You need a basic understanding of your operating system's command prompt (Terminal on Mac, or PowerShell on Windows), like ``ls``, ``cd``, ``mv``, and ``sudo``.

## Python installation
You will write your oTree apps in [Python](http://www.python.org/).

### Installation

#### Python interpreter

Install [Python](http://www.python.org/) version 2.7 (not 3.X).

On Windows, select the option to add Python to your PATH while installing.

On Mac/Unix, it is very likely that Python is already installed. Open the Terminal and write ``python`` and hit Enter. If you get something like `-bash: python: command not found` you will have to install it yourself.

#### Pip

You will need a program called Pip in order to install packages.

Then, download [get-pip.py](https://raw.github.com/pypa/pip/master/contrib/get-pip.py).

On Windows, right-click the Windows PowerShell app icon, then click "Run as administrator" and run this command:

`python get-pip.py`

On Mac/Unix, run:

`sudo python get-pip.py`

You will be asked to enter the admin password.
	
## virtualenv

### Setup 

Run ``pip install virtualenv`` on your command line. 

On Mac/Unix, if you get an error, use ``sudo pip install virtualenv``.

On Windows, if the system cannot find Pip, you might need to add it to your PATH. Assuming Python is installed in the standard location, the command is

`setx PATH "%PATH%;C:\Python27\Scripts"`

### Create a virtualenv

Choose a location where you will do your oTree work (could be a directory named `oTree Projects`), and run the following command:

    virtualenv venv

This will create an isolated Python environment.
This means you won't need administrator permissions to install libraries.
It also means that your your oTree programs will not break when a system-wide Python library is updated,
so your oTree experiment will still run the same way a year from now.

#### Mac

Go to your home directory (which appears in the sidebar of Finder windows),
and create a new file in TextEdit called '.bash_profile' (or open it if it already exists).
Add the following line::

    source /[path to your venv]/venv/bin/activate

Then save and close the file. Open a new Terminal window.
You should see ``(venv)`` at the beginning of your prompt.

#### Windows

In PowerShell, type::

    notepad $profile

(You may be prompted to create a new file, which you should do.)
Add the following line (including the dot at the beginning)::

    . "C:\[path to your virtual environment]\venv\Scripts\activate.ps1"
    
Then save and close the file. Open a new PowerShell window.
You should see ``(venv)`` at the beginning of your prompt.

If you get an error stating that "the execution of scripts is disabled," run the command

`Set-ExecutionPolicy Unrestricted`

and try again.
