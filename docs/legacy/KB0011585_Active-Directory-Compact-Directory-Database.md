---
title: Active Directory - Compact Directory Database
kb_number: KB0011585
version: 4.0
category: Active Directory
author: Joseph Streeter
valid_to: 03-28-2026
last_updated: 02-18-2025 10:27:05
---

## Description

Every 12 hours Active Directory performs garbage collections where it defragments whitespace within the database. This whitespace is optimized for performance, but it is not returned to the file system.

## Details

Garbage Collection Increase the garbage collection logging level from 0 to 1 in order to determine how much whitespace exists in a database. This change in logging level will result in an Event ID 1646 being logged to the Directory Service log. The event will show how much total space is used by the database file and how much recoverable whitespace exists.

Configure Garbage Collection Logging View current setting:

    $Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics"
    Get-ItemProperty -Path $Reg

Set logging level:

    $Reg = "HKLM:\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics"
    Set-ItemProperty -Path $Reg -Name "6 Garbage Collection" -Type DWORD -Value 1

## Information

**Compact (Offline Defragmentation)**  Prepare for Compacting:

Create a folder named "compact" in D:\NTDS.

Open an elevated PowerShell prompt Stop the AD DS Service by typing:
?

    Stop-Service ntds -force

Begin Compacting:

* Enter the command _"ntdsutil"_

* At the ntdsutil prompt, type _"activate instance ntds"_ and press _"ENTER"_  Type _"files"_  and press _"ENTER"_

* To begin compacting the database type _compact to "d:\NTDS\compact_ "

* If compacting completed with errors perform an integrity check (See Perform Integrity Check bellow)

Finish Compacting:

* Rename _"D:\NTDS\ndts.dit"_  _"D:\NTDS\ndts.dit.bk"_  so that it isn't overwritten

* Copy the compacted database file from _"D:\NTDS\compact"_  to _"D:\NTDS\compact"_  by typing _"copy D:\NTDS\compact\ndts.dit D:\NTDS\ndts.dit"_

* Delete all existing log files in _"L:\Logs"_  by typing _"del L:\Logs\\*.logs"_

Perform Integrity Check:

* Enter the command _"ntdsutil"_

At the ntdsutil prompt, type _"activate instance ntds"_  and press _"ENTER"_

* Type _"files"_  and press _"ENTER"_

* To begin the integrity check, type _integrity_

**Database Integrity Check:**

If there are any errors from the integrity check, delete the compacted database file, _"D:\NTDS\ntds.dit"_ , and perform the copy again

Restart AD DS:

Start the AD DS Service by typing ```start-service ntds```.

If successful Event IDs 1000 and 1394 should appear in the "Directory Service" log

If Event IDs 1046 and 1168 appear in the "Directory Service" log check the database integrity again

If the database integrity fails again:

* Stop the AD DS service ```stop-service ntds -force```

* Delete the compacted database file (_"del D:\NTDS\ntds.dit"_)

* Rename the original database file (_"D:\NTDS\ntds.dit.bk"_  to _"D:\NTDS\ntds.dit"_)

* Compact the database

* Rename the original database and copy the compacted database

* Perform integrity check If the integrity check succeeds but errors persist when starting the AD DS service, perform a "semantic database analysis with fixup

## Additional Information and Follow Up

Contact the Help Desk at extension 6666 if you have any questions about the information listed above.
