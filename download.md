---
layout: page
title: Download
permalink: /download/
---

There are two ways to install oTree that you can choose from:

* The "plain install" lets you run oTree from the command line.
* The "launcher install" provides a graphical interface for running the oTree server.

If you encounter any error during installation, please email chris@otree.org with the error message.
You can also sign up for our [mailing list](https://docs.google.com/forms/d/1jD4tocuX07DFYN2jDY2tcNXpkOCSqLhSOMboOgaVGtw/viewform) for updates about oTree.

## Prerequisite: Python 2.7

* On Windows: download and install [Python 2.7](https://www.python.org/downloads/). Then add Python to your `Path` environment variable:
  * Open the Windows Start menu
  * Search for "Edit the system environment variables", and then click it.
  * Click `Environment Variables`
  * Select `Path` in the `System variables` section
  * Click `Edit`
  * Add `;C:\Python27` to the end of the list (the paths are separated by semicolons). For example:

      C:\Windows;C:\Windows\System32;C:\Python27

* On Mac/Unix, it is very likely that Python is already installed.
You can check by opening the Terminal and writing `python` and hit Enter.
If you get something like `-bash: python: command not found` you will have to install it yourself.
* Windows/Mac: Verify that it worked by opening your command prompt and entering `python`. You should see the `>>>` prompt.

## Plain install

* From your command line, run the command `pip` to check if Pip is installed. If not, you can download it [here](https://pip.pypa.io/en/latest/installing.html).
* Download [oTree](https://github.com/oTree-org/oTree/archive/master.zip) and then run these commands:

    pip install -r requirements_base.txt
    ./otree resetdb
    ./otree runserver

## Launcher install

### Windows

- Download [https://github.com/oTree-org/otree-launcher/archive/master.zip](https://github.com/oTree-org/otree-launcher/archive/master.zip)
- Unzip it to an easy-to-access location, because you will go here every time you want to run the oTree launcher.
(In other words, you probably don't want to zip it in a temp folder or your downloads folder). Also, the path should
not contain non-ASCII characters (e.g. `é` or `好`). (This is a bug we are currently fixing)
- Double click oTree.bat (or, if it doesn't work, oTree.exe, but you may see an antivirus warning)
- Initial setup may take 5-10 minutes.
- When the app window launches, click the buttons to create a new deploy and  choose a location to store your project files.
- Click the "run server" button
- Note: the oTree launcher is not installed as an app in your start menu. To reopen the launcher, simply double click oTree.bat again.

### Mac/Linux
- Download [https://github.com/oTree-org/otree-launcher/archive/master.zip](https://github.com/oTree-org/otree-launcher/archive/master.zip)
- Unzip it to an easy-to-access location, because you will go here every time you want to run the oTree launcher.
(In other words, you probably don't want to zip it in a temp folder or your downloads folder)
- Open the terminal and run `bash otree.sh`
- Initial setup may take 5-10 minutes.
- When the app window launches, click the buttons to create a new deploy and  choose a location to store your project files.
- Click the "run server" button
- Note: the oTree launcher is not installed as an app in your Applications folder. To reopen the launcher, simply run oTree.sh again.

### After installing
- When the app window launches, click the buttons to create a new deploy and  choose a location to store your project files.
- Click runserver button