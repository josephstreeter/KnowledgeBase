---
title: Authentication - Troubleshooting Sign-in Problems (Azure AD)
kb_number: KB0011584
version: 6.0
category: Authentication
author: Joseph Streeter
valid_to: 07-04-2026
last_updated: 06-04-2025 09:54:34
---

## Description

This article provides guidance for troubleshooting a sign-in (authentication) error associated with an application protected by Azure Active Directory (AD). The article explains the types of information that should be collected to properly identify and resolve an authentication error on one's own, or to convey in a Help Desk request if further assistance is required.

## Details

Identifying the cause of an authentication error is important for applying the appropriate solution. Being prepared with as much potentially relevant information as possible when researching the problem - or submitting a Help Desk ticket - can simplify the process and minimize access-interruption and delays.

## Information

**Collecting Information:**

When you are experiencing or assisting with a sign-in error, collect the following information:

  1. **Capture error message**  – Copy and paste (preferred method) or take a screen shot of the error message. Sign-in issues involving Azure AD will show an error code that starts with “AADSTS”

NOTE: Error codes and messages are subject to change. For current information on AADSTS error descriptions, fixes, and some suggested workarounds, visit: [https://learn.microsoft.com/en-us/entra/identity-platform/reference-error-codes](https://learn.microsoft.com/en-us/entra/identity-platform/reference-error-codes)  **_(See below for information on using Microsoft's "Flagged Sign-ins" functionality in order to isolate sign-in attempts and reproduce sign-in errors as needed to obtain a code.)
  2. **Username**  – The username used for the sign-in attempt (e.g., <wwolfpack@madisoncollege.edu>)
  3. **Time**  – The date and time the sign-in error occurred
  4. **Application or applications**  – The application(s) where the user's attempted sign-in resulted in the error. Also provide the URL if applicable.
  5. **Client Application**  – The client application used when the sign-in error occurred (e.g., Outlook 2019, MS Teams, Outlook Mobile, Chrome, Edge)
  6. **Device information**  – Information about the device can assist support staff in resolving your issue

     * Device platform/version (e.g., iPhone 11, Windows 10, etc.)
     * Whether the device is Madison College owned/supported or a personally owned device
     * The location and workstation (if a network computer/thin client) from which the sign-in was attempted
     * If the sign-in was attempted via a virtual network, lab, or desktop
  7. **Additional Info**  – Any other information about the failed sign-in that may assist support-staff (e.g., was there an MFA prompt, did it work in the past, works from one device or another, are multiple users experiencing this issue)
  8. **Reply to follow-up information requests** – Prompt responses to support-staff requests for clarification or additional information will facilitate timely and effective resolutions.

[**Flagging Sign-ins**](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/overview-flagged-sign-ins)

Microsoft has introduced a feature to simplify locating a specific sign-in attempt among the many that may be logged in a given timeframe.  The **flagged sign-in**  feature gives the user the ability to enable flagging after receiving an error message. Doing so logs flagged sign-ins for review, facilitating replication of errors for troubleshooting purposes.

Once the feature is enabled, sign-in attempts made within the subsequent 20 (twenty) minutes will be flagged for review.  Please note, however, that only sign-in events from the same user, on the same browser and client device or computer will be flagged.  The flagging automatically turns off after 20 minutes.

The procedure for utilizing the flagging feature is as follows:

  1. A sign-in attempt results in an error.
  2. User clicks **View details**  in the error page.
  3. In **Troubleshooting details**, click**Enable Flagging**. When flagging is enabled, the display text will read "Disable Flagging."
  4. User closes the browser window.
  5. User opens a new browser window (in the same browser application) and attempts the same sign-in that failed.
  6. User captures the error-code information from the reproduced sign-in.

## Additional Information and Follow Up

If you are unable to resolve the issue on your own, please submit a Help Desk request with the information collected above. This will help us to quickly identify and resolve the sign-in problem.
