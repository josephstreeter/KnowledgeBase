---
title: Renewing Microsoft 365 Groups and Teams
kb_number: KB0011876
version: 2.0
category: Other
author: Joseph Streeter
valid_to: 05-02-2026
last_updated: 07-12-2025 12:00:00
---

## Description

This article provides comprehensive step-by-step guidance for Microsoft 365 Group and Teams owners on how to renew their group or team to maintain access and prevent expiration. Microsoft 365 Groups and associated Teams may have expiration policies set by the organization, requiring owners to renew them periodically to confirm their continued use and ensure resource management efficiency.

Microsoft 365 Groups serve as the foundation for various collaborative services including Microsoft Teams, SharePoint sites, Outlook groups, and other integrated applications. When these groups are subject to expiration policies, understanding the renewal process is critical to maintaining business continuity and preventing data loss.

**Key Scenarios:**

- Teams showing red expiration icons indicating imminent expiration
- Group owners receiving email notifications about upcoming expiration
- Teams that have become inactive but still contain valuable data
- Organizations implementing governance policies to manage group lifecycle
- Situations where automatic renewal has not occurred due to inactivity

## Details

Microsoft 365 Groups (including those tied to Microsoft Teams) are configured with expiration policies to ensure inactive groups are retired and organizational resources are managed efficiently. The standard configuration includes:

**Default Expiration Timeline:**

- **Primary Period**: Groups expire every 365 days by default
- **First Notice**: 30 days before expiration
- **Second Notice**: 15 days before expiration
- **Final Notice**: 1 day before expiration
- **Grace Period**: 30-day soft delete period after expiration

**Affected Services:**
When a Microsoft 365 Group expires, it impacts all connected services:

- Microsoft Teams (channels, chats, files)
- SharePoint Online site and document libraries
- Outlook group mailbox and conversations
- Planner plans and tasks
- OneNote notebooks
- Power BI workspaces (if connected)
- Stream videos and channels

### Notification Process

**Email Notifications to Group Owners:**
Group owners receive automated email notifications at specified intervals before expiration. These emails contain:

- Clear expiration date and time
- Direct link to renew the group
- Instructions for manual renewal through Teams or other interfaces
- Warning about data loss if renewal is not completed

**Visual Indicators in Teams:**

- Red expiration icon appears next to team names
- Warning messages in team settings
- Dashboard notifications in Teams admin center (for administrators)

### Automatic Renewal Triggers

To prevent accidental deletion, automatic renewal occurs when specific activities are detected:

**Teams Activities:**

- Any channel visit from team members
- Posting messages in channels
- File uploads or modifications in Teams
- Meetings scheduled or conducted using the team

**SharePoint Activities:**

- Viewing, editing, downloading files
- Moving, sharing, or uploading documents
- Creating or modifying lists and libraries
- **Note**: Simply viewing a SharePoint page does not trigger renewal

**Outlook Group Activities:**

- Joining or editing the group
- Reading or writing group messages
- Liking messages in Outlook on the web
- Calendar interactions within the group

**Microsoft Forms Activities:**

- Viewing, creating, or editing forms
- Submitting responses to group forms
- Analyzing form results

**Other Connected Services:**

- Planner task creation or updates
- OneNote section or page modifications
- Power BI workspace interactions

### Soft Delete and Recovery Process

**Soft Delete Phase (30 Days):**

- Group enters "soft delete" state after expiration
- All data remains recoverable but inaccessible to users
- Only administrators can restore during this period
- All connected services remain suspended

**Permanent Deletion:**

- After 30-day grace period, groups are permanently deleted
- All associated data across all services is irretrievably lost
- No recovery options available after permanent deletion

## Information

### Step 1: Identify Teams Requiring Renewal

**Visual Indicators in Microsoft Teams:**
If your team name has a red expiration icon next to it, the team will expire in fewer than 30 days and requires immediate attention.

**Check Expiration Status:**

1. Open Microsoft Teams client (desktop or web)
2. Look for red warning icons next to team names in the left navigation panel
3. Review any banner notifications at the top of the Teams interface

### Step 2: Manual Renewal Through Teams Interface

**For Team Owners - Primary Method:**

1. Navigate to the team in the left panel of the Teams client
2. Select **More options** (three dots) > **Manage team**
3. Select **Settings** > **Team Expiration**
4. Select **Renew now** to extend the team's lifecycle
5. Verify the new expiration date is displayed

**Alternative Method - Through Team Settings:**

1. Open the team requiring renewal
2. Click the team name at the top of the interface
3. Select **Edit team** from the dropdown menu
4. Navigate to the **Settings** tab
5. Look for **Expiration** or **Renewal** options
6. Click **Renew** and confirm the action

### Step 3: Email-Based Renewal

**When You Receive Renewal Notifications:**

1. Open the renewal email from Microsoft 365
2. Click the **Renew now** button in the email
3. Sign in to your Microsoft 365 account if prompted
4. Confirm the renewal in the web interface
5. Verify the updated expiration date

### Step 4: Alternative Renewal Methods

**Microsoft 365 Admin Center (For Administrators):**

