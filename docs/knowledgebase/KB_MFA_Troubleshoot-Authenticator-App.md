---
title: Troubleshooting Microsoft Authenticator App Issues
kb_number: KB_MFA_Troubleshoot-Authenticator-App
category: Authentication
version: 1.0
author: IAM Team
valid_to: 01-01-2027
last_updated: 07-12-2025
---

## Description

Common issues and solutions for the Microsoft Authenticator App.

## Details

Common issues and solutions for the Microsoft Authenticator App:

**Issue:** App not receiving notifications

- Ensure push notifications are enabled for the app in your device settings (iOS: Settings > Notifications > Authenticator; Android: Settings > Apps > Authenticator > Notifications).
- Check internet connectivity (Wi-Fi or cellular data must be active).
- Restart your device to refresh app services.
- Make sure battery saver or "Do Not Disturb" mode is not blocking notifications.
- Confirm the app is running in the background and not force-closed.

**Issue:** Unable to add account

- Make sure you scan the correct QR code from your organization's security portal.
- Update the app to the latest version via the App Store or Google Play.
- Try removing and re-adding the account in both the app and your security portal.
- Clear the app cache (Android: Settings > Apps > Authenticator > Storage > Clear Cache).
- If using work/school accounts, ensure your device is registered and compliant with company policies.

**Issue:** App not generating codes or codes not accepted

- Check your device's date and time settings; set to automatic to avoid time drift.
- Remove and re-add the account to resync codes.
- Update the app to the latest version.

**References:**

- [Troubleshoot Authenticator App](https://support.microsoft.com/en-us/account-billing/troubleshoot-the-microsoft-authenticator-app-5b7c7e93-0c7b-4a4a-8e8c-25c1b1b0a7a6)
- [Microsoft Authenticator FAQ](https://learn.microsoft.com/en-us/azure/active-directory/user-help/user-help-auth-app-faq)

## Additional Information and Follow-up

Contact IT support for persistent issues, device recovery, or if you cannot access your accounts.
