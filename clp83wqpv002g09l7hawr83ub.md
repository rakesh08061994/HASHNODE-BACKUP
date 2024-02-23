---
title: "Linux User and Group Management"
datePublished: Tue Nov 21 2023 09:01:40 GMT+0000 (Coordinated Universal Time)
cuid: clp83wqpv002g09l7hawr83ub
slug: linux-user-and-group-management
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/7okkFhxrxNw/upload/27c5b6df6b842cdf16151955ba103066.jpeg
tags: management, linux, devops, beginners, rhcsa

---

> The files mentioned in this article ex. (`/etc/passwd`, `/etc/group`, `/etc/shadow`, `/etc/gshadow`, `/etc/login.defs`, and `/etc/security/limits.conf`) play crucial roles in managing user accounts, groups, authentication, and system-wide settings in Linux.
> 
> Managing these files is vital for keeping your system secure, organizing who can do what, and adjusting how resources are used. Here's how:
> 
> 1. **Security:** These files hold the keys to user accounts and passwords. Managing them well keeps your system safe from unauthorized access.
>     
> 2. **User Control:** You decide who can access your system and what they can do. These files help create, change, and delete users and groups.
>     
> 3. **Access Management:** They control who gets to see, edit, or delete files and directories. By setting permissions based on users and groups, you control access to system resources.
>     
> 4. **System Settings:** You can tweak how your system operates. From setting password rules to limiting what resources users can consume, these files help fine-tune system-wide settings.
>     
> 
> By using commands to handle users and groups and tweaking these files, you maintain a secure and organized Linux system, controlling who does what and how they do it.

---

### /etc/passwd

The `/etc/passwd` file is a system file on Unix and Unix-like operating systems that stores basic information about users. Each line in the file represents a user account and contains several fields separated by colons (`:`). However, please note that the file might not contain passwords directly; instead, it typically contains hashed versions of passwords or placeholders for passwords, while the encrypted passwords themselves are often stored in a separate file like `/etc/shadow` for security reasons.

Here's an example of what a line in the `/etc/passwd` file might look like:

```bash
$ sudo vi /etc/passwd
ram:x:1007:1007:Ram,jaipur:/home/ram:/bin/bash
#username:password link:UID:GID:Gecos field:home directory:shell
```

Here's a breakdown of what each field typically represents:

1. `username`: The login name of the user.
    
2. `password`: Historically, this field used to contain the hashed password or a placeholder (like 'x' or '\*') to reference the password stored in `/etc/shadow`. On modern systems, the actual passwords are often stored in `/etc/shadow`.
    
3. `UID`: User ID, a unique number associated with the user.
    
4. `GID`: Group ID, the primary group ID associated with the user.
    
5. `Gecos field`: Usually contains additional information about the user (such as full name, phone number, etc.).
    
6. `home directory`: The user's home directory, the default location where the user is placed after logging in.
    
7. `shell`: The default shell or command interpreter for the user.
    

Please note that the format and fields might vary slightly based on the specific Unix-like system and its configuration. Also, modern systems often use more secure methods to store passwords and user information.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">This is a sample Example:</div>
</div>

> 1. `ram`: The username.
>     
> 2. `x`: Historically, this field used to contain the hashed password or a placeholder. However, modern systems typically store the actual passwords in the `/etc/shadow` file and use a placeholder (such as 'x') here.
>     
> 3. `1007`: User ID (UID). It's a unique number associated with the user.
>     
> 4. `1007`: Group ID (GID). It's the primary group ID associated with the user.
>     
> 5. `Ram,jaipur`: Gecos field. This field traditionally contains additional information about the user, such as the full name or other details.
>     
> 6. `/home/ram`: The user's home directory. This is the default location where the user is placed after logging in.
>     
> 7. `/bin/bash`: The default shell or command interpreter for the user. In this case, it's set to the Bash shell (`bash`), which is a common command-line shell on Unix-like systems.
>     
> 
> This line provides basic information about the user "ram," including the user ID, group ID, home directory, and default shell.

---

### /etc/shadow

The `/etc/shadow` file on Unix and Unix-like operating systems (such as Linux) is a crucial file for storing secure user account information, particularly encrypted passwords and other security-related data. It's a system file that typically contains sensitive information, and access to this file is restricted to privileged users like the root user.

