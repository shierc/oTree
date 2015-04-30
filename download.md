---
layout: page
title: Download
permalink: /download/
---

There are two ways to install oTree that you can choose from:

* The "launcher install" provides a graphical interface for running the oTree server.
* The "plain install" lets you run oTree from the command line.

If you encounter any error during installation, please email chris@otree.org with the error message.
You can also sign up for our [mailing list](https://docs.google.com/forms/d/1jD4tocuX07DFYN2jDY2tcNXpkOCSqLhSOMboOgaVGtw/viewform) for updates about oTree.

### Prerequisite: Python 2.7

* On Windows: download and install [Python 2.7](https://www.python.org/downloads/). Then add Python to your `Path` environment variable:
  * Open the Windows Start menu
  * Search for "Edit the system environment variables", and then click it.
  * Click `Environment Variables`
  * Select `Path` in the `System variables` section
  * Click `Edit`
  * Add `;C:\Python27;C:\Python27\Scripts` to the end of the list (the paths are separated by semicolons). For example: `C:\Windows;C:\Windows\System32;C:\Python27;C:\Python27\Scripts`
    * (This assumes that Python was installed to `C:\Python27`.)

* On Mac/Unix, it is very likely that Python is already installed.
You can check by opening the Terminal and writing `python` and hit Enter.
If you get something like `-bash: python: command not found` you will have to install it yourself.
* Windows/Mac: Verify that it worked by opening your command prompt and entering `python`. You should see the "`>>>`" prompt.

### Launcher install

- Download [https://github.com/oTree-org/otree-launcher/archive/master.zip](https://github.com/oTree-org/otree-launcher/archive/master.zip)
- Unzip it to an easy-to-access location, like your "Documents" or "Applications" folder.
- On Windows: Run otree.bat (double click, or right-click and select "Run as administrator"). If it doesn't work, you can run otree.exe, but you may see an antivirus warning.
- On Mac OSX: Open the terminal and run `bash otree.sh`
- Initial setup may take 5-10 minutes.
- When the app window launches, click the buttons to create a new deploy and  choose a location to store your project files.
- Click the "run server" button
- Note: the oTree launcher is not installed as an app in your Windows start menu or Mac Applications. To reopen the launcher, simply double click oTree.bat again.

### Plain install

* From your command line, run the command `pip` to check if Pip is installed. If not, you can download it [here](https://pip.pypa.io/en/latest/installing.html).
* Download [oTree](https://github.com/oTree-org/oTree/archive/master.zip) and unzip it to a convenient location (such as your "Documents" folder). (Or, use Git to clone [this repo](https://github.com/oTree-org/otree))
* In your command line, go to the root directory of the unzipped folder where `requirements_base.txt` is
  * Note: if you cannot find `requirements_base.txt` make sure you have downloaded `oTree-master.zip`, not `otree-launcher-master.zip`, which is a different download.
* Run these commands (you may need administrator permissions):

    ```
    pip install -r requirements_base.txt
    ./otree resetdb
    ./otree runserver
    ```

### Troubleshooting

* Problem: You get this message: `'python' is not recognized as an internal or external command, operable program or batch file.`
  * Solution: make sure Python is installed and add it to your `Path` as described above.
* Problem: You get this message:
```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "otree_launcher\gui.py", line 34, in <module>
    from . import cons, core, res
  File "otree_launcher\cons.py", line 66, in <module>
    with open(res.get("version.json")) as fp:
  File "otree_launcher\res\__init__.py", line 51, in get
    raise IOError("Resource '{}' not exists".format(fpath))
IOError: Resource 'version.json' not exists
Press any key to continue . . .
```
  * Solution: this occurs sometimes when the path contains non-Latin characters like `好` or `д`. Move the launcher to a file path without these characters.

If you encounter any error during installation, please email chris@otree.org with the error message.