1. Navigate to Microsoft 365 Admin Center
2. Go to **Groups** > **Active groups**
3. Find the group requiring renewal
4. Select the group and click **Renew**
5. Confirm the renewal action

**PowerShell Method (Advanced Users):**

```powershell
# Connect to Azure AD
Connect-AzureAD

# Renew a specific group
Set-AzureADGroup -ObjectId "group-object-id" -ExpirationDateTime (Get-Date).AddDays(365)

# Verify renewal
Get-AzureADGroup -ObjectId "group-object-id" | Select DisplayName, ExpirationDateTime
```

### Step 5: Verification and Confirmation

**After Renewal:**

1. **Check Visual Indicators**: Red expiration icons should disappear
2. **Verify in Settings**: Confirm new expiration date in team settings
3. **Email Confirmation**: Look for renewal confirmation email
4. **Test Functionality**: Ensure all team features remain accessible

**Monitor Automatic Renewal:**
Teams with regular activity should renew automatically. Monitor for:

- Channel visits and message activity
- File uploads and SharePoint interactions
- Meeting activities and calendar events
- Any connected service usage

### Troubleshooting Common Issues

**Cannot Find Renewal Option:**

- Verify you are listed as a team owner
- Check if another owner has already renewed the team
- Ensure you're using the latest version of Teams client
- Try accessing through Teams web interface

**Renewal Button Not Working:**

- Clear browser cache and cookies
- Try using a different browser or incognito mode
- Check your internet connection
- Sign out and sign back into Teams

**Permission Errors:**

- Confirm owner status with IT administrator
- Request ownership permissions if needed
- Contact other team owners for assistance

## Additional Information and Follow-up

### Best Practices for Group Management

**For Group Owners:**

1. **Multiple Owners**: Assign at least two owners to each group to ensure renewal redundancy
2. **Regular Monitoring**: Check group expiration dates quarterly
3. **Activity Maintenance**: Encourage regular team activity to trigger automatic renewal
4. **Documentation**: Maintain records of important teams and their business purposes

**For IT Administrators:**

1. **Policy Configuration**: Set appropriate expiration periods based on organizational needs
2. **Notification Templates**: Customize renewal notification emails for clarity
3. **Training Programs**: Educate users on group lifecycle management
4. **Monitoring Dashboards**: Use Microsoft 365 admin center to monitor group health

### Recovery and Restoration

**If a Group Has Expired:**

1. **Contact IT Administrator**: Only administrators can restore expired groups
2. **Provide Group Details**: Include group name, purpose, and business justification
3. **Act Quickly**: Restoration must occur within 30 days of expiration
4. **Data Verification**: Verify all data and services are restored properly after recovery

**Prevention Strategies:**

- Set up calendar reminders for renewal dates
- Implement automated monitoring for groups approaching expiration
- Create organizational policies for group lifecycle management
- Regular training on group management best practices

### Organizational Policy Considerations

**Governance Framework:**

- Establish clear guidelines for group creation and management
- Define roles and responsibilities for group owners
- Implement approval processes for group creation
- Regular audits of group usage and ownership

**Compliance and Security:**

- Ensure group expiration policies align with data retention requirements
- Consider regulatory compliance needs when setting expiration periods
- Implement appropriate security controls for group access
- Document group management procedures for audit purposes

### Contact Information and Support

**For Group Renewal Issues:**

- **Primary**: IT Help Desk for technical assistance
- **Secondary**: Microsoft 365 administrators for policy questions
- **Emergency**: IT emergency contact for critical business impact

**When to Escalate:**

- Multiple groups expiring simultaneously
- Inability to access renewal options
- Data loss concerns
- Policy modification requests

### References and Further Reading

**Microsoft Official Documentation:**

- [Manage Microsoft 365 group expiration policies](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/manage-expiration-policy?view=o365-worldwide)
- [Renew a Microsoft 365 group](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/renew-a-microsoft-365-group?view=o365-worldwide)
- [Overview of Microsoft 365 Groups](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/office-365-groups)
- [Restore a deleted Microsoft 365 group](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/restore-deleted-group)

**Teams-Specific Documentation:**

- [Manage Microsoft Teams settings in your organization](https://learn.microsoft.com/en-us/microsoftteams/enable-features-office-365)
- [Teams lifecycle management](https://learn.microsoft.com/en-us/microsoftteams/plan-teams-lifecycle)
- [Microsoft Teams admin documentation](https://learn.microsoft.com/en-us/microsoftteams/)

**PowerShell and Administration:**

- [Azure Active Directory PowerShell for Graph](https://learn.microsoft.com/en-us/powershell/azure/active-directory/install-adv2)
- [Microsoft 365 PowerShell documentation](https://learn.microsoft.com/en-us/powershell/microsoft-365/)
- [Set-AzureADGroup cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)

**Governance and Compliance:**

- [Microsoft 365 Groups governance](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaboration-governance-overview)
- [Information governance in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/compliance/manage-information-governance)
- [Data retention policies for Teams](https://learn.microsoft.com/en-us/microsoftteams/retention-policies)
