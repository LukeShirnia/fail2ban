Ansible Role: Fail2ban
=========

This installs and configures fail2ban, including jails such as: sshd, wp-login.php and xmlrpc on Redhat and Debian based systems


Role Variables
--------------

```
f2b_sshd: "y"
f2b_xmlrpc: "y"
f2b_wp_login: "y"

sshd_port: 22

ban_action: "firewallcmd-ipset"

# xml_rpc + wp_login
log_path: "%(nginx_access_log)s"

# xml_rpc
max_retry: "5"
find_time: "600"
ban_time: "31536000"

# wp_login
wp_login_retry: "10"
wp_login_findtime: "300"
wp_login_bantime: "31536000"
```

Example Playbook
----------------

```
---
- hosts: all
  become: yes
  vars:
    f2b_xmlrpc: "n"
    sshd_port: 1234
  roles:
    - fail2ban
```

License
-------

Apache

Author Information
------------------

This role was created by [Luke Shirnia](https://shirnia.com)
