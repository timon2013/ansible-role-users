Users
=========

The role can create users on your server. You can create users with sudo, use password, use key from file or variable. You can create groups for your user and assign specific user to specific group.

Build
-----------

Master branch:
[![Build Status](https://travis-ci.org/timon2013/ansible-role-users.svg?branch=master)](https://travis-ci.org/timon2013/ansible-role-users)

Dev Branch:
[![Build Status](https://travis-ci.org/timon2013/ansible-role-users.svg?branch=dev)](https://travis-ci.org/timon2013/ansible-role-users)

Requirements
------------

```bash
meta/main.yml
```

Role Variables
--------------

| Name | Default               | Type          | Description                       |
| ---- | --------------------- | ------------- | ----------------------------------|
| `disable_root_login` | False | Bool         | Disable user root login in /etc/ssh/sshd_config |
| `users_items` | defaults/main.yml | Array | Required. You can use: |
| user | not defined | String | Required. Username. |
| state | present | String | You can set absent or present. |
| shell | /bin/bash | String | Set the user's shell. |
| key | not defined | Bool | If you want to use ssh key login you have to define this variable. You can set true or false |
| key_var | not defined | String | You can enter a variable with a public key. If you don't set this, you use public key file. Default is "files/{{ item.user }}.pub" | 
| key_file | files/{{ item.user }}.pub | String | If you don't set this, you use public key file. Default is "files/{{ item.user }}.pub". This file is required. |
| password | not defined | String | The encrypted password https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-encrypted-passwords-for-the-user-module
| sudo | not defined | Bool | add to sudo. You can set true or false |
| sudo_without_password | not defined | Bool | Add to sudo without password confirmation. You can set true or false |
| groups | '' | List |  add the user to the groups. All existing groups will be retained. |
| `groups_items` |  | Array | You can use |
| name | not defined | String | Required. Group name. |
| state | present | string | You can set absent or present. |

Dependencies
------------

Example Playbook
----------------

```bash
molecule/default/playbook.yml
```

License
-------

MIT License

Author Information
------------------

timon2013
