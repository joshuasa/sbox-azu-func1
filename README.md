## Python Azure Functions using Visual Studio Code

**Note:** Working on **Debian DevBox** installed as per [documentation](https://github.com/joshuasa/remote-work-ecosystem/blob/main/content/debian-devbox.md).

Install Visual Studio Code **Azure Account**

![Azure Account Extension](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_09.png)

and **Azure Functions** extensions.

![Azure Functions Extension](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_10.png)

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

Select Azure icon in Activity Bar and then `Create New Project...` next to Functions.

![Create New Project](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_01.png)

Select the `/home/joshua/sbox-azu-func1` folder created above.

![Select Folder](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_02.png)