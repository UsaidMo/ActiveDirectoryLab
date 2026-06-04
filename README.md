### 📝 Project Summary

I built a complete Windows enterprise environment across two virtual machines. The first VM was used to house the Windows Server Domain Controller while the second was used to add a Windows 11 client workstation to the domain. Finally a secure file server was set up using Active Directory security groups to lock down folder permissions by department. The lab was split into THREE stages:

### 🛠️ Tools Used
* Oracle VirtualBox

### 💻 Operating systems

* Windows Server 2025
* Windows 11

## 📸 Step-by-Step Lab Walkthrough

### 🏢 Stage 1: Setting Up the Windows Server

#### Step 1.1: OS Installation, Admin Setup & Updates
The initial bootup, setting up the password, and installing the latest security updates to patch the system before configuration.
![Initial Setup and Updates](images/screenshot1.png)

#### Step 1.2: Hostname Configuration
Renaming the server to "Active-Directory-Lab" to make it easily identifiable on the network.
![Hostname Configuration](images/screenshot3.png)

#### Step 1.3: Installing AD DS
Adding the Active Directory Domain Services (AD DS) role and Group Policy Management features through the Server Manager.
![Installing AD DS](images/screenshot5.png)

#### Step 1.4: Domain Controller Promotion
Formally promoting the server to a Domain Controller after the role installation is complete.
![Domain Controller Promotion](images/screenshot6.png)

#### Step 1.5: Static IP Assignment
Manually assigning a static IPv4 address (192.168.1.174) and setting the preferred DNS to the loopback address to ensure network stability.
![Static IP Assignment](images/screenshot7.png)

#### Step 1.6: Organizational Unit (OU) Structure
Creating a logical OU hierarchy (e.g., France > User > IT, HR, Finance) to organize future users and computers.
![Organizational Unit Structure](images/screenshot8.png)

---

### 🖥️ Stage 2: Setting Up the Windows 11 Client

#### Step 2.1: Client Provisioning and Hostname
Performing a clean installation of Windows 11 on the client virtual machine and renaming the machine to "Windows11Client" for clear identification within the lab.
![Client Installation and Hostname](images/screenshot9.png)

#### Step 2.2: DNS Configuration
Manually setting the client's IPv4 DNS server to the IP of the Windows Server (192.168.1.174) so it can locate the domain.
![DNS Configuration](images/screenshot11.png)

#### Step 2.3: Joining the Domain
Entering Domain Administrator credentials to officially join the client machine to the "homelab.com" domain.
![Joining the Domain](images/screenshot12.png)

#### Step 2.4: Domain Join Confirmation
Successfully receiving the "Welcome to the homelab.com domain" message, confirming connectivity.
![Domain Join Confirmation](images/screenshot13.png)

#### Step 2.5: User Login
Verifying the setup by logging in as a domain user (e.g., John Joe) on the Windows 11 client.
![User Login](images/screenshot14.png)

#### Step 2.6: AD Organization
Moving the new client computer object from the default "Computers" container into the properly designated OU.
![AD Organization](images/screenshot15.png)

#### Step 2.7: Computer Metadata
Adding a description to the computer object in Active Directory to identify which user it belongs to.
![Computer Metadata](images/screenshot16.png)

---

### 🔒 Stage 3: File Server Setup and Permissions

#### Step 3.1: Root Folder Creation
Creating the primary data directory named "MyCompanyData" on the server's C: drive.
![Root Folder Creation](images/screenshot17.png)

#### Step 3.2: Departmental Sub-folders
Organizing the file server by creating sub-folders for HR, IT, Finance, and Public use.
![Departmental Sub-folders](images/screenshot18.png)

#### Step 3.3: Security Groups
Creating Global Security Groups (e.g., Finance) in Active Directory to manage departmental access.
![Security Groups](images/screenshot19.png)

#### Step 3.4: User Creation
Populating the OUs with individual domain users (e.g., William Shake) for each department.
![User Creation](images/screenshot20.png)

#### Step 3.5: Group Membership
Adding the corresponding users to their respective security groups to simplify permission management.
![Group Membership](images/screenshot21.png)

#### Step 3.6: NTFS Permissions
Configuring NTFS security settings to grant specific groups (like HR) "Modify" permissions on their folders.
![NTFS Permissions](images/screenshot22.png)

#### Step 3.7: Access Control Enforcement
Removing or denying access to unauthorized users to ensure department data remains private.
![Access Control Enforcement](images/screenshot23.png)

#### Step 3.8: Share Permissions
Configuring Advanced Sharing permissions for "Everyone" to allow network access to the "MyCompanyData" folder.
![Share Permissions](images/screenshot24.png)
