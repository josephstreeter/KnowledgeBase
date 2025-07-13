---
title: Active Directory – Reset DSRM Password
kb_number: KB0011590
version: 3.0
category: Active Directory
author: Joseph Streeter
valid_to: 03-28-2026
last_updated: 02-18-2025 10:32:31
---

## Description

This document contains the steps to reset the DSRM Password for Active Directory domain controllers

## Details

The Directory Service Restore Mode password is set on each Domain Controller during the dcpromo process and is not replicated. If a DSRM password for a domain controller is not known, it could be reset using the following procedure.

## Information

In WS 2003 and later the Domain Controller does not have to be booted into Restore Mode to change the DSRM password when using the ntdsutil command. This allows you to run the command against remote Domain Controllers as well.

    > ntdsutil
    > set dsrm password
    > reset password on server null
    > <Enter New DSRM Password>
    > <Confirm New DSRM Password>
    > q
    > q

## Additional Information and Follow Up

Contact the Identity and Access Management Team if you have any questions regarding the contents of this document.
