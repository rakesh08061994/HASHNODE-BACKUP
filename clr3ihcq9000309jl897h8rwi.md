---
title: "Linux Rhcsa Complete Re Exam"
datePublished: Sun Jan 07 2024 13:10:10 GMT+0000 (Coordinated Universal Time)
cuid: clr3ihcq9000309jl897h8rwi
slug: linux-rhcsa-complete-re-exam

---

PROMPT: Assume you are an experienced Linux engineer with 20 years of experience. You will be given some inputs in the form of Linux topics and their subtopics. For each topic and subtopic, you need to provide the following output in below format:

• Theory:

• Interview Questions and Answers:

• Practical Questions and Answers:

Input is given below:

Imagine you are a seasoned content formatting editor with expertise in organizing and structuring technical documents. You have been provided with a comprehensive Microsoft Word document containing detailed notes on various Linux topics and subtopics. However, the current formatting and organization of the text are not up to the mark. Your task is to meticulously arrange and format the text to ensure it is well-structured, easy to navigate, and aesthetically pleasing. Please transform this document into a perfectly formatted and structured resource.

This is MS-Word file:

---

**Links:**

1. * **Soft Link:**
        
        * [**Theory:** A soft link, also known as a symbolic link, is a special kind of file that points to another file or directory](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>1</sup>](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/). [It is similar to a shortcut in Windows](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>2</sup>](https://engineeringinterviewquestions.com/red-hat-linux-system-administration-interview-questions-answers/). [Soft links can link across different file systems, but if the original file is deleted or moved, the soft link will not work correctly](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>1</sup>](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/).
            
        * **Interview Questions and Answers:**
            
            * Q: What is a soft link in Linux?
                
            * [A: A soft link, also known as a symbolic link, is a file that points to another file or directory](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>3</sup>](https://www.linuxcareers.com/resources/blog/2023/02/linux-interview-questions-top-101-questions-and-answers/).
                
        * **Practical Questions and Answers:**
            
            * Q: How do you create a soft link in Linux?
                
            * A: You can create a soft link using the `ln -s` command. [For example, `ln -s source_file soft_link`](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>4</sup>](https://www.cyberciti.biz/faq/creating-soft-link-or-symbolic-link/).
                
    * **Hard Link:**
        
        * [**Theory:** A hard link is a directory entry that points to the data of an original file](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>5</sup>](https://askubuntu.com/questions/108771/what-is-the-difference-between-a-hard-link-and-a-symbolic-link). [Hard links are more flexible and remain linked even if the original or linked files are moved throughout the file system, although they are unable to cross different file systems](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>1</sup>](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/).
            
        * **Interview Questions and Answers:**
            
            * Q: What is a hard link in Linux?
                
            * [A: A hard link is a directory entry that points to the data of an original file](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>3</sup>](https://www.linuxcareers.com/resources/blog/2023/02/linux-interview-questions-top-101-questions-and-answers/).
                
        * **Practical Questions and Answers:**
            
            * Q: How do you create a hard link in Linux?
                
            * A: You can create a hard link using the `ln` command. [For example, `ln source_file hard_link`](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>6</sup>](https://superuser.com/questions/364993/what-is-the-typical-real-use-case-or-application-of-symbolic-hard-links-in-linux).
                
    * **Find command:**
        
        * [**Theory:** The `find` command in Linux is a dynamic utility designed for comprehensive file and directory searches within a hierarchical structure](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>7</sup>](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/). [It allows users to search by name, size, modification time, or content](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>7</sup>](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/).
            
        * **Interview Questions and Answers:**
            
            * Q: What is the `find` command in Linux?
                
            * [A: The `find` command in Linux is a utility for searching files and directories based on various criteria such as name, size, modification time, and more](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>3</sup>](https://www.linuxcareers.com/resources/blog/2023/02/linux-interview-questions-top-101-questions-and-answers/).
                
        * **Practical Questions and Answers:**
            
            * Q: How do you use the `find` command to search for a file in Linux?
                
            * A: To search for a file by its name, use the `-name` option followed by the name of the file you are searching for. [For example, `find /home/linuxize -type f -name document.pdf`](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>8</sup>](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/).
                
    * **Grep command:**
        
        * **Theory:** The `grep` command in Linux is a string and pattern matching utility that displays matching lines from multiple files. [It also works with piped output from other commands](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>9</sup>](https://www.howtogeek.com/496056/how-to-use-the-grep-command-on-linux/).
            
        * **Interview Questions and Answers:**
            
            * Q: What is the `grep` command in Linux?
                
            * [A: The `grep` command in Linux is a string and pattern matching utility that displays matching lines from multiple files](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>10</sup>](https://testbook.com/interview/linux-commands-interview-questions).
                
        * **Practical Questions and Answers:**
            
            * Q: How do you use the `grep` command to search for a string within a file?
                
            * A: To search for a string within a file, pass the search term and the file name on the command line. [For example, `grep "search term" filename`](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>9</sup>](https://www.howtogeek.com/496056/how-to-use-the-grep-command-on-linux/).
                
    * **Find vs Locate:**
        
        * **Theory:** Both `find` and `locate` are used to search for files in a Linux system. [The `find` command searches for files in a directory hierarchy based on a user-given expression](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>7</sup>](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/). [On the other hand, `locate` reads one or more databases prepared by `updatedb` and writes file names matching at least one of the pattern](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>11</sup>](https://www.simplilearn.com/linux-commands-interview-questions-article).
            
        * **Interview Questions and Answers:**
            
            * Q: What is the difference between `find` and `locate` commands in Linux?
                
            * [A: The `find` command searches for files in a directory hierarchy based on a user-given expression, while `locate` reads one or more databases prepared by `updatedb` and writes file names matching at least one of the pattern](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>11</sup>](https://www.simplilearn.com/linux-commands-interview-questions-article).
                
        * **Practical Questions and Answers:**
            
            * Q: How do you use the `locate` command to search for a file in Linux?
                
            * A: To search for a file using `locate`, simply pass the name of the file as an argument. [For example, `locate filename`](https://www.geeksforgeeks.org/soft-hard-links-unixlinux/)[<sup>11</sup>](https://www.simplilearn.com/linux-commands-interview-questions-article).
                

---

**1\. Input Output Redirection, Tee Command, vi vs vim:**

* **Theory:** In Linux, we can redirect the input and output of commands to and from files, and chain commands together using pipes (`|`). The `tee` command reads from standard input and writes to standard output and files. `vi` is a text editor in Linux, while `vim` is an improved version of `vi` with more features.
    
* **Interview Questions and Answers:**
    
    * Q: What is the difference between `vi` and `vim`?
        
    * A: `vim` stands for Vi IMproved. It’s an implementation of the `vi` editor with many additional features, including syntax highlighting, comprehensive help, improved search, code folding, and more.
        
* **Practical Questions and Answers:**
    
    * Q: How to save a file in `vi` or `vim`?
        
    * A: Press `Esc` and then type `:wq` to save and quit.
        

**2\. Man vs Pinfo Command:**

* **Theory:** `man` is a command to display the user manual of any command that we can run on the terminal. It provides a detailed view of the command. `pinfo` is a command that displays info pages in color.
    
* **Interview Questions and Answers:**
    
    * Q: What is the difference between `man` and `pinfo`?
        
    * A: `man` displays the manual pages, while `pinfo` displays info documents. `pinfo` provides a more detailed and interactive documentation than `man`.
        
* **Practical Questions and Answers:**
    
    * Q: How to get information about the `ls` command?
        
    * A: You can use either `man ls` or `pinfo ls`.
        

**3\. Head vs Tail:**

* **Theory:** `head` and `tail` are commands for outputting the beginning and end of files respectively.
    
* **Interview Questions and Answers:**
    
    * Q: How to view the first 5 lines of a file using `head`?
        
    * A: `head -n 5 filename`.
        
* **Practical Questions and Answers:**
    
    * Q: How to view the last 5 lines of a file using `tail`?
        
    * A: `tail -n 5 filename`.
        

**4\. Less vs More:**

* **Theory:** `less` and `more` are commands for viewing the contents of a file or output of a command in a page by page manner. `less` command is more powerful than `more` command because `less` allows backward navigation in the file but `more` doesn’t.
    
* **Interview Questions and Answers:**
    
    * Q: What is the difference between `less` and `more`?
        
    * A: `less` allows backward navigation in the file but `more` doesn’t.
        
* **Practical Questions and Answers:**
    
    * Q: How to open a file using `less`?
        
    * A: `less filename`.
        

**5\. Use of | symbol in Linux, how to use it:**

* **Theory:** The pipe (`|`) symbol in Linux is used to combine two or more commands, and in this, the output of one command acts as input to another command, and this command’s output may act as input to the next command and so on.
    
* **Interview Questions and Answers:**
    
    * Q: How does the pipe (`|`) symbol work in Linux?
        
    * A: It takes the output of the command on the left and uses it as input for the command on the right.
        
* **Practical Questions and Answers:**
    
    * Q: How to use the pipe symbol to combine commands?
        
    * A: `command1 | command2`. The output of `command1` is used as the input for `command2`.
        

---

![Linux](https://www.bing.com/th?id=OSK.975a9c7d8b6395ef609f5fb5e47123d5&pid=cdx&w=320&h=189&c=7&rs=1 align="left")

![](https://www.bing.com/th?id=OSK.975a9c7d8b6395ef609f5fb5e47123d5&pid=cdx&w=159&h=189&c=7 align="left")

Explore

Sure, let’s go through each of the subtopics:

1. **Types of User**
    
    * [**Theory**: In Linux, there are three types of users: root, regular, and service](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>1</sup>](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html). [The root user, also known as the superuser, has access to the entire Linux system and can perform any administrative task](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>1</sup>](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html). [Regular users have limited privileges and are intended for routine tasks](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>1</sup>](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html). [Service accounts are used by services to run processes and execute functions](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>1</sup>](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html).
        
    * [**Interview Questions and Answers**: A common interview question might be "What are the different types of users in a Linux system and what are their roles?"](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>2</sup>](https://www.geeksforgeeks.org/users-in-linux-system-administration/). The answer would be similar to the theory explanation above.
        
    * **Practical Questions and Answers**: A practical question could be “How do you create a new user in Linux and assign it to a group?” The answer would involve using the `useradd` command to create a new user and the `usermod` command to add the user to a group.
        
2. **Types of Shell**
    
    * [**Theory**: There are several shells available for Linux systems like BASH (Bourne Again SHell), which is the most widely used shell in Linux systems, and CSH (C SHell), whose syntax and usage are very similar to the C programming language](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>3</sup>](https://www.geeksforgeeks.org/introduction-linux-shell-shell-scripting/).
        
    * [**Interview Questions and Answers**: An interview question might be "What are the different types of shells in Linux and what are their uses?"](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>4</sup>](https://www.geeksforgeeks.org/linux-interview-questions/). The answer would be similar to the theory explanation above.
        
    * **Practical Questions and Answers**: A practical question could be “How do you change the default shell for a user in Linux?” The answer would involve using the `chsh` command.
        
3. **Primary Group vs Supplementary Group**
    
    * [**Theory**: In Linux, each user must belong to a primary group, which is used to decide which files are created by which users](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>5</sup>](https://www.baeldung.com/linux/primary-vs-secondary-groups). [Users can also belong to up to 15 supplementary groups, which are used for users to share files between them](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>5</sup>](https://www.baeldung.com/linux/primary-vs-secondary-groups).
        
    * [**Interview Questions and Answers**: An interview question might be "What is the difference between a primary group and a supplementary group in Linux?"](https://www.computernetworkingnotes.com/linux-tutorials/types-of-users-in-linux-explained-with-accounts.html)[<sup>6</sup>](https://unix.stackexchange.com/questions/605531/primary-vs-secondary-groups-in-linux). The answer would be similar to the theory explanation above.
        
    * **Practical Questions and Answers**: A practical question could be “How do you add a user to a supplementary group in Linux?” The answer would involve using the `usermod` command with the `-a` (append) and `-G` (groups) options.
        
4. **UID and GID Range**
    
    * **Theory**: In Linux, each user and group is identified by a unique ID. The User ID (UID) is a unique number assigned to each user, and the Group ID (GID) is a unique number assigned to each group. The UID and GID ranges can vary depending on the system configuration, but typically, system users and groups (like root) have UIDs and GIDs in the range of 0-999, and regular users and groups have UIDs and GIDs in the range of 1000 and above.
        
    * **Interview Questions and Answers**: An interview question might be “What is the significance of UID and GID in Linux and what are their typical ranges?” The answer would be similar to the theory explanation above.
        
    * **Practical Questions and Answers**: A practical question could be “How do you find the UID and GID of a user in Linux?” The answer would involve using the `id` command.
        

**/etc/passwd, /etc/group, /etc/shadow, /etc/gshadow file format**

* Theory: These files are crucial for user management in Linux. `/etc/passwd` stores user account information. `/etc/group` contains group membership information. `/etc/shadow` stores encrypted user passwords, and `/etc/gshadow` holds group passwords.
    
* Interview Questions and Answers:
    
    * Q: What is the purpose of the `/etc/passwd` file?
        
    * A: The `/etc/passwd` file stores essential information for each user account, including the username, user ID, group ID, home directory, shell, etc.
        
* Practical Questions and Answers:
    
    * Q: How can you view the contents of the `/etc/passwd` file?
        
    * A: You can use the `cat /etc/passwd` command to view the contents of the file.
        

1. **How to gain sudo access**
    

* Theory: Sudo access allows a permitted user to execute a command as the superuser or another user. To grant sudo access, you need to add the user to the sudo group or specify privileges in the sudoers file.
    
* Interview Questions and Answers:
    
    * Q: How can you give a user sudo privileges?
        
    * A: You can add the user to the sudo group using the command `usermod -aG sudo username`, or specify the user in the sudoers file with the `visudo` command.
        
* Practical Questions and Answers:
    
    * Q: How can you check if a user has sudo access?
        
    * A: Run a command with sudo. If the user has sudo access, they will be asked for their password. If not, they will receive a message that they are not in the sudoers file.
        

**3\. How to configure password policy for a user and all new users**

* Theory: Password policies can be set in the `/etc/login.defs` file or by using the `pam_`[`pwquality.so`](http://pwquality.so) module. Policies can include minimum length, complexity requirements, and password expiration.
    
* Interview Questions and Answers:
    
    * Q: How can you enforce a minimum password length?
        
    * A: You can set a minimum password length in the `/etc/login.defs` file or by configuring the `pam_`[`pwquality.so`](http://pwquality.so) module.
        
* Practical Questions and Answers:
    
    * Q: How can you set a minimum password length of 10 characters?
        
    * A: Edit the `/etc/pam.d/common-password` file and add `minlen=10` to the line with `pam_`[`pwquality.so`](http://pwquality.so).
        

**4\. How to change existing user’s information with usermod**

* Theory: The `usermod` command allows you to modify an existing user’s information, such as home directory, login name, and group membership.
    
* Interview Questions and Answers:
    
    * Q: How can you change a user’s home directory using `usermod`?
        
    * A: Use the command `usermod -d /new/home/dir username` to change the user’s home directory.
        
* Practical Questions and Answers:
    
    * Q: How can you add a user to a new group?
        
    * A: Use the command `usermod -aG groupname username` to add the user to a new group.
        

**5\. Check currently logged in user’s information**

* Theory: The `whoami` command shows the current user, and `id` displays the user’s UID, GID, and group memberships.
    
* Interview Questions and Answers:
    
    * Q: How can you check the current user’s group memberships?
        
    * A: Use the `id` command to display the current user’s UID, GID, and groups.
        
* Practical Questions and Answers:
    
    * Q: How can you find out who is currently logged in?
        
    * A: Use the `whoami` command to display the current user.
        

**6\. Check failed login attempt**

* Theory: Failed login attempts are logged in the `/var/log/auth.log` file. The `lastb` command shows the last failed login attempts.
    
* Interview Questions and Answers:
    
    * Q: How can you check for failed login attempts?
        
    * A: You can use the `lastb` command or check the `/var/log/auth.log` file.
        
* Practical Questions and Answers:
    
    * Q: How can you display the last five failed login attempts?
        
    * A: Use the command `lastb | head -n 5` to display the last five failed login attempts.
        
    
    **Use of skeleton data**
    
    * [**Theory**: The skeleton directory in Linux, typically `/etc/skel`, is used to initialize the home directory when a user is first created](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>1</sup>](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>2</sup>](https://unix.stackexchange.com/questions/285708/skeleton-directory-how-to-add-my-own-directories). It contains default configuration files and directories. [When a new user is added, the files and directories from the skeleton directory are copied to the user’s home directory](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>1</sup>](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/).
        
    * **Interview Questions and Answers**:
        
        * Q: What is the purpose of the skeleton directory in Linux?
            
        * A: The skeleton directory, usually `/etc/skel`, is used to initialize the home directory when a user is first created. [It contains default configuration files and directories that are copied to the user’s home directory upon creation](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>1</sup>](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/).
            
    * **Practical Questions and Answers**:
        
        * Q: How can you add your own directories to the skeleton directory?
            
        * A: You can simply create the desired directory structure under `/etc/skel`. [These directories will then be copied to the home directory of any newly created user](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>2</sup>](https://unix.stackexchange.com/questions/285708/skeleton-directory-how-to-add-my-own-directories).
            
* **.bashrc vs .bash\_profile**
    
    * **Theory**: `.bashrc` and `.bash_profile` are two important files that control the behavior of Bash. When an interactive shell is started, `.bashrc` is read. On the other hand, `.bash_profile` is executed for login shells. [In other words, `.bashrc` is executed in every new shell opened, and `.bash_profile` is executed once when you log in to the terminal](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>3</sup>](https://www.baeldung.com/linux/bashrc-vs-bash-profile-vs-profile)[<sup>4</sup>](https://linuxize.com/post/bashrc-vs-bash-profile/).
        
    * **Interview Questions and Answers**:
        
        * Q: What is the difference between `.bashrc` and `.bash_profile`?
            
        * [A: `.bashrc` is executed in every new shell opened and `.bash_profile` is executed once when you log in to the terminal](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>3</sup>](https://www.baeldung.com/linux/bashrc-vs-bash-profile-vs-profile)[<sup>4</sup>](https://linuxize.com/post/bashrc-vs-bash-profile/).
            
    * **Practical Questions and Answers**:
        
        * Q: Where should you place environment variables, in `.bashrc` or `.bash_profile`?
            
        * [A: Environment variables should generally be placed in `.bash_profile`](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>4</sup>](https://linuxize.com/post/bashrc-vs-bash-profile/).
            
* **How to change environment variable, how to modify PATH variable**
    
    * **Theory**: Environment variables in Linux can be set using the `export` command. [The `PATH` variable, which specifies directories to search for executable files, can be modified by adding or removing paths in this variable](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>5</sup>](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/)[<sup>6</sup>](https://phoenixnap.com/kb/linux-set-environment-variable)[<sup>7</sup>](https://stackoverflow.com/questions/45502996/how-to-set-environment-variable-in-linux-permanently)[<sup>8</sup>](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable)[<sup>9</sup>](https://superuser.com/questions/488173/how-can-i-edit-the-path-on-linux).
        
    * **Interview Questions and Answers**:
        
        * Q: How can you add a directory to the `PATH` variable in Linux?
            
        * [A: You can add a directory to the `PATH` variable by using the `export` command like this: `export PATH=$PATH:/path/to/directory`](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>8</sup>](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable)[<sup>9</sup>](https://superuser.com/questions/488173/how-can-i-edit-the-path-on-linux).
            
    * **Practical Questions and Answers**:
        
        * Q: How can you make the changes to the `PATH` variable persistent across sessions?
            
        * [A: To make the changes persistent, you can add the `export` command to a shell startup file like `~/.bashrc` or `~/.bash_profile`](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>6</sup>](https://phoenixnap.com/kb/linux-set-environment-variable).
            
* **env, printenv, export command**
    
    * **Theory**: `env`, `printenv`, and `export` are commands used to interact with environment variables in Linux. `env` can run another program in a custom environment. `printenv` [can print all or specified environment variables`export` is used to set environment variables](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>10</sup>](https://linuxconfig.org/how-to-print-environment-variables-on-linux)[<sup>11</sup>](https://linuxhandbook.com/print-environment-variables/)[<sup>5</sup>](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/)[<sup>12</sup>](https://unix.stackexchange.com/questions/469543/what-environment-variables-shell-variables-do-env-and-printenv-show).
        
    * **Interview Questions and Answers**:
        
        * Q: What is the difference between `env`, `printenv`, and `export` commands in Linux?
            
        * [A: `env` can run another program in a custom environment, `printenv` can print all or specified environment variables, and `export` is used to set environment variables](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>10</sup>](https://linuxconfig.org/how-to-print-environment-variables-on-linux)[<sup>11</sup>](https://linuxhandbook.com/print-environment-variables/)[<sup>5</sup>](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/)[<sup>12</sup>](https://unix.stackexchange.com/questions/469543/what-environment-variables-shell-variables-do-env-and-printenv-show).
            
    * **Practical Questions and Answers**:
        
        * Q: How can you print all environment variables in Linux?
            
        * [A: You can print all environment variables using the `printenv` command without any arguments](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>11</sup>](https://linuxhandbook.com/print-environment-variables/).
            
* **login.defs file usage, /etc/default/useradd file usage**
    
    * [**Theory**: `/etc/login.defs` provides default configuration information for several user account parameters](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>13</sup>](https://linuxtect.com/linux-etc-login-defs-tutorial/)[<sup>14</sup>](https://www.thegeekdiary.com/understanding-etclogin-defs-file/)[`/etc/default/useradd` sets the default values for the `useradd` command](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>15</sup>](https://unix.stackexchange.com/questions/192506/what-variables-are-valid-within-etc-default-useradd-file)[<sup>16</sup>](https://www.man7.org/linux/man-pages/man8/useradd.8.html)[<sup>17</sup>](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/)[<sup>18</sup>](https://www.linuxfromscratch.org/blfs/view/5.1/postlfs/skel.html)[<sup>19</sup>](https://www.ionos.com/digitalguide/server/configuration/linux-useradd-command/).
        
    * **Interview Questions and Answers**:
        
        * Q: What is the purpose of the `/etc/login.defs` and `/etc/default/useradd` files in Linux?
            
        * A: `/etc/login.defs` [provides default configuration information for several user account parameters`/etc/default/useradd` sets the default values for the `useradd` command](https://www.thegeekdiary.com/understanding-the-etc-skel-directory-in-linux/)[<sup>13</sup>](https://linuxtect.com/linux-etc-login-defs-tutorial/)[<sup>14</sup>](https://www.thegeekdiary.com/understanding-etclogin-defs-file/)[<sup>15</sup>](https://unix.stackexchange.com/questions/192506/what-variables-are-valid-within-etc-default-useradd-file)[<sup>16</sup>](https://www.man7.org/linux/man-pages/man8/useradd.8.html)[<sup>17</sup>](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/)[<sup>18</sup>](https://www.linuxfromscratch.org/blfs/view/5.1/postlfs/skel.html)[<sup>19</sup>](https://www.ionos.com/digitalguide/server/configuration/linux-useradd-command/).
            
    * **Practical Questions and Answers**:
        
        * Q: How can you change the default home directory for new users in Linux?
            
        * [A: You can change the default home directory for new users by modifying the `HOME` variable in the `/etc/default/useradd` file](https://www.man7.org/linux/man-pages/man8/useradd.8.html)[<sup>16</sup>](https://www.man7.org/linux/man-pages/man8/useradd.8.html).
            

---

**4\. Permission:**

* **Theory:**
    
    * **Types of Permission:** In Linux, there are three types of permissions: read (`r`), write (`w`), and execute (`x`). These permissions can be set for three types of users: the file owner, the group members, and others.
        
    * **rwx Permission Explanation and Meaning:** `rwx` stands for read, write, and execute permissions. `r` allows the file to be read, `w` allows the file to be written or modified, and `x` allows the file to be executed.
        
    * **How to Change Permission Symbolically and Numerically:** Permissions can be changed using the `chmod` command. Symbolically, `chmod u+x filename` would give the user execute permission. Numerically, permissions are represented as a three-digit number, where each digit is the sum of `r`\=4, `w`\=2, `x`\=1. For example, `chmod 755 filename` sets read, write, execute for the user, and read and execute for the group and others.
        
    * **How to Change Owner and Group Owner:** The `chown` command is used to change the owner of a file/directory, and the `chgrp` command is used to change the group. For example, `chown newowner filename` and `chgrp newgroup filename`.
        
    * **How File and Directory Get Default Permission \[umask\]:** The `umask` command is used to determine the default permission set when a new file or directory is created. For example, a common `umask` value is `022`, which gives the owner full permissions and only read and execute permissions to the group and others.
        
    * **How to Change Umask Value Permanently for Particular User, All User, New User:** The `umask` value can be changed permanently by adding a `umask` command to a shell startup file like `~/.bashrc` or `/etc/profile`.
        
    * **ACL (Access Control Lists):** ACLs provide more granular permissions than the standard user/group/others system. They can be set for individual users or groups using the `setfacl` command, like `setfacl -m u:username:rwx filename`.
        
    * **Default ACL and Clearing ACL Attributes:** Default ACLs are used when new objects are created. They can be set with `setfacl -d -m u:username:rwx dirname`. All ACL attributes can be removed with `setfacl -b filename`.
        
    * **Special Permissions (suid, sgid, stickybit):** These permissions provide additional controls. SUID (`s`) allows a program to run as the owner, SGID (`s`) makes new files inherit the group of the directory, and the sticky bit (`t`) restricts deletion of files to the owner.
        
    * **Linux Attributes and chattr/lsattr Commands:** Linux supports extended file attributes like immutability. These can be changed with `chattr` and viewed with `lsattr`.
        
    * **Giving Sudo Power and NOPASSWD Option:** Users can be given sudo privileges by adding them to the `/etc/sudoers` file. The `NOPASSWD` option allows them to use sudo without entering their password.
        
* **Interview Questions and Answers:**
    
    * **Q:** What does `chmod 644 filename` do?
        
    * **A:** It sets read and write permissions for the file owner, and only read permission for the group and others.
        
    * **Q:** How would you change the owner of a file?
        
    * **A:** I would use the `chown` command, like `chown newowner filename`.
        
    * **Q:** How would you give read and write permissions to a specific user using ACLs?
        
    * **A:** I would use the `setfacl` command, like `setfacl -m u:username:rw filename`.
        
    * **Q:** What does the sticky bit do and how would you set it?
        
    * **A:** The sticky bit restricts deletion of files in a directory to their owners. It can be set with `chmod +t dirname`.
        
* **Practical Questions and Answers:**
    
    * **Q:** Write a command to give all permissions to the owner and only read and execute permissions to the group and others.
        
    * **A:** The command would be `chmod 755 filename`.
        
    * **Q:** How would you set the default permissions for new files to `rw-rw-r--`?
        
    * **A:** I would use the `umask` command with the value `022`.
        
    * **Q:** Write a command to make a file immutable.
        
    * **A:** The command would be `chattr +i filename`.
        
    * **Q:** How would you give a user sudo privileges without a password? **A:** I would add a line to the `/etc/sudoers` file like `username ALL=(ALL) NOPASSWD:ALL`.
        

---

**Topic: Process Management & Service**

1. **PID and PPID**
    
    * **Theory**: PID stands for Process IDentifier, a unique number that identifies a process in the system. PPID is the Parent Process IDentifier, the unique number of the process’s parent.
        
    * **Interview Q&A**:
        
        * Q: What are PID and PPID in Linux?
            
        * A: PID is the unique identifier for a running process, while PPID is the unique identifier for its parent process.
            
    * **Practical Q&A**:
        
        * Q: How can you find the PID and PPID of a process in Linux?
            
        * A: You can use the `ps` command to display PIDs and PPIDs. For example, `ps -ef` will display a full listing of all processes, including their PIDs and PPIDs.
            
2. **System Boot and Poweroff**
    
    * **Theory**: The first process that starts when a Linux system boots is the `init` process with PID 1. When a Linux system powers off, the last process to shut down is typically also the `init` process.
        
    * **Interview Q&A**:
        
        * Q: Which process starts first and ends last during a Linux system’s lifecycle?
            
        * A: The `init` process is the first to start (with PID 1) and the last to end during a Linux system’s lifecycle.
            
    * **Practical Q&A**:
        
        * Q: How can you verify that the `init` process is the first to start and last to end on a Linux system?
            
        * A: You can use the `ps` command to check the status of the `init` process. For example, `ps -p 1` will show you the status of the process with PID 1, which is typically the `init` process.
            
3. **Process Listing Commands**
    
    * **Theory**: `ps`, `top`, and `htop` are commands used to display information about processes. `ps` provides a snapshot of current processes, `top` displays real-time information, and `htop` shows an interactive process viewer.
        
    * **Interview Q&A**:
        
        * Q: What are the differences between `ps`, `top`, and `htop`?
            
        * A: `ps` provides a static snapshot of current processes, `top` updates its display in real-time, and `htop` provides an interactive interface for process management.
            
    * **Practical Q&A**:
        
        * Q: How would you use `ps`, `top`, and `htop` to monitor processes on a Linux system?
            
        * A: `ps -ef` for a full listing of processes, `top` to monitor processes in real-time, and `htop` for an interactive view.
            
4. **Memory Usage**
    
    * **Theory**: The `free` command in Linux is used to check memory usage, including used and available RAM.
        
    * **Interview Q&A**:
        
        * Q: How can you check memory usage on a Linux system?
            
        * A: You can use the `free` command to display the amount of free and used memory on your system.
            
    * **Practical Q&A**:
        
        * Q: Show me how to check the amount of free RAM on a Linux system.
            
        * A: You can use the command `free -h` to display memory usage in a human-readable format.
            
5. **Process Signals**
    
    * **Theory**: Signals are software interrupts that provide a way to handle asynchronous events. For example, the `SIGKILL` signal forces a process to terminate immediately.
        
    * **Interview Q&A**:
        
        * Q: What are process signals in Linux and give some examples?
            
        * A: Process signals are software interrupts for handling events. Examples include `SIGKILL` for terminating a process and `SIGSTOP` for pausing a process.
            
    * **Practical Q&A**:
        
        * Q: How would you send a `SIGKILL` signal to a process with PID 123?
            
        * A: You can use the command `kill -9 123` to send a `SIGKILL` signal to the process.
            
6. **HANGUP Signal**
    
    * **Theory**: The `SIGHUP` (hangup) signal is sent to a process when its controlling terminal is closed. It was originally designed to notify the process that the user had disconnected, but is often used to instruct processes to reload their configuration files.
        
    * **Interview Q&A**:
        
        * Q: What is the `SIGHUP` signal and when is it used?
            
        * A: `SIGHUP` is a signal sent to a process when its controlling terminal is closed. It’s often used to instruct processes to reload configuration files.
            
    * **Practical Q&A**:
        
        * Q: How would you send a `SIGHUP` signal to a process with PID 123?
            
        * A: You can use the command `kill -HUP 123` to send a `SIGHUP` signal to the process.
            
7. **Passing Signals**
    
    * **Theory**: The `kill` command is used to send signals to processes. You can specify the signal either by name (e.g., `-HUP`) or by number (e.g., `-1`).
        
    * **Interview Q&A**:
        
        * Q: How can you send a signal to a process in Linux?
            
        * A: You can use the `kill` command followed by the signal name or number and the PID of the process.
            
    * **Practical Q&A**:
        
        * Q: How would you send a `SIGSTOP` signal to a process with PID 123?
            
        * A: You can use the command `kill -STOP 123` to send a `SIGSTOP` signal to the process.
            
8. **PID and PPID**
    
    * **Theory**: PID stands for Process IDentifier, a unique number that identifies a process in the system. PPID is the Parent Process IDentifier, the unique number of the process’s parent.
        
    * **Interview Q&A**:
        
        * Q: What are PID and PPID in Linux?
            
        * A: PID is the unique identifier for a running process, while PPID is the unique identifier for its parent process.
            
    * **Practical Q&A**:
        
        * Q: How can you find the PID and PPID of a process in Linux?
            
        * A: You can use the `ps` command to display PIDs and PPIDs. For example, `ps -ef` will display a full listing of all processes, including their PIDs and PPIDs.
            
9. **Process State Types**
    
    * **Theory**: Linux processes can be in one of several states: Running, Sleeping, Stopped, Zombie, or Uninterruptible sleep.
        
    * **Interview Q&A**:
        
        * Q: What are the different states a process can be in Linux?
            
        * A: A process in Linux can be in one of several states: Running, Sleeping, Stopped, Zombie, or Uninterruptible sleep.
            
    * **Practical Q&A**:
        
        * Q: How can you determine the state of a process in Linux?
            
        * A: You can use the `ps` command with the `-l` option to display process state information.
            
10. **Zombie State**
    
    * **Theory**: A Zombie process is a process that has completed execution but still has an entry in the process table.
        
    * **Interview Q&A**:
        
        * Q: What is a Zombie process in Linux?
            
        * A: A Zombie process in Linux is a process that has completed execution but still has an entry in the process table.
            
    * **Practical Q&A**:
        
        * Q: How can you find Zombie processes in Linux?
            
        * A: You can use the `ps` command with the `-l` option and look for processes with a state of `Z`.
            
11. **Load Average and CPU Load**
    
    * **Theory**: Load average is a measure of the amount of computational work that a computer system performs. CPU load is a measure of the amount of computational work that a computer’s processor performs.
        
    * **Interview Q&A**:
        
        * Q: What are load average and CPU load in Linux?
            
        * A: Load average is a measure of system activity over time, while CPU load is a measure of the utilization of the computer’s processor.
            
    * **Practical Q&A**:
        
        * Q: How can you check the load average and CPU load in Linux?
            
        * A: You can use the `uptime` command to check the load average, and the `top` command to check the CPU load.
            
12. **Jobs, bg, and fg Commands**
    
    * **Theory**: `jobs` is used to list the jobs running in the background, `bg` resumes suspended jobs in the background, and `fg` brings a job to the foreground.
        
    * **Interview Q&A**:
        
        * Q: What are the `jobs`, `bg`, and `fg` commands in Linux?
            
        * A: `jobs` lists the jobs running in the background, `bg` resumes suspended jobs in the background, and `fg` brings a job to the foreground.
            
    * **Practical Q&A**:
        
        * Q: How would you use the `jobs`, `bg`, and `fg` commands in Linux?
            
        * A: You can use `jobs` to list background jobs, `bg %jobid` to resume a job in the background, and `fg %jobid` to bring a job to the foreground.
            
13. **Starting a Process in the Background**
    
    * **Theory**: In Linux, you can start a process in the background by appending an ampersand (`&`) to the command.
        
    * **Interview Q&A**:
        
        * Q: How can you start a process in the background in Linux?
            
        * A: In Linux, you can start a process in the background by appending an ampersand (`&`) to the command.
            
    * **Practical Q&A**:
        
        * Q: Show me how to start a process in the background in Linux.
            
        * A: To start a process in the background, append an ampersand to the command. For example, `command &`.
            
14. **ps vs top**
    
    * **Theory**: `ps` provides a snapshot of current processes, while `top` displays real-time information about the system.
        
    * **Interview Q&A**:
        
        * Q: What are the differences between `ps` and `top`?
            
        * A: `ps` provides a static snapshot of current processes, while `top` updates its display in real-time.
            
    * **Practical Q&A**:
        
        * Q: How would you use `ps` and `top` to monitor processes on a Linux system?
            
        * A: `ps -ef` for a full listing of processes, `top` to monitor processes in real-time.
            
15. **Process Priority and Nice Value**
    
    * **Theory**: Process priority in Linux is determined by a process’s nice value. The nice value ranges from -20 (highest priority) to 19 (lowest priority). The default nice value for processes is 0.
        
    * **Interview Q&A**:
        
        * Q: What are process priority and nice value in Linux?
            
        * A: Process priority in Linux is determined by a process’s nice value, which ranges from -20 (highest priority) to 19 (lowest priority). The default nice value is 0.
            
    * **Practical Q&A**:
        
        * Q: How can you check and change the nice value of a process in Linux?
            
        * A: You can use the `top` command to check the nice value of a process, and the `renice` command to change it. For example, `renice +5 123` would increase the nice value of the process with PID 123 by 5.
            

**5\. Process Management & Service:**

* **How to modify process nice value for existing and new process**
    
    * **Theory:** The `nice` value of a process in Linux determines the priority of the process. A lower nice value means higher priority. The `renice` command is used to change the nice value of an existing process, while the `nice` command is used when starting a new process.
        
    * **Interview Questions and Answers:**
        
        * Q: How do you change the nice value of an existing process?
            
        * A: You can use the `renice` command followed by the new nice value and the Process ID (PID).
            
        * Q: How do you start a new process with a specific nice value?
            
        * A: You can use the `nice` command followed by the nice value and the command to start the new process.
            
    * **Practical Questions and Answers:**
        
        * Q: How would you change the nice value of a process with PID 1234 to 10?
            
        * A: You would use the command `renice 10 -p 1234`.
            
        * Q: How would you start a new instance of the `top` command with a nice value of 5?
            
        * A: You would use the command `nice -n 5 top`.
            
* **What is daemons, how to manage service unit in Linux**
    
    * **Theory:** A daemon is a background process that is designed to run autonomously, with little or not user intervention. The `systemctl` command is used to manage service units in Linux.
        
    * **Interview Questions and Answers:**
        
        * Q: What is a daemon in Linux?
            
        * A: A daemon is a background process that runs autonomously, often providing or helping to provide a specific service.
            
        * Q: How do you start a service in Linux?
            
        * A: You can use the `systemctl start` command followed by the name of the service.
            
    * **Practical Questions and Answers:**
        
        * Q: How would you start the `httpd` service?
            
        * A: You would use the command `systemctl start httpd`.
            
        * Q: How would you enable the `httpd` service to start on boot?
            
        * A: You would use the command `systemctl enable httpd`.
            
* **Difference between restart and reload a service**
    
    * **Theory**: Restarting a service stops it and then starts it again, which can interrupt connections. Reloading a service just reloads its configuration file, without interrupting connections.
        
    * **Interview Questions and Answers**:
        
        * Q: What is the difference between service restart and reload?
            
        * A: Restarting a service stops it and then starts it again, interrupting connections. Reloading a service just reloads its configuration file, without interrupting connections.
            
    * **Practical Questions and Answers**:
        
        * Q: How to restart and reload a service in Linux?
            
        * A: Use `systemctl restart servicename` to restart a service and `systemctl reload servicename` to reload a service.
            
* **How to start a service at boot time**
    
    * **Theory**: To start a service at boot time in Linux, you can enable the service using the systemctl command.
        
    * **Interview Questions and Answers**:
        
        * Q: How can you start a service at boot time in Linux?
            
        * A: You can enable the service using the systemctl command like `systemctl enable servicename`.
            
    * **Practical Questions and Answers**:
        
        * Q: How to enable the apache2 service to start at boot time?
            
        * A: Use the command `systemctl enable apache2`.
            
* **What mask and unmask in systemctl command**
    
    * **Theory**: The `mask` command in systemctl links the service to `/dev/null`, preventing the service from being started. The `unmask` command undoes the masking.
        
    * **Interview Questions and Answers**:
        
        * Q: What do the mask and unmask commands do in systemctl?
            
        * A: The `mask` command prevents the service from being started, even manually. The `unmask` command undoes the masking.
            
    * **Practical Questions and Answers**:
        
        * Q: How to mask and unmask the apache2 service?
            
        * A: Use `systemctl mask apache2` to mask the service and `systemctl unmask apache2` to unmask it.
            
* **Which process signal is used when we reload a service**
    
    * **Theory**: The SIGHUP signal is often used to reload a service.
        
    * **Interview Questions and Answers**:
        
        * Q: Which signal is used to reload a service in Linux?
            
        * A: The SIGHUP signal is often used to reload a service.
            
    * **Practical Questions and Answers**:
        
        * Q: How to send a SIGHUP signal to a process?
            
        * A: Use the command `kill -SIGHUP pid`.
            
* **What is the location of service unit file**
    
    * **Theory**: Service unit files are typically located in `/etc/systemd/system` or `/usr/lib/systemd/system`.
        
    * **Interview Questions and Answers**:
        
        * Q: Where are service unit files located in Linux?
            
        * A: Service unit files are typically located in `/etc/systemd/system` or `/usr/lib/systemd/system`.
            
    * **Practical Questions and Answers**:
        
        * Q: How to view the unit file of the apache2 service?
            
        * A: Use the command `systemctl cat apache2`.
            
* **pkill command uses, killall command uses, pidof and pgrep command uses**
    
    * **Theory**: `pkill` sends a signal to processes matching a pattern. `killall` sends a signal to all instances of a particular program. `pidof` finds the process ID of a running program. `pgrep` finds processes based on name and other attributes.
        
    * **Interview Questions and Answers**:
        
        * Q: What are the uses of pkill, killall, pidof, and pgrep commands in Linux?
            
        * A: `pkill` sends a signal to processes matching a pattern. `killall` sends a signal to all instances of a particular program. `pidof` finds the process ID of a running program. `pgrep` finds processes based on name and other attributes.
            
    * **Practical Questions and Answers**:
        
        * Q: How to kill all instances of the apache2 program?
            
        * A: Use the command `killall apache2`.
            
* **How to check process tree**
    
    * **Theory**: The `pstree` command is used to display a tree of processes.
        
    * **Interview Questions and Answers**:
        
        * Q: How can you check the process tree in Linux?
            
        * A: You can use the `pstree` command to check the process tree.
            
    * **Practical Questions and Answers**:
        
        * Q: How to display a tree of processes in Linux?
            
        * A: Use the command `pstree`.
            

---

**1\. What is SSH, what is the use of SSH, how SSH is different from Telnet**

* **Theory**: SSH (Secure Shell) is a protocol used to securely log onto remote systems. It can be used for secure data communication, remote command execution, and network services. SSH provides strong host-to-host and user authentication as well as secure encrypted communications over the internet. Unlike Telnet, which sends data in plain text, SSH is secure because it uses various forms of encryption to protect the data in transit.
    
* **Interview Questions and Answers**:
    
    * Q: What is SSH and why is it used?
        
    * A: SSH, or Secure Shell, is a protocol used to securely log onto remote systems. It is most commonly used for remote command execution and secure data communication. It provides strong encryption for data in transit, ensuring that the data is secure and private.
        
    * Q: How is SSH different from Telnet?
        
    * A: The main difference between SSH and Telnet is security. Telnet sends data in plain text which makes it vulnerable to interception. On the other hand, SSH provides strong encryption, ensuring that the data is secure and private during transit.
        
* **Practical Questions and Answers**:
    
    * Q: How can you log into a remote server using SSH?
        
    * A: You can use the ssh command followed by the username and IP address of the remote server. For example, `ssh user@192.168.1.1`.
        

**2\. How to configure SSH server, SSH port number**

* **Theory**: Configuring an SSH server involves editing the SSH daemon configuration file, usually located at `/etc/ssh/sshd_config`. The port number for SSH is defined in this file with the `Port` directive. The default port for SSH is 22.
    
* **Interview Questions and Answers**:
    
    * Q: How do you configure an SSH server?
        
    * A: Configuring an SSH server involves editing the SSH daemon configuration file, usually located at `/etc/ssh/sshd_config`. Changes in this file will affect the behavior of the SSH server.
        
    * Q: What is the default port for SSH and how can you change it?
        
    * A: The default port for SSH is 22. You can change it by editing the `Port` directive in the SSH daemon configuration file.
        
* **Practical Questions and Answers**:
    
    * Q: How can you change the default SSH port?
        
    * A: You can change the default SSH port by editing the SSH daemon configuration file. For example, to change the port to 2222, you would find the line that says `Port 22` and change it to `Port 2222`.
        
* **SSH v1 vs SSH v2**
    
    * [**Theory**: SSHv1 and SSHv2 are two versions of the Secure Shell protocol used for secure remote administration](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>1</sup>](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>2</sup>](https://www.informationweek.com/it-leadership/battle-of-the-ssh-protocols-sshv1-v-sshv2). [SSHv2 offers improved security over SSHv1, including better protection against eavesdropping, DNS and IP spoofing, and session hijacking](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>2</sup>](https://www.informationweek.com/it-leadership/battle-of-the-ssh-protocols-sshv1-v-sshv2). [SSHv2 uses different encryption and authentication algorithms and only uses host keys for authentication](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>3</sup>](https://newsitn.com/technology-news/ssh2-vs-ssh1-and-why-ssh-versions-still-matter/).
        
    * **Interview Questions and Answers**:
        
        * Q: What are the fundamental differences between SSH-1 and SSH-2 Protocols?
            
        * A: SSH-1 uses RSA algorithm for authentication, while SSH-2 uses DSA. [SSH-1 uses both server and host keys for authentication, while SSH-2 only uses host keys](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>4</sup>](https://ngelinux.com/ssh-v1-vs-ssh-v2-how-to-know-which-version-is-used-by-my-linux-system/).
            
    * **Practical Questions and Answers**:
        
        * Q: How can you force the use of SSHv2 in a connection?
            
        * [A: You can force the use of SSHv2 by modifying the “Protocol” line in your sshd\_config file to "Protocol 2"](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>5</sup>](https://www.tecmint.com/ssh-interview-questions/).
            
* **Types of Encryption: Symmetric vs Asymmetric Encryption**
    
    * [**Theory**: Symmetric encryption uses a single key for both encryption and decryption, while asymmetric encryption uses two different keys - one for encryption (public key) and one for decryption (private key)](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>6</sup>](https://certera.com/blog/symmetric-vs-asymmetric-encryption-detailed-guide)[<sup>7</sup>](https://www.geeksforgeeks.org/difference-between-symmetric-and-asymmetric-key-encryption/).
        
    * **Interview Questions and Answers**:
        
        * Q: What is the difference between symmetric and asymmetric encryption?
            
        * [A: Symmetric encryption uses a single key for both encryption and decryption, while asymmetric encryption uses two different keys for the same purpose](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>8</sup>](https://www.astrill.com/blog/symmetric-vs-asymmetric-encryption/).
            
    * **Practical Questions and Answers**:
        
        * Q: Can you give an example of a symmetric encryption algorithm and an asymmetric encryption algorithm?
            
        * [A: An example of a symmetric encryption algorithm is AES, while RSA is an example of an asymmetric encryption algorithm](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>9</sup>](https://preyproject.com/blog/types-of-encryption-symmetric-or-asymmetric-rsa-or-aes).
            
* **How SSH uses Asymmetric Encryption**
    
    * [**Theory**: SSH uses asymmetric encryption during the initial key exchange process to set up the symmetric encryption used to encrypt the session](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>1</sup>](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process). [The client and server both contribute toward establishing this key, and the resulting secret is never known to outside parties](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>1</sup>](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process).
        
    * **Interview Questions and Answers**:
        
        * Q: How does SSH use asymmetric encryption?
            
        * [A: SSH uses asymmetric encryption during the initial key exchange process to establish the symmetric encryption used to encrypt the session](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>1</sup>](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process).
            
    * **Practical Questions and Answers**:
        
        * Q: How can you verify that SSH is using asymmetric encryption during the initial key exchange?
            
        * [A: You can verify this by inspecting the SSH debug output during connection establishment](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>10</sup>](https://superuser.com/questions/1371944/when-is-asymmetric-and-symmetric-encryption-used-in-ssh).
            
* **How to login on a server using custom port and private key file**
    
    * **Theory**: To log in to a server using a custom port and a private key file, you use the `-p` option to specify the port and the `-i` option to specify the private key file in the SSH command.
        
    * **Interview Questions and Answers**:
        
        * Q: How can you log in to a server using a custom port and a private key file?
            
        * A: You can use the SSH command with the `-p` option to specify the port and the `-i` option to specify the private key file.
            
    * **Practical Questions and Answers**:
        
        * Q: Write a command to log in to a server at IP 192.168.1.1, port 2222, using the private key file `~/.ssh/id_rsa`.
            
        * A: The command would be `ssh -p 2222 -i ~/.ssh/id_rsa user@192.168.1.1`.
            
* **Passwordless Login and its Configuration**
    
    * **Theory**: Passwordless login in SSH is achieved using public key authentication. The public key is placed on the server, and the corresponding private key is kept on the client. When the client connects to the server, the server encrypts a challenge with the client’s public key. [The client must decrypt this challenge with its private key and send it back to the server to prove its identity](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process)[<sup>1</sup>](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process).
        
    * **Interview Questions and Answers**:
        
        * Q: What is passwordless login in SSH and how is it configured?
            
        * A: Passwordless login in SSH is achieved using public key authentication. [It is configured by generating a key pair on the client, placing the public key on the server, and using the private key on the client when connecting](https://interviewprep.org/ssh-protocol-interview-questions/)[<sup>11</sup>](https://interviewprep.org/ssh-protocol-interview-questions/).
            
    * **Practical Questions and Answers**:
        
        * Q: How can you set up passwordless login for a server?
            
        * [A: You can set up passwordless login by generating a key pair using `ssh-keygen`, copying the public key to the server using `ssh-copy-id`, and then connecting to the server using `ssh`](https://www.tecmint.com/ssh-interview-questions/)[<sup>5</sup>](https://www.tecmint.com/ssh-interview-questions/).
            

1. **How to restrict user from login using SSH, how to restrict root login via SSH**
    
    * **Theory**: SSH (Secure Shell) is a protocol used to securely log onto remote systems. [It can be configured to restrict user or root logins by editing the SSH daemon configuration file `/etc/ssh/sshd_config`](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>1</sup>](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>2</sup>](https://superuser.com/questions/1423238/how-to-prevent-users-from-logging-in-via-ssh-manually)[<sup>3</sup>](https://www.howtogeek.com/828538/how-and-why-to-disable-root-login-over-ssh-on-linux/)[<sup>4</sup>](https://unix.stackexchange.com/questions/99307/permit-root-to-login-via-ssh-only-with-key-based-authentication).
        
    * **Interview Questions and Answers**:
        
        * Q: How can you restrict a specific user from logging in via SSH?
            
        * [A: You can restrict a specific user from logging in via SSH by adding a `DenyUsers` directive followed by the username in the `/etc/ssh/sshd_config` file](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>1</sup>](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>5</sup>](https://www.ubuntumint.com/disable-ssh-user-login/).
            
        * Q: How can you restrict root login via SSH?
            
        * [A: You can restrict root login via SSH by setting the `PermitRootLogin` directive to `no` in the `/etc/ssh/sshd_config` file](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>3</sup>](https://www.howtogeek.com/828538/how-and-why-to-disable-root-login-over-ssh-on-linux/)[<sup>4</sup>](https://unix.stackexchange.com/questions/99307/permit-root-to-login-via-ssh-only-with-key-based-authentication).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you restrict the user ‘testuser’ from logging in via SSH?
            
        * [A: You would add the line `DenyUsers testuser` to the `/etc/ssh/sshd_config` file and then restart the SSH service](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>1</sup>](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>5</sup>](https://www.ubuntumint.com/disable-ssh-user-login/).
            
        * Q: How would you disable root login via SSH?
            
        * [A: You would set the line `PermitRootLogin no` in the `/etc/ssh/sshd_config` file and then restart the SSH service](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>3</sup>](https://www.howtogeek.com/828538/how-and-why-to-disable-root-login-over-ssh-on-linux/)[<sup>4</sup>](https://unix.stackexchange.com/questions/99307/permit-root-to-login-via-ssh-only-with-key-based-authentication).
            
2. **How to allow or block SSH login from a specific network**
    
    * [**Theory**: SSH can be configured to allow or block logins from specific IP addresses or networks by editing the `/etc/hosts.allow` and `/etc/hosts.deny` files or by setting up firewall rules](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>6</sup>](https://unix.stackexchange.com/questions/406245/limit-ssh-access-to-specific-clients-by-ip-address)[<sup>7</sup>](https://docs.rackspace.com/docs/restrict-ssh-login-to-a-specific-ip-or-host).
        
    * **Interview Questions and Answers**:
        
        * Q: How can you allow SSH login from a specific IP address?
            
        * [A: You can allow SSH login from a specific IP address by adding a line in the format `sshd: IP_ADDRESS` to the `/etc/hosts.allow` file](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>7</sup>](https://docs.rackspace.com/docs/restrict-ssh-login-to-a-specific-ip-or-host)[<sup>6</sup>](https://unix.stackexchange.com/questions/406245/limit-ssh-access-to-specific-clients-by-ip-address).
            
        * Q: How can you block SSH login from a specific IP address?
            
        * [A: You can block SSH login from a specific IP address by adding a line in the format `sshd: IP_ADDRESS` to the `/etc/hosts.deny` file](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>7</sup>](https://docs.rackspace.com/docs/restrict-ssh-login-to-a-specific-ip-or-host)[<sup>6</sup>](https://unix.stackexchange.com/questions/406245/limit-ssh-access-to-specific-clients-by-ip-address).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you allow SSH login from the IP address 192.168.1.100?
            
        * [A: You would add the line `sshd: 192.168.1.100` to the `/etc/hosts.allow` file](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>7</sup>](https://docs.rackspace.com/docs/restrict-ssh-login-to-a-specific-ip-or-host)[<sup>6</sup>](https://unix.stackexchange.com/questions/406245/limit-ssh-access-to-specific-clients-by-ip-address).
            
        * Q: How would you block SSH login from the IP address 192.168.1.100?
            
        * [A: You would add the line `sshd: 192.168.1.100` to the `/etc/hosts.deny` file](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>7</sup>](https://docs.rackspace.com/docs/restrict-ssh-login-to-a-specific-ip-or-host)[<sup>6</sup>](https://unix.stackexchange.com/questions/406245/limit-ssh-access-to-specific-clients-by-ip-address).
            
3. **How to change default SSH port**
    
    * [**Theory**: The default SSH port can be changed by editing the `Port` directive in the `/etc/ssh/sshd_config` file and then restarting the SSH service](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>8</sup>](https://linuxize.com/post/how-to-change-ssh-port-in-linux/)[<sup>9</sup>](https://linuxhandbook.com/change-ssh-port/)[<sup>10</sup>](https://www.rosehosting.com/blog/how-and-why-to-change-the-default-ssh-port-on-linux/)[<sup>11</sup>](https://www.geeksforgeeks.org/how-to-change-the-default-ssh-port-in-linux/)[<sup>12</sup>](https://www.hostinger.com/tutorials/how-to-change-ssh-port-vps).
        
    * **Interview Questions and Answers**:
        
        * Q: How can you change the default SSH port?
            
        * [A: You can change the default SSH port by editing the `Port` directive in the `/etc/ssh/sshd_config` file and then restarting the SSH service](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>8</sup>](https://linuxize.com/post/how-to-change-ssh-port-in-linux/)[<sup>9</sup>](https://linuxhandbook.com/change-ssh-port/)[<sup>10</sup>](https://www.rosehosting.com/blog/how-and-why-to-change-the-default-ssh-port-on-linux/)[<sup>11</sup>](https://www.geeksforgeeks.org/how-to-change-the-default-ssh-port-in-linux/)[<sup>12</sup>](https://www.hostinger.com/tutorials/how-to-change-ssh-port-vps).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you change the default SSH port to 2222?
            
        * [A: You would change the line `Port 22` to `Port 2222` in the `/etc/ssh/sshd_config` file and then restart the SSH service](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>8</sup>](https://linuxize.com/post/how-to-change-ssh-port-in-linux/)[<sup>9</sup>](https://linuxhandbook.com/change-ssh-port/)[<sup>10</sup>](https://www.rosehosting.com/blog/how-and-why-to-change-the-default-ssh-port-on-linux/)[<sup>11</sup>](https://www.geeksforgeeks.org/how-to-change-the-default-ssh-port-in-linux/)[<sup>12</sup>](https://www.hostinger.com/tutorials/how-to-change-ssh-port-vps).
            
4. **What is SSH tunneling**
    
    * **Theory**: SSH tunneling, also known as SSH port forwarding, is a method of transporting arbitrary networking data over an encrypted SSH connection. [It can be used to add encryption to legacy applications, implement VPNs (Virtual Private Networks), and access intranet services across firewalls](https://www.ubuntumint.com/restrict-ssh-access-user/)[<sup>13</sup>](https://www.ssh.com/academy/ssh/tunneling)[<sup>14</sup>](https://linuxize.com/post/how-to-setup-ssh-tunneling/)[<sup>15</sup>](https://www.concordia.ca/ginacody/aits/support/faq/ssh-tunnel.html)[<sup>16</sup>](https://goteleport.com/blog/ssh-tunneling-explained/).
        
    * **Interview Questions and Answers**:
        
        * Q: What is SSH tunneling and what is it used for?
            
        * A: SSH tunneling is a method of transporting arbitrary networking data over an encrypted SSH connection. [It can be used to add encryption to legacy applications, implement VPNs, and access intranet services across firewalls](https://www.ssh.com/academy/ssh/tunneling)[<sup>13</sup>](https://www.ssh.com/academy/ssh/tunneling)[<sup>14</sup>](https://linuxize.com/post/how-to-setup-ssh-tunneling/)[<sup>15</sup>](https://www.concordia.ca/ginacody/aits/support/faq/ssh-tunnel.html)[<sup>16</sup>](https://goteleport.com/blog/ssh-tunneling-explained/).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you create a local SSH tunnel?
            
        * [A: You would use the `-L` option with the `ssh` command in the format `-L [LOCAL_IP:]LOCAL_PORT:DESTINATION:DESTINATION_PORT [USER@]SSH_SERVER`](https://linuxize.com/post/how-to-setup-ssh-tunneling/)[<sup>14</sup>](https://linuxize.com/post/how-to-setup-ssh-tunneling/).
            

---

1. **Location where all the logs are stored**
    
    * **Theory**: In Linux, system logs are typically stored in the `/var/log` directory.
        
    * **Interview Questions and Answers**:
        
        * Q: Where are system logs stored in Linux?
            
        * A: System logs in Linux are typically stored in the `/var/log` directory.
            
    * **Practical Questions and Answers**:
        
        * Q: How can you list all the log files in a Linux system?
            
        * A: You can use the command `ls /var/log` to list all the log files.
            
2. **How to read log files, which command to use**
    
    * **Theory**: The `cat`, `less`, `more`, and `tail` commands are commonly used to read log files in Linux.
        
    * **Interview Questions and Answers**:
        
        * Q: Which commands can be used to read log files in Linux?
            
        * A: The `cat`, `less`, `more`, and `tail` commands can be used to read log files in Linux.
            
    * **Practical Questions and Answers**:
        
        * Q: How can you display the contents of a log file named `syslog`?
            
        * A: You can use the command `cat /var/log/syslog` to display the contents of the `syslog` file.
            
3. **How to monitor live logs from a file**
    
    * **Theory**: The `tail -f` command is used to monitor live logs from a file in Linux.
        
    * **Interview Questions and Answers**:
        
        * Q: How can you monitor live logs from a file in Linux?
            
        * A: You can use the `tail -f` command followed by the filename to monitor live logs from a file in Linux.
            
    * **Practical Questions and Answers**:
        
        * Q: How can you monitor live logs from the `syslog` file?
            
        * A: You can use the command `tail -f /var/log/syslog` to monitor live logs from the `syslog` file.
            
4. **In which file all the authentication logs and booting logs are stored**
    
    * **Theory**: Authentication logs are typically stored in the `auth.log` file and booting logs are stored in the `boot.log` file in the `/var/log` directory.
        
    * **Interview Questions and Answers**:
        
        * Q: Where are authentication logs and booting logs stored in Linux?
            
        * A: Authentication logs are typically stored in the `auth.log` file and booting logs are stored in the `boot.log` file in the `/var/log` directory.
            
    * **Practical Questions and Answers**:
        
        * Q: How can you display the contents of the `auth.log` and `boot.log` files?
            
        * A: You can use the commands `cat /var/log/auth.log` and `cat /var/log/boot.log` to display the contents of the `auth.log` and `boot.log` files respectively.
            
5. **What is syslog, what is rsyslog, what is system journal**
    
    * **Theory**: `syslog` is a standard for message logging, `rsyslog` is a rocket-fast system for log processing, and `system journal` or `journald` is a system service for collecting and storing logs.
        
    * **Interview Questions and Answers**:
        
        * Q: What are `syslog`, `rsyslog`, and `system journal`?
            
        * A: `syslog` is a standard for message logging, `rsyslog` is a rocket-fast system for log processing, and `system journal` or `journald` is a system service for collecting and storing logs.
            
    * **Practical Questions and Answers**:
        
        * Q: How can you display the status of the `rsyslog` service?
            
        * A: You can use the command `systemctl status rsyslog` to display the status of the `rsyslog` service.
            
6. **What is the work of systemd-journald service**
    
    * **Theory**: The `systemd-journald` service is responsible for collecting and storing log data, making it easier to manage logs in a centralized way.
        
    * **Interview Questions and Answers**:
        
        * Q: What is the role of the `systemd-journald` service?
            
        * A: The `systemd-journald` service is responsible for collecting and storing log data, making it easier to manage logs in a centralized way.
            
    * **Practical Questions and Answers**:
        
        * Q: How can you display the status of the `systemd-journald` service?
            
        * A: You can use the command `systemctl status systemd-journald` to display the status of the `systemd-journald` service.
            
7. **Location where system journal are stored**
    
    * Theory: In Linux, system journals are stored in the `/run/log/journal/` directory by default. [However, they can also be stored in the `/var/log/journal/` directory for persistent storage across reboots](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>1</sup>](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>2</sup>](https://devicetests.com/journalctl-system-logs-location).
        
    * Interview Questions and Answers:
        
        * Q: Where are system journals stored in Linux?
            
        * A: By default, system journals are stored in the `/run/log/journal/` directory. [However, for persistent storage across reboots, they can be stored in the `/var/log/journal/` directory](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>1</sup>](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>2</sup>](https://devicetests.com/journalctl-system-logs-location).
            
    * Practical Questions and Answers:
        
        * Q: How can you check the location of system journals in Linux?
            
        * A: You can check the location of system journals by looking at the directories `/run/log/journal/` and `/var/log/journal/`.
            
8. **How to check system journals**
    
    * [Theory: The `journalctl` command is used to read and filter system log messages, allowing users to navigate and search through logs](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>3</sup>](https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/)[<sup>4</sup>](https://linuxhandbook.com/journalctl-command/).
        
    * Interview Questions and Answers:
        
        * Q: How can you check system journals in Linux?
            
        * [A: You can check system journals in Linux using the `journalctl` command](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>3</sup>](https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/)[<sup>4</sup>](https://linuxhandbook.com/journalctl-command/).
            
    * Practical Questions and Answers:
        
        * Q: How can you use `journalctl` to check system journals?
            
        * [A: You can simply run `journalctl` in the terminal to display the entire journal, with the oldest entries at the top of the list](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>3</sup>](https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/).
            
9. **How to store system journal persistently**
    
    * [Theory: To configure the `systemd-journald` service to preserve system journals persistently across reboot, you need to set `Storage` to `persistent` in the `/etc/systemd/journald.conf` file](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>5</sup>](https://computingforgeeks.com/preserve-systemd-journals-logging-with-persistent-storage/)[<sup>6</sup>](https://www.redhat.com/sysadmin/store-linux-system-journals).
        
    * Interview Questions and Answers:
        
        * Q: How can you store system journals persistently in Linux?
            
        * [A: You can store system journals persistently in Linux by setting `Storage` to `persistent` in the `/etc/systemd/journald.conf` file](https://computingforgeeks.com/preserve-systemd-journals-logging-with-persistent-storage/)[<sup>5</sup>](https://computingforgeeks.com/preserve-systemd-journals-logging-with-persistent-storage/)[<sup>6</sup>](https://www.redhat.com/sysadmin/store-linux-system-journals).
            
    * Practical Questions and Answers:
        
        * Q: How can you configure `systemd-journald` to store system journals persistently?
            
        * A: You can edit the `/etc/systemd/journald.conf` file and set `Storage=persistent`. [Then, restart the `systemd-journald` service for the changes to take effect](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>5</sup>](https://computingforgeeks.com/preserve-systemd-journals-logging-with-persistent-storage/)[<sup>6</sup>](https://www.redhat.com/sysadmin/store-linux-system-journals).
            
10. **In which file all the audit logs are stored**
    
    * [Theory: By default, the Audit system stores log entries in the `/var/log/audit/audit.log` file](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>7</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sec-understanding_audit_log_files)[<sup>8</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/sec-understanding_audit_log_files).
        
    * Interview Questions and Answers:
        
        * Q: Where are all the audit logs stored in Linux?
            
        * [A: All the audit logs in Linux are stored in the `/var/log/audit/audit.log` file by default](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>7</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sec-understanding_audit_log_files)[<sup>8</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/sec-understanding_audit_log_files).
            
    * Practical Questions and Answers:
        
        * Q: How can you check the audit logs in Linux?
            
        * A: You can check the audit logs in Linux by viewing the `/var/log/audit/audit.log` file.
            
11. **What is auditing?**
    
    * Theory: The Linux Audit system provides a way to track security-relevant information about your system. [Based on pre-configured rules, Audit generates log entries to record as much information about the events that are happening on your system as possible](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>9</sup>](https://www.redhat.com/sysadmin/configure-linux-auditing-auditd)[<sup>10</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/security_hardening/auditing-the-system_security-hardening).
        
    * Interview Questions and Answers:
        
        * Q: What is auditing in Linux?
            
        * A: Auditing in Linux is a way to track security-relevant information about the system. [It generates log entries based on pre-configured rules to record as much information about the system events as possible](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>9</sup>](https://www.redhat.com/sysadmin/configure-linux-auditing-auditd)[<sup>10</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/security_hardening/auditing-the-system_security-hardening).
            
    * Practical Questions and Answers:
        
        * Q: How can you enable auditing in Linux?
            
        * A: You can enable auditing in Linux by starting the `auditd` service and configuring audit rules using the `auditctl` command.
            
12. **Best practices to audit Linux OS**
    
    * [Theory: Best practices for auditing a Linux OS include ensuring physical security of the system, auditing disk partitioning, watching file access, and monitoring system calls](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>11</sup>](https://www.isaca.org/resources/isaca-journal/issues/2015/volume-4/auditing-linuxunix-server-operating-systems)[<sup>10</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/security_hardening/auditing-the-system_security-hardening).
        
    * Interview Questions and Answers:
        
        * Q: What are some best practices for auditing a Linux OS?
            
        * [A: Some best practices for auditing a Linux OS include ensuring physical security of the system, auditing disk partitioning, watching file access, and monitoring system calls](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>11</sup>](https://www.isaca.org/resources/isaca-journal/issues/2015/volume-4/auditing-linuxunix-server-operating-systems)[<sup>10</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/security_hardening/auditing-the-system_security-hardening).
            
    * Practical Questions and Answers:
        
        * Q: How can you implement best practices for auditing a Linux OS?
            
        * [A: You can implement best practices for auditing a Linux OS by configuring the system for physical security, setting up disk partitions properly, using audit rules to watch file access, and monitoring system calls](https://askubuntu.com/questions/864722/where-is-journalctl-data-stored)[<sup>11</sup>](https://www.isaca.org/resources/isaca-journal/issues/2015/volume-4/auditing-linuxunix-server-operating-systems)[<sup>10</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/security_hardening/auditing-the-system_security-hardening).
            

---

**1\. IP Address Classes, How to Check IP Address Class, How to Check Public and Private IP**

* **Theory**: IP addresses are divided into five classes (A, B, C, D, E) based on the first octet value. The `ifconfig` or `ip addr` command can be used to check the IP address class in Linux. Public IPs are globally unique and are assigned by the ISP, while private IPs are used within local area networks.
    
* **Interview Questions and Answers**:
    
    * Q: What are the ranges for Class A, B, and C in IP addressing?
        
    * A: Class A: 1.0.0.0 to 126.0.0.0, Class B: 128.0.0.0 to 191.255.0.0, Class C: 192.0.0.0 to 223.255.255.0
        
* **Practical Questions and Answers**:
    
    * Q: How to check your IP address in Linux?
        
    * A: Use the command `ifconfig` or `ip addr`.
        

**2\. Gateway, CIDR, Subnetting, Broadcast Address**

* **Theory**: The gateway is an access point to another network. CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and routing Internet Protocol packets. Subnetting is the practice of dividing a network into two or more networks. Broadcast addresses are used to send data to all devices in a network.
    
* **Interview Questions and Answers**:
    
    * Q: What is the purpose of a subnet mask?
        
    * A: A subnet mask is used to divide an IP address into two parts, one for the network address and one for the host address.
        
* **Practical Questions and Answers**:
    
    * Q: How to determine the broadcast address of a network?
        
    * A: The broadcast address is the last address in the IP range. For example, for the network 192.168.1.0/24, the broadcast address is 192.168.1.255.
        

**1\. Switch vs Router**

* [Theory: A switch is a device that connects devices within a network and forwards data packets to and from those devices](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>1</sup>](https://www.geeksforgeeks.org/difference-between-socket-and-port/). [Unlike a router, a switch only sends data to the single device it is intended for](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>2</sup>](https://stackoverflow.com/questions/152457/what-is-the-difference-between-a-port-and-a-socket). [A router, on the other hand, is a device that connects various networks simultaneously](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>1</sup>](https://www.geeksforgeeks.org/difference-between-socket-and-port/). [It works in the network layer, while a switch works in the data link layer](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>1</sup>](https://www.geeksforgeeks.org/difference-between-socket-and-port/).
    
* Interview Questions and Answers:
    
    * Q: What is the main difference between a switch and a router?
        
    * A: The main difference between a switch and a router is that a switch connects devices within a network (often a local area network, or LAN) and forwards data packets to and from those devices. [A router, on the other hand, connects various networks simultaneously](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>1</sup>](https://www.geeksforgeeks.org/difference-between-socket-and-port/).
        
* Practical Questions and Answers:
    
    * Q: In a home network, would you typically use a switch, a router, or both?
        
    * A: In a home network, you would typically use both. The router connects the home network to the internet, while the switch connects various devices within the home network.
        

**2\. TCP vs UDP**

* Theory: TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are both transport layer protocols used in networking. [The main differences between the two are that TCP is a connection-oriented protocol that provides reliable data transfer, while UDP is a connectionless protocol that is faster and more efficient than TCP but does not guarantee reliable data transfer](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>3</sup>](https://www.geeksforgeeks.org/differences-between-tcp-and-udp/).
    
* Interview Questions and Answers:
    
    * Q: What are the main differences between TCP and UDP?
        
    * [A: TCP is a connection-oriented protocol that provides reliable data transfer, while UDP is a connectionless protocol that is faster and more efficient than TCP but does not guarantee reliable data transfer](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>3</sup>](https://www.geeksforgeeks.org/differences-between-tcp-and-udp/).
        
* Practical Questions and Answers:
    
    * Q: When would you use TCP over UDP, and vice versa?
        
    * A: TCP is typically used when reliability is more important than speed, such as transferring important files over the network. [UDP, on the other hand, is typically used for real-time applications like video streaming and online gaming, where speed is more important than reliability](https://www.geeksforgeeks.org/differences-between-tcp-and-udp/)[<sup>3</sup>](https://www.geeksforgeeks.org/differences-between-tcp-and-udp/).
        

**3\. Ports and Sockets**

* [Theory: A socket is a combination of an IP address and a port number](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>1</sup>](https://www.geeksforgeeks.org/difference-between-socket-and-port/). [It serves as the communication endpoint for processes running on a device](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>4</sup>](https://phoenixnap.com/kb/linux-socket). [A port, on the other hand, is a logical construct assigned to network processes so they can be identified within the system](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>1</sup>](https://www.geeksforgeeks.org/difference-between-socket-and-port/).
    
* Interview Questions and Answers:
    
    * Q: What is the difference between a port and a socket?
        
    * A: A port is a logical construct assigned to network processes so they can be identified within the system. [A socket, on the other hand, is a combination of an IP address and a port number](https://www.geeksforgeeks.org/difference-between-socket-and-port/)[<sup>1</sup>](https://www.geeksforgeeks.org/difference-between-socket-and-port/).
        
* Practical Questions and Answers:
    
    * Q: How are ports and sockets used in network communication?
        
    * A: In network communication, a socket (which is a combination of an IP address and a port number) serves as the endpoint for data transmission. [When a process wants to send or receive data, it opens a socket, which provides it with a way to send or receive data across the network](https://phoenixnap.com/kb/linux-socket)[<sup>4</sup>](https://phoenixnap.com/kb/linux-socket).
        

**Server-Client Model**

* [Theory: The server-client model is a distributed application structure that partitions tasks or workloads between the providers of a resource or service, called servers, and service requesters, called clients](https://www.geeksforgeeks.org/client-server-model/)[<sup>1</sup>](https://www.geeksforgeeks.org/client-server-model/)[<sup>2</sup>](https://en.wikipedia.org/wiki/Client%E2%80%93server_model). [In this model, the client sends a request for data to the server over the internet, the server accepts the requested process and delivers the data packets requested back to the client](https://www.geeksforgeeks.org/client-server-model/)[<sup>1</sup>](https://www.geeksforgeeks.org/client-server-model/).
    
* Interview Questions and Answers:
    
    * Q: Can you explain the server-client model?
        
    * A: The server-client model is a distributed application structure that partitions tasks or workloads between servers and clients. [The client sends a request for data to the server over the internet, the server accepts the requested process and delivers the data packets requested back to the client](https://www.geeksforgeeks.org/client-server-model/)[<sup>1</sup>](https://www.geeksforgeeks.org/client-server-model/).
        
* Practical Questions and Answers:
    
    * Q: How does a client interact with a server in the server-client model?
        
    * A: In the server-client model, a client sends a request for data to the server over the internet. [The server accepts the requested process and delivers the data packets requested back to the client](https://www.geeksforgeeks.org/client-server-model/)[<sup>1</sup>](https://www.geeksforgeeks.org/client-server-model/).
        

* **Dynamic Host Configuration Protocol (DHCP)**
    
    * [Theory: DHCP is a network protocol used to assign IP addresses and other network configuration parameters to devices on a network](https://www.geeksforgeeks.org/client-server-model/)[<sup>3</sup>](https://www.geeksforgeeks.org/dynamic-host-configuration-protocol-dhcp/)[<sup>4</sup>](https://linuxconfig.org/what-is-dhcp-and-how-to-configure-dhcp-server-in-linux). [It uses a client-server model and is based on discovery, offer, request, and ACK](https://www.geeksforgeeks.org/client-server-model/)[<sup>3</sup>](https://www.geeksforgeeks.org/dynamic-host-configuration-protocol-dhcp/).
        
    * Interview Questions and Answers:
        
        * Q: What is DHCP and how does it work?
            
        * A: DHCP stands for Dynamic Host Configuration Protocol. It is a network protocol used to assign IP addresses and other network configuration parameters to devices on a network. [It uses a client-server model and is based on discovery, offer, request, and ACK](https://www.geeksforgeeks.org/client-server-model/)[<sup>3</sup>](https://www.geeksforgeeks.org/dynamic-host-configuration-protocol-dhcp/).
            
    * Practical Questions and Answers:
        
        * Q: How does a DHCP client obtain an IP address?
            
        * A: A DHCP client obtains an IP address by sending a DHCP request over the network upon boot. The DHCP server then determines an appropriate address to give to the client based on the server’s availability and use regulations. [The server then reserves that address for the client and sends an OFFER/DHCPOFFER packet containing that address information back to the client](https://www.geeksforgeeks.org/client-server-model/)[<sup>5</sup>](https://www.educba.com/dhcp-interview-questions/).
            
* **DHCP Port Number**
    
    * Theory: DHCP uses two UDP ports: 67 and 68. [Port number 67 is used by the DHCP server, and port number 68 is used by the DHCP client](https://www.geeksforgeeks.org/client-server-model/)[<sup>6</sup>](https://linuxhandbook.com/common-ports/).
        
    * Interview Questions and Answers:
        
        * Q: Which ports does DHCP use?
            
        * A: DHCP uses two UDP ports: 67 and 68. [Port number 67 is used by the DHCP server, and port number 68 is used by the DHCP client](https://www.geeksforgeeks.org/client-server-model/)[<sup>6</sup>](https://linuxhandbook.com/common-ports/).
            
    * Practical Questions and Answers:
        
        * Q: Which port does a DHCP server use?
            
        * [A: A DHCP server uses UDP port number 67](https://www.geeksforgeeks.org/client-server-model/)[<sup>6</sup>](https://linuxhandbook.com/common-ports/).
            
* **Ping Command**
    
    * Theory: The ping command is used to check whether a host is reachable on a network or not. [It works by sending a packet of data to a specific host and waiting for a reply](https://www.geeksforgeeks.org/client-server-model/)[<sup>7</sup>](https://www.geeksforgeeks.org/ping-command-in-linux-with-examples/)[<sup>8</sup>](https://www.geeksforgeeks.org/network-configuration-trouble-shooting-commands-linux/).
        
    * Interview Questions and Answers:
        
        * Q: What is the purpose of the ping command?
            
        * A: The ping command is used to check whether a host is reachable on a network or not. [It works by sending a packet of data to a specific host and waiting for a reply](https://www.geeksforgeeks.org/client-server-model/)[<sup>7</sup>](https://www.geeksforgeeks.org/ping-command-in-linux-with-examples/).
            
    * Practical Questions and Answers:
        
        * Q: How do you use the ping command to check network connectivity?
            
        * [A: To check network connectivity using the ping command, you can type `ping` followed by the hostname or IP address of the host you want to reach](https://www.geeksforgeeks.org/client-server-model/)[<sup>7</sup>](https://www.geeksforgeeks.org/ping-command-in-linux-with-examples/).
            

Sure, let’s start with the first topic: `netstat`.

**netstat**

[• Theory: The `netstat` command is a network statistics tool used to display network connections for TCP, routing tables, and a number of network interface and network protocol statistics](https://en.wikipedia.org/wiki/Netstat)[<sup>1</sup>](https://en.wikipedia.org/wiki/Netstat). [It is available on Unix-like operating systems and also on IBM Windows NT-based operating systems](https://en.wikipedia.org/wiki/Netstat)[<sup>1</sup>](https://en.wikipedia.org/wiki/Netstat). [It is used for finding problems in the network and to determine the amount of traffic on the network as a performance measurement](https://en.wikipedia.org/wiki/Netstat)[<sup>1</sup>](https://en.wikipedia.org/wiki/Netstat).

• Interview Questions and Answers: 1. [What is the `netstat` command used for? - Answer: The `netstat` command is used to display network connections, routing tables, interface statistics, masquerade connections, and multicast memberships](https://en.wikipedia.org/wiki/Netstat)[<sup>2</sup>](https://www.golinuxcloud.com/netstat-command-in-linux/). 2. [What is the replacement for `netstat` in Linux? - Answer: On Linux, `netstat` (part of “net-tools”) is superseded by `ss` (part of iproute2)](https://en.wikipedia.org/wiki/Netstat)[<sup>2</sup>](https://www.golinuxcloud.com/netstat-command-in-linux/).

• Practical Questions and Answers: 1. [How to display all active connections using `netstat`? - Answer: You can use the command `netstat -a` to display all active connections](https://en.wikipedia.org/wiki/Netstat)[<sup>2</sup>](https://www.golinuxcloud.com/netstat-command-in-linux/). 2. [How to display only listening connections using `netstat`? - Answer: You can use the command `netstat -l` to display only listening connections](https://en.wikipedia.org/wiki/Netstat)[<sup>2</sup>](https://www.golinuxcloud.com/netstat-command-in-linux/).

**nslookup**

[• Theory: `nslookup` is a network administration command-line tool available in many computer operating systems for querying the Domain Name System (DNS) to obtain domain name or IP address mapping, or other DNS records](https://en.wikipedia.org/wiki/Netstat)[<sup>3</sup>](https://www.geeksforgeeks.org/dns-look-up/).

• Interview Questions and Answers: 1. [What is `nslookup` used for? - Answer: `nslookup` is used to query the Domain Name System (DNS) to obtain domain name or IP address mapping, or other DNS records](https://en.wikipedia.org/wiki/Netstat)[<sup>4</sup>](https://phoenixnap.com/kb/nslookup-command). 2. How does `nslookup` work? - Answer: `nslookup` sends a DNS query to your ISP’s DNS servers. [The servers look up the hostname in their DNS records and return the corresponding IP address](https://phoenixnap.com/kb/nslookup-command)[<sup>4</sup>](https://phoenixnap.com/kb/nslookup-command).

• Practical Questions and Answers: 1. [How to use `nslookup` to find the IP address of a website? - Answer: You can use the command `nslookup`](https://activedirectorypro.com/use-nslookup-check-dns-records/) [`website.com`](https://en.wikipedia.org/wiki/Netstat) [to find the IP address of a website](https://activedirectorypro.com/use-nslookup-check-dns-records/)[<sup>5</sup>](https://activedirectorypro.com/use-nslookup-check-dns-records/). 2. [How to use `nslookup` for reverse DNS lookup? - Answer: You can use the command `nslookup IP_address` for reverse DNS lookup](https://activedirectorypro.com/use-nslookup-check-dns-records/)[<sup>5</sup>](https://activedirectorypro.com/use-nslookup-check-dns-records/).

**What is the** `ifconfig` command used for? The `ifconfig` command in Linux is used to configure the kernel-resident network interfaces. It is used at boot time to set up the interfaces as necessary. [After that, it is usually used when needed during debugging or when you need system tuning](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>1</sup>](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/).

**What is the** `nmcli` command used for? `nmcli` is a command-line tool used for controlling NetworkManager and reporting network status. [It can be used to create, display, edit, delete, activate, and deactivate network connections, as well as control and display network device status](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>1</sup>](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/).

**What is the** `traceroute` command used for? `traceroute` is a command-line utility that shows the complete route to a destination address. [It also shows the time taken (or delays) between intermediate routers](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>2</sup>](https://www.geeksforgeeks.org/traceroute-in-network-layer/).

**What is the** `route` command used for? The `route` command in Linux is used for managing the IP/kernel routing table. [It allows displaying, adding, deleting, and modifying routing table entries](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>3</sup>](https://www.geeksforgeeks.org/route-command-in-linux-with-examples/).

**Why does** `traceroute` show 3 packets with 3 different types of ms value on every hop? `traceroute` discovery actually makes three attempts for each TTL value to find out intermediate router hops. [This allows to see if there are some alternative next-hops in the path](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>4</sup>](https://community.cisco.com/t5/routing/traceroute-interview-question/td-p/3836986).

**How does** `route` command work? The `route` command works by managing the IP/kernel routing table. It allows displaying, adding, deleting, and modifying routing table entries. [The command is useful for tasks such as setting up static routes, adding a default gateway, rejecting routing to specific hosts/networks, and accessing detailed routing information](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>3</sup>](https://www.geeksforgeeks.org/route-command-in-linux-with-examples/).

**How does** `nmcli` command work? `nmcli` is a command-line tool used for controlling NetworkManager and reporting network status. [It can be used to create, display, edit, delete, activate, and deactivate network connections, as well as control and display network device status](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>1</sup>](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/).

**How does** `ifconfig` command work? The `ifconfig` command in Linux is used to configure the kernel-resident network interfaces. It is used at boot time to set up the interfaces as necessary. [After that, it is usually used when needed during debugging or when you need system tuning](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/)[<sup>1</sup>](https://www.geeksforgeeks.org/nmcli-command-in-linux-with-examples/).

**1\. Use of /etc/hosts file**

* [**Theory:** The `/etc/hosts` file is a plain text file used in matching an FQDN with the server IP hosting a specific domain](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>1</sup>](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/). [It’s useful if a DNS server is not available when a user wants to access a domain from their browser](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>1</sup>](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/).
    
* **Interview Questions and Answers:**
    
    * Q: What is the purpose of the `/etc/hosts` file in Linux?
        
    * [A: The `/etc/hosts` file in Linux or any other operating system is used to map connections between IP addresses and domain names](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>2</sup>](https://linuxhandbook.com/etc-hosts-file/).
        
* [**Practical Questions and Answers:** The `/etc/hosts` file can be used to redirect URLs, block unwanted websites, and create website shortcuts](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>2</sup>](https://linuxhandbook.com/etc-hosts-file/).
    

**2\. Use of /etc/resolv.conf file**

* [**Theory:** In Linux, the `/etc/resolv.conf` file is known as the configuration file for DNS queries](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>3</sup>](https://www.baeldung.com/linux/etc-resolv-conf-file). [It translates domain names to IP addresses by querying the Domain Name Server (DNS)](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>3</sup>](https://www.baeldung.com/linux/etc-resolv-conf-file).
    
* **Interview Questions and Answers:**
    
    * Q: What is the purpose of the `/etc/resolv.conf` file in Linux?
        
    * [A: The `/etc/resolv.conf` file is a configuration file used by the Linux operating system to store information about Domain Name System (DNS) servers](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>4</sup>](https://www.howtouselinux.com/post/understanding-etc-resolv-conf-file-in-linux).
        
* [**Practical Questions and Answers:** You can change the contents of your `/etc/resolv.conf` file by editing the file with a text editor such as nano or vi](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>4</sup>](https://www.howtouselinux.com/post/understanding-etc-resolv-conf-file-in-linux).
    

**3\. What is nameserver in /etc/resolv.conf**

* [**Theory:** The `nameserver` directive in the `/etc/resolv.conf` file specifies the IP address of the domain name server that the resolver can query against](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>3</sup>](https://www.baeldung.com/linux/etc-resolv-conf-file).
    
* **Interview Questions and Answers:**
    
    * Q: What does the `nameserver` directive do in the `/etc/resolv.conf` file?
        
    * [A: The `nameserver` directive specifies the IP address of the domain name server that the resolver can query against](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>3</sup>](https://www.baeldung.com/linux/etc-resolv-conf-file).
        
* [**Practical Questions and Answers:** You can configure up to a maximum of three different DNS by specifying the `nameserver` directive repeatedly](https://blog.purestorage.com/purely-informational/what-is-the-etc-hosts-file-in-linux/)[<sup>3</sup>](https://www.baeldung.com/linux/etc-resolv-conf-file).
    
* **Hardware/MAC/Physical Address \[interface, ports, ethernet, lan, nic\]**
    
    * [Theory: A MAC (Media Access Control) address is a unique 48-bit identifier assigned to a Network Interface Card (NIC) by its manufacturer](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>1</sup>](https://www.geeksforgeeks.org/mac-address-in-computer-network/). [It operates at the Data Link Layer of the OSI model and is used to identify a device on a network](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>1</sup>](https://www.geeksforgeeks.org/mac-address-in-computer-network/). [There are two types of MAC addresses: Unicast (a frame sent out to a specific NIC) and Multicast (a frame sent to a group of devices)](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>2</sup>](https://engineeringinterviewquestions.com/mcqs-on-mac-address-answers/).
        
    * Interview Questions and Answers:
        
        * Q: Why is the MAC address called the Physical address?
            
        * [A: The MAC address is called a physical address because it physically identifies a piece of hardware](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>3</sup>](https://www.geeksforgeeks.org/top-50-ip-addressing-interview-questions-and-answers/).
            
    * Practical Questions and Answers:
        
        * Q: How to find the MAC address of a network interface in Linux?
            
        * [A: You can use the `ip link` or `ifconfig` command to display the MAC address of a network interface](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>4</sup>](https://www.sanfoundry.com/iot-questions-answers-mac-address/).
            
* **How to Change Hostname, /etc/hostname file**
    
    * [Theory: The hostname of a Linux system can be changed using the `hostnamectl` command or by editing the `/etc/hostname` file](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>5</sup>](https://linuxize.com/post/how-to-change-hostname-in-linux/). [The hostname is a label assigned to a machine that identifies it on a network](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>5</sup>](https://linuxize.com/post/how-to-change-hostname-in-linux/).
        
    * Interview Questions and Answers:
        
        * Q: How can you change the hostname in Linux?
            
        * [A: You can change the hostname in Linux using the `hostnamectl set-hostname new_hostname` command or by editing the `/etc/hostname` file](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>6</sup>](https://www.webasha.com/blog/top-linux-interview-questions-answers).
            
    * Practical Questions and Answers:
        
        * Q: How to change the hostname in Linux without restarting the system?
            
        * [A: You can use the `hostnamectl set-hostname new_hostname` command to change the hostname without restarting the system](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>7</sup>](https://www.howtouselinux.com/post/change-hostname-in-linux).
            
* **How to Change IP Address Graphically, How to Add New Connection Using nmcli**
    
    * [Theory: The IP address of a Linux system can be changed graphically via the Network section of the System Settings app](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>8</sup>](https://www.systranbox.com/how-to-change-your-ip-address-in-linux/). [A new network connection can be added using the `nmcli` command](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>9</sup>](https://devconnected.com/how-to-change-ip-address-on-linux/).
        
    * Interview Questions and Answers:
        
        * Q: How can you change the IP address in Linux?
            
        * [A: You can change the IP address in Linux using the `ip addr add [ip_address] dev [interface]` command or graphically via the Network section of the System Settings app](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>10</sup>](https://linuxhandbook.com/change-ip-address/).
            
    * Practical Questions and Answers:
        
        * Q: How to add a new network connection using `nmcli`?
            
        * [A: You can add a new network connection using the `nmcli connection add type ethernet ifname [interface_name]` command](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>11</sup>](https://prog.world/managing-network-connections-in-linux-using-the-nmcli-console-utility/).
            
* **Where All the Network Connection Configuration File Are Stored**
    
    * Theory: Network configuration files in Linux are typically stored in the `/etc/network/` directory. [The main configuration file is `/etc/network/interfaces` on Debian-based systems, and `/etc/sysconfig/network-scripts/ifcfg-*` on Red Hat-based systems](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>12</sup>](https://www.redhat.com/sysadmin/change-hostname-linux).
        
    * Interview Questions and Answers:
        
        * Q: Where are the network configuration files stored in Linux?
            
        * [A: Network configuration files in Linux are typically stored in the `/etc/network/` directory](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>12</sup>](https://www.redhat.com/sysadmin/change-hostname-linux).
            
    * Practical Questions and Answers:
        
        * Q: How to view the network configuration files in Linux?
            
        * [A: You can view the network configuration files in Linux using the `cat /etc/network/interfaces` or `cat /etc/sysconfig/network-scripts/ifcfg-*` command](https://www.geeksforgeeks.org/mac-address-in-computer-network/)[<sup>12</sup>](https://www.redhat.com/sysadmin/change-hostname-linux).
            
* **How to Change Date and Time in Linux**
    
    * Theory: The date and time in Linux can be changed using the `date` command or the `timedatectl` command. The `date` command is used to display or set the system date and time, while `timedatectl` is used to control the system time and date in systemd systems.
        
    * Interview Questions and Answers:
        
        * Q: How can you change the date and time in Linux?
            
        * A: You can change the date and time in Linux using the `date` command or the `timedatectl` command.
            
    * Practical Questions and Answers:
        
        * Q: How to set the system date to 2022-12-31 in Linux?
            
        * A: You can set the system date to 2022-12-31 in Linux using the `date -s 2022-12-31` command.
            
* **What is NTP, How to Configure NTP Client, Port Number of NTP**
    
    * Theory: NTP (Network Time Protocol) is a protocol used to synchronize computer clock times in a network. It operates over port number 123. An NTP client can be configured in Linux by editing the `/etc/ntp.conf` file and adding the NTP server’s IP address or hostname.
        
    * Interview Questions and Answers:
        
        * Q: What is NTP and what port does it use?
            
        * A: NTP (Network Time Protocol) is a protocol used to synchronize computer clock times in a network. It operates over port number 123.
            
    * Practical Questions and Answers:
        
        * Q: How to configure an NTP client in Linux?
            
        * A: An NTP client can be configured in Linux by editing the `/etc/ntp.conf` file and adding the NTP server’s IP address or hostname.
            

---

**Backup:**

* **Theory:**
    
    * Importance of Backup: Backups are crucial to prevent permanent data loss. [They safeguard computer systems and data against theft, illegal access, or any disaster](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>1</sup>](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>2</sup>](https://medium.com/@kjones120320/linux-server-backup-a-step-by-step-guide-a5a8016900c5)[<sup>3</sup>](https://www.scaler.com/topics/backup-commands-in-linux/)[<sup>4</sup>](https://www.redswitches.com/blog/linux-server-backups/).
        
    * [Types of Backup and Differences: There are three basic types of backup: Full, Differential, and Incremental](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>5</sup>](https://phoenixnap.com/kb/full-vs-incremental-vs-differential-backup). Full backup involves copying the entire data set. Differential backup saves only the data that has changed since the previous full backup. [Incremental backup includes the data that has changed since the last backup](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>5</sup>](https://phoenixnap.com/kb/full-vs-incremental-vs-differential-backup).
        
    * [Backup Strategy: A backup strategy is a plan that prepares you to quickly and easily recover your important data in the shortest amount of time possible](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>6</sup>](https://www.makeuseof.com/create-data-backup-restore-strategy-for-linux/)[<sup>7</sup>](https://www.redhat.com/sysadmin/5-backup-tips)[<sup>8</sup>](https://www.cloudpanel.io/blog/the-right-linux-server-backup-strategy/)[<sup>9</sup>](https://linuxsecurity.com/features/best-linux-backup-solutions-to-prevent-data-loss-in-a-ransomware-attack).
        
* **Interview Questions and Answers:**
    
    * Q: Why is backup important in Linux? A: Backup is important in Linux to prevent data loss due to hardware failure, virus attacks, or human error. [It allows for data recovery in case of any disaster](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>1</sup>](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>2</sup>](https://medium.com/@kjones120320/linux-server-backup-a-step-by-step-guide-a5a8016900c5)[<sup>3</sup>](https://www.scaler.com/topics/backup-commands-in-linux/)[<sup>4</sup>](https://www.redswitches.com/blog/linux-server-backups/).
        
    * Q: What are the different types of backups in Linux and how do they differ? A: In Linux, there are three basic types of backups: Full, Differential, and Incremental. Full backup involves copying the entire data set. Differential backup saves only the data that has changed since the previous full backup. [Incremental backup includes the data that has changed since the last backup](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>5</sup>](https://phoenixnap.com/kb/full-vs-incremental-vs-differential-backup).
        
    * Q: What is a backup strategy in Linux? A: A backup strategy in Linux is a plan that prepares you to quickly and easily recover your important data in the shortest amount of time possible. [It involves identifying risk factors, analyzing what data to back up, deciding the data backup type, and more](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>6</sup>](https://www.makeuseof.com/create-data-backup-restore-strategy-for-linux/)[<sup>7</sup>](https://www.redhat.com/sysadmin/5-backup-tips)[<sup>8</sup>](https://www.cloudpanel.io/blog/the-right-linux-server-backup-strategy/)[<sup>9</sup>](https://linuxsecurity.com/features/best-linux-backup-solutions-to-prevent-data-loss-in-a-ransomware-attack).
        
* **Practical Questions and Answers:**
    
    * Q: How would you create a full backup in Linux? A: You can use the `tar` command to create a full backup in Linux. [For example, `tar -cvf backup.tar /path/to/directory`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>10</sup>](https://www.geeksforgeeks.org/tar-command-linux-examples/).
        
    * Q: How would you perform a differential backup in Linux? A: Differential backups can be performed using tools like `rsync` that support incremental backups. [The command would be something like `rsync -a /source/directory /destination/directory`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>11</sup>](https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync).
        
    * [Q: How would you implement a backup strategy in Linux? A: Implementing a backup strategy in Linux involves identifying the data to back up, choosing the type of backup (full, differential, incremental), scheduling the backups, and regularly testing and updating the backup process](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>6</sup>](https://www.makeuseof.com/create-data-backup-restore-strategy-for-linux/)[<sup>7</sup>](https://www.redhat.com/sysadmin/5-backup-tips)[<sup>8</sup>](https://www.cloudpanel.io/blog/the-right-linux-server-backup-strategy/)[<sup>9</sup>](https://linuxsecurity.com/features/best-linux-backup-solutions-to-prevent-data-loss-in-a-ransomware-attack).
        

**Zip and Unzip Command, Tar Command, Compression Method with Tar:**

* **Theory:**
    
    * [Zip and Unzip Command: The `zip` command in Linux is used to compress files, while the `unzip` command is used to extract compressed files](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>12</sup>](https://www.geeksforgeeks.org/zip-command-in-linux-with-examples/)[<sup>13</sup>](https://unix.stackexchange.com/questions/6596/how-do-i-zip-unzip-on-the-unix-command-line).
        
    * Tar Command: The `tar` command in Linux is used to archive files. [It can also compress files using different methods](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>10</sup>](https://www.geeksforgeeks.org/tar-command-linux-examples/).
        
    * Compression Method with Tar: The `tar` command supports different compression methods. [The `-z` option uses `gzip` compression, and the `-j` option uses `bzip2` compression](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>10</sup>](https://www.geeksforgeeks.org/tar-command-linux-examples/)[<sup>14</sup>](https://www.pluralsight.com/cloud-guru/labs/aws/working-with-compressed-files-in-linux).
        
* **Interview Questions and Answers:**
    
    * [Q: What are the `zip` and `unzip` commands in Linux? A: The `zip` command in Linux is used to compress files, while the `unzip` command is used to extract compressed files](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>12</sup>](https://www.geeksforgeeks.org/zip-command-in-linux-with-examples/)[<sup>13</sup>](https://unix.stackexchange.com/questions/6596/how-do-i-zip-unzip-on-the-unix-command-line).
        
    * Q: What is the `tar` command in Linux and what are its uses? A: The `tar` command in Linux is used to archive files. [It can also compress files using different methods](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>10</sup>](https://www.geeksforgeeks.org/tar-command-linux-examples/).
        
    * Q: How do you compress files with the `tar` command in Linux? A: The `tar` command supports different compression methods. [The `-z` option uses `gzip` compression, and the `-j` option uses `bzip2` compression](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>10</sup>](https://www.geeksforgeeks.org/tar-command-linux-examples/)[<sup>14</sup>](https://www.pluralsight.com/cloud-guru/labs/aws/working-with-compressed-files-in-linux).
        
* **Practical Questions and Answers:**
    
    * [Q: How would you compress a file using the `zip` command in Linux? A: You can compress a file in Linux using the `zip` command like this: `zip`](https://www.geeksforgeeks.org/backup-and-restore/) [`compressed.zip`](https://www.geeksforgeeks.org/backup-and-restore/) [`file.txt`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>12</sup>](https://www.geeksforgeeks.org/zip-command-in-linux-with-examples/)[<sup>13</sup>](https://unix.stackexchange.com/questions/6596/how-do-i-zip-unzip-on-the-unix-command-line).
        
    * [Q: How would you extract a tarball using the `tar` command in Linux? A: You can extract a tarball in Linux using the `tar` command like this: `tar -xvf file.tar`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>10</sup>](https://www.geeksforgeeks.org/tar-command-linux-examples/).
        
    * [Q: How would you compress a directory using `gzip` compression with the `tar` command in Linux? A: You can compress a directory using `gzip` compression with the `tar` command like this: `tar -cvzf compressed.tar.gz directory/`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>10</sup>](https://www.geeksforgeeks.org/tar-command-linux-examples/)[<sup>14</sup>](https://www.pluralsight.com/cloud-guru/labs/aws/working-with-compressed-files-in-linux).
        

**Popular Backup Tools:**

* **Theory:**
    
    * [There are many backup tools available for Linux, including `rsync`, `fwbackups`, `Bacula`, `Backupninja`, and `Simple Backup Suite (sbackup)`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>15</sup>](https://www.tecmint.com/linux-system-backup-tools/)[<sup>16</sup>](https://itslinuxfoss.com/10-best-linux-backup-tools/)[<sup>17</sup>](https://www.codingninjas.com/studio/library/best-backup-tools-for-linux)[<sup>18</sup>](https://www.tutorialspoint.com/5-best-graphical-backup-tools-for-ubuntu-and-linux-mint).
        
* **Interview Questions and Answers:**
    
    * [Q: What are some popular backup tools in Linux? A: Some popular backup tools in Linux include `rsync`, `fwbackups`, `Bacula`, `Backupninja`, and `Simple Backup Suite (sbackup)`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>15</sup>](https://www.tecmint.com/linux-system-backup-tools/)[<sup>16</sup>](https://itslinuxfoss.com/10-best-linux-backup-tools/)[<sup>17</sup>](https://www.codingninjas.com/studio/library/best-backup-tools-for-linux)[<sup>18</sup>](https://www.tutorialspoint.com/5-best-graphical-backup-tools-for-ubuntu-and-linux-mint).
        
    * Q: What is `rsync` and why is it popular as a backup tool in Linux? A: `rsync` is a popular Linux backup tool that allows users to synchronize files and directories between two locations. [It is popular because it uses a special delta transfer algorithm and a few optimizations to make the operation faster](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>11</sup>](https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync).
        
    * Q: Can you name a graphical backup tool for Linux and describe its features? A: `fwbackups` is a graphical backup tool for Linux. [It offers features such as a simple interface, flexibility in the backup configuration, and remote backups](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>15</sup>](https://www.tecmint.com/linux-system-backup-tools/).
        
* **Practical Questions and Answers:**
    
    * [Q: How would you use `rsync` to backup a directory in Linux? A: You can use `rsync` to backup a directory in Linux like this: `rsync -a /source/directory /destination/directory`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>11</sup>](https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync).
        
    * Q: How would you use `fwbackups` to create a backup in Linux? A: `fwbackups` provides a graphical interface for creating backups. [You would open the application, select the files or directories to backup, choose the destination, and start the backup](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>15</sup>](https://www.tecmint.com/linux-system-backup-tools/).
        

**Transfer Data Between Linux Hosts:**

* **Theory:**
    
    * [Data can be transferred between Linux hosts using various methods such as `ftp`, `sftp`, `scp`, or `rsync`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>19</sup>](https://devconnected.com/4-ways-to-transfer-files-and-directories-on-linux/)[<sup>20</sup>](https://superuser.com/questions/345347/how-to-copy-a-file-between-two-linux-machines)[<sup>21</sup>](https://www.wikihow.com/Transfer-Files-from-One-Linux-Server-to-Another)[<sup>22</sup>](https://www.tutorialspoint.com/transfer-files-between-linux-machines-over-ssh).
        
* **Interview Questions and Answers:**
    
    * [Q: What are some methods to transfer data between Linux hosts? A: Some methods to transfer data between Linux hosts include `ftp`, `sftp`, `scp`, or `rsync`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>19</sup>](https://devconnected.com/4-ways-to-transfer-files-and-directories-on-linux/)[<sup>20</sup>](https://superuser.com/questions/345347/how-to-copy-a-file-between-two-linux-machines)[<sup>21</sup>](https://www.wikihow.com/Transfer-Files-from-One-Linux-Server-to-Another)[<sup>22</sup>](https://www.tutorialspoint.com/transfer-files-between-linux-machines-over-ssh).
        
    * [Q: How does `scp` work in Linux? A: `scp` provides a method to copy files from one machine to a remote machine over a secure SSH connection](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>20</sup>](https://superuser.com/questions/345347/how-to-copy-a-file-between-two-linux-machines).
        
    * Q: What is `rsync` and how is it used in Linux? A: `rsync` is a tool that allows users to synchronize files and directories between two locations. [It uses a special delta transfer algorithm and a few optimizations to make the operation faster](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>11</sup>](https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync).
        
* **Practical Questions and Answers:**
    
    * [Q: How would you use `scp` to copy a file from a local machine to a remote machine in Linux? A: You can use `scp` to copy a file from a local machine to a remote machine like this: `scp localfile.txt user@remote:/path/to/directory`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>20</sup>](https://superuser.com/questions/345347/how-to-copy-a-file-between-two-linux-machines).
        
    * [Q: How would you use `rsync` to synchronize a local directory with a remote directory in Linux? A: You can use `rsync` to synchronize a local directory with a remote directory like this: `rsync -a /local/directory user@remote:/path/to/directory`](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>11</sup>](https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync).
        

**Scp vs Rsync:**

* **Theory:**
    
    * `scp` and `rsync` are both used to copy files over a network. `scp` performs a plain linear copy, while `rsync` [uses a special delta transfer algorithm and a few optimizations to make the operation faster`scp` is always secure, whereas `rsync` must travel over SSH to be secure](https://www.geeksforgeeks.org/backup-and-restore/)[<sup>11</sup>](https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync)[<sup>23</sup>](https://superuser.com/questions/393608/difference-between-scp-and-rsync)[<sup>24</sup>](https://unix.stackexchange.com/questions/39718/is-there-ever-a-reason-to-use-scp-instead-of-rsync)[<sup>25</sup>](https://superuser.com/questions/1096498/file-synchronization-on-linux-over-network-scp-or-rsync).
        
* **Interview Questions and Answers:**
    
    * Q: What is the difference between `scp` and `rsync`? A: `scp` and `rsync` are both used to copy files over a network. `scp` performs a plain linear copy, while `rsync` uses a special delta transfer algorithm and a few optimizations to make the operation faster. `scp` is always secure, whereas `rsync` must travelover ssh to be secure.
        

---

1. **Package Management in Linux**
    
    * [**Theory**: Package management is a method of installing, maintaining, and updating software on a system](https://www.tecmint.com/linux-package-management/)[<sup>1</sup>](https://www.tecmint.com/linux-package-management/)[<sup>2</sup>](https://www.linode.com/docs/guides/linux-package-management-overview/). [In Linux, package management systems like RPM, DPKG, YUM, and APT are used to handle these tasks](https://www.tecmint.com/linux-package-management/)[<sup>1</sup>](https://www.tecmint.com/linux-package-management/)[<sup>2</sup>](https://www.linode.com/docs/guides/linux-package-management-overview/).
        
    * **Interview Questions and Answers**:
        
        * Q: What is package management in Linux?
            
        * A: Package management in Linux is a method of installing, maintaining, and updating software on a system. [It simplifies software administration by providing a standardized way to handle dependencies and maintain the software ecosystem](https://www.tecmint.com/linux-package-management/)[<sup>1</sup>](https://www.tecmint.com/linux-package-management/)[<sup>2</sup>](https://www.linode.com/docs/guides/linux-package-management-overview/).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you install a package using YUM?
            
        * A: You can install a package using YUM with the command `yum install <package-name>`.
            
2. **Package Manager for Debian based distribution and RHEL based distribution**
    
    * **Theory**: Debian-based distributions use the DPKG package management system with APT as the front-end tool. [Red Hat-based distributions use the RPM package management system with YUM or DNF as the front-end tool](https://www.tecmint.com/linux-package-management/)[<sup>3</sup>](https://linuxgenie.net/difference-between-linux-deb-vs-rpm/)[<sup>4</sup>](https://www.redhat.com/sysadmin/how-manage-packages).
        
    * **Interview Questions and Answers**:
        
        * Q: What package managers are used in Debian-based and Red Hat-based distributions?
            
        * A: Debian-based distributions use DPKG with APT as the front-end tool. [Red Hat-based distributions use RPM with YUM or DNF as the front-end tool](https://www.tecmint.com/linux-package-management/)[<sup>3</sup>](https://linuxgenie.net/difference-between-linux-deb-vs-rpm/)[<sup>4</sup>](https://www.redhat.com/sysadmin/how-manage-packages).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you update all packages using APT?
            
        * A: You can update all packages using APT with the command `sudo apt update && sudo apt upgrade`.
            
3. **Query for Packages Using RPM, RPM Database Overview**
    
    * [**Theory**: The RPM command can be used to query information about installed packages using the `-q` option](https://www.tecmint.com/linux-package-management/)[<sup>5</sup>](https://linuxconfig.org/how-to-query-packages-information-with-the-rpm-package-manager). [The RPM database, stored in `/var/lib/rpm`, contains metadata about installed RPMs](https://www.tecmint.com/linux-package-management/)[<sup>6</sup>](https://access.redhat.com/sites/default/files/attachments/rpm_tutorial_20120831.pdf).
        
    * **Interview Questions and Answers**:
        
        * Q: How do you query for packages using RPM?
            
        * [A: You can query for packages using RPM with the command `rpm -q <package-name>`](https://www.tecmint.com/linux-package-management/)[<sup>5</sup>](https://linuxconfig.org/how-to-query-packages-information-with-the-rpm-package-manager).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you list all installed packages using RPM?
            
        * A: You can list all installed packages using RPM with the command `rpm -qa`.
            
4. **RPM vs YUM, Repository, YUM Server and YUM Client**
    
    * **Theory**: RPM is a low-level package manager that doesn’t resolve dependencies automatically. [YUM, a front-end to RPM, resolves dependencies and can manage packages from online repositories](https://www.tecmint.com/linux-package-management/)[<sup>7</sup>](https://phoenixnap.com/kb/rpm-vs-yum). [A repository is a collection of software packages available for installation](https://www.tecmint.com/linux-package-management/)[<sup>8</sup>](https://www.geeksforgeeks.org/how-to-add-repositories-in-linux/). [A YUM server hosts a YUM repository, and a YUM client accesses the server to install, update, or remove packages](https://www.tecmint.com/linux-package-management/)[<sup>9</sup>](https://access.redhat.com/solutions/9934)[<sup>10</sup>](https://medium.com/@jaspreet.bhagat17/simplified-yum-configuration-for-rhel-9-a-comprehensive-how-to-91f826755f1e).
        
    * **Interview Questions and Answers**:
        
        * Q: What are the differences between RPM and YUM?
            
        * A: RPM is a low-level package manager that doesn’t resolve dependencies automatically. [YUM, a front-end to RPM, resolves dependencies and can manage packages from online repositories](https://www.tecmint.com/linux-package-management/)[<sup>7</sup>](https://phoenixnap.com/kb/rpm-vs-yum).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you add a new repository to YUM?
            
        * A: You can add a new repository to YUM by creating a `.repo` file in the `/etc/yum.repos.d` directory with the repository information.
            
5. **Configure YUM Client, Repodata, GPGCheck and GPGKey**
    
    * [**Theory**: A YUM client is configured by adding repository files to the `/etc/yum.repos.d` directory](https://www.tecmint.com/linux-package-management/)[<sup>11</sup>](https://linuxconfig.org/how-to-install-yum-on-linux). [Repodata is metadata about the packages in a YUM repository, created by the `createrepo` command](https://www.tecmint.com/linux-package-management/)[<sup>12</sup>](https://www.percona.com/blog/how-to-create-your-own-repositories-for-packages/). [GPGCheck and GPGKey are used to verify the authenticity of packages](https://www.tecmint.com/linux-package-management/)[<sup>10</sup>](https://medium.com/@jaspreet.bhagat17/simplified-yum-configuration-for-rhel-9-a-comprehensive-how-to-91f826755f1e).
        
    * **Interview Questions and Answers**:
        
        * Q: What is repodata in a YUM repository?
            
        * [A: Repodata is metadata about the packages in a YUM repository, created by the `createrepo` command](https://www.tecmint.com/linux-package-management/)[<sup>12</sup>](https://www.percona.com/blog/how-to-create-your-own-repositories-for-packages/).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you disable GPG check for a YUM repository?
            
        * A: You can disable GPG check for a YUM repository by setting `gpgcheck=0` in the repository’s `.repo` file.
            
6. **Modules and Modularity in RHEL 8**
    
    * **Theory**: Modules in RHEL 8 provide a way to deploy applications in different versions, each with its own set of dependencies. Modularity allows for the coexistence of different versions of the same software on the same system.
        
    * **Interview Questions and Answers**:
        
        * Q: What is modularity in RHEL 8?
            
        * A: Modularity in RHEL 8 allows for the coexistence of different versions of the same software on the same system, each with its own set of dependencies.
            
    * **Practical Questions and Answers**:
        
        * Q: How would you list all available modules for a package in RHEL 8?
            
        * A: You can list all available modules for a package in RHEL 8 with the command `dnf module list <package-name>`.
            
7. **Why DNF is Better Than YUM**
    
    * **Theory**: DNF, the next-generation version of YUM, provides better package management by resolving package dependencies more accurately. [It also uses less memory and has a better performance than YUM](https://www.tecmint.com/linux-package-management/)[<sup>13</sup>](https://sysadminxpert.com/difference-between-yum-and-rpm/).
        
    * **Interview Questions and Answers**:
        
        * Q: Why is DNF considered better than YUM?
            
        * [A: DNF is considered better than YUM because it resolves package dependencies more accurately, uses less memory, and has better performance](https://www.tecmint.com/linux-package-management/)[<sup>13</sup>](https://sysadminxpert.com/difference-between-yum-and-rpm/).
            
    * **Practical Questions and Answers**:
        
        * Q: How would you install a package using DNF?
            
        * A: You can install a package using DNF with the command `dnf install <package-name>`.
            
8. **Patching**
    
    * **Theory**: Patching is the process of applying updates to software packages to improve security, fix bugs, or add features.
        
    * **Interview Questions and Answers**:
        
        * Q: What is patching in the context of Linux?
            
        * A: Patching in the context of Linux is the process of applying updates to software packages to improve security, fix bugs, or add features.
            
    * **Practical Questions and Answers**:
        
        * Q: How would you apply all available updates to a system using YUM?
            
        * A: You can apply all available updates to a system using YUM with the command `yum update`.
            
9. **Updating and Patching Practical**
    
    * **Theory**: Updating and patching in Linux involves using a package manager like YUM or DNF to apply updates or patches to installed software packages.
        
    * **Practical Questions and Answers**:
        
        * Q: How would you update a specific package using YUM?
            
        * A: You can update a specific package using YUM with the command `yum update <package-name>`.
            
10. **Kernel Patching and Upgrade**
    
    * **Theory**: Kernel patching involves applying updates to the Linux kernel, often for security fixes or performance improvements. Upgrading the kernel involves installing a newer version of the kernel.
        
    * **Interview Questions and Answers**:
        
        * Q: What is kernel patching and upgrading in Linux?
            
        * A: Kernel patching involves applying updates to the Linux kernel, often for security fixes or performance improvements. Upgrading the kernel involves installing a newer version of the kernel.
            
    * **Practical Questions and Answers**:
        
        * Q: How would you upgrade the kernel using YUM?
            
        * A: You can upgrade the kernel using YUM with the command `yum update kernel`.
            

---

**1\. Why we use cronjob scheduling**

* **Theory**: Cron is a time-based job scheduler in Unix-like operating systems. Users can schedule jobs (commands or scripts) to run at specific times or on specific days. It is commonly used for system maintenance tasks, such as log rotation, system updates, or backups.
    
* **Interview Questions and Answers**:
    
    * Q: Why is cronjob scheduling important in Linux?
        
    * A: Cronjob scheduling is important as it allows users to automate system maintenance or administration tasks, ensuring they are performed consistently and without manual intervention.
        
* **Practical Questions and Answers**:
    
    * Q: How would you use a cron job to run a script every day at 3 am?
        
    * A: You would add the following line to your crontab file: `0 3 * * * /path/to/`[`script.sh`](http://script.sh)
        

**2\. How to schedule a cronjob, what is the syntax for crontab file**

* **Theory**: Cron jobs are scheduled using the `crontab` command. The syntax of a cron job is: `[Minute] [Hour] [Day_of_Month] [Month_of_Year] [Day_of_Week] [Command]`.
    
* **Interview Questions and Answers**:
    
    * Q: How do you schedule a cron job to run a script every Monday at 5 pm?
        
    * A: You would add the following line to your crontab file: `0 17 * * 1 /path/to/`[`script.sh`](http://script.sh)
        
* **Practical Questions and Answers**:
    
    * Q: How would you schedule a cron job to run a script on the first day of every month?
        
    * A: You would add the following line to your crontab file: `0 0 1 * * /path/to/`[`script.sh`](http://script.sh)
        

**3\. /etc/cron.d, /etc/cron.hourly, /etc/cron.daily, /etc/cron.weekly directory**

* **Theory**: These directories contain scripts that are run on a regular schedule. Scripts in `/etc/cron.hourly` are run every hour, scripts in `/etc/cron.daily` are run once a day, and so on.
    
* **Interview Questions and Answers**:
    
    * Q: What is the purpose of the `/etc/cron.daily` directory?
        
    * A: The `/etc/cron.daily` directory contains scripts that are run once a day.
        
* **Practical Questions and Answers**:
    
    * Q: How would you schedule a script to run once a week?
        
    * A: You would place the script in the `/etc/cron.weekly` directory.
        

**4\. How to allow or deny a user to schedule cronjob**

* **Theory**: The files `/etc/cron.allow` and `/etc/cron.deny` can be used to control which users can use cron. If `cron.allow` exists, only users listed in it can use cron. If `cron.allow` does not exist but `cron.deny` does, all users can use cron except those listed in `cron.deny`.
    
* **Interview Questions and Answers**:
    
    * Q: How would you prevent a user from scheduling cron jobs?
        
    * A: You would add the user’s name to the `/etc/cron.deny` file.
        
* **Practical Questions and Answers**:
    
    * Q: How would you allow only a specific user to schedule cron jobs?
        
    * A: You would create a `/etc/cron.allow` file containing only that user’s name.
        

**5\. Where all the cronjob logs are stored and which service trigger scheduled cronjob**

* **Theory**: By default, cron job output is mailed to the user who scheduled the job. If you want to log output to a file, you can redirect it in the crontab entry. The cron daemon triggers scheduled cron jobs.
    
* **Interview Questions and Answers**:
    
    * Q: Where are cron job logs stored?
        
    * A: By default, cron job output is mailed to the user. To store logs in a file, you can redirect output in the crontab entry.
        
* **Practical Questions and Answers**:
    
    * Q: How would you schedule a cron job to run a script every day and log output to a file?
        
    * A: You would add the following line to your crontab file: `0 0 * * * /path/to/`[`script.sh`](http://script.sh) `> /path/to/logfile`
        

---

**1\. DAS vs NAS vs SAN and the benefits of partitioning:**

* **Theory:**
    
    * **DAS (Direct Attached Storage)** is digital storage directly attached to the computer accessing it, without a network in between.
        
    * **NAS (Network Attached Storage)** is a file-level data storage server connected to a network providing data access to clients.
        
    * **SAN (Storage Area Network)** is a network providing access to consolidated block-level data storage.
        
    * Partitioning helps in improving system performance, provides better data organization, and enables multi-boot setups.
        
* **Interview Questions and Answers:**
    
    * Q: What are the key differences between DAS, NAS, and SAN?
        
    * A: DAS is directly attached to a computer, NAS is a file-level data storage server connected to a network, and SAN is a network providing access to consolidated block-level data storage.
        
    * Q: What are the benefits of partitioning?
        
    * A: Partitioning can improve system performance, provide better data organization, and enable multi-boot setups.
        
* **Practical Questions and Answers:**
    
    * Q: How would you decide when to use DAS, NAS, or SAN in a given scenario?
        
    * A: The choice depends on the specific data storage and access requirements of the scenario. DAS could be used for simple, cost-effective storage, NAS for file sharing over a network, and SAN for high-performance, block-level storage.
        

**2\. MBR vs GPT, parted and fdisk command, how to create a partition:**

* **Theory:**
    
    * **MBR (Master Boot Record)** and **GPT (GUID Partition Table)** are two different ways of storing partitioning information on a drive.
        
    * `fdisk` and `parted` are two command-line utilities for disk partitioning.
        
    * To create a partition, you can use the `fdisk` or `parted` command followed by the device name.
        
* **Interview Questions and Answers:**
    
    * Q: What are the differences between MBR and GPT?
        
    * A: MBR supports up to 4 primary partitions, while GPT supports up to 128 primary partitions. MBR cannot handle disks above 2TB, while GPT can handle disks of much larger size.
        
    * Q: How would you create a partition using the `fdisk` command?
        
    * A: You can create a partition using `fdisk` by typing `fdisk /dev/sdX` (replace X with the drive letter), then use the `n` command to create a new partition.
        
* **Practical Questions and Answers:**
    
    * Q: How would you create a 1GB partition on a disk using `parted`?
        
    * A: You can do this by typing `parted /dev/sdX mkpart primary ext4 1MiB 1GiB` (replace X with the drive letter).
        

**3\. Most used filesystem in Linux, ext3 vs ext4 filesystem, ext4 vs xfs filesystem:**

* **Theory:**
    
    * The most commonly used filesystem in Linux is `ext4`.
        
    * `ext4` is an improvement over `ext3` with new features like support for larger file sizes and volumes.
        
    * `xfs` is a high-performance filesystem with excellent support for large files and filesystems, but unlike `ext4`, it doesn’t support filesystem shrinking.
        
* **Interview Questions and Answers:**
    
    * Q: What are the differences between `ext3` and `ext4` filesystems?
        
    * A: `ext4` is an improvement over `ext3` with new features like support for larger file sizes and volumes, and improved performance and reliability.
        
    * Q: How does `ext4` compare to `xfs`?
        
    * A: `xfs` is a high-performance filesystem with excellent support for large files and filesystems. Unlike `ext4`, it doesn’t support filesystem shrinking.
        
* **Practical Questions and Answers:**
    
    * Q: How would you create an `ext4` filesystem on a partition?
        
    * A: You can create an `ext4` filesystem by typing `mkfs.ext4 /dev/sdXY` (replace X with the drive letter and Y with the partition number).
        

**4\. How to format partition with filesystem, mount command understanding with some options:**

* **Theory:**
    
    * To format a partition with a filesystem, you can use the `mkfs` command followed by the filesystem type and the device name.
        
    * The `mount` command is used to mount filesystems. The `-t` option specifies the filesystem type, and the `-o` option is used to specify mount options.
        
* **Interview Questions and Answers:**
    
    * Q: How would you format a partition with an `ext4` filesystem?
        
    * A: You can format a partition with an `ext4` filesystem by typing `mkfs.ext4 /dev/sdXY` (replace X with the drive letter and Y with the partition number).
        
    * Q: How would you use the `mount` command to mount a filesystem?
        
    * A: You can use the `mount` command by typing `mount /dev/sdXY /mnt/my_mount_point` (replace X with the drive letter, Y with the partition number, and `/mnt/my_mount_point` with your mount point).
        
* **Practical Questions and Answers:**
    
    * Q: How would you mount an `ext4` filesystem with read-only permissions?
        
    * A: You can do this by typing `mount -o ro /dev/sdXY /mnt/my_mount_point` (replace X with the drive letter, Y with the partition number, and `/mnt/my_mount_point` with your mount point).
        
* **Swap Space, Swap Space Priority, Swappiness Value and How to Change It**
    
    * [**Theory**: Swap space is a space on a hard disk that is a substitute for physical memory](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>1</sup>](https://www.geeksforgeeks.org/swap-space-in-operating-system/). [It is used as virtual memory which contains process memory images](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>1</sup>](https://www.geeksforgeeks.org/swap-space-in-operating-system/). [Swap space priority is a value between -1 and 32767, with higher numbers indicating higher priority](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>2</sup>](https://unix.stackexchange.com/questions/613265/what-is-swap-priority-and-why-does-it-matter). [Swappiness is a Linux kernel property that sets the balance between swapping out pages from the physical memory to the swap space and removing pages from the page cache](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>3</sup>](https://linuxize.com/post/how-to-change-the-swappiness-value-in-linux/).
        
    * **Interview Questions and Answers**:
        
        * Q: What is the purpose of swap space in Linux?
            
        * A: Swap space in Linux is used when the amount of physical memory (RAM) is full. [It helps the computer’s operating system in pretending that it has more RAM than it actually has](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>1</sup>](https://www.geeksforgeeks.org/swap-space-in-operating-system/).
            
        * Q: How does swap space priority work?
            
        * A: Each swap area has a priority. Higher numbers mean higher priority. [Swap pages are allocated from areas in priority order, highest priority first](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>2</sup>](https://unix.stackexchange.com/questions/613265/what-is-swap-priority-and-why-does-it-matter).
            
        * Q: What is swappiness and how can it be changed?
            
        * [A: Swappiness is a Linux kernel property that defines how often the system will use the swap space](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>3</sup>](https://linuxize.com/post/how-to-change-the-swappiness-value-in-linux/). [It can be changed by writing a new value to the “/proc/sys/vm/swappiness” file](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>4</sup>](https://itslinuxfoss.com/change-swappiness-value-linux/).
            
    * **Practical Questions and Answers**:
        
        * Q: How to change the swappiness value to 10?
            
        * [A: You can change the swappiness value to 10 by running the following command: `sudo sysctl vm.swappiness=10`](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>3</sup>](https://linuxize.com/post/how-to-change-the-swappiness-value-in-linux/).
            
* **Activating Swap Space at Boot Time, Mounting Partition at Boot Time**
    
    * [**Theory**: Swap space can be activated at boot time by adding an entry to the `/etc/fstab` file](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>5</sup>](https://www.howtogeek.com/devops/how-to-create-and-enable-a-swapfile-at-the-linux-command-line/). [Similarly, a partition can be mounted at boot time by adding an appropriate entry to the `/etc/fstab` file](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>6</sup>](https://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/).
        
    * **Interview Questions and Answers**:
        
        * Q: How can you activate swap space at boot time?
            
        * [A: Swap space can be activated at boot time by adding an entry to the `/etc/fstab` file](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>5</sup>](https://www.howtogeek.com/devops/how-to-create-and-enable-a-swapfile-at-the-linux-command-line/).
            
        * Q: How can you mount a partition at boot time?
            
        * [A: A partition can be mounted at boot time by adding an appropriate entry to the `/etc/fstab` file](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>6</sup>](https://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/).
            
    * **Practical Questions and Answers**:
        
        * Q: How to add an entry to the `/etc/fstab` file to mount a partition at boot time?
            
        * [A: You can add an entry to the `/etc/fstab` file to mount a partition at boot time by editing the `/etc/fstab` file and adding a line in the format: `/dev/sdXY /mount/point fstype defaults 0 0`, where `/dev/sdXY` is the partition and `/mount/point` is the directory where you want to mount the partition](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>6</sup>](https://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/).
            
* **Understanding /etc/fstab File, Some Mount Options**
    
    * [**Theory**: The `/etc/fstab` file is a configuration file that contains information about various file systems and how the system should mount them during boot](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>7</sup>](https://www.makeuseof.com/what-is-fstab-file-systems-table-linux/). [Mount options define how the system should treat the mounted filesystem](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>8</sup>](https://docs.oracle.com/en/operating-systems/oracle-linux/6/admin/about-mount-options.html).
        
    * **Interview Questions and Answers**:
        
        * Q: What is the role of the `/etc/fstab` file in a Linux system?
            
        * [A: The `/etc/fstab` file is a configuration file that contains information about various file systems and how the system should mount them during boot](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>7</sup>](https://www.makeuseof.com/what-is-fstab-file-systems-table-linux/).
            
        * Q: What are some common mount options and their meanings?
            
        * [A: Some common mount options include `auto`, which allows the file system to be mounted automatically by using the `mount -a` command, and `exec`, which allows the execution of any binary files located in the file system](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>8</sup>](https://docs.oracle.com/en/operating-systems/oracle-linux/6/admin/about-mount-options.html).
            
    * **Practical Questions and Answers**:
        
        * Q: How to add a filesystem to be mounted at boot time in the `/etc/fstab` file?
            
        * [A: You can add a filesystem to be mounted at boot time in the `/etc/fstab` file by adding a line in the format: `/dev/sdXY /mount/point fstype defaults 0 0`, where `/dev/sdXY` is the filesystem and `/mount/point` is the directory where you want to mount the filesystem](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>6</sup>](https://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/).
            
* **Logical Volume Manager (LVM), Advantage of LVM, Configuring LVM Partition**
    
    * [**Theory**: LVM is a tool for logical volume management which includes allocating disks, striping, mirroring and resizing logical volumes](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>9</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-lvm). [The main advantages of LVM are increased abstraction, flexibility, and control](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>10</sup>](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations).
        
    * **Interview Questions and Answers**:
        
        * Q: What is LVM and what are its advantages?
            
        * [A: LVM, or Logical Volume Management, is a storage device management technology that gives users the power to pool and abstract the physical layout of component storage devices for flexible administration](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>10</sup>](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations). [The main advantages of LVM are increased abstraction, flexibility, and control](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>10</sup>](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations).
            
    * **Practical Questions and Answers**:
        
        * Q: How to create an LVM partition?
            
        * [A: Creating an LVM partition involves several steps including creating physical volumes, creating a volume group, and creating logical volumes](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>11</sup>](https://www.linuxbuzz.com/create-lvm-partition-in-linux/).
            
* **Volume Group, Physical Extent**
    
    * [**Theory**: A volume group in LVM is a pool of disk space built from one or more physical volumes](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>12</sup>](https://www.geeksforgeeks.org/logical-volume-manager-lvm-tutorial/). [A physical extent is a small, fixed-size chunk of a volume within a volume group](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>10</sup>](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations).
        
    * **Interview Questions and Answers**:
        
        * Q: What is a volume group in LVM?
            
        * [A: A volume group in LVM is a pool of disk space built from one or more physical volumes](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>12</sup>](https://www.geeksforgeeks.org/logical-volume-manager-lvm-tutorial/).
            
        * Q: What is a physical extent in LVM?
            
        * [A: A physical extent is a small, fixed-size chunk of a volume within a volume group](https://www.geeksforgeeks.org/swap-space-in-operating-system/)[<sup>10</sup>](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations).
            
* **blkid, df, du, mount, umount, mkswap, lsblk Commands**
    
    * **Theory**: These are all Linux commands used for various operations. `blkid` prints the block device attributes, `df` reports file system disk space usage, `du` estimates file and directory space usage, `mount` mounts a filesystem, `umount` unmounts a filesystem, `mkswap` sets up a Linux swap area, and `lsblk` lists block devices.
        
    * **Interview Questions and Answers**:
        
        * Q: What does the `df` command do in Linux?
            
        * A: The `df` command in Linux reports file system disk space usage.
            
        * Q: How do you use the `mount` command to mount a filesystem in Linux?
            
        * A: The `mount` command can be used to mount a filesystem in Linux by specifying the device and the mount point, like so: `mount /dev/sdXY /mount/point`.
            
    * **Practical Questions and Answers**:
        
        * Q: How to use the `du` command to estimate the space usage of a directory?
            
        * A: You can use the `du` command to estimate the space usage of a directory by running `du -sh /path/to/directory`, where `/path/to/directory` is the directory you want to check.
            
* 1. **How to take snapshot in LVM, how to recover accidentally deleted LVM**
        
        * Theory:
            
            [LVM snapshots use a copy-on-write mechanism to take snapshots](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>1</sup>](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/). [When you create a snapshot volume, it holds some metadata about the source logical volume and its block details](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>1</sup>](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/). [When you make any changes in the source volume, LVM monitors the changes and takes a snapshot of the modified blocks](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>1</sup>](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/).
            
            * [To recover a deleted LVM, Linux keeps backup copies of LVM configuration in the `/etc/lvm/archive` directory](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>2</sup>](https://www.edureka.co/community/74977/how-to-recover-deleted-lvm-in-linux). [You can restore the LVM partition using `vgcfgrestore` and an archive file](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>2</sup>](https://www.edureka.co/community/74977/how-to-recover-deleted-lvm-in-linux).
                
        * Interview Questions and Answers:
            
            * Q: How do you create a snapshot in LVM?
                
            * [A: Use the `lvcreate` command with the `-L`, `-s`, and `-n` options](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>3</sup>](https://www.golinuxhub.com/2017/09/understanding-lvm-snapshots-create/).
                
            * Q: How do you recover a deleted LVM in Linux?
                
            * A: You need to find the backed-up configurations of Volume Group using the `vgcfgrestore --list <Volume-Group-Name>` command. [Then recover the LVM partition using `vgcfgrestore` and an archive file](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>4</sup>](https://www.stechies.com/lvm-interview-questions/).
                
        * Practical Questions and Answers:
            
            * Q: How do you create a snapshot of a logical volume named `lv1` in a volume group named `vg1`?
                
            * [A: Use the command `lvcreate -L 1G -s -n snap_lv1 /dev/vg1/lv1`](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>3</sup>](https://www.golinuxhub.com/2017/09/understanding-lvm-snapshots-create/).
                
            * Q: How do you recover a deleted logical volume named `lv1` from a volume group named `vg1`?
                
            * [A: Use the command `vgcfgrestore --list vg1` to find the backed-up configurations, then recover the LVM partition using `vgcfgrestore -f /etc/lvm/archive/vg1_<timestamp>.vg vg1`](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>4</sup>](https://www.stechies.com/lvm-interview-questions/).
                
    2. **How to extend LVM partition**
        
        * Theory:
            
            * [To extend the size of your logical volume, you need to create a new partition on the hard disk, add the partition you just created as a physical volume, add the new physical volume to the volume group, assign space from the volume group to the logical volume, and resize the filesystem](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>5</sup>](https://networklessons.com/uncategorized/extend-lvm-partition).
                
        * Interview Questions and Answers:
            
            * Q: What are the steps to extend an LVM partition?
                
            * A: Type in the `df -h` command for listing the file system. After that, check the available or free space in the Volume group. To increase the size of the partition, use the `lvextend` command. Execute the `resize2fs` command. [To verify the `/home` size use the `df` command](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>4</sup>](https://www.stechies.com/lvm-interview-questions/).
                
        * Practical Questions and Answers:
            
            * Q: How do you extend a logical volume named `lv1` in a volume group named `vg1` by 1GB?
                
            * [A: Use the command `lvextend -L +1G /dev/vg1/lv1`](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>4</sup>](https://www.stechies.com/lvm-interview-questions/).
                
    3. **How to migrate PV to another new PV in LVM**
        
        * Theory:
            
            * [The `pvmove` command moves allocated physical partitions and the data they contain from the source physical volume to one or more destination physical volumes](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>6</sup>](https://www.ibm.com/docs/en/ds8870/7.4?topic=manager-using-migratepv-command). [The specified physical volumes must all be in the same volume group](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>6</sup>](https://www.ibm.com/docs/en/ds8870/7.4?topic=manager-using-migratepv-command).
                
        * Interview Questions and Answers:
            
            * Q: How do you migrate data from one physical volume to another in LVM?
                
            * A: To migrate data from one physical volume to another, use the `pvmove` command: `pvmove <source_physical_volume> <destination_physical_volume>`. [This command will move all the data from the source physical volume to the destination physical volume](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>7</sup>](https://testbook.com/interview/linux-lvm-interview-questions).
                
        * Practical Questions and Answers:
            
            * Q: How do you migrate data from a physical volume `/dev/sdb` to another physical volume `/dev/sdc` in LVM?
                
            * [A: Use the command `pvmove /dev/sdb /dev/sdc`](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>7</sup>](https://testbook.com/interview/linux-lvm-interview-questions).
                
    4. **resize2fs and xfs\_growfs command**
        
        * Theory:
            
            * The `resize2fs` command is used to resize ext2, ext3, or ext4 file systems. [It can be used to enlarge or shrink an unmounted file system located on device](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>8</sup>](https://unix.stackexchange.com/questions/231598/what-does-resize2fs-command-do-in-linux).
                
            * [The `xfs_growfs` command is used to resize an XFS file system](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>9</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/storage_administration_guide/xfsgrow). The `-d` option grows the file system to the specified size (expressed in file system blocks). [Without the `-d` option, `xfs_growfs` will grow the file system to the maximum size supported by the device](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>9</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/storage_administration_guide/xfsgrow).
                
        * Interview Questions and Answers:
            
            * Q: What does the `resize2fs` command do in Linux?
                
            * A: `resize2fs` makes the filesystem use only the first size bytes of the storage. [It does this by moving both filesystem metadata and your data around](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>8</sup>](https://unix.stackexchange.com/questions/231598/what-does-resize2fs-command-do-in-linux).
                
            * Q: How do you resize an XFS file system?
                
            * [A: An XFS file system may be grown while mounted using the `xfs_growfs` command](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>9</sup>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/storage_administration_guide/xfsgrow).
                
        * Practical Questions and Answers:
            
            * Q: How do you extend an XFS file system on `/dev/sda1`?
                
            * [A: Use the command `xfs_growfs -d /dev/sda1`](https://ostechnix.com/how-to-use-lvm-snapshot-to-backup-your-data-in-linux/)[<sup>10</sup>](https://stackoverflow.com/questions/38160794/how-to-resize-root-partition-online-on-xfs-filesystem).
                
            * Q: How do you extend an ext4 file system on `/dev/sda1`?
                
            * [A: Use the command `resize2fs /dev/sda1`](https://superuser.com/questions/1742910/how-to-expand-logical-volume-on-existing-physical-volume-on-linux)[<sup>11</sup>](https://superuser.com/questions/1742910/how-to-expand-logical-volume-on-existing-physical-volume-on-linux).
                

---

**14–&gt;&gt; Booting:**

* **Explain the boot process of Linux OS**
    
    * **Theory:** The Linux boot process consists of several stages including BIOS, MBR, GRUB, Kernel, Init, Runlevel/Target. Each stage has a specific role in getting the system up and running.
        
    * **Interview Questions and Answers:**
        
        * Q: Can you explain the boot process of a Linux system?
            
        * A: The boot process of a Linux system involves several stages. It starts with the BIOS (Basic Input Output System), which initializes the hardware and checks for bootable media. The MBR (Master Boot Record) then loads the GRUB (Grand Unified Bootloader). GRUB locates the kernel, loads it into memory, and then control is passed to the kernel. The kernel initializes the system and mounts the root file system. The Init process then starts, which sets the runlevel or target and starts the corresponding services.
            
    * **Practical Questions and Answers:**
        
        * Q: How can you check the current runlevel of your system?
            
        * A: You can use the `runlevel` command to check the current runlevel of your system.
            
* **What is run level, what is target**
    
    * **Theory:** A runlevel is a mode of operation in the Linux operating system. Linux traditionally uses seven runlevels. A target is a similar concept used in systemd, which replaced the init system in many Linux distributions.
        
    * **Interview Questions and Answers:**
        
        * Q: What is the difference between a runlevel and a target?
            
        * A: A runlevel is a mode of operation in the Linux operating system. Linux traditionally uses seven runlevels. A target is a similar concept used in systemd, which replaced the init system in many Linux distributions.
            
    * **Practical Questions and Answers:**
        
        * Q: How can you change the default runlevel or target of your system?
            
        * A: You can use the `systemctl set-default` command to change the default target of your system.
            
* **How to resolve fstab issue at boot time**
    
    * **Theory:** The /etc/fstab file contains information about filesystems on the system. If there’s an error in this file, it can cause issues at boot time. To resolve these issues, you would need to boot into a rescue or single-user mode and correct the errors in the /etc/fstab file.
        
    * **Interview Questions and Answers:**
        
        * Q: How would you resolve an issue with the /etc/fstab file that is preventing the system from booting?
            
        * A: To resolve an issue with the /etc/fstab file, I would boot the system into rescue or single-user mode, then open the /etc/fstab file in a text editor, correct any errors, and then reboot the system.
            
    * **Practical Questions and Answers:**
        
        * Q: How can you check the syntax of the /etc/fstab file without rebooting the system?
            
        * A: You can use the `mount -a` command to mount all filesystems listed in /etc/fstab. This can help you catch any syntax errors before they cause issues at boot time.
            
* **How to reset root password in RHEL7, RHEL8, RHEL9**
    
    * **Theory:** To reset the root password in RHEL, you would need to boot into single-user mode or emergency mode, mount the root filesystem, then use the `passwd` command to change the root password.
        
    * **Interview Questions and Answers:**
        
        * Q: How would you reset the root password in RHEL?
            
        * A: To reset the root password in RHEL, I would reboot the system and interrupt the boot process to enter the boot menu. Then, I would append `rd.break` or `single` to the kernel line for single-user mode or `systemd.unit=`[`rescue.target`](http://rescue.target) or `systemd.unit=`[`emergency.target`](http://emergency.target) for emergency mode, then remount the root filesystem with read-write permissions using `mount -o remount,rw /sysroot`, chroot into the /sysroot directory, and then use the `passwd` command to change the root password.
            
    * **Practical Questions and Answers:**
        
        * Q: How can you ensure the SELinux context is correct after changing the root password?
            
        * A: After changing the root password, you can use the `touch /.autorelabel` command to ensure the SELinux context is correct. This will cause the system to relabel the filesystem for SELinux on the next reboot.