---
title: "Linux-Project (MANAGING LOCAL USERS AND
GROUPS)"
datePublished: Wed Jan 03 2024 12:55:39 GMT+0000 (Coordinated Universal Time)
cuid: clqxs7a3l000808jycfbbc4us
slug: linux-project-managing-local-users-and-groups
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/jLwVAUtLOAQ/upload/7bb4a90a0738391af5e15b280356cb9e.jpeg
tags: linux, server, projects

---

---

### **Introduction:**

In the dynamic landscape of corporate infrastructure, maintaining robust security measures while managing user access becomes pivotal. This article navigates through the process of establishing a secure Linux-based server system in the midst of organizational restructuring, focusing on user and group management and stringent password policy implementation.

### **Understanding the Scenario:**

As an IT administrator at GlobalTech Inc., overseeing a Linux-based server system, the recent restructuring necessitates the creation of new departments and user accounts. The primary objective is to fortify the security posture by setting up user accounts and groups effectively, limiting superuser access, enforcing strict directory access controls, and implementing stringent password policies.

---

1. ### **User and Group Setup:**
    

Creating user accounts and groups for the newly formed departments – R&D, Marketing, and Customer Support – is the initial step. This involves generating user accounts for each department and assigning appropriate privileges, facilitating streamlined access control by associating users with their respective departmental groups.

* Creating User Account:
    

```plaintext
# Create users for each department
sudo useradd RnDUser
sudo useradd MarketingUser
sudo useradd CustomerSupportUser
sudo groupadd RnDUserGroup
sudo groupadd MarketingUserGroup
sudo groupadd CustomerSupportUserGroup
sudo cat /etc/passwd
sudo cat /etc/group
```

* Creating Group Account (Assigning Users to Groups)
    

```plaintext
# Assign users to their respective departmental groups
sudo usermod -aG RnDUserGroup RnDUser
sudo usermod -aG MarketingUserGroup MarketingUser
sudo usermod -aG CustomerSupportUserGroup CustomerSupportUser

sudo cat /etc/group | grep -e RnDUserGroup -e MarketingUserGroup -e CustomerSupportUserGroup
```

---

1. ### **Superuser Access and Privileges:**
    

Limiting superuser access is crucial for maintaining system integrity. Configuring sudo access for department heads empowers them to perform essential administrative tasks without full root access. Educating users on responsible elevated privileges usage ensures the importance of limited access and minimizes potential risks.

* #### Configuring Sudo Access:
    
    Edit sudoers file using visudo (`sudo visudo`) and add lines for department heads:
    

```plaintext
RnDUser ALL=(ALL) /path/to/RnD_commands
MarketingUser ALL=(ALL) /path/to/Marketing_commands
CustomerSupportUser ALL=(ALL) /path/to/CustomerSupport_commands
```

---

1. ### **Directory Access Control:**
    

* #### Creating Directories:
    

```plaintext
# Create directories for each department
sudo mkdir /RnD_Data
sudo mkdir /Marketing_Content
sudo mkdir /CustomerSupport_Reports
```

* #### Setting Directory Permissions:
    

```plaintext
# Set permissions to restrict access
sudo chown -R :RnDUserGroup /RnD_Data
sudo chmod -R 770 /RnD_Data

sudo chown -R :MarketingUserGroup /Marketing_Content
sudo chmod -R 770 /Marketing_Content

sudo chown -R :CustomerSupportUserGroup /CustomerSupport_Reports
sudo chmod -R 770 /CustomerSupport_Reports
```

Establishing restricted access to department-specific directories – 'R&D\_Data', 'Marketing\_Content', and 'CustomerSupport\_Reports' – is imperative for data security. Setting permissions ensures that members within each department possess full access while restricting users from other departments to read-only or no access, fortifying data confidentiality.

1. ### **Password Policy Implementation:**
    

Implementing stringent password policies across the network adds an additional layer of security. Enforcing complexity, length, and expiration rules for all user accounts enhances system resilience. Regularly prompting users to update passwords aligns with policy compliance and reinforces security measures.

* #### \*\*Password Policy Implementation (\*\*Enforcing Password Policies):
    

```plaintext
# Open the login.defs file in a text editor (such as nano or vi)
sudo nano /etc/login.defs
```

Within the '/etc/login.defs' file, locate or add the following lines and adjust the values to meet your desired password policy:

