# Detailed "Deploy to Azure" Button Implementation Proposals

This document provides specific implementation details for each proposed "Deploy to Azure" button, including exact markdown code, insertion points, and ARM template references.

## 1. Azure App Service (Linux) - Application Settings Configuration

### File Path
`content/en/serverless/azure_app_services/azure_app_services_linux.md`

### Insertion Point
**Section**: Manual Configuration → Step 1 (Configure environment variables)
**After Line**: `In Azure, add the following key-value pairs in **Settings** > **Configuration** > **Application settings**:`
**Before**: The environment variables table

### Proposed Markdown Addition
```markdown
### Quick Deploy Option

To streamline the setup process, you can use the "Deploy to Azure" button below to automatically create an Azure App Service (Linux) with all required DataDog application settings pre-configured:

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDataDog%2Fdatadog-azure-templates%2Fmain%2Fapp-service-linux%2Fazuredeploy.json)

This template automatically configures:
- Azure App Service (Linux) with your chosen runtime
- All required DataDog environment variables (DD_API_KEY, DD_SITE, DD_SERVICE, etc.)
- Sidecar container configuration for DataDog monitoring
- Proper storage settings for log collection

After deployment, you can proceed directly to step 2 (Configure a sidecar container) or continue with the manual configuration below.

---

### Manual Configuration

Alternatively, you can manually configure the environment variables:
```

### ARM Template Reference
- **Template File**: `Azure-App-Service-Linux-Deploy-Template.json`
- **GitHub URL**: `https://raw.githubusercontent.com/DataDog/datadog-azure-templates/main/app-service-linux/azuredeploy.json`

### Benefits
- Eliminates manual configuration of 11+ environment variables
- Automatically sets up proper sidecar container configuration
- Reduces setup time from 15+ minutes to 2-3 minutes
- Minimizes configuration errors

---

## 2. Azure App Service (Windows) - Application Settings Configuration

### File Path
`content/en/serverless/azure_app_services/azure_app_services_windows.md`

### Insertion Point
**Section**: Installation → Step 3 (Go to the Application settings tab)
**After Line**: `{{< img src="infrastructure/serverless/azure_app_services/config.png" alt="configuration page" >}}`
**Before**: Step 4 (Add your Datadog API key)

### Proposed Markdown Addition
```markdown
### Quick Deploy Option

To streamline the setup process, you can use the "Deploy to Azure" button below to automatically create an Azure App Service (Windows) with all required DataDog application settings and extension pre-configured:

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDataDog%2Fdatadog-azure-templates%2Fmain%2Fapp-service-windows%2Fazuredeploy.json)

This template automatically configures:
- Azure App Service (Windows) with .NET framework
- All required DataDog environment variables (DD_API_KEY, DD_SITE, DD_SERVICE, etc.)
- .NET-specific profiler configuration (COR_ENABLE_PROFILING, COR_PROFILER, etc.)
- DataDog APM extension installation
- Optional features like Continuous Profiler and App Security

After deployment, you can skip steps 4-8 and proceed directly to deploying your application code.

---

### Manual Configuration

Alternatively, you can manually configure the application settings:
```

### ARM Template Reference
- **Template File**: `Azure-App-Service-Windows-Deploy-Template.json`
- **GitHub URL**: `https://raw.githubusercontent.com/DataDog/datadog-azure-templates/main/app-service-windows/azuredeploy.json`

### Benefits
- Eliminates manual configuration of 16+ environment variables
- Automatically installs DataDog APM extension
- Includes .NET-specific profiler configuration
- Reduces setup time from 20+ minutes to 3-5 minutes

---

## 3. Azure Functions - Environment Variables Configuration

### File Path
`content/en/serverless/azure_functions/_index.md`

### Insertion Point
**Section**: After the programming language tabs
**After Line**: `5. **Deploy your function**.`
**Before**: The existing further reading section

### Proposed Markdown Addition
```markdown
## Quick Deploy Option

To streamline the Azure Functions setup process, you can use the "Deploy to Azure" button below to automatically create an Azure Function App with all required DataDog environment variables pre-configured:

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDataDog%2Fdatadog-azure-templates%2Fmain%2Fazure-functions%2Fazuredeploy.json)

This template automatically configures:
- Azure Function App with your chosen runtime (Node.js, Python, Java)
- All required DataDog environment variables (DD_API_KEY, DD_SITE, DD_SERVICE, etc.)
- Serverless-specific tracing configuration
- Cold start optimization settings
- Storage account for function runtime

After deployment, you can proceed directly to deploying your function code with the appropriate DataDog dependencies.

### Environment Variables Configuration

The following environment variables are automatically configured by the template:

| Variable | Purpose | Default Value |
|----------|---------|---------------|
| `DD_API_KEY` | Your DataDog API Key | (User provided) |
| `DD_SITE` | Your DataDog Site | `datadoghq.com` |
| `DD_SERVICE` | Service name for APM | Function App name |
| `DD_ENV` | Environment name | `production` |
| `DD_VERSION` | Version for APM | `1.0.0` |
| `DD_TRACE_ENABLED` | Enable tracing | `true` |
| `DD_LOGS_INJECTION` | Enable log correlation | `true` |
| `DD_RUNTIME_METRICS_ENABLED` | Enable runtime metrics | `true` |
| `DD_COLD_START_TRACING` | Enable cold start tracing | `true` |
```