Each line in the `/etc/shadow` file represents a single user's account information and consists of several fields separated by colons (`:`). Here's a typical structure:

```bash
$ sudo vi /etc/shadow
ram:$y$j9T$BNw5300R75LCUOZgpua3C.$F.K3EjrhguSetVNquWMRb7QE/Szz1mALfNYAJms3aT2:19682:0:99999:7:3:19692:
#username:hashed_password:last_password_change:minimum_days_between_changes:maximum_days_between_changes:Warn_days_before_expiry:additional_days:account_
expiry_date:reserved_field  
```

Here's a breakdown of what each field typically represents:

1. `username`: The login name of the user.
    
2. `hashed_password`: The hashed (encrypted) password for the user. This field used to contain the placeholder character 'x' in the `/etc/passwd` file, indicating that the password is stored in the `/etc/shadow` file for security reasons.
    
3. `last_password_change`: The number of days since January 1, 1970, since the password was last changed.
    
4. `minimum_days_between_changes`: The minimum number of days required between password changes.
    
5. `maximum_days_between_changes`: The maximum number of days the password is valid before a change is required.
    
6. `days_before_expiry`: The number of days before the password expires that the user is warned about it.
    
7. `additional_days`: Number of days after the password expires until the account is disabled.
    
8. `expiry_date`: The date when the account will be disabled (given in days since January 1, 1970, usually 0 for active accounts).
    
9. `reserved_field`: Reserved for future use.
    

The `/etc/shadow` file is only accessible by privileged users to prevent unauthorized access to sensitive user authentication data. It's a critical security measure to ensure that passwords and related information are stored securely on the system.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">This is a sample Example below:</div>
</div>

> 1. `ram`: The username.
>     
> 2. `$y$j9T$BNw5300R75LCUOZgpua3C.$F.K3EjrhguSetVNquWMRb7QE/Szz1mALfNYAJms3aT2`: This long string is the hashed (encrypted) password for the user "ram". It's stored in a hashed format for security reasons.
>     
> 3. `19682`: The number of days since January 1, 1970, when the password was last changed.
>     
> 4. `0`: Minimum number of days required between password changes.
>     
> 5. `99999`: Maximum number of days the password is valid before a change is required.
>     
> 6. `7`: Number of days before the password expires that the user is warned.
>     
> 7. `3`: Number of days after the password expires until the account is disabled.
>     
> 8. `19692`: Date when the account will be disabled (given in days since January 1, 1970).
>     
> 
> The hashed password is the long string that starts with `$y$`, and it's stored in a format specific to the system and the hashing algorithm used for password encryption. This format helps enhance security by protecting the actual password from being easily deciphered if the `/etc/shadow` file is accessed without proper privileges.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">There is an additional command to check password aging related information</div>
</div>

```bash
$ sudo chage -l ram
Last password change					            : Nov 21, 2023
Password expires					                : never
Password inactive					                : never
Account expires						                : never
Minimum number of days between password change		: 0
Maximum number of days between password change		: 99999
Number of days of warning before password expires	: 7
```

>   
> The command `chage -l ram` in a Unix-like system is used to display the password expiration information for a specific user, in this case, the user "ram." It provides details about the user's password aging information. When you run `chage -l ram`, it lists various parameters related to password expiration and aging for the user "ram."
> 
> Here's a breakdown of what each field in the output typically represents:
> 
> * `Last password change:` Indicates the date of the user's last password change.
>     
> * `Password expires:` Specifies when the user's current password will expire.
>     
> * `Password inactive:` Indicates the period of inactivity allowed for the password. If the password remains inactive for this duration, the account is locked.
>     
> * `Account expires:` Specifies the date when the user account will expire, if applicable.
>     
> * `Minimum number of days between password change:` The minimum number of days required before the user can change their password again.
>     
> * `Maximum number of days between password change:` The maximum number of days the password is valid before a change is required.
>     
> * `Number of days before password expires when the user is warned:` The number of days before the password expiration when the user receives a warning.
>     

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you want to change particular unit from users aging policy try this:</div>
</div>

```bash
$ sudo chage --help
```