```plaintext
# Set password complexity rules (example values)
PASS_MAX_DAYS   90  # Maximum password age
PASS_MIN_DAYS   7   # Minimum password age
PASS_MIN_LEN    10  # Minimum password length
FAIL_DELAY      3    # Delay in seconds after a failed login attempt
FAILLOG_ENAB    yes  # Enable recording of failed login attempts
LOGIN_RETRIES   3    # Maximum number of login retries before account is locked
UID_MIN         1000 # Minimum value for user IDs (UIDs)
UID_MAX         60000 # Maximum value for user IDs (UIDs)
GID_MIN         1000 # Minimum value for group IDs (GIDs)
GID_MAX         60000 # Maximum value for group IDs (GIDs)
ENV_PATH        PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV_SUPATH      PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
UMASK           077  # Default umask value for new files
CREATE_HOME     yes  # Create home directories for new users by default
```

---

1. ### Different scenarios along with the corresponding `chage` command options and their explanations:
    

* ### Scenario 1: Setting Maximum Password Age
    
    **Scenario:** You want to ensure that user accounts require password changes every 90 days.
    
    **Command:**
    

```plaintext
sudo chage -l RnDUser
sudo chage RnDUser
```

```bash
sudo chage -M 90 username
```

**Explanation:** This command sets the maximum password age (`-M`) for the specified user (`username`) to 90 days. Users will be prompted to change their passwords after 90 days for security reasons.

---

* ### Scenario 2: Specifying Password Expiry Date
    
    **Scenario:** You need to set a specific date (e.g., December 31, 2024) for a user's password to expire.
    
    **Command:**
    

```bash
sudo chage -E "2024-12-31" username
```

**Explanation:** Using the `-E` flag allows setting the exact password expiration date for the specified user (`username`). After the specified date, the user will be prompted to change their password upon login.

---

* ### Scenario 3: Setting Minimum Days Between Password Changes
    
    **Scenario:** Ensure users cannot change their passwords too frequently by setting a minimum of 7 days between password changes.
    
    **Command:**
    

```bash
sudo chage -m 7 username
```

**Explanation:** This command sets the minimum number of days (`-m`) required between password changes for the user (`username`). Users will need to wait at least 7 days before changing their passwords again.

---

* ### Scenario 4: Account Inactivity and Disabling
    
    **Scenario:** Automatically disable a user account after 30 days of inactivity.
    
    **Command:**
    

```bash
sudo chage -I 30 username
```

**Explanation:** Using `-I` specifies the number of days of inactivity (`30` in this case) after which the account will be automatically disabled if the user doesn't log in within that period.

---

* ### Scenario 5: Disabling Password Expiration
    
    **Scenario:** Temporarily disable password expiration for a user account.
    
    **Command:**
    

```bash
sudo chage -M -1 username
```

**Explanation:** Setting the maximum password age (`-M`) to `-1` effectively disables password expiration for the specified user (`username`). They won't be prompted to change their password based on age.

---

* ### Scenario 6: Forcing Password Change on Next Login
    
    **Scenario:** Require a user to change their password immediately upon next login.
    
    **Command:**
    

```bash
sudo chage -d 0 username
```

**Explanation:** Using `-d` with a value of `0` forces the user to change their password during the next login attempt by setting the number of days since the epoch to 0.

---

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">NOTE: Important files:</div>
</div>

```plaintext
sudo man useradd
```

1. `/etc/passwd:` Contains user account information like usernames, user IDs (UIDs), group IDs (GIDs), home directories, and default shells.
    
2. `/etc/shadow:` Stores encrypted user passwords and password aging details, providing enhanced security by safeguarding password hashes.
    
3. `/etc/group:` Lists all system groups, associating users with their respective groups, along with group IDs (GIDs) and membership details.
    
4. `/etc/sudoers:` Manages user privileges, determining who can execute commands as root or other users with elevated permissions using `sudo`.
    
5. `/etc/login.defs:` Defines system-wide defaults for user accounts and password policies, specifying aging parameters and other policies.
    
6. `/etc/security/pwquality.conf:` Configures password quality requirements like complexity, length, and expiration, affecting password creation and modification rules.
    
7. `/etc/pam.d/:` Contains Pluggable Authentication Module configuration files for various services, allowing flexible authentication policies.
    
8. `/etc/default/useradd:` Specifies default values for creating new user accounts, setting parameters for home directories, shells, etc.
    
9. `/etc/default/userdel:` Defines default behaviors for deleting user accounts, deciding whether to remove home directories or mail spools.
    
10. `/etc/default/usermod:` Sets default behaviors and options for modifying existing user accounts, facilitating changes to user attributes.
    

### **Conclusion:**

In the ever-evolving corporate landscape, the stability and security of Linux-based server systems remain paramount. By effectively managing user accounts and groups, limiting superuser access, implementing stringent directory access controls, and enforcing robust password policies, GlobalTech Inc. fortifies its defenses against potential threats while fostering a secure environment for critical data and operations.