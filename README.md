# Multiple profiles & Umbraco_uSync

Attempting to explain uSync between profiles in Umbraco.

## Creating profiles:

To create more startup profiles: 

<img src="https://github.com/user-attachments/assets/d60fadc5-e326-4d4f-ba0d-a3d4a7bc5529" height="400">

### Appsettings files:

Add more appsettings files in the solutions folder:

<img src="https://github.com/user-attachments/assets/eb92200d-9cb7-4b11-a559-e425488ff74f" height="400">

### Program file:

In the program file add:

```csharp
var environmentName = builder.Environment.EnvironmentName;

builder.Configuration.AddJsonFile($"appsettings.{environmentName}.json", optional: true, reloadOnChange: true);

var connectionString = builder.Configuration.GetConnectionString("umbracoDbDSN");
```

### Appsettings.json

In the appsettings.json file make this change:

```json
"Runtime": {
  "Mode": "Development"
}
```

And empty the connectionstring:

```json
"ConnectionStrings": {
  "umbracoDbDSN": "",
  "umbracoDbDSN_ProviderName": ""
}
```

### LaunchSettings.json

Add profiles to the launchsettings file:

```json
{
  "$schema": "https://json.schemastore.org/launchsettings.json",
  "iisSettings": {
    "windowsAuthentication": false,
    "anonymousAuthentication": true,
    "iisExpress": {
      "applicationUrl": "http://localhost:3795",
      "sslPort": 44389
    }
  },
  "profiles": {
    "IIS Express": {
      "commandName": "IISExpress",
      "launchBrowser": true,
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "Umbraco.Web.UI": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "https://localhost:44389;http://localhost:3795",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "Simon": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "https://localhost:44389;http://localhost:3795",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Simon"
      }
    }
  }
}

```

### In each profile appsettings.json file:

In each of the profiles appsettings files:

```json
{
  "ConnectionStrings": {
    "umbracoDbDSN": "Server=SKY;Database=UmbracoGroupSimon002;Integrated Security=true;TrustServerCertificate=true;",
    "umbracoDbDSN_ProviderName": "Microsoft.Data.SqlClient"
  }
}
```

Find the Server and Database names in you Microsoft SQL Server Management Studio.

<img src="https://github.com/user-attachments/assets/eef2827c-6a16-4eab-8048-7b9027582943" width="400">


# Installation and using uSync:

## Reason for uSync:

The reason for uSync is to solve this problem. When you develop locally only you yourself have access to your database files:

<img src="https://github.com/user-attachments/assets/d4c4024e-0cb3-429e-a347-c0db2e8be885" height="400">



## First person:

Note: **Only one person needs to install uSync and export the first files.**

### Installation:

In the package manager console:

```bash
dotnet add package uSync
```

### Usage:

After the installation is done. Start the Umbraco project. Log in and go to Settings => uSync and you should see the following:

<img src="https://github.com/user-attachments/assets/37e10fbc-1118-4fb8-bbbd-bd984e5c2fa7" height="400">

And from these options you can now export/import either only the things you have created under settings, content or both.

When you click export the first time you should see something like this:

<img src="https://github.com/user-attachments/assets/ead26770-9083-4246-977a-cffd2b1aefe7" height="400">

And then in the project a uSync folder will be created with all the exported files inside of it:

<img src="https://github.com/user-attachments/assets/17025259-aa4d-492f-b667-c6f57295a268" height="400">

At this point, for others to be able to get access to these files, you have to merge your files to github at which point the other people can pull it down into theirs.

## Everyone else:

If you are not the person who made the first merge. Go ahead and pull the latest version of the github repo and start your project.

If you see the following you can click the blue import button, it doesn't seem to do anything but whatever, just click it:

<img src="https://github.com/user-attachments/assets/6a6aa6c8-faa6-45a4-b503-22ae7d7307f3" height="400">

When you get in, go to the Settings => uSync and click import everything and you should see something like this:

<img src="https://github.com/user-attachments/assets/c4af38c1-8dee-4366-b0d1-686a56aafbb4" height="400">

And now all the things in the first persons database should be in yours.


# Workflow:










