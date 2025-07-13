---
title: Email - Outlook Error: Data File Has Reached Maximum Size
kb_number: KB0011896
version: 2.0
category: Email
author: Joseph Streeter
valid_to: 07-04-2026
last_updated: 07-12-2025 12:00:00
---

## Description

Users may encounter an error in Microsoft Outlook stating that their data file has reached its maximum size. This typically occurs when the mailbox or local cache file (OST/PST) grows too large, preventing new emails from being sent, received, or stored locally. This issue can significantly impact productivity and email functionality.

The error commonly affects users with large mailboxes, those who rarely manage email storage, users of shared mailboxes, or environments with high email volume. Understanding the root cause and implementing proper email management practices is essential for preventing recurrence.

**Common Error Messages:**

- "The Outlook data file has reached the maximum size"
- "Cannot move the items. The file has reached its maximum size"
- "Your mailbox is over its size limit. You may not be able to send or receive new mail until you reduce your mailbox size"
- "The operation failed. An object could not be found"

## Details

### Understanding Outlook Data Files

Outlook uses different file types to store email data:

**OST Files (Offline Storage Table):**

- Used with Microsoft 365, Exchange Online, and Exchange Server
- Stores cached copy of mailbox data for offline access
- Default maximum size: 50 GB (configurable via registry)
- Location: `%localappdata%\Microsoft\Outlook\`

**PST Files (Personal Storage Table):**

- Used for POP3, IMAP accounts, or data archiving
- Maximum size: 50 GB for Outlook 2010 and later (2 GB for older versions)
- Can be stored in various locations (often Documents folder or network drives)

### Root Causes of Size Limit Issues

**Primary Factors:**

1. **Large Attachments**: Email attachments consume significant space, especially multimedia files, documents, and archived data
2. **Calendar History**: Extensive calendar data, meeting histories, and recurring appointment details
3. **Sent Items Accumulation**: Large volume of sent emails with attachments
4. **Shared Mailbox Access**: Multiple shared mailboxes cached locally increase OST file size
5. **Archive Policy**: Lack of proper email archiving or retention policies
6. **Deleted Items Retention**: Deleted items not permanently removed from the mailbox

**Environmental Considerations:**

- Network connectivity affecting synchronization
- Exchange/Microsoft 365 mailbox size limits
- Local disk space availability
- Outlook version and configuration settings

### Impact on Outlook Performance

When data files approach size limits:

- Email synchronization may become slow or fail
- Outlook startup and shutdown times increase significantly
- Search functionality becomes sluggish or unresponsive
- Risk of data corruption in oversized files
- Potential for complete Outlook failure or crashes

## Information

### Step 1: Immediate Space Recovery Actions

**Empty System Folders First:**

1. **Deleted Items Folder:**
   - In Outlook, navigate to the Folder Pane
   - Right-click **Deleted Items** and select **Empty Folder**
   - Confirm the deletion when prompted
   - For shared mailboxes, repeat this process for each shared mailbox's Deleted Items

2. **Junk Email Folder:**
   - Right-click **Junk Email** and select **Empty Folder**
   - This removes spam and unwanted emails taking up space

3. **Sent Items Management:**
   - Review and delete unnecessary sent emails, especially those with large attachments
   - Consider moving important sent items to archive folders

### Step 2: Use Mailbox Cleanup Tools

**Accessing Mailbox Cleanup (Outlook 2016/2019/2021/365):**

1. Navigate to **File** > **Tools** > **Mailbox Cleanup**
2. Use the following options strategically:

**Available Cleanup Options:**

- **View Mailbox Size**: Identify which folders consume the most space
- **Find Items Older Than**: Locate emails older than specified dates for deletion
- **Find Items Larger Than**: Identify emails with large attachments (typically > 1MB)
- **View Deleted Items Size**: Check space used by deleted items
- **Empty Deleted Items**: Remove items from Deleted Items folder
- **View Conflicts Size**: Identify and resolve synchronization conflicts

**Alternative Method for Modern Outlook:**

- Go to **File** > **Account Information** > **Tools** > **Mailbox Cleanup**

### Step 3: Advanced Mailbox Management

**Identify Large Items for Removal:**

1. **Search for Large Emails:**

   ```text
   Search criteria: size:>5MB
   ```

   - Use Outlook's search bar with size parameters
   - Review results and delete unnecessary large emails

2. **Date-Based Cleanup:**

   ```text
   Search criteria: received:<01/01/2023
   ```

   - Find emails older than a specific date
   - Archive or delete based on retention policies

3. **Attachment Management:**
   - Save important attachments to file systems
   - Delete original emails with large attachments
   - Use OneDrive/SharePoint for file sharing instead of email attachments

### Step 4: OST/PST File Compaction

**For OST Files (Exchange/Microsoft 365):**

1. **Access Data File Settings:**
   - Go to **File** > **Account Settings** > **Account Settings**
   - Select the **Data Files** tab
   - Choose your account and click **Settings**

2. **Advanced Settings:**
   - Click **Advanced** > **Outlook Data File Settings**
   - Select **Compact Now** to reduce file size
   - Wait for the compaction process to complete (may take several minutes)

**For PST Files:**

1. **Right-click PST in Folder Pane**
2. Select **Data File Properties**
3. Click **Advanced** > **Compact Now**

### Step 5: Configure Outlook Sync Settings

**Optimize Synchronization (Exchange/Microsoft 365):**

1. **Adjust Sync Timeframe:**
   - Go to **File** > **Account Settings** > **Account Settings**
   - Select your account > **Change** > **More Settings** > **Advanced**
   - Set "Mail to keep offline" to a shorter period (e.g., 12 months instead of All)

2. **Manage Shared Mailboxes:**
   - Download only essential shared mailboxes
   - Configure selective synchronization for large shared mailboxes

### Step 6: Alternative Solutions

**If Standard Methods Fail:**

1. **Create New Outlook Profile:**
   - Control Panel > Mail > Show Profiles > Add
   - Create fresh profile to rebuild OST file
   - Re-configure email accounts in new profile

2. **Manual OST Deletion:**
   - Close Outlook completely
   - Navigate to `%localappdata%\Microsoft\Outlook\`
   - Delete the problematic OST file
   - Restart Outlook (new OST will be created and synchronized)

3. **Registry Modification (Advanced Users):**

   ```text
   Registry Path: HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\PST
   Value: MaxLargeFileSize (DWORD)
   Data: Desired size in MB (e.g., 61440 for 60GB)
   ```

   **Warning**: Registry modifications should only be performed by experienced users

## Additional Information and Follow-up

### Prevention and Best Practices

**Ongoing Email Management:**

1. **Implement Email Retention Policies:**
   - Establish organization-wide email retention guidelines
   - Automatically archive emails older than specified periods
   - Train users on proper email hygiene practices

2. **Regular Maintenance Schedule:**
   - Monthly mailbox cleanup reviews
   - Quarterly OST/PST file compaction
   - Annual email archiving to PST files or online archives

3. **Attachment Management Best Practices:**
   - Use cloud storage (OneDrive, SharePoint) for large file sharing
   - Implement attachment size limits in email policies
   - Save important attachments locally and delete email copies

### Microsoft 365 Specific Considerations

**Online Archive Features:**

- Enable Online Archive for users with large mailboxes
- Configure auto-expanding archives for unlimited storage
- Use retention policies to automatically move old emails to archives

**Storage Quotas and Monitoring:**

- Monitor mailbox size reports in Microsoft 365 Admin Center
- Set up automated alerts for users approaching storage limits
- Implement data loss prevention policies for sensitive attachments

### Troubleshooting Advanced Issues

**When Standard Solutions Don't Work:**

1. **OST Corruption Issues:**
   - Use Scanpst.exe (Inbox Repair Tool) to check file integrity
   - Consider professional data recovery services for critical data
   - Restore from backup if corruption is severe

2. **Performance Optimization:**
   - Disable unnecessary Outlook add-ins
   - Update to latest Outlook version and patches
   - Consider hardware upgrades (SSD, additional RAM) for large data files

3. **Network and Connectivity Issues:**
   - Check Exchange server connectivity and performance
   - Verify adequate bandwidth for large mailbox synchronization
   - Consider cached mode optimization for slow connections

### Alternative Email Management Solutions

**Third-Party Tools:**

- MailStore for email archiving and compliance
- Quest Archive Manager for enterprise-level archiving
- CodeTwo Email Archiver for small to medium businesses

**Built-in Windows Tools:**

- PowerShell cmdlets for Exchange/Microsoft 365 mailbox management
- Group Policy settings for Outlook configuration management
- Windows Search indexing optimization for better email search performance

### Compliance and Legal Considerations

**Data Retention Requirements:**

- Understand legal requirements for email retention in your industry
- Implement appropriate archiving solutions for compliance
- Document email management procedures for audit purposes
- Consider eDiscovery requirements when implementing retention policies

### Contact Information and Escalation

For additional assistance:

- **Technology Services Help Desk**: Primary contact for technical issues
- **Student Help Desk**: Student-specific email support
- **Exchange Administrators**: For server-side mailbox issues
- **Microsoft Support**: For complex Outlook or Microsoft 365 issues

**When to Escalate:**

- Multiple users experiencing similar issues simultaneously
- Data corruption or loss suspected
- Registry modifications required
- Exchange server-side configuration changes needed

### References and Further Reading

- [Microsoft 365 mailbox storage limits](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits)
- [Outlook data file size limits](https://support.microsoft.com/en-us/office/outlook-pst-and-ost-file-sizes-and-limits-7df8b463-3ac0-440a-9f62-39ce2bac2d5d)
- [How to configure cached Exchange Mode](https://support.microsoft.com/en-us/office/turn-on-cached-exchange-mode-7885af08-9a60-4ec3-850a-e221c1ed0c1c)
- [Mailbox cleanup best practices](https://support.microsoft.com/en-us/office/reduce-the-size-of-your-mailbox-and-outlook-data-files-pst-and-ost-e4c6a4f1-d39c-47dc-a4fa-abe96dc8c7ef)