> ```plaintext
> 
> Usage: chage [options] LOGIN
> 
> Options:
>   -d, --lastday LAST_DAY        set date of last password change to LAST_DAY
>   -E, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
>   -h, --help                    display this help message and exit
>   -i, --iso8601                 use YYYY-MM-DD when printing dates
>   -I, --inactive INACTIVE       set password inactive after expiration
>                                 to INACTIVE
>   -l, --list                    show account aging information
>   -m, --mindays MIN_DAYS        set minimum number of days before password
>                                 change to MIN_DAYS
>   -M, --maxdays MAX_DAYS        set maximum number of days before password
>                                 change to MAX_DAYS
>   -R, --root CHROOT_DIR         directory to chroot into
>   -W, --warndays WARN_DAYS      set expiration warning days to WARN_DAYS
> ```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Note: You can choose particular options to change a particular unit from the users aging policy:-</div>
</div>

```bash
#change the minimum age of days to 4 and warn days should be 5 days. (which means user Ram cant change his password immediately, he has to wait 4 days)
$ sudo chage -m 4 -W 5 ram

# when user sita first login, system forced to chage her password on first login immediately.
$ sudo chage -d 0 sita 

# change users overall aging policy at once:-
$ sudo chage sita
chage sita
Changing the aging information for sita
Enter the new value, or press ENTER for the default

	Minimum Password Age [0]: 
	Maximum Password Age [99999]: 
	Last Password Change (YYYY-MM-DD) [1970-01-01]: 
	Password Expiration Warning [7]: 
	Password Inactive [-1]: 
	Account Expiration Date (YYYY-MM-DD) [2024-12-01]: 
```

---

### /etc/group

The `/etc/group` file on Unix and Unix-like systems contains information about user groups. Each line in this file represents a different group and contains several fields separated by colons (`:`). Here's a typical structure of a line in the `/etc/group` file:

```bash
#group_name:password:GID:user_list
sita:x:1008:
develoer:x:1011:sita,ram,rajiv
```

Here's a breakdown of what each field typically represents:

1. `group_name`: The name of the group.
    
2. `password`: Historically, this field used to contain the hashed group password or a placeholder indicating where the password is stored. However, in modern systems, it's usually left blank (as 'x' or '\*') or contains a placeholder to indicate that the group password is stored in another location.
    
3. `GID`: Group ID, a unique number associated with the group.
    
4. `user_list`: A comma-separated list of usernames that are members of this group.
    

For example:

```bash
admins:x:1000:user1,user2,user3
```

This line indicates a group named "admins" with a GID of 1000, and users "user1," "user2," and "user3" are members of this group.

The `/etc/group` file helps manage user groups on the system, specifying which users belong to which groups and assigning them appropriate permissions and access levels to files, directories, and resources based on their group membership.

---

### /etc/gshadow

The `/etc/gshadow` file on Unix and Unix-like systems (such as Linux) is a file that stores secure group-related information, primarily the encrypted passwords or placeholders for passwords associated with user groups. This file is analogous to `/etc/shadow`, which stores user-specific secure information.

Each line in the `/etc/gshadow` file represents a group and contains several fields separated by colons (`:`). Here's a typical structure of a line in the `/etc/gshadow` file:

```bash
#group_name:encrypted_password:administrators:members
developer:$6$vI7osiNYqUF60pfC$J6ErgFJnsU/HzFYJSFxANbwpYAek7oeT35j/r4iLuxt.DsP3vZwbtdn/mchD1at0ba.66cpAoBctIeVWnRa/b0::rajiv,rakesh,rupesh,himanshu
```

Here's a breakdown of what each field typically represents:

1. `group_name`: The name of the group.
    
2. `encrypted_password`: Historically, similar to `/etc/shadow`, this field used to contain the hashed (encrypted) group password or a placeholder indicating where the password is stored. On modern systems, it might be left blank (`x` or `*`) or contain a placeholder to indicate that the password is stored elsewhere.
    
3. `administrators`: Additional administrators of the group (optional).
    
4. `members`: Additional members of the group (optional).
    

The `/etc/gshadow` file is generally only accessible by privileged users (usually the root user) for security reasons. It stores more sensitive group-related information than the `/etc/group` file and is used to enhance security by protecting group passwords or related data.

Please note that the contents and structure of system files like `/etc/gshadow` might vary slightly depending on the specific Unix-like system and its configuration.

