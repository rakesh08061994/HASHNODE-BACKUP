---
title: "Solve: Break Linux Administrative Password on Fedora based Linux Machines"
seoTitle: "Reset Fedora Linux Admin Password"
seoDescription: "Learn how to reset or break the root password on Fedora systems using boot loader without external media"
datePublished: Tue Aug 13 2024 09:31:23 GMT+0000 (Coordinated Universal Time)
cuid: clzs83k0r000w09lgbwk8864y
slug: solve-break-linux-administrative-password-on-fedora-based-linux-machines
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723538697242/9088c6d9-0505-4a4c-9cf9-6a6b565f7bb8.png
tags: linux, hacking, passwords

---

---

**Y**ou know how it feels when you forget your Linux password and suddenly can’t do anything on your own machine? It's super frustrating, especially when you’re locked out of something important. Whether you’re using Fedora, Ubuntu, or any other Linux distro, you need that admin access to keep things running smoothly—installing software, updating the system, all that stuff. Without it, you’re just stuck.

But here’s the good news: Linux has a safety net. You can actually reset or break the password and get back in control. It might sound a bit intimidating at first, but trust me, with a little guidance, it’s totally doable.

---

**S**o, imagine this: you’re the system admin, and suddenly you can’t remember your root password. It’s one of those moments where everything grinds to a halt because, without that password, you’re locked out of doing just about anything important on your system. Maybe you were in the middle of something critical, and now you’re stuck. But don’t worry—Linux has got your back.

### **Resetting the Root Password from the Boot Loader**

If you ever find yourself in this situation, knowing how to reset a lost root password is a skill every system admin needs. If you’re already logged in with sudo access or as root, it’s no big deal. But if you’re not logged in, things get a bit trickier.

> You’ve got a few options here. Some might suggest booting from a Live CD, mounting your root file system, and then editing `/etc/shadow` to fix the problem. But let’s face it, not everyone wants to fiddle with external media. So, let’s explore a method that doesn’t require any of that.

On older Red Hat systems, you could just boot into runlevel 1 to get a root prompt. In the newer versions, like Red Hat Enterprise Linux 8 and beyond, it’s a bit different. You’ll need to use either the rescue or emergency targets, but here’s the catch—they still require the root password. If your system was deployed from a Red Hat cloud image, you might not have a rescue kernel in your boot menu, but your default kernel has a trick up its sleeve—it lets you enter maintenance mode without needing the root password.

### **How to Do It:**

### Approach-1

1. **Reboot Your System:** Start by rebooting your machine.
    
    **Interrupt the Boot:** When the boot-loader countdown starts, hit any key (except Enter) to stop it.
    
    > **You will see kernel images here, select "rescue" kernel image. use ↑ & ↓ arrow key to change the selection.**
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723540174841/a5b69a16-0fe3-4e36-88ed-d2fd2ecffba8.png align="center")
    
    **Select the Rescue Kernel:** Use the arrow keys to move the cursor to the entry with the word "rescue" in its name.
    
3. **Edit the Boot Parameters:** Press `e` to edit the selected entry.
    
4. **Modify the Kernel Command Line:** Find the line that begins with `linux` and append `rd.break` at the end after entering a single space. This tells the system to pause just before handing control from the initramfs to the actual system.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723540357882/0e59b6f6-25fb-4a7d-8cda-da5664ea0358.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723540495481/88a6cd23-9725-4d76-9294-1afc82dcc9f4.png align="center")
    
5. **Boot with the Changes:** Press `Ctrl+x` to boot with the modified parameters.
    
6. **Maintenance Mode:** When prompted, press Enter to enter maintenance mode.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723540551196/fe06b0b8-f337-4ce2-a17d-2ddf9e4adbaa.png align="center")
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Now, you’ll have access to a root shell, but there’s a catch—the root file system is mounted as read-only. You’ll need to remount it as read/write to make changes</div>
</div>

7. **Remount the File System:** Run this command to remount the root file system as read/write:
    
    ```plaintext
    switch_root:/# mount -o remount,rw /sysroot
    ```
    
8. **Enter a Chroot Jail:** This makes `/sysroot` the root of your file-system tree:
    
    ```plaintext
    switch_root:/# chroot /sysroot
    ```
    
9. **Reset the Password:** Set a new root password with this command:
    
    ```plaintext
    sh-5.1# passwd root
    Changing password for user root.
    New password: **********
    Retype new password: **********
    passwd: all authentication tokens updated successfully.
    ```
    
10. **Ensure Files Get Relabeled:** This step is crucial to avoid SELinux issues later. Run:
    
    ```plaintext
    sh-5.1# touch /.autorelabel
    ```
    
11. **Exit and Reboot:** Type `exit` twice—once to leave the chroot jail and once to exit the initramfs shell. The system will continue booting, perform a full SELinux relabel, and then reboot again. It will take some time to restart, so login now with new password for the root user.
    
    ```plaintext
    sh-5.1# exit
    switch_root:/# exit
    ```
    

---

### Approach-2

1. **Reboot Your System:** Start by rebooting your machine.
    
    **Interrupt the Boot:** When the boot-loader countdown starts, hit any key (except Enter) to stop it.
    
    > **You will see kernel images here, select "rescue" kernel image. use ↑ & ↓ arrow key to change the selection.**
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723540174841/a5b69a16-0fe3-4e36-88ed-d2fd2ecffba8.png align="center")
    
    **Select the Rescue Kernel:** Use the arrow keys to move the cursor to the entry with the word "rescue" in its name.
    
3. **Edit the Boot Parameters:** Press `e` to edit the selected entry.
    
4. **Modify the Kernel Command Line:** Find the line that begins with `linux` and append `rw init=/bin/bash` at the end after entering a single space. This tells the system to pause just before handing control from the initramfs to the actual system.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723556552752/08cd55d1-169c-4466-bc2b-dbe5c6b9e71a.png align="center")
    
5. **Boot with the Changes:** Press `Ctrl+x` to boot with the modified parameters.
    
6. **Maintenance Mode:** When prompted, press Enter to enter maintenance mode.
    
    ```plaintext
    bash# passwd root
    Changing password for user root.
    New password: **********
    Retype new password: **********
    passwd: all authentication tokens updated successfully.
    touch /.autorelabel
    /sbin/reboot -f
    ```
    
7. **Ensure Files Get Relabeled:** This step is crucial to avoid SELinux issues later.
    
    ```plaintext
    bash# touch /.autorelabel
    ```
    
8. **Exit and Reboot:** Type `/sbin/reboot -f` and hit enter. Now the system will continue booting, perform a full SELinux relabel, and then reboot again. It will take some time to restart, so login now with new password for the root user.
    
    ```plaintext
    bash# /sbin/reboot -f
    ```
    

And that’s it! You’re back in business with a new root password, and you didn’t even need to mess around with external media. Whether you’re troubleshooting or just making sure you’re prepared for a rainy day, knowing this trick can save you a lot of headaches.