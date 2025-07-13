---
title: Email - Resolving "Permission to Send on Behalf" Error in Shared Mailboxes
kb_number: KB0011878
version: 2.0
category: Email
author: Joseph Streeter
valid_to: 05-30-2026
last_updated: 07-12-2025 12:00:00
---

## Description

When attempting to send an email from a shared mailbox, users may encounter permission-related error messages that prevent successful email delivery. The most common error is:

> "This message could not be sent. You do not have the permission to send the message on behalf of the specified user."

This issue typically arises due to incorrect permission configuration or misunderstanding of the different types of shared mailbox permissions available in Microsoft Exchange and Microsoft 365 environments. Understanding the distinction between "Send As" and "Send on Behalf" permissions is crucial for proper shared mailbox functionality.

**Common Scenarios:**

- Users attempting to send emails from shared mailboxes they believe they have access to
- Delegates trying to send emails using incorrect permission types
- New users who haven't been properly configured with shared mailbox access
- Permission changes that haven't synchronized across Outlook clients

## Details

### Understanding Shared Mailbox Permissions

Shared mailboxes in Microsoft Exchange and Microsoft 365 allow multiple users to access and send emails from a common email address. However, there are distinct permission types that control how emails are sent and how they appear to recipients:

**Send As Permission:**

- **Functionality**: The recipient sees the email as sent directly from the shared mailbox address
- **Display**: Email appears to come from `sharedmailbox@organization.com`
- **Usage**: Standard permission assigned to shared mailbox delegates
- **Best Practice**: Recommended for most shared mailbox scenarios
- **Authentication**: Requires proper delegation setup in Exchange/Microsoft 365

**Send on Behalf Permission:**

- **Functionality**: The recipient sees the email with both the sender and shared mailbox identified
- **Display**: Email appears as `User Name on behalf of sharedmailbox@organization.com`
- **Usage**: Typically used for assistant/executive scenarios
- **Limitation**: May not be available to all shared mailbox users
- **Configuration**: Requires specific setup and is not the default for shared mailbox access

**Full Access Permission:**

- **Functionality**: Allows user to read, send, and manage emails in the shared mailbox
- **Scope**: Provides complete mailbox access including folders and settings
- **Requirement**: Usually granted alongside Send As permission for shared mailbox delegates
- **Security**: Should be carefully managed due to broad access scope

### Root Causes of Permission Errors

**Primary Issues:**

1. **Incorrect Permission Assignment**: User has "Send on Behalf" when "Send As" is needed
2. **Missing Permissions**: User lacks any sending permissions for the shared mailbox
3. **Synchronization Delays**: Permission changes haven't replicated across all systems
4. **Outlook Configuration**: Client not properly configured to detect shared mailbox permissions
5. **Cached Credentials**: Outdated authentication information in Outlook profile

**Environmental Factors:**

- Exchange Online vs. on-premises Exchange Server differences
- Hybrid Exchange deployments with synchronization issues
- Outlook version compatibility with permission types
- Network connectivity affecting permission verification
- Active Directory replication delays in hybrid environments

### Technical Background

**Permission Verification Process:**

1. User composes email and selects shared mailbox as sender
2. Outlook queries Exchange for user's permissions on the shared mailbox
3. Exchange validates permission type (Send As vs. Send on Behalf)
4. If permissions match the request type, email is sent
5. If permissions don't match, error message is displayed

**Microsoft 365 vs. Exchange On-Premises:**

- **Microsoft 365**: Permissions typically synchronize within 15-30 minutes
- **Exchange On-Premises**: May require longer replication times depending on infrastructure
- **Hybrid Environments**: Additional complexity due to directory synchronization requirements

## Information

### Step 1: Verify Current Permissions

**Check Your Access Status:**

1. **Contact Shared Mailbox Delegate:**
   - Identify someone who currently has administrative access to the shared mailbox
   - Request verification of your current permission level
   - Confirm whether you should have Send As or Send on Behalf permissions

