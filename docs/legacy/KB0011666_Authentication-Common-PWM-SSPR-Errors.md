---
title: Authentication - Common PWM SSPR Errors
kb_number: KB0011666
version: 5.0
category: Authentication
author: Joseph Streeter
valid_to: 07-04-2026
last_updated: 06-03-2025 11:06:39
---

## Description

PWM is a password registration and Self-Service Password Reset (SSPR) application. PWM is used to allow a new user to set their initial password, change a known password, or securely reset an unknown password.

## Details

A user may encounter a number of common error messages when using PWM. The following list will help explain those errors and methods that can be used to fix them.

## Information

### Unable to find username

This can happen if the Active Directory user object has not been created yet. There is a good chance that there is something wrong with the record in Campus Solutions or there was a failure to create the user object by the IdMS.

### PWM 5021: Your account is not eligible for activation:

A user can activate or register your account one time. This error is an indication that the user has already activated. The user should use the forgotten password option to access Password Self-Service if the password is not known.

### PWM 5023: Maximum login attempts for your userID have been exceeded. Try again later

Password Self-Service has a lockout feature that locks access for a period of 6 minutes. Please wait for the lock to clear.

### PWM 5024: Maximum login attempts for ip address have been exceeded. Try again later

Password Self-Service has protection features to prevent someone from attempting to brute force access a list of accounts from the same computer. This lock clears on its own after 30 minutes.

### PWM 5025: Maximum login attempts for this session have been exceeded. Try again later

Try closing and re-opening your browser, using a different browser, start a private browsing/incognito session, or waiting for the session to expire.

### PWM 5034: Invalid Form ID

The web browser presented an invalid link. Try clearing your web browser's cache, closing and re-opening your browser, using a different browser, or start a private browsing/incognito session.

### PWM 5063: A security violation has occurred.   Please try again later

This error can happen if the password self-service session is invalid or expired but your browser tries to use it anyway. Try closing and re-opening your browser your browser, using a different browser, or start a private browsing/incognito session.

### PWM 5065: Account is disabled

This error will happen if you try to log in or reset a forgotten password when your user object is disabled. See the information near the top of this article regarding access.

### PWM 5069: Maximum login attempts for your userID have been exceeded. Try again later

Please wait an hour for the lock to clear.

### PWM 5090: Your account hasn't been configured for this option...

This happens if you attempt to use the Forgotten Password option but do not have any recovery methods (secret questions, SMS phone, or alternate email) set up yet. Activate/Register your account or contact the Help Desk and verify your identity for additional assistance.

### I can't enter my username for Forgotten Password

If you repeatedly get error 5090 (above), you need to quit and restart your browser, try a different browser, or wait 5 minutes for your visitor session to expire.

## Additional Information and Follow Up

If you have any questions about the contents of this article, direct them to the Identity and Access Management Team.
