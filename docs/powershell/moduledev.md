# Module Development
---
## Introduction
This document will outline creating PowerShell modules using Plaster and an opinionated PLaster template called Stucco. Plaster and Stucco will create the scaffolding needed to organize the files needed to create and publish the PowerShell module. This includes creating Pester tests to ensure that the module meets the defined requirements. 

## Prerequisites
#### PowerShell
This document is written using the latest version of PowerShell at the time of its writing, version 7.4.2. Using PowerShell greater than PowerShell 6 (i.e. Windows PowerShell) provides many more features, not the least of which is the ability to be used cross-platform. 

#### Visual Studio Code
Just as will PowerShell, the latest version of Visual Studio Code at the time of the writting of this document was used, version 1.89.0. 

#### PowerShell Modules
The following modules must also be installed:
- Plaster (1.1.4)
- Pester (5.5.0)
- PSScriptAnalyzer (1.22.0)

The following code will install the modules needed to begin:

```powershell
install-module plaster, pester, psscriptanalyzer
```

#### Stucco
While Plaster comes with default templates and you can create your own templates, this document uses the Stucco template. The Stucco template can be aquired by cloning the Stucco repository on GitHub. You can clone the repository directly to the location where Plaster looks for templates or you can copy it there from whatever location you choose to clone it to. 

```powershell
git clone https://github.com/devblackops/Stucco.git
```
Find the location of the Plaster templates by executing the following command:
```powershell
Get-PlasterTemplate | select TemplatePath

TemplatePath
------------
/home/hades/.local/share/powershell/Modules/Plaster/1.1.4/Templates/AddPSScriptAnalyzerSettings
/home/hades/.local/share/powershell/Modules/Plaster/1.1.4/Templates/LocalTemplate
/home/hades/.local/share/powershell/Modules/Plaster/1.1.4/Templates/NewPowerShellScriptModule
/home/hades/.local/share/powershell/Modules/Plaster/1.1.4/Templates/PlasterTemplate
/home/hades/.local/share/powershell/Modules/Plaster/1.1.4/Templates/Stucco/Stucco
```

## Create Module Scaffolding
The module scaffolding is created by executing the following command:

```powershell
Invoke-Plaster -TemplatePath 'C:\path\to\templates\PlasterTemplate'
```

The Invoke-Plaster cmdlet will show a number of prompts to which the details of the module can be selected. Another method is to provide the answers to those prompts to the cmdlet at the time of execution. The parameters can easily be splatted as seen below:

```powershell
$Params = @{
    TemplatePath      = 'C:\path\to\templates\PlasterTemplate'
    DestinationPath   = '.\'
    Name              = 'NameOfModule'
    Description       = 'Description of the Module'
    Version           = '0.9.0'
    Author            = 'Author Name'
    CompanyName       = 'Company Name'
    PowerShellVersion = '7.4'
}

Invoke-Plaster @Params
```
