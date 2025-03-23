# Ansible System Setup Playbooks

This repository contains Ansible playbooks for automating system administration tasks, software installation, and firewall configurations.

## 📜 Playbooks

1. **System Administration Playbook (`system_admin.yml`)**
   - Updates packages
   - Manages users and firewall rules
   - Installs essential software like Vim, Git, and Nginx

2. **Software Installation Playbook (`install_software.yml`)**
   - Installs Git, Google Chrome, and NVIDIA drivers

3. **Master Playbook (`master_playbook.yml`)**
   - Calls both system administration and software installation playbooks

## 📌 How to Use

1️⃣ Setup Inventory
Modify `inventory.ini` with your server details:
```ini
[servers]
server1 ansible_host=192.168.1.10 ansible_user=jaffer ansible_ssh_private_key_file=~/.ssh/id_rsa
server2 ansible_host=192.168.1.11 ansible_user=jaffer ansible_ssh_private_key_file=~/.ssh/id_rsa

[all:vars]
ansible_python_interpreter=/usr/bin/python3
2️⃣ Run the Playbook
Execute the master playbook:
ansible-playbook -i inventory.ini playbooks/master_playbook.yml
3️⃣ Configure Firewall (Optional)
Allow traffic from a specific IP:
iptables -A INPUT -s <IP_ADDRESS> -j ACCEPT
iptables-save > /etc/iptables/rules.v4
