# Google Chrome Enterprise Deployment via Group Policy
![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=flat&logo=youtube&logoColor=white)

https://youtu.be/CZ71qQRGgbg

## Short Summary
![Active Directory](https://img.shields.io/badge/Active_Directory-5E5E5E?style=for-the-badge&logo=microsoft&logoColor=white)

This lab project focused on deploying the Google Chrome Enterprise MSI package to client computers using Group Policy Software Installation. The project included preparing a shared software repository, configuring permissions, creating a software deployment GPO, troubleshooting a failed deployment, and identifying a permissions issue that prevented successful installation.

## Project Overview

The goal of this lab was to deploy Google Chrome Enterprise to client computers in a Computers Organizational Unit (OU) using Group Policy Software Installation.

Before deployment, I verified the MSI package's digital signature, prepared a shared software deployment location, configured access permissions, and created a Group Policy Object (GPO) to assign the software package to domain-joined client computers.

## What I Did

### 1. Verified the Software Package

* Downloaded the Google Chrome Enterprise MSI package.
* Verified the software's digital certificate before deployment.

### 2. Prepared a Central Software Repository

* Created a dedicated folder for software deployment packages.
* Stored the MSI package on a shared partition.
* Configured folder and file permissions to allow client computers to access the installation package.

### 3. Configured Group Policy Software Installation

* Created a Group Policy Object for computer-based software deployment.
* Navigated to:

  * Computer Configuration
  * Software Settings
  * Software Installation
* Added a new assigned software package.
* Referenced the MSI package using the shared network path.
* Linked the GPO to the appropriate Computers OU.

### 4. Tested the Deployment

* Forced Group Policy updates on client computers.
* Restarted client machines to allow software installation during startup.
* Observed that the software deployment did not occur as expected after restart.

### 5. Troubleshooting and Resolution

* Reviewed the deployment configuration to identify the cause of the failure.
* Rechecked the shared folder and file permissions.
* Discovered that Authenticated Users did not have the required read permissions on the deployment package.
* Updated the NTFS permissions to grant the necessary read access.
* Repeated the deployment process by restarting the client computers.
* Confirmed that the software deployment completed successfully after the permissions issue was corrected.

## Technical Decisions

* Used a dedicated shared folder to centralize software deployment packages.
* Verified the MSI digital certificate before deployment.
* Used Group Policy Software Installation to automate software deployment to client computers.
* Used a UNC network path for the deployment source.
* Applied least-privilege access by granting read permissions required for package access.

## Challenges and Lessons Learned

The main challenge was troubleshooting a failed software deployment despite the GPO appearing to be configured correctly.

By systematically reviewing the configuration, I identified that the issue was caused by incorrect NTFS permissions on the deployment package. This reinforced the importance of verifying both share permissions and NTFS permissions when troubleshooting Group Policy software deployments.

## Outcome

* Successfully deployed Google Chrome Enterprise to client computers through Group Policy Software Installation.
* Diagnosed and resolved a permissions-related deployment failure.
* Gained practical experience with software deployment, Group Policy administration, file permissions, and troubleshooting deployment issues in a Windows domain environment.

## Skills Demonstrated

* Active Directory administration
* Group Policy management
* Software deployment using Group Policy
* Windows Server administration
* Shared folder configuration
* NTFS permissions management
* Software package verification
* Troubleshooting and root cause analysis
* Client system testing and validation
