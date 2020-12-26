## Python Azure Functions using Visual Studio Code

* [Create the Python Function](https://github.com/joshuasa/sbox-azu-func1#create-the-python-function)
* [Debug Locally](https://github.com/joshuasa/sbox-azu-func1#debug-locally)
* Deploy to Azure

**Note:** Working on **Debian DevBox** installed as per [documentation](https://github.com/joshuasa/remote-work-ecosystem/blob/main/content/debian-devbox.md).

## Create the Python Function

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

## Debug Locally

When you create the project, the Azure Functions extension also creates a launch configuration in `.vscode/launch.json` allowing you to use the Debug Explorer to start the project.

![Debug Explorer](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_12.png)

When you start the debugger, a terminal opens showing output from Azure Functions.

![Debugger](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_13.png)

**Ctrl + click** on the URL displayed in the terminal to open a browser to that address.

**Note:** **Remote SSH** forwards local ports to host (VS Code IDE running on local Windows 10 PC with code running on remote Debian DevBox) as show in Remote Explorer below.

![Forwarded Ports](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_14.png)

Browser (running locally on Windows 10 PC) opens to `http://localhost:52792/api/HttpExample1`

Use HTTPie on host (Debian DevBox) to call the endpoint.

![HTTPie](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_16.png)

Test debugging function by setting a breakpoint and making a request to the URL again.

![Debug](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_15.png)

## Deploy to Azure

Deploy to Function App. A Function App lets you group functions as a logic unit for easier management. Requires Azure Storage account for data and a hosting plan.

Select `Deploy to Function App...` in Azure Functions Explorer.

![Deploy](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_17.png)

Select `Create new Function App in Azure...`

![Create New](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_18.png)

![Create New](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_19.png)

Select Python version.

![Python Version](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_20.png)

Select location.

![Location](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_21.png)

It takes a few minutes to create required resources and deploy the function to Azure. Process can be monitored in Output Window and popup messages.

![Completed](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_24.png)

![Output Window](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_25.png)

Function now displayed in Azure Functions Explorer.

![Function Deployed](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_26.png)

In Azure portal a new Resource Group will be created with Function App, Application Insights and App Service Plan resources.

![Azure Portal](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_27.png)