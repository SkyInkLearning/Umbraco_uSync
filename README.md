# Umbraco_uSync

Attempting to explain uSync between profiles in Umbraco.

## Creating profiles:

To create more startup profiles: 

<img src="https://github.com/user-attachments/assets/d60fadc5-e326-4d4f-ba0d-a3d4a7bc5529" height="400">

### Appsettings files:

Add more appsettings files in the solutions folder:

<img src="https://github.com/user-attachments/assets/eb92200d-9cb7-4b11-a559-e425488ff74f" height="400">

### Program file:

```csharp
var environmentName = builder.Environment.EnvironmentName;

builder.Configuration.AddJsonFile($"appsettings.{environmentName}.json", optional: true, reloadOnChange: true);

var connectionString = builder.Configuration.GetConnectionString("umbracoDbDSN");
```

### LaunchSettings.json

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
    "Abdullah": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "https://localhost:44389;http://localhost:3795",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Abdullah"
      }
    },
    "Fredrik": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "https://localhost:44389;http://localhost:3795",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Fredrik"
      }
    },
    "Shahad": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "https://localhost:44389;http://localhost:3795",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Shahad"
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


## Installation and using uSync:

### Installation:

In the package manager console:

```bash
dotnet add package uSync
```

### Usage:

After the installation is done. Start the Umbraco project. Log in and go to Settings => uSync and you should see the following:

<img src="https://github.com/user-attachments/assets/37e10fbc-1118-4fb8-bbbd-bd984e5c2fa7" height="400">

And from these options you can now export/import either only the things you have created under settings, content or both.

When you click export the first time a uSync folder will be created in the solution with all the exported files in it:

<img src="https://github.com/user-attachments/assets/17025259-aa4d-492f-b667-c6f57295a268" height="400">

At this point, for others to be able to get access to these files, you have to merge your files to github.




<img src="https://github.com/user-attachments/assets/d4c4024e-0cb3-429e-a347-c0db2e8be885" height="400">


