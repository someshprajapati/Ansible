## LAB 1: Test Basic Ansible Ad-Hoc Commands

This lab demonstrates a few basic Ansible ad-hoc commands for validating connectivity and gathering facts from managed nodes.

### 1. Create the Inventory File

Create an inventory file that contains the IP addresses and connection details for the managed nodes.

```ini
[test_server]
192.168.56.12 hostname=node2 ansible_user=vagrant ansible_password=vagrant
192.168.56.13 hostname=node3 ansible_user=vagrant ansible_password=vagrant

[test_server:vars]
ansible_python_interpreter=/usr/bin/python3.12
```

Example command used to view the inventory:

```bash
cat inventory
```

### 2. List All Hosts

Use the following command to verify that Ansible can read all hosts from the inventory file.

```bash
ansible all -i inventory --list-hosts
```

Sample output:

```text
hosts (2):
  192.168.56.12
  192.168.56.13
```

### 3. Ping All Managed Nodes

Run the ping module to confirm connectivity from the control node to all managed hosts.

```bash
ansible all -i inventory -m ping
```

Sample output:

```text
192.168.56.13 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
192.168.56.12 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

### 4. Gather Facts From All Nodes

Use the `gather_facts` module to collect system details such as CPU architecture, IP addresses, and other host information.

Note: the `-m` option specifies the Ansible module to run.

```bash
ansible all -i inventory -m gather_facts
```

Sample output:

```text
192.168.56.13 | SUCCESS => {
    "ansible_facts": {
        "ansible_all_ipv4_addresses": [
            "192.168.56.13",
            "10.0.2.15"
        ],
        "ansible_all_ipv6_addresses": [
            "fdf5:b57e:90aa:49df:a00:27ff:fed4:df",
            "fe80::a00:27ff:fed4:df",
            "fd17:625c:f037:2:a00:27ff:fef0:f51d",
            "fe80::a00:27ff:fef0:f51d"
        ],
        "ansible_apparmor": {
            "status": "enabled"
        },
        "ansible_architecture": "aarch64"
    }
}
```

### 5. Gather Facts From a Specific Node

To collect facts from only one host, limit the command to that node.

```bash
ansible all -i inventory -m gather_facts --limit 192.168.56.12 | head
```

Sample output:

```text
192.168.56.12 | SUCCESS => {
    "ansible_facts": {
        "ansible_all_ipv4_addresses": [
            "192.168.56.12",
            "10.0.2.15"
        ],
        "ansible_all_ipv6_addresses": [
            "fdf5:b57e:90aa:49df:a00:27ff:feee:285a",
            "fe80::a00:27ff:feee:285a",
            "fd17:625c:f037:2:a00:27ff:fef0:f51d"
        ]
    }
}
```
