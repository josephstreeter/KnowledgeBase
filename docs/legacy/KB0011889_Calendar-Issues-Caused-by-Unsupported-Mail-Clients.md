---
title: Calendar Issues Caused by Unsupported Mail Clients
kb_number: KB0011889
version: 1.0
category: Email
author: Joseph Streeter
valid_to: 07-04-2026
last_updated: 06-04-2025 09:56:24
---

## Description

Users may encounter unexpected calendar behavior in Exchange Online, such as repeated meeting declines, duplicate responses, or lingering Out of Office (OOO) actions. These issues are often linked to the use of **unsupported mail clients**  that do not fully integrate with Exchange Online’s calendar and mailbox processing features.

## Details

Exchange Online relies on consistent and accurate synchronization between the mailbox and the client application. When users access their mailbox through unsupported clients—such as the native iOS Mail App or third-party email apps—calendar-related actions (e.g., meeting responses, OOO behavior) may not sync correctly. This can result in:

    * Repeated or delayed meeting declines
    * Calendar spam to meeting organizers
    * OOO messages being sent outside the configured time window
    * Inconsistent calendar state across devices

These issues typically occur when the unsupported client caches outdated mailbox data or attempts to process calendar items after a period of disconnection or inactivity.

## Information

To ensure reliable calendar functionality and full support from IT, users must access their Exchange Online mailbox using one of the following **supported mail clients** :

    * **Outlook Desktop App**  (Windows or macOS)
    * **Outlook Mobile App**  (iOS and Android)
    * **Outlook on the Web**(OWA)

Use of unsupported clients, including the **iOS native Mail App**,**legacy ActiveSync clients**, or**third-party email apps** , is discouraged for calendar management and OOO configuration.

**Additional Information and Follow-up**

**Recommended Actions:**

    * Users experiencing calendar issues should:
      * Remove and re-add their Exchange account on unsupported clients.
      * Switch to a supported client for all calendar and OOO-related tasks.
    * Users are encouraged to configure OOO settings and manage meetings only through supported clients to avoid sync issues.


