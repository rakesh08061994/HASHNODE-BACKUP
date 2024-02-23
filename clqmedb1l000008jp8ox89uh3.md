---
title: "Linux Ansible Playbook Projects"
datePublished: Tue Dec 26 2023 13:42:58 GMT+0000 (Coordinated Universal Time)
cuid: clqmedb1l000008jp8ox89uh3
slug: linux-ansible-playbook-projects
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/2iUrK025cec/upload/260757b983223447e22e913dcdf96a31.jpeg

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703579923366/e4321b18-db69-4a31-abec-0e9fff048466.png align="center")

* **Control Node:**
    
    A system on which Ansible is installed. You run Ansible commands such as `ansible` or `ansible-inventory` on a control node.
    
* **Inventory**
    
    A list of managed nodes that are logically organized. You create an inventory on the control node to describe host deployments to Ansible.
    
* **Managed node**
    
    A remote system, or host, that Ansible controls.
    

---

### What is Ansible and why this is so important?

Ansible is used for the multi-tier deployments and it models all of IT infrastructure into one deployment instead of handling each one separately. There are no agents and no custom security architecture is required to be used in the Ansible architecture. The deployment is simple plain English like language that is used in Ansible called YAML which stands for “YAML Ain’t Markup Language.”

To work with Ansible is very easy; it pushes out small programs called “Ansible Modules” to your nodes to connect. It can deploy and connect using the SSH agent to execute the modules and then removes it when finished.

There are no servers, daemons or databases required these modules can reside anywhere in the machines. You need to work with any text editor or terminal programs and along with a version control system to manage the changes in the content.

---

### What is main Components of Ansible Architecture?

Ansible is a radically simple IT automation engine that automates cloud provisioning, configuration management, application deployment, intra-service orchestration, and many other IT needs. Being designed for multi-tier deployments since day one, Ansible models your IT infrastructure by describing how all of your systems inter-relate, rather than just managing one system at a time. It uses no agents and no additional custom security infrastructure, so it is easy to deploy - and most importantly, it uses a very simple language (YAML, in the form of Ansible Playbooks) that allows you to describe your automation jobs in a way that approaches plain English.

