# **Linux Administration Labs**  
![Linux](https://img.shields.io/badge/Linux-Admin-blue?style=flat&logo=linux)  

Welcome to my **Linux Administration Labs** repository! This space documents my hands-on journey toward mastering Linux system administration. Each lab is designed to replicate real-world scenarios, showcasing practical skills in **server management, networking, scripting, monitoring, and automation**—all essential for a Linux Admin role.

---

## **Table of Contents**
- [Basic Linux Setup and Virtualization](#basic-linux-setup-and-virtualization)
- [LAMP Stack Deployment](#lamp-stack-deployment)
- [Monitoring and Alerting with Icinga2](#monitoring-and-alerting-with-icinga2)
- [Centralized Logging with Rsyslog](#centralized-logging-with-rsyslog)
- [Disk Management and LVM Setup](#disk-management-and-lvm-setup)
- [User Management and Permissions](#user-management-and-permissions)
- [Network Configuration and Troubleshooting](#network-configuration-and-troubleshooting)
- [Shell Scripting and Automation](#shell-scripting-and-automation)
- [Backup and Restore](#backup-and-restore)
- [Future Additions](#future-additions)
- [How to Use This Repository](#how-to-use-this-repository)
- [Contact and Feedback](#contact-and-feedback)

---

## **Basic Linux Setup and Virtualization**

### **Overview**  
- Set up Linux systems using **Vagrant** and **VirtualBox**.
- Create multiple VMs with private networks to simulate a lab environment.

### **Steps**
1. **Install VirtualBox and Vagrant** on your machine.
2. **Create a VM with Vagrant:**
   ```bash
   mkdir linux-lab
   cd linux-lab
   vagrant init ubuntu/bionic64
   vagrant up
   vagrant ssh
   ```
3. **Test VM Management Commands**
```bash
   vagrant halt
   vagrant up
   vagrant destroy
```
4. **Configure a Private Network Between VMs**
   - **Assign static IPs and SSH between them.**

---

 ## **LAMP Stack Deployment**

### **Overview**  
   - Install and configure the **LAMP stack** to host web applications.

### **Steps:**

**1. Install Apache:**
```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
```
**2. Install PHP and MariaDB:**
```bash
sudo apt install php mariadb-server php-mysql -y
sudo mysql_secure_installation
```
**3. Deploy a sample application (Kanboard or WordPress) and connect it to MariaDB.**






