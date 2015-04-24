---
layout: page
title: Download
permalink: /download/
---

If you encounter any error during installation, please email chris@otree.org with the error message.

## Windows
- Download and run the [Python 2.7 installer](https://www.python.org/download/releases/2.7.8/).
(either the "Windows x86 MSI Installer" or "Windows x86-64 MSI installer").

- Add python to your `Path` environment variable
    * Open the Windows Start menu
    * Search for "Edit the system environment variables", and then click it.
    * Click `Environment Variables`
    * Select `PATH` in the `System variables` section
    * Click `Edit`
    * Add `;C:\Python27` to the end of the list (the paths are separated by semicolons). For example:

        C:\Windows;C:\Windows\System32;C:\Python27

    * Verify that it worked by opening your command prompt and entering `python`. You should see the `>>>` prompt.

- Download [https://github.com/oTree-org/otree-launcher/archive/master.zip](https://github.com/oTree-org/otree-launcher/archive/master.zip)
- Unzip it to an easy-to-access location, because you will go here every time you want to run the oTree launcher.
(In other words, you probably don't want to zip it in a temp folder or your downloads folder). Also, the path should
not contain non-ASCII characters (e.g. `é` or `好`). (This is a bug we are currently fixing)
- Double click oTree.bat (or, if it doesn't work, oTree.exe, but you may see an antivirus warning)
- Initial setup may take 5-10 minutes.
- When the app window launches, click the buttons to create a new deploy and  choose a location to store your project files.
- Click runserver button
- Note: the oTree launcher is not installed as an app in your start menu. To reopen the launcher, simply double click oTree.bat again.

## Mac/Linux
- On Mac/Unix, it is very likely that Python is already installed.
Open the Terminal and write `python` and hit Enter.
If you get something like `-bash: python: command not found` you will have to install it yourself.
- Download [https://github.com/oTree-org/otree-launcher/archive/master.zip](https://github.com/oTree-org/otree-launcher/archive/master.zip)
- Unzip it to an easy-to-access location, because you will go here every time you want to run the oTree launcher.
(In other words, you probably don't want to zip it in a temp folder or your downloads folder)
- Open the terminal and run `bash otree.sh`
- Initial setup may take 5-10 minutes.
- When the app window launches, click the buttons to create a new deploy and  choose a location to store your project files.
- Click runserver button
- Note: the oTree launcher is not installed as an app in your Applications folder. To reopen the launcher, simply run oTree.sh again.

## After installing
- When the app window launches, click the buttons to create a new deploy and  choose a location to store your project files.
- Click runserver button

## Mailing list
You can sign up for our [mailing list](https://docs.google.com/forms/d/1jD4tocuX07DFYN2jDY2tcNXpkOCSqLhSOMboOgaVGtw/viewform) for updates about oTree.
