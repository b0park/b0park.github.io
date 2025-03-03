---
layout: post
title: "Google Workspace Former Employee Backup Guide"
permalink: /blog/google-workspace-former-employee-backup-guide/
date: 2024-04-26
categories: [Blog, Google Workspace]
tags: [google, workspace, backup, guide, gam, gyb]
image:
  path: /assets/images/backup-guide.jpg
  alt: Photo by Stephen Phillips - Hostreviews.co.uk on Unsplash
---
# Securely Backing Up Former Employee Data in Google Workspace: A Comprehensive Guide with Engram Vault
      
As businesses grow and employees come and go, it's important to have a system in place for backing up and managing the data of former employees. While Google Takeout is a useful tool for exporting data, it may not be the best option for larger organizations with multiple former employees to backup. That's where Google Apps Manager (GAM) and Got Your Back (GYB) come in.

In this blog post, we'll walk you through a step-by-step guide on how to use GAM and GYB to backup the data of former employees in Google Workspace. This method not only ensures that the organization's data is secure and protected, but it also helps with legal and compliance requirements. But what sets this method apart from a simple Google Takeout?

This method allows for continued use of Google Vault's eDiscovery tools without having to pay for a Google Archive user or full Google Workspace account. Instead, by sacrificing just one full Google Workspace account, organizations can create backups of all their former or archive users. This can help organizations save on costs and simplify their data backup and management processes. So, let's dive into how to use GAM and GYB to backup your former employee's data in Google Workspace.

## Step-by-Step Guide
### Step 1: Suspend User in Google Workspace
Before you begin the backup process, make sure to suspend the user's account to prevent any unwanted changes or access. To do this, log in to your Google Workspace admin console and navigate to the Users tab. Select the user you want to suspend and click on the Suspend User button. Confirm the action by clicking on Suspend User again in the pop-up window.
### Step 2: Export Contacts (if necessary)
If the user has contacts that you need to save, you can export them using the Google Contacts app. Simply navigate to the Contacts app and select the contacts you want to export. Click on the More button and select Export. Choose the format you want to use (e.g. Google CSV, Outlook CSV) and click on Export. Save the file to your computer.
### Step 3: Export Email GAM
The main part of the backup process involves using GAM to export the user's email. You'll need to install GAM on your computer if you haven't done so already. Once you've installed GAM, open a command prompt or terminal window and navigate to the GAM directory.
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> Download and install GAM on your computer. You can find the latest version of GAM on the GitHub repository (https://github.com/jay0lee/GAM)
{: .prompt-tip }
<!-- markdownlint-restore -->

To export the email, use the following command:

`F:\gam\gam.exe create export matter "VFE Backup" name user@domain.com corpus mail accounts user@domain.com
`

Replace "user@domain.com" with the email address of the user you want to back up. This command will create a new export called "VFE Backup" for the user's email.
### Step 4: Move the User to the Former Employee OU
After you've created the export, move the user to a Former Employee OU to remove them from your usual directories. This step is optional but recommended to keep your directory organized.
### Step 5: Use GAM to Check Export Emails Progress
Check the status of the export by running the following command:

`gam info export "VFE Backup" user@domain.com`

This command will display the status of the export. Wait for the status to change from "IN_PROGRESS" to "COMPLETED" before proceeding.
### Step 6: Download the Newly Created Export
Download the newly created export by running the following command:

`gam download export "VFE Backup" user@domain.com targetfolder user@domain.com
`

Replace "user@domain.com" with the email address of the user you backed up. This command will download, verify checksum, and extract the backup files.

### Step 7: Install, Configure, and Use GYB to Upload the Export
>https://github.com/GAM-team/got-your-back

Install and configure GYB on your computer if you haven't done so already. Once you've done that, upload the export to your former-employee-archive@domain.com account using the following command:

`gyb.exe --email former-employee-archive@domain.com --action restore-mbox --local-folder user@domain.com --strip-labels --label-restored user@domain.com --service-account`

Replace "user@domain.com" with the email address of the user you backed up. This command will upload the export to your archive account and restore the label for the user's email.

### Step 8: Delete the Account from Google Workspace
Once you've completed the backup process, you can delete the user's account from Google Workspace. Before you do this, make sure to check all the check boxes to move the user's Drive, Calendar, etc. data to another account. Use your ***former-employee-archive@domain.com*** account for this purpose.

That's it! You've successfully backed up the data of a former employee in Google Workspace using GAM and GYB.

## Tips and Best Practices
Backing up data can be a complicated process, but with the right tools and strategies, it can be a lot smoother. Here are some tips and best practices to consider when backing up a former employee's data in Google Workspace:

1. As an MSP provider, you’ve got plenty on your plate. Let us handle Workspace Backups by partnering with Engram Vault. We only charge for active accounts, any archived and disabled account will no longer be backed up after they’re disabled, but we’ll keep their archive available for as long  as we’re partnered. [Contact Us to Start a Free Trial Today!](https://www.engramvault.com/contact-us)

2. Use a machine with an SSD for GYB: GYB uses a small SQL database file to keep track of what's been uploaded in case of interruptions. Using a machine with an SSD can help speed up the process and reduce the likelihood of errors.

## Conclusion
After following the step-by-step guide and implementing the tips and best practices, you can ensure that your organization's data is securely backed up even after an employee has left. By using GAM and GYB, you can save time and money by not having to pay for additional Google Archive users or a full Google Workspace account.

Remember, backing up former employee data is crucial not just for compliance but also for business continuity. In the event that a former employee's data needs to be retrieved, having a backup will save time and ensure that all necessary information is readily available.

We hope that this guide has been helpful and informative in showing you how to properly backup former employee data in Google Workspace. By following the steps and best practices outlined here, you can rest assured that your organization's data is safe and secure. Don't hesitate to reach out to us if you have any questions or concerns about the backup process.

## Additional Resources
For those who want to learn more about GAM and GYB and how to use them for backup purposes, the following resources can be helpful:

1. [GAM Documentation](https://github.com/GAM-team/GAM/wiki): This is the official documentation for GAM, which provides detailed information on how to install, configure, and use the tool. 
2. [GYB Documentation](https://github.com/GAM-team/got-your-back/wiki): This is the official documentation for GYB, which provides detailed information on how to install, configure, and use the tool.
3. [Google Workspace Learning Center](https://support.google.com/a/users/): This is a comprehensive resource for learning about all the tools and features of Google Workspace, including GAM and GYB.
4. [Google Workspace Admin Help](https://support.google.com/a/): This is the official help center for Google Workspace administrators, which provides step-by-step instructions and troubleshooting guides for using GAM and GYB.