---

### /etc/default/useradd

The `/etc/default/useradd` file on Unix-like systems contains default configuration settings for the `useradd` command, which is used to create new user accounts. This file sets default values for various parameters that are applied when a new user account is created unless explicitly overridden during the account creation process.

```bash
$ sudo vi /etc/default/useradd
# useradd defaults file
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=2024-12-01
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=yes
```

1. `GROUP=100`: Specifies the default group ID that will be assigned to new user accounts if no specific group ID is provided during account creation.
    
2. `HOME=/home`: Sets the default home directory for new users. New users will have their home directory created within the `/home` directory unless specified otherwise during account creation.
    
3. `INACTIVE=-1`: Defines the number of days after the password expires (or becomes inactive) before the account is disabled. A value of `-1` means that the account will not be disabled after the password expires.
    
4. `EXPIRE=2024-12-01`: Sets the expiration date for newly created accounts. New accounts will have an expiration date of December 1st, 2024, unless changed during account creation.
    
5. `SHELL=/bin/bash`: Specifies the default shell for new user accounts. New users will have `/bin/bash` set as their default shell.
    
6. `SKEL=/etc/skel`: Defines the skeleton directory (`/etc/skel`) that contains default files and directories that are copied to a new user's home directory when their account is created.
    
7. `CREATE_MAIL_SPOOL=yes`: Determines whether a mail spool (mailbox) should be created for the new user by default. Setting it to `yes` means a mail spool will be created.
    

These settings provide defaults that streamline the user creation process, ensuring consistency across new user accounts based on predefined configurations. However, administrators can override these defaults by specifying different values during the `useradd` command execution.

---

### /etc/skel

The `/etc/skel` directory in Unix-like systems serves as a template directory for new user accounts. When a new user is created, their home directory is typically populated with the contents of the `/etc/skel` directory. This directory contains default files and directories that are copied to the new user's home directory, providing a basic structure and initial configuration for their account.

By default, the `/etc/skel` directory might contain various standard configuration files, such as:

1. `.bashrc`: Configuration file for the Bash shell, defining user-specific settings and aliases for the command line.
    
2. `.bash_profile`: Another Bash configuration file that sets up the user's environment upon login.
    
3. `.profile`: A profile script that is executed upon login, configuring the user's environment variables and settings.
    
4. `.bash_logout`: Script executed when the user logs out of a Bash shell session, allowing for cleanup or additional actions.
    
5. **Other configuration files or directories**: Additional default files or directories that provide initial configurations, examples, or guidelines for new users.
    

The specific contents of `/etc/skel` may vary depending on the system and the administrator's preferences. Administrators often customize this directory to include specific settings or files that they want to be present in every new user's home directory.

To view the contents of the `/etc/skel` directory, you can use the `ls` command in a terminal:

```bash
$ sudo ls -a /etc/skel
.bash_logout  .bash_profile  .bashrc  .mozilla

# For a test create a new custom file "guidelines.txt"
$ sudo touch /etc/skel/guidelines.txt
$ sudo echo "Come office on time" >> /etc/skel/guidelines.txt

# Now create a new user and check whether new created file copied or not in users home directlry
$ sudo useradd rajiv
$ sudo ls -a /home/rajiv
.bash_logout  .bash_profile  .bashrc  .mozilla  guidelines.txt
```

This command will list the files and directories present in the `/etc/skel` directory, showing what will be copied into new user home directories upon their creation.

---

### /etc/login.defs

The `/etc/login.defs` file on Linux systems contains default settings and configurations related to user login, password aging, and other authentication-related parameters. It's a text file that administrators can modify to set system-wide defaults for user accounts.

Here's an example of what you might find inside the `/etc/login.defs` file along with explanations of some common parameters:

```plaintext
$ sudo vi /etc/login.defs - Configuration control definitions for the login package

MAIL_DIR        /var/spool/mail
# Password aging settings
PASS_MAX_DAYS   90  # Maximum number of days a password is valid
PASS_MIN_DAYS   7   # Minimum number of days allowed before changing a password
PASS_WARN_AGE   14  # Number of days before password expiration to warn the user

UMASK         022
HOME_MODE       0700

# User ID settings
UID_MIN         1000    # Minimum UID value for regular users
UID_MAX         60000   # Maximum UID value

# Group ID settings
GID_MIN         1000    # Minimum GID value for regular groups
GID_MAX         60000   # Maximum GID value

# Other settings
ENCRYPT_METHOD  SHA512  # Default encryption method for passwords
```

