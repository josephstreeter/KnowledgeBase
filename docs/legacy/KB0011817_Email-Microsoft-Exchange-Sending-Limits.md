---
title: Email - Microsoft Exchange Sending Limits
kb_number: KB0011817
version: 3.0
category: Email
author: Joseph Streeter
valid_to: 02-28-2026
last_updated: 02-17-2025 17:15:53
---

## Description

This document provides information about Microsoft Exchange Online sending limits that apply to all users and mailboxes in the organization.

## Details

There are message-sending limits in Microsoft Exchange that have been configured to reduce the impact of phishing emails sent from employee and student accounts which have been compromised. Attackers like to use compromised accounts to send phishing emails because the message appears to be more legitimate because it is coming from someone inside the organization.

### Prerequisites

None specified.

### Email Sending Limits

| **Description** | **Limit** |
|-----------------|-----------|
| Maximum number of recipients in a single email | 50 recipients per email |
| Maximum number of recipients in all emails sent in a 24-hour period | 2,000 recipients per 24-hours |
| Maximum message size | 25 MB |

Exchange Sending Limits

| **Description** | **Limit** |
|-----------------|-----------|
| Maximum number of recipients in a single email | 50 recipients per email |
| Maximum number of recipients in all emails sent in a 24-hour period | 2,000 recipients per 24-hours |
| Maximum message size | 25 MB |
| Maximum attachment size | 35 MB |

* These limits do not affect emails addressed to groups published in the GAL. Emails sent to Exchange groups are considered as being sent` to a single recipient.

* Applied limits are subject to change by the Technology Services or if Microsoft modifies the service offering.

The Microsoft Exchange sending limits are configured as follows:

_Recipient Limit per Email

    - The maximum number of recipients allowed in the To:, Cc:, and Bcc: fields for a single email message.

    * Limit: 50 recipients per email.
    * Applies to: All students and employees
    * Details: Each email is limited to 50 recipients.

_   - Recipient Rate Limit_ – Discourages the delivery of unsolicited bulk messages

    * Limit: 2,000 total recipients per user in a 24-hour period.
    * Applies to: All students and employees
    * Details: Users cannot send to more than 2,000 recipients over a rolling, 24-hour period. Once this limit is reached, the user cannot send more messages until the total number of recipients contacted in the past 24 hours drops below the limit.
    * Example: If a user sends an email to 500 recipients at 9:00 AM, another to 250 recipients at 10:00 AM, another to 250 recipients at 11:00 AM, and another to 1,000 recipients at 2:00 PM, reaching the limit of 2,000 recipients, they will not be able to send further messages until 9:00 AM the following day.

To send a message to more than 50 recipients:

    * * Send the message to one or more Distribution Group or Microsoft 365 group published in the Global Address List (GAL). These groups count as only one recipient, regardless of the number of members.

_NOTE: An Outlook Contact List will not work the same way as a_ _Distribution Group. If you send a message to an Outlook_ _Contact List, each member will count as a recipient towards the_ _limit!_

    * * Send the message from a Shared Mailbox as they can exceed the 50 recipients per message restriction.
      * Use a mass email service to send large quantities of mail. Microsoft writes in its own documentation that Exchange is not a mass email service and imposes service limitations to deter this sort of activity.

### Frequently Asked Questions

**Q: Why are there sending limits?**

A: We can reduce the impact if an account is compromised, reducing the reach of the bad actor, while also allowing the majority of Madison College users to communicate effectively.

****

**Q: Who do these sending limits apply to?**

A: This will apply to all student and all employee mailboxes.

**Q: What happens if an account exceeds the daily limit of recipients?**

A: The account will be blocked from sending more messages until the total number of recipients contacted in the past 24 rolling hours drops below the limit. If the account has shown indicators of being compromised, it may also need to be remediated or even unblocked administratively.

****

**Q: How do I send a message to more than 50 recipients?**

A:**** The message will need to use one or more Distribution Groups or Microsoft 365 Groups that are published in the Global Address List (GAL).  Alternatively, a shared mailbox also has the capability to exceed the recipient-per-message restriction.

****

**Q: Will the email sending limits impact large meetings sent through Outlook?**

A: Sending the invite to one or more Distribution Groups or Microsoft 365 Groups published in the Global Address List (GAL) will allow you to reach an audience above the 50 recipient-per-message limit.  Groups in the GAL are counted as a single recipient.

****

**Q: Will this affect emails being sent from my application?**

A: These sending limits will only apply to student and employee mailboxes.

## Additional Information and Follow-up

Contact the Help Desk at extension x6666 if you have any questions about the information listed above.