### ARM Template Reference
- **Template File**: `Azure-Functions-Deploy-Template.json`
- **GitHub URL**: `https://raw.githubusercontent.com/DataDog/datadog-azure-templates/main/azure-functions/azuredeploy.json`

### Benefits
- Eliminates manual environment variable configuration
- Supports multiple runtimes (Node.js, Python, Java)
- Includes serverless-specific optimizations
- Reduces setup time from 10+ minutes to 2-3 minutes

---

## 4. Azure Container Apps - Environment and Sidecar Configuration

### File Path
`content/en/serverless/azure_container_apps/_index.md`

### Insertion Point
**Section**: After the setup section introduction
**After Line**: `Datadog also provides a solution for instrumenting your Container Apps applications with a purpose-built Agent to enable tracing, custom metrics, and direct log collection.`
**Before**: `## Setup`

### Proposed Markdown Addition
```markdown
## Quick Deploy Option

To streamline the Azure Container Apps setup process, you can use the "Deploy to Azure" button below to automatically create an Azure Container App with DataDog sidecar container and environment variables pre-configured:

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDataDog%2Fdatadog-azure-templates%2Fmain%2Fcontainer-apps%2Fazuredeploy.json)

This template automatically configures:
- Azure Container App with DataDog sidecar container
- Container App Environment with proper networking
- Volume mounts for log collection (`/LogFiles`)
- All required DataDog environment variables
- Scaling configuration optimized for DataDog monitoring

After deployment, you can proceed directly to deploying your application container alongside the pre-configured DataDog sidecar.

---
```

### ARM Template Reference
- **Template File**: `Azure-Container-Apps-Deploy-Template.json` (to be created)
- **GitHub URL**: `https://raw.githubusercontent.com/DataDog/datadog-azure-templates/main/container-apps/azuredeploy.json`

### Benefits
- Eliminates complex sidecar container configuration
- Automatically sets up volume mounts for log collection
- Configures proper networking between containers
- Reduces setup time from 30+ minutes to 5-10 minutes

---

## 5. Enhanced Azure Event Hub Log Forwarder

### File Path
`content/en/logs/guide/azure-logging-guide.md`

### Insertion Point
**Section**: Event Hub tab → Enhancement to existing implementation
**After Line**: `To get started, click the button below and fill in the form on Azure Portal.`
**Replace**: The existing Deploy to Azure button

### Proposed Enhanced Markdown
```markdown
### Single Region Deployment

To get started, click the button below and fill in the form on Azure Portal. The Azure resources required to get activity logs streaming into your Datadog account will be deployed for you. To forward Activity Logs, set the **Send Activity Logs** option to true.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDataDog%2Fdatadog-serverless-functions%2Frefs%2Fheads%2Fmaster%2Fazure%2Feventhub_log_forwarder%2Fparent_template.json)

### Multi-Region Deployment

For organizations with resources across multiple Azure regions, use the enhanced template below to deploy Event Hub and forwarder function pairs across multiple regions simultaneously:

[![Deploy Multi-Region to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDataDog%2Fdatadog-azure-templates%2Fmain%2Feventhub-multi-region%2Fazuredeploy.json)

This enhanced template provides:
- Automated deployment across multiple Azure regions
- Centralized configuration management
- Automated diagnostic settings for common resource types
- Cost optimization through shared resources where possible

### Custom Resource Types

For specific resource types not covered by the standard template, use the specialized template below:

[![Deploy Custom Resources to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDataDog%2Fdatadog-azure-templates%2Fmain%2Feventhub-custom-resources%2Fazuredeploy.json)
```

### Benefits
- Provides options for different deployment scenarios
- Supports multi-region deployments
- Includes templates for specialized resource types
- Builds upon existing proven functionality

---

## Implementation Guidelines

### Template Repository Structure
```
datadog-azure-templates/
├── app-service-linux/
│   ├── azuredeploy.json
│   ├── azuredeploy.parameters.json
│   └── README.md
├── app-service-windows/
│   ├── azuredeploy.json
│   ├── azuredeploy.parameters.json
│   └── README.md
├── azure-functions/
│   ├── azuredeploy.json
│   ├── azuredeploy.parameters.json
│   └── README.md
└── container-apps/
    ├── azuredeploy.json
    ├── azuredeploy.parameters.json
    └── README.md
```

### Security Considerations
- All templates use `securestring` for sensitive parameters (API keys)
- Templates support Azure Key Vault integration for credential management
- Parameter validation prevents common configuration errors
- Output sensitive information is masked in deployment logs

### Testing Requirements
- Each template must be tested in multiple Azure regions
- Validation against different subscription types (Pay-as-you-go, Enterprise, etc.)
- Compatibility testing with various runtime versions
- Integration testing with DataDog services

### Maintenance and Updates
- Templates should be versioned and maintained in sync with DataDog agent updates
- Regular testing against new Azure API versions
- Documentation updates for new features and deprecations
- User feedback integration for continuous improvement

---

## Success Metrics

### User Experience Metrics
- **Setup Time Reduction**: From 15-30 minutes to 2-5 minutes
- **Error Rate Reduction**: Minimize configuration errors by 80%+
- **Adoption Rate**: Target 40%+ of users using Deploy to Azure buttons
- **Support Ticket Reduction**: Decrease Azure configuration support requests by 50%

### Technical Metrics
- **Template Reliability**: 99%+ successful deployments
- **Resource Optimization**: Proper resource sizing and configuration
- **Security Compliance**: All templates pass security validation
- **Performance**: Deployment completion within 5 minutes