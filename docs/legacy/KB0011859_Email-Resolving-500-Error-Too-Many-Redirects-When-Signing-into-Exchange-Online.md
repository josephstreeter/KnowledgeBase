---
title: Email - Resolving 500 Error "Too Many Redirects" When Signing into Exchange Online
kb_number: KB0011859
version: 1.0
category: Email
author: Joseph Streeter
valid_to: 04-04-2026
last_updated: 03-12-2025 17:15:39
---

## Description

Users may encounter a "500 Error: Too Many Redirects" message when attempting to sign into Exchange Online. This error typically occurs due to misconfigurations related to user settings, admin roles, or mailbox properties.

## Details

Several factors can cause this error, including:

1. Incorrect Date/Time Settings
   * A significant time skew between the user’s computer and the Office 365 servers can trigger redirect issues.
   * To check and adjust date/time settings:
2. Right-click the clock in the bottom right corner of the taskbar.
   2. Select Adjust date/time.
   3. Ensure the date, time, and time zone are correct. Enable "Set time automatically" if possible.
3. Too Many Admin Roles Assigned
   * If a user has been assigned multiple licenses or administrative roles in Office 365, the portal may enter an endless redirect loop.
   * To resolve this an admin must review assigned/active roles. Some roles may be changed from active assigned to eligible or removed.
4. OWA (Outlook Web Access) Not Enabled
   * If OWA is disabled for the user’s mailbox, the redirect loop may occur.
   * Admins can verify and update OWA settings using PowerShell:
   * Check OWA Status:

   ```powershell
   Get-CASMailbox -Identity <user>
   ```

   * Enable OWA and Related Services:

   ```powershell
   Set-CASMailbox -Identity <user> -OWAEnabled $true -ImapEnabled $true -MAPIEnabled $true
   ```

## Information

If the issue persists after verifying the above settings, consider the following steps:

1. Clear Browser Cache: Remove cookies and cached data from the user's browser.
2. Test in Incognito/Private Browsing: Check if the issue persists in a private browsing session.

   ```powershell
   Set-CASMailbox -Identity <user> -OWAEnabled $true -ImapEnabled $true -MAPIEnabled $true
   ```

## Additional Information and Follow-up

* If the issue remains unresolved, escalate to the Identity and Access Management team with the following details:
  * Affected user’s UPN (User Principal Name)
  * Date and time of the issue
  * Any error codes associated with the 500 error
