---
title: "Start-to-Finish Ansible Setup: Easy Playbook Configuration"
datePublished: Fri Jan 05 2024 15:23:07 GMT+0000 (Coordinated Universal Time)
cuid: clr0scmll000409kyh7uv3qoo
slug: start-to-finish-ansible-setup-easy-playbook-configuration
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704468022129/23df849b-74a5-4c53-ab74-07855abed13f.jpeg
tags: linux, ansible, modules, beginner, devops, beginners, services, playbook, devops-articles, devops-trends, devops-journey, ansible-playbook, ansible-module, devopscommunity, 2024

---

> Note: Write your managed host's IP address and their hostnames in the `./hosts-ip.yml` file and don't forget to include it in your playbook.

```plaintext
vim ./hosts-ip.yml 
hosts-entries:   
  - ip: 192.168.10.1     
    hostname: mh1.example.com
  - ip: 192.168.10.2
    hostname: mh2.example.com  
  - ip: 192.168.10.3
    hostname: mh3.example.com
```

> Make sure to create an inventory file in the same place where your ansible.cfg is located, and don't forget to include it in your playbook.

```plaintext
vim ./inventory

[stage]
mh1.example.com

[test]
mh2.example.com

[prod]
mh3.example.com
```

> This is your ansible configuration playbook

```plaintext
---
- name: Install Ansible from scratch
  hosts: cn.example.com
  become: yes
  become_user: root
  gather_facts: yes
  vars:
    username: admin
    password: password
    inventory_file: path/to/inventory/file
  vars_files:
    - ./hosts-ip.yml
  tasks:
    - name: "Yum repository configuration on server"
      ansible.builtin.yum_repository:
        name: "{{ item.name }}"
        description: YUM repo
        file: external
        baseurl: "{{ item.baseurl }}"
        gpgcheck: 0
        enabled: 1
      loop:
        - { name: online_one, baseurl: "https://mirror.stream.centos.org/9-stream/AppStream/x86_64/os/" }
        - { name: online_two, baseurl: "https://mirror.stream.centos.org/9-stream/BaseOS/x86_64/os/" }
      when: ansible_facts.distribution in ['RedHat','Fedora'] and ansible_facts.distribution_major_version | int >= 9

    - name: "Setup EPEL REPOSITORY"
      ansible.builtin.dnf:
        name: https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm
        state: present
      when: ansible_facts.distribution in ['RedHat','Fedora'] and ansible_facts.distribution_major_version | int >= 9

    - name: "Install ansible in the machine"
      ansible.builtin.dnf:
        name: ansible
        state: latest
      register: output

    - name: show the result
      debug:
        var: output

    - name: "create ip hostname entry in /etc/hosts file of control-node machine"
      blockinfile:
        path: /etc/hosts
        lineinfile: "{{ item.ip }}  {{ item.hostname }}"
        state: present
      loop: "{{ hosts-entries }}"

    - name: "create a user {{ username }}"
      user:
        name:  "{{ username }}"
        state: present
        password: "{{ password | password_hash('sha512') }}"

    - name: Enable PermitRootLogin, PubkeyAuthentication, and PasswordAuthentication
      lineinfile:
        path: /etc/ssh/sshd_config
        regexp: "{{ item.regexp }}"
        line: "{{ item.line }}"
        state: present
        backup: yes
      loop:
        - { regexp: '^#?PermitRootLogin', line: 'PermitRootLogin yes' }
        - { regexp: '^#?PubkeyAuthentication', line: 'PubkeyAuthentication yes' }
        - { regexp: '^#?PasswordAuthentication', line: 'PasswordAuthentication yes' }
      notify: restart sshd service

    - name: "create ansible directory in {{ username }} home directory"
      file:
        path: "/home/{{ username }}/.ansible"
        state: directory

    - name: "Create ansible.cfg file in {{ username }} home directory under .ansible directory"
      file:
        path: "/home/{{ username }}/.ansible/{{ item }}"
        state: touch
      loop:
        - ansible.cfg
        - inventory

    - name: "Insert details in ansible.cfg file"
      blockinfile:
        path: "/home/{{ username }}/.ansible/ansible.cfg"
        block: |
          [defaults]
          inventory = "/home/{{ username }}/.ansible/inventory"
          remote_user = "{{ remote_user }}"
          ask_pass = false

          [privilege_escalation]
          become = true
          become_method = sudo
          become_user = root
          become_ask_pass = false

    - name: "create inventory file"
      ansible.builtin.copy:
        src: "{{ inventory_file }}"
        dest: "/home/{{ username }}/.ansible/inventory"
  handlers:
    - name: restart sshd service
      service:
        name: sshd
        state: restarted



- name: Install Ansible from scratch
  hosts: stage
  become: yes
  vars:
    username: ansible
  become_user: root
  gather_facts: yes
  tasks:
    - name: "Configure ssh to make password-less connection between machines"
      ansible.posix.authorized_key:
        user: '{{ username }}'
        state: present
        key: "{{ lookup('file', '/home/{{ username }}/.ssh/id_rsa.pub') }}"
      notify: restart sshd service
      register: connection-output

    - name: show the connection output
      debug:
        var: connection-output 

  handlers:
    - name: restart sshd service
      service:
        name: sshd
        state: restarted
```

