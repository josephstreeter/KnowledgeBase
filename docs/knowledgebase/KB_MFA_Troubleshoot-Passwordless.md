---
title: Troubleshooting Passwordless Sign-In Issues
kb_number: KB_MFA_Troubleshoot-Passwordless
category: Authentication
version: 1.0
author: IAM Team
valid_to: 01-01-2027
last_updated: 07-12-2025
---

## Description

Common issues and solutions for passwordless sign-in problems.

## Details

Common issues and solutions for passwordless sign-in:

**Issue:** Unable to register a passwordless method

- Ensure your account is eligible for passwordless options (check with IT if unsure).
- Use a supported device and browser (Edge, Chrome, Firefox).
- Clear browser cache and cookies before retrying.
- Disable browser extensions that may block authentication popups.
- Contact IT if options are missing or you see error messages.

**Issue:** Sign-in fails with passwordless method

- Check internet connectivity (Wi-Fi or cellular data must be active).
- Make sure your device or key is registered and active in your security info.
- Try an alternate method if available (Authenticator App, FIDO2 key, SMS).
- Restart your device and browser.
- If using a FIDO2 key, ensure it is inserted/tapped correctly and PIN is entered.

**Issue:** Authenticator App or FIDO2 key not working

- Update the app or key firmware to the latest version.
- Remove and re-add the method in your security info.
- Confirm your device's date and time settings are set to automatic.

**References:**

- [Troubleshoot passwordless sign-in](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-authentication-passwordless-troubleshoot)

## Additional Information and Follow-up

If you continue to experience issues, contact your IT support or refer to related KB articles for setup and troubleshooting.
