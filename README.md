# Umbraco_uSync
Explaining uSync

## Creating profiles:

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
