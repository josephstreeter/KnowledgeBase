---
title: IAM Help Desk Tool
kb_number: KB0011587
version: 3.0
category: Middleware
author: Joseph Streeter
valid_to: 03-01-2026
last_updated: 01-29-2025 16:37:56
---

## Description

This is a console application written for Tier I support staff to provide identity and account data for troubleshooting authentication and authorization issues.

This application should run on any domain-joined Windows workstation in our environment. The ability to perform the functions included in this tool are limited to the rights delegated in Active Directory to the account running the tool.

VPN is required if working off campus.

## Details

This application will show identity and account information stored in the IdMS, Active Directory, Azure Active Directory, and Azure AD Identity Protection for a particular user (student or employee). It also provides some basic functionality needed to support simple account issues.

NOTE: Recent changes to a student or employee record will not be visible in the tool until those changes are sent to the IdMS, Active Directory, Azure Active Directory, Exchange Online, etc. There are delays between each system, some within the cloud where we do not have any visibility. For example, a student may enroll at 1:00pm, but not have a mailbox provisioned in Exchange Online for over an hour.

## Information

Install and Run the Application

  1. Download the folder for the latest version of application (2.1.256) from the shared location:

    [https://madisoncollege365-my.sharepoint.com/:f:/g/personal/jstreeter_madisoncollege_edu/EoYZbr-mfWROmMgGbVJklmAB0NEL-1oD0MeD09rZdtobzQ?e=PRX9EI](https://madisoncollege365-my.sharepoint.com/:f:/g/personal/jstreeter_madisoncollege_edu/EoYZbr-mfWROmMgGbVJklmAB0NEL-1oD0MeD09rZdtobzQ?e=PRX9EI)

    ![](/sys_attachment.do?sys_id=800c62f21b57d2909446975b234bcbcb)

  2. Extract the files from the downloaded archive file and execute the setup.exe file. (NOTE: if you have a previous version installed you may have to uninstall it from the Control Panel)

    ![](/sys_attachment.do?sys_id=0c0ca2f21b57d2909446975b234bcbeb)

  3. Click the “Start” button or press the “Windows” key and begin typing helpdesk. The application will appear in the search results.
  4. Execute the application (HelpDeskToolv2.exe) by clicking it in the search results (Pin the application to the task bar for easier access).

Using the Application

  1. Click the “Start” button or press the “Windows” key and begin typing helpdesk. The application will appear in the search results.
  2. Execute the application (HelpDeskToolv2.exe) by clicking it in the search results (Pin the application to the task bar for easier access).
  3. When prompted, enter the user's UserID, Employee/Student ID, or Display Name and press Enter.
   | ![](/sys_attachment.do?sys_id=000c62f21b57d2909446975b234bcbcd)
  4. If the user is found, the application will display the identity information for the user.

If there are multiple matches to the display name that is entered, they will all be displayed. Enter the number associated with the entry that you want, and press Enter.

![](/sys_attachment.do?sys_id=000ca2f21b57d2909446975b234bcbe8)

Identity Data

![](/sys_attachment.do?sys_id=900ca2f21b57d2909446975b234bcbf5)

The application will return information identity information.

* UserID:  The user’s given name
* First Name: The user’s legal given name – this name does not represent a preferred name entered into WorkDay by an employee. If a student has entered a preferred name in Campus Solutions it will be represented here.
* Last Name: The user’s legal surname – this name does not represent a preferred name entered into WorkDay by an employee.
* Date of Birth: The user’s date of birth

  ![](/sys_attachment.do?sys_id=100ca2f21b57d2909446975b234bcbf7)

* Title: The user’s primary position title
* Manager: The user’s primary position manager
* Employee Type: The user’s primary position employee Type
  * S = Student
  * A = Administration
  * E = Staff
  * C = Consultant
  * F = Faculty
  * I = Tech Services
* Employee Status: The user’s primary position Employee Status.
  * P = Future
    * Students – Created an account, but have not enrolled
    * Employees – Hired by the organization, but have not started
  * A = Active
  * D = Inactive
    * Employee – Terminated
    * Student – Future use
  * X = De-provision
    * Future use, account will be deleted – currently this is likely an account created by a hacker
  * Employee Override: Used to override the user’s Employee Status
  * Employee ID: The user’s Employee or Student ID
  * Employee Number: The immutable ID for the user
  * Retired/Alumni: Represents retirement status of employees or Alumni status for students (Alumni status not currently implemented.)
  * Term Number: Represents a student’s most recent term number (May be a future term)

    ![](/sys_attachment.do?sys_id=040ca2f21b57d2909446975b234bcbe4)

  * Work Phone: The user’s assigned DN
  * Personal Phone: The user’s personal phone number as entered into WorkDay.
  * Work Email: The user’s assigned Madison College email address
  * Personal Email: The user’s personal email address as entered into WorkDay or Campus Solutions (NOTE: should not be a madisoncollege.edu address)

Use the options at the bottom of the window to navigate to information from other applications

  ![](/sys_attachment.do?sys_id=c00c62f21b57d2909446975b234bcbc9)

* A = View and manage Active Directory user object
* C = View Azure Active Directory user object
* P = PWM Activation/Challenge Questions
* B = Enter a new UserID or Employee/Student ID
* Q = Quit

Active Directory Information

Lists data associated with the user’s Active Directory user object.

![](/sys_attachment.do?sys_id=8c0ca2f21b57d2909446975b234bcbe9)

* Sam Account Name:  User’s UserID
* User Principal Name: User’s UPN
* Distinguished Name: Location of user object in AD
* Description: User’s description as it appears in AD
* Email: SMTP email address for user if mailbox is assigned
* Enabled: Active Directory user object is enabled or disabled
* Locked: Active Directory user object is locked due to repeated authentication failures
* Bad Pwds: The count of bad passwords entered
* Last Bad Attempt: Timestamp of the last bad password attempt
* Last Login: Timestamp for Last successful login
* Pwd Last Set: Timestamp for last password set
* Pwd Expiration Date: Password Expiration Date. May be used for forced terminations, but isn’t frequently used anymore.
* Object Creation: Active Directory user object’s whenCreated timestamp.
* Object Updated: Active Directory user object’s whenChanged timestamp.
* Hidden from GAL: Active Directory user object’s MsExchHideFromAddressBook attribute. Prospective students and inactive retired employees will be set to ‘true.’

  ![](/sys_attachment.do?sys_id=8c0c62f21b57d2909446975b234bcbce)

* Reset Password: Prompts for a new password and sets the provided string as the user object’s new password. (Note: To be used only in cases where the user cannot perform a reset using PWM or Azure SSPR)
* Unlock Account: Unlocks an account that is locked because of excessive logon failures.
* Refresh: Refreshes the data displayed in the tool.
* Enable Account: Enables the user object (Not all users will have rights to execute this function.)
* Disable Account: Disables the user object (Not all users will have rights to execute this function.)
* Enter new UserID: Retrieve data from a different user.
* Remove expiration: Remove an account expiration set on a user object.

Azure Active Directory Information

Lists data associated with the user’s Active Directory user object.

  ![](/sys_attachment.do?sys_id=940ca2f21b57d2909446975b234bcbf1)

* Display Name:  User’s display name as it appears in AAD
* First Name: User’s given name
* Last Name: User’s surname
* User Principal Name: User’s UPN
* Employee ID: The user’s employee or student ID
* Job Title: User’s job title as it appears in AAD
* Office Location: The user’s office location
* Enabled: Active Directory user object is enabled or disabled
* Last Password Change: Timestamp for last password set
* Last Sync Time: Timestamp for the last time the user object was synchronized from Active Directory
* Email: SMTP email address for user if mailbox is assigned
* Show in Address: If the user is configured to show in the Global Address List. Prospective students and inactive retired employees will be set to ‘false.’
* User Type: The type of user object. Will be “Member” or null for users in the organization or “Guest” for guest users that have been invited.
* Proxy Addresses: A list of the email addresses assigned to the user’s mailbox.

  ![](/sys_attachment.do?sys_id=840ca2f21b57d2909446975b234bcbe2)

* (F) Refresh: Refreshes the data displayed in the tool.
* (M) MFA Methods: View and manage Azure MFA methods
* (I) ID Protection: View Azure AD Identity Protection information
* (S) Sign-in Activity: lists Azure AD Sign-in Activity
* (E) Entitlements: Office 365 related licenses
* (B) Back to ID Info: Return to the Identity Information

PWM information

  ![](/sys_attachment.do?sys_id=800ca2f21b57d2909446975b234bcbe6)

* Activation Status: The PWM activation status

  * Activated = User is activated by PWM
  * No Activated = User is not activated by PWM
  * N/A = No data in AD (Most existing students will be N/A despite being activated in PWM)
* Challenge Q/A set: The user has Challenge questions and answers set in PWM

  * True = Challenge question exist in PWM
  * False = Challenge question does not exist in PWM
* Remove Activation: (future) Remove user’s entries from PWM

Entitlements

![](/sys_attachment.do?sys_id=140ca2f21b57d2909446975b234bcbf3)

Lists the licenses that are either direct assigned or assigned via Group Based Licensing (GBL) and the individual features of each license that are enabled. Disabled features are not shown.

Multi-factor Authentication (MFA)

![](/sys_attachment.do?sys_id=880ca2f21b57d2909446975b234bcbed)

Lists all methods that a user has configured.

* Phone: A phone number for One-way SMS and Two-way Voice used as a second authentication factor and Self-Service Password Reset
* Device: Microsoft Authentication application configured for the user’s account on a mobile device used as a second authentication factor

## Additional Information and Follow-up

[Additional information and follow-up steps needed]
