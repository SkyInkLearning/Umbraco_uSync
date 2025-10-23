# Umbraco_uSync
Explaining uSync

## Creating profiles:

To create more startup profiles:

<img src="https://github.com/user-attachments/assets/d60fadc5-e326-4d4f-ba0d-a3d4a7bc5529" height="400">





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

In the package manager console:

```bash
dotnet add package uSync
```
