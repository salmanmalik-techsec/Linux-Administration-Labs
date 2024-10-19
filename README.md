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

## **Monitoring and Alerting with Icinga2**
### **Overview**  
   - Use Icinga2 to monitor the status of your Linux systems and services.
### **Steps:**
**1. Install Icinga2:**
```bash
sudo apt install icinga2 monitoring-plugins -y
sudo systemctl start icinga2
```
**2. Monitor Remote Systems:**
- Install Icinga Agent on remote VMs.
- Set up alerts for CPU, memory, and storage usage.

 ## **Centralized Logging with Rsyslog**
### **Overview**  
   - Configure Rsyslog to collect logs from multiple VMs in a single location.

### **Steps:**

**1. Install Rsyslog:**
```bash
sudo apt install rsyslog -y
sudo systemctl start rsyslog
```
**2. Configure Remote Logging:**
- Set up remote VMs to forward logs to the primary Rsyslog server.
- Set up log rotation and monitor failed SSH attempts.
  
 ## **Disk Management and LVM Setup**
### **Overview**  
   - Manage partitions and configure LVM (Logical Volume Manager) for dynamic storage.

### **Steps:**

**1. Create Partitions with fdisk:**
```bash
sudo fdisk /dev/sdb
mkfs.ext4 /dev/sdb1
sudo mount /dev/sdb1 /mnt
```
**2. Configure LVM:**
   - Create Physical Volumes (PVs), Volume Groups (VGs), and Logical Volumes (LVs).
   - Extend a volume:
     ```bash
     sudo lvextend -L +1G /dev/mapper/myvg-mylv
     sudo resize2fs /dev/mapper/myvg-mylv
    ```

## **User Management and Permissions**
### **Overview**  
   - Manage user accounts, groups, and permissions to control access.

### **Steps:**

**1. Create Users and Groups:**
```bash
sudo useradd -m -s /bin/bash newuser
sudo passwd newuser
sudo groupadd devs
sudo usermod -aG devs newuser
```
**2. Manage Permissions:**
   - Use chmod, chown, and ACLs to configure access control.

## **Network Configuration and Troubleshooting**
### **Overview**  
   - Configure network interfaces and troubleshoot network issues.

### **Steps:**

**1. Configure Static IPs:**
   - Modify /etc/netplan/ or /etc/network/interfaces.
**2. Use Networking Tools:**
     ```bash
     ping google.com
     traceroute google.com
     sudo tcpdump -i eth0
     ```
## **Shell Scripting and Automation**
### **Overview**  
   - Automate routine tasks using shell scripts and cron jobs.

### **Steps:**

**1. Create a Backup Script:**
   ```bash
     #!/bin/bash
     sudo apt update && sudo apt upgrade -y | tee /var/log/update.log
```
**2.Schedule a Cron Job:**
- Run the backup script weekly:
  ```bash
  crontab -e
  0 3 * * 1 /path/to/script.sh
  ```
  ## **Backup and Restore**
### **Overview**  
   - Use rsync for backups and test disaster recovery scenarios.

### **Steps:**

**1. Backup with rsync:**
   ```bash
      rsync -avz /var/www/html/ /backup/
```
**2. Automate with Cron:**
   - Schedule daily backups using cron jobs.



