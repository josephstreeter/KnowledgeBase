---
title: Active Directory – Connect to Another Forest with PowerShell
kb_number: KB0011592
version: 3.0
category: Active Directory
author: Joseph Streeter
valid_to: 03-01-2026
last_updated: 01-29-2025 16:38:46
---

## Description

Connect to an Active Directory Forest other than the one that the client host is a member of.

## Details

PowerShell will automatically create a PSDrive for the Active Directory domain that the client is a member of. An additional PSDrive can be created for a different domain in another forest.

## Information

The following command will create a PSDrive for a different domain than the one the host is joined to.

```powershell
New-PSDrive -Name <PSDrive-Name> -PSProvider ActiveDirectory -Server "<Domain-Controller>" -Scope Global c-credential (Get-Credential "<User-Name>") -root "//RootDSE/"
```

The "-Scope Global" switch is required if you run this cmd-let from a script. The new PSDrive can be used in several ways. For example, to connect to the adtest.madisoncollege.edu forest with PowerShell from a host joined to the production ad.madisoncollege.edu forest. The following command will create a PSDrive named "ADTEST" that will be connected to the "adtest.wisc.edu" domain.

```powershell
New-PSDrive -Name ADTEST -PSProvider ActiveDirectory -Server "adtest.madisoncollege.edu" -Scope Global -credential (Get-Credential "ADTEST\<username>") -root "//RootDSE/"
```

To use this PSDrive you can "cd" to the "ADTEST" PSDrive and then run the Active Directory modules as normal:

```powershell
cd ADTEST:
Get-ADDomain
```

The second method is to provide the "server" switch with the name of the domain controller:

```powershell
PS C:\> Get-ADDomain -server "adtest.madisoncollege.edu"
```

The following code will check to see if the drive exists prior to attempting creation of the new PSDrive

```powershell
if (-not(Get-PSDrive TEST))
{
    New-PSDrive -Name ADTEST -PSProvider ActiveDirectory -Server "adtest.madisoncollege.edu" -Scope Global -credential (Get-Credential "ADTEST\<username>") -root "//RootDSE/"
}
Else
{
    "Drive already exists"
}
```

## Additional Information and Follow Up

References:

* [Active Directory Powershell: The Drive is the connection (Active Directory Powershell Blog)](http://blogs.msdn.com/b/adpowershell/archive/2009/03/11/the-drive-is-the-connection.aspx)
* [Using the New-PSDrive Cmdlet (TechNet)](http://technet.microsoft.com/en-us/library/ee176915.aspx)
* [Using the Get-PSDrive Cmdlet (TechNet)](http://technet.microsoft.com/en-us/library/ee176856.aspx)

Contact the the Identity and Access Management Team if you have any questions about the information listed above.
