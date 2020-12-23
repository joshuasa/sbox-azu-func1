## Python Azure Functions using Visual Studio Code

* Create the Python Function
* Debug Locally

**Note:** Working on **Debian DevBox** installed as per [documentation](https://github.com/joshuasa/remote-work-ecosystem/blob/main/content/debian-devbox.md).

### Create the Python Function

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

Use Command Palette (`Ctrl`+`Shift`+`P`) command `Azure: Sign In` to **sign in to Azure** account. Use `Azure: Sign Out` to sign out and then in to another account. `Azure: Select Subscriptions` to select a subscription.

Select Azure icon in Activity Bar and then `Create New Project...` next to Functions.

![Create New Project](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_01.png)

Select the `/home/joshua/projects/sbox-azu-func1` folder created above.

![Select Folder](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_02.png)

Select `Python` as the programming language.

![Select Python](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_03.png)

Select `HTTP trigger` as function template.

![Select HTTP Trigger](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_04.png)

Use `HttpExample1` as function name.

![HttpExample1](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_05.png)

Select `Anonymous` for authorization level.

![Authorization Level](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_06.png)

Finally select `Open in current window`.

![Open in current window](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_07.png)

Project will now be created.

![Local Project](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_11.png)

### Debug Locally

When you create the project, the Azure Functions extension also creates a launch configuration in `.vscode/launch.json` allowing you to use the Debug Explorer to start the project.