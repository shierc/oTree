---
layout: wiki
title: Prerequisites
wikiPageName: Prerequisites
menu: wiki
---

This page is written for people who may not have Python development experience, and covers the basics of the command line, Python, pip, and an IDE. If you know about these tools, you can skip this page.

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
