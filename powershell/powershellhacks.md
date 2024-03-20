# PowerShell Hacks

The following is a list of hacks that I've used to make the use of PowerShell better in certain situations. 

## PowerShell Paths When Using Folder Redirection
Group Policy is configuring folder redirection for several profile directories, including "Documents" where the default $PSModulePath and $Profile is located.  There has been performance issues when using PowerShell remotely over VPN as it takes PowerShell a while to search $PSModulePath to autoload modules. 

The following PowerShell code seemed to work to change the directory that $PSModulePath points to and improved performance significantly. Setting the $Profile path to local is also included. This is not really polished or significantly tested. Your mileage may vary. 

```
$env:PSModulePath = ($env:PSModulePath).replace("\\naf01b.matc.madison.login\ENHome2\Techservices\JStreeter\Documents\PowerShell\Modules","C:\Users\JStreeter\Documents\PowerShell\Modules")
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