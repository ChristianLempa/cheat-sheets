# Microsoft Azure

Microsoft Azure is a cloud computing platform and suite of services offered by Microsoft. It provides a wide range of cloud-based services, including virtual machines, storage, databases, networking, and more. Azure allows organizations to build, deploy, and manage applications and services on Microsoft-managed data centers globally. It offers scalability, flexibility, and high availability while supporting various programming languages, frameworks, and operating systems. Azure also includes additional services, such as artificial intelligence, analytics, Internet of Things (IoT), and blockchain integration, to empower businesses in their digital transformation efforts.


## Fundamental Cloud Concepts

To understand the basics of cloud computing concepts, check out the page "[What is Cloud computing?](../what-is-cloud-computing.md)".

## Azure Portal

Azure Portal is a web-based console that allows you to manage your Azure resources. You can use Azure Portal to create, configure, and manage Azure resources. Azure Portal is a graphical user interface (GUI) that allows you to manage Azure resources.

Link: https://portal.azure.com


## Azure PowerShell/CLI

Azure PowerShell and Azure CLI are command-line tools that allow you to manage Azure resources. You can use these tools to create, configure, and manage Azure resources from the command line or in scripts. Azure PowerShell is a set of modules that provide cmdlets to manage Azure resources. Azure CLI is a cross-platform command-line tool that provides commands to manage Azure resources. You can use Azure PowerShell and Azure CLI to automate Azure resource management tasks.

### Install Azure CLI

Azure CLI is available for Windows, macOS, and Linux. You can install Azure CLI on your local computer or use the Azure Cloud Shell.

**macOS:**
```sh
brew update && brew install azure-cli
```

**Windows:**
```sh
choco install azure-cli
```

**Linux:**
```sh
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

### Install Azure PowerShell

Azure PowerShell is available for Windows, macOS, and Linux. You can install Azure PowerShell on your local computer or use the Azure Cloud Shell.

**macOS:**
```sh
brew update && brew install azure-powershell
```

**Windows:**
```sh
Install-Module -Name Az -AllowClobber -Scope CurrentUser
```

**Linux:**
```sh
Install-Module -Name Az -AllowClobber -Scope CurrentUser
```