---

### Description of this playbook in short

This Ansible playbook is designed to set up Ansible on a managed host. Here’s a simplified explanation of what each part does:

1. **Yum repository configuration on server**: This task sets up the Yum repositories on the server. It uses a loop to add two repositories, one for AppStream and one for BaseOS. This task only runs if the server’s operating system is RedHat or Fedora and the major version is 9 or above.
    
2. **Setup EPEL REPOSITORY**: This task installs the EPEL repository on the server. This task also only runs if the server’s operating system is RedHat or Fedora and the major version is 9 or above.
    
3. **Install ansible in the machine**: This task installs the latest version of Ansible on the server.
    
4. **Show the result**: This task displays the result of the Ansible installation.
    
5. **Create IP hostname entry in /etc/hosts file of control-node machine**: This task adds entries to the /etc/hosts file on the control node machine. The entries are defined in the `hosts-entries` variable.
    
6. **Create a user**: This task creates a new user on the server. The username and password are defined in the `username` and `password` variables.
    
7. **Enable PermitRootLogin, PubkeyAuthentication, and PasswordAuthentication**: This task modifies the SSH configuration to enable root login, public key authentication, and password authentication.
    
8. **Configure ssh to make password-less connection between machines**: This task sets up SSH keys for the new user to allow password-less connections between machines.
    
9. **Create ansible directory in user home directory**: This task creates a new directory for Ansible in the home directory of the new user.
    
10. **Create ansible.cfg file in user home directory under .ansible directory**: This task creates an Ansible configuration file and an inventory file in the new Ansible directory.
    
11. **Insert details in ansible.cfg file**: This task adds configuration details to the Ansible configuration file.
    
12. **Create inventory file**: This task copies an inventory file to the new Ansible directory.
    

---

As we reach the end of this journey, remember that technology is not just about understanding the new, but about transforming the old. It’s about taking the world as we know it and daring to envision it better. Here at [**rakamodify.online**](https://www.rakamodify.online), we don’t just write about technology, we live it. We breathe it. And we share that passion with you, our readers.

So, keep exploring, keep innovating, and keep modifying. The future is a blank canvas, teeming with possibilities. And with every line of code, every circuit built, and every system debugged, you’re painting your masterpiece.

Thank you for joining us on this journey. Until next time, keep modifying your world, one byte at a time. 😊

**#Technology** **#Innovation #Coding #Blogging #Learning #Inspiration #RakaModify** #Ansible #DevOps #Automation #ConfigurationManagement #InfrastructureAsCode #AnsiblePlaybook #OpenSource #CloudComputing #ITAutomation #Tech