Common settings and their explanations:

* `MAIL_DIR:` Where user mail directory will be created on which location
    
* `PASS_MAX_DAYS`: Maximum number of days a password is valid before a user is required to change it.
    
* `PASS_MIN_DAYS`: Minimum number of days that need to pass before a user can change their password again.
    
* `PASS_WARN_AGE`: Number of days before password expiration that a user is warned about the impending expiration.
    
* `UID_MIN`, `UID_MAX`: Defines the minimum and maximum User ID values allowed for regular users.
    
* `GID_MIN`, `GID_MAX`: Specifies the minimum and maximum Group ID values allowed for regular groups.
    
* `ENCRYPT_METHOD`: Sets the default encryption method for passwords. It could be `MD5`, `SHA256`, `SHA512`, etc., depending on the system's configuration and security requirements.
    

These settings in `/etc/login.defs` help define system-wide parameters for user accounts, influencing password policies, UID/GID ranges, and encryption methods. Administrators can modify these settings to enforce specific password rules or set limits for user and group IDs on the system.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Solve the following Assignment questions related to /etc/login/defs file</div>
</div>

> Q1. I want to stop removing users default group during user deletation.
> 
> ```bash
> vi /etc/login.defs
> 
> USERGROUPS_ENAB no    # set no instead  of yes.
> :wq!
> ```
> 
> Q2. Give 5 second maximum time to login the user

> ```bash
> vi /etc/login.defs
> #
> # Max time in seconds for login(1)
> #
> LOGIN_TIMEOUT          5
> 
> 
> :wq!
> ```
> 
> Q3. Should not create users home directory on user creation.
> 
> ```bash
> vi /etc/login.defs
> # If useradd(8) should create home directories for users by default (non
> # system users only).
> # This option is overridden with the -M or -m flags on the useradd(8)
> # command-line.
> #
> CREATE_HOME     no
> 
> :wq!
> ```

---

### /etc/security/limits.conf

The `/etc/security/limits.conf` file on Unix-like systems, particularly Linux, is used to set system-wide limits and controls on resource allocation for user processes. It allows administrators to define constraints and limitations on various system resources, such as the maximum number of processes, maximum file size, CPU time, memory usage, and more for individual users or groups.

Each line in `limits.conf` typically follows a specific syntax, specifying a domain, type, item, value, and optional modifiers. Here's a general structure:

```bash
$ sudo vi /etc/security/limits.conf

<domain> <type> <item> <value>
```

* `<domain>`: Specifies the domain to which the limits apply. It can be a username, group name, wildcard (`@` for groups, `*` for all users), or `root` for the superuser.
    
* `<type>`: Indicates whether the entry is a hard limit (`hard`) that cannot be exceeded or a soft limit (`soft`) that can be temporarily exceeded.
    
* `<item>`: Represents the resource or system parameter being limited, such as `core` (core file size), `nofile` (open files), `nproc` (number of processes), etc.
    
* `<value>`: Specifies the value of the limit for the specified resource.
    

For instance, a line in `/etc/security/limits.conf` might look like this:

```bash
* hard nofile 4096
```

This line sets a hard limit (`hard`) for all users (`*`) on the number of open files (`nofile`) to `4096`.

The `limits.conf` file allows administrators to manage and control system resources to prevent abuse, ensure fair resource distribution, and enhance system stability and security. These limits apply to processes initiated by users or groups, helping to prevent system resource exhaustion, denial-of-service attacks, and other issues caused by uncontrolled resource usage.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Example questions answers related to the /etc/security/limits.conf file</div>
</div>

> Q1: To prevent users from logging in to multiple terminals or sessions simultaneously
> 
> ```bash
> $ sudo vi /etc/security/limits.conf
> *          hard    maxlogins       1
> ```
> 
> Q2. To restrict the file size a user can create.
> 
> ```bash
> *      hard      fsize      1000000  #(This is in KB (Kilo-Bytes) 1000000KB)
> ```