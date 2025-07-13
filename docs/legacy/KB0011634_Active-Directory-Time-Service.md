---
title: Active Directory - Time Service
kb_number: KB0011634
version: 2.0
category: Active Directory
author: Joseph Streeter
valid_to: 03-01-2026
last_updated: 01-29-2025 11:50:01
---

## Description

In an Active Directory environment, it is important to keep accurate time. Domain Controllers that are hosted in an virtualized environment are prone to clock drift.

## Details

The Domain Controller that hosts the PDC Emulator role in the forest root domain is an important part of time synchronization for the entire forest. The Domain Controller with the PDCE emulator role should be configured to use a reliable external time source. All other DCs should be configured to use the standard DC method of time synchronization.

A Group Policy Object linked to the Domain Controllers OU will configure Time Synchronization for the PDCE. A WMI filter on the policy will ensure that the policy applies to the PDCE in the event that the PDCE roll is transferred to or seized by another DC. In a Single Forest - Multiple Domain configuration this policy would only have to apply to the PDCE in the Forest Root Domain.

A separate Group Policy Object will configure the time service for all other domain controllers. It is important that the Group Policy Objects are applied in the appropriate order to ensure the PDCE GPO is applied last.

## Information

WMI Filter for PDCE FSMO Roll

Select * from Win32_ComputerSystem where DomainRole = 5
---
Roles 0 = standalone, 1 = Member workstation, 2 = Standalone Server, 3 = Member Server, 4 = Backup domain controller, 5 = Primary domain controller

PDCE Time Service Configuration

Administrative Templates/System/Windows Time Service/Global Configuration Settings – Enabled

    * AnnounceFlags   5

Administrative Templates/System/Windows Time Service/Time Providers/Configure Windows NTP Client – Enabled

    * NtpServer   ntp1.madisoncollege.edu,0x1, ntp2.madisoncollege.edu,0x1
    * Type NTP

Administrative Templates/System/Windows Time Service/Time Providers/Enable Windows NTP Client – Enabled

All Domain Controllers that are not Root Domain PDC Emulator

A Group Policy Object linked to the Domain Controllers OU, other than the Default Domain Controllers policy, will ensure that the default Time Synchronization settings are not changed on the remaining Domain Controllers.

Administrative Templates/System/Windows Time Service/Global Configuration Settings – Enabled

    * AnnounceFlags   10

Administrative Templates/System/Windows Time Service/Time Providers/Configure Windows NTP Client – Enabled

    * NtpServer    ntp1.madisoncollege,0x1, ntp2.madisoncollege,0x1
    * Type NT5DS

Administrative Templates/System/Windows Time Service/Time Providers/Enable Windows NTP Client – Enabled

## Additional Information and Follow Up

If you have any questions about the contents of this article, direct them to the Identity and Access Management Team.
