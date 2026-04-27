# 📦 Ansible Modules Overview

This repository documents commonly used **Ansible modules** categorized by their functionality.

---

## 📚 Module Categories

- System  
- Commands  
- Files  
- Database  
- Cloud  
- Windows  
- More...

---

## ⚙️ System Modules

Used for managing system-level configurations:

- User  
- Group  
- Hostname  
- Iptables  
- Lvg (Logical Volume Group)  
- Lvol (Logical Volume)  
- Make  
- Mount  
- Ping  
- Timezone  
- Systemd  
- Service  

---

## 💻 Command Modules

Used to execute commands on remote systems:

- Command  
- Expect  
- Raw  
- Script  
- Shell  

---

## 📁 File Modules

Used for managing files and directories:

- Acl  
- Archive  
- Copy  
- File  
- Find  
- Lineinfile  
- Replace  
- Stat  
- Template  
- Unarchive  

---

## ☁️ Cloud Modules

Used for managing cloud infrastructure:

- Amazon (AWS)  
- Atomic  
- Azure  
- Centrylink  
- Cloudscale  
- Cloudstack  
- Digital Ocean  
- Docker  
- Google Cloud  
- Linode  
- Openstack  
- Rackspace  
- Smartos  
- Softlayer  
- VMware  

---

## 📝 Notes

- These modules help automate infrastructure and configuration management.
- Commonly used in **DevOps workflows** and **IT automation**.
- Typically executed via Ansible playbooks.

---

## 🚀 Example Usage

```bash
ansible-playbook playbook.yml