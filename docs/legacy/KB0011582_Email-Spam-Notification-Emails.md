---
title: Email - Spam Notification Emails
kb_number: KB0011582
version: 5.0
category: Email
author: Joseph Streeter
valid_to: 03-01-2026
last_updated: 01-29-2025 16:44:07
---

## Description

Technology Services is constantly improving our security when it comes to email-based threats. Improvements to our policies have reduced the number of successful phishing attacks across the organization. However, these improvements have also increased the potential for legitimate emails to be prevented from being delivered.

## Details

In order to mitigate the loss of legitimate emails that are inappropriately categorized as spam, we will be enabling a feature that will send a Spam Notification email to users who have messages that were quarantined instead of being delivered.

## Information

The Spam Notification email contains the following information:

    ![](/sys_attachment.do?sys_id=8fccea361b57d2909446975b234bcb3f)

* The number of quarantined messages listed and the date of the last message in the list
* A link to the Quarantine Page where all of the messages sent to quarantine can be viewed
* A list of messages intended for your mailbox that were quarantined instead of being delivered and information about each message:

  * Sender – The sender’s name and email address of the quarantined message
  * Subject – The subject line text of the quarantined message
  * Date – The date and time (in UTC) that the message was quarantined
  * Actions – The actions that you are able to perform for that message

        ![](/sys_attachment.do?sys_id=03ccea361b57d2909446975b234bcb3e)

The actions available to you for each message will depend on how the message was categorized by Microsoft:

| Action  | Description | Available for Categories   |
|---------|-------------|----------------------------|
| Release | Releases the message from quarantine so that it will be delivered to the inbox | Spam, Bulk, Phishing                         |
| Request Release | Sends a request to admins to release the message from quarantine | High Confidence Spam, High Confidence Phishing |
| Review | Displays details about the message | All |

If an action, such as Release, is not available, this is due to the Microsoft categorization. It will require an administrator to review via Request Release.

The Quarantine Page (<https://security.microsoft.com/quarantine>) will show all of the messages that are currently quarantined for your mailbox and allow the recipient (you) to perform the same tasks that can be done from the email.

    ![](/sys_attachment.do?sys_id=07ccea361b57d2909446975b234bcb3b)

## Additional Information and Follow Up

Contact the Help Desk at extension x6666 if you have any questions about the information listed above.
