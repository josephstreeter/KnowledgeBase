# PowerShell - Active Directory
---

Remove ACE from a list of object's ACL for a security principal
```
function Remove-ADObjectACE()
{
    [CmdletBinding()]
    Param
    (
        $ADObject,
        $SecGroup
    )

    Write-Output ("Removing {0} from {1}" -f $SecGroup, $ADObject.name)
    Try
    {
        $Acl=(get-acl -path $ADObject.distinguishedname)
        $Ace = $Acl.access | ?{ $_.IsInherited -eq $false -and $_.IdentityReference -eq $SecGroup }
        if ($Ace)
        {
            $Acl.RemoveAccessRule($ace)
            Set-Acl -Path $Group.DistinguishedName -AclObject $Acl -ErrorAction Stop
            Return
        }
        else
        {
            Write-Output ("No ACL to remove from {0}" -f $ADObject.name)
        }
    }
    catch
    {
        Write-Error $_.exception.message
    }
}


$SecGroup = "AD\Domain Admins"
$Groups = Get-ADGroup -Filter * -SearchBase "OU=groups,OU=managed,DC=ad,DC=domain,DC=com"

foreach ($Group in $Groups)
{
    Remove-ADObjectACE -ADObject $Group -SecGroup $SecGroup -ErrorAction Stop
}
```