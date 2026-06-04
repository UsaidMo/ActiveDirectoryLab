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
Performing the initial bootup to select language and regional formats, creating a secure password for the built-in Administrator account, and installing the latest security updates to patch the system before configuration.
![Initial Bootup](images/1.%20(Stage%201)%20Initial%20bootup%20of%20windows%20server.png)
![Admin User Login](images/2.%20Admin%20user%20login.png)
![Windows Updates](images/4.%20Check%20any%20necessary%20windows%20updates.png)

#### Step 1.2: Hostname Configuration
Renaming the server to "Active-Directory-Lab" to make it easily identifiable on the network.
![Hostname Configuration](images/3.%20Change%20hostname%20of%20server.png)

#### Step 1.3: Installing AD DS
Adding the Active Directory Domain Services (AD DS) role and Group Policy Management features through the Server Manager.
![Installing AD DS](images/5.%20Create%20Active%20Directory.png)

#### Step 1.4: Domain Controller Promotion
Formally promoting the server to a Domain Controller after the role installation is complete.
![Domain Controller Promotion](images/6.%20Promote%20server%20to%20a%20domain%20controller.png)

#### Step 1.5: Static IP Assignment
Manually assigning a static IPv4 address (192.168.1.174) and setting the preferred DNS to the loopback address to ensure network stability.
![Static IP Assignment](images/7.%20Assign%20a%20static%20ip%20on%20the%20server.png)

#### Step 1.6: Organizational Unit (OU) Structure
Creating a logical OU hierarchy (e.g., France > User > IT, HR, Finance) to organize future users and computers.
![Organizational Unit Structure](images/8.%20Creating%20OUs%20for%20users%20and%20computers.png)

---

### 🖥️ Stage 2: Setting Up the Windows 11 Client

#### Step 2.1: Client Provisioning and Hostname
Performing a clean installation of Windows 11 on the client virtual machine and renaming the machine to "Windows11Client" for clear identification within the lab.
![Client Installation](images/9.%20(Stage%202)%20Setting%20up%20the%20Windows%2011%20Client.png)
![Client Hostname](images/9.%20Change%20hostname%20of%20the%20client.png)

#### Step 2.2: DNS Configuration
Manually setting the client's IPv4 DNS server to the IP of the Windows Server (192.168.1.174) so it can locate the domain.
![DNS Configuration](images/10.%20Change%20dns%20of%20client%20to%20ip%20of%20server%20and%20dhcp%20is%20enabled.png)

#### Step 2.3: Joining the Domain
Entering Domain Administrator credentials to officially join the client machine to the "homelab.com" domain.
![Joining the Domain](images/11.%20Make%20the%20client%20join%20the%20domain.png)

#### Step 2.4: Domain Join Confirmation
Successfully receiving the "Welcome to the homelab.com domain" message, confirming connectivity.
![Domain Join Confirmation](images/12.%20Confirmation%20of%20successfully%20joined%20the%20domain.png)

#### Step 2.5: User Login
Verifying the setup by logging in as a domain user (e.g., John Joe) on the Windows 11 client.
![User Login](images/13.%20We%20can%20successfully%20login%20as%20a%20user%20now.png)

#### Step 2.6: AD Organization
Moving the new client computer object from the default "Computers" container into the properly designated OU.
![AD Organization](images/14.%20Best%20Practice%20move%20the%20new%20user%20into%20an%20OU.png)

#### Step 2.7: Computer Metadata
Adding a description to the computer object in Active Directory to identify which user it belongs to.
![Computer Metadata](images/15.%20description%20for%20the%20computer%20(the%20user%20it%20belongs%20to).png)

---

### 🔒 Stage 3: File Server Setup and Permissions

#### Step 3.1: Root Folder Creation
(NOTE: All previous users have been deleted).......Now creating the primary data directory named "MyCompanyData" on the server's C: drive.
![Root Folder Creation](images/16%20(Stage%203).%20Create%20a%20file%20folder%20on%20the%20Windows%20server%20Vm.png)

#### Step 3.2: Departmental Sub-folders
Organizing the file server by creating sub-folders for HR, IT, Finance, and Public use.
![Departmental Sub-folders](images/17.%20Sub-folders%20on%20the%20file%20server.png)

#### Step 3.3: Security Groups
Creating Global Security Groups (e.g., Finance) in Active Directory to manage departmental access.
![Security Groups](images/18.%20Create%20security%20groups%20for%20each%20dep.png)

#### Step 3.4: User Creation
Populating the OUs with individual domain users (e.g., William Shake) for each department.
![User Creation](images/19.%20Create%20a%20user%20for%20each%20sec%20group.png)

#### Step 3.5: Group Membership
Adding the corresponding users to their respective security groups to simplify permission management.
![Group Membership](images/20.%20Add%20each%20corresponding%20user%20to%20the%20group.png)

#### Step 3.6: NTFS Permissions
Configuring NTFS security settings to grant specific groups (like HR) "Modify" permissions on their folders.
![NTFS Permissions](images/21.%20Config%20NTFS%20permissions%20(give%20HR%20users%20modified%20permiss).png)

#### Step 3.7: Access Control Enforcement
Removing or denying access to unauthorized users to ensure department data remains private.
![Access Control Enforcement](images/22.%20Deny%20access%20to%20HR%20for%20users%20not%20in%20HR.png)

#### Step 3.8: Share Permissions
Configuring Advanced Sharing permissions for "Everyone" to allow network access to the "MyCompanyData" folder.
![Share Permissions](images/23.%20Config%20share%20permissions.png)