* [Modules](https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#modules)
    
* [Module utilities](https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#module-utilities)
    
* [Plugins](https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#plugins)
    
* [Inventory](https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#inventory)
    
* [Playbooks](https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#playbooks)
    
* [The Ansible search path](https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#the-ansible-search-path)
    

---

1. ### Web-Server Configuration ansible-playbook
    

```plaintext
ansible@cn ~$ vim web-server.yml

---
- name: Configuring web server
  hosts: all
  tasks:
    - name: "Yum repository configuration on node1 machine"
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

    - name: Install yum package
      yum:
        name: httpd
        state: latest
      notify: restart service

    - name: create index.html
      file:
        path: /var/www/html/index.html
        state: touch

    - name: 'add 80 port in firewall'
      firewalld:
        port: 80/tcp
        state: enabled
        immediate: true
        permanent: true

    - name: add some lines
      lineinfile:
        line: "This is web-server successful deployment"
        path: /var/www/html/index.html

  handlers: 
    - name: restart service
        service:
          name: httpd
          state: restarted
          enabled: yes
```

```plaintext
$ ansible-playbook web-server.yml
```

---

1. ### User configuration Setup for Password-less SSH and sudo Permissions using Ansible playbook.
    

```plaintext
localhost@ansible ~$ vim webserver.yml 
---
- name: Configuring task1
  hosts: all
  vars:
    username: shyam
    userpass: password
  tasks:

    - name: Create a new user "{{ username }}"
      user:
        name: "{{ username }}"
        password: "{{ userpass | password_hash('sha512') }}" 
        state: present

    - name: Configure ssh to make password-less connection between managed-hosts machines
      ansible.posix.authorized_key:
        user: '{{ username }}'
        state: present
        key: "{{ lookup('file', '/home/ansible/.ssh/id_rsa.pub') }}"

    - name: Provide sudoers permission to user '{{ username }}'
      ansible.builtin.file:
        path: /etc/sudoers.d/{{ username }}
        state: touch

    - name: sudoers entry in /etc/sudoers.d/{{ username }}
      ansible.builtin.lineinfile:
        path: /etc/sudoers.d/{{ username }}
        line: "'{{ username }}' ALL=(ALL) NOPASSWD:ALL"

    - name: restart sshd service
      ansible.builtin.service:
        name: sshd
        state: restarted
```

```plaintext
$ ansible-playbook basic-task1.yml
```

---

1. ### Normal Linux Admin Tasks Automation By Ansible
    

```plaintext
$ vim basic.yml
---
- name: Solve RHCSA practice dump paper question
  hosts: stage
  gather_facts: true
  vars:
    - userpass: aternoth
  tasks:

    - name: "Yum repository configuration on node1 machine"
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
      when: ansible_facts.distribution == "RedHat" or ansible_facts.distribution == "Fedora"

    - name: "Install httpd package"
      yum:
        name: "{{ item }}"
        state: latest
      loop:
        - firewalld
        - httpd
        - selinux-policy

    - name: "Start the services"
      service:
        name: "{{ item }}"
        state: started
        enabled: true
      loop:
        - httpd
        - firewalld

    - name: "add 82 port on selinux"
      community.general.seport:
        ports: 82
        proto: tcp
        setype: http_port_t
        state: present

    - name: add port 82 on firewall
      ansible.posix.firewalld:
        port: 82/tcp
        permanent: true
        state: enabled
        immediate: yes

    - name: Ensure the default Apache port is 82
      ansible.builtin.lineinfile:
        path: /etc/httpd/conf/httpd.conf
        regexp: '^Listen '
        line: Listen 82

    - name: Check if user natasha exists
      ansible.builtin.command: getent passwd natasha
      register: natasha_user_check
      ignore_errors: true

    - name: create a user natasha is not exists
      user:
        name: natasha
        state: present
      when:  natasha_user_check.rc != 0

    - name: cronjob
      ansible.builtin.cron:
        name: "check dirs"
        minute: "30"
        hour: "13"
        user: natasha
        job: "/bin/echo hiya"

    - name: restart crond service
      service:
        name: crond
        state: restarted
        enabled: true

    - name: create group sysadmin
      group:
        name: sysadmin
        state: present

    - name: "Create the following users, groups, and group memberships"
      user:
        name: "{{ item.name }}"
        state: present
        groups: "{{ item.group }}"
        password: "{{ userpass | password_hash('sha512') }}"
        shell: "{{ item.shell }}"
      loop:
        - { name: natasha, group: sysadmin, shell: /bin/bash }
        - { name: sarah, group: sysadmin, shell: /bin/bash }

    - name: "Create user harry with no login shell"
      user:
        name: harry
        password: "{{ userpass | password_hash('sha512') }}"
        shell: /sbin/nologin


    - name: "Create a collaborative directory “/common/admin” and do following conf"
      file:
        path: /common/admin #--------- /common directory should be created on managed host
        group: sysadmin
        state: directory
        mode: 02770
```

```plaintext
ansible-playbook basic.yml
```

---

1. ### How to create disk Logical Volume partition, and mount
    

```plaintext
[ansible@cn ~]$ vim partition.yml

- name: playbook for simple 1 GB partition
  hosts: stage
  become: true
  tasks:
    - name: create partition
      parted:
        device: /dev/sdc
        number: 1
        flags: [ lvm ]
        state: present
        part_end: 4GB
      register: opt

    - name: Show details
      debug:
        var: opt

    - name: Install lvm2 dependency
      package:
        name: lvm2
        state: present

    - name: task for creating volume group
      lvg:
          vg: sample-vg2
          pvs: /dev/sdc
          pesize: 16

    - name: task for creating logical volume
      lvol:
          vg: sample-vg2
          lv:  sample-lv2
          size: 1g
          force: yes

    - name: Create directory data1 if does not exist
      file:
        path: /data3
        state: directory
        mode: '0755'

    - name: format the xfs filesystem
      filesystem:
        fstype: xfs
        dev: /dev/sample-vg2/sample-lv2

    - name: mount the lv on /data3
      mount:
        path: /data3
        src: /dev/sample-vg2/sample-lv2
        fstype: xfs
        state: mounted
```

```plaintext
$ ansible-playbook partition.yml
```

---

---

---

---

---

---

---