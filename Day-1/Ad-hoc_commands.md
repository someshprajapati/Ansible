# Ansible Ad-Hoc Commands

## Ping all

```bash
ansible all -m ping
```

## Create a file on all remote clients

```bash
ansible all -m file -a "path=/home/somesh/adhoc1 state=touch mode=700"
```

## Delete a file on all remote clients

```bash
ansible all -m file -a "path=/home/somesh/adhoc1 state=absent"
```

## Copy a file to remote clients

```bash
ansible all -m copy -a "src=/tmp/adhoc2 dest=/home/somesh/adhoc2"
```

## Install packages

Install `telnet`:

```bash
ansible all -m yum -a "name=telnet state=present"
```

Install `httpd-manual`:

```bash
ansible all -m yum -a "name=httpd-manual state=present"
```

## Start the httpd service

```bash
ansible all -m service -a "name=httpd state=started"
```

## Start httpd and enable it at boot

```bash
ansible all -m service -a "name=httpd state=started enabled=yes"
```

## Check httpd service status on remote clients

```bash
ansible all -m shell -a "systemctl status httpd"
```

## Remove the httpd package

Using the `yum` module:

```bash
ansible all -m yum -a "name=httpd state=absent"
```

Using a shell command:

```bash
ansible all -m shell -a "yum remove httpd"
```

## Create a user on remote clients

```bash
ansible all -m user -a "name=jsmith home=/home/jsmith shell=/bin/bash state=present"
```

## Add a user to a different group

```bash
ansible all -m user -a "name=jsmith group=somesh"
```

## Delete a user on remote clients

Using the `user` module:

```bash
ansible all -m user -a "name=jsmith home=/home/jsmith shell=/bin/bash state=absent"
```

Using a shell command:

```bash
ansible all -m shell -a "userdel jsmith"
```

## Get system information from remote clients

```bash
ansible all -m setup
```

## Run a command without the shell module

Example: reboot `client1`

```bash
ansible client1 -a "/sbin/reboot"
```