---
title: Authentication - Troubleshooting Multifactor Authentication
kb_number: KB0011655
version: 4.0
category: Common Problems/Issues
author: Joseph Streeter
valid_to: 07-04-2026
last_updated: 06-13-2025 16:30:16
---

## Description

This document details how to troubleshoot Multifactor Authentication (MFA) methods including via the Microsoft Authenticator mobile app and via SMS text messages.

The information contained in this document comes primarily from Microsoft's best practice recommendations.

## Details

Each student and employee should have two authentication methods configured. Technology Services recommends that the Microsoft Authenticator mobile app be used as the primary method and SMS be used as the secondary method.

## Information

***If the Authenticator app is not receiving prompts or SMS messages are not being delivered:***

* Restart the mobile device
* Make sure that Do Not Disturb is NOT enabled on the mobile device
* Verify that notifications are enabled for the following applications:
  * Authenticator app
  * Text messaging app
  * Phone calls
* Check battery-related settings on the mobile device – Try turning off battery optimization for both the authentication app and messaging app (Battery optimization settings may stop less frequently used apps from remaining active in the background and may affect notifications)
* Make sure the mobile device is getting a sufficient signal – have someone attempt to call or text the user to make sure messages are getting through
* If the user often has signal-related problems, it is recommended that they install and use the Microsoft Authenticator app on the mobile device. The Authenticator app can generate random security codes for sign-in without requiring any cell signal or Internet connection.
* Disable any third-party security apps on the phone and request another verification code to be sent

***User receives “You've hit our limit on verification calls” or “You’ve hit our limit on text verification codes” errors:***

* Use the Authenticator App verification code or try to sign in again in a few minutes – Microsoft may limit repeated authentication attempts that are performed by the same user in a short period of time (This limitation does not apply to the Microsoft Authenticator app or verification code)

***User receives “Sorry, we're having trouble verifying your account" error message:***

* Use the Authenticator App verification code or try to sign in again in a few minutes – Microsoft may limit / block voice or SMS authentication attempts that are performed by the same user, phone number, or organization due to a high number of failed voice or SMS authentication attempts (This limitation does not apply to the Microsoft Authenticator app or verification code)

## Additional Information and Follow Up

Contact the Help Desk at extension 6666 if you have any questions about the information listed above.
