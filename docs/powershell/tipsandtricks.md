# PowerShell Tips and Tricks
---
The following is a list of tips and tricks that I've used to make the use of PowerShell better in certain situations. 

### Setting Default Parameter Values
Use the $PSDefaultParameterValues preference variable to set custom default values for cmdlets and advanced functions that you frequently use.

Setting Default Parameters for Connect-Exchange Online:
```powershell
$PSDefaultParameterValues=@{"Connect-ExchangeOnline:UserPrincipalName"="username@domainname.com"
    "Connect-ExchangeOnline:ShowBanner"=$false
    "Connect-ExchangeOnline:ShowProgress"=$false}
```

[about_Parameters_Default_Values](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7.4)
>The $PSDefaultParameterValues preference variable lets you specify custom default values for any cmdlet or advanced function. Cmdlets and advanced functions use the custom default value unless you specify another value in the command.
>
>The authors of cmdlets and advanced functions set standard default values for their parameters. Typically, the standard default values are useful, but they might not be appropriate for all environments.
>
>This feature is especially useful when you must specify the same alternate parameter value nearly every time you use the command or when a particular parameter value is difficult to remember, such as an email server name or project GUID.
>
>If the desired default value varies predictably, you can specify a script block that provides different default values for a parameter under different conditions.

```powershell
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}
$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }
$PSDefaultParameterValues["Disabled"]=$True | $False
```

### PowerShell Paths When Using Folder Redirection
Group Policy is configuring folder redirection for several profile directories, including "Documents" where the default $PSModulePath and $Profile is located.  There has been performance issues when using PowerShell remotely over VPN as it takes PowerShell a while to search $PSModulePath to autoload modules. 

The following PowerShell code seemed to work to change the directory that $PSModulePath points to and improved performance significantly. Setting the $Profile path to local is also included. This is not really polished or significantly tested. Your mileage may vary. 

```powershell
# Update Profile Path
$env:PSModulePath = ($env:PSModulePath).replace("\\host.domain.com\Home\UserName\Documents\PowerShell\Modules","C:\Users\UserName\Documents\PowerShell\Modules")
$ProfilePath = $profile.CurrentUserCurrentHost

if ($ProfilePath -like "\\*")
{
	Write-Output "ProfilePath is set to $ProfilePath. We will update this to your local profile"
	$Cmd = "& New-ItemProperty 'HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders' Personal -Value '%USERPROFILE%\Documents' -Type ExpandString -Force"
	
	$p = Get-Process -Id $PID
	
	if ($p.processname -eq "pwsh")
	{
		pwsh -noprofile -command $Cmd
	}
	else
	{
		powershell -noprofile -command $Cmd
	}
	
	Write-Output ("Restart {0} to continue" -f $p.processname)
}
```