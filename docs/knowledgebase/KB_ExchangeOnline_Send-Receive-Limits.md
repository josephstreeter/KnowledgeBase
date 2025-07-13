---
title: Understanding Exchange Online Send/Receive Limits
kb_number: KB_ExchangeOnline_Send-Receive-Limits
category: Exchange Online
version: 1.0
author: IAM Team
valid_to: 01-01-2027
last_updated: 07-12-2025
---

## Description

Overview of send and receive limits in Exchange Online.

## Details

Exchange Online enforces limits on message size, recipient count, and mailbox storage to ensure reliable service and prevent abuse. These limits may differ based on your organization's licensing and policies. Understanding these limits helps prevent issues with sending, receiving, or storing emails. If you regularly reach these limits, consider using alternative file sharing methods or requesting a quota increase from IT support.

## Information

### Exchange Online Send/Receive Limits

- **Maximum message size:** 150 MB (default is 35 MB for most organizations)
- **Recipient limit per message:** 500 recipients
- **Daily send limit:** 10,000 recipients per day
- **Mailbox size limit:** 50 GB (E1/E3), 100 GB (E5)
- **Attachment size limit:** 150 MB (may be lower for some clients)

### How to Check Your Limits

- In Outlook Web App, go to 'Settings' > 'View all Outlook settings' > 'Mail' > 'Message handling'.
- Ask your IT support for your organization's specific limits.

## Additional Information and Follow-up

- Limits may vary based on your organization's policies and licensing.
- If you exceed a limit, you may receive a non-delivery report (NDR) or error message.
- Large attachments may be blocked; use OneDrive or SharePoint for sharing large files.

If you need higher limits or encounter issues, contact your IT support or helpdesk.

## References

- [Microsoft: Exchange Online limits](https://learn.microsoft.com/en-us/exchange/limits-exchange-online)
- [Microsoft: Message size and recipient limits](https://learn.microsoft.com/en-us/exchange/mail-flow/message-size-limits)
