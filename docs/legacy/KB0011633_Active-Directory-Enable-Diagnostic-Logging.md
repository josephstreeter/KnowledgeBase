---
title: Active Directory - Enable Diagnostic Logging
kb_number: KB0011633
version: 5.0
category: Active Directory
author: Joseph Streeter
valid_to: 03-01-2026
last_updated: 01-23-2025 12:00:00
---

## Description

This article provides comprehensive guidance on enabling and configuring diagnostic logging for Active Directory Domain Services (AD DS) and related components. Diagnostic logging is essential for troubleshooting domain controller issues, monitoring replication, and analyzing authentication problems in Active Directory environments.

Proper diagnostic logging configuration enables administrators to capture detailed information about Active Directory operations, helping to identify and resolve issues related to authentication, replication, LDAP operations, and other critical domain services. Understanding how to enable, configure, and manage these logs is crucial for maintaining a healthy Active Directory infrastructure.

**Use Cases:**

- Troubleshooting domain controller replication issues
- Diagnosing authentication and authorization problems
- Monitoring LDAP query performance and errors
- Investigating security-related events in Active Directory
- Analyzing network connectivity and communication issues between domain controllers

## Details

### Active Directory Diagnostic Logging Registry Location

Diagnostic logging for domain controllers is centrally managed through the Windows Registry at:

```text
HKLM\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics
```

Each diagnostic category is controlled by a specific REG_DWORD entry that determines the verbosity level of logging for that particular service or component.

### Diagnostic Logging Categories

The following table lists all available diagnostic logging categories and their corresponding registry entry IDs:

| Entry ID | Service | Description |
|----------|---------|-------------|
| 1 | Knowledge Consistency Checker (KCC) | Monitors replication topology generation and maintenance |
| 2 | Security Events | Tracks security-related operations and authentication events |
| 3 | ExDS Interface Events | Logs Exchange Directory Service interface operations |
| 4 | MAPI Interface Events | Records Messaging Application Programming Interface activities |
| 5 | Replication Events | Monitors domain controller replication activities |
| 6 | Garbage Collection | Tracks cleanup operations for deleted objects |
| 7 | Internal Configuration | Records internal configuration changes and operations |
| 8 | Directory Access | Logs directory access and query operations |
| 9 | Internal Processing | Monitors internal AD DS processing activities |
| 10 | Performance Counters | Records performance-related metrics and counters |
| 11 | Initialization/Termination | Tracks service startup and shutdown events |
| 12 | Service Control | Logs service control operations and management activities |
| 13 | Name Resolution | Monitors DNS and NetBIOS name resolution activities |
| 14 | Backup | Records backup and restore operations |
| 15 | Field Engineering | Advanced debugging information for Microsoft support |
| 16 | LDAP Interface Events | Logs LDAP protocol operations and queries |
| 17 | Setup | Records installation and configuration activities |
| 18 | Global Catalog | Monitors Global Catalog operations and queries |
| 19 | Inter-site Messaging | Tracks communication between Active Directory sites |
| 20 | Group Caching | Logs universal group membership caching activities |
| 21 | Linked-Value Replication | Monitors linked attribute replication (group memberships) |
| 22 | DS RPC Client | Records outbound RPC operations from domain controller |
| 23 | DS RPC Server | Logs inbound RPC operations to domain controller |
| 24 | DS Schema | Tracks schema-related operations and modifications |

### Diagnostic Logging Levels

Each diagnostic category can be configured with different verbosity levels, ranging from minimal logging to extensive debugging information:

| Value | Level | Description | Performance Impact | Recommended Use |
|-------|-------|-------------|-------------------|-----------------|
| 0 | None | Only critical events and error events are logged | Minimal | Default production setting |
| 1 | Minimal | Very high-level events and major task completions | Low | Initial troubleshooting when problem location is unknown |
| 2 | Basic | Moderate level of detail with operational information | Low | General monitoring and basic troubleshooting |
| 3 | Extensive | Detailed information including task steps and processes | Medium | Targeted troubleshooting when problem area is identified |
| 4 | Verbose | Comprehensive logging with detailed operational data | High | Advanced troubleshooting requiring detailed analysis |
| 5 | Internal | Complete logging including debug strings and all configuration changes | Very High | Deep troubleshooting for specific categories only |

### Performance and Storage Considerations

**Important Warnings:**

