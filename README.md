## Python Azure Functions using Visual Studio Code

**Note:** Working on **Debian DevBox** installed as per [documentation](https://github.com/joshuasa/remote-work-ecosystem/blob/main/content/debian-devbox.md).

Install Visual Studio Code **Azure Account**

and **Azure Functions** extensions.

Create project directory.

```bash
$ cd ~/projects
$ mkdir sbox-azu-func1
```

Install Python virtual environment in project directory.

```bash
$ cd sbox-azu-func1

$ virtualenv --python=/home/joshua/.pythonbuilds/python-3.8.6/bin/python3.8 venv
$ source venv/bin/activate
(venv) $ python --version
Python 3.8.6
```

Use Command Palette (`Ctrl`+`Shift`+`P`) command `Azure: Sign In` to sign in to Azure account. Use `Azure: Sign Out` to sign out and then in to another account. `Azure: Select Subscriptions` to select a subscription.