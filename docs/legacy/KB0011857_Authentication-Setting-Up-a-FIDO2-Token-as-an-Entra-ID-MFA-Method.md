---
title: Authentication - Setting Up a FIDO2 Token as an Entra ID MFA Method
kb_number: KB0011857
version: 1.0
category: Authentication
author: Joseph Streeter
valid_to: 04-04-2026
last_updated: 03-12-2025 17:15:10
---

## Description

FIDO2 security tokens provide a secure, phish-resistant, and convenient way to authenticate with Microsoft Entra ID. This method is an alternative for students and employees who cannot use SMS or the Microsoft Authenticator app for multi-factor authentication (MFA). Tokens are available for purchase at campus bookstores, and guidance on acquiring and setting up a token can be obtained from the Technology Services Help Desk, Student Help Desk, or the Bookstore.

---

## Details

***Why Use Multiple MFA Methods?***

It is highly recommended to configure multiple MFA methods to prevent being locked out of your account. If your primary authentication method is lost, unavailable, or compromised, having an alternative ensures you can still access your account and maintain security. A FIDO2 token serves as a reliable backup, especially in situations where mobile authentication is not an option.

***Why SMS is Not Recommended for MFA***

While SMS-based authentication is commonly used, it is not the most secure method. Security risks associated with SMS MFA include:

* SIM Swapping Attacks: Attackers can fraudulently transfer a victim’s phone number to a different SIM card, intercepting authentication messages.
* Phishing Attacks: Users may be tricked into providing their one-time SMS codes to attackers through fake login pages.
* Message Interception: SMS messages can sometimes be intercepted via vulnerabilities in mobile networks, making them susceptible to exploitation.

FIDO2 security tokens are a superior alternative because they are resistant to phishing attacks and do not rely on network-based authentication, offering a more secure and reliable MFA method. By using a FIDO2 security token, users benefit from hardware-based authentication that is resistant to phishing because it does not transmit authentication data that can be intercepted. Unlike SMS or app-based codes, which can be phished or stolen, FIDO2 tokens authenticate directly with the service provider, ensuring a higher level of security and reducing the risk of credential theft. Additionally, since FIDO2 tokens do not rely on network security, they are not vulnerable to SIM-swapping or other mobile network-based attacks.

---

## Information

***Setting up Security Key Method:***

  1. Acquire a FIDO2 Token
     * Visit the campus bookstore to purchase a FIDO2 token.
     * If the token was not acquired the college, ensure the token is compatible with Microsoft Entra ID.
  2. Register the FIDO2 Token
     * Sign in to the [Microsoft Security Info](https://mysignins.microsoft.com/security-info) page.
     * Click Add sign-in method.

      ![A sign in to sign in to accountAI-generated content may be incorrect.](/sys_attachment.do?sys_id=86e2c4f487d46e9033808489cebb3529)

  3. Select Security Key.

      ![A screenshot of a login pageAI-generated content may be incorrect.](/sys_attachment.do?sys_id=4ae2c07487d46e9033808489cebb35b0)

  4. You will be asked to sign in with an MFA method. Complete the authentication process using an existing method.

      ![A screenshot of a computerAI-generated content may be incorrect.](/sys_attachment.do?sys_id=35e2c07487d46e9033808489cebb3540)

  5. Choose USB device or NFC device, depending on your token type. Most devices will likely be USB type A or C.

      ![A screenshot of a computerAI-generated content may be incorrect.](/sys_attachment.do?sys_id=65e280b487d46e9033808489cebb35c8)

  6. Follow the on-screen instructions to insert or tap your token and complete the setup.

      ![](/sys_attachment.do?sys_id=a5e2c0f487d46e9033808489cebb354b)

  7. Select Use External Security Key from the pop-up menu.

      ![](/sys_attachment.do?sys_id=31e284f487d46e9033808489cebb35de)

  8. Click OK on the “Security key setup” pop-up.

      ![](/sys_attachment.do?sys_id=fde2483487d46e9033808489cebb3562)

  9. Click OK on the “Continue setup” pop-up.

      ![](/sys_attachment.do?sys_id=31e24cb487d46e9033808489cebb35c3)

  10. If this is the first time setting up this token you will be asked to set and confirm a pin. If this is not the first time the token is set up, enter the pin configured for this device.

      ![](/sys_attachment.do?sys_id=f1e2c0b487d46e9033808489cebb3508)

  11. When prompted to touch the security key, the device should be flashing.

      ![](/sys_attachment.do?sys_id=f1e244f487d46e9033808489cebb35a8)

  12. At the prompt, enter a descriptive name for the token.

      ![](/sys_attachment.do?sys_id=02e284f487d46e9033808489cebb35be)

  13. Test the Token
     *Sign out and attempt to sign in using your FIDO2 token.
     * If successful, your token is now a registered MFA method.
  14. Configure Backup MFA Methods
     * Ensure you have at least one additional MFA method, such as a backup FIDO2 token or an authentication app, in case of device loss.

## Additional Information and Follow-up

FIDO2 tokens can also be used for non-college services such as Facebook, Google, GitHub, and other platforms that support FIDO2 authentication. Additionally, personal FIDO2 tokens can be used for authentication, provided they are compatible with Entra ID.

* If you encounter issues setting up or using your FIDO2 token, contact the Technology Services Help Desk or Student Help Desk for assistance.
* Lost or malfunctioning tokens should be reported immediately so alternative authentication options can be configured.
* Refer to the [Microsoft Documentation](https://learn.microsoft.com/en-us/security/identity-protection/) for further information on secure authentication practices.

By setting up a FIDO2 token as an Entra ID MFA method, you enhance security and minimize risks associated with less secure authentication methods.

FIDO2 tokens can also be used for non-college services such as Facebook, Google, GitHub, and other platforms that support FIDO2 authentication. Additionally, personal FIDO2 tokens can be used for authentication, provided they are compatible with Entra ID.

* If you encounter issues setting up or using your FIDO2 token, contact the Technology Services Help Desk or Student Help Desk for assistance.
* Lost or malfunctioning tokens should be reported immediately so alternative authentication options can be configured.
* Refer to the [Microsoft Documentation](https://learn.microsoft.com/en-us/security/identity-protection/) for further information on secure authentication practices.

By setting up a FIDO2 token as an Entra ID MFA method, you enhance security and minimize risks associated with less secure authentication methods.