- **Levels 4-5**: Should only be used temporarily and for specific troubleshooting scenarios
- **Production Impact**: High verbosity logging can significantly impact domain controller performance
- **Storage Requirements**: Extensive logging can generate large volumes of log data rapidly
- **Monitoring**: Always monitor disk space when enabling verbose logging

**Best Practices:**

- Enable verbose logging only for specific categories related to the problem
- Set logging back to level 0 or 1 after troubleshooting is complete
- Monitor Event Log sizes to prevent disk space issues
- Consider log rotation and archival strategies for extended troubleshooting periods

## Information

### View Current Logging Levels with PowerShell

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics"
Get-ItemProperty -Path $Reg
```

### Configure with PowerShell

Use the following PowerShell example to configure logging levels:

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics"
Set-ItemProperty -Path $Reg -Name <service> -Type DWORD -Value <value>
```

**Example: Enable verbose replication logging:**

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics"
Set-ItemProperty -Path $Reg -Name "5 Replication Events" -Type DWORD -Value 3
```

### Netlogon Logging Configuration

**After enabling Netlogon logging** the activity will be logged to `%windir%\debug\netlogon.log`. Depending on the amount of activity you may want to increase the size of this log from the default 20 MB. When the file reaches 20 MB, it is renamed to Netlogon.bak, and a new Netlogon.log file is created.

The size of the Netlogon.log file can be increased by changing the MaximumLogFileSize registry entry. This registry entry does not exist by default.

**Configure log size with PowerShell:**

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters"
New-ItemProperty -Path $Reg -Name MaximumLogFileSize -Type DWORD -Value <log-size>
```

**Configure log size with Group Policy:**

Computer Configuration\Administrative Templates\System\Net Logon\Maximum Log File Size

### Turn on NetLogon Logging

**Command Line:**

```cmd
nltest /dbflag:0x2080ffff
```

***Note: `0x2080ffff` enables verbose logging for Netlogon, which includes all events and debug information.***

**PowerShell:**

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters\"
Set-ItemProperty -Path $Reg -Name DBFlag -Type DWORD -Value 545325055

Restart-Service netlogon
```

### Turn off NetLogon Logging

**Command Line:**

```cmd
nltest /dbflag:0x0
```

**PowerShell:**

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters\"
Set-ItemProperty -Path $Reg -Name DBFlag -Type DWORD -Value 0

Restart-Service netlogon
```

## Additional Information and Follow-up

### Troubleshooting Tips

**Common Issues and Solutions:**

1. **Registry Access Denied**: Ensure you have administrative privileges on the domain controller
2. **Changes Not Taking Effect**: Some diagnostic settings may require a restart of the Active Directory Domain Services service
3. **Log File Location**: Diagnostic events are written to the Directory Service event log (Event ID 1644 and others)
4. **Performance Impact**: Monitor CPU and disk I/O when enabling verbose logging levels

### Event Log Locations

- **Directory Service Log**: Applications and Services Logs > Directory Service
- **System Log**: Windows Logs > System
- **Security Log**: Windows Logs > Security
- **Netlogon Log**: `%windir%\debug\netlogon.log`

### PowerShell Script Examples

**Reset all diagnostic logging to default (0):**

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics"
1..24 | ForEach-Object {
    Set-ItemProperty -Path $Reg -Name "$_" -Type DWORD -Value 0
}
```

**Enable replication troubleshooting logging:**

```powershell
$Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics"
# Enable replication events (5) and KCC (1) at extensive level
Set-ItemProperty -Path $Reg -Name "5 Replication Events" -Type DWORD -Value 3
Set-ItemProperty -Path $Reg -Name "1 Knowledge Consistency Checker" -Type DWORD -Value 3
```

### References

- [Microsoft Documentation: Active Directory Diagnostic Logging](https://docs.microsoft.com/en-us/troubleshoot/windows-server/identity/configure-ad-and-lds-event-logging)
- [Microsoft Support: How to Enable Active Directory Diagnostic Event Logging](https://support.microsoft.com/en-us/help/314980)
- [Microsoft Docs: Netlogon Service](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc778026(v=ws.10))
- [TechNet: Active Directory Replication and Topology Management Using Windows PowerShell](https://docs.microsoft.com/en-us/powershell/module/addsadministration/)
- [Microsoft Learn: Troubleshoot Active Directory replication problems](https://docs.microsoft.com/en-us/troubleshoot/windows-server/identity/troubleshoot-ad-replication-problems)
- [Microsoft Docs: Active Directory Event IDs](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/active-directory-event-ids)