2. **Self-Check in Outlook:**
   - Open Outlook and navigate to **File** > **Account Settings** > **Delegate Access**
   - Look for the shared mailbox in your delegate list
   - Note the permission level displayed (if any)

3. **Test Email Composition:**
   - Create a new email in Outlook
   - Click the **From** field (if not visible, go to **Options** > **From**)
   - Check if the shared mailbox appears in the dropdown list
   - Note whether it shows as "Send As" or "Send on Behalf"

### Step 2: Request Proper Permissions

**Using Organization Process:**

1. **Shared Mailbox Request Process:**
   - Use the official Shared Mailbox Request process: [KB0011838](https://madisoncollege.service-now.com/sp?id=kb_article&sysparm_article=KB0011838)
   - Ensure you request "Send As" permission specifically
   - Include business justification for shared mailbox access
   - Specify the shared mailbox name and your required access level

2. **Work with Current Delegates:**
   - Current delegates can add you through the established process
   - Provide them with your exact email address and required permission type
   - Request confirmation once permissions have been applied

### Step 3: Configure Outlook for Shared Mailbox Access

**Outlook Desktop (2016/2019/2021/365):**

1. **Automatic Configuration (Recommended):**
   - Outlook should automatically detect shared mailboxes within 10-15 minutes
   - Restart Outlook if the shared mailbox doesn't appear automatically
   - Check the folder pane for the shared mailbox listing

2. **Manual Addition (If Needed):**
   - Go to **File** > **Account Settings** > **Account Settings**
   - Select **Email** tab > **Change** > **More Settings** > **Advanced**
   - Click **Add** and enter the shared mailbox email address
   - Click **OK** and restart Outlook

3. **Sending Email Correctly:**
   - Compose a new email
   - Click the **From** button (enable via **Options** > **From** if not visible)
   - Select the shared mailbox from the dropdown
   - Verify it shows as direct sending, not "on behalf of"

**Outlook Web App (OWA):**

1. **Access Shared Mailbox:**
   - Log into Outlook Web App
   - Look for the shared mailbox in the left folder pane
   - If not visible, click **Add shared folder or mailbox**

2. **Compose from Shared Mailbox:**
   - Click **New message**
   - Click the **From** field and select the shared mailbox
   - Verify the sender address shows correctly

### Step 4: Troubleshooting Common Issues

**Permission Synchronization Problems:**

1. **Wait for Replication:**
   - Allow 15-30 minutes for permissions to synchronize in Microsoft 365
   - On-premises Exchange may require up to 2 hours
   - Restart Outlook after the waiting period

2. **Clear Outlook Cache:**
   - Close Outlook completely
   - Hold **Ctrl** while starting Outlook to access safe mode
   - Alternatively, create a new Outlook profile temporarily

3. **Verify in Multiple Clients:**
   - Test access in both Outlook desktop and Outlook Web App
   - Mobile app testing can help isolate client-specific issues

**Persistent Error Resolution:**

1. **Check for Conflicting Permissions:**
   - Verify you don't have both Send As and Send on Behalf permissions
   - Remove Send on Behalf if present and Send As is intended

2. **Validate Mailbox Configuration:**
   - Confirm the shared mailbox is properly configured in Exchange
   - Verify the shared mailbox license status (if applicable)

3. **Test with Different Email:**
   - Try sending a test email to yourself first
   - Use a simple subject and body to isolate permission issues

## Additional Information and Follow-up

### Prevention and Best Practices

**For Shared Mailbox Administrators:**

1. **Standardize Permission Types:**
   - Always grant "Send As" permission for shared mailbox delegates
   - Avoid mixing "Send As" and "Send on Behalf" permissions for the same user
   - Document permission assignments for audit and troubleshooting purposes

2. **Regular Permission Audits:**
   - Review shared mailbox permissions quarterly
   - Remove access for users who no longer need it
   - Verify that new users receive appropriate permissions promptly

3. **User Training:**
   - Educate users on the difference between permission types
   - Provide clear instructions for requesting shared mailbox access
   - Create documentation for common troubleshooting steps

**For End Users:**

1. **Follow Established Processes:**
   - Always use the official Shared Mailbox Request process: [KB0011838](https://madisoncollege.service-now.com/sp?id=kb_article&sysparm_article=KB0011838)
   - Specify "Send As" permission when requesting access
   - Provide business justification for access requests

2. **Maintain Current Outlook Versions:**
   - Keep Outlook updated to the latest version
   - Regularly restart Outlook to ensure proper synchronization
   - Report persistent issues promptly to IT support

### Advanced Troubleshooting

**For IT Support Staff:**

1. **PowerShell Verification (Exchange Online):**

   ```powershell
   # Check mailbox permissions
   Get-MailboxPermission -Identity "SharedMailbox@domain.com" | Where-Object {$_.User -eq "user@domain.com"}
   
   # Check Send As permissions
   Get-RecipientPermission -Identity "SharedMailbox@domain.com" | Where-Object {$_.Trustee -eq "user@domain.com"}
   ```

2. **Exchange Management Shell (On-Premises):**

   ```powershell
   # View current permissions
   Get-MailboxPermission -Identity "SharedMailbox" -User "Domain\Username"
   
   # Grant Send As permission
   Add-RecipientPermission -Identity "SharedMailbox" -Trustee "Domain\Username" -AccessRights SendAs
   ```

3. **Common Administrative Solutions:**
   - Remove and re-add permissions if synchronization fails
   - Check Exchange server health and replication status
   - Verify Active Directory connectivity in hybrid environments

### Microsoft 365 Specific Considerations

**Online Environment Features:**

- Shared mailboxes don't require licenses for basic functionality
- Auto-mapping typically works within 10-15 minutes
- Exchange Online PowerShell provides detailed permission management

**Hybrid Environment Challenges:**

- Directory synchronization may cause permission delays
- On-premises Exchange and Exchange Online permission differences
- Azure AD Connect configuration impacts shared mailbox access

### Security and Compliance

**Access Control Best Practices:**

1. **Principle of Least Privilege:**
   - Grant minimum necessary permissions
   - Regularly review and remove unnecessary access
   - Implement approval workflows for shared mailbox access

2. **Audit and Monitoring:**
   - Log shared mailbox access and sending activities
   - Monitor for unauthorized access attempts
   - Implement alerts for permission changes

3. **Data Protection:**
   - Ensure shared mailbox content is included in backup strategies
   - Consider retention policies for shared mailbox emails
   - Implement data loss prevention (DLP) policies if needed

### Escalation Criteria

**When to Contact IT Support:**

- Permission errors persist after following all troubleshooting steps
- Multiple users experience similar issues simultaneously
- Shared mailbox appears to be completely inaccessible
- Outlook crashes when attempting to access shared mailboxes

**Information to Provide:**

- Exact error message text
- Shared mailbox email address
- Your email address and domain credentials
- Steps already attempted to resolve the issue
- Outlook version and operating system details

### Contact Information

For additional assistance:

- **Technology Services Help Desk**: Primary contact for technical issues
- **Shared Mailbox Delegates**: Can verify and manage permissions through established processes
- **Exchange Administrators**: For server-side configuration issues

### References and Further Reading

**Internal Documentation:**

- [Shared Mailbox Request Process (KB0011838)](https://madisoncollege.service-now.com/sp?id=kb_article&sysparm_article=KB0011838)

**Microsoft Official Documentation:**

**Shared Mailbox Management:**

- [Create a shared mailbox in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-a-shared-mailbox)
- [Open and use a shared mailbox in Outlook](https://support.microsoft.com/en-us/office/open-and-use-a-shared-mailbox-in-outlook-d94a8e9e-21f1-4240-808b-de9c9c088afd)
- [Add a shared mailbox to Outlook](https://support.microsoft.com/en-us/office/add-a-shared-mailbox-to-outlook-f4ea4bd4-0b12-405b-a94a-b717f9c44bbe)
- [Remove a shared mailbox from Outlook](https://support.microsoft.com/en-us/office/remove-a-shared-mailbox-from-outlook-fc64f2b1-d9be-474b-b9c2-b42d2d6ca17d)

**Permission Management:**

- [Give mailbox permissions to another user in Exchange Online](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)
- [Manage permissions for recipients in Exchange Online](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)
- [Add-RecipientPermission cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/exchange/add-recipientpermission)
- [Get-MailboxPermission cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/exchange/get-mailboxpermission)

**PowerShell and Exchange Online Management:**

- [Exchange Online PowerShell V3 module](https://learn.microsoft.com/en-us/powershell/exchange/exchange-online-powershell-v2)
- [Connect to Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell)
- [Exchange Online PowerShell for Mailbox Permissions](https://learn.microsoft.com/en-us/powershell/module/exchange/mailboxes/get-mailboxpermission)
- [Remove-RecipientPermission cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/exchange/remove-recipientpermission)

**Outlook Configuration and Troubleshooting:**

- [Outlook doesn't automatically add shared mailboxes in Microsoft 365](https://support.microsoft.com/en-us/office/outlook-doesn-t-automatically-add-shared-mailboxes-in-microsoft-365-6db6b06e-7e02-44f4-bba5-52e09a5da54b)
- [Troubleshoot issues with shared mailboxes](https://learn.microsoft.com/en-us/exchange/troubleshoot/mailboxes/shared-mailboxes-unexpected-behavior)
- [Outlook profile issues with shared mailboxes](https://support.microsoft.com/en-us/office/outlook-profile-issues-with-shared-mailboxes-b20bf4b5-7adc-4db1-8b8b-e73f2b3e6c8c)
- [Fix Outlook connection problems in Microsoft 365 and Exchange Online](https://support.microsoft.com/en-us/office/fix-outlook-connection-problems-in-microsoft-365-and-exchange-online-d8c52c5e-82c0-46e4-82c0-e36b5c9d8aa4)

**Exchange Server (On-Premises):**

- [Manage permissions for recipients in Exchange Server](https://learn.microsoft.com/en-us/exchange/recipients/mailbox-permissions)
- [Shared mailboxes in Exchange Server](https://learn.microsoft.com/en-us/exchange/recipients/shared-mailboxes)
- [Exchange Management Shell quick reference](https://learn.microsoft.com/en-us/exchange/exchange-management-shell-quick-reference-for-exchange-server)

**Hybrid Exchange Environments:**

- [Hybrid deployments with Exchange Server and Exchange Online](https://learn.microsoft.com/en-us/exchange/exchange-hybrid)
- [Azure AD Connect synchronization](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect)
- [Troubleshoot Azure AD Connect sync](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/tshoot-connect-sync-errors)

**Security and Compliance:**

- [Auditing in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/compliance/auditing-solutions-overview)
- [Data loss prevention (DLP) in Exchange Online](https://learn.microsoft.com/en-us/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Retention policies in Exchange Online](https://learn.microsoft.com/en-us/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies)

**Additional Troubleshooting Resources:**

- [Microsoft 365 and Office 365 service health](https://learn.microsoft.com/en-us/microsoft-365/enterprise/view-service-health)
- [Exchange Online service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)
- [Outlook troubleshooting for admins and IT professionals](https://support.microsoft.com/en-us/office/outlook-troubleshooting-for-admins-and-it-professionals-d6ff6d34-9c95-4b9b-b7b5-3c6a2b2e1bc1)
- [Microsoft Support and Recovery Assistant (SaRA)](https://support.microsoft.com/en-us/office/about-the-microsoft-support-and-recovery-assistant-e90bb691-c2a7-4697-a94f-88836856c72f)
