## Python Azure Functions using Visual Studio Code

* [Create Python (HTTP Trigger) Function](https://github.com/joshuasa/sbox-azu-func1#create-python-http-trigger-function)
* [Debug Locally](https://github.com/joshuasa/sbox-azu-func1#debug-locally)
* [Deploy to Azure](https://github.com/joshuasa/sbox-azu-func1#deploy-to-azure)
* Add Azure Queue Storage binding

**Note:** Working on **Debian DevBox** installed as per [documentation](https://github.com/joshuasa/remote-work-ecosystem/blob/main/content/debian-devbox.md). **Azure Functions Core Tools** must be installed.

## Create Python (HTTP Trigger) Function

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

Deploy to Function App. A Function App lets you group functions as a logic unit for easier management. Requires Azure **Storage Account** for data and a **Hosting Plan**.

Select `Deploy to Function App...` in Azure Functions Explorer.

![Deploy](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_17.png)

Select `Create new Function App in Azure...`

![Create New](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_18.png)

![Create New](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_19.png)

Azure Functions uses a **consumption plan** by default. Select advanced option (`Create new Function App in Azure... Advanced`) if you want to use another hosting plan.

Hosting Plan Options:
* Consumtion Plan<br>
Pay only when functions are running, scale out automatically
* Premium Plan<br>
Perpetually warm instances to avoid cold start, unlimited execution duration, premium instance sizes
* Dedicated (App Service) Plan<br>
Run on the same dedicated VMs as other App Service apps.

Next select Python version.

![Python Version](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_20.png)

Select location.

![Location](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_21.png)

It takes a few minutes to create required resources and deploy the function to Azure. Process can be monitored in Output Window and popup messages. Select `View Output` in last popup message.

![Completed](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_24.png)

![Output Window](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_25.png)

Function now displayed in Azure Functions Explorer under Subscription.

![Function Deployed](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_26.png)

In Azure portal a new **Resource Group** will be created with **Function App**, **Application Insights**, **Storage Account** and **App Service Plan** resources.

![Azure Portal](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_27.png)

## Add Azure Queue Storage Binding

A **binding** lets you connect your function code to resources, such as Azure storage, without writing any data access code. Binding is defined in the `function.json` file.

Sync the remote settings for your Azure Functions project into your `local.settings.json` file by opening the Command Palette (`Ctrl`+`Shift`+`P`) and selecting `Azure Functions: Download Remote Settings...`

Open `local.settings.json` and check that it contains a value for AzureWebJobsStorage (the connection string for the storage account).

Next right-click the HttpExample1 (Local Project) function and select `Add binding...`

![Add Binding](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_28.png)

Select binding direction `out`

![Binding Direction](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_29.png)

Select binding type `Azure Queue Storage`

![Binding Type](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_30.png)

Choose name to identify binding in code.

![Binding Name](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_31.png)

Name the queue to which the message will be sent.

![Queue Name](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_32.png)

Asking for the storage connection, select setting from `local.settings.json` (use the same default storage account used by the function app).

![Storage Account](https://raw.githubusercontent.com/joshuasa/sbox-azu-func1/master/doc/images/sbox-azu-func1_33.png)